# Bio-Info Exercises (BIO-463)

## Project Setup

- R 4.5.3 installed via Homebrew
- renv environment at project root — run `renv::restore()` to install packages
- Quarto renders `.qmd` files to HTML (with `embed-resources: true`) and PDF
- VS Code with Quarto extension for editing/previewing

## R Packages

- `ape` — phylogenetics (read.dna, dist.dna, bionj, root, ladderize)
- `adegenet` — population genetics

## Rendering

**Always run `quarto render` from the project root**, not from a subdirectory.
The renv activation script lives at `./.Rprofile` and is only sourced when R
starts in the root. Running from a subdirectory uses system R, which lacks
`knitr`, `rmarkdown`, and the assignment packages — the render will fail with
"there is no package called 'rmarkdown'". Knitr sets the working directory to
the document's folder, so relative paths inside the `.Rmd`/`.qmd` still
resolve correctly.

```bash
# From /Users/aw/code/bio-info
quarto render week6/ExercisesWeek6.qmd --to html
quarto render Assignment2/Assignment.Rmd --to html
```

## Data Files (week6)

- `week6/spike_seq.fasta` — SARS-CoV-2 spike gene nucleotide sequences
- `week6/spike_annot.csv` — sequence annotations (collection date, Pango lineage)
