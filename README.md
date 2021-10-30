# Smart-Parking

It is composed of two scripts with the following roles:
Select the coordinates of the parking spaces and save them into a file.
Get the coordinates from the file and decide if the spot is available or not.

#Program flow is as follows:

   User inputs file name for a video, a still image from the video, and a path for the output file of parking space coordinates.
User clicks 4 corners for each spot they want tracked. Presses 'q' when all desired spots are marked.
Video begins with the user provided boxes overlayed the video. Occupied spots initialized with red boxes, available spots with green.
Car leaves a space, the red box turns green.
Car drives into a free space, the green box turns red
