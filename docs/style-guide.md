# Barn website style guide

Established 11 November 2026. The standard for new and changed pages on the Barn website and on each
tool's own website (Barnspec, Barnark, Barntree).

**This guide extends the Barn suite base style guide** (`docs/style-guide.md` in the suite folder). The
base guide wins for anything it states: tool colours (§4), neutrals and themes (§5), typography and
wording (§6), spacing (§7), controls (§8), states (§9), accessibility and motion (§10). This guide adds
only what a website needs and the base guide lacks. `assets/base/` (shared) and `assets/site.css` (the main site) are the reference implementation:
where this guide and the stylesheet disagree, say so in the change and fix one of them.

The suite's `purpose.md` wins over both: no page is added for completeness, only for a
reader's real need.

## 1. Who the sites are for

A developer who has never heard of Barn and wants to know what a tool is, whether it suits them, and
how to try it. Each tool site reads as if the other tools did not exist. Barn appears only where it is
relevant, in a closing "Used in Barn" line, and the main Barn site is linked from the header and
footer, never required reading.

Users only. No internals, history or known issues. Those stay in each repository's `docs/`.

## 2. Page structure

Every page has, in order:

1. A **skip link** (`<a class="skip" href="#main">Skip to content</a>`), the first focusable element.
2. A **site header** (`header.site-header > .wrap`): the wordmark linking home, then one `nav` with an
   `aria-label`. `aria-current="page"` marks the current page.
3. `main#main`, holding **sections** (`section.section > .wrap`). A page opens with a **hero**
   (`.hero`) only where it introduces something: a home page or a tool's introduction. Documentation
   pages open with their heading (§4).
4. A **site footer** (`footer.site-footer`): the credit line and one `nav aria-label="Footer"`.

The header and footer markup is identical on every page of a site, apart from `aria-current`. There is
no build step to share it, so a check in the suite's `bin/ci-all` compares them.

Each page has:

- `<html lang="en-GB">`, `charset`, `viewport`;
- a `<title>` of the form `Page · Site`, and a `description` of one sentence;
- the tool's favicon (`assets/<tool>.svg`), and `<body data-brand="spec|ark|tree">` on a tool's pages
  (no `data-brand` on the Barn pages);
- one `h1`, and headings that never skip a level.

Links between a site's own pages are **relative and never start with `/`**, because a project site is
served from a subpath (`/<repository>/`). Every internal link resolves from the folder it is in.

### Go deeper

Detail that most readers don't need first goes in a `.deeper` list of `details` elements with a short
`summary` (a title and one line saying what is inside). The main pages lead with the idea and the
picture, and put terminology and commands in "Go deeper". Documentation pages don't use it: the
documentation is the deeper material, and its content stays visible and linkable.

## 3. Tool colour on a website

- A tool page sets `data-brand` on `body`; its header nav item and any card for that tool set their own.
  Components then read `--brand`, `--brand-ink`, `--brand-text`, `--brand-bright` and `--brand-tint`.
- **Links and coloured text use `--brand-text`.** `--brand-bright` is for fills, dots, borders and text
  on the dark code blocks. `--brand` with `--brand-ink` is the one primary button per page region.
- Don't hard-code a hex value in a page or a tool's `site.css`. Use a token. A new token goes in the
  master tokens and is reported in the change.
- The known gap in the base guide (§4) applies: no new small white-on-orange or white-on-sky text.

## 4. Documentation pages

Used for the "Documentation" section of a tool site. The layout (side navigation and page width) is
built in the shared stylesheet; this is how a page uses it.

- **Layout.** A page is a side navigation and one article. At narrow widths the navigation goes above
  the article and wraps, and the page never scrolls sideways.
- **Side navigation.** One `nav aria-label="Documentation"` listing every documentation page in
  reading order, grouped under a few plain headings. The current page has `aria-current="page"`. It is
  identical on every documentation page, apart from `aria-current`.
- **Article.** One `h1`, then `h2` and `h3` sections. Every `h2` and `h3` has an `id` and a visible
  self-link, so a section can be linked. Ids are lower-case words joined by hyphens and never change
  once published. Prose stays within 65 to 75 characters a line.
- **Order.** Say what a thing is, then how to do it, then the details. A task page starts with the
  task as a verb ("Add a role"), and ends with a link to what comes next.
- **Code, commands and output.**
  - A command is a `pre` with a `code` child. The prompt `$` is a `.p` span, so it can't be selected
    with the command. Output follows in the same block, with comments in `.c`.
  - A command shown is a command run: it is verified for real, in a disposable barn, with the released
    binaries, before it is published. Output shown is real output, trimmed only with a visible `…`.
  - Paths and names in prose use `code`. Show a path as the user would type it. Never show a local
    machine path.
  - Show one way to do a thing. Alternatives go in a short note after it.
- **Callouts.** Two kinds only: a **Note** (extra context) and a **Warning** (something loses data,
  or can't be undone). A callout starts with its kind in bold, never colour alone, and is rare. If a
  page has more than two, the page is trying to say too much.
- **Tables** hold comparisons and option lists, with a header row and `scope` on header cells. A table
  too wide for a phone scrolls within its own labelled region.
- **Glossary.** One page lists every term the tool introduces, in alphabetical order, each as a `dl`
  entry with an `id`. The first use of a term on a page links to its entry. A term means one thing
  across the whole site and matches the tool's own words (the GUI and CLI use the same ones).
- **When something goes wrong.** One short page per tool: the errors a user will really meet, in the
  tool's own words, each with what it means and what to do. Don't invent errors.

## 5. Wording on a website

The base guide's §6 applies. In addition:

- **British spelling**, sentence case headings, and curly apostrophes and quotes in prose.
- **Maturity note.** Every tool's introduction says, near the top and in plain words, that the tool is
  early (0.x) and not ready for real projects, until that stops being true. It is repeated nowhere
  else. A site never hard-codes something that goes stale (a version number, a count of features): it
  links to Packagist, or says "0.x".
- **"Used in Barn".** A closing line on a tool's introduction and in its quick start, saying what the
  tool is in a barn (a tab, or no tab) with a link to the main site. Nowhere else.
- **Install commands** match what is on Packagist at the time of writing.
- **Tone.** Direct, calm and specific. Say what the tool does and doesn't do. No superlatives, no
  marketing claims the tool doesn't back with a screenshot or a run, and no "simply" or "just".
- **Naming.** The base guide's rules and each tool's vocabulary apply: "area of business" is never
  shortened; Barnark says template, never schema; Barntree says Tree and its Tree words; nothing is
  described as being for PHP projects.
- **Third person** for roles, stories and scenarios, never "As a … I want …".

## 6. Images and screenshots

- Screenshots are **real captures** of the real tool, taken in Chrome at 2× resolution, of a
  disposable barn with made-up data (a hotel, a house). Never a mock-up, and never real project data
  or a local path.
- Files are `.webp` in `assets/screens/`, named for what they show (`spec-map`), and never renamed once
  published, because READMEs embed them by URL. A retaken shot replaces the file in place.
- Every `img` has `width` and `height` (so the page doesn't jump), `loading="lazy"` below the fold, and
  alt text that says what a reader would learn from the picture, not "screenshot of …".
- Wrap a screenshot in `figure.shot` with its `.shot-bar` caption, so it reads as a window. Don't add
  shadows or frames of your own.
- Illustrations (inline SVG) use the tokens, so they follow the theme and the tool colour, and carry
  `aria-hidden="true"` unless they say something the text doesn't.
- Retaking: record in the site's `README.md` the date, the version of the tool and what each shot
  shows, as the main site's README does.

## 7. Each site's own style guide

A tool's site has `docs/style-guide.md`. It begins "This guide extends the Barn website style guide"
with a link to this guide, and adds only that tool's vocabulary, colour and exceptions, each exception
with a reason, as each GUI's guide does. It may not contradict this guide.

### What a tool site may change

- Its own pages, its own `site.css` (tool-specific components only), its screenshots and its favicon.
- Its tool colour, only by using the master token.

### What it may not change

- The shared stylesheet copy (`assets/base/`). A change goes in the master and is copied to every site in
  the same change. The drift check fails when a copy differs.
- The header and footer structure, the skip link, the navigation pattern and the documentation layout.
- The base guide's rules. A rule that is wrong for every tool is changed in the base guide, not here.

## 8. Verifying a page

Look at the rendered page, not only the HTML.

- Open it in Chrome at about 375, 768 and 1280 pixels wide, in both light and dark themes, with no
  horizontal page scroll at any width.
- Tab through it: the skip link comes first, focus is always visible, and the order is logical.
- Follow every internal link and every image from the folder it is in, and check relative paths.
- Check contrast of `--brand-text` on the page background and `--brand-bright` on code blocks, in both
  themes.
- Run every command shown, as §4 says. A page whose command fails is wrong, not the command.
- Search the page for the wording rules in §5, and for any claim about a version, a feature or a
  release, which is checked against the tags and the tool itself.
- Report what was checked and what remains.

## 9. The stylesheets

- `assets/base/base.css` is the entry: it declares the cascade layers (`tokens`, `reset`, `layout`,
  `components`, `illustration`, `docs`) and imports one file per concern. Every other file reads only the tokens in
  `tokens.css` (colours are `light-dark(light, dark)`, so one declaration serves both themes).
- A component's responsive rules sit inside the component, as a nested `@media`. To change how
  something looks everywhere, change its file or its token; nothing else needs to move.
- `assets/site.css` is a site's own, unlayered, so it wins over `base/` without raising specificity.
  Put a component in `site.css` until a second site needs it, then move it to `base/` in the same
  change as the copies.
- Use the system's own tools before new ones: custom properties, `light-dark()`, nesting, grid, flex
  and `clamp()`. No preprocessor and no build step.
