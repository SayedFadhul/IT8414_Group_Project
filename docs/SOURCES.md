# Sources adapted

Every tutorial, documentation page, repository or course example that our code or text draws on, and what we changed. This becomes Appendix C of the report. Add a row when you adapt something, in the same commit as the code.

| Source | Used for | Where in our work | What we changed | Added by | Date |
|---|---|---|---|---|---|
| IT8414 Lab 1 notebook (Week 1), `try_download` helper | Downloading a file with a browser User-Agent header | Notebook 2.0, download cell | Streams the 656.6 MB zip straight to disk, adds a SHA-256 fingerprint check, and unzips only when the images are missing | Sayed Fadhul Hashem | 2026-10-30 |
| IT8414 Lab 5 notebook (Week 5), "Quick look at the data" cell | Showing photos in a grid with titles | Notebook 3.0, Figure 2 | Uses a fixed, seeded sample of Paper and Cardboard photos, shows file names as titles, and uses the grid for a privacy check | Sayed Fadhul Hashem | 2026-10-30 |
| Matplotlib documentation, `Axes.bar_label` | Writing values on bars | Notebook 3.0, Figure 1 | Labels show each class's count and share on a horizontal bar chart | Sayed Fadhul Hashem | 2026-10-30 |
| N. Krawetz, "Kind of Like That", The Hacker Factor Blog, 2013 (the difference hash, dHash) | Near-duplicate image fingerprints | Notebook 3.0, duplicate search | Our own 256-bit version (17×16 grey pixels) in NumPy; all pairs compared at once with a matrix product; cut-off of 24 bits chosen by looking at the closest pairs | Sayed Fadhul Hashem | 2026-10-30 |
| scikit-learn documentation, `StratifiedGroupKFold` | A stratified split that keeps groups together | Notebook 4.0, split cell | Used twice (5 folds, then 4) to make one 60/20/20 split instead of cross-validation | Sayed Fadhul Hashem | 2026-10-30 |
