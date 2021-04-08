# Identifying Intracranial Hemorrhaging in CT Scan Images
(Note: for a more detailed write-up of the entire process, please read `comprehensive_report.pdf` found in the home directory of this repository.)

Brain hemorrhaging can be one of the most dangerous situations a person faces. If not identified and treated quickly, it can put your life in serious danger and potentially cause long lasting damage. Identifying hemorrhages in CT scans quickly and accurately is often the deciding factor between which of these situations come to fruition.

This project employs a neural network inside a Jupyter Notebook to analyze 100,000+ images of brain CT scans and identify A) whether hemorrhaging is occurring and B) what type of hemorrhaging is occuring.

# The Data
The CT images for this project were orignally for [this Kaggle competition](https://www.kaggle.com/c/rsna-intracranial-hemorrhage-detection). Unfortunately, I found the competition too late to join the competition itself, but with the dataset still available, the challenge of the project intrigued me.

The CT scans come in the [DICOM](https://www.dicomstandard.org) image format, which is considered the international standard for medical imaging formats. What makes DICOM images so useful for medical imaging is its metadata. Every DICOM image comes with a robust set of metadata which can contain anything from patient ID, to the degrees of the image's rotation.

Roughly 650,000 DICOM images were provided for this project, but for the sake of model speed during testing, 100,000 images were used for several of the steps (due to the sheer number, the images are not uploaded to this repo. Please follow the Kaggle link to find them).

Along with the images, a CSV containing patient ID and hemorrhaging information was provided for training and testing the model.

DICOM Image example at 75x75 resolution:

![DICOM](https://github.com/bjhammack/intracranial_hemorrhage_detection/blob/master/images/image_sample_v2.png?raw=true "DICOM Image")

# Data Import
Before analysis could take place, several transformative steps needed to be taken to have interpretable data.

First, the training label CSV needed to be transformed into a format that could actually be used for training. After this, the images needed to be imported, their patient IDs and pixel arrays extracted, then they needed to be matched to their training label, so I could actually identify what types of hemorrhaging were occuring in each image.

With this all complete, the data was in a condition for initial analysis.

## Note
After import, the numpy arrays of both the images and the labels that were imported are written to .npy files in the `/data/` folder. This is so subsequent analysis can be performed without going through the tedious image import every time. These files do NOT contain the whole dataset and may not be the version of the import used in the final iteration of the model.

# Neural Network
The neural network went through several iterations, each one pursuing a new angle or incorporating new transformations to the data. This section will only cover the final form of the model; if you wish to read about each iteration, the thought process behind each, and the results of them please read `comprehensive_report.pdf` found in the home directory of this report.
