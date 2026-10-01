# Style for Caption Text

## Figure Caption Text

Each figure requires new caption text. Create the text following these guidelines in the given HTML format. Some examples are given below.
 
## Figure Caption Text Guidelines
When generating caption text, `<CaptionText>`, Claude should follow these guidelines:
- `<CaptionText>` should focus on the main learning objective of the figure.
- Use `[OriginalAltText]` and `[OriginalCaptionText]` and the image in the file named `<ImageFileName>` to create the new caption text.
  - If `[OriginalAltText]` has no value, is the name of an image file, or is random text, do not use it to create `<CaptionText>`.
- Do not repeat text verbatim between `<AltText>` and `<CaptionText>`. Some words may be the same, but `<CaptionText>` should have more details regarding the learning objective.
- `<CaptionText>` should be brief, one or two complete sentences.
- If the figure is an image, include the name of the telescope or spacecraft and the wavelength of light, e.g. observed, visible, X-ray, inrared, if available.
- If the figure has multiple subfigures: refer to them based on their type and labels. e.g. Image (a), Diagram (c)

# Examples

Examples of figure caption text (`<CaptionText>`) for figures in an OER astronomy textbook. Note that the image files for the examples are in the same directory as this file.  Normally, image files will be in a directory called images in the chapter directory. 

## Example 1

`[OriginalCaptionText]` is `Orion Nebula in visible and infrared.`
`[OriginalAltText]` has no value
Local Example File Name: OrionNebula.png

`<CaptionText>` is `The visible light in Image (a) of the Orion nebula reveals its structure, but infrared light in Image (b) can reveal significantly more details.`

## Example 2

`[OriginalCaptionText]` is `Hertzsprung-Russell diagram with protostars of different mass.`
`[OriginalAltText]` has no value
Local Example File Name: HRprotostar.png

`<CaptionText>` is `The tracks traced on the H‐R diagram by developing protostars demonstrate how the length of time they take to form decreases with mass.`

