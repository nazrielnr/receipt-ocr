# Receipt OCR Research Pipeline

Komparasi arsitektur OCR (Tesseract, EasyOCR, PaddleOCR, DocTR) untuk ekstraksi data struk belanja.

---

## ⚡ Quick Setup (Wajib sebelum buka notebook)

Lakukan langkah ini **sekali** di komputer masing-masing.

### 1. Pastikan Python 3.12 tersedia

Cek via terminal:
```powershell
py -0p
```
Harus ada baris `-V:3.12`. Kalau belum ada, download di [python.org](https://www.python.org/downloads/).

### 2. Buat virtual environment (`.venv`)

```powershell
# Di folder project ini
py -3.12 -m venv .venv
```

### 3. Install semua dependency

```powershell
# PyTorch + CUDA 12.1 (NVIDIA GPU)
.venv\Scripts\pip.exe install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# Semua library OCR & evaluasi
.venv\Scripts\pip.exe install pytesseract easyocr paddleocr paddlepaddle-gpu python-doctr[torch] jiwer rapidfuzz imagehash Pillow opencv-python matplotlib seaborn pandas scikit-learn tqdm ipykernel
```

> **Tidak punya GPU NVIDIA?** Ganti perintah pertama dengan:
> ```powershell
> .venv\Scripts\pip.exe install torch torchvision torchaudio
> ```

### 4. Register kernel Jupyter

```powershell
.venv\Scripts\python.exe -m ipykernel install --user --name ocr-research --display-name "Python 3.12 (OCR Research)"
```

### 5. Install Tesseract OCR Engine

Download installer Windows: [https://github.com/UB-Mannheim/tesseract/wiki](https://github.com/UB-Mannheim/tesseract/wiki)

Pilih versi **64-bit**. Install ke path default: `C:\Program Files\Tesseract-OCR\`

---

## 📂 Struktur Dataset

Setelah setup, tambahkan dataset dengan struktur berikut:

```
dataset/
├── images/
│   ├── clear/       ← struk bersih
│   ├── skewed/      ← struk miring
│   ├── low_light/   ← struk redup
│   └── occluded/    ← struk terpotong
└── annotations/
    └── ground_truth.json
```

> Folder `dataset/` di-ignore oleh `.gitignore` — isi secara manual setelah clone.

---

## 🚀 Buka Notebook

1. Buka `gacor.ipynb` di VS Code
2. Klik **"Select Kernel"** (pojok kanan atas)
3. Pilih **"Python 3.12 (OCR Research)"**
4. Jalankan cell dari atas ke bawah

---

## ⚠️ Catatan

| Library | Status |
|---|---|
| Tesseract, EasyOCR, PaddleOCR, DocTR | ✅ Didukung |
| MMOCR | ⚠️ Skip — belum support Python 3.12 + Windows |
