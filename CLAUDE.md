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

```bash
quarto render week6/ExercisesWeek6.qmd --to html
```

## Data Files (week6)

- `week6/spike_seq.fasta` — SARS-CoV-2 spike gene nucleotide sequences
- `week6/spike_annot.csv` — sequence annotations (collection date, Pango lineage)
