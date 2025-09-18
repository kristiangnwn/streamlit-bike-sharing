import streamlit as st
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Set tema dan konfigurasi dasar
st.set_page_config(page_title="Bike Sharing Dashboard", layout="wide")

# Load data
@st.cache_data
def load_data():
    return pd.read_csv("Bike_hour.csv")

df = load_data()

# Sidebar untuk filter
st.sidebar.header("Filter Data")
hour_selected = st.sidebar.slider("Pilih Jam", min_value=0, max_value=23, value=(0, 23))

# Filter data berdasarkan jam
filtered_df = df[(df['hr'] >= hour_selected[0]) & (df['hr'] <= hour_selected[1])]

# Judul Dashboard
st.title("📊 Bike Sharing Dashboard")

### 1️⃣ Visualisasi Tren Penyewaan Sepeda Per Jam
st.subheader("Tren Penyewaan Sepeda Berdasarkan Jam")
hourly_rentals = filtered_df.groupby('hr')['cnt'].mean()  # Menggunakan filtered_df

fig, ax = plt.subplots(figsize=(10, 5))
sns.lineplot(x=hourly_rentals.index, y=hourly_rentals.values, marker='o', ax=ax)
ax.set_xlabel('Jam dalam Sehari')
ax.set_ylabel('Jumlah Penyewaan Sepeda')
ax.set_title('Tren Penyewaan Sepeda Berdasarkan Jam')
ax.grid()

st.pyplot(fig)

### 2️⃣ Visualisasi Pengaruh Cuaca
st.subheader("Pengaruh Cuaca terhadap Penyewaan Sepeda")
weather_rentals = filtered_df.groupby('weathersit')['cnt'].mean()  # Menggunakan filtered_df

fig, ax = plt.subplots(figsize=(8, 5))
sns.barplot(x=weather_rentals.index, y=weather_rentals.values, palette='Blues', ax=ax)
ax.set_xlabel('Kondisi Cuaca')
ax.set_ylabel('Rata-rata Penyewaan')
ax.set_title('Pengaruh Cuaca terhadap Penyewaan Sepeda')

# Perbaiki label x-axis
ax.set_xticks(range(len(weather_rentals.index)))  # Tambahkan ini
ax.set_xticklabels(['Clear', 'Cloudy', 'Light Rain/Snow', 'Heavy Rain/Snow'])

st.pyplot(fig)

### **Kesimpulan**
st.subheader("Kesimpulan 📌")
st.markdown("""
### **1. Kapan waktu dengan jumlah penyewaan sepeda tertinggi dalam sehari?**
- Penyewaan sepeda **paling tinggi terjadi pada jam 08:00 dan 17:00**.
- Hal ini menunjukkan bahwa penggunaan sepeda sangat dipengaruhi oleh jam berangkat dan pulang kerja/sekolah.
- Penyewaan lebih rendah pada dini hari dan larut malam, menunjukkan bahwa sepeda jarang digunakan di luar jam sibuk.

### **2. Bagaimana pengaruh cuaca terhadap jumlah penyewaan sepeda?**
- **Cuaca cerah (Clear) memiliki penyewaan tertinggi**, karena pengguna lebih nyaman bersepeda dalam kondisi cuaca yang baik.
- **Cuaca berawan (Cloudy) masih memiliki tingkat penyewaan yang cukup tinggi**, meskipun sedikit lebih rendah dari cuaca cerah.
- **Hujan ringan atau salju ringan (Light Rain/Snow) menurunkan jumlah penyewaan**, menunjukkan bahwa kondisi cuaca mulai memengaruhi keputusan pengguna.
- **Hujan deras atau salju lebat (Heavy Rain/Snow) menyebabkan penyewaan turun drastis**, karena cuaca ekstrem membuat pengguna enggan bersepeda.

### **Implikasi dan Saran**
- **Menambah jumlah sepeda pada jam sibuk (08:00 & 17:00)** untuk mengakomodasi permintaan yang tinggi.
- **Strategi promosi saat cuaca buruk**, seperti diskon atau penyediaan perlengkapan tambahan (misalnya jas hujan), untuk menjaga tingkat penyewaan tetap stabil.
- **Perawatan ekstra selama musim hujan/salju**, memastikan sepeda dalam kondisi baik dan aman digunakan.

Dengan memahami pola ini, pengelola layanan dapat mengoptimalkan ketersediaan sepeda serta meningkatkan pengalaman pengguna. 🚴‍♂️📊
""")
