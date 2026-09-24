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
- Do **not** recurse into the chapter's `images/` subfolder or touch
  `manifest.csv`.
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

1. For the introduction page, the page similar to `<NN.SS>-<Section-Title-Slug>.html` edit the  
1. Locate a figure in the file, e.g it starts with `<figure>` and ends with `</figure>` and do the following:
    1. Check if the figure html already matches editing standards. If it does not go to step 2 `Use the figure html section...`. If it does meet standards then:
      1. Locate the accessible description by navigating to the URL for the accessible description using Playwright and copying the html for the figure.  Note that the figure number in the text at the URL will be incorrect. 
      2. Create the figure number by following the directions in the step below: 3. Identify the figure number.
      3. Create a new accessible description link by referring to the accessible description link section in `editing-standards.md`
      4. Update the figure html with the new accessible description link
      5. Confirm that the image for the figure is in `images/`
        - If it is not there look for a file with a matching title in `$ROOT/chapters/extra-images/` 
           - If it is there change the name of the file to match the chapter and section similar to `<NN.SS>-<FigureTitle>` and move it to `images/`
           - If it is not there ask the user for guidance
      6. Skip all of the steps until 12. `Write accessible description...`
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
    4. Locate the image file that is used for the figure.
    5. Create figure attribution
       - Refer to the Figure Attribution section in `editing-standards.md`
       - If there is a default attribution for the figure it's name will appear at the end of the figure caption text. Example: if it looks like this `<figcaption>Figure \(\PageIndex{1}\) : Doppler Effect. (a) A source, S, makes waves whose numbered crests (1, 2, 3, and 4) wash over a stationary observer. (Openstax Astronomy).</figcaption>` use the Openstax Astronomy default attribution.
         - In the file, find the row with matching figure title and use the given information to format an attribution according to editing standards.
    6. Create figure caption text
       - Refer to the figure caption text section in `editing-standards.md`
    7. Create the accessible description
       - Refer to the accessible description section in `editing-standards.md`
    8. Create the alternative text
       - Refer to the alternative text section in `editing-standards.md`
    9. Create the accessible description link
       - Refer to the accessible description link section in `editing-standards.md`
    10. Create the figure html
       - Refer to the figure html section in `editing-standards.md`
    11. Ovewrite the old figure html with the new html.
    12. Write accessible description to accessible description page. e.g. `$ROOT/chapters/<NN>-<Chapter-Title-Slug>/<NN.SS>-Accessible-Descriptions.html`
       - place the accessible description in a logical place according to figure number.
       - do not overwrite any accessible descriptions that are currently on the page
       - If there is already an accesible description on the page with the same figure number, ask the user for guidance
2. Once all figures are processed check `images/` for any unused images for this section
    1. Find any images in `images/` that have a name similar to `<NN.SS>-<FigureTitle>` where `<NN.SS>` matches the current chapter and section number but the figure title does not match any figures from the current section page
    2. Move the unused image to `$ROOT/chapters/extra-images/`
3. Remove any 


## Hard exclusions — never modify or remove, under any rule above

- Class attributes from header, list, or paragraph tags. e.g. `<li class="lt-phys-64811">`
- Anything not explicitly covered by rules 1–9 above 

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
under **AI**, listing: chapter processed, files touched, and total edit
counts per rule.

## After running

Remind the user:
- Review changes with `git diff` on the chapter folder before committing.