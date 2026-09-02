# Resume / CV sources

LaTeX sources for the resume, mirrored from the Overleaf project.

`resume_special.tex` is the version currently compiled on Overleaf and the one
published on the website.

## Layout

| Path | Contents |
| --- | --- |
| `resume_*.tex` | One top-level document per resume variant (special, quant, ds, research, biostat, consulting, ...) |
| `global/` | Sections shared by every variant (education, awards, publications) |
| `sections/`, `sections_<variant>/` | Per-variant objective / experience / projects / skills |

Each `resume_*.tex` carries its own preamble and `\input`s the sections it needs,
so variants can diverge freely.

## Building locally

Needs a TeX distribution with `latexmk` and `pdflatex` — on macOS,
[MacTeX](https://tug.org/mactex/) (or `brew install --cask mactex-no-gui`).
If `latexmk` isn't on your `PATH`, add TeX Live's bin directory:

```bash
export PATH="/Library/TeX/texbin:$PATH"
```

Then:

```bash
make            # build resume_special.tex -> build/resume_special.pdf
make all        # build every resume_*.tex variant
make resume_ds  # build one specific variant
make watch      # rebuild on save
make clean      # remove build artifacts
```

Output goes to `build/`, which is git-ignored.

## Publishing to the website

`cv.html` and `index.html` link to `assets/pdf/resume_KZhang.pdf`. To rebuild the
resume and refresh that file:

```bash
make publish
```

This keeps the copy checked into the repo current. It is optional, though: the
deploy workflow (`.github/workflows/deploy.yml`) compiles `resume_special.tex`
itself on every push to `master` and copies the result over
`assets/pdf/resume_KZhang.pdf` before publishing, so **the live site always
serves a PDF built from the sources in this folder** — editing a `.tex` file and
pushing is enough.

Run `make publish` when you also want the committed PDF to match what the site
will serve.
