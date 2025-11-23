# Posture_Corrector

#  Posture Corrector - Posture and Drowsiness Detection

This project detects **bad posture** and **drowsiness** using **computer vision** and **machine learning techniques**. By leveraging **MediaPipe, OpenCV, and dlib**, the system analyzes human body landmarks and eye aspect ratio (EAR) to determine whether a person maintains good posture and is awake.

##  Project Description

The **Posture Corrector System** captures live video from a webcam and processes the frames to analyze key points on the human body. The system:

- Detects **posture** issues by calculating neck flexion and shoulder alignment angles.
- Identifies **drowsiness** by tracking eye aspect ratio (EAR) and triggering alerts if eye closure is prolonged.
- Provides **audio and visual alerts** when bad posture or drowsiness is detected.

This project is useful for individuals who spend long hours sitting, such as office workers, students, and gamers. It helps improve ergonomic awareness and prevent health issues like back pain and fatigue.


##  Technologies Used

-  **Python** – Main programming language
-  **OpenCV** – Video capture and image processing
-  **MediaPipe** – Body landmark detection
-  **NumPy** – Numerical computations (e.g., angle calculations)
-  **dlib** – Facial landmark detection for drowsiness monitoring
-  **scipy** – Euclidean distance calculations for EAR measurements
-  **pygame** – Audio feedback system

##  How It Works

###  **Posture Detection**
1. **Video Capture**: Captures a live feed using OpenCV.
2. **Pose Detection**: Extracts body landmarks using **MediaPipe Pose**.
3. **Angle Calculation**:
   - **Neck Flexion Angle**: Measures the angle between the nose, neck, and a vertical reference.
   - **Shoulder Alignment Angle**: Compares shoulder positions with a horizontal reference.
4. **Posture Evaluation**: If the angles deviate beyond **15° for neck flexion** or **10° for shoulder misalignment**, posture is flagged as **bad**.
5. **Alerts**: If bad posture is detected, the system displays `"BAD POSTURE"` and plays an alert sound (`dikdur.mp3`).

###  **Drowsiness Detection**
1. **Facial Detection**: Uses `dlib` to identify facial landmarks.
2. **Eye Aspect Ratio (EAR) Calculation**: Measures the distance between upper and lower eyelids.
3. **Threshold Detection**: If EAR falls below **0.25** for **20 consecutive frames**, the system detects drowsiness.
4. **Alerts**: When drowsiness is detected, `"SLEEPING WARNING!"` is displayed, and an alarm sound (`bad_posture_warning.mp3`) plays.

##  Customization

- Modify `EAR_THRESHOLD` to adjust drowsiness sensitivity.
- Adjust `angle_threshold` and `z_diff_threshold` to refine posture sensitivity.
- Replace the alert sounds (`dikdur.mp3`, `bad_posture_warning.mp3`) with custom audio files.

##  How to Run

### 1️⃣ **Clone the repository**
```bash
git clone https://github.com/your-username/Posture_Corrector.git
cd Posture_Corrector-main

### 2️⃣ **Install dependencies**
```bash
pip install numpy opencv-python mediapipe pygame dlib scipy

### 3️⃣ **Download the required dlib model**
wget http://dlib.net/files/shape_predictor_68_face_landmarks.dat.bz2
bzip2 -d shape_predictor_68_face_landmarks.dat.bz2
mv shape_predictor_68_face_landmarks.dat Posture_Corrector-main/

### 4️⃣ **Run the script**
python posture_detection.py

### 5️⃣ **Exit the application**
Press 'q' to quit the application.

