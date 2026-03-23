# CV - Jon Zorrilla Gamboa (LaTeX)

A LaTeX-based curriculum vitae for Jon Zorrilla Gamboa, Data Scientist. Built with a custom `simplecv.sty` style file and `biblatex` for publications management. The document is organized into modular section files under `sections/`.

## Project structure

```
.
├── main.tex              # Main document entry point
├── simplecv.sty          # Custom CV style package
├── papers.bib            # BibTeX bibliography (publications)
└── sections/
    ├── experience.tex
    ├── education.tex
    ├── courses.tex
    ├── skills.tex
    ├── languages.tex
    ├── publications.tex
    ├── projects.tex
    ├── awards.tex
    ├── teaching.tex
    └── extracurricular.tex
```

## Prerequisites

This project requires a working LaTeX distribution. The setup below targets **WSL (Ubuntu/Debian)**.

### 1. Install LaTeX packages

```bash
sudo apt update
sudo apt install -y \
    texlive-latex-base \
    texlive-latex-extra \
    texlive-fonts-extra \
    texlive-lang-cyrillic \
    texlive-bibtex-extra \
    biber
```

> **Note:** `texlive-fonts-extra` provides `fontawesome5`. `texlive-lang-cyrillic` is required by the `babel` Russian language option in `simplecv.sty`. `biber` is the backend for `biblatex`.

Alternatively, install the full distribution to avoid missing package issues (larger download, ~5 GB):

```bash
sudo apt install -y texlive-full biber
```

### 2. (Optional) Install latexmk for automated builds

```bash
sudo apt install -y latexmk
```

## Cloning the repository

```bash
git clone https://github.com/Jonzg/cv-latex-en.git
cd cv-latex-en
```

If you use SSH:

```bash
git clone git@github.com:Jonzg/cv-latex-en.git
cd cv-latex-en
```

## Compilation

Because the document uses `biblatex` with the `biber` backend, it must be compiled in the following order:

```bash
pdflatex main.tex
biber main
pdflatex main.tex
pdflatex main.tex
```

### Using latexmk (recommended)

`latexmk` handles the multi-pass compilation automatically:

```bash
latexmk -pdf main.tex
```

To clean auxiliary files:

```bash
latexmk -c
```

The output PDF will be at `main.pdf`.
