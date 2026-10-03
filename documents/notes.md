# Notes

### Claude: format-figure run on 00-Astronomy-Toolkit, errors and suggestions (2026-10-02)


**Errors found in the guidelines:**


7. `figure-html.md` Example 1 (line 46): the caption title shows `RX J1856.5.E2.88.923754` (URL-encoded). Only the link should be encoded; the visible title should be `RX J1856.5−3754`.
8. `accessible-description-link.md` line 30: the example `<FigureTitleURL>` is `Interior_of_the Sun` (missing `_`).
9. `variables.md` line 86: Key Terms example says "the accessible description file is `1.06-Key-Terms.html`". It should say key terms file.
10. `accessible-description.md` HTML format (lines 101–105): the nested `<ul>` is not inside an `<li>`, and there is a stray `</li>`.

### Claude review: libretext-export, format-figure, and variable definitions (2026-10-01)

Review only. No skill or guideline files were changed.

**Variables used in guidelines or skills but never defined in `variables.md`:**

| Variable | Where | Fix |
|---|---|---|
x| `[acc-desc-link]` | figure-html.md line 26 | rename to e.g. `<AccessibleDescriptionLink>` and define |
x| `[LicenseLink]`, `[AuthorLink]`, `[ImageLink]` | thumbnail-attributions.md line 9, chapter-page.md line 30 | use the defined `[LicenseURL]`, `[AuthorURL]`, `[FigureURL]` |
x| bare `LicenseLink`/`AuthorLink`/`ImageLink`/`License`/`Author`/`Source` | thumbnail-attributions.md line 17 (no brackets at all) | use `<LicenseURL>` etc. |
x| `LicenseLink`, `AuthorLink`, `FigureLink` | figure-html.md Example 2, lines 55-59 | rename to `LicenseURL`/`AuthorURL`/`FigureURL` |
x| `[Course]`, `[NN%3A_Front_Matter]` | export-book SKILL.md line 24 | use `[TextbookTitle]` (same thing) |

**Variable errors in other page-styles files:**

1. **figure-html.md:**
x   - Line 26: the link title uses `<N>.<SS>: Accessible Descriptions`. `<SS>` is the figure's own section, not the accessible-description page. The example shows `13.8`, so it should be the accessible-description section number (with no leading zero).
x   - Line 30 writes `\(\PageIndex{i}\)` instead of `<i>`.
x   - Lines 9 and 19 contain a stray `</a>` in the "original" format.
x   - Line 17 is missing a closing backtick after `([AttributionInfo])`.
2. **accessible-description-link.md:**
x   - Line 9 uses `<FigureTitle>`, which by definition is hyphenated (for file names), but the link needs underscores (line 24).
x   - The examples (lines 34 and 40) label the spaced title as `<FigureTitle>`; that's actually `[FigureTitle]`.
x   - The special-character encoding seen in figure-html Example 1 (`−` → `.E2.88.92`) is not documented.
3. **figure-attribution.md:**
x   - Line 38 has `C0[ccol]` and line 47 has `[ccol]`. The shorthand in attribution-info.md is `cc0`/`cc0l`; line 35 uses `cc0l` correctly.
x   - Line 33 calls all six variables "URL variables", but only three are URLs.
x4. **editing-standards.md line 121:** "Check for variable definitions `page-styles/...`" is missing "in".




Accessibility

In Example and other box elements, heading levels jump from Heading 5 (default page title) to Heading 4 (author’s first subheading) and then drop to Heading 6. Easiest fix would be to move those initial subheadings from Heading 4 to Heading 6 and leave all other subheads at that level.

None of the Key Terms pages begin with a Heading 2, so may not be accessible to some screen readers. Since students may want to review those pages, they need to be accessible to everyone.

Only one of the intro page Table of Contents has some page descriptions. These elements should be consistent throughout - either include page descriptions on all content pages, or leave them off.

As with other OER texts, the attribution lines at the bottom of each page often (but not always) include linked URLs. Best practice to meet ADA Title II is to link all URLs to descriptive text (yes, even in references - we’ve chatted about that).

I just noticed another pattern. At the bottom of most pages, the author includes a subheading (Examples and Exercises) above one or more Example and Exercise boxes. This is not ideal, as there is no page content - just those boxes - so navigating these pages will be a bit confusing if someone uses the Headings List shortcut in JAWS. But since these elements seem to always appear at the bottom of pages, I don’t think this will be a serious accessibility block. Folks should be able to listen to the content in sequence, even if a screen reader does vocalize those boxes last in the reading order. I’m noting this in my Recommended Improvements section and suggesting that the initial subheadings be removed throughout.




## Scratch

