# Data

## Dataset

| Item | Detail |
|---|---|
| Name | RealWaste |
| Source | UCI Machine Learning Repository: https://archive.ics.uci.edu/dataset/908/realwaste |
| DOI | 10.24432/C5SS4G |
| Licence | Creative Commons Attribution 4.0 International (CC BY 4.0) |
| Download | `realwaste.zip`, 656.6 MB |
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

These are the counts published on the UCI page. The notebook recounts the downloaded files in section 2.0.

## Citation

[1] S. Single, S. Iranmanesh, and R. Raad, "RealWaste: A novel real-life data set for landfill waste classification using deep learning," *Information*, vol. 14, no. 12, p. 633, 2023.

[2] S. Single, S. Iranmanesh, and R. Raad, "RealWaste," UCI Machine Learning Repository, 2023. doi: 10.24432/C5SS4G.

## How to get the data

1. Download `realwaste.zip` from the UCI page above.
2. Extract it into a `data/` folder at the top of this repository. The exact folder names inside the archive are checked in notebook section 2.0.
3. `data/` is listed in `.gitignore`, so the images are never committed.

A preparation script (download, checks and split) will be added here once it is written.

## Notes

- The same dataset is also listed on IEEE DataPort under a different licence (CC BY-NC-SA 4.0), where it needs a subscription. We use the UCI copy.
- Full-size images are available from the dataset's authors on request. We use the 524 × 524 release.
