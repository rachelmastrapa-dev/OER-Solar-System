---
name: libretext-export
description: Use when exporting raw editor-source HTML for a chapter's sections from LibreTexts Workbench into this repo. Triggers on requests like "export chapter [name]", "pull the HTML for [chapter]", "sync [chapter] from libretext".
---

# LibreText Chapter Export

## Purpose
Pull the raw editor-source HTML (not rendered page text) for every section in a
LibreTexts Workbench chapter, and save it into this repo under `chapters/`,
mirroring the chapter/section structure. 

## Prerequisites
- Playwright MCP connected and logged into the LibreTexts/Conductor session
  (persistent browser profile — should already be logged in from setup).
- Read-only task. **Never click Save, Publish, Commit, or any write/edit
  control in the LibreText editor.** This tool only reads source HTML; it
  never modifies the live page. If a step seems to require confirming a
  change, stop and ask the user first.

## Editing Standards
The editings standards for this project are described in `$ROOT/guidelines/editing-standards.md`.  
- The `editing-standards.md` file contains brief descriptions of formatting standards.
- It also contains directions to other files that have more detailed descriptions of specific formatting standards.
- Always look in `editing-standards.md` first when looking for information about editing, formatting, or general guidance for this project, then follow the directions to other files when needed.
- If there is a rule that says to use editing standards, look for guidance in `editing-standards.md`.
- Check for any variable definitions in the section about variables in `editing-standards.md`. Variables are usually in the form `<VariableName>` but sometimes `[VariableName]` in the case of URLs submitted by the user

## Input
A single LibreTexts Table of Contents (TOC) URL for one chapter, e.g.:
`https://[library].libretexts.org/Workbench/[TextbookTitle]/[NN]%3A_[ChapterTitle]`

## Steps

1. **Discover section links**
   Navigate to the chapter TOC URL with Playwright. Read the page's sidebar/
   nested TOC tree and collect every sub-page link that belongs to this
   chapter (not sibling chapters). Record each link's display title and its
   position in the chapter (e.g. "12.3: Observing Black Holes").

2. **Determine the file path**
   - Create the chapter directory in the repository according to the section on chapter directory in `editing-standards.md`

3. **For each section link, extract the source HTML**
   - Navigate to the section page.
   - Open the page editor (the same control used in the earlier recon step).
   - Switch to Source/Code view.
   - Copy the raw HTML exactly as shown — do not clean, reformat, or
     summarize it.
   - Close/exit the editor without saving.

4. **Archive figure images (without touching the HTML)**
   - After capturing a section's raw HTML, scan it for every `<img>` tag
     and record its `src` (and, if present, any `data-*` lazy-load source
     attribute — check a real captured section first to see which one
     LibreText actually uses; don't assume).
   - before downloading images, check `chapters/extra-images` for the image.  If it is there don't bother downloading it. move the image to the the chapter images directory, rename the image based on , and update the manifest .
   - **Do not rewrite the `src` in the saved HTML file.** The saved section
     HTML must keep pointing at the original LibreTexts image URL exactly
     as exported — the local image copy is a backup, not a replacement.
   - For each distinct image URL in the section, fetch the image bytes
     using the same authenticated Playwright browser session (so it works
     even if the image host requires the login session), and save it to
     `chapters/<NN>-<Chapter-Title>/images/<ImageFileName>`. Create the image file name using guidelines in `image-file-name.md`.
   - If the same image URL appears in more than one section, download it
     once and reuse the local file for the manifest entries below rather
     than fetching it twice.
   - Append one row per image to `chapters/<NN>-<Chapter-Title>/images/manifest.csv`
     with columns: `local_filename, original_src_url, section, alt_text`.
     Create the manifest file with a header row if it doesn't exist yet.
     This is a plain provenance record, not a replacement for your formal
     attribution log — it just saves you from having to re-find each
     image's source URL later.
   - if the user has given instructions to overwrite
      - if an image is found in the local images directory, but is not connected to a figure in the chapter then move the image to `chapters/extra-images` and move that figures line in the chapter manifest to the manifest file in `chapters/extra-images`

5. **Write the files**

   Create directories as needed. Write each section's raw HTML to its file.
   Do not overwrite an existing file silently — if the file already exists,
   report the conflict and ask whether to overwrite. If all of the chapter content exists, ask if the chapter should be skipped.
    - Refer to the section titles section in `editing-standards.md` to create the names of the local files.
     - Also create a file and copy in the HTML for the TOC page for the chapter as section 00 with the title `Introduction`
     - Example: `chapters/12-Black-Holes/12.00-Introduction.html`
   - If a chapter or section number can't be determined cleanly from the
     page, ask the user rather than guessing.
   - overwrite instructions
     - if the user gives instructions to overwrite, then only update local files that are different from libretext, skip any files that are the same between libretext and the local file.

6. **Delete redundant files**
  If playright has left a lot of files, such as copies of the images, or copies of the html, in `.playwright-mcp/`, then delete all of the duplicate files in the playwright directory. Do **not** delete any html or image files in the chapters directory or subdirectory.

7. **Report back**
   After the run, list every file written (path only), any sections that
   failed to extract and why, and any chapter/section numbering the tool
   had to guess at.

## Logging

Append an entry to today's session file (`sessions/<date>-sessionNN.md`)
under **AI**, listing: chapter processed, files touched, number of images.

## Notes
- If the editor's Source-view control can't be found on a given page (site
  layout can vary slightly), stop on that page, ask the user for the click
  path once, and this skill file should be updated with what worked.
- This tool copies all HTML from the page, including figures.
- Using Claude in Chrome caused a lot of problems, while playwright went smoothly.  Avoid using Chrome in Chrome. Ask the user if you can't find playwright.