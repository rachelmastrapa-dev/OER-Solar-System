# Style for Thumbnail Attributions

Refer to the variables section in `editing-standards.md` for any variables.  Variables appear as `[Variable]` or `<Variable>`

## Thumbnail Attribution Format

Only present in the introduction (TOC) pages for chapters, located at the bottom. The attribution is for the thumbnail for the chapter. Since it is decorative, no accessible description is required. The main part of the text that needs to be formatted is the figure attribution, but check the rest of the text, making sure that Thumbnail is bold, there is a period after the thumbnail caption text, etc.

### HTML Format

`<p><strong>Thumbnail</strong>: Thumbnail caption text. (<a href="<LicenseURL>" target="_blank" title="<License>"><License>.</a>; <a href="<AuthorURL>" target="_blank" title="<Author>"><Author></a> via <a href="<FigureURL>" target="_blank" title="<Source>"><Source></a>)</p>`

#### Example HTML

`<p><strong>Thumbnail</strong>: The James Lick telescope at Lick Observatory, Mt. Hamilton, California. It is a 36 inch refractor. (<a href="https://creativecommons.org/licenses/by/2.0/deed.en" target="_blank" title="CC BY 2.0">CC BY 2.0</a>; <a href="https://www.flickr.com/people/23369083@N05" target="_blank" title="myyorgda">myyorgda</a> via <a href="https://commons.wikimedia.org/wiki/File:Lick_Observatory_Refractor.jpg" target="_blank" title="Wikimedia Commons">Wikimedia Commons</a>)</p>`

### Attribution information

- All information needed to format the attribution should be present on the TOC page. 
 - Follow the methods used in the Figure Attribution section of `editing-standards.md` to read the attribution information from the text on the TOC page, but only use the thumbnail format for writing the HTML to the file.
- if any needed information is not present, ask the user for guidance
