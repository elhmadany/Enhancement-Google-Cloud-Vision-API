# Enhancement of OCR Service Provided by Google Cloud Vision API Project

## Problem Statement
### Primary Research Problem
The primary research problem is the limitation of Google Cloud Vision API in handling complex OCR scenarios. Specifically, the current OCR functionality struggles with accurately extracting text from documents with multi-column layouts and pages containing intricate tables. These challenges significantly impact the quality of the extracted text, which is crucial when preparing datasets for training deep learning models and large language models (LLMs). Therefore, the aim of this project is to enhance the Google Cloud Vision API’s performance in these complex situations by applying image processing techniques.

### Complex OCR Scenario with Tables - Page Handling
We have successfully overcome the challenges of extracting textual data from tables within document images and PDF books. Our approach begins by detecting whether a table exists on the image page. If a table is present, we have implemented image processing algorithms to identify both horizontal and vertical lines within the image.

1. **Horizontal Line Detection:** We create a list of horizontal lines, sorting them from top to bottom based on their y-values.
2. **Vertical Line Detection:** For each pair of adjacent horizontal lines, we check for the presence of vertical lines between them. If vertical lines are found, we determine their x-values and calculate their lengths by subtracting the y-values of the top from the bottom (y2 - y1).
3. **Segmentation:** If a vertical line is situated between two horizontal lines, we use it to segment the text, mapping the coordinates of each word's bounding box.

These steps are repeated until all horizontal lines have been processed, treating each detected vertical line as a column (marked with the symbol “‖”) and each horizontal line as a row (marked with the symbol "--"). The resulting text layout is then compared to the output from Google Vision API for OCR before applying our approach.

## Repository Contents
This repository includes:
- **Demo Code:** Explanation and implementation of the algorithms.
- **Sample PDF Pages:** Examples of text and tables used during testing.
- **Jupyter Notebook:** Demonstrates the approach with sample data.
- **Presentation File:** Summarizing the project objectives, methods, and results.

This project is aimed at improving OCR accuracy in complex scenarios, ensuring high-quality datasets for downstream applications such as deep learning and LLM training.

