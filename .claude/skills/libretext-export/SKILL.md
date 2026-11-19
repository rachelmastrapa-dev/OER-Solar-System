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

## Locating repo files
Before reading any repository-relative paths below, resolve the repo root:
`ROOT=$(git rev-parse --show-toplevel)`

Reference files as `$ROOT/guidelines/editing-standards.md`, 
`$ROOT/guidelines/page-styles/example-box.md`, etc.

## Editing Standards
The editing standards for this project are described in `$ROOT/guidelines/editing-standards.md`.  
- The `editing-standards.md` file contains brief descriptions of formatting standards.
- It also contains directions to other files that have more detailed descriptions of specific formatting standards.
- Always look in `editing-standards.md` first when looking for information about editing, formatting, or general guidance for this project, then follow the directions to other files when needed.
- If there is a rule that says to use editing standards, look for guidance in `editing-standards.md`.
- Check for any variable definitions in the section about variables in `editing-standards.md`.
- When writing directories, file names, or the text in files, if there are any special characters, such as `%27`, `'`, `,`, `:`, `%3A`, copy them exactly as they are found. Example, if the orignal has `:` write `:` and if the orignal has `%3A` write `%3A`. Follow any variables and templates defined in guidelines that have special characters. 

## Playwright and Libretext
When accessing libretext, make sure that Playwright is logged in with the user's credentials.
 - Do not use anonymous access, i.e check that `Deki.UserName` is not `Anonymous`
 - If Playwright is not logged in to Libretext, ask user to log in.

## Input
A single LibreTexts Table of Contents (TOC) URL for one chapter, e.g.:
`https://[library].libretexts.org/Workbench/[TextbookTitle]/[NN]%3A_[ChapterTitle]`

### Overwrite Mode
If the user gives instructions to overwrite local files, follow instructions that are labelled overwrite mode.

## Steps

1. **Discover section links**
   Navigate to the chapter TOC URL with Playwright. Read the page's sidebar/
   nested TOC tree and collect every sub-page link that belongs to this
   chapter (not sibling chapters). Record each link's display title and its
   position in the chapter (e.g. "12.3: Observing Black Holes").

2. **Determine the file path**
   - Create the chapter directory in the repository according to the section on chapter directory in `editing-standards.md`

3. **For each section link, extract the source HTML** 
   - Report to user the methods that work best for this step and give and example of how to write it. 
   - Preferred method (read-only API, returns exactly the editor's Source view):
     - On the chapter TOC page (logged in), get page ids with
       `/@api/deki/pages/<chapterPageId>/subpages?dream.out.format=json`
       (chapter page id is `Deki.PageId`).
     - For the TOC page and each section, fetch the editor source in `browser_evaluate`:
       ```js
       const t = await (await fetch(`/@api/deki/pages/${id}/contents?mode=edit`, {credentials:'include'})).text();
       const html = new DOMParser().parseFromString(t,'application/xml').querySelector('body').textContent;
       ```
     - Do **not** add `format=xhtml` — the body then comes back as XML child
       elements and `textContent` strips all tags. Do not use
       `dream.out.format=json` for contents — it returns invalid JSON escapes.
     - Save the results with `browser_evaluate`'s `filename` parameter
       (e.g. `.playwright-mcp/chNN-source.json`, a JSON-encoded string), then
       write each section file from it with a script. Note:
       `browser_run_code_unsafe`'s `filename` parameter *loads code* from a
       file; it does not save output.
     - An empty `body` means the page is empty in Libretext; write an empty file and report it.
   - Fallback (if the API fails): navigate to the section page, open the page
     editor, switch to Source/Code view, copy the raw HTML exactly as shown,
     and close the editor without saving.
   - Copy the raw HTML exactly — do not clean, reformat, or summarize it.

4. **Archive figure images (without touching the HTML)**
   - After capturing a section's raw HTML, scan it for every `<img>` tag.
    - Confirm that the `<img>` tag is inside a `<figure>` wrapper. If it is not, report the line number of the image tag in step 7.
    - record the `src` of each `<img>` tag (and, if present, any `data-*` lazy-load source
     attribute — check a real captured section first to see which one
     LibreText actually uses; don't assume).
   - before downloading images, check `chapters/extra-images`:
      - Find the `<FigureTitle>` for the figure using the figure html surrounding the image tag and by referring to the Figure Title section in `editing-standards.md`
      - Search for any files in `chapters/extra-images` with a file name similar to `<FigureTitle>`.  
      - Ask the user for confirmation to use the local file. 
      - If the user confirms, move the image to the current chapter images directory, rename the image based on the current chapter and section following the section on image file names in `editing-standards.md`, and update the `manifest.csv` in both locations. 
      - If the user does not confirm (responds `no` or `download`), download the file.
   - **Do not rewrite the `src` in the saved HTML file.** The saved section
     HTML must keep pointing at the original LibreTexts image URL exactly
     as exported — the local image copy is a backup, not a replacement.
   - LibreText images use plain `src="/@api/deki/files/<id>/<name>"` (some
     also carry `data-media-type`; no lazy-load source attribute seen so far).
     These URLs redirect (302) to signed `files.mtstatic.com` URLs, so a
     `fetch()` inside the page fails with CORS. They have been public, so
     download with `curl -sL -o <file> -w '%{content_type}' https://[library].libretexts.org<src>`
     and choose the extension from the content type (jpeg → `.jpg`). If curl
     gets a login page or an error, fall back to the authenticated Playwright
     session (`page.request.get(url, {maxRedirects:0})` in
     `browser_run_code_unsafe` to get the signed `location` URL, then curl that).
   - For each distinct image URL in the section, fetch the image bytes and save it to
     `chapters/<NN>-<ChapterTitle>/images/<ImageFileName>`. Create the image file name using guidelines in the image file names section in `editing-standards.md`.
   - If the same image URL appears in more than one section, download it
     once and reuse the local file for the manifest entries below rather
     than fetching it twice.
   - Append one row per image to `chapters/<NN>-<ChapterTitle>/images/manifest.csv`
     with columns: `local_filename, original_src_url, section, alt_text`.
     - Create the manifest file with a header row if it doesn't exist yet.
     - For each image the line in the manifest is: `<ImageFileName>,[OriginalSourceURL],<N>.<SS>,[OriginalAltText]`
   - Overwrite Mode
     - After all images have been saved, check the `/images/` directory for unused images.
     - Unused images have file names that are not similar to the `<FigureTitle>` of any of the images that were processed. 
     - After identifying unused file, ask the user if they should be moved.
     - If user confirms moving the files, move the files to `chapters/extra-images` and update `manifest.csv` in both locations.

5. **Write the files**

   - Create directories as needed. Write each section's raw HTML to its file in the chapter directory.
   Do not overwrite an existing file silently — if the file already exists,
   report the conflict and ask whether to overwrite. If all of the chapter content exists, ask if the chapter should be skipped.
   - Refer to the section file name section in `editing-standards.md` to create the names of the local files in the chapter directory and copy in the html to the appropriate file.
   - Create a file and copy in the HTML for the TOC page referring to TOC file name section in `editing-standards.md`. 
   - If a chapter or section number can't be determined cleanly from the page, ask the user rather than guessing.
   - Overwrite Mode
      - Only update local files that are different from libretext
      - skip any files that are the same between libretext and the local file.

6. **Delete redundant files**
  If playwright has left a lot of files, such as copies of the images, or copies of the html, in `.playwright-mcp/`, then delete all of the duplicate files in the playwright directory. Do **not** delete any html or image files in the chapters directory or subdirectory.

7. **Report back**
   After the run, list every file written (path only), any sections that
   failed to extract and why, and any chapter/section numbering the tool
   had to guess at and the location of any `img` tags that are not inside a `<figure>` wrapper.

## Logging

Append an entry to today's session file (`sessions/<date>-sessionNN.md`)
under **AI**, listing: chapter processed, files touched, number of images. Also copy any post-completion questions or comments returned by Claude in the UI into a new subsection under **Notes**.

## Notes
- If the editor's Source-view control can't be found on a given page (site
  layout can vary slightly), stop on that page, ask the user for the click
  path once, and this skill file should be updated with what worked.
- This tool copies all HTML from the page, including figures.
- Using Claude in Chrome caused a lot of problems, while playwright went smoothly.  Avoid using Claude in Chrome. Ask the user if you can't find playwright.