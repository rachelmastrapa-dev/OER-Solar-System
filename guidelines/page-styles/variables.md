# Variables

A list of variables used for multiple skills. 
  - Variables are in the form `<Variable>`
     - `Variable` describes the type of variable
     - The `<>` surrounding the text represent the fact that it is a variable

## URL General Forms

User provides a URL for material in libretext. These are the general forms of different types of URLs
URL variables will have brackets `[]`
The workbench URLs are for the textbook editing in Libretext Conductor. 

## Textbook URL (Workbench)

The general form of a textbook URL is `https://[library].libretexts.org/Workbench/[TextbookTitle]/`
Example: `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10`

- The `[library]` variable represents the name of the textbook's library, a collection of textbooks, which are organized by topic. The `[library]` in the example is `phys` for physics.
- The `[TextbookTitle]` variable is the title of the textbook with `_` representing the spaces. In the example, `[TextbookTitle]` is `De_Anza_-_ASTR10`


### Chapter URL (Workbench)

The general form of a chapter URL is `https://[library].libretexts.org/Workbench/[TextbookTitle]/[NN]%3A_[ChapterTitle]`
Example: `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy`
- The `[NN]` variable is the chapter number. 
   - If the number of the chapter is a single digit, there is a leading zero. 
   - In the Example `[NN]` is `01`
- The `[ChapterTitle]` variable is the title of the chapter with `_` representing the spaces. In the example, `[ChapterTitle]` is `Introduction_to_Astronomy`

### Section URL (Workbench)

The general form of a chapter URL is `https://[library].libretexts.org/Workbench/[TextbookTitle]/[NN]%3A_[ChapterTitle]/[N].[SS]%3A_[SectionTitle]`
Example: `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy/1.01%3A_How_Science_Works`
- The `[SS]` variable is the section number.
   - If the number of the section is a single digit, there is a leading zero. 
   - In the Example `[SS]` is `01`
- The `[SectionTitle]` variable is the title of the section with `_` representing the spaces. In the example, `[SectionTitle]` is `How_Science_Works`


## Repository Textbook Files

The overall structure of the local directory of a textbook is a directory called chapters in the repository, Example: `$ROOT/chapters/`

### Chapters

Each chapter has a chapter number:
- The chapter number can be found by using the URL variable `[NN]`
- When creating local files, directories, creating a new URL, use these variables:
    - `<N>` is the chapter number with no leading 0 for single digit chapters. Example: If `[NN]` is `01` then `<N>` is `1`
    - `<NN>` is the chapter number with a leading 0 for single digit chapters. Example: if `[NN]` is `01` then `<NN>` is `01`

`<ChapterTitle>` is the title of the chapter in the format used to create the local directory for the chapter
- To get the `<ChapterTitle>` replace the `_` in `[ChapterTitle]` with `-`
   - Example: for the URL `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy`
   the `<ChapterTitle>` is `Introduction-to-Astronomy`

Each chapter has a directory in the repository: `chapters/<NN>-<ChapterTitle>`

## Sections

Within each chapter directory there are html files that have the content for the table of contents (TOC) and each page in the chapter.

Each section has a section number:
- The section number can be found by using the URL variable `[SS]`
- When creating local files, directories, creating a new URL, use the variable:
    - `<SS>` is the chapter number with a leading 0 for single digit chapters. Example: if `[SS]` is `01` then `<SS>` is `01`

`<SectionTitle>` is the title of the section in a chapter.
- To get the `<SectionTitle>`, replace the `_` in `[SectionTitle]` with `-`.
   - Example: for the URL `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy/1.01%3A_How_Science_Works` the `<Section-Title>` is `How-Science-Works`

## Figure Title 

The figure title or `<FigureTitle>` is the text in the figure caption between the figure number, similar to `Figure \(\PageIndex{1}\) <FigureTitle>.` It should be followed by the figure caption text.

 Example: If the figure caption is `<figcaption>Figure \(\PageIndex{1}\) : Earth. Our home is unique in the Solar System, due to its liquid water surface and the presence of life. (<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>) <a href="/Workbench/De_Anza_-_ASTR10/02:_Night_Sky_Navigation/2.10:_Accessible_Descriptions#Figure_2.1.1_Earth" target="_blank" title="2.10: Accessible Descriptions">Accessible description of Figure \(\PageIndex{1}\)</a>.</figcaption>` the `<FigureTitle>` is `Earth`.


## Image File Names

Image files are located in `$ROOT/chapters/<NN>-<ChapterTitle>/images/`
The image file names begin with `<N>.<SS>-<FigureTitle>`

Add a `-` for any space in `<FigureTitle>`.  

The file name should have an extension appropriate to an image file including, but not limited to .png or .jpg. If this is a Libretext project, note that the only accepted formats are .jpg, .png, and .gif. 

Example: For a jpg image in chapter 3 section 12, with a `<FigureTitle>` of `The Electromagnetic Spectrum` then the image file name will be `3.12-The-Electromagnetic-Spectrum.jpg`