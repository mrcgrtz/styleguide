# Coding Style Guide

This is my personal frontend coding style guide. It is a living document
and new ideas are always welcome. Please contribute.

## Table of contents

 * [General principles](#general-principles)
 * [Third-party projects](#3rdparty)
 * [HTML](#html)
 * [CSS](#css)
 * [JavaScript](#javascript)
 * [PHP](#php)

<a name="general-principles"></a>
## General principles

### Project

 * Your project must have an .editorconfig file in your project’s root
   directory. Stick to the [one](https://github.com/Dreamseer/dotfiles/blob/master/.editorconfig)
   in this dotfiles repository, if possible.
 * Your project must have a .gitattributes file in your project’s root
   directory. Stick to the [one](https://github.com/Dreamseer/dotfiles/blob/master/.gitattributes)
   in this dotfiles repository, if possible.

### File format

Files must be stored as ASCII text and must use the UTF-8 character
encoding.

Line termination follows the Unix text file convention, thus lines must
end with a single linefeed ({{{LF}}}) character. Line feeds are
represented as ordinal {{{10}}}, or hexadecimal {{{0x0A}}}. Do not use
carriage returns ({{{CR}}}) like Macintosh computers do ({{{0x0D}}}) or
the carriage return/linefeed combination ({{{CRLF}}}) like Windows
computers do ({{{0x0D}}}, {{{0x0A}}}).

When saving files, manually remove extra lines at the end of all files,
so that unwanted space is not inserted. It is also a good habit to
ensure all trailing spaces are removed.

Files must end with a new line at their end (EOF).

We prefer readability over file-size savings when it comes to
maintaining existing files. Plenty of whitespace is encouraged. There is
no need for any developer to purposefully compress HTML or CSS, nor
obfuscate JavaScript.

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

### HTTP content type

Always use the text/html content type with a UTF-8 encoding:

	Content-Type: text/html; charset=utf-8

### Doctype

Always use the minimal, versionless doctype.

	<!DOCTYPE html>

### Language

Always define which language the page is written in.

	<html lang="de">

### Encoding

Always define the character encoding using the minimal charset meta
element. The encoding should be defined as early as possible.

	<meta charset="utf-8">

### Elements and Attributes

All element and attribute names should be lowercase. Attribute values
should be quoted. Optional closing tags should be included. Self-closing
elements should not be closed. Optional attributes should be omitted.
Always include html, head and body tags.

 * No type or language attributes on script tags.
 * No type attribute on link or style tags.

	<script src="…"><script>
	<script></script>
	<link rel="stylesheet" href="…">
	<style></style>

### Indentation

Do not indent inside html, body, script, or style. Indent inside head
and all other elements.

### Layered semantic markup / principles

 * Use semantic class/ID names and appropriate HTML elements for
   content as defined in
   [The Elements of HTML](http://developers.whatwg.org/semantics.html#semantics).
 * Do not use inline CSS or inline JavaScript.
 * Use Microformats and Microdata where possible.
 * Use dashes (not underscores) as a word delimiter in class/ID names.

### Validation

All HTML documents should be verified against the W3C validator to
ensure that the markup is well formed. This in and of itself is not
directly indicative of good code, but it helps to weed out problems that
are able to be tested via automation. It is no substitute for manual
code review.

### Accessibility

 * Documents should work without JavaScript enabled.
 * Documents should be accessible by screenreaders.
 * Use attributes provided by [WAI-ARIA](http://www.w3.org/TR/wai-aria/)
   to avoid accessibility issues for people using screenreaders or other
   devices.
 * Keep keyboard navigation in mind, do not rely on mouse events.
 * Follow the [WCAG2](http://www.w3.org/TR/WCAG20/#guidelines).

<a name="css"></a>
## CSS

<a name="javascript"></a>
## JavaScript

<a name="php"></a>
## PHP
