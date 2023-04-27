---
title: Markdown
pubDate: 2023-04-27
description: ''
---

## 语法

```markdown
*斜体*
**加粗**
==高亮==
`行内代码`
~~删除线~~
[链接](https://example.org/)
<u>下划线<u>
```

### Links

[Reference-style links](https://www.markdownguide.org/basic-syntax#reference-style-links)

```markdown
[label 1][reference link]  
[label 2][reference link]

[reference link]: [https://www.google.com](https://www.google.com/)
```

### Footnotes

Here is a simple footnote[^1].

A footnote can also have multiple lines[^2].  

You can also use words, to fit your writing style more closely[^note].

### LaTeX 公式

$$E=mc^2$$

## Markdown 代码块支持的语言

GitHub uses Linguist to perform language detection and syntax highlighting. Here a list of common languages that can be used with the backtick (see full list in [Linguist - languages.yml](https://github.com/github/linguist/blob/master/lib/linguist/languages.yml)).

| 名称        | 关键字                  |
| ----------- | ----------------------- |
| C           | cpp, c                  |
| C#          | csharp                  |
| CSS         | css                     |
| Delphi      | delphi, pascal, pas     |
| Diff        | diff patch              |
| Erlang      | erl, erlang             |
| GO          | go, golang              |
| Java        | java                    |
| JavaScript  | js, jscript, javascript |
| JSON        | json                    |
| PHP         | php                     |
| Python      | py, python              |
| Ruby        | ruby, rails, ror, rb    |
| SASS & SCSS | sass, scss              |
| Shell       | sh, bash, zsh           |
| SQL         | sql                     |
| Swift       | swift                   |
| Text        | text, plain             |
| XML         | xml, xhtml, xslt, html  |
| YAML        | yml                     |

## Front Matter

Front matter allows you to keep metadata attached to an instance of a content type—i.e., embedded inside a content file.

```yml
aliases: [/posts/my-old-url/]
tags: [investing, stock]
```

- aliases: an array of one or more aliases (e.g., old published paths of renamed content) that will be created in the output directory structure . See [Aliases](https://gohugo.io/content-management/urls/#aliases) for details.

[^1]: My reference.
[^2]: Every new line should be prefixed with 2 spaces.  
  This allows you to have a footnote with multiple lines.
[^note]:
    Named footnotes will still render with numbers instead of the text but allow easier identification and linking.  
    This footnote also has been made with a different syntax using 4 spaces for new lines.
