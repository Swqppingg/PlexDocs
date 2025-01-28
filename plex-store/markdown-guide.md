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

<details>

<summary>Example</summary>

## Heading 1

### Heading 2

#### Heading 3

**Heading 4**

</details>

### **Text formatting**

Plex Store currently support most markdown formatting. Simply add `**`, `_`, or `~~` around text to format it.

| Style         | How to write it          | Result            |
| ------------- | ------------------------ | ----------------- |
| Bold          | `**bold**` or `__bold__` | **bold**          |
| Italic        | `*italic*` or `_italic_` | _italic_          |
| Strikethrough | `~~strikethrough~~`      | ~~strikethrough~~ |

You can also combine them. For example, write `**_bold and italic_**` to get _**bold and italic**_ text.

### Blockquotes

Use `>` to create a blockquote.

> This is a blockquote.

```
> This is a blockquote.
```

### Lists

#### Ordered Lists

To create a ordered list, add line items with numbers followed by periods.

1. Line 1
2. Line 2
3. Line 3
4. Line 4

```md
1. Line 1
2. Line 2
3. Line 3
4. Line 4
```

#### Unordered List <a href="#unordered-list" id="unordered-list"></a>

To create a unordered list, add dashes (`-`), asterisks (`*`), or plus signs (`+`) in front of line items.

* First item
* Second item
* Third item
* Fourth item

```md
- First item
- Second item
- Third item
- Fourth item
```

You can also nest them by adding indents on the list items:

* First item
* Second item
  * Additional item
  * Additional item
* Third item

```md
- First item
- Second item
  - Additional item
  - Additional item
- Third item
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

