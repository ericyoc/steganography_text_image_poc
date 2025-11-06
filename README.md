# Image-Based Steganography in Python

This repository implements **image-based steganography**, allowing you to **embed text or an image** into a cover image using LSB (Least Significant Bit) techniques. The implementation supports **password-protected embedding** and extraction, with **visualization of modified pixels**.

---

## Motivating Research Articles
Babu, T., & Nair, R. R. (2025). Secure Data Embedding in Digital Images: Enhancing Covert Communication with LSB-Based Techniques. Procedia Computer Science, 258, 2091-2100 and found at https://www.sciencedirect.com/science/article/pii/S1877050925015625 

Panigrahi, R., & Padhy, N. (2025). An effective steganographic technique for hiding the image data using the LSB technique. Cyber Security and Applications, 3, 100069 and found at https://www.sciencedirect.com/science/article/pii/S2772918424000353
---

## Concepts: Steganography

**Steganography** is the art of hiding secret information within ordinary, non-suspicious media so that its existence is concealed. Unlike encryption, which scrambles data but clearly indicates the presence of secret information, steganography hides **the fact that a secret exists at all**.

### Key Concepts:

1. **Cover Image** – The original image that hides the secret.  
2. **Payload** – The data being hidden (text or image).  
3. **Embedding** – Process of inserting the payload into the cover image.  
4. **Extraction** – Retrieving the hidden payload from the modified image.  
5. **LSB Embedding** – Modifying the least significant bits of pixel values to encode data, minimizing visual distortion.  
6. **Password Protection** – Uses a password to seed the pseudorandom sequence for pixel selection, ensuring only users with the correct password can extract the data.

### Importance and Use Cases:

- **Privacy and Confidentiality:** Hide messages securely without attracting attention.  
- **Covert Communication:** Communicate secretly in hostile environments.  
- **Digital Watermarking:** Protect intellectual property by embedding ownership marks.  
- **Data Integrity Verification:** Embed hidden checksums to detect tampering.  

---

## Features

- Embed **text** into a cover image and extract it later.  
- Embed a **secret image** into a cover image and extract it later.  
- **Password protection** ensures only authorized extraction.  
- **Visualization**:
  - Highlights modified pixels in **red**.
  - Shows original vs. stego images side by side.
  - Extracted text and image are displayed.

---

## Requirements

- Python 3.x  
- `numpy`  
- `Pillow`  
- `matplotlib`  
- `tqdm`  
- Google Colab (optional for Drive integration)

Install dependencies with:

```bash
pip install numpy pillow matplotlib tqdm
````

---

## Usage

### 1. Mount Google Drive (Colab)

```python
from google.colab import drive
drive.mount('/content/drive')
```

### 2. Place Images in Drive

* **Cover Image**: `cover_image.png`
* **Optional Secret Image**: `secret_image.png`
* Place both under `/content/drive/MyDrive/stego/`.

### 3. Run the Script

```bash
python stego_main.py
```

### 4. Enter Inputs

* Enter a **short password** (used for both embedding and extraction).
* Enter **text to hide** (if embedding text).

### 5. Outputs

* `cover_with_text.png` – Cover image with embedded text.
* `cover_with_image.png` – Cover image with embedded image.
* **Diff overlays** showing red pixels where embedding occurred.
* Extracted **text** and **secret image** displayed.

---

## How It Works

1. **Embedding:**

   * Secret payload is converted into bits.
   * Password generates a **deterministic pseudorandom sequence** of pixel positions.
   * Least significant bits (LSBs) of selected pixels are modified to store the secret.

2. **Visualization:**

   * Pixel-wise difference between original and stego images is computed.
   * Red pixels indicate where changes occurred.

3. **Extraction:**

   * Password recreates the pixel sequence.
   * Reads LSBs to reconstruct the secret.
   * Text is rendered as an image; secret images are displayed.

---

## Examples

### Embedding Text

* **Original Cover Image:** `cover_image.png`
* **Stego Image:** `cover_with_text.png`
* **Diff Overlay:** Pixels in red show where text was embedded.
* **Extracted Text:** Displayed as an image.

### Embedding Image

* **Original Cover Image:** `cover_image.png`
* **Stego Image:** `cover_with_image.png`
* **Diff Overlay:** Pixels in red show where the secret image was embedded.
* **Extracted Secret Image:** Displayed.

---

## Notes

* Keep **text and secret image sizes reasonable** relative to the cover image.
* Default embedding uses **1-bit LSB** for minimal visual distortion.
* Correct **password** is required for extraction.
* This system works best with **PNG images** to avoid lossy compression artifacts.

---

## License

This project is released under the **MIT License**.

---


