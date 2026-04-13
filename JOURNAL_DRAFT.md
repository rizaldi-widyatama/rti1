# Analisis Keamanan Basis Data Menggunakan Penerapan Role-Based Access Control (RBAC)

---

## ABSTRACT

Di era digital yang semakin berkembang, keamanan basis data menjadi aspek kritis dalam menjaga kerahasiaan, integritas, dan ketersediaan informasi organisasi. Penelitian ini menganalisis efektivitas penerapan Role-Based Access Control (RBAC) sebagai mekanisme pengamanan basis data melalui pendekatan analisis komparatif berbasis literatur. Data penelitian berasal dari 15 artikel jurnal ilmiah terbitan 2024-2026 yang membahas implementasi RBAC dalam berbagai konteks sistem informasi. Analisis dilakukan menggunakan kerangka empat dimensi: identifikasi ancaman, mekanisme pencegahan, evaluasi efektivitas, dan rekomendasi optimalisasi. Hasil penelitian menunjukkan bahwa RBAC mampu mengidentifikasi dan memitigasi sepuluh jenis ancaman keamanan basis data, baik eksternal (SQL injection, brute force, malware/ransomware, DDoS, insecure APIs) maupun internal (privilege escalation, insider threats, human error, kesalahan konfigurasi, weak passwords), dengan insider threats menjadi ancaman paling dominan (6 dari 15 paper). RBAC mencegah ancaman melalui empat lapisan mekanisme: autentikasi (Bcrypt hashing, session management, email verification), otorisasi (role-permission mapping, middleware validation, least privilege), level basis data (GRANT/REVOKE, role inheritance, stored procedures), dan level aplikasi (Spatie Permission, Filament Shield). Hasil evaluasi menunjukkan efektivitas tinggi dengan pass rate 100% pada seluruh pengujian fungsional, penurunan violation rate dari 72,73% menjadi 0%, pengurangan rata-rata permission sebesar 43,06%, peningkatan skor keamanan 31,88%, dan skor System Usability Scale (SUS) rata-rata 76 (kategori Good). Integrasi AI/ML dengan RBAC lebih lanjut dapat meningkatkan keamanan hingga 37% dan mengurangi biaya operasional 42%. Penelitian ini merekomendasikan penerapan least privilege secara ketat, regular access review, separation of duty, audit trail komprehensif, serta integrasi RBAC dengan enkripsi AES-256, rate limiting, MFA, input validation, dan IDS/IPS untuk pertahanan berlapis. Transisi menuju ABAC untuk lingkungan dinamis, integrasi blockchain untuk audit trail immutable, dan adopsi post-quantum cryptography menjadi arahan pengembangan masa depan yang krusial.

**Kata kunci:** Role-Based Access Control (RBAC), keamanan basis data, kontrol akses, insider threats, analisis komparatif.

---

## ABSTRACT

In the rapidly evolving digital era, database security has become a critical aspect in maintaining the confidentiality, integrity, and availability of organizational information. This study analyzes the effectiveness of Role-Based Access Control (RBAC) implementation as a database security mechanism through a comparative literature-based analytical approach. Data were sourced from 15 peer-reviewed journal articles published between 2024 and 2026 discussing RBAC implementation across various information system contexts. The analysis was conducted using a four-dimensional framework: threat identification, prevention mechanisms, effectiveness evaluation, and optimization recommendations. The results indicate that RBAC is capable of identifying and mitigating ten types of database security threats, both external (SQL injection, brute force, malware/ransomware, DDoS, insecure APIs) and internal (privilege escalation, insider threats, human error, misconfiguration, weak passwords), with insider threats being the most predominant (6 out of 15 papers). RBAC prevents threats through four layered mechanisms: authentication (Bcrypt hashing, session management, email verification), authorization (role-permission mapping, middleware validation, least privilege), database-level (GRANT/REVOKE, role inheritance, stored procedures), and application-level (Spatie Permission, Filament Shield). Evaluation results demonstrate high effectiveness with a 100% pass rate across all functional testing, a reduction in violation rate from 72.73% to 0%, an average permission reduction of 43.06%, a security score improvement of 31.88%, and an average System Usability Scale (SUS) score of 76 (Good category). Further integration of AI/ML with RBAC can enhance security by up to 37% and reduce operational costs by 42%. This study recommends strict enforcement of least privilege, regular access review, separation of duty, comprehensive audit trails, and integration of RBAC with AES-256 encryption, rate limiting, MFA, input validation, and IDS/IPS for layered defense. Transition toward ABAC for dynamic environments, blockchain integration for immutable audit trails, and adoption of post-quantum cryptography represent crucial future development directions.

**Keywords:** Role-Based Access Control (RBAC), database security, access control, insider threats, comparative analysis.

---

## 1. INTRODUCTION

Di era transformasi digital yang semakin pesat, basis data (database) menjadi komponen krusial dalam sistem informasi modern. Hampir seluruh organisasi, mulai dari institusi pendidikan, layanan kesehatan, sektor bisnis, hingga pemerintahan, mengandalkan basis data untuk menyimpan, mengelola, dan memproses informasi sensitif yang mendukung operasional dan pengambilan keputusan strategis. Namun, ketergantungan ini juga meningkatkan kerentanan terhadap berbagai ancaman keamanan, baik yang berasal dari pihak eksternal maupun internal organisasi.

Berdasarkan laporan Badan Siber dan Sandi Negara (BSSN), Indonesia menghadapi sekitar 190 juta upaya serangan siber selama periode Januari hingga Agustus 2020, angka yang melampaui jumlah serangan pada tahun-tahun sebelumnya [14]. Serangan-serangan ini meliputi SQL injection, ransomware, distributed denial-of-service (DDoS), dan berbagai bentuk eksploitasi lainnya yang menargetkan basis data sebagai sumber informasi utama. Selain ancaman eksternal, faktor internal seperti kesalahan konfigurasi, penyalahgunaan hak akses oleh karyawan, dan human error juga menjadi penyebab signifikan kebocoran data yang sering kali luput dari perhatian [5], [12].

Dalam konteks keamanan basis data, berbagai model kontrol akses telah dikembangkan untuk membatasi dan mengelola hak akses pengguna terhadap data. Model-model tersebut meliputi Discretionary Access Control (DAC), Mandatory Access Control (MAC), Role-Based Access Control (RBAC), dan Attribute-Based Access Control (ABAC). Di antara model-model tersebut, RBAC telah menjadi pendekatan yang paling banyak diadopsi karena kemampuannya dalam menyederhanakan manajemen hak akses berdasarkan peran atau jabatan pengguna dalam organisasi, serta mendukung prinsip least privilege di mana setiap pengguna hanya diberikan akses minimal yang diperlukan untuk menjalankan tugasnya [4], [8], [13].

Meskipun RBAC telah banyak diimplementasikan dalam berbagai sistem informasi, sebagian besar penelitian yang ada berfokus pada aspek implementasi teknis pada domain spesifik—seperti sistem multi-tenant [1], manajemen air bersih [4], stok obat apotek [7], e-learning [10], dan layanan administrasi [11]—tanpa melakukan analisis komparatif yang menyeluruh mengenai efektivitas RBAC dalam menangani berbagai jenis ancaman keamanan basis data. Kesenjangan ini menimbulkan kebutuhan akan sebuah studi yang secara sistematis mengidentifikasi, mengevaluasi, dan membandingkan mekanisme pencegahan RBAC dari berbagai implementasi yang telah ada.

Penelitian ini bertujuan untuk menganalisis keamanan basis data melalui penerapan RBAC dengan menggunakan kerangka analisis empat dimensi: identifikasi ancaman, mekanisme pencegahan, evaluasi efektivitas, dan rekomendasi optimalisasi. Data yang digunakan berasal dari 15 artikel jurnal ilmiah terbitan 2024-2026 yang membahas implementasi dan analisis RBAC dalam berbagai konteks sistem informasi. Hasil analisis diharapkan dapat memberikan pemahaman komprehensif mengenai efektivitas RBAC dalam mengamankan basis data serta rekomendasi praktis bagi pengembang sistem dan pembuat kebijakan keamanan informasi.

---

## 2. LITERATURE REVIEW AND PROBLEM STATEMENT

### 2.1 Literature Review

#### A. Keamanan Basis Data

Keamanan basis data merupakan serangkaian langkah, kebijakan, dan mekanisme yang dirancang untuk melindungi sistem basis data dari berbagai ancaman yang dapat mengganggu kerahasiaan (confidentiality), integritas (integrity), dan ketersediaan (availability) data—yang dikenal sebagai CIA Triad [2], [12]. Ancaman terhadap basis data dapat diklasifikasikan menjadi dua kategori utama: ancaman eksternal dan ancaman internal.

Ancaman eksternal berasal dari luar organisasi dan meliputi serangan siber seperti SQL injection yang memanfaatkan celah keamanan pada query database, ransomware yang mengenkripsi data dan menuntut tebusan, serangan DDoS yang melumpuhkan ketersediaan layanan, dan man-in-the-middle (MITM) yang menyadap komunikasi data [14], [15]. Ancaman internal, di sisi lain, berasal dari dalam organisasi dan mencakup penyalahgunaan hak akses oleh karyawan (insider threats), kesalahan konfigurasi sistem oleh administrator, penggunaan password yang lemah, dan kelalaian pengguna dalam mengikuti prosedur keamanan [5], [12], [14]. Penelitian menunjukkan bahwa lebih dari 80% pelanggaran keamanan sistem basis data disebabkan oleh faktor manusia daripada kerentanan teknis [5], [12].

Strategi pertahanan berlapis (defense in depth) menjadi pendekatan yang direkomendasikan untuk mengamankan basis data, yang mencakup kombinasi kontrol akses, enkripsi data, audit trail, firewall, sistem deteksi intrusi (IDS/IPS), serta pelatihan keamanan bagi pengguna [5], [12], [14].

#### B. Model Kontrol Akses

Model kontrol akses merupakan mekanisme yang mengatur bagaimana subjek (pengguna atau proses) dapat berinteraksi dengan objek (data atau sumber daya) dalam sistem. Empat model utama yang umum digunakan adalah:

| Model | Basis Keputusan | Fleksibilitas | Kompleksitas |
|-------|-----------------|---------------|--------------|
| **DAC** (Discretionary Access Control) | Pemilik data menentukan akses | Tinggi | Rendah |
| **MAC** (Mandatory Access Control) | Label keamanan sistem | Rendah | Tinggi |
| **RBAC** (Role-Based Access Control) | Peran/jabatan pengguna | Sedang | Sedang |
| **ABAC** (Attribute-Based Access Control) | Atribut subjek, objek, konteks | Sangat Tinggi | Tinggi |

DAC memberikan kewenangan kepada pemilik data untuk menentukan siapa yang dapat mengakses sumber daya, namun pendekatan ini terlalu fleksibel dan rentan terhadap pemberian akses yang sembarangan [5], [8]. MAC menerapkan kontrol yang ketat berdasarkan label keamanan, tetapi beban kerjanya besar dan kurang fleksibel untuk lingkungan dinamis [8]. ABAC menawarkan kontrol paling granular berdasarkan atribut dinamis (waktu, lokasi, perangkat), namun kompleksitas implementasinya tinggi [5], [15]. RBAC berada di tengah-tengah, menawarkan keseimbangan antara keamanan dan kemudahan manajemen dengan mengelompokkan pengguna berdasarkan peran organisasi [5], [8], [13].

#### C. Role-Based Access Control (RBAC)

RBAC merupakan model kontrol akses yang menetapkan izin berdasarkan peran atau jabatan yang dimiliki pengguna dalam suatu organisasi [8]. Model RBAC NIST terdiri dari empat komponen utama:

1. **User/Subjek:** Individu atau entitas yang mengakses sistem.
2. **Role/Peran:** Kumpulan tanggung jawab atau fungsi dalam organisasi.
3. **Permission/Izin:** Hak untuk melakukan operasi tertentu terhadap objek (misalnya SELECT, INSERT, UPDATE, DELETE).
4. **Session/Sesi:** Hubungan sementara antara user dengan subset role yang diaktifkan.

RBAC menerapkan dua prinsip fundamental:

- **Least Privilege:** Setiap pengguna hanya diberikan akses minimum yang diperlukan untuk menjalankan tugasnya [4], [5], [13].
- **Separation of Duty (SoD):** Tugas-tugas kritis dipisahkan ke peran yang berbeda untuk mencegah konflik kepentingan dan penyalahgunaan wewenang [4], [13].

Keuntungan utama RBAC meliputi: kemudahan manajemen karena perubahan dilakukan pada tingkat peran bukan individu [8], skalabilitas untuk sistem dengan banyak pengguna [5], dukungan audit trail yang mempermudah pelacakan aktivitas [2], [5], dan reusabilitas peran di berbagai bagian sistem [8], [13]. Keterbatasan RBAC termasuk fenomena "role explosion" di mana jumlah peran menjadi terlalu banyak dan sulit dikelola seiring pertumbuhan organisasi [13], [15], serta ketidakmampuan untuk mempertimbangkan faktor kontekstual seperti waktu atau lokasi akses [5], [15].

#### D. Implementasi RBAC pada Basis Data

RBAC dapat diimplementasikan pada dua level utama: level basis data dan level aplikasi.

Pada **level basis data**, MySQL menyediakan fitur role management sejak versi 8.0 dengan perintah GRANT dan REVOKE untuk memberikan atau mencabut hak akses pada tingkat database, tabel, kolom, hingga prosedur spesifik [2], [9]. PostgreSQL menawarkan mekanisme RBAC yang lebih fleksibel dengan dukungan role inheritance, di mana peran dapat mewarisi hak akses dari peran lain, serta kontrol akses granular hingga tingkat kolom [2], [12]. PostgreSQL juga menyediakan ekstensi pgAudit untuk pencatatan aktivitas pengguna secara detail [2].

Pada **level aplikasi**, framework modern menyediakan package untuk mengelola RBAC secara dinamis. Pada ekosistem Laravel, Spatie Permission menjadi package paling populer yang digunakan dalam berbagai penelitian [1], [4], [6], [7], sementara Filament Shield menawarkan integrasi RBAC dengan admin panel Filament [1]. Pada ekosistem Python, Flask memungkinkan pembuatan decorator kustom seperti `@roles_required` untuk proteksi route berbasis peran [8].

#### E. Ringkasan Penelitian Terdahulu

Tabel berikut merangkum 15 penelitian yang menjadi dasar analisis dalam studi ini.

**Tabel 1. Ringkasan Penelitian Terdahulu**

| Ref | Penulis (Tahun) | Fokus | Metode | Temuan Utama |
|-----|-----------------|-------|--------|--------------|
| [1] | Fitrianto & Sulistyo (2026) | RBAC multi-tenant Laravel | Waterfall, Black Box | kl_id efektif isolasi data 23 kantor |
| [2] | Wahyudi (2025) | Keamanan DBMS MySQL/PostgreSQL | Studi literatur | PostgreSQL unggul audit, MySQL praktis enkripsi |
| [3] | Purwitasari et al. (2026) | RBAC penjualan perhiasan PostgreSQL | R&D Eksperimental | 100% validasi hak akses, 14 tabel kritis |
| [4] | Nasich et al. (2025) | RBAC manajemen air, SoD | SDRE, Z3Prover | Kolusi 72,73%→0%, permission -43,06% |
| [5] | az Zahra & Nasution (2025) | Kontrol akses + enkripsi | Studi literatur | Defense in depth, >80% breach faktor manusia |
| [6] | Mary & Febriyani (2025) | Laravel 12 + Rate Limiting + RBAC | Evaluasi 8 aspek | Skor keamanan 5,38→8,56 (+3,19) |
| [7] | Purba & Hidayasari (2026) | RBAC stok obat apotek | Waterfall, Black Box, SUS | SUS 76 (Good), 100% pass 23 skenario |
| [8] | Prasetia & Manongga (2024) | RBAC Flask PT. XYZ | Test Case | Akses berbasis jabatan, decorator custom |
| [9] | Sukma et al. (2025) | Hak akses hotel MySQL | Eksperimental | GRANT/REVOKE efektif 3 peran |
| [10] | Firmansyah et al. (2026) | RBAC e-learning pemberdayaan perempuan | Waterfall, Black Box | Privilege escalation dicegah, 100% valid |
| [11] | Firmansyah et al. (2025) | RBAC layanan administrasi bahasa | RAD, Black Box + Beta | Digitalisasi proses manual 1.500+ mahasiswa |
| [12] | Hafsah et al. (2025) | Keamanan data database | Studi kasus kualitatif | Enkripsi hibrida terkuat, password lemah |
| [13] | Sahyudi & Susanto (2025) | RBAC pada ERP (SLR) | SLR PRISMA | AI/ML +37% keamanan, biaya -42% |
| [14] | Alifatuzzahra (2025) | Keamanan DB vs kebocoran data | Studi kasus SLR | 190 juta serangan siber, AES-256 + RBAC |
| [15] | Alexander (2025) | Perbandingan keamanan cloud | SLR PRISMA | AES tercepat, ABAC lebih fleksibel |

### 2.2 Problem Statement

Berdasarkan tinjauan literatur di atas, teridentifikasi beberapa kesenjangan dalam penelitian RBAC yang ada. Sebagian besar studi berfokus pada implementasi teknis RBAC pada domain spesifik tanpa melakukan analisis komparatif lintas domain [1], [3], [7], [9], [10], [11]. Beberapa penelitian membahas aspek keamanan basis data secara konseptual tanpa evaluasi kuantitatif mendalam [2], [5], [12], [14]. Hanya sedikit penelitian yang melakukan sintesis komprehensif mengenai efektivitas RBAC dari berbagai perspektif implementasi [13], [15].

Oleh karena itu, penelitian ini merumuskan empat pertanyaan penelitian (Research Questions) yang memandu analisis:

- **RQ1 (Identification):** Ancaman keamanan apa saja terhadap basis data yang dapat diidentifikasi dan dimitigasi melalui penerapan RBAC?
- **RQ2 (Prevention):** Bagaimana mekanisme pencegahan yang diterapkan RBAC terhadap berbagai jenis ancaman keamanan basis data?
- **RQ3 (Evaluation):** Seberapa efektif RBAC dalam menegakkan pembatasan akses berdasarkan hasil pengujian dari berbagai implementasi?
- **RQ4 (Recommendation):** Apa saja praktik terbaik dan rekomendasi untuk mengoptimalkan penerapan RBAC dalam keamanan basis data?

---

## 3. METHOD

Penelitian ini menggunakan pendekatan **analisis komparatif berbasis literatur** (comparative literature analysis) untuk mengevaluasi penerapan RBAC dalam konteks keamanan basis data. Penelitian ini tidak mengembangkan sistem baru, melainkan menganalisis dan mensintesis temuan dari penelitian-penelitian yang telah ada.

### Sumber Data

Data penelitian berasal dari **15 artikel jurnal ilmiah** yang diterbitkan antara tahun 2024 hingga 2026, yang dikumpulkan dalam koleksi "RBAC Journal." Kriteria inklusi yang diterapkan adalah:

1. Artikel membahas penerapan atau analisis RBAC dalam konteks keamanan basis data atau sistem informasi.
2. Artikel memuat hasil pengujian atau evaluasi efektivitas kontrol akses.
3. Artikel diterbitkan dalam jurnal atau prosiding konferensi terakreditasi.
4. Artikel tersedia dalam teks lengkap (full-text).

Kriteria eksklusi meliputi artikel yang hanya membahas RBAC secara teoretis tanpa implementasi atau evaluasi, serta artikel yang tidak membahas aspek keamanan basis data.

### Kerangka Analisis

Analisis dilakukan menggunakan kerangka empat dimensi yang dirancang untuk menjawab keempat pertanyaan penelitian:

| Dimensi | Pertanyaan Penelitian | Fokus Analisis |
|---------|----------------------|----------------|
| **Identifikasi** | RQ1 | Klasifikasi ancaman eksternal dan internal terhadap basis data yang teridentifikasi dalam 15 paper |
| **Pencegahan** | RQ2 | Mekanisme teknis RBAC yang digunakan untuk mencegah/mitigasi setiap jenis ancaman |
| **Evaluasi** | RQ3 | Metrik efektivitas: violation rate, pass rate, SUS score, permission reduction, security score |
| **Rekomendasi** | RQ4 | Best practices, integrasi dengan mekanisme keamanan lain, arahan penelitian masa depan |

### Teknik Analisis Data

Proses analisis dilakukan melalui tahapan berikut:

1. **Ekstraksi Data:** Setiap paper diekstraksi informasi mengenai jenis ancaman yang diidentifikasi, mekanisme RBAC yang diterapkan, metode pengujian yang digunakan, metrik hasil pengujian, dan rekomendasi yang diberikan.
2. **Sintesis Komparatif:** Temuan dari 15 paper dipetakan ke dalam kerangka empat dimensi untuk mengidentifikasi pola, kesamaan, perbedaan, dan tren.
3. **Analisis Tematik:** Temuan dikelompokkan ke dalam tema-tema utama berdasarkan dimensi analisis, kemudian dianalisis secara naratif untuk menghasilkan insight komprehensif.
4. **Perbandingan Metrik:** Metrik kuantitatif dari berbagai paper (violation rate, pass rate, SUS, dll.) dibandingkan untuk mengevaluasi konsistensi dan efektivitas RBAC lintas implementasi.

---

## 4. RESULTS AND DISCUSSION

### 4.1 Identification

Berdasarkan analisis terhadap 15 paper, ancaman keamanan terhadap basis data yang dapat diidentifikasi dan dimitigasi melalui RBAC dapat diklasifikasikan menjadi dua kategori utama: ancaman eksternal dan ancaman internal.

#### A. Ancaman Eksternal

**SQL Injection.** Serangan SQL injection memanfaatkan celah keamanan pada input aplikasi untuk mengeksekusi query berbahaya secara langsung ke database. Ancaman ini diidentifikasi dalam beberapa paper sebagai salah satu vektor serangan paling kritis terhadap basis data [6], [14]. Mary dan Febriyani [6] mencatat bahwa validasi input yang ketat menjadi pertahanan pertama, sementara RBAC berperan sebagai lapisan kedua dengan membatasi permission pengguna sehingga meskipun query berhasil dieksekusi, akses terhadap data tetap dibatasi oleh role yang dimiliki.

**Brute Force Attack.** Serangan brute force mencoba berbagai kombinasi password untuk mendapatkan akses ke akun pengguna. Paper [6] mengimplementasikan Rate Limiting sebagai pencegahan primer, sementara RBAC berfungsi sebagai pembatas damage—bahkan jika akun berhasil diretas, attacker hanya mendapatkan akses sesuai role akun tersebut, bukan akses penuh ke seluruh sistem [6], [14].

**Malware dan Ransomware.** Malware dan ransomware mengancam ketersediaan dan integritas data dengan mengenkripsi atau merusak database. Paper [14] dan [15] mengidentifikasi ancaman ini sebagai salah satu yang paling merusak. RBAC berkontribusi dengan membatasi hak akses _write_ dan _delete_ hanya kepada pengguna yang berwenang, sehingga mengurangi risiko penyebaran malware melalui akun dengan hak akses berlebih [5], [14].

**DDoS dan Insecure APIs.** Serangan DDoS melumpuhkan ketersediaan layanan, sementara kerentanan API membuka akses ilegal ke data cloud [14], [15]. Meskipun RBAC tidak secara langsung mencegah DDoS, mekanisme autentikasi dan otorisasi RBAC membantu memastikan bahwa hanya pengguna terdaftar yang dapat menggunakan resource API, mengurangi beban dari request tidak sah [15].

#### B. Ancaman Internal

**Privilege Escalation.** Penyalahgunaan hak akses di mana pengguna mencoba memperoleh akses di luar role yang diberikan. Paper [10] mengidentifikasi ini sebagai risiko utama pada platform multi-role, di mana peserta e-learning mungkin mencoba mengakses fitur mentor atau admin. RBAC mencegah hal ini melalui validasi role pada setiap request di level middleware [4], [8], [10].

**Insider Threats.** Karyawan atau pengguna internal yang menyalahgunakan akses sah mereka untuk mengakses data di luar tanggung jawab mereka. Paper [4] mencatat bahwa pada sistem spreadsheet tanpa RBAC, setiap pengguna yang memiliki akses file dapat melihat seluruh sheet tanpa batasan, menghasilkan violation rate sebesar 72,73% pada skenario kolusi [4]. Paper [5] dan [12] juga menekankan bahwa insider threat sulit dideteksi karena pelaku memiliki kredensial sah.

**Human Error dan Kesalahan Konfigurasi.** Kesalahan tidak disengaja oleh pengguna atau administrator, seperti mengubah formula pada spreadsheet, salah konfigurasi hak akses, atau menggunakan password lemah. Paper [5] mencatat bahwa lebih dari 80% pelanggaran keamanan basis data disebabkan oleh human error [5], [12]. Paper [7] menunjukkan bahwa tanpa RBAC, semua pengguna di apotek dapat mengakses dan memodifikasi data di luar kewenangan mereka, meningkatkan risiko kesalahan operasional.

**Shared Credentials dan Weak Passwords.** Penggunaan password yang mudah ditebak atau berbagi akun antar pengguna. Paper [12] mengidentifikasi bahwa password seperti "123456" atau "password" masih banyak digunakan, sementara paper [6] mengimplementasikan Bcrypt hashing untuk mengamankan penyimpanan password [6], [12].

**Tabel 2. Matriks Ancaman vs Paper yang Mengidentifikasi**

| Jenis Ancaman | Paper yang Mengidentifikasi | Jumlah Paper |
|---------------|---------------------------|--------------|
| SQL Injection | [6], [14], [15] | 3 |
| Brute Force | [6], [14] | 2 |
| Malware/Ransomware | [14], [15] | 2 |
| DDoS | [14], [15] | 2 |
| Insecure APIs | [15] | 1 |
| Privilege Escalation | [4], [10], [13] | 3 |
| Insider Threats | [4], [5], [12], [13], [14], [15] | 6 |
| Human Error | [5], [12], [14] | 3 |
| Kesalahan Konfigurasi | [9], [14], [15] | 3 |
| Weak Passwords | [6], [12], [14] | 3 |

Dari tabel di atas, **insider threats** merupakan ancaman internal yang paling banyak diidentifikasi (6 dari 15 paper), diikuti oleh **privilege escalation**, **human error**, **kesalahan konfigurasi**, dan **weak passwords** (masing-masing 3 paper). Pada ancaman eksternal, **SQL injection** paling sering dibahas (3 paper). Temuan ini mengindikasikan bahwa penelitian-penelitian yang ada lebih banyak memusatkan perhatian pada risiko yang berasal dari dalam organisasi, yang konsisten dengan literatur yang menyatakan bahwa ancaman internal lebih sulit dideteksi dan lebih berbahaya karena pelaku memiliki akses sah [5], [14].

### 4.2 Prevention

RBAC menerapkan berbagai mekanisme pencegahan untuk melindungi basis data dari ancaman yang telah diidentifikasi. Berdasarkan analisis 15 paper, mekanisme pencegahan RBAC dapat dikategorikan ke dalam empat lapisan:

#### A. Lapisan Autentikasi

Autentikasi merupakan gerbang pertama yang memverifikasi identitas pengguna sebelum masuk ke sistem. Mekanisme yang teridentifikasi meliputi:

- **Password Hashing dengan Bcrypt:** Paper [6] dan [14] mengimplementasikan Bcrypt untuk mengenkripsi password sebelum disimpan ke database, sehingga meskipun database berhasil diakses oleh pihak tidak sah, password tetap tidak dapat dibaca dalam bentuk plain text [6], [14].
- **Session Management:** Setelah login berhasil, sistem menyimpan informasi role pengguna dalam sesi. Paper [8] menggunakan session-based role storage pada Flask, sementara paper [10] menggunakan JSON Web Token (JWT) yang menyimpan role_id untuk verifikasi di setiap request [8], [10].
- **Email Verification:** Paper [10] mengimplementasikan verifikasi email sebagai langkah tambahan pada proses registrasi peserta e-learning, memastikan keaslian identitas sebelum akun diaktifkan [10].

#### B. Lapisan Otorisasi (Inti RBAC)

Otorisasi merupakan lapisan inti RBAC yang menentukan apa yang dapat dilakukan pengguna setelah terautentikasi. Mekanisme yang teridentifikasi:

- **Role-Permission Mapping:** Setiap peran dipetakan dengan permission spesifik (CREATE, READ, UPDATE, DELETE) pada tabel atau modul tertentu. Paper [1] mendefinisikan 8 peran dengan hak akses berbeda untuk 23 kantor layanan [1]. Paper [3] mendefinisikan 4 role dengan akses ke 14 tabel kritis pada sistem penjualan perhiasan [3]. Paper [7] memetakan 4 role dengan matriks akses yang jelas untuk manajemen stok obat [7].

- **Middleware Validation:** Validasi role dan permission dilakukan di level middleware sebelum request diproses. Paper [4] mengimplementasikan middleware `can` dari Spatie Permission yang menolak akses di backend bahkan jika pengguna mencoba mengakses URL secara langsung [4]. Paper [10] menggunakan middleware ExpressJS yang memverifikasi JWT dan role_id sebelum memproses request [10]. Paper [8] membuat decorator custom `@roles_required` pada Flask untuk proteksi route [8].

- **Prinsip Least Privilege:** Setiap role hanya diberikan permission minimum. Paper [4] mencatat rata-rata pengurangan permission sebesar 43,06% dibandingkan sistem spreadsheet sebelumnya [4]. Paper [7] memastikan Apoteker hanya bisa mengelola obat keluar (tidak bisa masuk), dan Admin hanya bisa mengelola obat masuk (tidak bisa keluar) [7].

#### C. Lapisan Basis Data (Database-Level)

- **GRANT dan REVOKE (MySQL):** Paper [2] dan [9] mengimplementasikan perintah SQL GRANT dan REVOKE untuk memberikan atau mencabut hak akses pada level database, tabel, dan kolom [2], [9]. Pada sistem hotel ABC, Manajer mendapatkan `GRANT ALL PRIVILEGES`, Resepsionis mendapatkan `GRANT SELECT, INSERT, UPDATE` pada tabel tertentu, dan Tamu hanya `GRANT SELECT, INSERT, UPDATE` pada tabel reservasi sendiri [9].

- **Role Inheritance (PostgreSQL):** Paper [2] dan [3] memanfaatkan fitur role inheritance pada PostgreSQL di mana peran dapat mewarisi hak akses dari peran lain, menyederhanakan manajemen pada struktur organisasi hierarkis [2], [3]. Paper [3] menggunakan perintah GRANT dan REVOKE melalui pgAdmin 4 dan DBeaver untuk mengelola akses 4 role terhadap 14 tabel [3].

- **Stored Procedures dan PL/pgSQL:** Paper [8] mengimplementasikan fungsi PL/pgSQL `get_menu(kode_jabatan)` pada PostgreSQL yang mengembalikan daftar menu yang dapat diakses berdasarkan jabatan dalam format JSON [8].

#### D. Lapisan Aplikasi (Application-Level)

- **Spatie Permission (Laravel):** Package RBAC paling populer, digunakan pada paper [1], [4], [6], dan [7]. Menyediakan fitur definisi role dan permission secara dinamis, middleware `can` dan `@can`, serta integrasi dengan Laravel's authentication system [4], [6].

- **Filament Shield (Laravel):** Paper [1] menggunakan Filament Shield yang terintegrasi dengan admin panel Filament untuk manajemen role dan permission secara visual melalui checkbox [1].

- **Custom Implementation:** Paper [10] dan [11] mengimplementasikan RBAC secara custom menggunakan middleware ExpressJS dan Laravel, masing-masing disesuaikan dengan kebutuhan platform e-learning dan layanan administrasi [10], [11].

**Tabel 3. Mekanisme Pencegahan RBAC per Jenis Ancaman**

| Ancaman | Mekanisme Pencegahan RBAC | Paper Rujukan |
|---------|--------------------------|---------------|
| SQL Injection | Least privilege membatasi query scope, validasi input middleware | [6], [14] |
| Brute Force | Rate limiting + RBAC membatasi damage per role | [6], [14] |
| Insider Threats | Role-based permission, audit trail, SoD | [4], [5], [12], [13] |
| Privilege Escalation | Middleware role validation di setiap request | [4], [8], [10] |
| Human Error | Pembatasan akses sesuai fungsi mengurangi risiko kesalahan | [7], [12] |
| Weak Passwords | Bcrypt hashing + RBAC membatasi akses akun lemah | [6], [12] |
| Unauthorized Access | GRANT/REVOKE, role-permission mapping | [2], [3], [9] |

### 4.3 Evaluation

Efektivitas RBAC dievaluasi melalui berbagai metode pengujian yang digunakan dalam 15 paper. Bagian ini membandingkan hasil pengujian dan metrik efektivitas dari berbagai implementasi.

#### A. Metode Pengujian yang Digunakan

**Tabel 4. Metode Pengujian per Paper**

| Paper | Metode Pengujian | Jumlah Skenario | Pass Rate |
|-------|-----------------|-----------------|-----------|
| [1] Fitrianto & Sulistyo | Black Box | 8 | 100% |
| [3] Purwitasari et al. | Privilege validation (DBeaver) | 14 tabel | 100% |
| [4] Nasich et al. | White Box + Black Box | 67 + 37 | 100% |
| [6] Mary & Febriyani | Evaluasi 8 aspek | — | — |
| [7] Purba & Hidayasari | Black Box + SUS | 23 + 4 responden | 100% |
| [8] Prasetia & Manongga | Test Case | 5 | 100% |
| [9] Sukma et al. | Simulasi eksperimental | 3 peran | 100% |
| [10] Firmansyah et al. | Black Box | 10 | 100% |
| [11] Firmansyah et al. | Black Box + Beta | — | — |
| [13] Sahyudi & Susanto | SLR (meta-analysis) | 10 artikel | — |
| [15] Alexander | SLR (meta-analysis) | 65-87 studi | — |

Dari 11 paper yang melakukan pengujian langsung, **Black Box Testing** merupakan metode paling dominan (7 paper), diikuti oleh **White Box Testing** (1 paper), **Test Case** manual (1 paper), **simulasi eksperimental** (1 paper), dan **SUS/User Acceptance Testing** (2 paper). Dua paper sisanya merupakan systematic literature review [13], [15].

Seluruh paper yang melakukan pengujian fungsional melaporkan **pass rate 100%**, mengindikasikan bahwa RBAC berhasil diterapkan sesuai spesifikasi dalam setiap konteks implementasi.

#### B. Metrik Efektivitas Kuantitatif

Selain pass rate, beberapa paper melaporkan metrik kuantitatif yang lebih spesifik:

**Violation Rate (Tingkat Pelanggaran Akses).** Paper [4] oleh Nasich et al. merupakan satu-satunya yang mengukur violation rate secara komparatif. Pada sistem spreadsheet tanpa RBAC, violation rate pada skenario kolusi mencapai 72,73% (8 dari 11 langkah uji berhasil dilakukan oleh pihak yang tidak berwenang). Setelah implementasi RBAC, violation rate turun menjadi **0%**—seluruh 11 langkah uji yang seharusnya tidak diperbolehkan berhasil ditolak oleh sistem [4]. Metrik ini menjadi bukti paling kuat efektivitas RBAC dalam mencegah akses tidak sah.

**Permission Reduction (Pengurangan Hak Akses).** Paper [4] juga mengukur bahwa implementasi RBAC menghasilkan pengurangan rata-rata permission sebesar **43,06%** dibandingkan sistem spreadsheet. Ini berarti hampir setengah dari hak akses yang sebelumnya dimiliki pengguna secara default berhasil dikurangi sesuai prinsip least privilege [4]. Secara per role, pengurangan tertinggi pada Superadmin (68%) dan terendah pada Resepsionis (20%) [4].

**Security Score Improvement.** Paper [6] oleh Mary dan Febriyani mengevaluasi keamanan menggunakan 8 aspek (Manual Code Inspection, Best Practices, Security Review, Performance Review, Database Operations, Code Organization, Error Handling, File Management). Skor rata-rata sebelum perbaikan sebesar **5,375/10** meningkat menjadi **8,5625/10** setelah implementasi RBAC dan Rate Limiting, memberikan peningkatan sebesar **+3,19 poin** atau sekitar **31,88%** [6]. Peningkatan tertinggi pada aspek Code Organization dan Best Practices (masing-masing +4,0) [6].

**System Usability Scale (SUS).** Paper [7] oleh Purba dan Hidayasari mengukur penerimaan pengguna menggunakan instrumen SUS. Skor rata-rata SUS sebesar **76** dengan kategori "Good" [7]. Per role: Superadmin 75, Admin 80, Apoteker 70, Owner 79. Skor Apoteker yang paling rendah (70) kemungkinan karena peran ini memiliki akses paling terbatas, sehingga persepsi kemudahan penggunaan lebih rendah dibandingkan Admin (80) yang memiliki akses lebih luas [7].

**Code Coverage.** Paper [4] melaporkan code coverage sebesar **95,25%** pada pengujian white box terhadap RbacController, mengindikasikan bahwa hampir seluruh jalur eksekusi kode RBAC teruji [4].

**Evaluasi Performa.** Paper [15] oleh Alexander mencatat bahwa evaluasi kebijakan ABAC memiliki latensi rata-rata **194,89 ms** untuk kebijakan kompleks [15]. Meskipun paper ini tidak mengukur latensi RBAC secara langsung, literatur yang disintesis menunjukkan bahwa RBAC memiliki overhead yang lebih rendah dibanding ABAC karena keputusan akses berbasis role statis lebih sederhana dibanding evaluasi multi-atribut dinamis [15].

**Peningkatan Keamanan dari Integrasi AI/ML.** Paper [13] oleh Sahyudi dan Susanto melaporkan bahwa integrasi AI/ML (decision tree dan random forest) dengan RBAC dapat meningkatkan keamanan hingga **37%** dan mengurangi biaya operasional sebesar **42%** [13]. Otomatisasi dalam penerapan RBAC terbukti mengurangi waktu pengelolaan hingga **65%** dibanding pendekatan manual [13].

#### C. Analisis Konsistensi dan Keterbatasan

Secara keseluruhan, hasil pengujian dari 15 paper menunjukkan **konsistensi tinggi** dalam efektivitas RBAC. Seluruh implementasi RBAC melaporkan keberhasilan dalam membatasi akses sesuai peran, mencegah privilege escalation, dan menolak akses tidak sah.

Namun, terdapat beberapa keterbatasan dalam evaluasi yang ada:

1. **Dominasi Black Box Testing:** 7 dari 11 paper pengujian hanya menggunakan Black Box, yang tidak mengevaluasi struktur internal kode RBAC. Hanya paper [4] yang melakukan White Box Testing dengan code coverage [4].
2. **Tidak Ada Pengujian Keamanan Mendalam:** Sebagian besar paper tidak melakukan penetration testing atau evaluasi kerentanan terhadap serangan siber canggih. Pengujian umumnya terbatas pada skenario fungsional normal.
3. **Tidak Ada Studi Longitudinal:** Seluruh paper mengevaluasi RBAC pada satu titik waktu. Tidak ada yang mengukur efektivitas RBAC dalam jangka panjang (misalnya setelah 6 atau 12 bulan penggunaan).
4. **Sampel Pengguna Kecil:** Paper yang melakukan UAT (seperti paper [7] dengan 4 responden) memiliki sampel yang sangat kecil, sehingga generalisasi hasil terbatas [7].

### 4.4 Recommendation

Berdasarkan sintesis temuan dari 15 paper, bagian ini merumuskan rekomendasi optimalisasi penerapan RBAC untuk keamanan basis data dalam tiga kategori: praktik terbaik (best practices), integrasi dengan mekanisme keamanan lain, dan arahan untuk pengembangan masa depan.

#### A. Best Practices Implementasi RBAC

**1. Terapkan Prinsip Least Privilege Secara Ketat.** Setiap peran hanya boleh memiliki permission minimum yang diperlukan untuk menjalankan fungsinya. Paper [4] membuktikan bahwa penerapan least privilege berhasil mengurangi permission hingga 43,06% dan menurunkan violation rate dari 72,73% menjadi 0% [4]. Paper [5], [12], dan [13] juga menekankan prinsip ini sebagai fondasi RBAC [5], [12], [13].

**2. Lakukan Regular Access Review.** Audit dan tinjauan hak akses secara berkala diperlukan untuk memastikan bahwa permission tetap sesuai dengan kebutuhan pengguna yang mungkin berubah seiring waktu. Paper [2] dan [13] merekomendasikan review hak akses secara periodik untuk mencegah akumulasi hak akses yang tidak lagi relevan [2], [13].

**3. Terapkan Separation of Duty (SoD).** Pisahkan tugas-tugas kritis ke peran yang berbeda untuk mencegah konflik kepentingan. Paper [4] mengidentifikasi 6 constraint SoD, termasuk larangan satu role memiliki kombinasi permission CREATE pada MeterReading, Bill, dan Journal secara bersamaan [4].

**4. Hindari Role Explosion.** Paper [13] dan [15] memperingatkan fenomena "role explosion" di mana jumlah peran menjadi terlalu banyak dan tidak terkendali seiring pertumbuhan organisasi [13], [15]. Solusinya: gunakan role hierarchy (peran hierarkis yang mewarisi permission dari peran di bawahnya) dan lakukan role mining secara berkala untuk mengonsolidasi peran yang redundan.

**5. Implementasikan Audit Trail yang Komprehensif.** Catat setiap aktivitas akses pengguna, termasuk login, query yang dieksekusi, data yang diubah, dan waktu akses. Paper [2], [5], [12], dan [15] menekankan pentingnya audit trail untuk deteksi insider threat dan kepatuhan regulasi [2], [5], [12], [15]. Paper [10] mengimplementasikan tabel `audit_logs` yang mencatat timestamp, user_id, dan status setiap aktivitas login [10].

#### B. Integrasi dengan Mekanisme Keamanan Lain

RBAC tidak boleh berdiri sendiri sebagai satu-satunya mekanisme keamanan. Berdasarkan temuan 15 paper, RBAC perlu diintegrasikan dengan:

**Enkripsi Data.** Paper [5], [12], [14], dan [15] merekomendasikan enkripsi (khususnya AES-256) untuk melindungi data sensitif saat disimpan (at rest) dan saat dikirim (in transit) [5], [12], [14], [15]. Enkripsi menjadi lapisan terakhir yang melindungi data meskipun RBAC berhasil ditembus—data yang dicuri tetap tidak dapat dibaca tanpa kunci dekripsi [12], [15].

**Rate Limiting.** Paper [6] mengimplementasikan Rate Limiting pada Laravel 12 untuk membatasi jumlah request dalam periode waktu tertentu, mencegah serangan brute force pada autentikasi [6]. Kombinasi Rate Limiting + RBAC menghasilkan peningkatan skor keamanan sebesar 31,88% [6].

**Multi-Factor Authentication (MFA/2FA).** Paper [2] dan [14] merekomendasikan penambahan lapisan autentikasi kedua (seperti OTP atau biometrik) di samping password [2], [14]. Meskipun belum diimplementasikan dalam paper-paper yang dianalisis, MFA menjadi standar industri yang semakin penting mengingat meningkatnya serangan berbasis kredensial [10], [14].

**Input Validation dan Sanitasi.** Paper [6] dan [14] menekankan pentingnya validasi input ketat untuk mencegah SQL injection dan Cross-Site Scripting (XSS) [6], [14]. RBAC dan input validation saling melengkapi: input validation mencegah serangan masuk, RBAC membatasi dampak jika serangan berhasil.

**Firewall dan IDS/IPS.** Paper [14] merekomendasikan penggunaan firewall, Intrusion Detection System (IDS), dan Intrusion Prevention System (IPS) untuk mendeteksi dan menghentikan serangan secara real-time sebelum mencapai database [14].

#### C. Arahan Pengembangan Masa Depan

**Transisi dari RBAC ke ABAC untuk Lingkungan Dinamis.** Paper [5] dan [15] mengidentifikasi bahwa RBAC bersifat statis dan tidak mampu mempertimbangkan faktor kontekstual seperti waktu, lokasi, atau perangkat akses [5], [15]. ABAC menawarkan kontrol granular berbasis atribut dinamis, memungkinkan aturan seperti "akses hanya diperbolehkan pada jam kerja dari jaringan kantor" [5], [15]. Meskipun kompleksitas ABAC lebih tinggi, transisi bertahap dari RBAC menuju ABAC atau hybrid RBAC-ABAC direkomendasikan untuk lingkungan cloud dan multi-tenant yang dinamis [5], [15].

**Integrasi AI/ML untuk Deteksi Anomali.** Paper [13] melaporkan bahwa integrasi machine learning (decision tree, random forest) dengan RBAC meningkatkan keamanan hingga 37% dan mengurangi biaya operasional 42% [13]. AI/ML dapat menganalisis pola perilaku pengguna secara real-time dan mendeteksi anomali yang mengindikasikan insider threat atau compromised account [13], [15]. Paper [15] juga menyebutkan Federated Learning sebagai teknik yang memungkinkan pelatihan model AI tanpa memindahkan data mentah, menjaga privasi sekaligus meningkatkan keamanan [15].

**Blockchain untuk Audit Trail yang Immutable.** Paper [13] mengidentifikasi penggunaan blockchain untuk mencatat aktivitas otorisasi pada buku besar yang tidak dapat diubah (immutable) [13]. Pendekatan ini meningkatkan transparansi dan kepercayaan, terutama untuk kepatuhan terhadap regulasi ketat seperti GDPR atau HIPAA [13], [15].

**Post-Quantum Cryptography (PQC).** Paper [15] memperingatkan bahwa munculnya komputasi kuantum mengancam algoritma asimetris tradisional seperti RSA [15]. Transisi menuju kriptografi pasca-kuantum perlu dipertimbangkan untuk menjaga ketahanan sistem dalam jangka panjang [15].

**Dynamic Role Management.** Paper [10] mengidentifikasi keterbatasan RBAC statis yang memerlukan perubahan kode untuk menambah atau mengubah peran [10]. Pengembangan sistem manajemen peran dinamis di mana administrator dapat mendefinisikan role dan permission baru melalui antarmuka tanpa modifikasi kode menjadi kebutuhan penting untuk skalabilitas.

**Tabel 5. Matriks Rekomendasi Implementasi Berdasarkan Skala Organisasi**

| Rekomendasi | Organisasi Kecil (<50) | Menengah (50-500) | Besar (>500) |
|-------------|----------------------|-------------------|--------------|
| Model RBAC | Flat RBAC | Hierarchical RBAC | RBAC + ABAC Hybrid |
| Package | Spatie Permission | Spatie + custom middleware | Custom + AI/ML |
| Audit | Manual periodic | Automated audit trail | Blockchain immutable logs |
| Enkripsi | AES-256 kolom sensitif | AES-256 menyeluruh | PQC-ready |
| Authentication | Password + Bcrypt | + MFA/OTP | + Biometrik/Adaptive |
| Review Akses | 6 bulan sekali | 3 bulan sekali | Real-time monitoring |

---

## 5. CONCLUSION

Penelitian ini menganalisis keamanan basis data melalui penerapan Role-Based Access Control (RBAC) dengan menggunakan kerangka analisis empat dimensi berdasarkan sintesis 15 artikel jurnal ilmiah. Berdasarkan hasil analisis, berikut adalah jawaban terhadap keempat pertanyaan penelitian:

**Pertama (RQ1 — Identifikasi):** RBAC dapat mengidentifikasi dan memitigasi sepuluh jenis ancaman keamanan basis data, yang terbagi menjadi ancaman eksternal (SQL injection, brute force, malware/ransomware, DDoS, insecure APIs) dan ancaman internal (privilege escalation, insider threats, human error, kesalahan konfigurasi, weak passwords). Insider threats merupakan ancaman yang paling banyak diidentifikasi (6 dari 15 paper), mengindikasikan bahwa risiko dari dalam organisasi menjadi perhatian utama dalam literatur RBAC.

**Kedua (RQ2 — Pencegahan):** RBAC mencegah ancaman melalui empat lapisan mekanisme: (1) lapisan autentikasi dengan password hashing (Bcrypt), session management, dan email verification; (2) lapisan otorisasi melalui role-permission mapping, middleware validation, dan prinsip least privilege; (3) lapisan basis data menggunakan GRANT/REVOKE (MySQL), role inheritance (PostgreSQL), dan stored procedures; serta (4) lapisan aplikasi melalui package seperti Spatie Permission dan Filament Shield. Setiap lapisan saling melengkapi untuk menciptakan pertahanan berlapis terhadap ancaman.

**Ketiga (RQ3 — Evaluasi):** RBAC terbukti sangat efektif dalam menegakkan pembatasan akses. Seluruh paper yang melakukan pengujian fungsional melaporkan pass rate 100%. Metrik kuantitatif menunjukkan penurunan violation rate dari 72,73% menjadi 0%, pengurangan rata-rata permission sebesar 43,06%, peningkatan skor keamanan sebesar 31,88%, dan skor SUS rata-rata 76 (kategori Good). Integrasi AI/ML dengan RBAC lebih lanjut dapat meningkatkan keamanan hingga 37% dan mengurangi biaya operasional 42%.

**Keempat (RQ4 — Rekomendasi):** Praktik terbaik implementasi RBAC meliputi penerapan least privilege secara ketat, regular access review, separation of duty, pencegahan role explosion, dan audit trail komprehensif. RBAC perlu diintegrasikan dengan enkripsi (AES-256), rate limiting, MFA, input validation, dan IDS/IPS untuk pertahanan berlapis. Arahan pengembangan masa depan mencakup transisi menuju ABAC untuk lingkungan dinamis, integrasi AI/ML untuk deteksi anomali, blockchain untuk audit trail immutable, dan post-quantum cryptography untuk ketahanan jangka panjang.

### Keterbatasan Penelitian

Penelitian ini memiliki beberapa keterbatasan. Pertama, analisis hanya mencakup 15 artikel jurnal dari koleksi tertentu dengan rentang waktu 2024-2026, sehingga mungkin tidak mencakup seluruh literatur RBAC yang relevan. Kedua, seluruh paper berasal dari konteks Indonesia, sehingga generalisasi temuan ke konteks internasional perlu kehati-hatian. Ketiga, mayoritas paper menggunakan Black Box Testing tanpa penetration testing mendalam, sehingga evaluasi keamanan RBAC terhadap serangan canggih belum terukur secara komprehensif.

### Saran untuk Penelitian Selanjutnya

Penelitian selanjutnya disarankan untuk: (1) melakukan studi longitudinal yang mengukur efektivitas RBAC dalam jangka panjang; (2) melakukan penetration testing dan evaluasi kerentanan RBAC terhadap serangan siber canggih; (3) mengeksplorasi integrasi RBAC dengan ABAC untuk kontrol akses kontekstual; (4) mengembangkan model RBAC dinamis yang tidak memerlukan perubahan kode untuk modifikasi peran; dan (5) membandingkan efektivitas RBAC across berbagai DBMS (MySQL, PostgreSQL, Oracle, MongoDB) secara empiris.

---

## 6. REFERENCES

[1] D. Fitrianto and W. Y. Sulistyo, "Penerapan Role Based Access Control untuk Keamanan Data Multi Tenant SIMPEL Lazismu," *INSECT*, vol. 12, no. 1, pp. 1–10, 2026, ISSN: 2476-9010.

[2] A. J. Wahyudi, "Manajemen User Dan Keamanan Akses Data Dalam DBMS," *JRIIN*, vol. 3, no. 7, pp. 1557–1560, 2025, ISSN: 3025-0919.

[3] A. Purwitasari, T. L. I. Sugata, and A. B. Putra, "Implementasi Role-Based Access Control (RBAC) untuk Keamanan Sistem Informasi Penjualan Perhiasan pada PostgreSQL di pgAdmin 4 dan DBeaver," *MAIKA*, vol. 6, no. 1, pp. 103–114, 2026, ISSN: 2548-9720.

[4] A. K. Nasich, S. A. Wicaksono, and M. C. Saputra, "Implementasi Role Based Access Control (RBAC) dalam Sistem Informasi Manajemen Pelanggan dan Pembayaran Air Berbasis Web (studi pada PT Tirta Wangi Sejahtera)," *J. Pengemb. Teknol. Inf. dan Ilmu Komputer*, vol. 9, no. 9, 2025, ISSN: 2548-964X.

[5] F. az Zahra and M. I. P. Nasution, "Analisis Implementasi Model Kontrol Akses Berbasis Peran dan Enkripsi untuk Keamanan Data pada Sistem Basis Data Relasional," *Socius: Jurnal Penelitian Ilmu-Ilmu Sosial*, vol. 2, no. 12, pp. 561–567, 2025, doi: 10.5281/zenodo.15683326.

[6] T. Mary and N. Febriyani, "Peningkatan Keamanan Sistem Informasi Berbasis Laravel 12 dengan Rate Limiting dan Role-Based Access Control (RBAC)," *JTEKSIS*, vol. 7, no. 3, pp. 473–481, 2025, doi: 10.47233/jteksis.v7i3.1976.

[7] D. A. Purba and N. Hidayasari, "Implementasi Role-Based Access Control (RBAC) pada Sistem Informasi Manajemen Stok Obat," *Sistemasi*, vol. 15, no. 2, pp. 684–698, 2026, ISSN: 2302-8149.

[8] Y. A. Prasetia and D. Manongga, "Role-Based Access Control (RBAC) untuk Sistem Otorisasi Terpusat Berbasis Flask Studi Kasus PT. XYZ," *JIPI*, vol. 9, no. 4, pp. 1768–1778, 2024, doi: 10.29100/jipi.v4i1.5403.

[9] W. N. M. Sukma, R. M. Kotalima, H. A. Gazani, A. S. Fitri, and A. B. Putra, "Implementasi Hak Akses untuk Meningkatkan Keamanan Manajemen Hotel ABC Berbasis Database MySQL," in *Proc. SNESTIK V*, Surabaya, Indonesia, 2025, pp. 477–484, doi: 10.31284/p.snestik.2025.7370.

[10] R. Firmansyah, A. Hamdi, and D. Riandini, "Perancangan Sistem Autentikasi Multi-Role Berbasis RBAC pada Platform E-Learning Pemberdayaan Ekonomi Perempuan," *RABIT*, vol. 11, no. 1, pp. 1094–1104, 2026, doi: 10.36341/rabit.v11i1.7226.

[11] M. Firmansyah, Mustika, and Pujianto, "Implementasi Role-Based Access Control pada Sistem Informasi Layanan Administrasi pada Lembaga Bahasa UM Metro," *JMIK*, vol. 6, no. 2, pp. 113–122, 2025, ISSN: 2721-3501.

[12] A. Hafsah, A. A. B. Kaban, S. L. Ramadhan, and Nurbaiti, "Keamanan Data dalam Sistem Database," *JINU*, vol. 2, no. 4, pp. 183–197, 2025, doi: 10.61722/jinu.v2i4.4997.

[13] M. Sahyudi and E. R. Susanto, "Analisis Implementasi Sistem Keamanan Basis Data Berbasis Role-Based Access Control (RBAC) pada Aplikasi Enterprise Resource Planning," *SATESI*, vol. 5, no. 1, pp. 105–116, 2025, ISSN: 2807-8152.

[14] N. Alifatuzzahra, "Analisis Keamanan Database dalam Menghadapi Ancaman Kebocoran Data di Perusahaan Teknologi Informasi," *IGNITE*, vol. 3, no. 3, pp. 11–22, 2025, doi: 10.59841/ignite.v3i1.2957.

[15] A. D. Alexander, "Studi Perbandingan Model Keamanan Data pada Cloud Computing," *JIFORTY*, vol. 6, no. 2, pp. 105–114, 2025, ISSN: 2722-4058.

---

*End of manuscript.*
