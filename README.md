# LaTeX Writing Template (Correspondence / Short-Form Articles)

This repository serves as a **reusable LaTeX template** for short-form scientific writing,
including **Nature Biomedical Engineering Correspondences**, brief perspectives, and
related article types. It is designed for **collaborative, version-controlled writing**
using Git.

The template emphasizes:
- Clean separation of content into small files
- Predictable LaTeX builds
- Minimal formatting assumptions (journal systems reflow content)
- Low merge-conflict overhead for multi-author work

---

## Intended Use

This template is optimized for:
- Nature-family Correspondences (e.g., *Nature Biomedical Engineering*)
- Short commentaries or perspectives
- Early-stage drafts prior to journal-specific class files

It is **not** intended for:
- Full-length technical articles with complex sectioning
- Camera-ready production PDFs (journal templates should be used later)

---

## Target Journal: Nature Biomedical Engineering — Correspondence

Correspondences discuss issues relevant to a broad slice of the biomedical engineering
community. They do **not** present original research and are distinct from *Matters Arising*.
Peer review is at the Editor’s discretion.

### Format constraints
- **Main text:** 300–800 words
- **Display items:** 1 figure total
- **References:** up to 10
- **Reference list:** article titles omitted (book titles allowed)
- Exceptions may be granted by the Editor on a case-by-case basis

---

## Repository Structure

```
project/
  tex/
    main.tex                 # Thin driver file
    macros.tex               # Shared macros and helper commands
    refs.bib                 # Bibliography (biblatex/biber)
    sections/
      01_maintext.tex
      02_figure_caption.tex
      03_acknowledgements.tex
      06_supplementary_figures.tex
  figures/                   # Figures (use Git LFS if large)
  build/                     # Auto-generated PDF and aux files
  Makefile
  .gitignore
```

---

## Build Instructions

### Requirements
- TeXLive (recommended: current year)
- `latexmk`
- `biber` (for bibliography)

### Build PDF
```bash
make pdf
```

### Clean build artifacts
```bash
make clean
```

The compiled PDF and auxiliary files are written to `build/`.

---

## Collaboration Conventions (Important)

### One sentence per line
Write prose with one sentence per line:
```tex
This is the first sentence.
This is the second sentence.
```

This dramatically improves Git diffs and reduces merge conflicts.

### One logical unit per file
Each major component lives in its own file under `tex/sections/`.
Avoid editing `main.tex` except for structure and ordering.

### Comments
Use lightweight comments for internal notes:
```tex
% TODO(Name): tighten this paragraph.
```

Remove TODOs before submission.

---

## Figures

- Only **one main figure** is allowed for Correspondence articles.
- Supplementary figures (if permitted) are grouped in
  `06_supplementary_figures.tex`.
- Supplementary figures are automatically numbered **S1, S2, ...**
  using helper macros defined in `macros.tex`.

---

## Bibliography

- Uses `biblatex` + `biber` for draft flexibility.
- Maintain a single `refs.bib` file per project.
- Use stable citation keys (e.g., `AuthorYearKeyword`).

Journal-specific `.cls` / `.bst` files can be introduced later if required.

---

## Version Control Notes

- Do **not** commit build artifacts.
- Use feature branches and pull requests for substantive edits.
- PDFs can be attached as CI artifacts or generated locally.

---

## Template Philosophy

This template is intentionally conservative.
It prioritizes:
- clarity over cleverness
- reproducibility over formatting polish
- collaboration over customization

Journal-specific styling should be applied **after acceptance**
using official publisher templates.

---

## License / Usage

This template is intended for internal academic use.
Adapt freely within your group or collaborators.
