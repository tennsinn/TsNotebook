# Markdown

## Title

Set heading level 1 (`<h1>`) and 2 (`<h2>`) with at least one `=` or `-` symbol in the next line.

	Heading Level 1
	===

	Heading Level 2
	---

Using a certain number of `#` symbols in front of the title, will be parsed into the corresponding title `<h1>` to `<h6>`.

	# Heading level 1
	## Heading level 2
	### Heading level 3
	#### Heading level 4
	##### Heading level 5
	###### Heading level 6

## Paragraph

Add more than 2 spaces at the end of the line will prase as a `<br>` tag.

	Paragraph 1 Line 1  
	Paragraph 1 Line 2

Add a blank line after a paragraph can end the current paragraph and create a new one enclosed in `<p>` tag.

	Paragraph 1

	Paragraph 2

## Font

Default font style including italic, bold, and strikethrough.

*Notice: the font style can be added or rewrited by the plugins.*

	*italic*
	_italic_
	**bold**
	__bold__
	***italic and bold***
	___italic and bold___

	~~strikethrough~~

## HTML tag

HTML tag is supported in markdown, for example: `<kbd>`, `<b>`, `<i>`, `<em>`, `<sup>`, `<sub>`, `<br>` and so on.

But some extensions can support the use of pure Markdown.

### Plugin: markdown-it-underline

Add support for `<u>` tag, the underline contents need be enclosed with symbol `_`, it will replace the default italic style.

	_underline_

### Plugin: markdown-it-sup

Add support for `<sup>` tag, the sup contents need be enclosed with symbol `^`.

	^sup^

### Plugin: markdown-it-sub

Add support for `<sub>` tag, the sub contents need be enclosed with single `~` on each side.

	~sub~

### Plugin: markdown-it-kbd

Add support for `kbd` tag.

	[[kbd]]

### Plugin: markdown-it-deflist

Add support for `<dl>` tag, but do not support multiple terms and descroptions.

	term
	: description

### Plugin: markdown-it-abbr

Add support for `<abbr>` tag, the abbreviation need be defined first, so it will be displayed on all the same names in the content.

	*[abbr]: full name
	The contents include abbr tag.

### Plugin: markdown-it-checkbox

	[ ] unchecked
	[x] checked

### Plugin: markdown-it-mark

	==mark==

### Plugin: markdown-it-attrs

Add custom style or set any attrs, this can be used in heading, paragraph, inline element, list and fenced code blocks.

Can use `.` as the short hand of `class=`, `#` as `id=` and `..` as `css-module=`.

	# Heading {#identifier}

	Paragraph {.class}

	*inline element*{attr=value}

	- item
	{attr="spaced value"}

	```markdown {data=data}
	```

The delimiter can be changed and set the enabled attributes.

	leftDelimiter: '{', // default '{'
	rightDelimiter: '}', // default '}'
	allowedAttributes: []  // empty array = all attributes are allowed

### Plugin: markdown-it-table-of-contents

	[[TOC]]

### Plugin: markdown-it-container

Render with nested div structure, refering the container structure of bootstrap, need add style links.

	::::: container_class
	:::: row_class
	::: column_class
	contents
	:::
	::::
	:::::

### Plugin: markdown-it-footnote

Need extension 'markdown-it-footnote' to support footnote feature, or the original markdown engine will prase it as a link.

	[^footnote-tag]

	[^footnote-tag]: footnote_contents

### Plugin: markdown-it-html5-embed

Add support for embedding audio/video in the HTML5 way, by using `<video>` and `<audio>` tags.

Embed in-place with the link or image syntax, and it can be setted in html5embed item.

	html5embed: {
		useImageSyntax: true, // Enables video/audio embed with ![]() syntax (default)
		useLinkSyntax: true   // Enables video/audio embed with []() syntax
	}

## Separator

Use more than 3 `*` or `-` or `_` in a single line without any other things, can add the spaces within the symbols.

	***
	* * *
	---
	- - -
	___
	_ _ _

## List

Use symble `*`, `+`, `-` followed by a space to create an unordered list.

	* item 1
	* item 2

	+ item 1
	+ item 2

	- item 1
	- item 2

Use number followed by a dot and space `1. ` to create an ordered list.

	1. item 1
	2. item 2

Use four spece or a tab before list symble to create a nested list.

	1. item 1
		- item 1
		- item 2
	1. item 2

## Block

Use the symble `>` followed by a space to create a block.

	> block content  
	> block content

The block can be nested and indentable.

	> block content  
	> > nested block content  
	> > > nested block content

The block can be added into list.

	1. item 1
		> block in list
		> > block in list
	1. item 2

## Code

Create the inline code enclosed in two <code>`</code>.

	`inline code`

Code block with 4 spaces or a tab on the front the line.

	code block

Code block with symble <code>```</code> on the start and end of the code, and can indicate the code name.

	```codename
	code content
	```

## Link

Use the name enclosed in square brackets and link enclosed in parentheses.

	[link_name1](link_addr1 "link_title1")

	[link_name2]
	[link_name2]: link_addr2 "link_title2"

	[link_name3][link_tag]
	[link_tag]: link_addr3 "link_title3"

Link to the Headings.

	[Heading IDs](#heading-ids)

Or directly use the weblink.

	www.weblink.com

## Image

Add the Image link inline.

	![link_name](link_addr "link_title")

Add the Image with the defined tag, and can add the link at the end of the file with the tag.

	![link_name][link_tag]
	[link_tag]: link_addr3 "link_title3"

## Table

Create the table with symbol `|` indicates the cell. The table must included the first line which is the header of the table and the seccond line shows the alignment, symbol `:` indicates the align rule.

	| left         |     center     |         right |
	| :----------- | :------------: | ------------: |
	| left content | center content | right content |

*Note: Suggest to use `&#124;` as `|` in the table.*

### Plugin: markdown-it-multimd-table

Caption and colspan is the default enabled feature, but multiline, rowspan and headerless should be set to true in settings.

	multiline:  false, // default false
	rowspan:    false, // default false
	headerless: false, // default false

#### Caption

Can add the caption at the next line of the table enclosed with `[]`.

	| left         |     center     |         right |
	| :----------- | :------------: | ------------: |
	| left content | center content | right content |
	[caption]

#### Colspan

Automatic merge the cell with the left one when nothing between two column pipes.

	| column 1         |   column 2   | column 3 |
	| :--------------- | :----------: | -------: |
	| independent cell |      merged cells      ||

#### Headerless

Can create the table without headers.

	| :----------- | :------------: | ------------: |
	| left content | center content | right content |

#### Rowspan

Automatic merge the cell with the above one when only two `^^` inside the cell.

	| column 1         |   column 2   |         column 3 |
	| :--------------- | :----------: | ---------------: |
	| independent cell | merged cells | independent cell |
	| independent cell |      ^^      | independent cell |

#### Multiline

Use a backslash at the line end, will merge the content below.

	| column 1 | column 2 |    column 3 |
	| :------- | :------: | ----------: |
	| part 1   | - item 1 | single line | \
	| part 2   | - item 2 |             |

## Math

Add the inline Tex or LaTeX format math enclosed with notation `$`.

	$LaTeX_math$

Will parse as the independent formula if enclosed with double doller symbol `$$`, can add multiple lines in it.

	$$
	LaTeX_math
	$$
