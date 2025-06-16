# Unsupervised-Learning
Dataset ini berisi data customer sebuah perusahaan penerbangan dan  beberapa fitur yang dapat menggambarkan value dari customer  tersebut
https://drive.google.com/drive/folders/1v7BjYPybGlhQ9oNiPwgA-1l1uh3Vi3yW?usp=sharing (link dataset)

# Overview
Project berupa clustering end-to-end pertanyaan bisnis dimana akan diberikan sebuah dataset mentah berisi data customer untuk dianalisis:
- Exploratory Data Analysis (EDA)
- Data Preprocessing
- Feature Engineering
- Modeling + Evaluasi (Unsupervised)
- Interpretasi model + Rekomendasi Bisnis

Goal : Clustering customers based on dataset and describe their characteristics
Business Impact : Recomendation the best way and strategic approach for each customer clusters

# Data Preprocessing
- Handling Missing Values with imputation mode for kategorical data and median for numerical data
- Transformation and scalling with MinMaxScaler
- Deskripsi Statistik kolom kategorical dan numerical
- Univariate Analysis : Boxplot, KDE Plot
- Multivariate Analysis : Heatmap 

# Feature Engineering
Feature Engineering dilakukan berdasarkan metode RFM (Recency-Frequency-Monetary) yang biasa dilakukan dalam segmentasi customer.
RFM Score : Recency-Frequency-Monetary
- Recency = Hari terakhir transaksi sampai tanggal referensi (3/31/2014)
- Frequency = Jumlah perjalanan
- Monetary = Total spending

Feature yang ditambahkan:
- Recency (Days_Since_Last_Flight) = Selisih hari antara Last_Flight_Date dan 3/31/2014
- Tenure (Customer_Tenure) = Lama pelanggan aktif (dari First_Flight_Date ke 3/31/2014)
- Spending_per_Trip = Total_Spending / Frequency

# Model Pipeline
Baseline Model : K-Means <br>
Model Evaluated : Elbow Methode dan Silhouette Score

# Deskripsi Kontekstual Masing-masing Cluster:
Cluster 0: Aktif Hemat
- Recency rendah (mean: 0.069) → Customer baru saja melakukan penerbangan.
- Tenure menengah (mean: 0.045) → Pelanggan sudah cukup lama menjadi customer, meskipun tidak yang paling lama.
- Spending per trip sangat rendah (mean: 0.017) → Mereka menghabiskan uang sangat sedikit per perjalanan.
- Kesimpulan:
Customer aktif (baru terbang) dan setia (tenure sedang), namun hemat saat terbang. Mungkin pengguna promo, kelas ekonomi, atau short-haul flight.

Cluster 1 : Big Spenders yang Tidak Aktif
- Recency tinggi (mean: 0.729) → Sudah lama tidak terbang.
- Tenure tinggi (mean: 0.039) → Sudah jadi pelanggan cukup lama.
- Spending per trip tinggi (mean: 0.048) → Pengeluaran per perjalanan tinggi.
- Kesimpulan:
Ini adalah customer lama yang loyal tapi tidak aktif lagi baru-baru ini, dan dulunya mereka adalah big spender (mungkin pengguna kelas bisnis/first-class atau frequent flyer internasional).

Cluster 2 : Customer Baru
- Recency menengah (mean: 0.34) → Terbang terakhir kali tidak terlalu lama atau terlalu baru.
- Tenure sangat rendah (mean: 0.041) → Pelanggan baru.
- Spending per trip rendah (mean: 0.023) → Pengeluaran per perjalanan cukup rendah.
- Kesimpulan:
Ini adalah pelanggan baru, sudah mulai melakukan perjalanan tapi belum terlalu aktif, dan pengeluarannya kecil. Bisa jadi mereka sedang mencoba layanan.

# Rekomendasi Bisnis

1. Untuk Cluster 0 (Aktif tapi Hemat)<br>
Strategi Monetisasi: Tawarkan layanan tambahan seperti bagasi ekstra, makanan, atau opsi naik kelas (upsell). Selain itu, perusahaan juga bisa menawarkan paket bundling atau program loyalitas berbasis aktivitas, seperti insentif poin untuk jumlah perjalanan tertentu, guna mendorong frekuensi terbang dan nilai transaksi per perjalanan mereka.

2. Untuk Cluster 1 (Big Spenders yang Tidak Aktif)<br>
Strategi Retensi: Kirimkan email promosi eksklusif, diskon untuk penerbangan jarak jauh, atau program loyalitas VIP. Tujuannya mengaktifkan kembali customer yang berpotensi memberi profit tinggi. Perusahaan dapat mengirimkan kampanye email atau SMS khusus berisi penawaran comeback, seperti diskon besar atau upgrade gratis. Selain itu, membentuk program loyalitas premium seperti keanggotaan VIP atau akses lounge dapat membangun kembali hubungan emosional dan memperkuat keterikatan mereka. Perusahaan juga disarankan untuk melakukan survei singkat untuk mengetahui alasan mengapa mereka berhenti terbang, sebagai dasar untuk memperbaiki layanan atau mengembangkan program retensi yang lebih tepat sasaran.

3. Untuk Cluster 2 (Customer Baru)<br>
Strategi Engagement: Kirim kampanye "Welcome Journey" untuk mengedukasi tentang keuntungan layanan, mileage reward, dan manfaat jadi member premium. Kemudian penawaran promosi khusus untuk pembelian kedua, misalnya potongan harga atau layanan bagasi gratis, juga bisa mendorong mereka untuk kembali terbang. Selain itu, pendekatan personalisasi seperti rekomendasi rute berdasarkan preferensi awal dapat menciptakan pengalaman positif yang memperkuat loyalitas sejak awal.

