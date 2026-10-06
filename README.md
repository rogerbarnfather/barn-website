# BarnSuite website

A static site for BarnSuite: a home page plus one page each for Barnspec,
Barnark and Barncept. There is no build step.

It leads with the philosophy and the GUIs. Details, terminology, the command
line and installation sit in each page's collapsible "Go deeper" sections.
The screenshots in `assets/screens/` are real: the three GUIs running against
a copy of Pleasant Stay, with one extra in-progress Phase added to that copy
so the map shows every status.

Open `index.html` in a browser, or serve the folder:

```bash
php -S localhost:8000 -t website
```

Each tool has one colour, shared with its GUI:

| Tool | Light | Dark |
|---|---|---|
| Barnspec (mint) | `#1daf8d` fill, `#0d6d5a` text | `#39d0ad` |
| Barnark (orange) | `#bc4c00` | `#f0883e` |
| Barncept (sky blue) | `#0376a7` | `#42bff8` |

A page takes its colour from `<body data-brand="spec|ark|cept">`, and any
element with `data-brand` takes that tool's colour. The tokens are at the top
of `assets/site.css`.
