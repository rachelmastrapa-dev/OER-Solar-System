---
name: format-key-terms
description: Format the key terms for a chapter. This skill is designed to streamline the process of formatting key terms for an Open Educational Resource (OER) astronomy textbook in Libtetext. Triggers on "format key terms in chapter X".
---

# Format Key Terms

Apply a set of rules to every section HTML file in **one local chapter folder**. 

## Locating repo files
Before reading any repository-relative paths below, resolve the repo root:
`ROOT=$(git rev-parse --show-toplevel)`

Reference files as `$ROOT/guidelines/editing-standards.md`, 
`$ROOT/guidelines/page-styles/example-box.md`, etc.

## Input

Ask which chapter to process if not specified, e.g.:

> "Which chapter folder should I edit? (e.g. `chapters/07-Black-Holes/`)"

## Precondition — clean working tree required

Before doing anything else, check `git status` on the target chapter folder.

- If there are **any uncommitted changes** in `$ROOT/chapters/<NN>-<ChapterTitle>/`,
  **stop immediately** and tell the user to commit first. Do not edit any files.
- Only proceed once the working tree for that folder is clean.

## Discovery

- List every `<N>.<SS>-<SectionTitle>.html` file directly inside the
  given chapter folder.
- Do **not** recurse into the chapter's `images/` in search of section or html files, but do look there for image files and to update `manifest.csv`.
- If no matching files are found, say so and stop.

## Editing Standards
The editings standards for this project are described in `$ROOT/guidelines/editing-standards.md`.  
- The `editing-standards.md` file contains brief descriptions of formatting standards.
- It also contains directions to other files that have more detailed descriptions of specific formatting standards.
- Always look in `editing-standards.md` first when looking for information about editing, formatting, or general guidance for this project, then follow the directions to other files when needed.
- If there is a rule that says to use editing standards, look for guidance in `editing-standards.md`.
- Check for any variable definitions in the section about variables in `editing-standards.md`. 
- Only the first appearance of a term should have a link.

## Per-file edit rules

Apply these, in order, to each file's HTML. When searching for terms, skip the files with names that include `Key-Terms`, `Accessible-Descriptions` or `Introduction`. If a judgment needs to be made, ask the user, otherwise complete tasks, then write the result back to the same path (overwrite in place). 

1. Search for key terms by referring to the Find Key Term section in `editing-standards.md`

     2. For each key term, `[term]` found follow these steps.

        1. Find the value for `[definition]` in `<key-term-source>` by referring to the Find Definition section in `editing-standards.md`
        2. Format and write the `<key-term-def>` to the key terms page following instructions in the Key Terms Page in `editing-standards.md`
           - do not overwrite other terms on the key term page, write each `<key-term-def>` to a new line
        3. Format and write the `<key-terms-link>` in the original text, replacing `[key-term-text]` in the local html file by following the instructions in the Key Terms Link section in `editing-standards.md` 
  
2. Format the Key Terms Page
    - Refer to the Key Terms Page section in `editing-standards.md`
    - Ask the user for guidance if there is no key terms page, that is no file with a name that includes `Key-Terms`. 
    - If `<term-anchor>` for a term already exists on the page, don't add it again.
    - Make sure the page has an appropriate header at the top
    - Alphabetize the list of terms by term


## Hard exclusions — never modify or remove, under any rule above

- Class attributes from header, list, or paragraph tags. e.g. `<li class="lt-phys-64811">`
- Anything not explicitly covered by rules 1–2 above 

## Output

After processing each file, overwrite it in place and print a one-line
summary of what changed, e.g.:

```
3.02-Stellar-Winds.html: 5 key terms found and replaced with links, 5 terms and definitions added to key terms page.
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