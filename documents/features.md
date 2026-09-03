# Features to Implement

- Always update table-of-contents when exporting from libretext

# Features to build in to this project

# general

- problem with not being able to write to session while running a skill that will run to the file - VS Codium problem?  get multiple files - annoying  end up closing file.  Make a separate AI session file?  

## New skills

- research
- searching for information in libretext and remixing??

## Changes and new features for old skills
- Reading sources information during export
  - automatic attribution codes in text
     - gather unique codes in classes
     - provide instructions for creating URL and finding actual URL
     - Need to keep default info for libretext sources in attributions-info, or make a new file auto-attributions?
   - references, text attributions, figures
     -  put information in text?  - can use codes in attribution info

- edit text
 - edit all equations, including in figures and tables

 - glossary scraper
   - put in policy for duplicate terms and same word multiple meanings
   - examples from Claude: Duplicate terms with identical/near-identical definitions across chapters (e.g. asteroid, comet, parallax, dark matter) were deduped to one entry. "focus" appears with two unrelated meanings (ellipse geometry vs. telescope optics) — split into focus (ellipse) and focus (telescope), matching the book's own disambiguation style (e.g. nucleus (of an atom) vs nucleus (of a comet)).
   - key terms
     - has to be done post final edit of text. 
     - change to highlighting key terms instead of making separate list. - scans for specific color highlight and searches master list for def 
     - OR just make a master list of words and have claude scan book and glossary list, and make key terms

- terminology
  - false color image

- guidelines
  - general
    - figures must be explained in text - must have educational purpose, not just decorative exception: chapter thumbnails, decorative images labelled as decorative in alt-text

Notes to organize
other stuff to get rid of: as we will see terminology

build tool to scan for topics and link to section in textbook

step one for solar system - load in pages from stellar that I can use.

add prescession of axis back in for Earth, and tides

Moon - figure for tip of orbit relative to Earth - exlipse season

terminology - use lowercase au

decadal survey Read
openstax skill fix - further exploration - need to clean up lists that have already been moved to an H2 header, run again?, format figure - format thumbnails??, when claude indexes figures, check manifest - need to read attribution info when downloading?

Future improvements - autologging of fig attributions, references, auto-attributions
using terminology guidelines and more specific editing styles, for quotes, parens, dashes, etc. simplify sentences