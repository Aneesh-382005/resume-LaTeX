# Resume LaTeX Build Pipeline

This repository stores resume source in LaTeX and automatically builds and commits a PDF whenever `src/main.tex` changes on `main`.

## Repository Structure

- `src/main.tex`: public resume source (compiled by CI)
- `dist/`: build output folder (CI writes `Aneesh_Grover_Resume.pdf` here)
- `.github/workflows/build-and-publish-resume.yml`: CI/CD workflow

## Local Build

You can build locally with TeX Live + `latexmk`:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error -output-directory=dist src/main.tex
```

Expected output:

- `dist/main.pdf` (local default name)

If you want the exact CI filename locally:

```bash
cp dist/main.pdf dist/Aneesh_Grover_Resume.pdf
```

## CI and Publishing

On every push that changes `src/main.tex` on `main`, GitHub Actions:

1. Compiles `src/main.tex`
2. Moves the compiled PDF to `dist/Aneesh_Grover_Resume.pdf`
3. Uploads the PDF as a workflow artifact (`resume-pdf`)
4. Commits `dist/Aneesh_Grover_Resume.pdf` back into the repo

## Public PDF URL Pattern

The simplest stable URL is the raw GitHub file URL:

`https://raw.githubusercontent.com/<github-username>/<repository-name>/main/dist/Aneesh_Grover_Resume.pdf`

For this repo, that will be:

`https://raw.githubusercontent.com/Aneesh-382005/resume-LaTeX/main/dist/Aneesh_Grover_Resume.pdf`

That repo file can also be opened directly from the GitHub UI under `dist/Aneesh_Grover_Resume.pdf`.
