# trantor

A Metropolis-style theme for the [`ltx-talk`](https://ctan.org/pkg/ltx-talk)
presentation class: Libertinus Serif body, Libertinus Sans titles, a slim
progress bar, and tagged PDF/UA output for accessible slides.

![The title slide and an example slide](preview.png)

The [demo deck](slides.pdf) is produced by `slides.tex`.

## Requirements

- LuaLaTeX (the theme uses `fontspec` and Lua-based math tagging).
- A recent TeX Live or MacTeX, for `ltx-talk`.
- The Libertinus fonts and the `euler-math` package, both in TeX Live.

## Getting started

Copy `trantor.sty` (and a `logo.png` if you want one) next to your document and
compile `slides.tex` twice with LuaLaTeX:

```sh
lualatex slides.tex
lualatex slides.tex
```

The second pass fills in the table of contents on the section pages.
`slides.tex` is a short demo you can strip down into your own deck.

## Customising

- **Accent colour.** Sets the progress bar and the rule under the title. Define
  it anywhere in your preamble:
  ```latex
  \definecolor{accent}{HTML}{2A7AE2}
  ```
- **Logo.** Drop a `logo.png` beside your slides and it appears on the title
  page, or redefine `\titlelogo` to point at your own file. With no logo file
  the title page omits it.
- **Title spacing.** Use `\stitle{...}` instead of `\frametitle{...}` on dense
  slides to keep a clear gap below the title.
- **Tick and cross.** `\yes` and `\no` give a check mark and a cross.
- **Reference footnote.** `\footline{...}` pins a small citation to the
  bottom-left of the slide.

## Building

- **Draft** (the default). Fast, no tagging. Good for writing.
- **Accessible** (PDF/UA-2). Swap the `\DocumentMetadata` line at the top of
  `slides.tex` for the tagged block below it, then compile twice. Give every
  figure an `alt={...}` description so it passes PDF/UA.
- **Handout.** Add `[handout]` to `\documentclass` to collapse overlays to one
  page per frame. This is faster while writing; remove it to see the animations.

## Credits

Design inspired by Matthias Vogelgesang's
[Metropolis](https://github.com/matze/mtheme) beamer theme (CC BY-SA 4.0). This
is an independent reimplementation for `ltx-talk`.

## License

MIT, see [LICENSE](LICENSE). The Libertinus fonts are licensed separately under
the SIL Open Font License.
