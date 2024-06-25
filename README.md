# Car-Parking-Detection

![carpark_censored-1](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/bc1f4247-e0fe-4354-a094-65a6de264ef3)

When I was in my data science internship in internet of things division, I got responsibility to build an AI model for car parking detection project. This project was a new innovation to handle high error rate of existing project before. I made this AI model using SqueezeNet due to tight hardware specification and high accuracy prediction of model expected. This model was expected to run in raspberry pi 4 and would sending real time prediction data. Here is how i was made this model:

**1. Import Libraries**

![image-2](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/9deef7a2-6d21-482d-b04b-b7bf7379e9d2)

_(Libraries)_

For this project, I was using OpenCV for image processing, Tensorflow for model training, and sklearn and numpy for data processing.

**2. Load dataset**

![image-1](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/b4ffdadf-bb3b-4d25-9917-2339f9154588)

_(Load Dataset)_

Made two empty list to store dataset images and classes. Read the images using OpenCV imread, resize it to compress data into smaller size, and change the color from RGB to gray to simplify the model to learn. I made 3 classes here due to project requirement where the model need to classify whether car parking space was occupied or not and if it was not occupied then whether the lockey (name for car parking unit) was up or down.

![image](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/f5830220-d113-4578-a6fb-d9addd4ec2ce)

_(*0 = empty down)_

![image](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/eb712b98-dba0-4e75-8a8a-2824010449e6)

_(*1 = empty up)_

![image](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/9d8f39ce-85a1-45ae-ae86-4ba6c8fadb11)

_(*2 = occupied)_

Every class has 9000 images and total of dataset was 27000 images.

**3. Data processing**

![image-5](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/7019faf4-85cf-4a57-a5e8-1c65b5269476)

_(Split Dataset)_

First, split dataset into training and testing dataset. I was using 80% training dataset and 20% testing dataset ratio.

![image-6](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/e68e949e-0b9e-458e-81d1-6753b34670f6)

_(Reshape Dataset)_

Then, reshape the images dataset. This step is necessary for the images dataset could be trained by tensorflow.

![image-7](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/237809e2-f6d3-4450-a565-7c8ed70dc303)

_(Normalize and Format Dataset)_

Normalize the images dataset to simplify the AI model to learn and convert classes label into desired format using OneHotEncoder (this was also necessary for tensorflow).

**4. Making the model**

![image-8](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/0554a927-e5ea-45ae-b9f0-5d0ef2f7cd1b)

_(Make Model and Fit Dataset)_

I could not show the model architecture due to project confidentiality. I made this model using adam optimizer and categorical crossentropy for loss option. 

**5. Save the model**

![image-9](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/1704bed4-5448-4470-aebe-77dad26f5c85)

_(Save Model)_

After model fitted, then save the model in json and h5 format.

**6. Convert saved model to TFLITE format**

![image-10](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/6cee8773-3b3a-4f87-bb44-616a8ca61d6a)

_(Convert to TFLite)_

TFLITE format would be used if you want to use saved model in tight hardware specification like raspberry pi. This format may lose accuracy a bit but perfectly works in small device because it is lightweight AI model.

**7. Model Evaluation**

![image-11](https://github.com/radiadus/Car-Parking-Detection/assets/55176713/c791253f-4f10-4447-ae8b-a4a6f2e93ef9)

_(Evaluation)_

Last but not least is model evaluation. I was using confusion matrix and accuracy score to evaluated the model. This model had very high accuracy up to 99.9% which it was only did false detection two times.

# Conclusion

In conclusion,

1. I was able to made image classification AI Model and run it on raspberry pi 4 for real time detection.
2. This image classification AI model able to decrease false detection and unit error up to 81% and total downtime up to 96% on a car parking detection project.
3. Successful save 62% on units maintenance budget on car parking project.



