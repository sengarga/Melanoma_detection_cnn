# Problem statement 
To build a CNN based model which can accurately detect melanoma. Melanoma is a type of cancer that can be deadly if not detected early. It accounts for 75% of skin cancer deaths. A solution that can evaluate images and alert dermatologists about the presence of melanoma has the potential to reduce a lot of manual effort needed in diagnosis.

The dataset consists of 2357 images of malignant and benign oncological diseases, which were formed from the International Skin Imaging Collaboration (ISIC). All images were sorted according to the classification taken with ISIC, and all subsets were divided into the same number of images, with the exception of melanomas and moles, whose images are slightly dominant.


The data set contains the following diseases:

- Actinic keratosis
- Basal cell carcinoma
- Dermatofibroma
- Melanoma
- Nevus
- Pigmented benign keratosis
- Seborrheic keratosis
- Squamous cell carcinoma
- Vascular lesion



# Project Pipeline
- Data Reading/Data Understanding:
  
We start by reading and understanding the dataset. We define the path for both the train and test images, ensuring we know where the data is located for the next steps.

- Dataset Creation:
  
We create the training and validation datasets from the train directory. While doing so, we ensure that the batch size is set to 32 and that all images are resized to 180x180 pixels.

- Dataset Visualization:
  
Next, we create a visualization code to inspect the dataset. This allows us to visualize one instance of each of the nine classes present in the dataset, helping us better understand the variety of images we are working with.

- Model Building & Training:
  
We build a CNN model that can accurately detect the 9 classes present in the dataset. While building the model, we rescale the images to normalize pixel values between (0,1).
We choose an appropriate optimizer and loss function for model training.
The model is then trained for around 20 epochs.
After the model fit, we analyze the results and write down our findings. We check if there is any evidence of overfitting or underfitting and assess the model’s performance.
We encounter overfitting so we apply augmentation to the images.

- Model Building & Training on Augmented Data:

After applying data augmentation, we build the CNN model again to accurately detect the 9 classes. The images are rescaled to normalize pixel values between (0,1).
We choose the appropriate optimizer and loss function.
The model is trained again for approximately 20 epochs.
We evaluate the model after training to determine if the earlier issue (overfitting/underfitting) has been resolved.
We find that the problem of overfitting is somewhat solved but model is unstable and accuracy is also very low.

- Class Distribution:

We examine the current class distribution in the training dataset and observe that the data is imbalanced.
We analyze which class has the least number of samples and which classes dominate in terms of the proportionate number of samples.
Handling Class Imbalances:

To rectify the class imbalance, we use the Augmentor library to augment the data and balance the class distribution.

- Model Building & Training on Rectified Class Imbalance Data:

Once we have balanced the class distribution, we build the CNN model once again to accurately detect the 9 classes, ensuring the images are rescaled to normalize pixel values between (0,1).
We select the appropriate optimizer and loss function.
This time, we train the model for around 30 epochs to evaluate how the rectified data impacts model performance.

We finally observe that our model accuracy is quite good and also overfitting is reduced to a large extent.

 
## CNN Architecture Design
we used the below architecture for our custom CNN model

- input layer with normalization


- First Convulation layer(number of filters = 32,size= (3,3), activation = ReLu)  and pooling layer(2,2)


- Second Convulation layer(number of filters = 64,size= (3,3), activation = ReLu)  and pooling layer(2,2)


- Third Convulation layer(number of filters = 128 ,size= (3,3), activation = ReLu)  and pooling layer(2,2)


- Dropout layer with 20% Fraction of the input units to drop.


- Flatten Layer

- Dense Layer (128, ReLu)


- Dropout layer with 30% Fraction of the input units to drop.

- Dense Layer with softmax activation function.



