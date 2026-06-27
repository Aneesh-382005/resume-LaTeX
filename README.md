# Resume LaTeX Build Pipeline

This repository stores resume source in LaTeX and automatically builds a public PDF on every push to `main`.

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

On every push to `main`, GitHub Actions:

1. Compiles `src/main.tex`
2. Moves the compiled PDF to `dist/Aneesh_Grover_Resume.pdf`
3. Uploads the PDF as a workflow artifact (`resume-pdf`)
4. Publishes `dist/` to GitHub Pages

## Public PDF URL Pattern

After enabling Pages for this repository, the public resume URL is:

`https://<github-username>.github.io/<repository-name>/Aneesh_Grover_Resume.pdf`

For this repo, that will be:

`https://Aneesh-382005.github.io/resume-LaTeX/Aneesh_Grover_Resume.pdf`
