# Coding Style Guide

This is my personal frontend coding style guide. It is a living document
and new ideas are always welcome. Please contribute.

## Table of contents

 * [General principles](#general-principles)
    * [Project](#project)
    * [File format](#file-format)
    * [Indenting and line length](#indenting-and-line-length)
 * [Third-party projects](#3rdparty)
 * [HTML](#html)
    * [HTTP content type](#html-content-type)
    * [Doctype](#doctype)
    * [Language](#language)
    * [Encoding](#encoding)
    * [Elements and Attributes](#elements-and-attributes)
    * [Indentation](#indentation)
    * [Layered semantic markup / principles](#semantics)
    * [Validation](#validation)
    * [Accessibility](#accessibility)
 * [CSS](#css)
    * [HTTP content type](#css-content-type)
    * [Format](#format)
    * [Declaration order](#declaration-order)
    * [Comments](#comments)
    * [Preprocessors](#preprocessors)
 * [JavaScript](#javascript)
 * [PHP](#php)
 * [License](#license)
 * [Sources](#sources)

<a name="general-principles"></a>
## General principles

All code in any code-base should look like a single person typed it, no
matter how many people contributed. Strictly enforce the agreed-upon
style. If in doubt when deciding upon a style, use existing, common
patterns.

<a name="project"></a>
### Project

 * Your project must have an .editorconfig file in your project’s root
   directory. Stick to the [one](https://github.com/Dreamseer/dotfiles/blob/master/.editorconfig)
   in this dotfiles repository, if possible.
 * Your project must have a .gitattributes file in your project’s root
   directory. Stick to the [one](https://github.com/Dreamseer/dotfiles/blob/master/.gitattributes)
   in this dotfiles repository, if possible.

<a name="file-format"></a>
### File format

Files must be stored as ASCII text and must use the UTF-8 character
encoding without BOM.

Line termination follows the Unix text file convention, thus lines must
end with a single linefeed (`LF`) character. Line feeds are
represented as ordinal `10`, or hexadecimal `0x0A`. Do not use carriage
returns (`CR`) like Macintosh computers do (`0x0D`) or the carriage
return/linefeed combination (`CRLF`) like Windows computers do (`0x0D`,
`0x0A`).

When saving files, manually remove extra lines at the end of all files,
so that unwanted space is not inserted. It is also a good habit to
ensure all trailing spaces are removed.

Tip: configure your editor to “show invisibles”. This will allow you to
eliminate end-of-line whitespace, eliminate unintended blank-line
whitespace, and avoid polluting commits.

Files must end with a new line at their end (`EOF`).

We prefer readability over file-size savings when it comes to
maintaining existing files. Plenty of whitespace is encouraged. There is
no need for any developer to purposefully compress HTML or CSS, nor
obfuscate JavaScript.

<a name="indenting-and-line-length"></a>
### Indenting and line length

[Tabs are superior](http://lea.verou.me/2012/01/why-tabs-are-clearly-superior/),
so use hard tabs to indent, not spaces. Proper nesting shall be
denoted by no more than a single tab for each level of depth.

Tabs in your text editor shall be visually equivalent to four spaces.

Never mix tabs and spaces. Code indented with a mixture of tabs and
spaces should be converted to using tabs exclusively.

Limit all lines to a maximum of 79 characters. There are still many
devices around that are limited to 80 character lines; plus, limiting
windows to 80 characters makes it possible to have several windows
side-by-side. The default wrapping on such devices disrupts the visual
structure of the code, making it more difficult to understand.
Therefore, please limit all lines to a maximum of 79 characters. For
flowing long blocks of text (docstrings or comments), limiting the
length to 72 characters is recommended.

<a name="3rdparty"></a>
## Third-party projects

When working on a third-party project, such as a Drupal module or a
jQuery plugin, always stick to the corresponding coding style guide if
the project will be published.

Some third-party coding style guides:

 * [jQuery’s Style Guides](http://contribute.jquery.org/style-guide/)
 * [Drupal Coding Standards](http://drupal.org/coding-standards)
 * [WordPress Coding Standards](http://make.wordpress.org/core/handbook/coding-standards/)
 * …

<a name="html"></a>
## HTML

<a name="html-content-type"></a>
### HTTP content type

Always use the `text/html` content type with a UTF-8 encoding:

	Content-Type: text/html; charset=utf-8

<a name="doctype"></a>
### Doctype

Always use the minimal, versionless doctype.

	<!DOCTYPE html>

<a name="language"></a>
### Language

Always define which language the page is written in.

	<html lang="de">

<a name="encoding"></a>
### Encoding

Always define the character encoding using the minimal charset `meta`
element. The encoding should be defined as early as possible.

	<meta charset="utf-8">

<a name="elements-and-attributes"></a>
### Elements and Attributes

All element and attribute names should be lowercase. Attribute values
should be quoted. Optional closing tags should be included. Self-closing
elements should not be closed. Optional attributes should be omitted.
Always include `html`, `head` and `body` tags.

 * No `type` or `language` attributes on `script` elements.
 * No `type` attribute on link or `style` elements.

```html
<script src="…"><script>
<script></script>
<link rel="stylesheet" href="…">
<style></style>
```

<a name="indentation"></a>
### Indentation

Do not indent inside `html`, `body`, `script`, or `style`. Indent inside
`head` and all other elements.

<a name="semantics"></a>
### Layered semantic markup / principles

 * Use semantic class/ID names and appropriate HTML elements for
   content as defined in
   [The Elements of HTML](http://developers.whatwg.org/semantics.html#semantics).
 * Do not use inline CSS or inline JavaScript.
 * Use Microformats and Microdata where possible.
 * Use dashes (not underscores) as a word delimiter in class/ID names.

<a name="validation"></a>
### Validation

All HTML documents should be verified against the W3C validator to
ensure that the markup is well formed. This in and of itself is not
directly indicative of good code, but it helps to weed out problems that
are able to be tested via automation. It is no substitute for manual
code review.

<a name="accessibility"></a>
### Accessibility

 * Documents should work without JavaScript enabled.
 * Documents should be accessible by screenreaders.
 * Use attributes provided by [WAI-ARIA](http://www.w3.org/TR/wai-aria/)
   to avoid accessibility issues for people using screenreaders or other
   devices.
 * Keep keyboard and touch navigation in mind, do not rely on mouse
   events only.
 * Follow the [WCAG2](http://www.w3.org/TR/WCAG20/#guidelines).

<a name="css"></a>
## CSS

<a name="css-content-type"></a>
### HTTP content type

Always use the `text/css` content type with a UTF-8 encoding:

	Content-Type: text/css; charset=utf-8

<a name="format"></a>
### Format

The chosen code format must ensure that code is: easy to read; easy to
clearly comment; minimizes the chance of accidentally introducing
errors; and results in useful diffs and blames.

 * Use one discrete selector per line in multi-selector rulesets.
 * Include a single space before the opening brace of a ruleset.
 * Include one declaration per line in a declaration block.
 * Use one level of indentation for each declaration.
 * Include a single space after the colon of a declaration.
 * Use lowercase and shorthand hex values, e.g., `#aaa`.
 * Use single quotes consistently, e.g., `content: ''`.
 * Quote attribute values in selectors, e.g., `input[type='checkbox']`.
 * Where allowed, avoid specifying units for zero-values, e.g.,
   `margin: 0`.
 * Include a space before each comma in multi-selector rulesets.
 * Include a space after each comma in comma-separated property or
   function values.
 * Include a semi-colon at the end of the last declaration in a
   declaration block.
 * Place the closing brace of a ruleset in the same column as the first
   character of the ruleset.
 * Separate each ruleset by a blank line.

```css
.selector-1 ,
.selector-2 ,
.selector-3[type='text'] {
	display: block;
	-webkit-box-sizing: border-box;
	-moz-box-sizing: border-box;
	box-sizing: border-box;
	font-family: FreeSans, Arial, sans-serif;
	color: #333;
	background: #fff;
	background: linear-gradient(#fff, rgba(0, 0, 0, .8));
}

.selector-a ,
.selector-b {
	padding: 10px;
}
```

<a name="declaration-order"></a>
### Declaration order

If declarations are to be consistently ordered, it should be in
accordance with a single, simple principle. My preference is for
structurally important properties (e.g. display, positioning and box
behavior) to be declared prior to all others. Avoid alphabetical
ordering as it separates related properties.

```css
.selector {
	/* display and flow */
	display: value;
	visibility: value;
	float: value;
	clear: value;
	/* positioning */
	position: value;
	top: value;
	right: value;
	bottom: value;
	left: value;
	z-index: value;
	/* box behavior */
	transform: value;
	box-shadow: value;
	box-sizing: value;
	box-orient: value;
	box-align: value;
	box-direction: value;
	box-pack: value;
	box-lines: value;
	box-line-progression: value;
	box-flex: value;
	box-ordinal-group: value;
	/* dimensions */
	min-width: value;
	max-width: value;
	width: value;
	min-height: value;
	max-height: value;
	height: value;
	clip: value;
	overflow-x: value;
	overflow-y: value;
	overflow: value;
	/* margins, padding, borders and outlines */
	margin-top: value;
	margin-right: value;
	margin-bottom: value;
	margin-left: value;
	margin: value;
	padding-top: value;
	padding-right: value;
	padding-bottom: value;
	padding-left: value;
	padding: value;
	border-top-width: value;
	border-top-style: value;
	border-top-color: value;
	border-top: value;
	border-right-width: value;
	border-right-style: value;
	border-right-color: value;
	border-right: value;
	border-bottom-width: value;
	border-bottom-style: value;
	border-bottom-color: value;
	border-bottom: value;
	border-left-width: value;
	border-left-style: value;
	border-left-color: value;
	border-left: value;
	border-width: value;
	border-style: value;
	border-color: value;
	border: value;
	border-top-left-radius: value;
	border-top-right-radius: value;
	border-bottom-right-radius: value;
	border-bottom-left-radius: value;
	border-radius: value;
	border-image-source: value;
	border-image-slice: value;
	border-image-width: value;
	border-image-outset: value;
	border-image-repeat: value;
	border-image: value;
	border-collapse: value;
	border-spacing: value;
	outline-top-width: value;
	outline-top-style: value;
	outline-top-color: value;
	outline-top: value;
	outline-right-width: value;
	outline-right-style: value;
	outline-right-color: value;
	outline-right: value;
	outline-bottom-width: value;
	outline-bottom-style: value;
	outline-bottom-color: value;
	outline-bottom: value;
	outline-left-width: value;
	outline-left-style: value;
	outline-left-color: value;
	outline-left: value;
	outline-width: value;
	outline-style: value;
	outline-color: value;
	outline: value;
	outline-top-left-radius: value;
	outline-top-right-radius: value;
	outline-bottom-right-radius: value;
	outline-bottom-left-radius: value;
	outline-radius: value;
	outline-offset: value;
	/* grid */
	grid-columns: value;
	grid-rows: value;
	grid-column-align: value;
	grid-row-align: value;
	grid-column-span: value;
	grid-row-span: value;
	grid-layer: value;
	/* columns */
	column-width: value;
	column-count: value;
	columns: value;
	column-rule-width: value;
	column-rule-style: value;
	column-rule-color: value;
	column-rule: value;
	column-gap: value;
	column-span: value;
	column-fill: value;
	break-before: value;
	break-after: value;
	break-inside: value;
	/* colors and backgrounds */
	color: value;
	background-color: value;
	background-image: value;
	background-repeat: value;
	background-attachment: value;
	background-position: value;
	background-size: value;
	background-clip: value;
	background-origin: value;
	background: value;
	opacity: value;
	/* typography */
	font-family: value;
	font-size: value;
	font-size-adjust: value;
	font-weight: value;
	font-style: value;
	font-variant: value;
	font-stretch: value;
	font: value;
	line-height: value;
	letter-spacing: value;
	word-spacing: value;
	vertical-align: value;
	text-align: value;
	text-decoration: value;
	text-indent: value;
	text-transform: value;
	text-shadow: value;
	text-rendering: value;
	white-space: value;
	word-wrap: value;
	hyphens: value;
	orphans: value;
	widows: value;
	/* text direction */
	direction: value;
	unicode-bidi: value;
	/* lists */
	list-style-type: value;
	list-style-position: value;
	list-style-image: value;
	list-style: value;
	/* tables */
	table-layout: value;
	caption-side: value;
	empty-cells: value;
	/* images */
	image-rendering: value;
	image-region: value;
	/* generated content */
	content: value;
	quotes: value;
	counter-increment: value;
	counter-reset: value;
	/* animation */
	animation-delay: value;
	animation-direction: value;
	animation-duration: value;
	animation-fill-mode: value;
	animation-iteration-count: value;
	animation-name: value;
	animation-play-state: value;
	animation-timing-function: value;
	animation: value;
	/* general appearance */
	cursor: value;
	pointer-events: value;
	transition-property: value;
	transition-duration: value;
	transition-timing-function: value;
	transition-delay: value;
	transition: value;
	appearance: value;
	resize: value;
	filter: value;
	zoom: value;
	/* printing appearance */
	size: value;
	page-break-before: value;
	page-break-after: value;
	page-break-inside: value;
}
```

<a name="comments"></a>
### Comments

Well commented code is extremely important. Take time to describe
components, how they work, their limitations, and the way they are
constructed. Do not leave others in the team guessing as to the purpose
of uncommon or non-obvious code.

Comment style should be simple and consistent within a single code base.

* Place comments on a new line above their subject.
* Make liberal use of comments to break CSS code into discrete sections.
* Use “sentence case” comments and consistent text indentation.
* Use [KSS](https://github.com/kneath/kss/blob/master/SPEC.md) for
  documenting rulesets. KSS attempts to provide a methodology for
  writing maintainable, documented CSS within a team. Specifically, KSS
  is a documentation specification and styleguide format.

```css
/* =====================================================================
   Section comment block
   ================================================================== */

/* Sub-section comment block
   ================================================================== */

/*
A button suitable for giving stars to someone.

:hover             - Subtle hover highlight.
.stars-given       - A highlight indicating you’ve already given a star.
.stars-given:hover - Subtle hover highlight on top of given stars.
.disabled          - Dims the button to indicate it cannot be used.

Styleguide 2.1.3.
*/
a.button.star {
	…
}
a.button.star.stars-given {
	/* Basic comment */
	…
}
a.button.star.disabled {
	…
}
```

<a name="preprocessors"></a>
### Preprocessors

Different CSS preprocessors have different features, functionality, and
syntax. Your conventions should be extended to accommodate the
particularities of any preprocessor in use. The following guidelines are
in reference to [LESS](http://lesscss.org/), [Sass](http://sass-lang.com/),
and [Stylus](http://learnboost.github.io/stylus/).

 * Use a CSS-like syntax, like SCSS in Sass or the non-omitting syntax
   in Stylus.
 * Limit nesting to 1 level deep. Reassess any nesting more than 2
   levels deep. This prevents overly-specific CSS selectors.
 * Avoid large numbers of nested rules. Break them up when readability
   starts to be affected. Preference to avoid nesting that spreads over
   more than 20 lines.
 * Always place `@extend` statements on the first lines of a declaration
   block.
 * Where possible, put mixins at the end of a declaration block.
 * Consider prefixing custom functions with `x-` or another namespace.
   This helps to avoid any potential to confuse your function with a
   native CSS function, or to clash with functions from libraries.

<a name="javascript"></a>
## JavaScript

tbd.

<a name="php"></a>
## PHP

tbd.

<a name="license"></a>
## License

This Coding Style Guide is licensed under the [Creative Commons
Attribution 3.0 Unported License](http://creativecommons.org/licenses/by/3.0/).
This applies to all documents in this repository.

<a name="sources"></a>
## Sources

 * [WordPress Coding Standards](http://make.wordpress.org/core/handbook/coding-standards/)
 * [Fellowship Code Standards](http://developer.fellowshipone.com/patterns/code.php)
 * [jQuery’s Style Guides](http://contribute.jquery.org/style-guide/)
 * [Idiomatic CSS](https://github.com/necolas/idiomatic-css)
 * [Idiomatic JS](https://github.com/rwldrn/idiomatic.js/)
 * [PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md)
 * [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)
 * [PEAR Coding Standards](http://pear.php.net/manual/en/standards.php)
 * [PEP 8 — Style Guide for Python Code](http://www.python.org/dev/peps/pep-0008/)
