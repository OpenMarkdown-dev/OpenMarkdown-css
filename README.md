# @openmarkdown-dev/css

The stylesheet OpenMarkdown uses for Markdown rendered as HTML: the same colours, fonts and
type scale as the [OpenMarkdown editor](https://openmarkdown.dev/editor/), as plain CSS. Light,
dark, or following the reader's system. No JavaScript, no fonts to download, no dependencies.

```sh
npm install @openmarkdown-dev/css
```

## Usage

Load the sheet and put `class="om-doc"` on the element that holds the rendered HTML:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/@openmarkdown-dev/css/openmarkdown.css">
<body class="om-doc">
  <article class="om-doc-body"><!-- rendered Markdown --></article>
</body>
```

With a bundler: `import "@openmarkdown-dev/css";`. `om-doc-body` is optional: it centres the
text in a readable column.

## Schemes

| File | Import | Scheme |
| --- | --- | --- |
| `openmarkdown.css` | `@openmarkdown-dev/css` | Light, and dark when the reader's system is dark (`prefers-color-scheme`). |
| `openmarkdown-light.css` | `@openmarkdown-dev/css/light` | Always light. |
| `openmarkdown-dark.css` | `@openmarkdown-dev/css/dark` | Always dark. |

## What it styles

Everything a CommonMark / GFM renderer emits inside `.om-doc`: headings, paragraphs, links,
emphasis, inline code and code blocks, block quotes, lists, tables, rules and images.

The rest uses the classes OpenMarkdown's own renderer (the app's Export as HTML) puts on its
output: `om-callout` and `om-callout-<note|tip|important|warning|caution>` with
`om-callout-title` (GitHub-style callouts), `om-task` (task list items), `om-table-wrap`
(a table that scrolls sideways), `om-align-<left|center|right>` (table cell alignment),
`om-math-block` (display math), `om-mermaid` (a drawn diagram), `om-props` (a note's
Properties table), `om-agent` (an `@agent` mention) and `om-image-missing`.

## Theming

Every colour, font and corner is a `--ome-*` custom property, declared on `.om-doc`. To
change one, set it on `.om-doc` in a stylesheet loaded after this one:

```css
.om-doc {
  --ome-accent: #0b6bcb;
  --ome-font: "Inter", system-ui, sans-serif;
}
```

They are the editor's theme tokens; the
[editor's README](https://github.com/OpenMarkdown-dev/OpenMarkdown-editor#theming) lists
what each one is used for.

## Versions

This package has the same version as `@openmarkdown-dev/editor` and is released with it.
Changes to the stylesheet are noted in the
[editor's CHANGELOG](https://github.com/OpenMarkdown-dev/OpenMarkdown-editor/blob/main/CHANGELOG.md).

## Contributing

This repository is generated: the stylesheet is built from the editor's design tokens in the
OpenMarkdown source and exported here on each release, so it is never edited in this
repository.

- **Issues are welcome here**: a rendering bug (with a small Markdown sample and the browser),
  a missing style, a theming question.
- **Pull requests are not accepted here**, because the files would be overwritten by the next
  export. To change the stylesheet, open a pull request on the editor repository,
  [OpenMarkdown-dev/OpenMarkdown-editor](https://github.com/OpenMarkdown-dev/OpenMarkdown-editor),
  against `src/editor/render/renderStyle.ts` (the rules) or `src/editor/tokens.ts` (the values).
  Its [contributing guide](https://github.com/OpenMarkdown-dev/OpenMarkdown-editor/blob/main/CONTRIBUTING.md)
  and Contributor License Agreement apply, and the change ships in both packages with the next release.

## License and trademark

The stylesheet is [MIT](https://github.com/OpenMarkdown-dev/OpenMarkdown-css/blob/main/LICENSE).
The MIT license covers the code, not the name: "OpenMarkdown" and its logo are trademarks,
and the [trademark policy](https://github.com/OpenMarkdown-dev/OpenMarkdown-editor/blob/main/TRADEMARK.md)
says what you may do with them.
