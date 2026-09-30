---
name: format-figure
description: Format figure html for figures in an OER textbook, including caption text, alt-text, figure attribution, and accessible description. This skill is designed to streamline the process of editing figures for an Open Educational Resource (OER) astronomy textbook in Libretext. Since astronomy is a visual science, it is important to make the figures clear to the broadest audience possible. Triggers on "format figures in chapter X", "fix the figure html", "write accessible descriptions"
---

# Format Figure  

Apply a set of rules to every section HTML file in **one local chapter folder**. 

## Locating repo files
Before reading any repository-relative paths below, resolve the repo root:
`ROOT=$(git rev-parse --show-toplevel)`

Reference files as `$ROOT/guidelines/editing-standards.md`, 
`$ROOT/guidelines/page-styles/example-box.md`, etc.

## Prerequisites
- Playwright MCP connected and logged into the LibreTexts/Conductor session
  (persistent browser profile — should already be logged in from setup).
- Read-only task. **Never click Save, Publish, Commit, or any write/edit
  control in the LibreText editor.** This tool only reads source HTML; it
  never modifies the live page in Libretext. If a step seems to require confirming a
  change in Libretext, stop and ask the user first.

## Input

Ask which chapter to process if not specified, e.g.:

> "Which chapter folder should I edit? (e.g. `chapters/07-Black-Holes/`)"

## Precondition — clean working tree required

Before doing anything else, check `git status` on the target chapter folder.

- If there are **any uncommitted changes** in `$ROOT/chapters/<NN>-<ChapterTitle>/`,
  **stop immediately** and tell the user to commit first. Do not edit any files.
- Only proceed once the working tree for that folder is clean.

## Discovery

- List every `<<N>.<SS>-<SectionTitle>.html` file directly inside the
  given chapter folder.
- Do **not** recurse into the chapter's `images/` in search of section or html files, but do look there for image files and to update `manifest.csv`.
- If no matching files are found, say so and stop.

## Editing Standards
The editing standards for this project are described in `$ROOT/guidelines/editing-standards.md`.  
- The `editing-standards.md` file contains brief descriptions of formatting standards.
- It also contains directions to other files that have more detailed descriptions of specific formatting standards.
- Always look in `editing-standards.md` first when looking for information about editing, formatting, or general guidance for this project, then follow the directions to other files when needed.
- If there is a rule that says to use editing standards, look for guidance in `editing-standards.md`.
- Check for any variable definitions in the section about variables in `editing-standards.md`. Variables are usually in the form `<VariableName>` but sometimes `[VariableName]` in the case of URLs submitted by the user

## Per-file edit rules

Apply these, in order, to each file's HTML, skipping the files that include `Key-Terms` or `Accessible-Descriptions` in their file name. Read the file, apply all rules
in memory, if a judgment needs to be made, ask the user, otherwise complete tasks, then write the result back to the same path (overwrite in place). 

1. For the file matching the TOC file name, refer to TOC file name in `editing-standards.md`, there is no figure html to format, but there is a thumbnail attribution at the bottom of the page. Format and overwrite the thumbnail attribution according to the thumbnail attribution section in `editing-standards.md`
2. For each `<figure>` element, in document order, do the following:
   1. Check if the figure html already matches editing standards (refer to the figure html section in `editing-standards.md`). If it does not meet standards, go to step 2.2 `Use the figure html section...`. If it does meet standards then:
      1. Find the accessible description text locally or in Libretext:
         1. Identify the figure title by referring to the variables section in `editing-standards.md`.
         2. Find the URL for the accessible description link in the figure html by referring to the figure html  section in `editing-standards.md`. 
         3. Find the chapter title in the URL by referring to the variables section in `editing-standards.md`.
         4. Search in the file similar to  `<N>.<AA>-Accessible-Descriptions.html` in `$ROOT/chapters/<NN>-<ChapterTitle>/` for an accessible description with the same figure title and copy the html for that figure title. If there is no matching accessible description in the local file, then:
           1. Navigate to the accessible description link URL using Playwright. 
           2. Identify the appropriate accessible description on the page by matching the figure title
           3. Open the page editor.
           4. Switch to Source/Code view.
           5. Copy the raw HTML of the accessible description exactly as shown — do not clean, reformat, or summarize it.
           6. Close/exit the editor without saving.
      2. Create the figure number by following the directions in step 2.3 `Create the figure number` and update the accessible description with the new figure number.
      3. Create a new accessible description link by referring to the accessible description link section in `editing-standards.md`
      4. Update the figure html with the new accessible description link.
      5. Confirm that the image for the figure is in `images/`
        - If it is not there look for a file with a matching title in `$ROOT/chapters/extra-images/` 
           - If it is there, change the name of the file to match the chapter and section according to the image file names section  in `editing-standards.md` without changing the figure title or file extension and move it to `images/` and update `manifest.csv` in both locations
           - If it is not there ask the user for guidance
      6. Go to step  2.12. `Write accessible description...`
   2. Use the figure html section in editing standards to find values for `[OriginalAltText]` and `[OriginalCaptionText]`. 
   3. Create the figure number:
      1. Check that the figure index in `\(\PageIndex{<i>}\)` makes sense.  For example, going in order from the beginning of the page to the end of the page if the last figure had an index of 2, then the current figure should have an index of 3. Note that figures are numbered independently of tables.  
      2. Create the figure number using the figure number section in `editing-standards.md`
   4. Locate the local copy of the image file that is used for the figure html by searching for a file in `images/` that matches the chapter, section number, and figure title according to the image file names section  in `editing-standards.md`
   5. Create figure attribution
      - Refer to the Figure Attribution section in `editing-standards.md`
       - Always  VARIABLE
       - The default attribution for all figures is the Openstax Astronomy format found in the Figure Attribution section in `editing-standards.md`
          - if there is no attribution information, use Openstax Astronomy
          - If there are empty parentheses `()` at the end of the figure caption text, use Openstax Astronomy
       - Or, there might be a different default textbook such as Openstax Chemistry referenced in the Figure Attribution section in `editing-standards.md`. 
       - Or, there might be information for another source. Use the shorthand in `attribution-info.md` to decode and retrieve needed information to format the figure attribution.
       - If any information is missing, ask the user for guidance
          - exception: if there is no author link, do not ask the user for guidance.  Instead, format the attribution with no author link
   6. Create `<CaptionText>` by referring to the Figure Caption Text section in `editing-standards.md`
   7. Create the accessible description
       - check the accessible description page for an accessible description that matches the same figure title. 
         - confirm with user that the accessible description is correct
         - update the figure number for the accessible description and go to step 2.8  `Create the alternative text`
       - Refer to the accessible description section in `editing-standards.md`
   8. Create the alternative text
       - Refer to the alternative text section in `editing-standards.md`
       - Do not update the alt-text for the figure in `manifest.csv` in order to keep a record of the original alt-text
   9. Create the accessible description link
       - Refer to the accessible description link section in `editing-standards.md`
   10. Create the figure html
       - Refer to the figure html section in `editing-standards.md`
   11. Overwrite the old figure html with the new html.
   12. Write accessible description to accessible description page. e.g. `$ROOT/chapters/<NN>-<ChapterTitle>/<N>.<SS>-Accessible-Descriptions.html`
       - if there is no file matching the name, ask user for guidance
       - place the accessible description in a logical place according to figure number.
       - do not overwrite any accessible descriptions that are currently on the page
       - If there is already an accessible description on the page with the same figure number, ask the user for guidance
3. Once all figures are processed check `images/` for any unused images for this section
    1. Find any images in `images/` that have a figure title that does not match any of the figure titles processed in step 2 `For each `<figure>` element...`. Refer to the variables section in `editing-standards.md` to identify figure titles and image file names.
    2. **Ask user to confirm the move**.
    3. Move any unused images to `$ROOT/chapters/extra-images/` 
    4. Update `manifest.csv` in both locations
4. Remove any accessible descriptions that are not related to a figure in this section and has a figure number related to the section, again looking for any unmatched figure titles, similar to in step 3 `Once all figures are processed...`. **Ask user to approve deletion**.
5. Report the presence of any `<img>` tags outside a `<figure>` wrapper. Do **not** process them as figures.


## Hard exclusions — never modify or remove, under any rule above

- Class attributes from header, list, or paragraph tags. e.g. `<li class="lt-phys-64811">`
- Anything not explicitly covered by rules 1–5 above 

## Output

After processing each file, overwrite it in place and print a one-line
summary of what changed, and any  `<img>` tags outside a `<figure>` wrapper e.g.:

```
3.02-Stellar-Winds.html: 7 figures reformatted, 7 accessible descriptions written, 1 unused image moved.
```

After the whole chapter is done, print a chapter-level total across all
files and all rule types.

## Logging

Append an entry to today's session file (`sessions/<date>-sessionNN.md`)
under **AI**, listing: chapter processed, figure html edited, images moved, and accessible descriptions removed.

## After running

Remind the user:
- Review changes with `git diff` on the chapter folder before committing.