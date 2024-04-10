# magic balls
# Overall Strategy
![alt text](docs/pipeline.jpg "Title")

The main idea was to make a model as simple as possible without the complication of preprocessing or postprocessing. For training the model, I used only one image of a ball which I found using a simple OpenCV function. After this, I pasted the same ball onto background photos I took from Kaggle. I divided the ball into 2 classes: magic-ball and a fixed color circle/ball. There are other wide-ranging possibilities to perform the task, but I chose this way because, in my understanding, it is the fastest (as you can see, it takes me an average of 70 ms per image) and requires minimum time for pre- and post-processing.

* Step 1 - I chose a simple image and using HoughCircles (OpenCV) found the magic ball.
* Step 2 - Using copy-paste augmentation, I created a new dataset.
* Step 3 - I trained a YOLOv8-nano detector to find 2 classes (0: magic ball, 1: regular ball).
* Step 4 - For inference, I used scale TTA and NMS for ensemble.
* Step 5 - For postprocessing, I converted the bounding boxes to circles.
