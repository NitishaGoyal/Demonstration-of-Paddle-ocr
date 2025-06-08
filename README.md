# 📄 PaddleOCR Text Extraction Project

This project uses [PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR), a powerful OCR (Optical Character Recognition) tool, to extract and visualize text from images using Python.

## 🧠 Features

- Extracts text from images using PaddleOCR.
- Displays bounding boxes, recognized text, and confidence scores.
- Works with English-language text (can be extended to other languages).
- Simple and modular Python script.

---

## 📦 Installation

Before running the code, install the required libraries:

```bash
# Upgrade pip
python -m pip install --upgrade pip

# Install PaddlePaddle (check [https://www.paddlepaddle.org.cn/install/quick](https://www.paddlepaddle.org.cn/install/quick) for GPU instructions)
python -m pip install paddlepaddle

# Install PaddleOCR
pip install paddleocr

# Clone the official PaddleOCR repository
git clone https://github.com/PaddlePaddle/PaddleOCR

🧾 Usage
Place the image you want to process inside a folder (e.g., flipkart images/).

Run the Python script.

from paddleocr import PaddleOCR, draw_ocr
from matplotlib import pyplot as plt
import cv2
import os

# Initialize OCR model
ocr = PaddleOCR(lang='en')

# Image path
img_path = os.path.join('.', 'flipkart images/marie.png')

# Perform OCR
result = ocr.ocr(img_path)

# Extract text, boxes, and confidence scores
boxes = [res[0] for res in result[0]]
text = [res[1][0] for res in result[0]]
scores = [res[1][1] for res in result[0]]

# Load font
font_path = os.path.join('PaddleOCR', 'doc', 'fonts', 'latin.ttf')

# Load and convert image
img = cv2.imread(img_path)
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Annotate image
annotated = draw_ocr(img, boxes, text, scores, font_path=font_path)

# Display result
plt.figure(figsize=(15, 15))
plt.imshow(annotated)
plt.axis('off')
plt.show()

🧪 Sample Output
Recognized text printed in the console.

Annotated image with bounding boxes and labels shown using matplotlib.

📜 License
This project uses PaddleOCR, which is under the Apache 2.0 License."# Demonstration-of-Paddle-ocr" 
