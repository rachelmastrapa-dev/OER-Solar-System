# Shortened Editing for "Easy Chapters"

## Whole Chapter - Manual in Libretext

1. Back up pages to ASTR 4 backup - done for all chapters
2. Chapter structure and pages
  - go over content of pages and delete or relocate extra, rearrange order
  - Delete extra matrerial & notes 
  - leave manual attributions until after pasting material
3. Copy in material from sources 
  - copy in key terms
  - go through material and paste where useful 
  - check auto -attributions
4. TOC - Check for summaries and remove
5. remove blue highlights
6. Figures title and ()
7. Change numbering and titles of exercises and examples
8. Commit Changes in Conductor



- add new figures 
  - put all attribution information in caption in (), unless openstax astronomy leave empty ()
  - use shorthand - update attribution info
    - make hyperlinks, no bare URLs or they get truncated
  - accessible description info
    - put long captions from original source in alt text for now
    - write `No description` at the end of figure caption if it does not need one.  Note that it needs to be described in the text


## Libretext export - Claude/AI Passive

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

- human checks diffs

## Key Terms
5. Key terms
  - in html search for term
   -  find in text and highlight - <span class="mt-bgcolor-2ecc71">term</span>
   - put all definitions in solar-system-key-terms.csv

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


## Edit HTML - Claude/AI + consult Human

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


## Edit Content - Human  

- main chapter page
  - reduce to 10 or fewer learning objectives (no learning objectives on sub-pages) 
  - check thumbnail
  - write introduction

- All pages
  - check for highlighted text e74c3c  red
  - Headers - proper structure
  - edit text for clarity
  
      
- Figures
  - contextualize figures and tables. - write descriptions in text or in alternative text

- Further Exploration
   - check for full link
   - contextualize further exploration links

- check references and attribtions

<!-->  - class attributes - connecting to location default attribute?  page attribute? < -->

## Format Figures - Claude AI

**User: Commit and close all files**

- format thumbnail attribution on intro page
- Increment Figure indices- double checks that figure indices make sense
- Accesible Descriptions
  - retreive online accessible description
  - delete extras
  - use if already present
- alt-text
- Figure attribution
 - set default figure caption to openstax astronomy in figure-attributions.md. and skill
 - shifted to attribution info in place
- Figure HTML
 - use formatted html without redoing 
- look for figure in extra images or ask for help
- move unused figures to extra-images


## Format Sources - Claude/AI Passive

**User: Commit and close all files**

References, manual attributions - per section page?, need style files for each

### new features

- adjust to just reading locally
- may be already formatted - change to default format
- use individual links for authors if available, otherwise make all text one link
- when indexing, note that tables and figures are indexed independently
- modify APA format to link URLs ??? get answer from Kim, be ready to fix everything again with a new skill

## Format Key Terms - Claude AI Passive

**User: Commit and close all files**

- Key terms
  - Locate terms by highlight: <span class="mt-bgcolor-2ecc71">term</span>
  - Locate definition in solar-system-key-terms.csv
  - Format terms and definitions and add to key terms page
   - Write Key Terms in H2 at top of page  see key-terms-page
  - Format links for term and replace highlighted text


## Final Review - Claude/AI - interactive

**User: Commit and close all files**

make suggestions - search for outer material??. accesibility
1. Make minor grammar and spelling errors.
2. Ask about more complicated errors


## Final Check- Human
- Manually paste each page and check for functionality. - key terms and accessible descriptions first!!  
- Commit changes in Conductor 
- Update progress log.
- Notify Jyothsna that it is done. 
- When you make corrections, update progress again. 

## Reviews
- check Caitlin and Jyothsnas - link here?
- wait for accessibility review?

## Full Textbook in LibreTexts

- License Restacker

## Jyothsna
- Main chapter page 
  - start with H2 Introduction and brief summary
- Remove all section summaries
- Change name of last page to Accessible Descriptions

