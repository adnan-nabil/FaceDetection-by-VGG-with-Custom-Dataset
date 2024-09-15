
# REALTIME DEEP FACE DETECTION MODEL

Hello, I am Nabil Adnan. This is my deep learning project. This is based on an object detection model. This project is a realtime face detection model. In future I can use it as age or sentiment analysis.


## What I really did here:

1. COLLECTING AND ANNOTATING IMAGES

2. APPLYING BOUNDING BOX AUGMENTATION

3. BUILD A DEEP OBJECT DETECTION Model

4. EVALUATING MODEL PERFORMANCE

5. DETECTING FACES IN REAL TIME


## What tools I used here:

1. Python

2. OpenCV

3. Tensorflow

4. labelme

5. matplotlib

6. Albumentation


## AT A GLANCE

At first I collect some data(images) for my model using my laptops webcam. And after that I annotate images . For annotation I used a library called "Labelme". 

After annotation I did augmentation. Because limited data is not enough for any model to train properly. So that, I augment my collected images using a library named "Albumentation". I did random crop, brightness changing, flipping and gamma shifting. By this augmentation technique I got aroud 30X more data which was enough for my model training. 

The name of this project is deep face detetction model. But there is actually two different models.
1. First one is actually detect face
2. Second model is a regression model.


