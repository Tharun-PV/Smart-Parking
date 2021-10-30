# Smart-Parking

## Overview:
![alt text](https://github.com/Tharun-PV/Smart-Parking/blob/b8d8b09d279ea6b713f6dfe2ded953b595f57c2c/Sample%20Output/Sample_output.png)


The concept behind this solution is quite simple. It is composed of two scripts with the following roles:
- Select the coordinates of the parking spaces and save them into a file.
- Get the coordinates from the file and decide if the spot is available or not.

The reason for splitting this solution in two scripts is strictly related to avoiding to select the spots every time you want to see if there are any available spots especially if used the same location as before. To keep this as simple as possible, from now on I will refer to these scripts as selector and detector.

After everything is set up in python, the most important dependency would be OpenCV library. To add it to your virtual environment through pip you can run....
```python
pip install opencv-python
```

## Program flow

First of all we will need to setup a parking lot camera. In my case, as I don’t have any parking lots that I can see from my windows I choose to use my Secondary Monitor to play with it. Also I set up a webcam in-front of the parking lot to get a good image, so the image we are working on looks like this:

![alt text](https://github.com/Tharun-PV/Smart-Parking/blob/b8d8b09d279ea6b713f6dfe2ded953b595f57c2c/Sample%20Images/Sample_image02.jpg)

Now, let’s get to the coding part. First we need to build the selector.

## Spot Slector

To take the first frame provided by the webcam, save it and use the picture to select the spots.
The following code works like this:

- Opens the video stream in 'image' variable; 'suc' determines if the stream was opened successfully.
- Writes the first frame into 'frame0.jpg'.
- The new saved picture is read in 'img' variable.

Now that we have saved the first frame and opened it in the img variable we can use selectROIs function to mark our parking spots.

## Detector

Now that we’re done with selecting parking spots, it’s time to do some image processing.
The way I approached this was:

- Get coordinates from the .csv file.
- Build a new image out of it.
- Apply 'Canny' function available in OpenCV.
- Count the white pixels inside the new image.
- Establish a pixel range within the spot would be occupied.
- Draw a red or green rectangle on the live feed.

Now the most important part takes places, the appliance of 'drawRectangle' function to all the coordinates taken by 'Selector' script.
What’s left to do now is to write the number of available spots on the resulted image, display the 'Canny' function result and, obviously, a well known way to stop our loop.
