# Find Key Term

Find the key terms in section pages.

# Instructions
- Check for variable definitions in `page-styles/variables.md`
- Search for text in the file that is highlighted in green. Example: `<span class="mt-bgcolor-2ecc71">star</span>`
  - do not change or remove any highlighted text that uses any color other than green (`mt-bgcolor-2ecc71`)
  - if the same term is highlighted multiple times, only use the first occurrance and remove highlighting from subsequent occurrances.
- Set `[key-term-text]` to the highlighted text. Example: `[key-term-text]` is `<span class="mt-bgcolor-2ecc71">star</span>`
- Set `[term]` to the highlighted word or words in `[key-term-text]` Example: If `[key-term-text]` is  `<span class="mt-bgcolor-2ecc71">black hole</span>` then `[term]` is `black hole`
