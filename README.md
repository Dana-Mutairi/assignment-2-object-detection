
# Assignment 2: Object Detection and Descriptive Summary

A computer-vision project that implements manual object-detection visualization and programmatic scene summarization using Ultralytics YOLO26, NumPy, Pillow, and OpenCV in Google Colab.

[Open the notebook in Google Colab](https://colab.research.google.com/github/Dana-Mutairi/assignment-2-object-detection/blob/main/Assignment_2_Object_Detection_and_Descriptive_Summary.ipynb)

## Project Objective

This project performs object detection on a custom image of a basketball player holding a ball. It extracts bounding-box coordinates, class labels, and confidence scores from YOLO26 predictions.

A custom confidence threshold is applied, and the accepted bounding boxes and class labels are drawn manually using OpenCV without using YOLO’s built-in plotting function. A natural-language description of the detected scene is then generated programmatically and displayed below the image.

## Project Workflow

1. Install and import the required libraries.
2. Load and inspect the basketball image.
3. Load the pretrained YOLO26 nano model.
4. Run object-detection inference.
5. Extract bounding-box coordinates, class IDs, and confidence scores.
6. Apply a custom confidence threshold.
7. Draw bounding boxes manually using `cv2.rectangle()`.
8. Add class labels using `cv2.putText()`.
9. Count the accepted object classes.
10. Generate a natural-language description of the scene.
11. Display the description below the annotated image.
12. Save the final detection result.

## Technologies

- Python
- Google Colab
- Ultralytics YOLO26
- NumPy
- Pillow (PIL)
- OpenCV
- Matplotlib

## Repository Structure

```text
assignment-2-object-detection/
├── Assignment_2_Object_Detection_and_Descriptive_Summary.ipynb
├── basketball_player.jpg
├── basketball_detection_result.png
└── README.md
```

## How to Run

1. Open the notebook using the Google Colab link above.
2. Ensure `basketball_player.jpg` is available in the Colab session.
3. Select **Runtime → Run all**.
4. Wait for the YOLO26 model weights to download.
5. Review the manually annotated image and generated description.

## Custom Confidence Filtering

A low model-level confidence value is initially used to retrieve detections. Each result is then evaluated against a custom threshold:

```python
confidence_threshold = 0.35

if confidence < confidence_threshold:
    continue
```

Only detections that satisfy the threshold are displayed and included in the descriptive summary.

## Manual Bounding-Box Visualization

The assignment does not use YOLO’s built-in `result.plot()` method. Bounding boxes and labels are drawn manually:

```python
cv2.rectangle(
    annotated_image,
    (x1, y1),
    (x2, y2),
    (255, 0, 0),
    3
)

cv2.putText(
    annotated_image,
    label,
    (x1, text_y),
    cv2.FONT_HERSHEY_SIMPLEX,
    0.7,
    (255, 0, 0),
    2
)
```

## Detected Scene

The model detects the basketball player as a `person` and the basketball as a `sports ball`. The class labels are counted programmatically and used to generate a natural-language description beneath the final image.

## Learning Outcomes

This project demonstrates:

- YOLO26 inference on a custom image
- Bounding-box coordinate extraction
- Class-ID and class-name extraction
- Custom confidence thresholding
- Manual visualization using OpenCV
- Programmatic object counting
- Natural-language scene summarization
- Technical documentation in Google Colab

## Image Attribution

Add the original image source and licence here:

```text
Image source: [Insert source URL]
Licence: [Insert licence or usage terms]
```

> A freely reusable image from a source such as Wikimedia Commons, Unsplash, Pexels, or Pixabay is recommended for a public repository.

## Training Acknowledgment

This project was completed as part of Computer Vision training coursework. Appreciation is extended to [SDAIA Academy](https://github.com/SDAIAAcademy) for supporting technical learning and open-source project development.
