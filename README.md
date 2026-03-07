# Optimisasi Performa Database

**Abstrak**

Basis data (database) merupakan komponen vital dalam pengelolaan informasi di berbagai sektor, mulai dari layanan publik hingga industri *e-commerce* skala besar. Dengan pertumbuhan volume data yang eksponensial (*big data*), tantangan terhadap skalabilitas, keamanan, dan efisiensi pemrosesan data, khususnya kinerja *query*, menjadi sangat mendesak. Makalah akademik ini menyajikan tinjauan komprehensif terhadap berbagai teknik dan arsitektur optimisasi basis data yang bersumber dari studi dan implementasi terkini [5], [10]. Metodologi yang digunakan adalah sintesis temuan dari studi empiris dan literatur yang berfokus pada optimasi tingkat *query* dan skema, strategi *caching* dan pendistribusian data, serta implementasi *middleware* dan arsitektur modern [9], [13].

Temuan kunci mengindikasikan bahwa optimalisasi performa tidak hanya dicapai melalui teknik tradisional seperti **indexing** dan **partitioning**, tetapi juga melalui adopsi teknik pemuatan data lanjutan seperti **Batch Loading** dan **Parallel Processing** untuk mencapai *throughput* tertinggi [2]. Lebih lanjut, di lingkungan *e-commerce* yang kompetitif, implementasi arsitektur **Headless Commerce** dengan integrasi *caching* berbasis **Redis** terbukti esensial untuk memenuhi standar kecepatan dan responsivitas modern (seperti **Core Web Vitals**) [9], [13]. Disimpulkan bahwa integrasi strategi optimasi teknis dengan praktik keamanan (misalnya *Parameterized Queries*) serta penataan ulang skema basis data (*database restructuring*) secara berkala merupakan fondasi untuk mencapai kinerja sistem basis data yang andal, efisien, dan berkelanjutan [5], [8].

---

## 1. Pendahuluan

Sistem Basis Data (SBD) memegang peran sentral dalam infrastruktur teknologi informasi, berfungsi sebagai penyimpan, pengelola, dan penyedia data operasional. Dalam konteks perkembangan teknologi digital dan *e-commerce* 4.0, volume dan kompleksitas data terus meningkat, menuntut kualitas dan efektivitas sistem berbasis data yang lebih tinggi [11]. Kegagalan dalam mengoptimalkan kinerja SBD akan berdampak langsung pada lambatnya pemrosesan *query* yang kompleks [5], penurunan kinerja sistem [4], serta risiko kerugian bisnis akibat pengalaman pengguna yang buruk (misalnya waktu respons website yang lambat) [10].

Urgensi optimisasi basis data dapat dilihat dalam beberapa konteks:

*   **Skalabilitas Bisnis:** Platform *e-commerce* besar seperti Shopee memerlukan arsitektur basis data yang mampu menangani lonjakan volume transaksi, terutama saat periode promosi puncak, tanpa mengalami penurunan kinerja signifikan. Hal ini menuntut praktik terbaik seperti **replikasi, partisi, dan *load balancing*** [10].
*   **Efisiensi Operasional:** Dalam manajemen data berskala besar, seperti pengelolaan data kependudukan oleh Kementerian Dalam Negeri, keamanan dan integritas data menjadi krusial, di mana teknologi inovatif seperti **Blockchain** dipertimbangkan untuk menjamin desentralisasi dan *immutability* [12].
*   **Akurasi Data:** Bahkan di lingkungan pendidikan (perpustakaan sekolah), basis data yang tidak terorganisir, berisi duplikasi, dan kesalahan *input* dapat menghambat akurasi pencarian dan efisiensi layanan, yang memerlukan **penataan ulang skema basis data** [8].

Oleh karena itu, tujuan optimisasi basis data adalah untuk meningkatkan efisiensi dan kecepatan sistem [5], memastikan integritas dan aksesibilitas data [2], serta mendukung pengambilan keputusan strategis berbasis fakta [6].

---

## 2. Konsep Dasar Performa Database

Performa basis data mengacu pada efisiensi dan kecepatan basis data dalam mendistribusikan data, baik saat proses *load*, *query*, maupun *update* [2]. Analisis performa basis data yang komprehensif memerlukan pemahaman terhadap metrik dan faktor-faktor yang mempengaruhinya:

### 2.1. Metrik Kinerja Utama

| Metrik Kinerja | Definisi dan Konteks | Referensi |
| :---: | :---: | :---: |
| **Throughput** | Jumlah unit data yang berhasil diproses dalam satuan waktu (misalnya baris data per menit). Teknik *Batch Loading* terbukti mencapai *throughput* tertinggi, yaitu 90.000 baris per menit, dibandingkan *baseline* 50.000 baris per menit [2]. | [2] |
| **Waktu Respons (*Latency*)** | Waktu yang dibutuhkan sistem untuk merespons suatu permintaan (*query*). Optimalisasi database secara langsung meningkatkan kecepatan respons website/aplikasi, yang berkontribusi pada pengalaman pengguna yang lebih lancar [10]. | [10] |
| **Efisiensi I/O** | Kecepatan operasi Input/Output data. *Batch Loading* dan *Parallel Processing* dapat meningkatkan efisiensi I/O, misalnya mencapai 65 MB/s pada *Batch Loading* [2]. | [2] |
| **Penggunaan Sumber Daya** | Persentase pemanfaatan CPU dan memori. *Partitioning* efektif untuk mengurangi penggunaan CPU (menjadi 65%) dan memori (menjadi 58%) dibandingkan *baseline* [2]. | [2] |
| **Core Web Vitals (CWV)** | Metrik performa web yang kritis, termasuk *Largest Contentful Paint* (LCP), *Interaction to Next Paint* (INP), dan *Cumulative Layout Shift* (CLS). Optimasi *e-commerce* melalui arsitektur modern bertujuan meningkatkan skor CWV, yang memengaruhi peringkat pencarian dan konversi bisnis [13]. | [13] |

### 2.2. Faktor yang Mempengaruhi Performa

Menurut Elmasri dan Navathe (2016), performa basis data sangat dipengaruhi oleh desain skema, indeks, dan arsitektur sistem [2]. Lebih lanjut, faktor-faktor yang menentukan mencakup:

*   **Ukuran *Batch*:** Ukuran *batch* yang lebih besar dapat meningkatkan efisiensi *load data* dengan mengurangi *overhead* transaksi. Namun, ukuran yang terlalu besar berisiko menurunkan performa karena beban memori yang meningkat [2].
*   **Arsitektur Sistem:** Penggunaan sistem basis data terpusat dapat menyebabkan penurunan kinerja saat banyak pengguna mengakses secara bersamaan dan rentan terhadap risiko kehilangan data akibat ketergantungan pada satu *server* [4].
*   **Kualitas Skema dan Data:** Skema basis data yang *flat* dan tidak berelasi menyulitkan analisis. Selain itu, basis data yang tidak terorganisir yang mengandung duplikasi data atau kesalahan *input* secara fundamental menurunkan performa *query* dan keakuratan [3], [8].

---

## 3. Teknik Optimisasi Query

Optimisasi *query* berfokus pada penyesuaian struktur permintaan data dan skema basis data untuk meminimalkan waktu eksekusi dan konsumsi sumber daya.

### 3.1. Pengindeksan (*Indexing*)

Indeks adalah struktur data tambahan yang digunakan untuk mempercepat pencarian data. Indeks dapat secara signifikan meningkatkan performa *query*, namun harus digunakan dengan hati-hati dalam proses *load data* karena indeks yang terlalu banyak atau tidak tepat dapat memperlambat proses *insert* dan *update* [2]. Dalam studi empiris, penerapan *indexing* berhasil meningkatkan *throughput* menjadi 54.500 baris per menit [2].

### 3.2. Optimasi Logika Query Tingkat Lanjut

Optimasi logika *query* melibatkan teknik yang memastikan permintaan data diproses dengan cara yang paling efisien oleh *Query Optimizer* DBMS:

**A. Penggunaan *Parameterized Queries***

Untuk mengatasi ancaman keamanan dan inefisiensi, penggunaan *parameterized queries* direkomendasikan. Teknik ini mampu secara signifikan mengurangi risiko serangan **SQL Injection** karena memisahkan perintah SQL dari data yang dimasukkan pengguna. Pengurangan risiko keamanan ini berkontribusi pada keandalan sistem [5].

**B. Prosedur Tersimpan (*Stored Procedures*)**

Penggunaan *stored procedures* pada SQL Server terbukti mampu menurunkan waktu eksekusi *query* hingga lebih dari **90%** dan secara signifikan mengurangi beban kerja pada CPU [5]. *Stored procedures* memungkinkan DBMS untuk menyimpan rencana eksekusi yang telah dioptimalkan, sehingga mengurangi waktu kompilasi *query* pada setiap eksekusi.

**C. Pendekatan Algoritmik dan Heuristik**

*   **Algoritma Pencarian:** Optimasi *query* dapat dilakukan melalui penerapan algoritma pencarian yang efisien [5]. Penggunaan algoritma yang tepat (misalnya *binary search* dibandingkan *linear search* pada data terindeks) dapat mempercepat pemrosesan *query*.
*   **Algoritma Genetik:** Dalam konteks basis data terdistribusi, pendekatan heuristik seperti **Algoritma Genetik** dapat digunakan untuk menentukan rute eksekusi *query* yang paling optimal dengan mempertimbangkan biaya komunikasi dan I/O [5].

### 3.3. Optimasi Proses Data Loading

Proses pemuatan data (*data loading*) yang tidak efisien dapat membebani seluruh sistem basis data. Teknik optimasi utama meliputi:

**A. Batch Loading**

*Batch Loading* adalah teknik memuat data dalam blok besar (*batch*) untuk mengurangi *overhead* transaksi. Teknik ini menunjukkan peningkatan performa terbaik dengan *throughput* mencapai **90.000 baris per menit** dan efisiensi I/O mencapai **65 MB/s** [2].

**B. Parallel Processing**

*Parallel Processing* memungkinkan eksekusi proses *load data* secara bersamaan pada beberapa *thread* atau *core*. Teknik ini secara signifikan meningkatkan *throughput* menjadi **85.700 baris per menit** dan efisiensi I/O menjadi **60 MB/s**, menjadikannya sangat efektif untuk volume data yang besar [2].
Tabel Perbandingan Kinerja Teknik Optimasi Data Loading [2]

| Teknik Optimasi | Throughput (Baris/Menit) | Penggunaan CPU (%) | Penggunaan Memori (%) | Efisiensi I/O (MB/s) |
| :---: | :---: | :---: | :---: | :---: |
| **Baseline (Tanpa Optimasi)** | 50.000 | 75% | 60% | 40 |
| **Indexing** | 54.500 | 70% | 62% | - |
| **Partitioning** | 66.700 | 65% | 58% | 46 |
| **Parallel Processing** | 85.700 | 80% | 75% | 60 |
| **Batch Loading** | **90.000** | 78% | 70% | **65** |

---

## 4. Optimisasi Level Server dan Skema

Optimisasi pada level server dan skema mencakup keputusan arsitektural dan struktural yang memengaruhi cara data disimpan, diakses, dan dikelola secara keseluruhan.

### 4.1. Strategi Caching

**A. Penerapan Redis sebagai Cache**

Penggunaan basis data *Key-Value* seperti **Redis** sebagai *cache* sangat efektif dalam mengatasi masalah keterlambatan pemrosesan *query* pada aplikasi yang menggunakan basis data relasional (misalnya MySQL) dengan volume tinggi.

Redis berfungsi untuk menyimpan data sementara, yang secara signifikan meningkatkan kecepatan akses *endpoint* API dan meningkatkan total waktu respons sistem sebesar **6,74%** [9]. Hal ini sangat relevan untuk data yang memerlukan akses cepat, seperti data autentikasi pengguna dan permintaan transaksi.

**B. HOLAP (*Hybrid Online Analytical Processing*)**

Efisiensi arsitektural juga bisa dicapai melalui pendekatan **HOLAP** (kombinasi dari MOLAP dan ROLAP). HOLAP menawarkan kemudahan dalam analisis data multidimensi, sekaligus memastikan efisiensi dalam hal penyimpanan dan akses data, menjembatani kebutuhan antara kinerja *query* operasional dan analisis data yang mendalam [5].

### 4.2. Arsitektur Basis Data Terdistribusi dan *Decoupled*

**A. Basis Data Terdistribusi (*Distributed Database*)**

Sistem basis data terdistribusi menyimpan data di berbagai lokasi fisik, namun menyatukan data melalui mekanisme khusus menjadi satu kesatuan terpadu [4]. Manfaat utama dari arsitektur ini meliputi:

*   **Peningkatan Keandalan:** Redundansi data meminimalkan risiko kehilangan informasi [4].
*   **Peningkatan Akses:** Dapat meningkatkan kecepatan akses data hingga **30%** dibandingkan sistem terpusat [4].
*   **Pengurangan Beban Server:** Distribusi permintaan data ke lokasi yang relevan dapat mengurangi beban *server* pusat hingga **70%** [4].

**B. Arsitektur Headless/Decoupled Commerce**

Dalam *e-commerce*, pergeseran menuju arsitektur **Headless/Decoupled Commerce** menjadi strategi optimasi performa yang penting. Model ini memisahkan lapisan *frontend* (misalnya dengan **Next.js** atau PWA) dari *backend* (misalnya dengan **Laravel**) melalui API [13]. Keuntungan utamanya adalah fleksibilitas ekstrem untuk optimasi *frontend* tanpa memengaruhi logika bisnis *backend*, yang secara langsung meningkatkan skor **Core Web Vitals** dan indeksasi SEO [13].

### 4.3. Manajemen Skema dan Data Integrity

**A. Penataan Ulang Basis Data (*Database Restructuring*)**

Penataan ulang skema basis data adalah langkah fundamental untuk mengatasi masalah kualitas data, seperti duplikasi atau kesalahan *input*. Dalam kasus implementasi SLiMS, penataan ulang berhasil menunjukkan perbaikan signifikan dalam struktur database, eliminasi duplikasi, dan peningkatan akurasi pencarian koleksi [8].

**B. Desain Basis Data Relasional**

Mengubah basis data yang awalnya *flat* (tidak berelasi, misalnya hasil *web scraping*) menjadi basis data relasional sangat penting untuk sistem pencarian dan analisis yang kompleks [3].

*   **DDL (Data Definition Language):** Perintah DDL (CREATE, DROP, ALTER) digunakan untuk mendeklarasikan, menciptakan, dan membuat relasi antar tabel dengan menentukan indeks kunci (*key*) [3].
*   **DML (Data Manipulation Language):** *Query* DML berfungsi sebagai manipulator data, seperti menampilkan, mengubah, dan mengisi data [3].

### 4.4. Integrasi ETL dan Data Warehouse

Untuk mengoptimalkan analisis data transaksional, proses **ETL (Extract, Transform, Load)** diperlukan untuk mempersiapkan data. ETL memuat data ke dalam *data warehouse* yang terstruktur. Proses ini sangat penting karena data transaksi yang tersedia tidak secara langsung memberikan wawasan yang berguna tanpa adanya proses analisis yang mendalam [6]. Data yang telah dioptimalkan melalui ETL ini kemudian dapat divisualisasikan (misalnya menggunakan Tableau) untuk pengambilan keputusan strategis bisnis dan analisis.

---

## 5. Monitoring dan Pemeliharaan

Monitoring dan pemeliharaan adalah proses berkelanjutan untuk menjamin performa optimal sistem basis data.

### 5.1. Pemantauan Kinerja dan Audit *Query*

Pemeliharaan dilakukan dengan mengukur dan menganalisis metrik kinerja sistem setelah penerapan teknik optimasi:

*   **Pengukuran Komparatif:** Melakukan pengujian kinerja (*benchmark*) untuk mengukur dampak optimalisasi terhadap waktu respons, *throughput*, dan utilitas sumber daya. Dalam studi Shopee, analisis data kuantitatif dari *benchmark* digunakan untuk mengevaluasi pengaruh optimalisasi basis data terhadap kinerja dan pertumbuhan platform [10].
*   **Diagnosis Kueri Mendalam:** Analisis yang lebih rinci (*detailed query diagnosis*) diperlukan untuk mengidentifikasi *endpoint* atau *query* tertentu yang masih mengalami penurunan performa (misalnya pada penerapan *caching* Redis) [9].

### 5.2. Penjaminan Integritas dan Kualitas Data

Aktivitas pemeliharaan yang paling mendasar adalah menjaga kebersihan dan kualitas data, yang secara langsung mencegah *database bloat* dan masalah performa yang diakibatkannya:

*   **Pembersihan Data (*Data Cleaning*):** Penghapusan kolom yang tidak digunakan dan perincian informasi (*refinement*) diperlukan sebelum data dimuat ke dalam basis data untuk analisis. Proses ini memastikan hanya data yang relevan dan bersih yang diproses [3].
*   **Penataan Ulang Periodik:** Melakukan penataan ulang skema secara berkala (misalnya penataan ulang basis data SLiMS) untuk menghilangkan duplikasi dan kesalahan *input* data lama yang terkumpul dari waktu ke waktu, memastikan keakuratan dan kecepatan pencarian tetap terjaga [8].

### 5.3. Pembuatan Sistem *Business Intelligence* (BI)

Pemeliharaan performa juga didukung dengan membangun arsitektur data yang memungkinkan analisis yang efisien. Sistem BI yang terintegrasi memungkinkan analisis data yang lebih dalam dan membantu perusahaan mengidentifikasi peluang bisnis strategis [6]. Visualisasi data interaktif pada *dashboard* memungkinkan tim bisnis mengambil keputusan berdasarkan data, yang merupakan bentuk pengawasan kinerja berbasis hasil [6].

---

## 6. Kesimpulan dan Rekomendasi

### 6.1. Sintesis dan Rekomendasi Praktik Terbaik

Optimalisasi performa basis data adalah proses berlapis yang memerlukan intervensi pada level *query* hingga arsitektural. Temuan dari seluruh studi menunjukkan bahwa tidak ada satu teknik tunggal yang dominan, melainkan kombinasi strategi yang disesuaikan dengan kebutuhan sistem:

1.  **Prioritaskan *Batch Loading* untuk Throughput:** Untuk proses pemuatan data yang intensif, **Batch Loading** dan **Parallel Processing** harus diprioritaskan untuk mencapai *throughput* dan efisiensi I/O tertinggi, meskipun dengan manajemen sumber daya yang cermat [2].
2.  **Kombinasikan Keamanan dan Query Tuning:** Optimalisasi kinerja *query* harus mencakup penggunaan **Indexing** bersama dengan **Parameterized Queries** dan **Stored Procedures** untuk meningkatkan kecepatan sekaligus menahan serangan keamanan (SQL Injection) [5].
3.  **Adopsi Arsitektur *Decoupled* dan *Caching*:** Untuk sistem *e-commerce* dan aplikasi web, adopsi arsitektur **Headless Commerce** yang didukung oleh **Redis *caching*** adalah keharusan untuk memenuhi standar performa modern (CWV) dan menjamin responsivitas [9], [13].
4.  **Pastikan Integritas Skema:** Lakukan **Penataan Ulang (*Restructuring*)** dan konversi dari model *flat* ke relasional menggunakan **DDL/DML** untuk memastikan integritas dan kemudahan analisis data, yang merupakan fondasi performa jangka panjang [3], [8].
5.  **Terapkan ETL untuk Analisis:** Proses **ETL** harus diimplementasikan untuk menyediakan *data warehouse* yang terstruktur guna mendukung analisis data mendalam dan pengambilan keputusan strategis [6].

### 6.2. Pandangan Masa Depan (*Future Trends*)

Masa depan optimisasi basis data akan semakin fokus pada pengamanan dan pendistribusian data di lingkungan yang *hyper-connected*:

*   **Desentralisasi dengan Blockchain:** Teknologi **Blockchain** menawarkan solusi inovatif untuk meningkatkan keamanan database melalui desentralisasi dan *immutability*. Hal ini relevan terutama untuk data sensitif seperti database kependudukan [12].
*   **Peran AI dalam *Query Optimization*:** Pendekatan heuristik seperti **Algoritma Genetik** akan semakin dikembangkan dan mungkin diotomatisasi melalui kecerdasan buatan untuk mengoptimalkan rencana eksekusi *query* secara *real-time* [5].
*   ***Full-Stack Performance Alignment*:** Optimalisasi performa akan meluas dari *database server* hingga ke *frontend*, dengan arsitektur **Headless/Decoupled** menjadi standar industri untuk mencapai skor performa web (CWV) yang tinggi dan pengalaman pengguna yang mulus [13].