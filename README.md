# Parking Area Detection and Monitoring
This project consists of two modules that work together to detect, label, and monitor parking areas using a video feed. It leverages computer vision and deep learning to identify parking areas, detect cars within those areas, and provide real-time feedback on available and occupied spaces.

## Modules
1. Locate Areas Code
This module allows users to manually define parking areas by drawing polygons on video frames and assigning names to each area. The defined areas are saved for future use.

2. Detect Areas Code
This module uses the pre-defined parking areas and detects cars within those regions using a YOLO model. It counts occupied and empty spaces, displaying this information on the video feed.

## Module 1: Locate Areas Code
### Objective
Manually define and save parking areas by drawing polygons on video frames.

### Workflow
1. Input Video:
Loads a video file to allow frame-by-frame drawing.
2. Drawing Polygons:
Allows the user to draw polygons on the video using mouse inputs.
Prompts the user to assign a name to each area after drawing.
3. Saving Data:
Saves the drawn polygons and their names in a serialized file (LocatedAreas) using Python's pickle module.
4. Visualization:
Displays the saved polygons and their corresponding names in the video feed.
### Key Functionalities
Mouse Event Handling: Detects mouse inputs to draw polygons.
Data Persistence: Stores polygon coordinates and area names for reuse.
Interactive Visualization: Shows defined areas and labels on the video.
### Technical Details
Libraries Used:
OpenCV: For video processing and mouse event handling.
NumPy: For handling polygon coordinates.
Pickle: For saving and loading serialized data.

## Module 2: Detect Areas Code
### Objective
Automatically detect cars within the pre-defined parking areas and monitor parking space availability.

### Workflow
1. Input Video:
Loads a video and processes it frame-by-frame.
2. Car Detection:
Uses the YOLOv8 model to detect objects in each frame.
Filters detections to identify cars only.
3. Parking Area Matching:
Checks if the center of a detected car falls within any pre-defined parking area using cv2.pointPolygonTest.
4. Counting Cars:
Counts the number of cars in each area.
Calculates and displays the number of empty spaces based on a fixed total capacity.
5. Output Visualization:
Highlights detected cars and displays the count of occupied and available spaces on the video feed.
### Key Functionalities
1. Object Detection:
Utilizes a pre-trained YOLOv8 model for real-time car detection.
2. Parking Area Matching:
Matches detected cars to parking areas using geometric tests.
3. Real-Time Feedback:
Displays parking space occupancy and availability dynamically.
4. Data Reuse:
Loads the saved polygons and names from the LocatedAreas file.
### Technical Details
Libraries Used:
YOLO (Ultralytics): For car detection.
Pandas: For organizing detection data.
OpenCV: For video processing and geometric calculations.
NumPy: For working with bounding box and polygon coordinates.
Efficiency:
Processes every third frame to reduce computational load while maintaining responsiveness.
Customizations:
Car classes are filtered using a COCO dataset class list.Note: Explanation of the code is placed in comments inside each notebook

To deal with these notebooks first:
Open the notebook called locate the areas and put the video in which you want to detect the places. Run the notebook and pop-up window will appear and identify the places where cars are parked by pressing the left mouse button. When you finish specifying a specific place, go to the notebook to put a number for this place and repeat that process in order to You finish specifying all the places, and when you are finished, you will notice that a file called LocatedAreas has been created.

secondly:
Go to the notebook called detect areas and run the notebook and you will notice the changes that will occur when you park a car or go far away, and this is by counting the full areas and the empty areas.
Note: There are some features that can be exposed while the notebook is running, which are called detect areas. The lines of code for these features have been preserved by making a comment about them.
There are two videos showing the results called detected areas with details hidden and detected areas with details
