# Work log

Each member adds their own entries, in date order, and commits them from their own GitHub account. The commit history is the second record of who did what.

## Before Week 7 (to 31 Oct 2026)

| Date | Member | Work done | Evidence |
|---|---|---|---|
| 2026-10-30 | Sayed Fadhul Hashem | Created the GitHub repository | Commit 1c7c231 |
| 2026-10-30 | Sayed Fadhul Hashem | Read the project brief and marking sheet; planned the project: dataset (RealWaste), models (custom CNN and MobileNetV2 transfer learning), role split and timeline to 4 Jan 2027 | README.md |
| 2026-10-30 | Sayed Fadhul Hashem | Set up the repository structure: README, DATA.md, work log, sources log and notebook skeleton | Commit 46abb21 |
| 2026-10-30 | Sayed Fadhul Hashem | Organised the repository into folders: notebooks, docs, report and slides | Commit 632c27b |
| 2026-10-30 | Sayed Fadhul Hashem | Updated the role split: swapped Ali's and Mohamed's areas, and made each role one lead with the other two members as contributors | Commit 04dbe1b |
| 2026-10-30 | Sayed Fadhul Hashem | Downloaded RealWaste and ran first checks: 4,752 images, class counts match, all readable and 524 × 524, no exact duplicates; found near-duplicate photos to handle in the split | docs/DATA.md |
| 2026-10-30 | Sayed Fadhul Hashem | Wrote notebook section 2.0 (download with fingerprint check, image table, recount against the published counts) and the dataset-paths cell in 1.0 | Notebook 1.0 and 2.0 |
| 2026-10-30 | Sayed Fadhul Hashem | Installed Python 3.12 and a project environment on the demo laptop; ran sections 1.0 and 2.0 there: 4,752 images, every class count matches | Notebook 2.0 outputs |
| 2026-10-30 | Sayed Fadhul Hashem | Rebalanced the roles: Mohamed now leads Grad-CAM (9.1) and the prediction-on-any-image cell (9.3); Ali leads transfer learning, error analysis and the conclusion | Commit 3276a90 |
| 2026-10-30 | Sayed Fadhul Hashem | Wrote section 3.0: Figure 1 class balance (2.9 to 1; majority baseline 19.4%) with the decisions it drives, and Figure 2 privacy check of Paper and Cardboard photos | Commit 5b02e2b |
| 2026-10-30 | Sayed Fadhul Hashem | Added the duplicate search and Figure 3 to 3.0: no identical files, 2 near-duplicate pairs (256-bit fingerprint, 24-bit cut-off checked by eye) | Notebook 3.0 |
| 2026-10-30 | Sayed Fadhul Hashem | Wrote the 4.0 split: stratified and grouped 60/20/20 (2,851 / 950 / 951), with leakage and balance checks (no group crosses sets; class shares within 0.1 points) and a test-set fingerprint | Notebook 4.0, docs/DATA.md |

## Week 7 (1–5 Nov 2026)

| Date | Member | Work done | Evidence |
|---|---|---|---|
