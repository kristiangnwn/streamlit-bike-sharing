# 🚲 Streamlit Bike Sharing Analysis

Proyek ini merupakan tugas akhir **Dicoding - Belajar Analisis Data dengan Python**.  
Aplikasi ini menganalisis dataset **Bike Sharing** (`day.csv` dan `hour.csv`) menggunakan Python dan menampilkan hasilnya dalam bentuk dashboard interaktif dengan **Streamlit**.

---

## 📊 Fitur Analisis
- **Data Wrangling** → pengumpulan, pemeriksaan, dan pembersihan data.  
- **Exploratory Data Analysis (EDA)** → eksplorasi data harian & per jam.  
- **Visualisasi** → grafik tren, distribusi, dan pola musiman (matplotlib & seaborn).  
- **Dashboard Streamlit** → interaktif untuk eksplorasi data.  
- (Opsional) **Advanced Analysis** → RFM, clustering, atau geospatial.

---

## 🛠️ Tech Stack
- **Python 3.9+**
- **Streamlit**
- **Pandas, Numpy**
- **Matplotlib, Seaborn**
- **Scikit-learn** (opsional untuk analisis lanjut)

---

## 🚀 Cara Menjalankan
1. Clone repository ini:
   ```bash
   git clone https://github.com/kristiangwn/streamlit-bike-sharing.git
   cd streamlit-bike-sharing

## Buat virtual environment
python -m venv .venv
source .venv/bin/activate   # Mac/Linux
.venv\Scripts\activate      # Windows

## Install dependencies:
pip install -r requirements.txt

## Jalankan aplikasi Streamlit:
streamlit run app.py
