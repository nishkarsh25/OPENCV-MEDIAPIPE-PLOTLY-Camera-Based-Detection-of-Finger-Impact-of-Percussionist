# OPENCV-MEDIAPIPE-PLOTLY-Camera-Based Detection of Finger Impact of Percussionist: Precise Time of Impact

This project aims to develop a camera-based system to accurately detect finger impact during percussion performance. The system analyzes finger joint movements using computer vision and machine learning techniques to determine the precise moments when impact occurs, providing insights into the player’s technique, rhythm, and overall performance.

## Introduction

Percussion performance relies heavily on precise finger movements to produce accurate and expressive sounds. Detecting the exact moment of finger impact with a percussion instrument can offer valuable insights for performance analysis, training, and gesture research.

This project introduces a non-invasive, camera-based system that tracks finger joint movements using computer vision to estimate the time of impact during percussion. Leveraging tools like MediaPipe and OpenCV, it enables frame-wise analysis of joint angles, identifies high-velocity moments as impact events, and visualizes them with statistical metrics and plots. Both calibrated and uncalibrated video streams are analyzed for comparative study and validation.

## Features

- **Impact Detection from Camera**  
  Detects precise frames when a percussionist's finger makes impact, based purely on video data.

- **Hand Landmark Tracking**  
  Uses MediaPipe to extract 3D hand landmarks and compute joint angles for each finger.

- **Angle-Based Analysis**  
  Tracks joint angle changes over time to visualize motion and estimate velocity-based impacts.

- **Calibrated vs Uncalibrated Analysis**  
  Compares performance across calibrated and uncalibrated setups for deeper evaluation.

- **Frequency & Motion Visualizations**  
  Uses FFT to reveal dominant motion frequencies and dynamic plots to represent movement characteristics.

- **Statistical Reporting**  
  Outputs key metrics such as mean interval between impacts, standard deviation, and frequency of impact.

- **Customizable Thresholds**  
  Enables fine-tuning of impact detection sensitivity for different playing styles and setups.


## Report

You can view the detailed project report [here](https://res.cloudinary.com/drkwwvdoe/image/upload/v1745244075/Cpastone_2_ha01sj.pdf)

## Folder Structure

```
📦Calibration_Images
📦LeftHand_LeftIndexFrames
📦LeftHand_LeftMiddleFingerFrames
📦LeftHand_LeftWristFrames
📦LeftHand_PinkyFingerFrames
📦LeftHand_RingFingerFrames
📦LeftHand_ThumbFrames
📦RightHand_RightIndexFrames
📦RightHand_RightMiddleFingerFrames
📦RightHand_RightPinkyFingerFrames
📦RightHand_RightRingFingerFrames
📦RightHand_RightThumbFrames
📦RightHand_RightWristFrames
📜Code_Pipeline.ipynb
📜LeftHand_LeftIndex.png
📜LeftHand_LeftMiddleFinger.png
📜LeftHand_LeftWrist.png
📜LeftHand_PinkyFinger.png
📜LeftHand_RingFinger.png
📜LeftHand_Thumb.png
📜License
📜RightHand_RightIndex.png
📜RightHand_RightMiddleFinger.png
📜RightHand_RightPinkyFinger.png
📜RightHand_RightRingFinger.png
📜RightHand_RightThumb.png
📜RightHand_RightWrist.png

```

## Screenshot/Pipleine/Results

<img src="https://github.com/nishkarsh25/OPENCV-MEDIAPIPE-PLOTLY-Camera-Based-Detection-of-Finger-Impact-of-Percussionist/blob/main/LeftHandPinkyFinger.png?raw=true" alt="Screenshot 1" width="1000">

## Tech Stack

- **Python** – Core programming language used for data processing and analysis.
- **OpenCV** – For image and video processing.
- **MediaPipe** – Used for hand landmark detection.
- **NumPy & Pandas** – For data manipulation and analysis.
- **Matplotlib & Plotly** – For data visualization.
- **Jupyter Notebook** – For interactive development and experimentation.
- **SciPy** – Used for frequency and signal analysis.



## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

## Prerequisites

Before running the pipeline, ensure you have the following installed:

- Python 3.8 or above
- pip (Python package installer)
- Jupyter Notebook or any Python IDE that supports `.ipynb` files


## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/nishkarsh25/OPENCV-MEDIAPIPE-PLOTLY-Camera-Based-Detection-of-Finger-Impact-of-Percussionist.git
   ```

2. Navigate to the project branch:

   ```bash
   git checkout <branch-name>
   ```

   Replace `<branch-name>` with the name of the branch you want to checkout.

3. Install Required Dependencies

   Lastest versions of `mediapipe` require `numpy` version 1.26.x for compatibility. To ensure everything works smoothly, install the dependencies with the following commands:

   First, downgrade `numpy`(if necessary):
   ```bash
   python -c "import numpy; print(numpy.__version__)"
   pip install numpy==1.26.4
   ```
   
   ```bash
   pip install opencv-python mediapipe pandas numpy matplotlib plotly scipy
   ```

4. Run the Notebook
   
   Open Code_Pipeline.ipynb using Jupyter Notebook or your preferred environment and run the cells sequentially.
   
   ```bash
   jupyter notebook Code_Pipeline.ipynb
   ```


## Usage

Follow these steps to run the camera-based finger impact detection system:

## Note: 
   - The current images present in the `Calibration_Images` folder were captured using the **repository admin's webcam**. These **must be removed** before proceeding.
   - **Clear all previous images** in the `Calibration_Images` folder before adding new ones. If calibration images were previously taken from a different device, they might not work correctly for your webcam or phone calibration.
   - The **intrinsic and extrinsic properties** of the camera (webcam or phone) are device-specific, meaning the calibration images must be captured from the exact device you plan to use for real-time hand tracking.
   - If you're using **your webcam**, make sure the calibration images are taken from your webcam. If you're using **your phone**, capture the images using your phone's camera.


### Step 1: Capture Chessboard Images for Camera Calibration
1. **Print the Chessboard Pattern**: Print a **11x8 chessboard pattern** (10 internal corners horizontally and 7 internal corners vertically). Ensure that the chessboard is printed on a flat sheet of paper and remains undistorted.
   
2. **Take Pictures from Different Angles**:
   - Position the chessboard in front of your webcam/phone and take **at least 10-15 images**. 
   - Make sure the entire chessboard is clearly visible and flat, but you can hold the chessboard at different angles or distances from the camera.
   
3. **Save the Images**:
   - Save all the captured images in a folder named `Calibration_Images`. 
   - Ensure the images are in **.jpg format** (e.g., `image1.jpg`, `image2.jpg`, etc.).

### Step 2: Place Your Images in the Correct Folder
- Place all the **chessboard calibration images** in the `Calibration_Images` folder. This folder will be used for camera calibration.

### Step 3: Run the Calibration Script
- Run the **camera calibration** script to calibrate your webcam and compute the intrinsic parameters.
- This step uses the images you just captured to determine the camera matrix and distortion coefficients.

### Step 4: Set Up the Webcam
- Make sure your webcam is connected to the system and functional. 
- The program will use the webcam to track hand gestures while playing an instrument.

### Step 5: Start the Impact Detection Pipeline
- Once the calibration is complete, start the main pipeline by running the Python script to begin the hand tracking and impact detection.
- The webcam will open, and it will detect your hand movements as you play the instrument.
- Ensure your hand is clearly visible to the webcam and positioned within the camera's frame.

### Step 6: Play the Instrument
- Play the percussion instrument in front of the webcam.
- The system will track your hand's finger movements and detect the impacts based on the finger angles.

### Step 7: Quit the Camera Feed
- Press **`q`** on your keyboard to quit the camera feed once you're done playing.

### Step 8: Video Capture
- After pressing **`q`**, the system will save the frames of the webcam video in a folder named **`captured_frames`**.
- Each frame will be saved as an image in this folder, allowing you to review the frames later.

### Step 9: View the Results
- After quitting the camera feed, the system will generate and display the analysis plots.
  - You will see graphs showing the detected finger angles over time.
  - Impact analysis will be shown with markers indicating the time frames of finger impacts.


## Contributing

Contributions to this project are highly appreciated! Whether you discover bugs, have feature requests, or wish to contribute improvements, your input is valuable. Here's how you can contribute:

- **Report Issues:** If you encounter any bugs or issues while using MyCalculatorApp, please open an issue on the GitHub repository. Be sure to provide detailed information about the problem and steps to reproduce it.

- **Submit Pull Requests:** If you have enhancements or fixes to propose, feel free to submit a pull request. Contributions that improve the functionality, usability, or performance of this app are welcomed and encouraged.

Contributions are welcome! If you'd like to contribute to this project, please follow these steps:

1. **Fork the Repository**.
2. **Create a New Branch** (`git checkout -b feature/your-feature-name`).
3. **Make Your Changes**.
4. **Commit Your Changes** (`git commit -am 'Add some feature'`).
5. **Push to the Branch** (`git push origin feature/your-feature-name`).
6. **Create a New Pull Request**.

## License

This project is licensed under the [The 3-Clause BSD License](LICENSE).Feel free to explore, modify, and contribute to this project as you see fit. Your feedback and contributions are greatly appreciated! 🚀✨

## Acknowledgements

This project was developed as part of a research initiative at the **Indian Institute of Technology Hyderabad (IIT-H)**, under the **Department of Biomedical Engineering** and the **Department of Natural Intelligence**.


## Credits

This project makes use of the following tools and libraries:

- [OpenCV](https://opencv.org/) – For real-time computer vision operations and camera calibration.
- [MediaPipe](https://mediapipe.dev/) – For accurate and efficient hand landmark detection.
- [NumPy](https://numpy.org/) – For numerical operations and efficient matrix handling.
- [Pandas](https://pandas.pydata.org/) – For structured data analysis and manipulation.
- [Matplotlib](https://matplotlib.org/) – For static plotting and visual data representation.
- [Plotly](https://plotly.com/) – For interactive, web-based data visualizations.
- [SciPy](https://scipy.org/) – For signal processing and peak detection.

All libraries and frameworks used are open-source and integral to the completion of this project.

### Dataset:
- All the data used in this project, including calibration and hand tracking video frames, was **self-collected** using a **standard chessboard and webcam/phone setup**.

We sincerely thank all contributors, test subjects, and reviewers who helped validate and improve the pipeline.


## Author

- **Nishkarsh Gupta**
  - GitHub: [nishkarsh25](https://github.com/nishkarsh25)
  - Email: bm21btech11016@gmail.com
