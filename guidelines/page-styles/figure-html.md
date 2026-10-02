# Figure HTML

Refer to the variables section in `editing-standards.md` for any variables.  Variables appear as `[Variable]` or `<Variable>`

## Original Figure HTML

When reading the original figure HTML from the local file, it's general format will be:

`<figure><img alt="[OriginalAltText]" class="internal default" src="[OriginalSourceURL]" /> <figcaption>Figure \(\PageIndex{<i>}\) : [FigureTitle]. [OriginalCaptionText]. ([AttributionInfo]).</figcaption> </figure>`

Some figures will not have any alternative text. If there is no `alt=` in the `<img>` wrapper, then `[OriginalAltText]` has no value.

Some figures will not have any attribution information. Either the parentheses after `[OriginalCaptionText].` will be empty or there will be no parentheses at all. In both cases set  `[AttributionInfo]` to no value. 

### Image Credits

Some, but not all, orginal figure html has an image credit. It will be after `([AttributionInfo])` and start with `Credit:`.  In this case the original html will look like this:

`<figure><img alt="[OriginalAltText]" class="internal default" src="[OriginalSourceURL]" /> <figcaption>Figure \(\PageIndex{<i>}\) : [FigureTitle]. [OriginalCaptionText]. ([AttributionInfo]) [ImageCredit].</figcaption> </figure>`


## Figure HTML Format

The html format for the new figure html is:

`<figure><img alt="<AltText>. Details in caption." class="internal default" src="[OriginalSourceURL]" /> <figcaption>Figure \(\PageIndex{<i>}\) : [FigureTitle]. <CaptionText>. (<FigureAttribution>) <a href="<AccessibleDescriptionLink>" target="_blank" title="<N>.<AA>: Accessible Descriptions">Accessible description of Figure \(\PageIndex{<i>}\)</a>.</figcaption> </figure>`

# Figure HTML Guidelines

- When generating the new figure HTML,  confirm that both occurrances of `\(\PageIndex{<i>}\)` have the same value of the figure index, `<i>`. Example: If the figure index, `<i>`, is 5, both occurances should be `\(\PageIndex{5}\)`
- The figure index should be the same as the last digit of the figure number, `<FigureNumber>`.  Example: If `<FigureNumber>` is `2.3.1`, then both occurances `<i>` is `1`.

## Examples

## Example 1

- `<AltText>`is `Neutron Star RX J1856.5-3754 by Hubble Space Telescope`
- `[OriginalSourceURL]` is `/@api/deki/files/42859/figure-213-isolatedNeutronStar.jpg`
- `[FigureTitle]` is `Neutron Star RX J1856.5-3754`
- `<CaptionText>` is `This Hubble Space telescope image is the first direct observation of a neutron star, labeled with an arrow, in visible light.`
- `<FigureAttribution>` is `<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.nasa.gov/" target="_blank" title="Fred Walter (State University of New York at Stony Brook) and NASA/ESA">Fred Walter (State University of New York at Stony Brook) and NASA/ESA</a> via <a href="https://esahubble.org/images/opo9732a/" target="_blank" title="ESA Hubble">ESA Hubble</a>`
- `<AccessibleDescriptionLink>` is `/Workbench/De_Anza_-_ASTR10/13:_Stellar_Finale/13.08:_Accessible_Descriptions#Figure_13.4.1_Neutron_Star_RX_J1856.5-3754`

The new figure html is:

`<figure><img alt="Neutron Star RX J1856.5-3754 by Hubble Space Telescope. Details in caption." class="internal default" src="/@api/deki/files/42859/figure-213-isolatedNeutronStar.jpg" /><figcaption>Figure \(\PageIndex{1}\) : Neutron Star RX J1856.5.E2.88.923754. This Hubble Space telescope image is the first direct observation of a neutron star, labeled with an arrow, in visible light. (<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://www.nasa.gov/" target="_blank" title="Fred Walter (State University of New York at Stony Brook) and NASA/ESA">Fred Walter (State University of New York at Stony Brook) and NASA/ESA</a> via <a href="https://esahubble.org/images/opo9732a/" target="_blank" title="ESA Hubble">ESA Hubble</a>) <a href="/Workbench/De_Anza_-_ASTR10/13:_Stellar_Finale/13.08:_Accessible_Descriptions#Figure_13.4.1_Neutron_Star_RX_J1856.5.E2.88.923754" target="_blank" title="13.8: Accessible Descriptions">Accessible description of Figure \(\PageIndex{1}\)</a>.</figcaption></figure>`

## Example 2

- `<AltText>`is `SN 1006 in X-ray, infrared, and visible light`
- `[OriginalSourceURL]` is `/@api/deki/files/46059/7c6fd59f47b3a3d89cf431e8ba9d417f6d39356f`
- `[FigureTitle]` is `SN 1006`
- `<CaptionText>`  is `1000 years later, the remnant of SN 1006 can be detected with X-ray and radio observations`
- `<FigureAttribution>` is `<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>`
- `<AccessibleDescriptionLink>` is `/Workbench/De_Anza_-_ASTR10/13:_Stellar_Finale/13.08:_Accessible_Descriptions#Figure_13.3.1_SN_1006`

The html should be:

`<figure><img alt="SN 1006 in X-ray, infrared, and visible light. Details in caption." class="internal default" src="/@api/deki/files/46059/7c6fd59f47b3a3d89cf431e8ba9d417f6d39356f" /> <figcaption>Figure \(\PageIndex{1}\) : SN 1006. 1000 years later, the remnant of SN 1006 can be detected with X-ray and radio observations. (<a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" title="CC BY 4.0">CC BY 4.0</a>; <a href="https://openstax.org/books/astronomy-2e/pages/preface" target="_blank" title="Fraknoi, et al.">Fraknoi, et al.</a> via <a href="https://openstax.org/details/books/astronomy" target="_blank" title="Openstax Astronomy 2nd ed.">Openstax Astronomy 2nd ed.</a>) <a href="/Workbench/De_Anza_-_ASTR10/13:_Stellar_Finale/13.08:_Accessible_Descriptions#Figure_13.3.1_SN_1006" target="_blank" title="13.8: Accessible Descriptions">Accessible description of Figure \(\PageIndex{1}\)</a>.</figcaption> </figure>`
