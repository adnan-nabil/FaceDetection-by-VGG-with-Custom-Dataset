

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

The name of this project is deep face detetction model. But indise there is actually two different models work together.
1. First one is actually detect face. (Is it face or not)

2. Second model is a regression model. (Bounding of box in a face)


For two different models I need loss function. I used here two different loss function for different purposes. 

1. For classification I used "BinaryCrossEntropy"

2. For regression,
   Σ(x-x̂)² + (y-ŷ)² + Σ(w-ŵ)²+(h-ĥ)²


To define the loss functions I used Keras functional API in here.


Inside my model I used VGG16 image classification model. It is a powerful pretained model for image classsification. It is already pretrained and can help me to classification and regression.

My model finally give me 5 values. First one is either [0,1] and the rest 4 is X1, Y1, X2, Y2. 





## Dependencies and setup

![Screenshot 2024-09-15 154058](https://github.com/user-attachments/assets/a6931003-92f7-4b35-ac1e-a7a1fd0a74c5)


Install necessary dependencies like python, labelme, openCV, tensorflow, matplotlib and albumentation




## Collect images using openCV
At first I collected some data(images) for my model using my laptops webcam. And after that I annotate images . For annotation I used a library called "Labelme". 

![Screenshot 2024-09-16 143541](https://github.com/user-attachments/assets/94b9e2e0-0185-4dc9-98ed-71fd031daccc)

In here I import some necessary libraries. uuid is stands for uniform unique identity. It is because to rename the images uniquly for future use of annotation and augmentation.


![Screenshot 2024-09-16 143741](https://github.com/user-attachments/assets/189ad48e-9310-42fe-9dbc-aaf7d3959c81)

using the os library I address the images path to store which I will collect.

In the next cell I use cv2 for open my webcam to take images. When my webcam is running it takes frame after a certain time which I defined using time library. I set 0.5sec. It will take 30 images at a time.I defined it in num_images variable on the first cell.

So, everytime I run this cell it will take 30 images atleast. This is how I collected data for my deep face detection model. 





## Annotate images

![Screenshot 2024-09-16 145553](https://github.com/user-attachments/assets/77615b39-aadf-416f-bba9-3f7ece72808f)


Labelme is a fantastic tool for image annotation and segmentation. I used this tool for my data annotation. It saved my annotation as JSON file.





## Image Loading fucntion and partitioning
After annotation I did augmentation. Because limited data is not enough for any model to train properly. So that, I augment my collected images using a library named "Albumentation". I did random crop, brightness changing, flipping and gamma shifting. By this augmentation technique I got aroud 30X more data which was enough for my model training. 

![Screenshot 2024-09-16 152537](https://github.com/user-attachments/assets/63f9782f-2cf5-432e-9689-0504020fdd6e)
Importing Tensorflow , Json, numpy and matplotlib.

![Screenshot 2024-09-16 152725](https://github.com/user-attachments/assets/9e9c6937-b6bb-4f7d-ac37-2f428a1c5a4e)


In this cell I just decode every images using map function and load image function. When I read any image in tensorflow it would be a byte image. then I have to deocde the image for further processing.


![Screenshot 2024-09-17 120842](https://github.com/user-attachments/assets/16d8eb7a-68d2-4b31-91d0-26d02957f93b)

See the raw images with matplotlib.


![Screenshot 2024-09-17 121042](https://github.com/user-attachments/assets/65ccc2a4-9be4-4f29-9668-a80091a0623f)

Divide data for train test validation. I did it by hand or manually. 70% data for training. 15% for testing and 15% for validation.


![Screenshot 2024-09-17 121442](https://github.com/user-attachments/assets/3a55faac-1f36-4583-a07a-d3b5bb853645)


I divide data manually. Transfer random data in different folders such as Train, Test, Validation. Now I have to move their corresponding annotated file to the same directory. And also initially I named my images by "uuid" (Uniform Unique Identity). So it is not a big deal to move corresponding annotation JSON file to move their folder. In here I did the same thing. It is very simple thing. Split the name of the file. Then use the first part of the name, matching the file and move them to their folder. 


## Now the Image Augmentation Part

After annotation I did augmentation. Because limited data is not enough for any model to train properly. So that, I augment my collected images using a library named "Albumentation". I did random crop, brightness changing, flipping and gamma shifting. By this augmentation technique I got aroud 30X more data which was enough for my model training.

![Screenshot 2024-09-17 122106](https://github.com/user-attachments/assets/72c6a88d-9e7e-4d3a-bf5b-b768dd4540b2)

Import albumentation library.


![Screenshot 2024-09-17 122315](https://github.com/user-attachments/assets/431b06f8-d4d4-4c64-999e-472475d8745b)

Albumentation is fantastic library for augmentation. In this cell the augmentor variable i declared. Inside augmentor variabe I define what technoques should apply for image augmentation. I used randomcrop, horizonta flip, image contrast change, vertical flip and RGB shifting.

![Screenshot 2024-09-17 145642](https://github.com/user-attachments/assets/52f3d86d-a294-487b-b7e5-4728c34fa09c)
![Screenshot 2024-09-17 145717](https://github.com/user-attachments/assets/b92154ef-43bf-4113-a7d6-ce091ad0f307)
![Screenshot 2024-09-17 150102](https://github.com/user-attachments/assets/47976026-eca5-4207-8250-4b0fadf8d1da)


In here I just observed a single annotated image and its coordinates and also I run it in my augmentation technique to see if its work properly or not.


Next I will build a total pipeline for augment all of my images.


