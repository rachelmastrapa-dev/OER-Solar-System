# Style for Figure Attribution

## Figure Attribution

In OER textbooks, figures must be attributed. Figure attributions are required to give the figure author credit. Figure attributions have a specific format in Libretext and includes links that need to be formatted in HTML.

## HTML Format

Figure attributions are rendered in text with the general format License; Author via Source with links to License Author and Source.

The HTML is: <a href="LicenseLink" target="_blank" title="License">License</a>; <a href="AuthorLink" target="_blank" title="Author">Author</a> via <a href="FigureLink" target="_blank" title="Source">Source</a>

The LicenseLink, License, AuthorLink, Author, FigureLink, and Source are required to format the figure attribution.

Read `attribution-info.md` to decode some of the information that is used regularly. 
Example: If the information looks like this: `Celestial Coordinates,Planisphere,pd,pdl,Antonio Zatta,https://en.wikipedia.org/wiki/Antonio_Zatta,wc,https://commons.wikimedia.org/wiki/File:1777_celestial_map_of_the_Northern_Hemisphere_by_Antionia_Zatta.jpg` use the information in `attribution-info.md` to make the information into `Celestial Coordinates,Planisphere,Public Domain,https://commons.wikimedia.org/wiki/Public_domain,Antonio Zatta,https://en.wikipedia.org/wiki/Antonio_Zatta,Wikimedia Commons,https://commons.wikimedia.org/wiki/File:1777_celestial_map_of_the_Northern_Hemisphere_by_Antionia_Zatta.jpg`


## Example

LicenseLink: https://creativecommons.org/licenses/by/4.0/

License: CC BY 4.0

AuthorLink: https://www.instagram.com/m.s.faghanpour.a/

Author: M. Sadegh Faghanpour

FigureLink: https://ase.exopla.net/index.php/Fil...mes_2025_s.jpg

Source: All Skies Encyclopedia

<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.instagram.com/m.s.faghanpour.a/" target="_blank" title="M. Sadegh Faghanpour">M. Sadegh Faghanpour</a> via <a href="https://ase.exopla.net/index.php/Fil...mes_2025_s.jpg" target="_blank" title="All Skies Encyclopedia">All Skies Encyclopedia</a>

This renders in text as:

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); [M. Sadegh Faghanpour](https://www.instagram.com/m.s.faghanpour.a/) via [All Skies Encyclopedia](https://ase.exopla.net/index.php/Fil...mes_2025_s.jpg)

## Default Attributions

There are some default formats that will be used. Use these default attributions when they are given in place of attribution information.

### Openstax Astronomy

Default attribution for Openstax Astronomy.  If there is no attribution information for a figure, or if there are empty partheses `()` after the figure caption text, use this attribution.

LicenseLink: https://creativecommons.org/licenses/by/4.0/

License: CC BY 4.0

AuthorLink: https://openstax.org/books/astronomy-2e/pages/preface

Author: Fraknoi, et al.

FigureLink: https://openstax.org/details/books/astronomy

<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>

This renders in text as:

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/); [Fraknoi, et al.](https://openstax.org/books/astronomy-2e/pages/preface) via [Openstax Astronomy 2nd ed.](https://openstax.org/details/books/astronomy)

### Openstax Chemistry

If the attribution information is (Openstax Chemistry)

<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://chem.libretexts.org/Bookshelves/General_Chemistry/Chemistry_2e_(OpenStax)/00%3A_Front_Matter/01%3A_TitlePage" target="_blank" title="Flowers, Theopold and Langley">Flowers, Theopold and Langley</a> via <a href="https://chem.libretexts.org/Bookshelves/General_Chemistry/Chemistry_2e_(OpenStax)" target="_blank" title="Openstax Chemistry 2nd ed.">Openstax Chemistry 2nd ed.</a>

### Intro Physics Park

If the attribution info is (Intro Physics Park)

<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.linkedin.com/in/bkpark" target="_blank" title="Andrew Park">Andrew Park</a> via <a href="https://phys.libretexts.org/Bookshelves/Conceptual_Physics/Introduction_to_Physics_(Park)" target="_blank" title="Introduction to Physics (Park)">Introduction to Physics (Park)</a>

### Chem1 Lower

<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.sfu.ca/chemistry/department/faculty-staff/profiles/emeritus-and-retired-faculty/quantumdot.html">Stephen Lower</a> via <a href="https://chem.libretexts.org/Bookshelves/General_Chemistry/Chem1_(Lower)" title="https://chem.libretexts.org/Bookshelves/General_Chemistry/Chem1_(Lower)">Chem1 Lower</a>
