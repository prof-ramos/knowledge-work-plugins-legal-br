**CRITICAL: You MUST complete these steps in order. Do not skip ahead to writing code.**

If you need to fill out a PDF form, first check to see if the PDF has fillable form fields. Run this script from this file's directory:
 `python scripts/check_fillable_fields <file.pdf>`, and depending on the result go to either the "Fillable fields" or "Non-fillable fields" and follow those instructions.

# Fillable fields
If the PDF has fillable form fields:
- Run this script from this file's directory: `python scripts/extract_form_field_info.py <input.pdf> <field_info.json>`. It will create a JSON file with a list of fields.
- Convert the PDF to PNGs: `python scripts/convert_pdf_to_images.py <file.pdf> <output_directory>`
- Analyze the images to determine the purpose of each form field
- Create a `field_values.json` file with the values to be entered for each field
- Run the `fill_fillable_fields.py` script: `python scripts/fill_fillable_fields.py <input pdf> <field_values.json> <output pdf>`

# Non-fillable fields
If the PDF doesn't have fillable form fields, you'll add text annotations.

## Step 1: Try Structure Extraction First

Run this script to extract text labels, lines, and checkboxes with their exact PDF coordinates:
`python scripts/extract_form_structure.py <input.pdf> form_structure.json`

**Check the results**: If `form_structure.json` has meaningful labels, use **Approach A: Structure-Based Coordinates**. If the PDF is scanned/image-based, use **Approach B: Visual Estimation**.

## Approach A: Structure-Based Coordinates (Preferred)

Use when `extract_form_structure.py` found text labels in the PDF.

1. Analyze the structure from form_structure.json
2. Create fields.json using `pdf_width` and `pdf_height` (signals PDF coordinates)
3. Validate: `python scripts/check_bounding_boxes.py fields.json`

## Approach B: Visual Estimation (Fallback)

Use when the PDF is scanned/image-based.

1. Convert PDF to images: `python scripts/convert_pdf_to_images.py <input.pdf> <images_dir/>`
2. Identify form fields visually
3. Use zoom refinement with ImageMagick crops for precise coordinates
4. Create fields.json using `image_width` and `image_height`
5. Validate: `python scripts/check_bounding_boxes.py fields.json`

## Step 2: Validate Before Filling

**Always validate bounding boxes before filling:**
`python scripts/check_bounding_boxes.py fields.json`

## Step 3: Fill the Form

`python scripts/fill_pdf_form_with_annotations.py <input.pdf> fields.json <output.pdf>`

## Step 4: Verify Output

```bash
python scripts/convert_pdf_to_images.py <output.pdf> <verify_images/>
```
