# Parking Space Detection using OpenCV

This project detects **free and occupied parking spaces** in real-time using classic **computer vision techniques** (OpenCV). The system loads predefined parking spot coordinates, processes each video frame, and identifies which spaces are available based on pixel intensity analysis.

---

## 🚗 Features

- Detects parking spots in real-time from video
- Uses **adaptive thresholding**, **blur**, **binary masks**, and **pixel counting**
- Marks each parking space as:
  - 🟢 **Free**
  - 🔴 **Occupied**
- Includes a tool to **manually select parking space positions**
- Displays live free-space counter (e.g., `Free: 12/20`)

---

## 🗂 Project Files

| File | Description |
|------|-------------|
| `main.py` | Main parking detection script using OpenCV and CVZone :contentReference[oaicite:0]{index=0} |
| `ParkingSpacePicker.py` | Tool to manually draw/select parking spot areas on an image :contentReference[oaicite:1]{index=1} |
| `CarParkPos` | Pickle file storing coordinates of all parking spaces |
| `process.py` | Demonstration of multiprocessing queue (not required for main detection) :contentReference[oaicite:2]{index=2} |

---

## 🧠 How It Works

### **1. Parking Spot Mapping**
Using `ParkingSpacePicker.py`, you:
- Click to **add** a parking spot rectangle  
- Right-click to **remove**  
All coordinates are saved to `CarParkPos`.

### **2. Frame Processing**
Each video frame is processed using:
- Grayscale conversion  
- Gaussian blur  
- Adaptive thresholding  
- Median blur  
- Dilation  

### **3. Occupancy Detection**
For each saved parking space:
- Crop the region  
- Count white pixels using `cv2.countNonZero()`  
- If pixel count < threshold → **Free**  
- Else → **Occupied**

This logic is found in the `checkSpaces()` function.  
:contentReference[oaicite:3]{index=3}

---

## 📦 Dependencies

Install via pip:

```bash
pip install opencv-python cvzone numpy
