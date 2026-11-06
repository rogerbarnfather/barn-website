# Barn website

Part of [Barn](https://rogerbarnfather.github.io/barn-website/).

A static site for Barn: a home page, a page for Barn itself, and one page each for Barnspec,
Barnark and Barncept. There is no build step.

It leads with the philosophy and the GUIs. Details, terminology, the command
line and installation sit in each page's collapsible "Go deeper" sections.
The screenshots in `assets/screens/` are real, taken in Chrome at twice the size.

Taken on 2026-11-05, on the Barnark 8.2 line:

- `ark-tags`: the Barnark GUI on its own, in a project made with
  `barnark template:clone "Domain Driven Design" Hotel src` and given three
  contexts, on the History tab with the `Application` tag picked out.

Retaken on 2026-11-03, on Barnspec 3.1.0 and the Barnark 7 line, against a
made-up hotel whose stories were written through Barnspec's API for the shots:

- `spec-map` and `spec-work`: the Barnspec GUI's Story map and a Work board. In
  `spec-work` the scenario's two tickets are done and it has never been run.
- `barn-home`, `ark-browse` and `ark-check`: a barn made with
  `barn build --template="Domain Driven Design" --template-name=Hotel`, given
  three contexts and two aggregates, with the same hotel's stories. The home shot
  hides the barn's path, which was a scratch folder. The Barnark shots leave out
  the barn's top bar.
- `ark-new`: the Barnark GUI on its own, in a project with nothing bound yet,
  with Clone into the project filled in.

Retaken on 2026-10-25:

- `cept-vocab` (the name is kept because READMEs embed it) and `cept-editor`:
  the Barncept GUI over a folder holding Barncept's own example concepts
  (House, Room, Kitchen, Garden, Pet) and Barnark's Domain Driven Design
  template, open on House's Living room and on a bounded context's Domain.

The three GUIs' READMEs and Barnspec's, Barnark's and Barncept's embed
`spec-map`, `ark-browse` and `cept-vocab` by their published URL, so replacing
one updates those READMEs too, and renaming or removing one breaks them. Their
alt text describes the picture, so it changes with it.

Open `index.html` in a browser, or run this from the website checkout:

```bash
php -S localhost:8000 -t .
```

Each tool has one colour, shared with its GUI:

| Tool | Light | Dark |
|---|---|---|
| Barnspec (mint) | `#18d19e` fill, `#07795f` text | `#3ff0bf` |
| Barnark (orange) | `#f25c05` fill, `#c84600` text | `#ff9244` |
| Barncept (sky blue) | `#0b95e0` fill, `#0a76b5` text | `#55c9ff` |

A page takes its colour from `<body data-brand="spec|ark|cept">`, and any
element with `data-brand` takes that tool's colour. The tokens are at the top
of `assets/site.css`.

Large and decorative text (headline accent, kickers, the "+" icons, nav hover)
uses `--brand-bright`; small body links keep the deeper `--brand-text` so they
stay readable on white.
