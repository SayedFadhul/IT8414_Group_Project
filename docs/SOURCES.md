# Sources adapted

Every tutorial, documentation page, repository or course example that our code or text draws on, and what we changed. This becomes Appendix C of the report. Add a row when you adapt something, in the same commit as the code.

| Source | Used for | Where in our work | What we changed | Added by | Date |
|---|---|---|---|---|---|
| IT8414 Lab 5 notebook (Week 5), "Quick look at the data" cell | Showing photos in a grid with titles | Notebook 3.0, Figures 2 and 3 | Shows a fixed, seeded sample of Paper and Cardboard photos (Figure 2, our privacy check) and the closest fingerprint pairs (Figure 3), with file names as titles | Sayed Fadhul Hashem | 2026-10-30 |
| N. Krawetz, "Kind of Like That", The Hacker Factor Blog, 2013 (the difference hash, dHash) | Near-duplicate image fingerprints | Notebook 3.0, duplicate search | Our own 256-bit version (17×16 grey pixels) in NumPy; each photo compared with every other photo in a loop (see the Lab 2A row); cut-off of 24 bits chosen by looking at the closest pairs | Sayed Fadhul Hashem | 2026-10-30 |
| scikit-learn documentation, `StratifiedGroupKFold` | A stratified split that keeps groups together | Notebook 4.0, split cell | Used twice (5 folds, then 4) to make one 60/20/20 split instead of cross-validation | Sayed Fadhul Hashem | 2026-10-30 |
| IT8414 Lab 5 notebook (Week 5), setup cell | All imports and one fixed `SEED` in one setup cell | Notebook 1.0, data setup cell | Holds only what sections 2.0 to 4.0 need: libraries, seed, data paths and the class list | Sayed Fadhul Hashem | 2026-11-10 |
| IT8414 Lab 1 notebook (Week 1), results table (`rows.append`, then `pd.DataFrame`) and bar labels (`ax.text` in a loop) | Building a table one row at a time; writing values next to horizontal bars | Notebook 2.0, image table; 3.0, Figure 1 | One row per photo (path, file name, class, label) instead of one per prediction; each bar label shows a class count and its share of all photos | Sayed Fadhul Hashem | 2026-11-10 |
| IT8414 Lab 2A solution notebook (Week 2), nearest-neighbour `predict` loop | Comparing one row with every other row | Notebook 3.0, duplicate search | Counts differing fingerprint bits instead of Euclidean distance, and keeps every pair under 30 bits instead of only the nearest neighbour | Sayed Fadhul Hashem | 2026-11-10 |
