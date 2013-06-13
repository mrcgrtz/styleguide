# Dreamseer’s Indisputable Coding Style

**This is my personal frontend coding style guide.** It is a living
document and —despite its name— it is disputable, new ideas are always
welcome. I really do not intend to impose my style preferences on other
people’s code or projects; if an existing common style exists, it should
be respected.

The keywords “MUST”, MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”,
“SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this
document are to be interpreted as described in
[RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).

## Table of contents

 * [General principles](#general-principles)
    * [Project defaults](#project-defaults)
    * [File format](#file-format)
    * [Indenting and line length](#indenting-and-line-length)
 * [Third-party projects](#3rdparty)
 * [HTML](#html)
    * [HTTP content type](#html-content-type)
    * [Doctype](#doctype)
    * [Language](#language)
    * [Encoding](#encoding)
    * [Elements and attributes](#elements-and-attributes)
    * [Indentation](#indentation)
    * [Layered semantic markup / principles](#semantics)
    * [Validation](#validation)
    * [Accessibility](#accessibility)
 * [CSS](#css)
    * [HTTP content type](#css-content-type)
    * [Ruleset format](#css-format)
       * [Link rulesets](#link-rulesets)
    * [Property order](#property-order)
    * [Properties with vendor prefixes](#vendor-prefixes)
    * [Comments](#css-comments)
    * [Preprocessors](#preprocessors)
 * [JavaScript](#javascript)
    * [HTTP content type](#js-content-type)
    * [Format](#js-format)
    * [Comments](#js-comments)
    * [Modules](#modules)
 * [PHP](#php)
    * [PSR-1 and PSR-2](#php-standards)
    * [Optional exceptions from PSR-1 and PSR-2](#exceptions)
 * [License](#license)
 * [Sources](#sources)

<a name="general-principles"></a>
## General principles

All code in any code-base SHOULD look like a single person typed it, no
matter how many people contributed. Strictly enforce the agreed-upon
style. If in doubt when deciding upon a style, use existing, common
patterns.

<a name="project-defaults"></a>
### Project defaults

Every project MUST have an `.editorconfig` file in its root directory.

```ìni
# This file is for unifying the coding style for different editors
# and IDEs. EditorConfig is awesome: http://EditorConfig.org

########################################################################
# Top-most EditorConfig file
########################################################################
root = true

########################################################################
# All files
########################################################################
[*]
# indent using tabs
indent_style = tab
indent_size = tab
tab_width = 4
# Unix-style newlines with a newline ending every file
end_of_line = LF
insert_final_newline = true
# use UTF-8 without BOM
charset = utf-8
# remove any trailing whitespace
trim_trailing_whitespace = true
```

If Git is used as a VCS, a project MUST have a `.gitattributes` file in
its root directory, too.

```text
# Automatically normalize line endings for all text-based files
* text=auto
```

<a name="file-format"></a>
### File format

Files MUST be stored as ASCII text and MUST use the UTF-8 character
encoding without BOM.

Line termination follows the Unix text file convention, thus lines MUST
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

Files MUST end with a new line at their end (`EOF`).

I prefer readability over file-size savings when it comes to
maintaining existing files. Plenty of whitespace is encouraged. There is
no need for any developer to purposefully compress HTML or CSS, nor
obfuscate JavaScript.

<a name="indenting-and-line-length"></a>
### Indenting and line length

[Tabs are superior](http://lea.verou.me/2012/01/why-tabs-are-clearly-superior/),
so use hard tabs to indent, not spaces. Proper nesting SHALL be
denoted by no more than a single tab for each level of depth.

Tabs in your text editor SHOULD be visually equivalent to four spaces.

Never mix tabs and spaces. Code indented with a mixture of tabs and
spaces SHOULD be converted to using tabs exclusively.

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

When working on a to-be-published third-party project, such as a Drupal
module or a jQuery plugin, always stick to the corresponding coding
style guide.

Some third-party coding style guides:

 * [jQuery’s Style Guides](http://contribute.jquery.org/style-guide/)
 * [Drupal Coding Standards](http://drupal.org/coding-standards)
 * [WordPress Coding Standards](http://make.wordpress.org/core/handbook/coding-standards/)
 * …

<a name="html"></a>
## HTML

<a name="html-content-type"></a>
### HTTP content type

You MUST use the `text/html` content type with a UTF-8 encoding:

```
Content-Type: text/html; charset=utf-8
```

<a name="doctype"></a>
### Doctype

You MUST use the minimal, versionless doctype.

```html
<!DOCTYPE html>
```

<a name="language"></a>
### Language

You MUST define which language the page is written in.

```html
<html lang="de">
```

<a name="encoding"></a>
### Encoding

You MUST define the character encoding using the minimal charset `META`
element. The encoding SHOULD be defined as early as possible.

```html
<meta charset="utf-8">
```

<a name="elements-and-attributes"></a>
### Elements and attributes

All element and attribute names SHOULD be lowercase. Attribute values
SHOULD be double-quoted. Optional closing tags SHOULD be included.
Self-closing elements SHOULD NOT be closed. Optional attributes SHOULD
be omitted. Always include `HTML`, `HEAD` and `BODY` tags.

 * No `type` or `language` attributes on `SCRIPT` elements.
 * No `type` attribute on `LINK` or `STYLE` elements.

```html
<script src="..."></script>
<script></script>
<link rel="stylesheet" href="...">
<style></style>
```

<a name="indentation"></a>
### Indentation

You MUST NOT indent inside `HTML`, `BODY`, `SCRIPT`, or `STYLE`. Indent
inside `HEAD` and all other block elements.

List items and all table elements (like `CAPTION`, `THEAD`, `TFOOT`,
`TBODY`, `TR`, `TH`, and `TD`) SHOULD stay on their own line and be
indented, too.

<a name="semantics"></a>
### Layered semantic markup / principles

 * Use semantic class/ID names and appropriate HTML elements for
   content as defined in
   [The Elements of HTML](http://developers.whatwg.org/semantics.html#semantics).
 * Actual `P` elements MUST be used for paragraph delimiters as opposed
   to multiple `BR` elements.
 * `DL` (definition lists) and `BLOCKQUOTE` SHOULD be used when
   appropriate.
 * Items in list form SHOULD always be housed in a `UL`, `OL`, or `DL`,
   never a set of `DIV` or `P` elements.
 * Inline CSS or inline JavaScript MUST NOT be used.
 * Dashes (not underscores) MUST be used as word delimiters in class/ID
   names.
 * Tables SHOULD NOT be used for page layout.
 * `THEAD`, `TBODY`, and `TH` elements (and `scope` attribute) SHOULD be
   used when appropriate.
 * Use `LABEL` elements to label each form field, the `for` attribute
   SHOULD associate itself with the form field, so users can click the
   labels. `cursor: pointer;` on the label is wise, as well.
 * [Microformats](http://microformats.org/) and Microdata SHOULD be used
   where appropriate, specifically
   [hCard](http://microformats.org/wiki/hcard) and
   [adr](http://microformats.org/wiki/adr).
 * Always use the appropriate case for headers and titles. Do not use
   all caps or all lowercase titles in markup, instead apply the CSS
   property `text-transform`.

<a name="validation"></a>
### Validation

All HTML documents SHOULD be verified against the
[W3C validator](http://validator.w3.org/nu/) to ensure that the markup
is well formed. This in and of itself is not directly indicative of good
code, but it helps to weed out problems that are able to be tested via
automation. It is no substitute for manual code review.

<a name="accessibility"></a>
### Accessibility

 * Documents SHOULD work without JavaScript enabled.
 * Documents SHOULD be accessible by screenreaders.
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

You MUST use the `text/css` content type with a UTF-8 encoding:

```
Content-Type: text/css; charset=utf-8
```

<a name="css-format"></a>
### Ruleset format

The chosen code format must ensure that code is: easy to read; easy to
clearly comment; minimizes the chance of accidentally introducing
errors; and results in useful diffs and blames.

 * Use one discrete selector per line in multi-selector rulesets.
 * Include a space before each comma in multi-selector rulesets.
 * Include a single space before the opening brace of a ruleset.
 * Include one declaration per line in a declaration block.
 * Use one level of indentation for each declaration.
 * Include no space before and a single space after the colon of a
   declaration.
 * Where allowed, you MUST avoid specifying units for zero-values, e.g.,
   `margin: 0`.
 * Line heights SHOULD also be unit-less, unless necessary to be defined
   as a specific pixel value. This is
   [more](http://meyerweb.com/eric/thoughts/2006/02/08/unitless-line-heights/)
   than just a style convention, but is worth mentioning here.
 * You MUST NOT use a leading zero for decimal values.
 * You MUST NOT pad parentheses with spaces.
 * Multiple comma-separated values for one property SHOULD be separated
   by either a space or a newline, including within `rgba()`. Newlines
   SHOULD be used for lengthier multi-part values such as those for
   shorthand properties like `box-shadow` and `text-shadow`. Each
   subsequent value after the first should then be on a new line,
   indented to the same level as the selector and then spaced over to
   left-align with the previous value.
 * Include no space before and a space after each comma in
   comma-separated property or function values.
 * Hex values MUST be lowercase and shorthand, e.g., `#aaa`.
 * Always use single quotes for attribute selectors or values, e.g.,
   `input[type='checkbox'] { content: ''; }`. You MUST NOT mix quotes.
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

<a name="link-rulesets"></a>
#### Link rulesets

For any `A` element, you MUST NOT use the `A` selector only. Instead
you MUST use these pseudo-classes in
[this order](http://meyerweb.com/eric/css/link-specificity.html) for
specifity reasons:

```css
a:link ,
a:visited ,
a:hover ,
a:focus ,
a:active {
	color: #46c;
	background: #fff;
}

a:link ,
a:visited {
	text-decoration: none;
}

a:hover ,
a:focus ,
a:active {
	text-decoration: underline;
}
```

Tip: Keep *LoVe/HAte* in mind for `:link`, `:visited`,
`:hover`/`:focus`, and `:active`.

<a name="property-order"></a>
### Property order

If properties are to be consistently ordered, it SHOULD be in
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

<a name="vendor-prefixes"></a>
### Properties with vendor prefixes

When using vendor prefixes, you MUST add the non-prefixed property at
the end. Thus vendor prefixes should go longest (-webkit-) to shortest
(unprefixed). Values MAY be right aligned with spaces after the colon
provided that all the values are the same across all prefixes.

```css
.selector {
	-webkit-transition: all 1s ease-out;
	-moz-transition:    all 1s ease-out;
	-ms-transition:     all 1s ease-out;
	-o-transition:      all 1s ease-out;
	transition:         all 1s ease-out;
}
```

<a name="css-comments"></a>
### Comments

Well commented code is extremely important. Take time to describe
components, how they work, their limitations, and the way they are
constructed. Do not leave others in the team guessing as to the purpose
of uncommon or non-obvious code.

Comment style should be simple and consistent within a single code base.

* Comments MUST be placed on a new line above their subject.
* Make liberal use of comments to break CSS code into discrete sections.
* Use “sentence case” comments and consistent text indentation.
* CSS file headers MUST use Doctype-style [CSSDOC](http://cssdoc.net/).
* Rulesets SHOULD be documented using
  [KSS](https://github.com/kneath/kss/blob/master/SPEC.md). KSS attempts
  to provide a methodology for writing maintainable, documented CSS
  within a team. Specifically, KSS is a documentation specification and
  styleguide format.

```css
/**
 * @package    My project
 * @subpackage Ratings module
 * @license    MIT License, http://opensource.org/licenses/MIT
 * @copyright  Copyright (c) 2013, John Doe
 * @author     John Doe
 * @media      all
 */

/*
A button suitable for giving stars to someone.

:hover             - Subtle hover highlight.
.stars-given       - A highlight indicating you’ve already given a star.
.stars-given:hover - Subtle hover highlight on top of given stars.
.disabled          - Dims the button to indicate it cannot be used.

Styleguide 2.1.3.
*/
button.star {
	...
}

button.star.stars-given {
	/* Basic comment */
	...
}

button.star.disabled {
	...
}
```

<a name="preprocessors"></a>
### Preprocessors

Different CSS preprocessors have different features, functionality, and
syntax. Your conventions should be extended to accommodate the
particularities of any preprocessor in use. The following guidelines are
in reference to [LESS](http://lesscss.org/), [Sass](http://sass-lang.com/),
and [Stylus](http://learnboost.github.io/stylus/).

 * You MUST use a CSS-like syntax, like SCSS in Sass or the non-omitting
   syntax in Stylus.
 * You MUST place `@extend` statements on the first lines of a
   declaration block. Knowing right off the bat that an element inherits
   another whole set of rules from elsewhere is good.
 * You SHOULD put mixins at the end of a declaration block.
 * You MUST limit nesting to 3 level deep. Reassess any nesting more than 4
   levels deep. This prevents overly-specific CSS selectors.
 * You SHOULD avoid large numbers of nested rules. Break them up when
   readability starts to be affected. Preference to avoid nesting that
   spreads over more than 20 lines.
 * Nothing goes after the nested stuff. And the same order as above
   within the nested selector would apply.
 * All vendor-prefixes MUST use mixins. The only exception MAY be when
   it is super proprietary, unlikely to be standardized as is, and so
   including other vendor prefixes or the non-prefixed version is likely
   to cause more harm that good (i.e. `-webkit-line-clamp`).
 * You MAY prefix custom functions with `x-` or another namespace. This
   helps to avoid any potential to confuse your function with a native
   CSS function, or to clash with functions from libraries.
 * Global and section-specific files are just table of contents. In
   other words, no styles directly in them. Force yourself to keep all
   styles organized into component parts. List vendor/global
   dependencies first, then author dependencies, then patterns, then
   parts.

<a name="javascript"></a>
## JavaScript

<a name="js-content-type"></a>
### HTTP content type

You MUST use the `application/javascript` content type with a UTF-8
encoding:

```
Content-Type: application/javascript; charset=utf-8
```

<a name="js-format"></a>
### Format

The chosen code format must ensure that code is: easy to read; easy to
clearly comment; minimizes the chance of accidentally introducing
errors; and results in useful diffs and blames.

 * Namespaces MUST be declared in `StudlyCaps` and SHOULD start with
   leading double underscores (i.e. `__MySite`). Use one global
   namespace per site and do not pollute the global namespace.
 * AMD module names MUST be declared in `StudlyCaps`.
 * Constant names MUST be declared in `UPPERCASE`.
 * Everything else (like method or variable names) MUST be declared in
  `camelCase`. Private methods or variables SHOULD start with a leading
   single underscore (i.e. `_myPrivateMethod`).
 * Do not use underscores in names as a word delimiter.
 * You are not a human code compiler/compressor, so do not try to be
   one: Use thoughtful naming (and a readable structure).
 * Always use single quotes. You MUST NOT mix quotes.
 * There MUST be one blank line after a scope (function), and there
   MUST be one blank line after the block of `var`/`let`/`const`
   statements.
 * Control structures always have spaces before and after the conditions
   and span multiple lines.
 * Opening braces for methods MUST go on the same line, and closing
   braces MUST go on the next line after the body.
 * Control structure keywords MUST have one space after them; method and
   function calls MUST NOT.
 * Opening braces for control structures MUST go on the same line, and
   closing braces MUST go on the next line after the body.
 * Opening parentheses for control structures MUST NOT have a space
   after them, and closing parentheses for control structures MUST NOT
   have a space before.
 * Ternary operations SHOULD NOT be used.
 * Use only one `var`/`let`/`const` per scope (function).
 * `var`/`let`/`const` statements SHOULD always be in the beginning of
   their respective scope (function).
 * [Strict Mode](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Functions_and_function_scope/Strict_mode)
   for methods SHOULD be invoked where possible.

```js
function foo() {

	// if possible, use Strict Mode
	'use strict';

	// combined vars first
	var bar = '',
		baz = 1;

	// strict checks with === or !==
	if (baz !== bar) {
		...
	}

	// spaces before and after coditions
	for (var i = 0; i < length; i++) {
		...
	}

	// indent object values
	baz = new Foobar({
		lorem: 'foobar',
		ipsum: 3,
		dolor: '',
		sit:   2,
		amet:  9
	});

	// span multiple lines, avoid ternary operator
	if (true) {
		...
	} else {
		...
	}
}
```

<a name="js-comments"></a>
### Comments

Well commented code is extremely important. Take time to describe
components, how they work, their limitations, and the way they are
constructed. Do not leave others in the team guessing as to the purpose
of uncommon or non-obvious code.

Comment style should be simple and consistent within a single code base.

* Comments must be placed on a new line above their subject.
* Use “sentence case” comments and consistent text indentation.
* Use Doctype-style [JSDuck](https://github.com/senchalabs/jsduck/wiki)
  for functions and properties to ease automated API documentation
  generation.

<a name="modules"></a>
### Modules

If possible, stick to the Asynchronous Module Definition (AMD) API as
defined [here](https://github.com/amdjs/amdjs-api/wiki).

```js
define([
	'MyModules/Requirement1',
	'MyModules/Requirement2'
], function(Requirement1, Requirement2) {

	'use strict';

	var _myMethod;

	/**
	 * @method _myMethod
	 * My Method does nothing. Sadface.
	 * @private
	 */
	_myMethod = function() {
		...
	};

	return {
		init: function() {
			...
		}
	};

});
```

For jQuery plugins, stick to [this pattern](https://github.com/umdjs/umd/blob/master/jqueryPlugin.js).

For everything else use the Revealing Module Pattern which is defined
[here](http://addyosmani.com/resources/essentialjsdesignpatterns/book/#revealingmodulepatternjavascript):

```js
window.__MySite = window.__MySite || {};

window.__MySite.MyModule = (function(window, document, undefined) {

	'use strict';

	var _myMethod;

	/**
	 * @method _myMethod
	 * My Method does nothing. Sadface.
	 * @private
	 */
	_myMethod = function() {
		...
	};

	return {
		init: function() {
			...
		}
	};

})(window, document);

window.__MySite.MyModule.init();
```

<a name="php"></a>
## PHP

<a name="php-standards"></a>
### PSR-1 and PSR-2

I highly recommend sticking to these guidelines defined by the PHP
Framework Interoperability Group:

 * [PSR-1](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md)
 * [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)

<a name="exceptions"></a>
### Optional exceptions from PSR-1 and PSR-2

To be consistent with code written in [JavaScript](#javascript), these
exceptions are allowed:

 * Code MUST use tabs for indenting, not 4 spaces.
 * Opening braces for closure, method and function calls MUST go on the
   same line, and closing braces MUST go on the next line after the
   body.
 * Closure, method and function calls MUST NOT have a space after their
   keywords.

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
 * [Isobar Front-end Code Standards & Best Practices](http://isobar-idev.github.io/code-standards/)
 * [Sass Style Guide](http://css-tricks.com/sass-style-guide/)
 * [Code Conventions for the Java™ Programming Language](http://www.oracle.com/technetwork/java/javase/documentation/codeconvtoc-136057.html)
 * [Code Conventions for the JavaServer Pages Technology Version 1.x Language](http://www.oracle.com/technetwork/articles/javase/code-convention-138726.html)
