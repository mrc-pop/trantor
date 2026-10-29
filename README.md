# trantor

A Metropolis-style theme for the [`ltx-talk`](https://ctan.org/pkg/ltx-talk)
presentation class: Libertinus Serif body, Libertinus Sans titles, a slim
progress bar, and tagged PDF/UA output for accessible slides.

![The title slide and an example slide](preview.png)

## Getting started

trantor needs LuaLaTeX, with a recent TeX Live or MacTeX carrying the Libertinus
fonts and `lua-unicode-math` v0.9+.

Copy `trantor.sty` (and a `logo.png` if you want one) next to your document and
compile twice:

```sh
lualatex slides.tex
lualatex slides.tex
```

`slides.tex` is a short [demo deck](slides.pdf) that can be edited into your
own.

## Options

Give them to the package, or to `\trantorset`, which also works mid-document:

```latex
\usepackage[accent-html = 2A7AE2, divider = title]{trantor}
\trantorset{accent = blue!60!black}
```

| Key | What it does |
| --- | --- |
| `accent-html = 2A7AE2` | accent colour from a hex string |
| `accent = blue!60!black` | accent colour from any xcolor expression |
| `numbering = content` | *(default)* the title and divider slides are not numbered, only the "actual content" is |
| `numbering = all` | every slide is numbered |
| `divider = toc` | *(default)* `\sectionpage` is a dark slide with the table of contents and the current section highlighted |
| `divider = title` | `\sectionpage` names only the current section, over a progress bar |
| `header = light` | *(default)* frame titles on the page background |
| `header = dark` | frame titles inside a dark band |
| `appendix = overrun` | *(default)* backup slides count past the total, e.g. 16/15, 17/15 |
| `appendix = restart` | backup slides are numbered among themselves, e.g. 1/3, 2/3 |

`header` is read once at `\begin{document}`, so it should be set in the
preamble. The others can be changed at any point.

## Customising

- **Title page**: `\subtitle{...}` sits under the title, and a `logo.png` beside
  your slides appears on the right. Redefine `\titlelogo` for a different file.
- **Maths font**: Euler by default. Change the `\RequirePackage{lum-euler}` line
  in `trantor.sty` for another.
- **Title spacing**: use `\stitle{...}` instead of `\frametitle{...}` on dense
  slides to keep a clear gap below the title.
- **Inside your own frame**: `\maketitle`, the divider commands and `\standout`
  typeset in the current frame if there is one, so a `\note` or a `\footline` can
  sit alongside them; called between frames they open their own.
- **Divider slides**: `\sectionpage` and `\subsectionpage` follow the `divider`
  option; `\outlinepage` puts the table of contents on a dark slide with every
  entry in full white, for an overview after the title page or between parts of
  a long talk; `\standout{...}` puts a single line of text on that slide
  instead.
- **Emphasis**: `\standoutline{...}` centres a line in the title font on the
  current slide.
- **Reference footnote**: `\footline{...}` pins a small citation to the
  bottom-left of the slide, and `\arxiv{1508.05949}` tags a statement with a
  small grey link to the abstract.
- **Plain slides**: `\plainpage` hides the progress bar and frame number on a
  frame, as the title page and the dark panels do. Useful for a full-bleed image.
- **Backup slides**: `\appendix` starts them, and the `appendix` option decides
  how they are numbered.
- **Colours**: `TrantorAccent` is the one meant to change; `TrantorDark`,
  `TrantorLight` and `TrantorMuted` can be redefined after loading the package.
- **Other**: `\yes` and `\no` give a check mark and a cross.

## Building

- **Draft** (the default): fast, with tagging disabled.
- **Accessible** (PDF/UA-2): swap the `\DocumentMetadata` line at the top of
  `slides.tex` for the tagged block below it, then compile three times. Give
  every figure an `alt={...}` description so it passes PDF/UA. The rest is
  handled by ltx-talk.

You can also use `ltx-talk`'s `handout` option.

## Credits

Design inspired by Matthias Vogelgesang's
[Metropolis](https://github.com/matze/mtheme) beamer theme (CC BY-SA 4.0). This
is an independent reimplementation for `ltx-talk`.

## License

MIT, see [LICENSE](LICENSE). The Libertinus fonts are licensed separately under
the SIL Open Font License.
