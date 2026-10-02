# Variables

A list of variables used for multiple skills. 
  - Variables are in the form `<Variable>` or `[]`
     - `Variable` describes the type of variable
     - The `<>` or `[]` surrounding the text represent the fact that it is a variable

## Textbook Title
- `[TextbookTitle]` is `DeAnza_-_ASTR4`

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

The general form of a section URL is `https://[library].libretexts.org/Workbench/[TextbookTitle]/[NN]%3A_[ChapterTitle]/[N].[SS]%3A_[SectionTitle]`
Example: `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy/1.01%3A_How_Science_Works`
- The `[SS]` variable is the section number.
   - If the number of the section is a single digit, there is a leading zero. 
   - In the Example `[SS]` is `01`
- The `[N]` variable is the chapter number with no leading 0 for single digit chapter numbers.
   - In the example `[N]` is `1`
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

### Sections

Within each chapter directory there are html files that have the content for the table of contents (TOC) and each page in the chapter.

Each section has a section number:
- The section number can be found by using the URL variable `[SS]`
- When creating local files, directories, creating a new URL, use the variable:
    - `<S>` is the section number with no leading 0 for single digit sections. Example: If `[SS]` is `01` then `<S>` is `1`
    - `<SS>` is the section number with a leading 0 for single digit section. Example: if `[SS]` is `01` then `<SS>` is `01`

`<SectionTitle>` is the title of the section in a chapter.
- To get the `<SectionTitle>`, replace the `_` in `[SectionTitle]` with `-`.
   - Example: for the URL `https://phys.libretexts.org/Workbench/De_Anza_-_ASTR10/01%3A_Introduction_to_Astronomy/1.01%3A_How_Science_Works` the `<SectionTitle>` is `How-Science-Works`

- `<AA>` is the section number (including a leading 0 for single digit section numbers) of the local file for the accessible description page which will vary between chapters. For any chapter number `<N>`, the local accessible description file will be `<N>.<AA>-Accessible-Descriptions.html`
- `<AA>` is used for reading the section number from the local file, not writing the original file.
 - Example: In Chapter 1 Introduction to Astronomy, the accessible description file is `1.07-Accessible-Descriptions.html` so `<AA>` is `07`

- `<KK>` is the section number (including a leading 0 for single digit section numbers) of the local file for the key terms page which will vary between chapters. For any chapter number `<N>`, the local key terms file will be `<N>.<KK>-Key-Terms.html`
- `<KK>` is used for reading the section number from the local file, not writing the original file.
 - Example: In Chapter 1 Introduction to Astronomy, the accessible description file is `1.06-Key-Terms.html` so `<KK>` is `06`


## Figure Title 

When reading the original figure HTML from the local file, it's general format will be:

`<figure><img alt="[OriginalAltText]" class="internal default" src="[OriginalSourceURL]" /> <figcaption>Figure \(\PageIndex{<i>}\) : [FigureTitle]. [OriginalCaptionText]. ([AttributionInfo])</a>.</figcaption> </figure>`

- `[FigureTitle]` is the title of a figure read from the original HTML in a local file.
  - Example: If the figure caption is `<figcaption>Figure \(\PageIndex{1}\) : Earth. Our home is unique in the Solar System, due to its liquid water surface and the presence of life. (<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>) <a href="/Workbench/De_Anza_-_ASTR10/02:_Night_Sky_Navigation/2.10:_Accessible_Descriptions#Figure_2.1.1_Earth" target="_blank" title="2.10: Accessible Descriptions">Accessible description of Figure \(\PageIndex{1}\)</a>.</figcaption>` the `[FigureTitle]` is `Earth`.

- `<FigureTitle>` is the title of the figure adapted to write into an image file name. 
  - `<FigureTitle>` is created by replacing the spaces in `[FigureTitle]` with a `-`.
  - Copy all other text as is, including special characters.
  - Example: If `[FigureTitle]` is `The Electromagnetic Spectrum`, then `<FigureTitle>` is `The-Electromagnetic-Spectrum`


## Figure or Table Index

Figures and tables are numbered using the pageindex function. For example, the second table on a page would be referered to as `Table \(\PageIndex{2}\)` and the 10th figure would be `Figure \(\PageIndex{10}\)`

`<i>` is the figure index or table index, which may appear as  `\(\PageIndex{<i>}\)` when the index is unknown

## Figure Number
- The figure number `<FigureNumber>` is in the format `<N>.<S>.<i>`
- Example: For the third figure of the 4th section page of chapter 13, then `<FigureNumber>` is 13.4.3.

## Image File Names
- `[OriginalSourceURL]` is the url for an image file read from the original HTML in a local file.
  - this value is saved in `manifest.csv` in the column for original_src_url
  - For an individual figure, `[OriginalSourceURL]` is the same in the original HTML and in the new HTML
- `<ImageFileName>` is the name of an image file.
 - The image file names begin with `<N>.<SS>-<FigureTitle>`
 - The file name should have an extension appropriate to an image file including, but not limited to .png or .jpg. If this is a Libretext project, note that the only accepted formats are .jpg, .png, and .gif. 
 - Example: For a jpg image in chapter 3 section 12, with a `<FigureTitle>` of `The-Electromagnetic-Spectrum` then `<ImageFileName>` is `3.12-The-Electromagnetic-Spectrum.jpg` 

## Alternative Text

- `[OriginalAltText]` is a string of alternative text read from the original figure html in a local file.
 - Sometimes there is no original alternative text so `[OriginalAltText]` has no value. Sometimes the text is just a file name or random text.
- `<AltText>` is the new alternative text for a figure generated in the format html skill and written into the new figure html.

## Caption Text
- `[OriginalCaptionText]` is the original caption text read from the original figure html in a local file.
- `<CaptionText>` is the new caption text generated in the format html skill and written into the new figure html.
 - `<CaptionText>` is a part of the overall figure caption, located between the title and the figure attribution.
- `[ImageCredit]` is the image credit read from the original figure html in a local file.
  - original figure html may or may not have an image credit.

## Figure Attributions
- `[AttributionInfo]` is the information needed to create the new figure attribution. It is read from the original figure html in a local file.
  - Sometimes there will be no attribution information. 
- `<FigureAttribution>` is the new figure attribution generated in the format html skill and written into the new figure html.
- `<LicenseURL>` is the URL of the license of a figure.
- `<License>` is the name of the license of a figure.
- `<AuthorURL>` is the URL of the author of a figure. 
 - Sometimes there will be no URL for an author. 
- `<Author>` is the name of the author of the figure. 
- `<FigureURL>` is the URL where the image file used in the figure can be found. 
- `<Source>` is the name of the repository, textbook, or other type of source where the figure is found.
- `[License]` is the name of the license read from `[AttributionInfo]`
- `[LicenseURL]` is the URL for the license read from `[AttributionInfo]`
- `[Author]` is the name of the author read from `[AttributionInfo]`
- `[AuthorURL]` is the URL for the author read from `[AttributionInfo]`
  - there may not be a value for `[AuthorURL]`
- `[FigureURL]` is the URL for the figure read from `[AttributionInfo]`
- `[Source]` is the name of the sources read from `[AttributionInfo]`

## Accessible Description Link
- `<AccessibleDescriptionLink>` is the link to the accessible description and defined in `page-styles/accessible-description-link.md`