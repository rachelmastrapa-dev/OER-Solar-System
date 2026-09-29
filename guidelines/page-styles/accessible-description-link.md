# Accessible Description Link

The accessible description link is needed to link the figure caption to the accessible description on a separate page. It requires a submitted link.

## Accessible Description Link Format

Refer to the variables section in `editing-standards.md` for variable definitions.  Variables appear as `[Variable]` or `<Variable>`

- The accessible description link should look similar to this: `/Workbench/[TextbookTitle]/[NN]:_[ChapterTitle]/<N>.<SS>:_Accessible_Descriptions#Figure_<FigureNumber>_<FigureTitle>` 


### ASTR 4 Settings

For the astronomy 4 textbook, the textbook part of the link is:

TextbookTitle: DeAnza_-_ASTR4

There may be references to URLs including ASTR10.  They may be needed to recover accessible description text online. Or they may be included in an older example.  When creating new links, assume the textbook is astonomy 4. 


## Accesible Decription Link Guidelines 

- Add a `_` between empty spaces in the link
- Omit the figure number if not available.
- The figure number may appear as `\(\PageIndex{<i>}\)` in other parts of the figure html. Only use a numerical number in the accessible description link. It will either be a number similar to this: 4.8.1, or there will be no number at all.

## Examples

This figures do not actually exist in the repository, the are only examples.

Chapter 14, section 2, first figure
`<FigureNumber>`: 14.2.1
`<FigureTitle>`: Binary Black Hole

Accessible description link: `/Workbench/DeAnza_-_ASTR4/14:_Black_Holes/14.06:_Accessible_Descriptions#Figure_14.2.1_Binary_Black_Hole`

Chapter 2, section 4, third figure
`<FigureNumber>`: 2.4.3
`<FigureTitle>`: Interior of the Sun
Accessible description link: `/Workbench/DeAnza_-_ASTR4/02:A_Night_Sky_Navigation/2.10:_Accessible_Descriptions#Figure_2.4.3_Interior_of_the_Sun`