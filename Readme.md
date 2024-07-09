# Car Tracking, Speed Estimation, and Counting

This project utilizes OpenCV to detect, track, and estimate the speed of cars in a video. Additionally, it counts the number of cars passing through a specific area in each frame. The program uses Haar Cascade for car detection and the KCF tracker for tracking the detected cars.

## Prerequisites

To run this project, you will need the following:
- OpenCV library installed on your system
- A video file named `Cars.mp4`
- Haar Cascade XML file for car detection (`cars.xml`)

## Getting Started

### CMake

CMake is a tool that helps manage the build process of software projects. It simplifies the compilation and linking of code by generating native build configurations (like Makefiles or Visual Studio project files) for your project. 

### Building the Project

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Create a build directory:**
   ```bash
   mkdir build
   cd build
   ```

3. **Generate build files using CMake:**
   ```bash
   cmake ..
   ```

4. **Build the project:**
   ```bash
   make
   ```

5. **Run the executable:**
   ```bash
   ./CarTracking
   ```

## Algorithm

The algorithm can be broken down into several steps:

1. **Video Capture:**
   - The video file `Cars.mp4` is opened using OpenCV's `VideoCapture`.

2. **Load Haar Cascade Classifier:**
   - The Haar Cascade XML file (`cars.xml`) is loaded to detect cars in each frame of the video.

3. **Car Detection:**
   - Each frame is converted to grayscale and histogram equalization is applied.
   - The Haar Cascade is used to detect cars in the frame.
   - Overlapping detections are filtered out to avoid multiple rectangles on the same car.

4. **Car Tracking:**
   - For each detected car, a KCF tracker is created and initialized.
   - The center of the car's bounding box is calculated for speed estimation.

5. **Speed Estimation:**
   - The speed of each car is estimated based on the movement of its center between consecutive frames.
   - The speed is displayed on the video frame.

6. **Car Counting:**
   - Cars passing through a specific area (defined by the user) in each frame are counted.
   - The count is updated in real-time as the video progresses.

7. **Display:**
   - Bounding boxes and speed information are drawn on the frame.
   - The frame is displayed in a window.
   - The program exits if the ESC key is pressed.