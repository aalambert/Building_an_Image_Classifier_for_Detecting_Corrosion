# Capstone-Project: Building an Image Classifer for Detecting Corrosion


## Problem Statement

Corrosion of oilfield equipment and processing facilities is a common occurance that can pose a serious threat to the integrity of the facilities. Direct total costs due to corrosion are in the billions of dllars each year. Identifying corrosion is the first step in the analysis and prevention of corrosion-based failures. Visual inspection of corrosion can give insight into the degree of corrosion that is occuring. $ ~{1} $ It is hoped to be able to use computer vision in order to be able to identfy corrosion onsite. 

This project's goal is demonstrate proof of concept that computer vision can be used to indentify corrosion. Due to the lack of availability of open oilfield corrosion datasets, this project will use a generlized multi-class corrosion dataset with 5 differebt classes of corrosion. This dataset  has images that have been annotated with expert corrosion ratings obtained over 10 years of laboratory corrosion testing by material scientists. $ ~{2} $  

The goal is to build an image classification model to detect corrosion from images. The model should classify images into multiple categories (5 different corrosion degrees, 5 being max corrosion and 9 being very little corrosion). The metric is to beat the baseline of 20%. 


#### References:

1. Martin, R.L., Stegmann, D.W., Sookprasong, P.A.;"Oilfield Corrosion Failures Analysis: Lessons Learned from Pitting Mprphologies"; International Petroleum Technology Conference, 2016, IPTC-18941-MS.
2. https://www.bmvc2021-virtualconference.com/assets/papers/1544.pdf


## Data Source

The data source is from WPI-ARL (Worcestar Polytechnic Institute):

#### https://arl.wpi.edu/corrosion_dataset/

##### @InProceedings{yin2021BMVC, author = {Yin, Biao and Josselyn, Nicholas and Considine, Thomas and Kelley, John and Rinderspacher, Berend and Jensen, Robert and Snyder, James and Zhang, Ziming and Rundensteiner, Elke},title = {Corrosion Image Data Set for Automating Scientific Assessment of Materials},booktitle = {British Machine Vision Conference (BMVC)},year = {2021}}

It is split into training, validation, and test sets (.8, .1, .1). The dataset consists of 5 classes of corrosion with 600 images. The images are equally balanced across 5 degrees od corrosion from 5 (the most corrosion) to 9 (the least corrosion).


## Model Architecture and Training Process

- Goal is to have computers see and understand pictures, videos, and other digital imagery, much like a human would
- Automating visual processing that is normally done by humans
    - Obstructions in road for autonomous vehicles
    - Detecting defects before shipping to customers
    - Reading a CT scan with better accuracy than a human
- Computer vision techniques identify patterns in data 
- ML experts train complex models on vast amounts of visual data with the computer eventually learning to distinguish differences between images
- Well-annotated data is the foundation of training a good computer vision model

The problem solving process includes the following:

1. Source Data: Import the libraries you'll need and get the data set from https://arl.wpi.edu/corrosion_dataset/. It's already split into training, validation, and test sets.

2. Data Preprocessing and Transformation
    - Resize the image size to 224x224 pixels.
    - Normalize the image data.
    - Apply data augmentations like random rotations or flips to improve generalization.

3. Initialise (Build) the Model. Use a pre-trained model (e.g., **ResNet18**) from `torchvision.models` and fine-tune it for the plant disease classification task

4. Train the Model: Train the model on the training data set
    - Use a suitable loss function (e.g., cross-entropy) and optimizer (e.g., Adam).

5. Evaluate the Model

    - Evaluate the model on the validation set.
    - Report the overall model accuracy.

6. Visulation

   - Use Grad-CAM (Gradient-weighted Class Activation Mapping) to visulize where the model is looking from a heat map.

## Results and Key Takeaways


PyTorch was used to efficiently preprocess and transform the data to prepare the images for modeling. Resnet18 along with the cross-entropy loss function and Adam optimizer trained the images to label with the appropiate classes. After training over 2000 Epochs, the training loss was found to be 1.1905 and the validation loss was found to be 1.6131. The training accuracy was 48.96 % and the validation accuracy was 30.00%. Testing on the test set images found the accuracy of the model to be 43.33%. This accuracy exceeded the metric of performinig better than the basline 20% accuracy. This proof on concept indicates that it could be possible to use computer vision technology to automate corrosion detection from sample images.

Future work should include:

- Collect more images to improve the accuracy of the model.
- Experiment with the augmentation parameters to see if accuracy can be improved. A very aggresive augmentation transform was used. This could be introducing noise into the model.
- Expand technology to look at oilfield corrosion
- Once expanded to oilfield corrosion, build a dashboard or visualization interface for the end users, i.e. the oilfield operators.

