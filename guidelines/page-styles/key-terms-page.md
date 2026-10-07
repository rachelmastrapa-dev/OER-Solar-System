# Key Terms Page

The section page that has the key terms for the chapter.

## Key Terms File

- The file for the key terms page is `<N>.<KK>-Key-Terms.html`
- Write every `<key-term-def>` to this file.

## Variables
- `<term-sing>` is the singular form of `[term]`
  - Example: If `[term]` is `stars` then `<term-sing>` is star
  - Note that some terms in astronomy have a plural form that ends in -ae. The plural form of supernova is supernovae. If `[term]` is `supernovae`, `<term-sing>` is `supernova`
  - **Exception** If the term is plural in `<key-term-source>`, then `<term-sing>` should be plural
   - Example if the term in `<key-term-source>` is `scissors` then `<key-term-source>` is `scissors`
- `<term-anchor>` is value of `<term-sing>` with the spaces replaced with `+`
  - Example: If `<term-sing>` is `event horizon` then `<term-anchor>` is `event+horizon`
  - remove acronyms Example: if `<term-sing>` is `cosmic microwave background (CMB)` then `<term-anchor>` is `cosmic+microwave+background`
- `<term-sing>` and `<term-anchor>` should also be formatted to fully lowercase. 
  - There are some exceptions for acronyms such as (CMB) Example: if `[term]` is `Cosmic microwave backround (CMB)` because it was at the beginning of a sentence, then `<term-sing>` is `cosmic microwave backround (CMB)` and `<term-anchor>` is `cosmic+microwave+background`

## Key Term HTML Format
- `<key-term-def>` is a single term and definition formatted for the key term page. 
- The standard format is:
`<li><a id="<term-anchor>" name="<term-anchor>"><strong><term-sing></strong></a>: [definition]</li>`

## Page HTML Format

This is the general HTML format with different values for `<key-term-def>`, e.g. terma, termb, termc, termd. The list should be alphabetized by term. 

<h2><chapter-title-space> Key Terms</h2>

<ul>
    <key-term-def> (terma)
    <key-term-def> (termb)
    <key-term-def> (termc)
    <key-term-def> (termd)
</ul>


## Example HTML 
<h2>Black Holes Key Terms</h2>

<ul>
    <li><a id="escape+velocity" name="escape+velocity"><strong>escape velocity</strong></a>: the minimum speed that must be achieved for a free, non-propelled object to escape from the gravitational influence of a massive body, i.e. to achieve an infinite distance from it</li>
    <li><a id="event+horizon" name="event+horizon"><strong>event horizon</strong></a>: the distance from a black hole where the escape velocity equals the speed of light, the fastest possible speed known, and within which nothing can escape. In this sense, the event horizon is a point of no return. See also: Schwarzschild radius</li>
    <li><a id="gravitational+wave" name="gravitational+wave"><strong>gravitational wave</strong></a>: a disturbance in the curvature of spacetime caused by changes in how matter is distributed; gravitational waves propagate at (or near) the speed of light</li>
    <li><a id="singularity" name="singularity"><strong>singularity</strong></a>: the point of zero volume and infinite density to which any object that becomes a black hole must collapse, according to the theory of general relativity</li>
</ul>