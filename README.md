# Math 121 Course Documents — Fall 2008 (NYU)

Course documents for **Math 121: Calculus I** at New York University, Fall 2008, by [Matthew Leingang](https://github.com/leingang).

## Contents

```
.
├── bin/                  # Utility scripts
│   └── remove-bad-ents.pl   # Perl script to normalize HTML entities/ligatures
├── docs/                 # Source documents (reStructuredText)
│   ├── cal.txt           # Course calendar (weekly schedule of topics)
│   ├── hw.txt            # Homework assignments (15 weeks of problem sets)
│   ├── lessons.txt       # Detailed lesson outlines with learning objectives
│   └── Makefile          # Build rules for this directory
└── lib/                  # Build toolchain and shared libraries
    ├── docutils-0.5/     # Bundled Docutils (rst→HTML converter)
    ├── html2isite.xsl    # XSLT to strip HTML down for iSites CMS upload
    ├── htmlscreen.xsl    # XSLT to produce screen-optimized HTML
    ├── isites.mk         # Make rules for iSites-targeted output
    ├── latex_directive.py      # Docutils directive: render LaTeX → PNG
    ├── latex_tth_directive.py  # Alternate LaTeX directive using tth
    ├── new.css           # Stylesheet for generated HTML
    ├── rst.mk            # Make rules for reStructuredText → HTML / PDF
    ├── rst2html.py       # Entry-point wrapper for rst2html
    ├── tex.mk            # Make rules for LaTeX → DVI / PS / PDF
    └── tex4ht.mk         # Make rules for LaTeX → HTML via tex4ht
```

## Course Overview

Math 121 is a first-semester calculus course covering:

| Weeks | Topics |
|-------|--------|
| 1–3   | Functions, limits, and continuity |
| 4–5   | Derivatives and differentiation rules |
| 6–7   | Exponential, logarithmic, and inverse trig functions |
| 8     | L'Hôpital's Rule, exponential growth and decay |
| 9–10  | Applications of derivatives (curve sketching, optimization) |
| 11–12 | Integration and the Fundamental Theorem of Calculus |
| 13–15 | Techniques of integration (parts, partial fractions, improper integrals) |

## Building

The documents are written in [reStructuredText](https://docutils.sourceforge.io/rst.html) and converted to HTML using [Docutils](https://docutils.sourceforge.io/) (version 0.5, bundled in `lib/docutils-0.5`).

### Prerequisites

- Python (2.x)
- `make`
- `xsltproc` (for XSLT-based HTML post-processing)
- `perl` (for `bin/remove-bad-ents.pl`)
- `pdflatex` / `latex` + `dvipng` (optional, for LaTeX math rendering)
- `wkpdf` (optional, for HTML → PDF conversion)

### Generate HTML

```bash
cd docs
make
```

This produces:
- `*.html` — full standalone HTML pages
- `*-screen.html` — screen-optimized HTML (via `htmlscreen.xsl`)

### Targets

| Target | Description |
|--------|-------------|
| `make` / `make all` | Build all HTML files |
| `make dist` | Zip output files for upload (requires clean SVN working copy) |
| `make clean` | Remove generated files |

## Notes

- Source files use SVN keyword substitution (`$Id$`, `$Date$`, `$HeadURL$`).
- The `iSites` targets produce HTML suitable for embedding in Harvard's iSites course management system.
- The bundled `docutils-0.5` is used instead of a system-installed version to ensure reproducibility.
