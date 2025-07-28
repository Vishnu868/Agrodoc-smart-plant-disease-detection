# 🌿 AgroDoc: Smart Plant Disease Detection System

An end-to-end IoT + ML system to detect plant diseases using deep learning, advise fertilizer/pesticide, and enable real-time monitoring via mobile app and ESP32-CAM integration.

##  Features

-  Leaf disease detection using YOLOv5 + Selective Feature Refinement (SFR)
-  Flutter mobile app with upload/camera + advisory UI
-  ESP32-CAM for field-based image capture and inference
-  Flask REST API to handle predictions
-  Advisory for fertilizer, pesticide, and precautions
-  Soil/humidity sensor integration for irrigation management

---

##  Tech Stack

| Layer            | Tech Used |
|------------------|-----------|
| ML Model         | YOLOv5 + SFR (PyTorch) |
| Backend API      | Flask (Python) |
| Mobile App       | Flutter |
| IoT Devices      | ESP32-CAM, NodeMCU, DHT11, Moisture Sensor, Relay |
| Advisory DB      | JSON / Firebase Realtime DB |
| Hosting          | Render/Railway/Jetson Nano, Netlify (Web), Cloudinary (optional) |

---

##  Project Structure

Agrodoc-smart-plant-disease-detection
┣  ML_Model/
┃ ┣  detect.py
┃ ┣  train.py
┃ ┣  model_weights.pt
┣  Backend_Flask/
┃ ┣  app.py
┃ ┣  static/uploads/
┃ ┗  utils/
┣  IoT_ESP32_CAM/
┃ ┣  esp32_cam_capture.ino
┃ ┗  http_post_image.ino
┣  Flutter_App/
┃ ┣ lib/
┃ ┃ ┗  main.dart
┃ ┣  screens/
┃ ┃ ┣  home.dart
┃ ┃ ┣  result.dart
┃ ┃ ┗  upload.dart
┣  Website_Interface/
┃ ┣  index.html
┃ ┣  style.css
┣  Advisory_DB/
┃ ┗  advisory.json
┣ README.md
┣ requirements.txt
┗ .gitignore

---

##  Workflow

1. User uploads plant image via **Flutter app** or **ESP32-CAM**.
2. Flask backend receives image → processes it with **YOLOv5 + SFR**.
3. Detected disease is matched with **advisory.json**.
4. JSON response sent with:
    -  Disease Name
    -  Recommended Fertilizer
    -  Pesticide
    -  Precautions

---

##  Flutter App UI

- Camera and gallery upload
- Show detection result + advisory
- Optional history log (Firebase)
- Beautiful Material3 design

---

##  ESP32-CAM Role

- Capture image
- Convert to base64
- POST to Flask backend
- View response on OLED / Serial Monitor

---

##  Sample API Response

```json
{
  "disease": "Tomato Leaf Curl",
  "fertilizer": "NPK 20-20-20",
  "pesticide": "Imidacloprid",
  "precautions": "Remove infected leaves, control whitefly population"
}
