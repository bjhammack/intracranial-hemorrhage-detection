# Identifying Intracranial Hemorrhaging in CT Scan Images
(note: to read the comprehensive and detailed write-up on this project please view intracranial_hemorrhage_detection_writeup.pdf)

Brain hemorrhaging can be one of the most dangerous situations a person faces. If not identified and treated quickly, it can put your life in serious danger and potentially cause long lasting damage. Identifying hemorrhages in CT scans quickly and accurately is often the deciding factor between which of these situations come to fruition.

This project employs a neural network inside a Jupyter Notebook to analyze 100,000+ images of brain CT scans and identify A) whether hemorrhaging is occurring and B) what type of hemorrhaging is occuring.

# The Data
The CT images for this project were orignally for [this Kaggle competition](https://www.kaggle.com/c/rsna-intracranial-hemorrhage-detection). Unfortunately, I found the competition too late to join the competition itself, but with the dataset still available, the challenge of the project intrigued me.

The CT scans come in the [DICOM](https://www.dicomstandard.org) image format, which is considered the international standard for medical imaging formats. What makes DICOM images so useful for medical imaging is its metadata. Every DICOM image comes with a robust set of metadata which can contain anything from patient ID, to the degrees of the image's rotation.

Roughly 650,000 DICOM images were provided for this project, but for the sake of testing speed, 100,000 images were used during testing (due to the sheer number, these are not uploaded to this repo. Please follow the Kaggle link to find them).

Along with the images, a CSV containing patient ID and hemorrhaging information was provided for training and testing the model.

DICOM Image example at 75x75 resolution:
![DICOM](https://github.com/bjhammack/intracranial_hemorrhage_detection/blob/master/images/image_sample_v2.png?raw=true "DICOM Image")

# Data Analysis


# Data Transformation


# Neural Network


# Final Thoughts
