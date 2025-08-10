# SearchablePDF

Convert scanned PDFs into fully searchable, text-layered documents using open-source tools.  
A complete Windows 11 workflow with **Tesseract OCR** and **OCRmyPDF** for fast, accurate results.

---

## 📌 Features
- **Full OCR support** for scanned PDFs
- Keeps the **original layout and images**
- Works entirely **offline** on Windows 11
- Uses **open-source** tools from GitHub
- Supports **multiple languages** (via Tesseract language packs)

---

## 🛠️ Tools Used
- [Tesseract OCR (UB Mannheim build)](https://github.com/UB-Mannheim/tesseract/wiki) – OCR engine
- [OCRmyPDF](https://github.com/ocrmypdf/OCRmyPDF) – PDF handling + text layer generation
- Python 3 – required to run OCRmyPDF

---

## 📥 Installation (Windows 11)

### 1. Install Tesseract OCR
1. Download the latest **Windows installer** from:  
   👉 [https://github.com/UB-Mannheim/tesseract/wiki](https://github.com/UB-Mannheim/tesseract/wiki)
2. Run the installer and **select the language packs** you need (English recommended, more can be added later).
3. Note the installation path (e.g., `C:\Program Files\Tesseract-OCR`).
4. Add Tesseract to the PATH:
   - Press `Win + S` → search for **"Edit the system environment variables"**
   - Click **Environment Variables**
   - Under **System variables**, select `Path` → **Edit** → **New**
   - Paste:
     ```
     C:\Program Files\Tesseract-OCR
     ```
   - Click **OK** to save.

To verify installation, open **PowerShell** and run:
```powershell
tesseract --version
````

---

### 2. Install Python (if not installed)

* Download Python from:
  👉 [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)
* Run the installer and **check** "Add Python to PATH".
* Verify installation:

```powershell
python --version
```

---

### 3. Install OCRmyPDF

Open **PowerShell** and run:

```powershell
pip install ocrmypdf
```

Verify installation:

```powershell
ocrmypdf --version
```

---

## 🚀 Usage

### 1. Place your PDF in a known location

Example: `C:\Users\YourName\Downloads\1.pdf`

### 2. Run OCRmyPDF

Basic command (English OCR):

```powershell
ocrmypdf -l eng "C:\Users\YourName\Downloads\1.pdf" "C:\Users\YourName\Downloads\output.pdf"
```

If your PDF already has a text layer but you want to **replace** it:

```powershell
ocrmypdf --force-ocr -l eng "C:\Users\YourName\Downloads\1.pdf" "C:\Users\YourName\Downloads\output.pdf"
```

---

## 🌍 Language Support

* Download additional Tesseract language packs from the installer or manually from:
  👉 [https://tesseract-ocr.github.io/tessdoc/Data-Files.html](https://tesseract-ocr.github.io/tessdoc/Data-Files.html)
* Use multiple languages by separating with `+`:

```powershell
ocrmypdf -l eng+fra input.pdf output.pdf
```

---

## 🛠 Troubleshooting

`tesseract : The term 'tesseract' is not recognized`

* Tesseract is not in your PATH. Follow Step 1.4 above.

`PriorOcrFoundError: page already has text!`

* Use `--force-ocr` to replace existing text.

### OCRmyPDF runs but text is inaccurate

* Use higher-quality scans (300 DPI recommended).
* Try installing additional language packs for better recognition.

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

---
