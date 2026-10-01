# Style for Figure Attribution

## Figure Attribution

In OER textbooks, figures must be attributed. Figure attributions are required to give the figure author credit. Figure attributions have a specific format in Libretext and includes links that need to be formatted in HTML.

Refer to the variables section in `editing-standards.md` for any variables.  Variables appear as `[Variable]` or `<Variable>`

## HTML Format

Figure attributions are rendered in text with the general format
 `<License>; <Author> via <Source>`

with links to `<License>`, `<Author>`, and `<Source>`.

The HTML is: 

`<a href="<LicenseURL>" target="_blank" title="<License>"><License></a>; <a href="<AuthorURL>" target="_blank" title="<Author>"><Author></a> via <a href="<FigureURL>" target="_blank" title="<Source>"><Source></a>`

## Attribution Information

The information for the attribution, `[AttributionInfo]`, is read from the orginal figure html in a local file.

If there is no attribution information, or if `[AttributionInfo]` has no value, then use the default attribution for this textbook.
 - For ASTR 4 Solar System the default attribution is Openstax Astronomy.

The attribution information, `[AttributionInfo]`, may use shorthand that can be translated using `attribution-info.md`. 

The attribution information, `[AttributionInfo]`, may come in different formats.  
 1. It might already be in a format matching the HTML format section. If so, then set `<FigureAttribution>` to the value in `[AttributionInfo]`
 2. If the format is similar to:`[License][[LicenseURL]]; [Author][[AuthorURL]] via [Source][[FigureURL]]`
   - For each of these variables `[License]`,`[LicenseURL]`, `[Author]`, `[AuthorURL]`, `[Source]`, and `[FigureURL]` , check `attribution-info.md` and replace the value of the variable. If there are no shorthand values, use the read value for each variable. 
   - In some cases, the value the URL variables, `[License]`,`[LicenseURL]`, `[Author]`, `[AuthorURL]`, `[Source]`, and `[FigureURL]` has been formatted in a hyperlink, this is not consisted with the format in the HTML format section. In this case, find the URL and in the hyperlink text and reset the variable to just the URL. 
     - Example: if `[AuthorURL]` is `<a href="https://commons.wikimedia.org/wiki/User:Emekadecatalyst]" rel="freelink" title="https://commons.wikimedia.org/wiki/User:Emekadecatalyst]">https://commons.wikimedia.org/wiki/U...ekadecatalyst` set `[AuthorURL]` to `https://commons.wikimedia.org/wiki/User:Emekadecatalyst`
   - Example of `[LicenseURL]` is `cc0l` then set `[LicenseURL]` to `https://creativecommons.org/public-domain/cc0/`
   - Set the variables for the attribution based on the read values: `<License>` = `[License]`, `<LicenseURL>` = `[LicenseURL]`, `<Author>` = `[Author]`, `<AuthorURL>` = `[AuthorURL]`, `<Source>` = `[Source]` and `<FigureURL>` = `[FigureURL]`
   - Example: if `[AttributionInfo]` is:
    `C0[ccol]; Emeka Udenze[https://commons.wikimedia.org/wiki/User:Emekadecatalyst] via wc[https://commons.wikimedia.org/wiki/File:Temperature_Scales.png]` then 
    `<License>` is `CC0`
    `<LicenseURL>` is `https://creativecommons.org/public-domain/cc0/`
    `<Author>` is `Emeka Udenze`
    `<AuthorURL>` is `https://commons.wikimedia.org/wiki/User:Emekadecatalyst`
    `<Source>` is `Wikimedia Commons`
    `<FigureURL>` is `https://commons.wikimedia.org/wiki/File:Temperature_Scales.png`
 3. If the attribution information, `[AttributionInfo]`, has a combination shorthand and html matching the section on HTML format, then use a combination of steps 1. and 2. 
   - Example: if `[AttributionInfo]` is:
     `CC0[ccol]; Emeka Udenze[https://commons.wikimedia.org/wiki/User:Emekadecatalyst] via <a href="https://commons.wikimedia.org/wiki/File:Temperature_Scales.png" target="_blank">wc</a>` then 
    `<License>` is `CC0`
    `<LicenseURL>` is `https://creativecommons.org/public-domain/cc0/`
    `<Author>` is `Emeka Udenze`
    `<AuthorURL>` is `https://commons.wikimedia.org/wiki/User:Emekadecatalyst`
    `<Source>` is `Wikimedia Commons`
    `<FigureURL>` is `https://commons.wikimedia.org/wiki/File:Temperature_Scales.png`


## Example

`<LicenseURL>`: https://creativecommons.org/licenses/by/4.0/
`<License>`: CC BY 4.0
`<AuthorURL>`: https://www.instagram.com/m.s.faghanpour.a/
`<Author>`: M. Sadegh Faghanpour
`<FigureURL>`: https://ase.exopla.net/index.php/Fil...mes_2025_s.jpg
`<Source>`: All Skies Encyclopedia

`<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.instagram.com/m.s.faghanpour.a/" target="_blank" title="M. Sadegh Faghanpour">M. Sadegh Faghanpour</a> via <a href="https://ase.exopla.net/index.php/Fil...mes_2025_s.jpg" target="_blank" title="All Skies Encyclopedia">All Skies Encyclopedia</a>`

### No Author URL

If there is no URL for the author: 
- Set `<AuthorURL>` to have no value
- Format the attribution without a link for the author. 

Example: 

`<LicenseURL>`: https://creativecommons.org/licenses/by/4.0/
`<License>`: CC BY 4.0
`<AuthorURL>`:
`<Author>`: M. Sadegh Faghanpour
`<FigureURL>`: https://ase.exopla.net/index.php/Fil...mes_2025_s.jpg
`<Source>`: All Skies Encyclopedia
`<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; M. Sadegh Faghanpour via <a href="https://ase.exopla.net/index.php/Fil...mes_2025_s.jpg" target="_blank" title="All Skies Encyclopedia">All Skies Encyclopedia</a>`


## Default Attributions

There are some default formats that will be used. Use these default attributions when they are given in place of attribution information.

### Openstax Astronomy

Default attribution for Openstax Astronomy.  If there is no attribution information for a figure use this attribution.

`<LicenseURL>`: https://creativecommons.org/licenses/by/4.0/
`<License>`: CC BY 4.0
`<AuthorURL>`: https://openstax.org/books/astronomy-2e/pages/preface
`<Author>`: Fraknoi, et al.
`<FigureURL>`: https://openstax.org/details/books/astronomy
`<Source>`: Openstax Astronomy 2nd ed.

`<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>`

### Openstax Chemistry

If the attribution information is (Openstax Chemistry)

`<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://chem.libretexts.org/Bookshelves/General_Chemistry/Chemistry_2e_(OpenStax)/00%3A_Front_Matter/01%3A_TitlePage" target="_blank" title="Flowers, Theopold and Langley">Flowers, Theopold and Langley</a> via <a href="https://chem.libretexts.org/Bookshelves/General_Chemistry/Chemistry_2e_(OpenStax)" target="_blank" title="Openstax Chemistry 2nd ed.">Openstax Chemistry 2nd ed.</a>`

### Intro Physics Park

If the attribution info is (Intro Physics Park)

`<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.linkedin.com/in/bkpark" target="_blank" title="Andrew Park">Andrew Park</a> via <a href="https://phys.libretexts.org/Bookshelves/Conceptual_Physics/Introduction_to_Physics_(Park)" target="_blank" title="Introduction to Physics (Park)">Introduction to Physics (Park)</a>`

### Chem1 Lower

`<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.sfu.ca/chemistry/department/faculty-staff/profiles/emeritus-and-retired-faculty/quantumdot.html">Stephen Lower</a> via <a href="https://chem.libretexts.org/Bookshelves/General_Chemistry/Chem1_(Lower)"  target="_blank" title="Chem1 Lower">Chem1 Lower</a>`
