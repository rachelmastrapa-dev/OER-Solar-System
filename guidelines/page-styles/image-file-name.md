# Image File Name

How to locate the image file that is connected to the figure html. 

Image files are located in `$ROOT/chapters/<NN>-<Chapter-Title-Slug>/images/`
The image file names begin with `<N>.<SS>-<FigureTitle>`
Where 
- `<N>` is the chapter number (no leading 0)
- `<SS>` is the section number (includes leading 0 for single digits)
- `<FigureTitle>` is the title of the figure.  The title of the figure is found in between the figure number 

The file name should have an extension appropriate to an image file including, but not limited to .png or .jpg. If this is a Libretext project, note that the only accepted formats are .jpg, .png, and .gif. 

Find the appropriate image based on the first part of the file name.  This image is used for generated alternative text, figure caption text, and the accessible description.

## Figure Title 

The figure title or `<FigureTitle>` is the text in the figure caption between the figure number, similar to `Figure \(\PageIndex{1}\)`, and a period.

 Example: If the figure caption is `<figcaption>Figure \(\PageIndex{1}\) : Earth. Our home is unique in the Solar System, due to its liquid water surface and the presence of life. (<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>) <a href="/Workbench/De_Anza_-_ASTR10/02:_Night_Sky_Navigation/2.10:_Accessible_Descriptions#Figure_2.1.1_Earth" target="_blank" title="2.10: Accessible Descriptions">Accessible description of Figure \(\PageIndex{1}\)</a>.</figcaption>` the `<FigureTitle>` is `Earth`.



