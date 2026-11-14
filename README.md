# Barn website

Part of [Barn](https://rogerbarnfather.github.io/barn-website/).

A static site for Barn: a home page, a page for Barn itself, one page each for Barnspek,
Barnark and Barntree, and a Philosophy page. There is no build step.

It leads with the philosophy and the GUIs. Details, terminology, the command
line and installation sit in each page's collapsible "Go deeper" sections.
The screenshots in `assets/screens/` are real, taken in Chrome at twice the size.

Styles: `assets/base/` is the shared stylesheet (tokens, layout, components and the documentation
layout, one file each; `base.css` is the entry). Each tool's own site carries an identical copy, and
`bin/ci-all` in the suite folder fails if one differs. `assets/site.css` holds only this site's own
components. See `docs/style-guide.md`.

Retaken on 2026-11-08, on Barntree core 8.1.0, CLI 6.2.0 and GUI 6.3.0
with the approved evergreen branding:

- `cept-editor`: House’s expanded Template tree and its workspace sidebar.
- `cept-template-edit`: the Kitchen leaf’s explicit editing session, with Save and Cancel.
- `cept-items`: Willow Cottage, an independent House Construction with Front bedroom
  and Back bedroom list members.
- `cept-history`: the Construction’s creation and two member-addition revisions.
- `cept-vocab`: the current House Glossary, retaining its existing public filename.

These are real Chrome captures at 1280 × 820 CSS pixels and 2× resolution, using
a disposable barn and the shipped House example. The temporary barn path is hidden
in the screenshots. Construction creation and member additions use the released CLI;
the GUI reads the same saved records. No real project data was changed.
The Barntree page and related product summaries now describe Templates,
Constructions, exact captured sources and immutable revision history.

Taken on 2026-11-05, on the Barnark 8.2 line:

- `ark-tags`: the Barnark GUI on its own, in a project made with
  `barnark template:clone "Domain Driven Design" Hotel src` and given three
  contexts, on the History tab with the `Application` tag picked out.

Retaken on 2026-11-03, on Barnspek 3.1.0 and the Barnark 7 line, against a
made-up hotel whose stories were written through Barnspek's API for the shots:

- `spec-map` and `spec-work`: the Barnspek GUI's Story map and a Work board. In
  `spec-work` the scenario's two tickets are done and it has never been run.
- `barn-home`, `ark-browse` and `ark-check`: a barn made with
  `barn build --template="Domain Driven Design" --template-name=Hotel`, given
  three contexts and two aggregates, with the same hotel's stories. The home shot
  hides the barn's path, which was a scratch folder. The Barnark shots leave out
  the barn's top bar.
- `ark-new`: the Barnark GUI on its own, in a project with nothing bound yet,
  with Clone into the project filled in.

Earlier captures on 2026-10-25 (superseded above):

- `cept-vocab` (the name is kept because READMEs embed it) and `cept-editor`:
  the Barntree GUI over a folder holding Barntree's own example trees
  (House, Room, Kitchen, Garden, Pet) and Barnark's Domain Driven Design
  template, open on House's Living room and on a bounded context's Domain.

The three GUIs' READMEs and Barnspek's, Barnark's and Barntree's embed
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
| Barnspek (sky blue) | `#0b95e0` fill, `#0a76b5` text | `#55c9ff` |
| Barnark (orange) | `#f25c05` fill, `#c84600` text | `#ff9244` |
| Barntree (mint) | `#18d19e` fill, `#07795f` text | `#3ff0bf` |

The main Barn site (`index.html`) uses mint too, as `data-brand="barn"`: green
reads as passing, where blue felt sad on a home page.

A page takes its colour from `<body data-brand="spec|ark|tree|barn">`, and any
element with `data-brand` takes that tool's colour. The tokens are at the top
of `assets/site.css`.

Large and decorative text (headline accent, kickers, the "+" icons, nav hover)
uses `--brand-bright`; small body links keep the deeper `--brand-text` so they
stay readable on white.

### Barnark captures refreshed 2026-11-14

`ark-browse.webp` and its theme-selected `ark-browse-dark.webp` companion are the same
2× Chrome captures as the Barnark site: published core 0.3.0 / GUI 0.2.10, a disposable
Hotel ark at `/src`, three contexts, Booking and tagged layers. The local barn path is hidden.
Existing README embed URLs are retained.

### Barnspek rename captures — 2026-11-14

Retaken from the local Barnspek core/CLI/GUI **0.1.0 candidates**, inside Barn GUI
**0.2.0 candidate**, in installed Chrome at 2× resolution. These candidates are not
published yet. Each light capture has a `-dark.webp` companion selected by the site.
Existing public image filenames and README embed URLs are retained.

- `spec-map`: Reservations at a made-up Hotel, with six stories for Guest and
  Receptionist across the five lifecycle stages. Five are planned; the receipt
  story was proven by a real Scenario Bridge run and released.
- `spec-work`: a replacement-receipt scenario whose one ticket is done, with no
  run recorded. It remains “All tickets done — not yet run”.
- `barn-home`: Hotel, one green and one red scenario, and a clean Hotel ark
  at `/src` made from the earlier disposable Barnark capture fixture.

The map is 1408 × 780 CSS pixels and Work is 1408 × 930; the main site's home
capture is 1408 × 420. Only disposable projects were written. The local path
was hidden before capture; no screenshot wording or result was painted over.
Capture scripts, fixture records and verification are retained in the suite's
`docs/plans/barnspek-rename-stage4b/` evidence. Website destination and publication
remain pending; the existing verified site URL above is unchanged.

### Spek tab screenshots — 2026-11-14

The affected light and dark screenshots were recaptured from the real Barn GUI with the
Spek label, using a disposable Hotel and Chrome at 2× resolution.
