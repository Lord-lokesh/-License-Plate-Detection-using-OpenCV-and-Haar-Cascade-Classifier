# -License-Plate-Detection-using-OpenCV-and-Haar-Cascade-Classifier

# Name: Lokesh M

# Register Number: 212224230142

# Aim

To implement a License Plate Detection system using OpenCV and Haar Cascade Classifier, draw bounding boxes, crop the detected region, and blur the license plate to improve privacy. The detection accuracy is improved by tuning Haar Cascade parameters.


# Software Used

Python 3.7 or above

OpenCV (opencv-python)

NumPy

Matplotlib

Jupyter Notebook (Anaconda)


Haar Cascade File: haarcascade_russian_plate_number.xml

# Algorithm

Import necessary libraries such as OpenCV and Matplotlib

Read the input vehicle image

Convert the original image to grayscale for faster computation


Load the Haar Cascade classifier for license plate detection

Detect license plate using detectMultiScale function

Draw rectangle around detected area


Crop the detected region using numpy slicing with (x, y, w, h) values

Apply median blurring on the cropped region

Replace the original region with blurred version

Display final result using Matplotlib

# Program

```
def detect_plate(img):
    img_copy = img.copy()

    gray = cv2.cvtColor(img_copy, cv2.COLOR_BGR2GRAY)

    plates = plate_cascade.detectMultiScale(
        gray,
        scaleFactor=1.1,
        minNeighbors=4
    )

    for (x, y, w, h) in plates:
        cv2.rectangle(
            img_copy,
            (x, y),
            (x + w, y + h),
            (0, 255, 0),
            3
        )

    return img_copy




def detect_and_blur_plate(img):
    img_copy = img.copy()

    gray = cv2.cvtColor(img_copy, cv2.COLOR_BGR2GRAY)

    plates = plate_cascade.detectMultiScale(
        gray,
        scaleFactor=1.1,
        minNeighbors=4
    )

    for (x, y, w, h) in plates:
        roi = img_copy[y:y+h, x:x+w]

        blurred_roi = cv2.medianBlur(roi, 15)

        img_copy[y:y+h, x:x+w] = blurred_roi

    return img_copy



```

<img width="502" height="547" alt="image" src="https://github.com/user-attachments/assets/b3f52d73-70f1-4e13-ac45-f044f0595a67" />

<img width="536" height="558" alt="image" src="https://github.com/user-attachments/assets/87b0201f-1967-418b-a9d2-0b0ed57ab10a" />


<img width="533" height="548" alt="image" src="https://github.com/user-attachments/assets/49e5f0ea-eb89-4b73-9013-bbaeb932ab4d" />

# Modification Done
Parameter tuning was performed by adjusting scaleFactor and minNeighbors values in detectMultiScale to improve accuracy and reduce false detections. Median blur was applied to protect license plate information.

# Result
The License Plate Detection system was successfully implemented using OpenCV and Haar Cascade. The detected license plate region was blurred using median filtering. The modified values improved overall detection performance and output quality.

# Conclusion
This workshop demonstrates how classical computer vision methods like Haar Cascades can be used for real-time applications such as automated toll systems, smart parking, and traffic surveillance. Proper preprocessing and parameter tuning significantly improve detection results.


