# Variables

A list of variables used for multiple skills. 
  - Variables are in the form `<Variable>`
     - `Variable` describes the type of variable
     - The `<>` surrounding the text represent the fact that it is a variable

The overall structure of the local directory a textbook is a directory called chapters in the repository, Example: `$ROOT/chapters/`

Each chapter has a chapter number:
- The chapter number can be found by using the URL supplied by the user.
   - The general form of the chapter URL is `https://[library].libretexts.org/Workbench/[Course]/[NN%3A_Chapter_Title]`
   - `NN` is the chapter number.
     - In the URL, single digit chapter numbers have a leading 0.
- `<N>` is the chapter number with no leading 0 for single digit chapters.
- `<NN>` is the chapter number with a leading 0 for single digit chapters.

`<Chapter-Title>` is the title of the chapter in the format used to create the local directory for the chapter
- The chapter title can be found by using the URL supplied by the user.
- The general form of the chapter URL is `https://[library].libretexts.org/Workbench/[Course]/[NN%3A_Chapter_Title]`
   - Use the text located in the same place in the URL as `Chapter_Name` and replace each `_` with `-` to create the text for `<Chapter-Title>`
   - Example: for the URL `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy`
   the `<Chapter-Title>` is `Introduction-to-Astronomy`

Each chapter has a directory in the repository: `chapters/<NN>-<Chapter-Title>`

Within each chapter directory there are html files that have the content for the table of contents (TOC) and each page in the chapter.

`<Section-Title>` is the title of the section in a chapter.
- The section title can be found using the URL for the section. 
   - The general form of the section URL is `https:[library].libretexts.org/Workbench/[Course]/[NN%3A_Chapter_Name]/[1.01%3A_How_Science_Works`
   - Example: for the URL `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy/1.01%3A_How_Science_Works` the `<Section-Title>` is `How-Science-Works`



Image files are located in `$ROOT/chapters/<NN>-<Chapter-Title-Slug>/images/`
The image file names begin with `<N>.<SS>-<FigureTitle>`
Where 
- `<N>` is the chapter number (no leading 0)
- `<SS>` is the section number (includes leading 0 for single digits)
- `<FigureTitle>` is the title of the figure.  The title of the figure is found in between the figure number 

The file name should have an extension appropriate to an image file including, but not limited to .png or .jpg. If this is a Libretext project, note that the only accepted formats are .jpg, .png, and .gif. 

Find the appropriate image based on the first part of the file name.  This image is used for generated alternative text, figure caption text, and the accessible description.

## Figure Title 

The figure title or `<FigureTitle>` is the text in the figure caption between the figure number, similar to `Figure \(\PageIndex{1}\)`, and a period.

 Example: If the figure caption is `<figcaption>Figure \(\PageIndex{1}\) : Earth. Our home is unique in the Solar System, due to its liquid water surface and the presence of life. (<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>) <a href="/Workbench/De_Anza_-_ASTR10/02:_Night_Sky_Navigation/2.10:_Accessible_Descriptions#Figure_2.1.1_Earth" target="_blank" title="2.10: Accessible Descriptions">Accessible description of Figure \(\PageIndex{1}\)</a>.</figcaption>` the `<FigureTitle>` is `Earth`.



