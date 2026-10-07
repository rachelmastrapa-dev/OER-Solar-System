# Find Definition

Find the definition for each key term.

## Instructions
- Check for variable definitions in `page-styles/variables.md`
- Search for the definition associated with a key term `[term]` in `<key-term-source>`
  - Ignore case when searching for the definition. Example: if `[term]` is `Star`, then a line in `<key-term-source>` that starts with `star` is a match
- Assign the found definition in the file to `[definition]`
  - Example: If the value for `[term]` is `black hole`, then search for the line in `<key-term-source>` that starts with `black hole,` and assign the text after the comma in `black hole,` to `[definition]`. In this case, the line in the file that starts with `black hole,` is `black hole,a region in spacetime where gravity is so strong that nothing—not even light—can escape` so `[definition]` is `a region in spacetime where gravity is so strong that nothing—not even light—can escape`
  - Note that the text in definitions may include commas, so always read all text after the first comma to the end of the line and assign it to definition
    - Example: If the line from the file is `black hole,a region in spacetime where gravity is so strong that nothing, not even light, can escape` then `[definition]` is `a region in spacetime where gravity is so strong that nothing, not even light, can escape`
  - In cases, where `[term]` is plural, and none of the lines in the file match the plural form, then use the definition associated with the singular form.
    - Example: If `[term]` is `black holes`, and none of the lines in `<key-term-source>` starts with `black hole` and use the associated definition
  - There may be multiple definitions for the same term. In this case, use the definition that matches the context of the text surrounding where `[term]` was found, use the associated definition and ask the user for confirmation.   

## Textbook Key Term Source

Different textbooks will have different file that has the master list of key terms. Change the variable here to use a different file. The file should be a .csv file formatted with the first line header: `term,definition`.

For ASTR 4 the Solar System

`<key-term-source>` is `$ROOT/chapters/solar-system-key-terms.csv`