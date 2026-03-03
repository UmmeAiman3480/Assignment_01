# Introduction to Computer Vision — Assignment 01

**Course:** Introduction to Computer Vision  
**Assignment:** 01 (22F-3480)  


-
## Repository Structure

```
aiman/
├── README.md
├── 22f_3480_Assignment_01.ipynb   # Main notebook with all implementations
├── A1_CV(8A).pdf                   # Assignment handout
├── report.md                       # Project report (key insights, analysis, findings)
└── test_images/                    # (Optional) Place your test images here
```

---

## Environment Setup

### Prerequisites

- **Python:** 3.8 or higher  
- **Libraries:** NumPy, Matplotlib, OpenCV (OpenCV used for comparison/loading only, not for core task solutions)

### Installation

1. **Clone or download** this repository.

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   # Windows:
   venv\Scripts\activate
   # Linux/macOS:
   source venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install numpy matplotlib opencv-python
   ```

   Or use a `requirements.txt`:
   ```
   numpy
   matplotlib
   opencv-python
   ```
   Then: `pip install -r requirements.txt`

---

## How to Run

1. **Place test images** in a folder and update paths in the notebook (see *Test Images* below).  
   The notebook currently expects:
   - `OIP (1).jpg` — e.g. low-contrast or first test image  
   - `OIP.jpg` — e.g. dark/underexposed or second test image  

2. **Open the notebook:**
   ```bash
   jupyter notebook 22f_3480_Assignment_01.ipynb
   ```
   Or open `22f_3480_Assignment_01.ipynb` in VS Code / Cursor with Jupyter support.

3. **Run all cells** in order (Kernel → Run All).  
   Each section corresponds to a question part:
   - **Imports & Load Images** — Load and display two grayscale test images  
   - **Q1(a)** — Histogram equalization from scratch + comparison with `cv2.equalizeHist`  
   - **Q1(b)** — Contrast stretching + comparison with histogram equalization  
   - **Q1(c)** — Gamma (power-law) transformation with multiple gamma values  
   - **Q2(a)** — 2D convolution (zero/replicate/none padding), box/identity/edge kernels  
   - **Q2(b)** — Gaussian kernel and blur (custom vs OpenCV)  
   - **Q2(c)** — Separable Gaussian filtering and timing comparison  
   - **Q3(a)** — Gradients: central difference, Sobel, Prewitt, Roberts  
   - **Q3(b)** — Canny edge detector from scratch (smoothing, gradient, NMS, hysteresis)  
   - **Q3(c)** — Edge detection comparison (gradient, Sobel, LoG, Canny) and noise robustness  

---

## Test Images Used

| Image        | Purpose / Description |
|-------------|------------------------|
| **OIP (1).jpg** | First test image — used for histogram equalization, contrast stretching, gamma, convolution, Gaussian, gradients, Canny, and edge comparison. Can be low-contrast or general. |
| **OIP.jpg**     | Second test image — used for Q1(a) and Q1(b) comparisons (before/after and histograms). Can be dark/underexposed. |

**Note:** The notebook uses paths like `/content/OIP (1).jpg` and `/content/OIP.jpg` (Google Colab style). For local runs, change these to your own paths, e.g.:

- `test_images/OIP (1).jpg`
- `test_images/OIP.jpg`

Ensure both images are grayscale-compatible (color images are converted to grayscale in the notebook).

---

## Assumptions

1. **Input images** are read with OpenCV (`cv2.imread`) and converted to grayscale; valid file paths and readable images are assumed.  
2. **Convolution:** Kernels are odd-sized where applicable; padding uses half-kernel width/height.  
3. **Canny:** Default thresholds used are `low=30`, `high=100`; these can be tuned per image.  
4. **LoG and edge thresholds:** Simple fixed thresholds are used for LoG and gradient magnitude (e.g. LoG threshold 5, gradient 50, Sobel 100); adjust if needed for your images.  
5. **Timing:** Execution time may vary with image size and machine; separable filtering is expected to be faster than full 2D Gaussian.  
6. **Noise test (Q3(c)):** Gaussian noise with σ=25 is added for robustness comparison; results may vary with different random seeds.

---

## Library Usage (per Assignment)

- **Allowed for implementation:** NumPy, Matplotlib.  
- **For comparison/loading only:** OpenCV, scikit-image (e.g. `cv2.equalizeHist`, `cv2.filter2D`, `cv2.GaussianBlur`, `cv2.Canny` are used only for verification, not as the main solution).  
- **Not allowed for core tasks:** Library functions that directly solve the task (e.g. must not use `cv2.equalizeHist` for Q1(a) implementation).

