# Face Detection Model using DL 
Project 02 for Computer Vision Using Deep Learning

*ps it's actually an end to end object detection pipeline*

## Work Breakdown
1. **Collecting** images from the webcam
2. **Anotating** images: drawing bounding boxes around the head using the LABELME library which helps draw the bounding boxes as well as labelings
3. **Augmentation**: Due to insufficient data we need to increase numbers by augmenting the data by applying random cropping, brightness level variation, flipping and gamma transformations that allow us to 30X our dataset size. This is achieved via the **Albumentation library**
4. **Training**: An object detection model is essentially two models - an **image classification** model that has to determine the existence of an image with a certain degree of certainty and a **regression model** - to estimate the approximate coordinates of the two diagonally opposite points required to plot the bounding box
 - Before training, we also need to determine the **Loss Functions** which is done through
   -  the **BinaryCrossentropy** class for face classification and
   -  for **Localisation** for the regression model we need to calculate the difference in x,y          coordinates and the predicted x,y coordinates
   -  as well as the difference between the width and height of the bounding box and the corresponding predicted        values
5. **Building the Model**: using the Keras functional API to build it using VGG16 model that is already trained with a lot of data so we only need to add the final two layers of our model, namely the classification and the regression model.
 - What we get out of this model are 5 values
 -  firstly a value between 0-1 that tells the certainty of a face present in the image
 -  then a set of 4 values x1, y1 and x2, y2 that tell us the coordinates of the polar opposite       points of the box
6. **Testing and Detection**: are the beans cooked ????
