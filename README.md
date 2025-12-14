# Customer-Segmentation
Customer Segmentation for Personalized Retail Marketing

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-Sklearn%20|%20Pandas%20|%20Plotly-green)

## 📋 Overview
Proyek ini bertujuan melakukan segmentasi pelanggan (Customer Segmentation) pada dataset **Online Retail** menggunakan analisis **RFM (Recency, Frequency, Monetary)** dan algoritma **K-Means Clustering**.

Pendekatan ini digunakan untuk menggantikan strategi promosi massal yang diberikan secara seragam kepada seluruh pelanggan menjadi **strategi pemasaran yang lebih personal dan tepat sasaran**, berdasarkan perilaku belanja aktual pelanggan.

## 🎯 Business Objective
Tujuan utama dari proyek ini adalah membantu perusahaan ritel menghindari pendekatan promosi yang massal dengan membangun segmentasi pelanggan berbasis data transaksi, sehingga:
- Strategi promosi dapat disesuaikan untuk setiap segmen pelanggan
- Retensi pelanggan dapat ditingkatkan
- Efektivitas kampanye pemasaran menjadi lebih optimal, personal dan efektif

## 📊 Dataset
Dataset yang digunakan adalah `online_retail.csv`, yang berisi data transaksi dari toko online berbasis di UK.

- **Sumber Data:** https://www.kaggle.com/datasets/ulrikthygepedersen/online-retail-dataset  
- **Encoding:** `latin-1`

### Kolom Utama
- `InvoiceNo`: Nomor transaksi
- `CustomerID`: ID unik pelanggan
- `StockCode`: Kode produk
- `Description`: Deskripsi produk
- `InvoiceDate`: Tanggal transaksi
- `Quantity`: Jumlah barang
- `UnitPrice`: Harga per unit
- `Country`: Negara pembelian

### Dataset Overview
- Jumlah data awal: **541,909 baris**
- Jumlah data setelah proses cleaning: **397,924 baris**
- Jumlah CustomerID unik final: **4,339 pelanggan**

## 🛠️ Tech Stack
Proyek ini dibangun menggunakan **Python** dengan library berikut:
- **Data Processing:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn, Plotly Express
- **Machine Learning:** Scikit-Learn (K-Means, StandardScaler, Evaluation Metrics)

## ⚙️ Workflow Analisis

### 1. Data Cleaning
- Menghapus baris tanpa `CustomerID`
- Mengonversi tipe data `InvoiceDate` ke format datetime
- Menghapus transaksi retur/batal (`Quantity <= 0`)
- Menghapus kolom yang tidak relevan (`Country`)

### 2. RFM Feature Engineering
- **Recency (R):** Jumlah hari sejak transaksi terakhir
- **Frequency (F):** Jumlah transaksi unik pelanggan
- **Monetary (M):** Total nilai transaksi pelanggan

### 3. Clustering (K-Means)
- Standarisasi fitur RFM menggunakan `StandardScaler`
- Menentukan jumlah cluster optimal menggunakan **Elbow Method** dan **Silhouette Score**
- Melatih model K-Means dengan jumlah cluster terbaik

#### Clustering Configuration
- Algorithm: K-Means
- Random State: 42
- n_init: 10
- Range K yang diuji: 3–10
- Jumlah cluster optimal: **K = 5**

### 4. Profiling & Evaluasi
- Pemetaan cluster ke segmen bisnis:
  * Big Spenders
  * Champions
  * Loyalists
  * Regular
  * At-Risk
- Evaluasi kualitas clustering menggunakan metrik kuantitatif

## 📐 Clustering Evaluation
- **Silhouette Score:** 0.6176  
- **Davies–Bouldin Index:** 1.1437  
- **Calinski–Harabasz Score:** 3156.85  

Hasil evaluasi menunjukkan bahwa pemilihan **K = 5** menghasilkan cluster yang cukup kompak serta memiliki pemisahan antar cluster yang baik.

## 📈 Visualisasi Hasil
Visualisasi yang dihasilkan dalam proyek ini meliputi:

- **Correlation Heatmap:** Hubungan antar variabel data mentah  
![Correlation Heatmap](Visualisasi/image.png)

- **Elbow Curve:** Menentukan jumlah cluster optimal  
![Elbow Curve](Visualisasi/image-1.png)

- **RFM Heatmap:** Rata-rata nilai RFM pada setiap cluster  
![RFM Heatmap](Visualisasi/image-2.png)

- **2D Scatter Plot:** Sebaran cluster berdasarkan Recency vs Frequency  
![2D Scatter Plot](Visualisasi/image-3.png)

- **Bar Chart:** Distribusi jumlah pelanggan per segmen  
![Segment Distribution](Visualisasi/image-4.png)

### Segment Distribution Insight
Sebagian besar pelanggan berada pada segmen **Regular** dan **At-Risk**, sementara segmen **Big Spenders** dan **Champions** hanya mencakup sebagian kecil pelanggan. Pola ini umum terjadi pada bisnis ritel, di mana sebagian kecil pelanggan memberikan kontribusi nilai transaksi yang sangat besar. 

## 🚀 Cara Menjalankan Code

1. **Clone repository:**
    ```bash
    git clone https://github.com/Tikleboy/Captone_Project_Customer-Segmentation
    ```
2.  **Install Dependencies:**
    Pastikan memiliki library yang dibutuhkan. Menginstallnya via pip:
    ```bash
    pip install numpy pandas seaborn plotly matplotlib scikit-learn
    ```

3.  **Siapkan Dataset:**
    Pastikan file `online_retail.csv` berada di direktori yang sama dengan 'Notebook.ipynb'.

4.  **Jalankan Script:**
    Jalankan file Notebook.


## 📝 Segmentasi
Berikut adalah segmentasi dan karakteristik setiap segmen:

| Segmen            | Karakteristik                                               |
| ----------------- | ----------------------------------------------------------- |
| **Big Spenders**  | Recency rendah, Frequency tinggi, Monetary sangat tinggi.   |
| **Champions**     | Baru saja belanja, sering belanja, pengeluaran besar.       |
| **Loyalists**     | Cukup sering belanja dengan pengeluaran menengah.           |
| **Regular**       | Belanja standar, jarang kembali dalam waktu dekat.          |
| **At-Risk**       | Sudah lama tidak belanja, frekuensi dan pengeluaran rendah. |

## 👥 Author

**Capstone Tim ID : A25-CS315**

**Paulus Ferdinand Stanly Lopez - M891D5Y1563**

**Wahyu Ramadhani - M891D5Y1951**

**Eka Fanya Yohana Dasilva - M401D5X0523**
