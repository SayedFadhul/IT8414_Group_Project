# 1 Introduction

*Draft by Sayed Fadhul Hashem. Reference numbers are local to this section and will be renumbered when the report is assembled.*

## 1.1 Problem statement and motivation

Global municipal solid waste is projected to grow from 2.01 billion tonnes a year in 2016 to 3.40 billion by 2050 [1]. Bahrain collected 1.477 million tonnes of municipal waste in 2025 [2]. Its main municipal landfill, at Askar, reached its end-use capacity in 2016 yet still receives waste [3], and a new engineered landfill is being planned [4]. Every recyclable item buried there loses its value and takes up scarce space.

This project builds an image classifier that names a waste item's material from a photo, as a decision aid for our end users: landfill reception and material-recovery staff, who must recognise materials quickly and consistently. Real waste is dirty, crushed and mixed: a model trained on photos of clean objects reached only 49.69% accuracy on real landfill waste, against 89.19% for a model trained on real waste [5]. We therefore use RealWaste, photographed at a landfill's reception point [5], [6].

## 1.2 Aim and objectives

**Aim:** to build and critically evaluate deep learning models that classify photos of landfill waste into nine material classes.

**Objectives:**
1. Split the data 60/20/20, stratified and with near-duplicate photos kept together, and show that no information leaks between the sets.
2. Train a custom convolutional neural network (CNN) as a baseline and a MobileNetV2 transfer-learning model, tuning at least three hyperparameters on the validation set.
3. Compare both models on the held-out test set using macro-averaged F1, accuracy, per-class precision and recall, confusion matrices and ROC-AUC, against a majority-class baseline (Section 3.2), and recommend one for deployment.
4. Explain the models' decisions with Grad-CAM and analyse their errors class by class.

## 1.3 Scope and assumptions

The task is single-label classification of one item or pile per photo. Detecting several items in one scene, conveyor integration and real-time operation are out of scope. We assume the dataset's labels are correct. RealWaste was photographed at one Australian site, so we assume, and later question (Section 6.4), that its items resemble the waste arriving in Bahrain.

## 1.4 Report structure

Section 2 reviews related work and theory, Section 3 the dataset and its preparation, and Section 4 the models, training and evaluation methods. Section 5 reports the results, Section 6 discusses them, including limitations and ethics, and Section 7 concludes with future work.

## References used in this section

[1] S. Kaza, L. C. Yao, P. Bhada-Tata, and F. Van Woerden, *What a Waste 2.0: A Global Snapshot of Solid Waste Management to 2050*. Washington, DC, USA: World Bank, 2018, doi: 10.1596/978-1-4648-1329-0.

[2] "Homes generate 40pc of Bahrain's waste," *Gulf Daily News*, Manama, Bahrain, Jul. 24, 2026. Accessed: Oct. 30, 2026. [Online]. Available: https://www.gdnonline.com/Details/1401518

[3] M. A. K. Ebrahim, "Municipal waste landfill site selection model for Bahrain," M.Sc. thesis, Dept. Mech. Eng., Univ. of Bahrain, Sakhir, Bahrain, 2017. Accessed: Oct. 30, 2026. [Online]. Available: https://digitalrepository.uob.edu.bh/ar/node/1243

[4] "New engineered landfill planned for Askar City," *Daily Tribune*, Manama, Bahrain, Jul. 22, 2024. Accessed: Oct. 30, 2026. [Online]. Available: https://www.newsofbahrain.com/bahrain/101409.html

[5] S. Single, S. Iranmanesh, and R. Raad, "RealWaste: A novel real-life data set for landfill waste classification using deep learning," *Information*, vol. 14, no. 12, Art. no. 633, 2023, doi: 10.3390/info14120633.

[6] S. Single, S. Iranmanesh, and R. Raad, "RealWaste," UCI Machine Learning Repository, 2023, doi: 10.24432/C5SS4G.
