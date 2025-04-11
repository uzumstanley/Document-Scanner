# Document Scanner

An automated **Document Scanner** that uses OpenCV and Tesseract OCR to transform photos of documents into clean, perspective-corrected scans with extracted text.

<p align="center">
  <img src="https://user-images.githubusercontent.com/XXX/preview.gif" alt="Project Demo" width="70%">
</p>

<details>
<summary><strong>Table of Contents</strong> (click to expand)</summary>

1. [Overview](#overview)  
2. [Key Features](#key-features)  
3. [Tech Stack](#tech-stack)  
4. [Installation & Usage](#installation--usage)  
5. [Project Structure](#project-structure)  
6. [How It Works](#how-it-works)  
7. [Planned Improvements](#planned-improvements)  
8. [Contributing](#contributing)  
9. [License](#license)

</details>

---

## Overview

This **Document Scanner** combines **OpenCV** for perspective transformation and **pytesseract (Tesseract OCR)** for text extraction to produce crisp, scanner-quality images from ordinary photos. It can:

- Detect document edges and **correct perspective**.  
- **Enhance readability** using thresholding and other filters.  
- Extract text using OCR, making the scanned copy easily searchable and editable.

---

## Key Features

- **Automatic Edge Detection** – Finds the boundary of your document with Canny + contours.
- **Perspective Correction** – Warps images to produce a flat, top-down view.
- **OCR Integration** – Extracts text from scanned images for quick editing.
- **Modular Codebase** – Separate files for scanning logic, OCR logic, and utility functions.
- **Cross-Platform Setup** – Works on Windows, macOS, and Linux with minimal changes.

---

## Tech Stack

| Tool / Library  | Purpose                               |
|-----------------|----------------------------------------|
| **Python**      | Core language                          |
| **OpenCV**      | Image processing & computer vision     |
| **pytesseract** | Optical Character Recognition (OCR)    |
| **NumPy**       | Numerical computations & matrix ops    |
| **Tkinter**     | Simplified GUI for file browsing       |

---

## Installation & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/uzumstanley/Document-Scanner.git
cd Document-Scanner
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```
> **Note**: Make sure you have Python 3.7+ installed.

### 3. Install and Configure Tesseract OCR
- **Windows**: [Download Installer](https://github.com/tesseract-ocr/tesseract). After installing, add the Tesseract installation folder to your system `PATH`.
- **macOS**:  
  ```bash
  brew install tesseract
  ```
- **Linux**:  
  ```bash
  sudo apt-get install tesseract-ocr
  ```
Then, specify the full path to `tesseract.exe` in [`ocr.py`](ocr.py#L6) (Windows) or ensure it’s in your PATH (macOS/Linux).

### 4. Run the Application
```bash
python main.py
```
- A file dialog will appear. Select the document image you want to scan.
- Once done, the scanned image appears on the screen, and the extracted text is printed in the console.

---

## Project Structure

```
Document-Scanner
├── main.py             # Starts the GUI, displays scanned output, and prints OCR results
├── requirements.txt    # Project dependencies
├── scanner.py          # Logic for perspective correction & image preprocessing
├── ocr.py              # Text extraction using Tesseract
├── utils.py            # Utility functions (order_points, four_point_transform, etc.)
├── README.md           # Project documentation
└── __pycache__/        # Compiled Python files (ignored by Git)
```

---

## How It Works

1. **Image Preprocessing**: Applies Gaussian blur and Canny edge detection to isolate the document boundary.
2. **Contour Detection**: Finds contours, identifies the largest 4-point polygon (likely the document).
3. **Perspective Transformation**: Uses the four detected points to warp the image, creating a flat, rectangular “scan.”
4. **Binarization**: Thresholds the warped image to improve contrast and readability for OCR.
5. **Text Extraction**: Converts the final image to text via Tesseract OCR (`pytesseract`).

---

## Planned Improvements

- **GUI Enhancements**: Adding progress bars, adjustable filters, and error handling pop-ups.
- **Automatic Cropping**: Detecting and removing any excess borders after warping.
- **Batch Processing**: Scanning multiple images/folders in a single run.
- **PDF Generation**: Exporting scanned images + extracted text as PDF for easy sharing.

---

## Contributing

Contributions and suggestions are welcome! Check out the [Issues](../../issues) tab or open a Pull Request to propose changes.  

1. **Fork** the repo on GitHub.  
2. **Clone** your fork locally.  
3. **Create** a new branch for your feature/bugfix.  
4. **Commit** and push your changes.  
5. **Submit** a Pull Request.

---

## License

This project is licensed under the [MIT License](LICENSE). You are free to use, share, and adapt it, provided you give appropriate credit.

---

### Thanks for checking out the Document Scanner! If you find it helpful, please **star** this repository and consider sharing it with others. 

If you have any questions or suggestions, feel free to [open an issue](../../issues) or contact me directly. I hope this project helps you with your document processing tasks!
