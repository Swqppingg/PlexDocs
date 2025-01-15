---
description: Markdown Guide for product descriptions
---

# Markdown Guide

### Headings

Use `#` symbols followed by a space to create headings. The number of `#` symbols determines the heading level.

```
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
```

### **Emphasis (Italics and Bold)**

* Italicize text with one asterisk or underscore: `*italic*` or `_italic_`
* Bold text with two asterisks or underscores: `**bold**` or `__bold__`
* Combine both: `**This is bold and *italic* text.**`

```
*This text is italicized.*
_This text is also italicized._

**This text is bold.**
__This text is also bold.__

**This is bold and *italic* text.**
```

### Strikethrough

Use two tildes `~~` to strike through text.

```
~~This text is strikethrough.~~
```

### Blockquotes

Use `>` to create a blockquote.

```
> This is a blockquote.
```

### Lists

* **Unordered Lists**: Use `-`, `+`, or `*` followed by a space.
* **Ordered Lists**: Use numbers followed by a period.

```
- Item 1
- Item 2
  - Subitem 1
  - Subitem 2

+ Item 1
+ Item 2

* Item 1
* Item 2

1. First item
2. Second item
   1. Subitem 1
   2. Subitem 2
```

### Links

* **Inline Links**: `[Link Text](URL)`
* **Reference Links**: `[Link Text][id]` and `[id]: URL`

```
[GitHub](https://github.com)

[Google][1]

[1]: https://www.google.com
```

### Images

* **Inline Images**: `![Alt Text](Image URL)`
* **Reference Images**: `![Alt Text][id]` and `[id]: Image URL`

```
![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

![Google Logo][1]

[1]: https://www.google.com/images/branding/googlelogo/1x/googlelogo_color_272x92dp.png
```

### Code

* **Inline Code**: Use backticks `` ` `` to wrap inline code.
* **Code Blocks**: Use triple backticks to create code blocks.

<pre><code><strong>``function example() {
</strong>console.log("This is a code block.");
}``
</code></pre>

### Markdown Syntax Highlighting

You can specify the language after the opening backticks in a code block.

```
``javascript
function helloWorld() {
    console.log("Hello, World!");
}``
```

### Tables

Use pipes `|` and hyphens `-` to create tables. The hyphens separate the header row from the data rows.

```
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| row 1 | content | $2600 |
| row 2 | content | $3600 |
| row 3 | content | $4200 |
```

### Custom Containers

```
:::info
This is an information container.
:::

:::success
This is a success container.
:::

:::warning
This is a warning container.
:::

:::danger
This is a danger container.
:::
```

