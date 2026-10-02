# Accessible Description Link

The accessible description, `<AccessibleDescriptionLink>`, link is needed to link the figure caption to the accessible description on a separate page. It requires a submitted link.

## Accessible Description Link Format

Refer to the variables section in `editing-standards.md` for variable definitions.  Variables appear as `[Variable]` or `<Variable>`

- The accessible description, `<AccessibleDescriptionLink>`, link should look similar to this: `/Workbench/[TextbookTitle]/[NN]:_[ChapterTitle]/<N>.<AA>:_Accessible_Descriptions#Figure_<FigureNumber>_<FigureTitleURL>` 


## Accesible Decription Link Guidelines 

- Add a `_` between empty spaces in the link
- Omit the figure number if not available.
- The figure number may appear as `\(\PageIndex{<i>}\)` in other parts of the figure html. Only use a numerical number in the accessible description link. It will either be a number similar to this: 4.8.1, or there will be no number at all.

## Examples

This figures do not actually exist in the repository, the are only examples.

Chapter 14, section 2, first figure
`<FigureNumber>`: `14.2.1`
`<FigureTitleURL>`: `Binary_Black_Hole`

`<AccessibleDescriptionLink>` is  `/Workbench/DeAnza_-_ASTR4/14:_Black_Holes/14.06:_Accessible_Descriptions#Figure_14.2.1_Binary_Black_Hole`

Chapter 2, section 4, third figure
`<FigureNumber>`: 2.4.3
`<FigureTitleURL>`: `Interior_of_the Sun`
`<AccessibleDescriptionLink>` is `/Workbench/DeAnza_-_ASTR4/02:_Night_Sky_Navigation/2.10:_Accessible_Descriptions#Figure_2.4.3_Interior_of_the_Sun`