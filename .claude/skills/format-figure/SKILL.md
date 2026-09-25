---
name: format-figure
description: Format figure html for figures in an OER textbook, including caption text, alt-text, figure attribution, and accessible description. This skill is designed to streamline the process of editing figures for an Open Educational Resource (OER) astronomy textbook in Libtetext. Since astronomy is a visual science, it is important to make the figures clear to the broadest audience possible.

---

# Format Figure  

Apply a set of rules to every section HTML file in **one local chapter folder**. 

## Locating repo files
Before reading any repository-relative paths below, resolve the repo root:
`ROOT=$(git rev-parse --show-toplevel)`

Reference files as `$ROOT/guidelines/editing-standards.md`, 
`$ROOT/guidelines/page-styles/example-box.md`, etc.

## Precondition — clean working tree required

Before doing anything else, check `git status` on the target chapter folder.

- If there are **any uncommitted changes** in `$ROOT/chapters/<NN>-<Chapter-Title-Slug>/`,
  **stop immediately** and tell the user to commit first. Do not edit any files.
- Only proceed once the working tree for that folder is clean.

## Input

Ask which chapter to process if not specified, e.g.:

> "Which chapter folder should I edit? (e.g. `chapters/07-Black-Holes/`)"

## Discovery

- List every `<NN.SS>-<Section-Title-Slug>.html` file directly inside the
  given chapter folder.
- Do **not** recurse into the chapter's `images/` in search of section or html files, but do look there for image files and to update `manifest.csv`.
- If no matching files are found, say so and stop.

## Editing Standards
The editings standards for this project are described in `$ROOT/guidelines/editing-standards.md`.  
- The `editing-standards.md` file contains brief descriptions of formatting standards.
- It also contains directions to other files that have more detailed descriptions of specific formatting standards.
- Always look in `editing-standards.md` first when looking for information about editing, formatting, or general guidance for this project, then follow the directions to other files when needed.
- If there is a rule that says to use editing standards, look for guidance in `editing-standards.md`.

## Per-file edit rules

Apply these, in order, to each file's HTML. Read the file, apply all rules
in memory, if a judgement needs to be made, ask the user, otherwise complete tasks, then write the result back to the same path (overwrite in place). 

1. For the introduction page, the page similar to `<NN.SS>-<Section-Title-Slug>.html`, there is no figure html to edit, but there is a thumbnail attribution at the bottom of the page. Format at overwrite the thumbnail attribution according to the thumbnail attribution section in `editing-standards.md`
2. Locate a figure in the file, e.g it starts with `<figure>` and ends with `</figure>` and do the following:
    1. Check if the figure html already matches editing standards. If it does not go to step 2.2 `Use the figure html section...`. If it does meet standards then:
      1. Locate the accessible description by navigating to the URL for the accessible description using Playwright and copying the html for the figure.  Note that the figure number in the text at the URL will be incorrect. 
      2. Create the figure number by following the directions in the step below: 3. Identify the figure number.
      3. Create a new accessible description link by referring to the accessible description link section in `editing-standards.md`
      4. Update the figure html with the new accessible description link
      5. Confirm that the image for the figure is in `images/`
        - If it is not there look for a file with a matching title in `$ROOT/chapters/extra-images/` 
           - If it is there change the name of the file to match the chapter and section according to guidelines in `image-file-name.md` without changing the figure title or file extension and move it to `images/` and update `manifest.csv` in both locations
           - If it is not there ask the user for guidance
      6. Go to step  2.12. `Write accessible description...`
    2. Use the figure html section in editing standards to locate the alt-text and figure caption in the figure html. Do **not** preserve the original alt-text or figure caption text in paragraph form.
    3. Identify the figure number.
       - Check that the figure index in `\(\PageIndex{1}\)` makes sense.  For example, going in order from the beginning of the page to the end of the page if the last figure had an index of 2, then the current figure should have an index of 3 
       - The figure number is in the format `chapter number.section number.figure index`
         - Example: For the third figure of the 4th section page of chapter 13, the figure number is 13.4.3
       - The chapter number and section number are in the name of the file `<NN.SS>-<Section-Title-Slug>.html` 
         - The chapter number is `NN` and the section number is `SS`
         - Drop the leading `0` for single digit chapters or sections  
            - Example: If the name of the file is `02.01-A-Tour-of-the-Universe`, the chapter number is 2 and the section number is 1.  
       - The figure index starts at 1 with the first figure on the page, and increases for each figure. That is the first figure has a figure index of 1, the second figure has a figure index of 2, etc.
       - For the third figure in `02.01-A-Tour-of-the-Universe` the figure number of 2.1.3
    4. Locate the local copy of the image file that is used for the figure html by searching for a file in `images/` that matches the chapter, section number, and figure title according to `image-file-name.md`
    5. Create figure attribution
      - Refer to the Figure Attribution section in `editing-standards.md`
       - Always create the attribution based on the provided information in parentheses at the end of the figure caption in the original figure html
       - The default attribution for all figures is the Openstax Astronomy format found in `figure-attribution.md`
          - if there is no attribution information, use Openstax Astronomy
          - If there are empty parentheses `()` at the end of the figure caption text, use Openstax Astronomy
       - Or, there might be a different default textbook referenced in `figure-attribution.md` found at the end of the figure caption text such as Openstax Chemistry
       - Or, there might be information for another source. Use the shorthand in `attribution-info.md` to decode and retrieve needed information to format the figure attribution.
       - If any information is missing, ask the user for guidance
          - exception: if there is no author link, do not ask the user for guidance.  Instead, format the attribution with no author link
    6. Create figure caption text
       - Refer to the figure caption text section in `editing-standards.md`
    7. Create the accessible description
       - check the accessible description page for an accessible description that matches the same figure title. 
         - confirm with user that the accessible description is correct
         - update the figure number for the accessible description and go to step 3.8  `Create the alternative text`
       - Refer to the accessible description section in `editing-standards.md`
    8. Create the alternative text
       - Refer to the alternative text section in `editing-standards.md`
    9. Create the accessible description link
       - Refer to the accessible description link section in `editing-standards.md`
    10. Create the figure html
       - Refer to the figure html section in `editing-standards.md`
    11. Ovewrite the old figure html with the new html.
    12. Write accessible description to accessible description page. e.g. `$ROOT/chapters/<NN>-<Chapter-Title-Slug>/<NN.SS>-Accessible-Descriptions.html`
       - if there is no file matching the name, ask user for guidance
       - place the accessible description in a logical place according to figure number.
       - do not overwrite any accessible descriptions that are currently on the page
       - If there is already an accessible description on the page with the same figure number, ask the user for guidance
3. Once all figures are processed check `images/` for any unused images for this section
    1. Find any images in `images/` that begin with `<NN.SS>-<FigureTitle>` where `<NN.SS>` matches the current chapter and section number but the figure title does not match any figures from the current section page
    2. Move the unused image to `$ROOT/chapters/extra-images/`
    3. Update `manifest.csv` in both locations
4. Remove any accessible descriptions that are not related to a figure in the chapter


## Hard exclusions — never modify or remove, under any rule above

- Class attributes from header, list, or paragraph tags. e.g. `<li class="lt-phys-64811">`
- Anything not explicitly covered by rules 1–4 above 

## Output

After processing each file, overwrite it in place and print a one-line
summary of what changed, e.g.:

```
3.02-Stellar-Winds.html:Number of figures found and html formatted. Number of unused images moved.
```

After the whole chapter is done, print a chapter-level total across all
files and all rule types.

## Logging

Append an entry to today's session file (`sessions/<date>-sessionNN.md`)
under **AI**, listing: chapter processed, figure html edited, and images moved accessible descriptions removed.

## After running

Remind the user:
- Review changes with `git diff` on the chapter folder before committing.