# classify.py
import cv2
import serial
import time
from some_model import predict_trash_type 

ser = serial.Serial('/dev/ttyUSB0', 9600) 

cam = cv2.VideoCapture(0)

while True:
    ret, frame = cam.read()
    if not ret:
        continue

    label = predict_trash_type(frame)
    print("Detected:", label)

    # Send to ESP32
    msg = f"TRASH:{label}\n"
    ser.write(msg.encode())

    time.sleep(2)
