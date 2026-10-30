# 3 Dataset and preprocessing

*Draft by Sayed Fadhul Hashem. Reference numbers continue from Section 1 and will be renumbered when the report is assembled. Items marked TO CONFIRM wait for notebook cells that are not written yet.*

## 3.1 Dataset description

RealWaste [5], [6] contains 4,752 colour photos of waste received at the Whyte's Gully Waste and Resource Recovery facility in Wollongong, Australia. Each photo is 524 × 524 pixels and carries one of nine material labels (Table I); the raw RGB pixels are the only input features. The UCI page lists the licence as CC BY 4.0, but the authors' README in the archive states CC BY-NC-SA 4.0, so we follow the stricter terms: non-commercial academic use and no redistribution of the images.

**Table I.** Dataset summary

| Item | Detail |
|---|---|
| Source | UCI Machine Learning Repository [6]; paper by the dataset's authors [5] |
| Licence | CC BY-NC-SA 4.0 (archive README); CC BY 4.0 (UCI page) |
| Size | 4,752 JPEG photos, 524 × 524 × 3; 656.6 MB zip |
| Classes (photos) | Plastic 921, Metal 790, Paper 500, Miscellaneous Trash 495, Cardboard 461, Vegetation 436, Glass 420, Food Organics 411, Textile Trash 318 |
| Integrity | SHA-256 fingerprint of the zip recorded; every class count matches the authors' published numbers |

The data have known limitations. All photos come from one site, and every one we viewed shows a single item or pile on a light concrete floor, so a model may learn this setting as well as the material. Miscellaneous Trash is a catch-all class of unrelated items, and the packaging and brands are Australian rather than Bahraini. A seeded check of 12 Paper and Cardboard photos found no readable name or address, but the Paper class contains envelopes (Section 6.5).

[Fig. 1: Sample photos from each class. TO CONFIRM: export of Ali Haji's sample grid in notebook section 3.0.]

## 3.2 Exploratory data analysis

Fig. 2 shows the class balance. Plastic has 921 photos and Textile Trash 318, a ratio of 2.9 to 1, and always predicting Plastic would already score 19.4% accuracy. This led to three decisions: a stratified split (Section 3.4), macro-averaged F1 as the headline metric (Section 4.6) and a test of class weights (Section 5.2).

[Fig. 2: Images per class. Export of notebook Figure 1.]

A SHA-256 hash of every file found no identical files. To find re-shots of the same item, we compared 256-bit difference hashes [7], which record where brightness rises between neighbouring pixels of a small greyscale copy, across every pair of photos. Only two pairs differ in fewer than 24 bits, each showing one item photographed twice (Fig. 3); the four closest pairs above this cut-off, at 26 and 29 bits, show different items. Each pair is kept inside one set (Section 3.4), so the model is never tested on a photo it has effectively seen. A hash cannot catch an item re-photographed from a very different angle (Section 6.4).

[Fig. 3: Near-duplicate pairs, then the closest pairs that are different items. Export of notebook Figure 3.]

[TO CONFIRM: Mohamed Alradhi's image size and brightness figure and the augmentation choice it supports.]

## 3.3 Preprocessing pipeline

1. **Integrity.** Every run checks the download's SHA-256 fingerprint and recounts the photos per class, so all results use identical data. [TO CONFIRM: number of unreadable images from Mohamed Alradhi's scan in notebook section 2.0.]
2. **Encoding.** Class names become integer labels 0 to 8 in alphabetical order (Cardboard = 0, Vegetation = 8).
3. **Resizing and scaling.** [TO CONFIRM when implemented] Photos are resized to 224 × 224, MobileNetV2's ImageNet input size [8], and scaled by fixed rules (divided by 255 for the baseline, mapped to −1 to 1 for MobileNetV2 [11]), so no statistic is learned from the data and no test information can leak into training.
4. **Augmentation.** [TO CONFIRM when implemented] Random flips, rotations and zooms are applied to training photos only, to reduce overfitting on 2,851 training photos.

## 3.4 Train, validation and test split

We split the data 60/20/20, the ratio the course recommends for datasets under 10,000 samples [9]. Following the same guidance, the split is stratified because the classes are imbalanced, and grouped so that each near-duplicate pair stays in one set. scikit-learn's `StratifiedGroupKFold` [10], applied twice, takes one of five folds as the test set and then one of the four remaining folds as the validation set. Every class's share in each set is within 0.1 percentage points of its overall share (Table II), and neither pair crosses two sets. A fixed seed (42) makes the split repeatable, and a fingerprint of the test-set file names (`e9c3df307b09`) shows whether another computer, running scikit-learn 1.9.1, produces the same split. The test set is used only once, for the final evaluation (Section 5.3).

**Table II.** Split sizes and class shares (% of each set)

| Class | Training | Validation | Test | All |
|---|---|---|---|---|
| Cardboard | 9.7 | 9.7 | 9.7 | 9.7 |
| Food Organics | 8.6 | 8.7 | 8.6 | 8.6 |
| Glass | 8.8 | 8.8 | 8.8 | 8.8 |
| Metal | 16.6 | 16.6 | 16.6 | 16.6 |
| Miscellaneous Trash | 10.4 | 10.4 | 10.4 | 10.4 |
| Paper | 10.5 | 10.5 | 10.5 | 10.5 |
| Plastic | 19.4 | 19.4 | 19.5 | 19.4 |
| Textile Trash | 6.7 | 6.6 | 6.6 | 6.7 |
| Vegetation | 9.2 | 9.2 | 9.3 | 9.2 |
| **Photos** | **2,851 (60.0%)** | **950 (20.0%)** | **951 (20.0%)** | **4,752** |

## References used in this section

[5] S. Single, S. Iranmanesh, and R. Raad, "RealWaste: A novel real-life data set for landfill waste classification using deep learning," *Information*, vol. 14, no. 12, Art. no. 633, 2023, doi: 10.3390/info14120633.

[6] S. Single, S. Iranmanesh, and R. Raad, "RealWaste," UCI Machine Learning Repository, 2023, doi: 10.24432/C5SS4G.

[7] N. Krawetz, "Kind of like that," *The Hacker Factor Blog*, Jan. 21, 2013. Accessed: Oct. 30, 2026. [Online]. Available: https://www.hackerfactor.com/blog/index.php?/archives/529-Kind-of-Like-That.html

[8] M. Sandler, A. Howard, M. Zhu, A. Zhmoginov, and L.-C. Chen, "MobileNetV2: Inverted residuals and linear bottlenecks," in *Proc. IEEE/CVF Conf. Comput. Vis. Pattern Recognit. (CVPR)*, 2018, pp. 4510–4520, doi: 10.1109/CVPR.2018.00474.

[9] "Week 2, Part A: From dataset to prediction: The foundations," IT8414 Deep Learning for Data Analytics lecture slides, Bahrain Polytechnic, 2026.

[10] scikit-learn developers, "StratifiedGroupKFold," scikit-learn 1.9.1 documentation. Accessed: Oct. 30, 2026. [Online]. Available: https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.StratifiedGroupKFold.html

[11] TensorFlow developers, "tf.keras.applications.mobilenet_v2.preprocess_input," TensorFlow API documentation. Accessed: Oct. 30, 2026. [Online]. Available: https://www.tensorflow.org/api_docs/python/tf/keras/applications/mobilenet_v2/preprocess_input
