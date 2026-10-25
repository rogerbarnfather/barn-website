# Barn website

Part of [Barn](https://rogerbarnfather.github.io/barn-website/).

A static site for Barn: a home page, a page for Barn itself, and one page each for Barnspec,
Barnark and Barncept. There is no build step.

It leads with the philosophy and the GUIs. Details, terminology, the command
line and installation sit in each page's collapsible "Go deeper" sections.
The screenshots in `assets/screens/` are real. The two Barnspec shots
(`spec-map`, `spec-work`) are the Barnspec GUI running against a copy of
Pleasant Stay, with one extra in-progress Phase added to that copy so the map
shows every status.

The others were retaken on 2026-10-25, after Barnark lost switching, files and
borrowing and Barn lost `barn adopt`, from the local checkouts (not yet
released) in headless Chrome at twice the size:

- `barn-home`, `ark-browse`, `ark-check` and `ark-new`: a new barn made with
  `barn build --template="Domain Driven Design"`, given three contexts, two
  aggregates, a Model View Controller `site/` and a Library `lib/StayPeriod`, and
  Pleasant Stay's story map copied in. The home shot hides the barn's path, which
  was a scratch folder.
- `cept-vocab` (the name is kept because READMEs embed it) and `cept-editor`:
  the Barncept GUI over a folder holding Barncept's own example concepts
  (House, Room, Kitchen, Garden, Pet) and Barnark's current Domain Driven Design
  template, open on House's Living room and on a bounded context's Domain.

The three GUIs' READMEs and Barnspec's, Barnark's and Barncept's embed
`spec-map`, `ark-browse` and `cept-vocab` by their published URL, so replacing
one updates those READMEs too, and renaming or removing one breaks them. Their
alt text describes the picture, so it changes with it.

Open `index.html` in a browser, or serve the folder:

```bash
php -S localhost:8000 -t website
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
