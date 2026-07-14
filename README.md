# AI-Based Smart Attendance Monitoring System

An AI-powered attendance management system that uses face recognition to automatically detect, identify, and log attendance — removing the need for manual roll calls or physical registers.

The project has two parts:

1. **Core Desktop Application** — a Python + OpenCV + Tkinter app that registers student faces, trains a recognition model, and marks attendance automatically via webcam, exporting records to CSV.
2. **Web Platform (extended module)** — a full-stack version with a Flask + MongoDB backend and a Next.js frontend, adding student/teacher login, live camera-based attendance sessions, and a dashboard to view records.

---

## Features

- **Face Registration** — capture and store a student's face samples using a webcam.
- **Model Training** — train a face-recognition model (LBPH in the desktop app / DeepFace + MTCNN embeddings in the web module) on the registered faces.
- **Automatic Attendance** — recognize faces in real time and mark attendance without manual input.
- **Subject/Session-wise Records** — attendance is logged per subject/session with date and timestamp.
- **Attendance History** — view past attendance in a tabular format; export to CSV/Excel.
- **Web Platform Extras** — student and teacher authentication, student registration & profile updates, teacher-initiated attendance sessions, and a dashboard for viewing attendance records.

---

## Tech Stack

**Desktop Application**
- Python 3
- OpenCV (Haar Cascade + LBPH Face Recognizer)
- Tkinter (GUI)
- Pandas, NumPy, Pillow
- pyttsx3 (voice feedback)

**Web Platform**
- **Backend:** Flask, Flask-CORS, Flask-Bcrypt, PyMongo (MongoDB), DeepFace, MTCNN, OpenCV
- **Frontend:** Next.js, React, TypeScript, Tailwind CSS, face-api.js, Socket.IO client, Framer Motion
- **Database:** MongoDB

---

## Project Structure

```
├── attendance.py                  # Main desktop app (Tkinter GUI entry point)
├── takeImage.py                   # Captures and stores face samples
├── trainImage.py                  # Trains the LBPH face recognition model
├── automaticAttedance.py          # Marks attendance via live face recognition
├── show_attendance.py             # Displays attendance records
├── takemanually.py                # Manual attendance fallback
├── haarcascade_frontalface_*.xml  # Pre-trained face detection classifiers
├── TrainingImageLabel/            # Trained model file (Trainner.yml)
├── StudentDetails/                # Registered student records (CSV)
├── Attendance/                    # Generated attendance CSVs (per subject)
│
├── backend/                       # Flask API for the web platform
│   ├── app.py
│   ├── auth/                      # Signup/login routes
│   ├── student/                   # Registration, profile updates, attendance view
│   ├── teacher/                   # Attendance session handling
│   └── recognition.py             # Face detection & embedding logic (DeepFace/MTCNN)
│
└── frontend/                      # Next.js web client
    └── app/                        # Pages for student/teacher dashboards, sessions, auth
```

---

## Getting Started

### 1. Desktop Application

```bash
# Clone the repository
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>

# Install dependencies
pip install -r requirements.txt

# Run the application
python attendance.py
```

**How to use:**
1. Click **Register New Student**, enter an enrollment number and name, then click **Take Image** to capture face samples via webcam.
2. Click **Train Image** to train the recognition model on all registered faces.
3. Click **Automatic Attendance**, enter the subject name, and let the system recognize faces and mark attendance.
4. Click **View Attendance** to see records in tabular format.

### 2. Web Platform

**Backend:**
```bash
cd backend
pip install -r requirements.txt
python app.py
```

**Frontend:**
```bash
cd frontend
npm install
npm run dev
```

The frontend runs at `http://localhost:3000`, with the backend API running separately (default `http://localhost:5000`).

> Note: The web platform requires a MongoDB instance — set your connection string as an environment variable rather than hardcoding it.

---

## Screenshots

**Application UI**
![Simple UI](Project%20Snap/1.PNG)

**Capturing Face Samples**
![Taking Image](Project%20Snap/2.PNG)

**Marking Attendance**
![Marking Attendance](Project%20Snap/6.PNG)

**Attendance in Tabular Format**
![Attendance Table](Project%20Snap/7.PNG)

---

## Future Scope

- Cloud deployment of the web platform for multi-classroom use.
- Real-time notifications for absentee alerts.
- Integration with institutional ERP/student management systems.
- Liveness detection to prevent photo-based spoofing.

---

## Author

**Dhruv Johri**
Final Year, B.Tech CSE, SRMS CET, Bareilly (AKTU)
