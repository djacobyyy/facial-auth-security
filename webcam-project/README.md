# Webcam Face Recognition Prototype

## Usage

Install dependencies from the repo root:

    pip install -r requirements.txt

Then, from `webcam-project/`:

- Enroll a face (saves `<Name>_face.npy`; asks before overwriting):

      python enroll_face.py <Name>

  Press S to enroll, Q to quit.

- Recognize enrolled faces:

      python face_recognition.py

  Keys: A logs a recognition attempt for all visible faces, Q quits.
  Events are sent over UDP on port 5006.

- Detect faces only:

      python face_detection.py

  Events are sent over UDP on port 5005.

The two scripts use different ports, so they can run at the same time.

Recognition uses cosine similarity with a threshold of 0.363 (the OpenCV
SFace reference value).

## GUI

From the repo root, run:

    python main_gui.py

The GUI uses the models (`yunet.onnx`, `sface.onnx`) and enrolled faces in
`webcam-project/`, so it shares enrollments with `face_recognition.py`.
Buttons: Enroll Mode, Save Face, Recognition Mode, Log Attempt (plus Stop
Camera). Recognition events are sent over UDP on port 5006.
