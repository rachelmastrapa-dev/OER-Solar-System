# Editing Instructions
## Starting Day - Human
1. Create new issue in git
    1. Editing for the day with date
    2. List goals for the day
2. Move issue to working in project, assign self, create branch
3. Create new session file for today in VSCodium
4. Starting Claude Code
    1. Open a terminal command prompt 
    2. Navigate to repo cd Crap\OERAI\git_repos\OER-Solar-System
    3. Type claude
    4. Exit when not using
5. **Commit often! Keep careful session notes!**

## Ending Day - Human
1. List questions/goals for tomorrow in session file
2. Save and close all files, commit, merge branches.

## Textbook Planning - Human

- decide on page and chapter layouts - create guideline files
- Create table of contents for book
- create detailed list of topics
- organize topics into table of contents  - or review list while editing


## Whole Chapter - Manual in Libretext

- Edit chapter page
  - check size of thumbnail image
  - Confirm chapter and section titles from TOC
  - check chapter TOC for summaries and remove

- Edit other pages 
  - Delete Extra material
  - Delete extra figures

- add titles to figures
- add new figures 
  - put all attribution information in caption in (), unless openstax astronomy leave empty ()
  - use shorthand - update attribution info
  - put long captions in alt text for now

- Commit changes in Conductor

## Libretext export - Claude/AI Passive

### Actions
- single chapter
- copies html from libretext pages to local files
   - preserves chapter structure, titles, section titles and numbering
- makes local copies of images
   - creates a manifest file info for each image
   - stores images for entire chapter in one folder for each chapter called images
- don't number images file names yet, because there will be future figures - make them all figure
  - label with section number and title
- overwriting 
  - only update new html and images
  - move unused images to chapters/extra-images

## Review Chapter Import - Human

- Edit chapter page
  - at bottom of page write thumbnail and paste in all thumbnail attribution info and caption

- Edit pages
 - sub sections
   - create properly nested subsections according to guidelines
   - copy subsections into TOC
   - move materials into proper section 
   
 - review topic list to make sure they are all included
 - check **extras.md**

 - mix more information
   - find and copy in info from Solar System Sources - Libretext or copy locally?
   - add figures 
     - add to libretext and copy html into local file 
     - save local copy of image in images dir
     - - put long captions in alt text for now


<figure><img alt="alt-text" class="default" src="https://query.libretexts.org/@api/deki/files/1990/Placeholder_Image.jpg" style="width: 214px; height: 169px;" />
<figcaption>Figure \(\PageIndex{1}\): Title. Copy and Paste Caption here. (License[LicenseLink]; Author [Authorlink] via <a href="figurelink" target="_blank">source</a>)</figcaption>
</figure>


- figures  
   - check against files, manifest
   - put all attribution information in caption in (), unless openstax astronomy leave empty ()
- references - put in all information in References section
- text attribution - put in all information in Attributions section

**update guidelines to recongnize new data sources, read code, update attribution info**


## Clean HTML - Claude/AI Passive
- Read .claude/clean-html/SKILL.md
- Summary, removing italics, bold, spans, figure ## set to default, etc. remove <p>&nbsp;</p> 
- delete empty paragraphs and lists
- make a guidelines for clean html
find and replace  &times; x 
&amp; & 
&rsquo; '
&minus; -
&ldquo; nothing
&rdquo; nothing
&mdash; nothing
&ndash; -
&micro; μ
&deg; °


## Edit HTML - Claude/AI user interactions

**User: Commit and close all files**
Ask for help!
1. Move all learning objectives to main chapter page. Create learning objectives box and introduction header.
2. Change all equations from MathML to Latex.
3. Move all link to learning items to Further Exploration. Move unboxed text to a box. Combine boxes. links with target="_blank"
4. Put example and exercises in boxes and move to the correct section.
5. replace current key terms with key term color <span class="mt-bgcolor-2ecc71">term</span>
6. delete footnotes - move text to where it was referenced and delete all footnote html - make exceptions for tables or figures
7. Terminology
8.  IDEA and ADA flagging


## Chapter Review - Manual   

- main chapter page
  - reduce to 10 or fewer learning objectives (no learning objectives on sub-pages)
- Content
  - edit text for clarity

- highlight or make links for 
      
- Figures
  - contextualize figures and tables.
  - check indices
  - check for figure or table references in text and confirm indices
- key terms 
   -  find in text and highlight - <span class="mt-bgcolor-2ecc71">term</span>
- Further Exploration
   - check for full link
   - contextualize further exploration links



<!-->  - class attributes - connecting to location default attribute?  page attribute? < -->

## Format Figures - Claude AI

**User: Commit and close all files**

- Increment Figure indices??
- Accesible Descriptions
- alt-text
- Figure attribution
- Figure HTML

### New features

- correcting for moved or missing images
  - finding accessible description using link? - or ask for page? ask - user will tell you which chapter it is in
  - find image in another chapter??  or ask? look in extra-images
  - if a figure in images for a chapter is not used, move it to extra-images at chapter level - don't duplicate images
  - if figure html is already done, skip except for putting accessible description in correct place and changing link

- first scan all figures in entire chapter and check against manifest and image names - update figures that have moved, list figures that are no longer present and move to chapter wide images folder /moved-images

 - format thumbnail - create separate guideline file
 - set default figure caption to openstax astronomy. 
 - update format figures to get rid of extra accessible descriptions,  and renumber if overwriting
Format figure - skips figures with proper formatted html and an accessible description


## Format Sources - Claude/AI Passive

**User: Commit and close all files**

References, manual attributions - per section page?, need style files for each

### new features

- adjust to just reading locally
- may be already formatted - change to default format
- use individual links for authors if available, otherwise make all text one link
- when indexing, note that tables and figures are indexed independently

## Format Key Terms - Claude AI Passive

**User: Commit and close all files**

- Key terms
  - Check against key terms list from Openstax and create list for chapter
  - Format terms and definitions and add to key terms page
  - Find first occurance of term in chapter paragraph text, not figure, table, or heading 
     - format text to bold and link
     - handle whether in plural or singular in paragraph text.

## new features 
   - key terms
     - has to be done post final edit of text. 
     - change to highlighting key terms instead of making separate list. - scans for specific color highlight and searches master list for def 
     - OR just make a master list of words and have claude scan book and glossary list, and make key terms
     also deleting of re-highlighting key terms - refinding first occurance, deleting ones that aren't there

put key terms in key term page un edited

## Final Review - Claude/AI - interactive

**User: Commit and close all files**

make suggestions - search for outer material??. accesibility
1. Make minor grammar and spelling errors.
2. Ask about more complicated errors


## Final Check- Manual
- Manually paste each page and check for functionality.
  - check size of thumbnail image  for main chapter page   
- Commit changes in Conductor 
- Update progress log.
- Notify Jyothsna that it is done. 
- When you make corrections, update progress again. 

## Reviews
- check Caitling and Jyothsnas - link here?
- wait for accessibility review?

## Jyothsna
- Main chapter page 
  - start with H2 Introduction and brief summary
- Remove all section summaries
- Change name of last page to Accessible Descriptions

