# Data

## Dataset

| Item | Detail |
|---|---|
| Name | RealWaste |
| Source | UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/908/realwaste |
| DOI | 10.24432/C5SS4G |
| Licence | CC BY-NC-SA 4.0 according to the authors' README inside the archive; the UCI page lists CC BY 4.0. Both allow our non-commercial academic use with attribution, and we do not redistribute the images. |
| Download | `realwaste.zip`, 688,545,323 bytes (656.6 MB) |
| SHA-256 of the zip | `1EDE08B32358EE62065BCC1C8CB47A2ECE04E8DFF5B1FB53342BB8750895B2F3` (downloaded 30 Oct 2026) |
| Images | 4,752 colour photos, 524 × 524 pixels |
| Classes | 9 (counts below) |
| Collected at | The point of reception of a landfill: Whyte's Gully Waste and Resource Recovery facility, Wollongong, NSW, Australia |

| Class | Images |
|---|---|
| Plastic | 921 |
| Metal | 790 |
| Paper | 500 |
| Miscellaneous Trash | 495 |
| Cardboard | 461 |
| Vegetation | 436 |
| Glass | 420 |
| Food Organics | 411 |
| Textile Trash | 318 |
| **Total** | **4,752** |

These are the counts published on the UCI page and in the archive's README, and our download matches them exactly. The notebook recounts the files in section 2.0.

## Citation

[1] S. Single, S. Iranmanesh, and R. Raad, "RealWaste: A novel real-life data set for landfill waste classification using deep learning," *Information*, vol. 14, no. 12, p. 633, 2023.

[2] S. Single, S. Iranmanesh, and R. Raad, "RealWaste," UCI Machine Learning Repository, 2023. doi: 10.24432/C5SS4G.

## How to get the data

1. Download `realwaste.zip` from the UCI page above.
2. Extract it into a `data/` folder at the top of this repository. This creates `data/realwaste-main/RealWaste/`, with one folder per class, for example `data/realwaste-main/RealWaste/Food Organics/Food Organics_81.jpg`.
3. `data/` is listed in `.gitignore`, so the images are never committed.

Notebook sections 1.0 (paths) and 2.0 do these steps automatically: they download the zip if it is missing, check its SHA-256 fingerprint, unzip it and recount the images per class. The split is added in section 4.0.

## First checks (30 Oct 2026)

- All 4,752 files are JPEGs that open without errors. All are 524 × 524 pixels in 3-channel colour, and file sizes range from 48 KB to 243 KB.
- No two files are byte-for-byte identical.
- Some near-duplicates exist. For example, `Food Organics_81.jpg` and `Food Organics_82.jpg` show the same pile of waste photographed twice. A quick 64-bit image hash flagged 109 similar pairs, but the pairs we inspected were mostly different objects in a similar position on the same background, so a stronger check is needed. Notebook section 4.0 will find near-duplicates properly and keep each group in one split, so the test set holds no copies of training images.
- The photos we inspected show a single item or pile on a light concrete floor. The analysis in section 3.0 will check this across the dataset.

## Notes

- The same dataset is also listed on IEEE DataPort (CC BY-NC-SA 4.0), where it needs a subscription. We use the UCI copy.
- Full-size images are available from the dataset's authors on request. We use the 524 × 524 release.
