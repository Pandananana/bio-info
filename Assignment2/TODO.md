# Assignment 2 — TODO

This todo list includes multiple tasks and their subtasks.

The file to work on is @Assignment.Rmd. Please work in this file, for example when you are showing your work, you shouldn't create unique scripts, it should be shown in the assignment, and compiled/rendered using Quarto to html.

> **Note on heavy chunks while iterating:** The two slowest chunks —
> `find_markers` (`FindAllMarkers`, ~5–10 min) and `cell_type_annotation`
> (`SingleR`, ~10–20 min) — are currently set to `eval=FALSE` so renders stay
> fast during iteration. When you reach **task 4** (markers) and **task 5**
> (SingleR), remove the `eval=FALSE` from those chunk headers in
> `Assignment.Rmd` so they actually execute. Their `cache=TRUE` flag means each
> only runs slowly once; subsequent renders reuse the cached results.

---

## 1. Choose dimensionality reduction parameters — **to do**

Inspect the existing PCA/elbow output and pick PC count.

- [ ] Run the existing PCA + `ElbowPlot` chunk and decide how many PCs to retain
- [ ] Update `dims` in `RunUMAP` to match the chosen PC count

## 2. Build neighbourhood graph and cluster — **to do**

Run clustering with chosen parameters.

- [ ] Set `dims` in `FindNeighbors` to match the UMAP `dims`
- [ ] Choose `k.param` for `FindNeighbors` (typical 20–30)
- [ ] Choose `resolution` for `FindClusters` (try 0.3, 0.5, 0.8, 1.0 — pick the one giving biologically sensible clusters)
- [ ] Choose clustering algorithm: Leiden (`algorithm = 4`) if `leidenAlg` available, else Louvain (`algorithm = 1`)

## 3. Visualise clusters (UMAP + spatial) — **to do**

Run the provided visualisation chunks and assess cluster quality.

- [ ] Render UMAP coloured by `seurat_clusters`
- [ ] Render spatial map of all clusters together on tissue coordinates
- [ ] Render per-cluster faceted spatial footprints
- [ ] Verify clusters look spatially coherent (consistent with brain anatomy); if not, return to group 2 and adjust resolution

## 4. Identify marker genes — **to do**

- [ ] Run `FindAllMarkers` (one-vs-rest, `only.pos = TRUE`)
- [ ] Inspect top 5 markers per cluster
- [ ] Note candidate cell-type identities based on known brain markers

## 5. Automated cell-type annotation with SingleR — **to do**

- [ ] Install/load `celldex`, load `MouseRNAseqData()` reference
- [ ] Run `SingleR` against `label.main` (and optionally `label.fine`)
- [ ] Transfer labels back to the Seurat object (`GE$SingleR_label`)
- [ ] Cross-check SingleR labels against marker-gene-based identities from group 4

## 6. Biological interpretation — **to do**

Synthesise findings into a coherent message.

- [ ] Map cluster spatial footprints to known mouse brain regions (cortex layers, hippocampus, striatum, white matter, ventricles, etc.)
- [ ] Decide on a single biological message the figure(s) should convey
- [ ] Identify the 1–2 most informative views (e.g. UMAP + annotated spatial map) to support that message

## 7. Build final figure(s) — **to do**

- [ ] Add a new section at the bottom of `Assignment.Rmd` for deliverables
- [ ] Produce one or two final figures (clear axes, meaningful colours, labels, annotations)
- [ ] Ensure figures are publication-quality (font sizes, legend, layout via `patchwork`)

## 8. Write figure legend — **to do**

- [ ] Write paper-style legend: data type, method, what is shown, definition of all visual elements (axes, colours, groups)
- [ ] Make legend self-contained (understandable without the rest of the document)

## 9. Write results paragraph — **to do**

- [ ] 3–4 sentences covering: (a) main observation, (b) biological meaning, (c) connection to mouse brain organisation / study context

## 10. Final submission — **to do**

- [ ] Knit `Assignment.Rmd` to HTML (and PDF if required)
- [ ] Verify rendered output looks correct
