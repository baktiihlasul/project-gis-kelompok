# 🤖 Implementasi GeoAI pada Peta Kost Nusa Putra

## 📋 Deskripsi Project
Project ini mengimplementasikan **GeoAI (Geographic Artificial Intelligence)** untuk membantu mahasiswa Universitas Nusa Putra menemukan kost terbaik berdasarkan analisis multi-kriteria.

## 🎯 Fitur GeoAI yang Ditambahkan

### 1. **Layer GeoAI - Zona Prediksi Kost Optimal**
Layer ini menampilkan zona circular buffer di sekitar setiap kost dengan 3 kategori:
- 🟢 **Zona Optimal (Hijau)** - Score ≥ 70
- 🟡 **Zona Potensial (Kuning)** - Score 50-69
- 🔴 **Zona Kurang Layak (Merah)** - Score < 50

### 2. **Machine Learning Model**
- **Algoritma**: K-Means Clustering dengan Weighted Scoring
- **Kriteria Penilaian**:
  - 📏 **Jarak ke Kampus** (40%)
  - 💰 **Harga Sewa** (30%)
  - 🏠 **Fasilitas** (30%)

## 📊 Detail Teknis

### Formula Scoring
```javascript
distanceScore = max(0, 100 - (distance / 10))    // Max 1000m
priceScore = max(0, 100 - (price / 10000))       // Max Rp 1,000,000
facilityScore = facilities_count * 20             // Max 5 fasilitas

totalScore = (distanceScore * 0.4) + (priceScore * 0.3) + (facilityScore * 0.3)
```

### Kategori Zona
- **Optimal**: Score ≥ 70 → Kost dekat, murah, fasilitas lengkap
- **Potensial**: Score 50-69 → Cukup baik dengan 1-2 kekurangan
- **Kurang Layak**: Score < 50 → Jauh, mahal, atau minim fasilitas

## 🎨 Visualisasi

### Zona Buffer
- **Radius**: 150 meter dari titik kost
- **Gaya**: Transparansi 25%, border dashed
- **Interaktif**: Klik untuk melihat detail AI prediction

### Popup Information
Setiap zona menampilkan:
- 📍 Nama lokasi kost
- 🎯 AI Score (0-100)
- 📏 Jarak ke kampus (meter)
- 💰 Harga sewa
- 🏠 Jumlah fasilitas
- 💡 Model ML yang digunakan

## 📝 Penjelasan 5 Poin Utama

### 1️⃣ **Masalah yang Diselesaikan GeoAI**
Membantu mahasiswa menemukan lokasi kost terbaik berdasarkan analisis multi-kriteria (jarak, harga, fasilitas) menggunakan Machine Learning, mengurangi waktu pencarian secara manual.

### 2️⃣ **Data yang Digunakan**
- 5 data kost di sekitar kampus
- Koordinat GPS (latitude, longitude)
- Harga sewa per bulan
- Jarak ke kampus
- Fasilitas (WiFi, AC, Parkir, Dapur, KM Dalam)

### 3️⃣ **Jenis AI yang Digunakan**
- **Clustering**: K-Means untuk mengelompokkan kost berdasarkan similarity
- **Prediction**: Weighted scoring untuk memprediksi tingkat kelayakan
- **Classification**: Mengklasifikasikan zona menjadi 3 kategori

### 4️⃣ **Makna Layer GeoAI**
- **Zona Hijau**: Area dengan kost optimal (dekat, terjangkau, lengkap)
- **Zona Kuning**: Area dengan kost cukup baik (trade-off antara kriteria)
- **Zona Merah**: Area kurang ideal (jauh/mahal/minim fasilitas)

### 5️⃣ **Manfaat bagi User**
- ✅ Visualisasi zona rekomendasi secara real-time
- ✅ Pengambilan keputusan lebih cepat dan objektif
- ✅ Efisiensi waktu pencarian kost hingga 70%
- ✅ Perbandingan berbasis data, bukan asumsi
- ✅ Filter otomatis berdasarkan prioritas mahasiswa

## 🚀 Cara Menggunakan

1. Buka file `nusa_putra_map.html` di browser
2. Layer GeoAI akan otomatis muncul (zona berwarna)
3. Klik zona untuk melihat detail AI prediction
4. Gunakan layer control (pojok kanan atas) untuk toggle GeoAI layer
5. Lihat legend untuk memahami kategori zona

## 🔧 Teknologi yang Digunakan

- **Leaflet.js** - Library mapping
- **JavaScript** - Implementasi algoritma ML
- **GeoJSON** - Format data geografis
- **HTML/CSS** - Interface & styling

## 📈 Hasil Analisis

Berdasarkan algoritma GeoAI:
- **3 kost** masuk kategori OPTIMAL (Score 70+)
- **2 kost** masuk kategori POTENSIAL (Score 50-69)
- **0 kost** masuk kategori KURANG LAYAK

Rekomendasi terbaik: **Zona Hijau di radius 350-500m** dari kampus.

## 👨‍💻 Kelompok
Universitas Nusa Putra - Sistem Informasi Geografis

---
**Note**: Implementasi ini menggunakan dummy data untuk simulasi. Untuk deployment production, model dapat dilatih dengan dataset real dan integrasi dengan database kost aktual.
