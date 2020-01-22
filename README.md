# Identifying Intracranial Hemorrhaging in CT Scan Images
(Note: for a more detailed write-up of each step, please view the Jupyter Notebook itself.)

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

# Data Analysis


# Data Transformation


# Neural Network
The neural network went through several iterations, each one pursuing a new angle or incorporating new transformations to the data. 

## Iteration 1
The first iteration used images at a resolution of 50x50, used 3 hidden dense layers with relu activation, two droupout layers, had an output layer with sigmoid activation, and binary crossentropy as its loss function. This provided the following results:

Loss:

![loss](https://github.com/bjhammack/intracranial_hemorrhage_detection/blob/master/images/model_loss_v1.png?raw=true "Loss")

Acc:

![acc](https://github.com/bjhammack/intracranial_hemorrhage_detection/blob/master/images/model_acc_v1.png?raw=true "Accuracy")

While these results were encouraging for a first pass, two immediate questions needed to be answered: 1) Was the image resolution preventing the model from being any more accuract? 2) Was the model performing so well due to overfitting? Iteration 2 shed some light on the first question.

## Iteration 2
Iteration 2 kept an identical model to iteratoin 1, the only differencd was that now the images were 75x75 resolution, instead of 50x50. After running the model, almost identical results were achieved, with 0.449 loss and 0.815 accuracy. This made me feel comfortable going back to 50x50 images, for the sake of processing speed, and allowed me to shift my focus to examining the possibility of much more integral data issues causing these results for iteration 3.

## Iteration 3
Iteration 3 saw two major changes. First, the distribution of hemorrhaging images was altered. For the previous two iterations, half the images imported were images without any hemorrhaging and the other half were randomly selected positive hemorrhaging images. Now, to test and see if the large count of negative hemorrhaging images were allowing the model to be overfit, 90% of the images would be randomly selected positive hemorrhaging images. If the model was overfitting, surely the large influx of hemorrhaging images would cause a noticeable decrease in performance. Secondly, an extra set of data was introduced. 25,000 new images would be used to test the model's predictive power after it had been trained, providing more metrics for us to examine. The model itself remained the same.

# Final Thoughts
