# RBAC Journal Collection - Summary Index

> **Auto-generated:** April 12, 2026  
> **Total Papers:** 15  
> **Directory:** `/Users/870041/Downloads/RBAC Journal/`  
> **Languages:** English / Bahasa Indonesia

---

## Table of Contents / Daftar Isi

| # | Filename | Title / Judul | Year | Key Topic |
|---|----------|-------|------|-----------|
| 1 | `1-10.pdf` | Penerapan RBAC untuk Keamanan Data Multi Tenant SIMPEL Lazismu | 2026 | RBAC + Multi-tenant (Laravel) |
| 2 | `1.+jriin+-+aldi+-+1557-1560.pdf` | Manajemen User Dan Keamanan Akses Data Dalam DBMS | 2025 | DBMS Security (MySQL/PostgreSQL) |
| 3 | `1224+-.pdf` | Implementasi RBAC untuk Keamanan Sistem Informasi Penjualan Perhiasan pada PostgreSQL | 2026 | RBAC on PostgreSQL (pgAdmin/DBeaver) |
| 4 | `15257.pdf` | Implementasi RBAC dalam Sistem Informasi Manajemen Pelanggan dan Pembayaran Air | 2025 | RBAC + Separation of Duty (Laravel) |
| 5 | `1785-5389-1-PB.pdf` | Analisis Implementasi Model Kontrol Akses Berbasis Peran dan Enkripsi | 2025 | RBAC + ABAC + PBAC + Encryption |
| 6 | `1976-Article Text-8897-1-10-20250723.pdf` | Peningkatan Keamanan Sistem Informasi Berbasis Laravel 12 dengan Rate Limiting dan RBAC | 2025 | Laravel 12 Security (Rate Limiting + RBAC) |
| 7 | `5403-15846-1-PB.pdf` | Implementasi RBAC pada Sistem Informasi Manajemen Stok Obat | 2026 | RBAC for Pharmacy Stock Management |
| 8 | `5958-16450-1-PB.pdf` | Role-Based Access Control untuk Sistem Otorisasi Terpusat Berbasis Flask | 2024 | RBAC with Python Flask |
| 9 | `7370-29745-1-PB.pdf` | Implementasi Hak Akses untuk Meningkatkan Keamanan Manajemen Hotel ABC Berbasis MySQL | 2025 | MySQL Access Control (Hotel System) |
| 10 | `87-+7226)+Rizal+Firmansyah.pdf` | Perancangan Sistem Autentikasi Multi-Role Berbasis RBAC pada Platform E-Learning | 2026 | RBAC for E-Learning (ReactJS+ExpressJS) |
| 11 | `9875-Article Text-25871-1-10-20251218.pdf` | Implementasi RBAC pada Sistem Informasi Layanan Administrasi Lembaga Bahasa | 2025 | RBAC for Admin Services (Laravel/RAD) |
| 12 | `Annisa+Hafsah+4997.pdf` | Keamanan Data dalam Sistem Database | 2025 | Database Security (Encryption + RBAC) |
| 13 | `Article+Text+0501-105-116.pdf` | Analisis Implementasi Sistem Keamanan Basis Data Berbasis RBAC pada Aplikasi ERP | 2025 | RBAC in ERP Systems (SLR) |
| 14 | `IGNITE+Vol+3+No+3+Juli+2025+hal+11-22.pdf` | Analisis Keamanan Database dalam Menghadapi Ancaman Kebocoran Data | 2025 | Database Security & Data Breach Prevention |
| 15 | `Jiforty-V6N2-4.pdf` | Studi Perbandingan Model Keamanan Data pada Cloud Computing | 2025 | Cloud Security (AES/RSA/ECC, RBAC vs ABAC) |

---

## Detailed Summaries / Ringkasan Detail

---

### 1. `1-10.pdf`

**Full Title:** Penerapan Role Based Access Control untuk Keamanan Data Multi Tenant SIMPEL Lazismu

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | David Fitrianto, Wicaksono Yuli Sulistyo |
| **Institution** | Universitas Siber Muhammadiyah |
| **Journal** | INSECT, Vol. 12 No.01, 2026, ISSN: 2476-9010 |
| **Pages** | 10 |
| **Development Method** | Waterfall |
| **Tech Stack** | Laravel + Filament + Filament Shield |
| **Testing** | Black Box (8 skenario, semua lolos) |

#### 🇬🇧 English

**Summary:**  
Implements RBAC for SIMPEL (Sistem Informasi Manajemen dan Pelaporan), a centralized multi-tenant data management platform for Lazismu Daerah Kebumen integrating reporting from **23 service offices**. Key innovation: integrates `kl_id` (Kantor Layanan ID) as an authentication parameter for row-level data isolation using Laravel's Global Scope. Prevents cross-tenant data access even when users manipulate URL parameters.

**Key Points:**
- Roles: Super Admin, Admin Layanan, Staff Fundraising, Fundraising Daerah, Staff Program, Program Daerah, Keuangan Daerah, Pimpinan
- Uses Filament Shield plugin for dynamic role/permission management
- `kl_id` attribute mandatory for all users; acts as parent for all data
- Black Box testing confirms cross-office data isolation works correctly
- Regional offices can view but cannot modify/delete branch office data

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Mengimplementasikan RBAC untuk SIMPEL (Sistem Informasi Manajemen dan Pelaporan), platform manajemen data multi-tenant tersentralisasi untuk Lazismu Daerah Kebumen yang mengintegrasikan pelaporan dari **23 kantor layanan**. Inovasi utama: mengintegrasikan atribut `kl_id` (Kantor Layanan ID) sebagai parameter autentikasi untuk isolasi data tingkat baris menggunakan Global Scope Laravel. Mencegah akses data lintas tenant bahkan ketika pengguna memanipulasi parameter URL.

**Poin Utama:**
- Peran: Super Admin, Admin Layanan, Staff Fundraising, Fundraising Daerah, Staff Program, Program Daerah, Keuangan Daerah, Pimpinan
- Menggunakan plugin Filament Shield untuk manajemen peran dan izin secara dinamis
- Atribut `kl_id` wajib untuk semua pengguna; bertindak sebagai induk dari seluruh data
- Pengujian Black Box mengkonfirmasi isolasi data antar kantor layanan berjalan dengan benar
- Kantor daerah dapat melihat tetapi tidak dapat mengubah/menghapus data kantor cabang

---

### 2. `1.+jriin+-+aldi+-+1557-1560.pdf`

**Full Title:** Manajemen User Dan Keamanan Akses Data Dalam DBMS

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Author** | Aldi Juli Wahyudi |
| **Institution** | Universitas Pamulang |
| **Journal** | JRIIN, Volume 3, No. 7, Desember 2025, Hal 1557-1560 |
| **Pages** | 4 |
| **Method** | Deskriptif kualitatif, studi literatur + studi kasus |

#### 🇬🇧 English

**Summary:**  
A conceptual paper explaining principles of user management and data access security mechanisms in DBMS, covering authentication, authorization, RBAC, encryption, and logging/auditing. Compares implementation in **MySQL 8.0** and **PostgreSQL**.

**Key Points:**
- Covers CIA Triad (Confidentiality, Integrity, Availability)
- MySQL 8.0: role management, AES_ENCRYPT(), SSL/TLS, audit_log plugin
- PostgreSQL: RBAC with role inheritance, OpenSSL integration, pgAudit extension
- PostgreSQL superior in audit and RBAC flexibility; MySQL more practical for function-based encryption
- Recommends: least privilege principle, multi-factor authentication, periodic access review

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Makalah konseptual yang menjelaskan prinsip-prinsip manajemen pengguna dan mekanisme keamanan akses data dalam DBMS, mencakup autentikasi, otorisasi, RBAC, enkripsi, serta logging dan auditing. Membandingkan implementasi pada **MySQL 8.0** dan **PostgreSQL**.

**Poin Utama:**
- Mencakup CIA Triad (Kerahasiaan, Integritas, Ketersediaan)
- MySQL 8.0: manajemen peran, AES_ENCRYPT(), SSL/TLS, plugin audit_log
- PostgreSQL: RBAC dengan role inheritance, integrasi OpenSSL, ekstensi pgAudit
- PostgreSQL unggul dalam audit dan fleksibilitas RBAC; MySQL lebih praktis untuk enkripsi berbasis fungsi
- Rekomendasi: prinsip least privilege, autentikasi multi-faktor, tinjauan akses berkala

---

### 3. `1224+-.pdf`

**Full Title:** Implementasi Role-Based Access Control (RBAC) untuk Keamanan Sistem Informasi Penjualan Perhiasan pada PostgreSQL di pgAdmin 4 dan DBeaver

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Astri Purwitasari, Tri Luhur Indayanti Sugata, Agung Brastama Putra |
| **Institution** | UPN "Veteran" Jawa Timur |
| **Journal** | MAIKA, Vol.6, No. 1, Januari 2026 |
| **Pages** | 12 |
| **Method** | R&D dengan pendekatan eksperimental |

#### 🇬🇧 English

**Summary:**  
Implements RBAC as layered security mechanism in a jewelry sales information system managing **3 brands, 5 stores, 20 products, 30 customers, and 100 transactions** worth billions of rupiah. Uses PostgreSQL with pgAdmin 4 and DBeaver.

**Key Points:**
- 4 roles: Customer_User (SELECT on 8 tables), Sales_Staff (full operational access), Supplier_User (limited access), Admin (complete control)
- 14 critical tables with role-based privilege restrictions
- 100% success rate in privilege validation testing via DBeaver
- Unauthorized access rejected with "relation does not exist" and "permission denied" errors
- Uses GRANT and REVOKE commands for privilege management

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Mengimplementasikan RBAC sebagai mekanisme keamanan berlapis pada sistem informasi penjualan perhiasan yang mengelola **3 brand, 5 toko, 20 produk, 30 pelanggan, dan 100 transaksi** bernilai miliaran rupiah. Menggunakan PostgreSQL dengan pgAdmin 4 dan DBeaver.

**Poin Utama:**
- 4 peran: Customer_User (SELECT pada 8 tabel), Sales_Staff (akses operasional penuh), Supplier_User (akses terbatas), Admin (kontrol penuh)
- 14 tabel kritis dengan pembatasan hak akses berbasis peran
- Tingkat keberhasilan 100% dalam validasi hak akses melalui pengujian di DBeaver
- Akses tidak sah ditolak dengan error "relation does not exist" dan "permission denied"
- Menggunakan perintah GRANT dan REVOKE untuk manajemen hak akses

---

### 4. `15257.pdf`

**Full Title:** Implementasi Role Based Access Control (RBAC) dalam Sistem Informasi Manajemen Pelanggan dan Pembayaran Air Berbasis Web (studi pada PT Tirta Wangi Sejahtera)

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Alvin Kamal Nasich, Satrio Agung Wicaksono, Mochamad Chandra Saputra |
| **Institution** | Universitas Brawijaya |
| **Journal** | J-PTIIK, Vol. 9, No. 9, September 2025 |
| **Pages** | 9 |
| **Method** | Scenario-Driven Role Engineering (SDRE) |
| **Tech Stack** | Laravel + Spatie Permission |
| **Testing** | White box (67 kasus, 100% lolos, 95.25% coverage), Black box (37 kasus, 100% lolos) |

#### 🇬🇧 English

**Summary:**  
Replaces Google Sheets-based system at PT Tirta Wangi Sejahtera (water utility company) with RBAC-secured web system. Uses **Scenario-Driven Role Engineering** validated with **Z3Prover** for formal constraint verification. Focuses on **Separation of Duty (SoD)** to prevent collusion.

**Key Points:**
- Roles: Pelanggan, Pegawai Lapangan, Kasir, Manajemen Jurnal Transaksi, Direktur, Resepsionis, Finance, Superadmin
- 6 constraints modeled (SoD, cardinality, temporal)
- Collusion violation rate reduced from **72.73% (spreadsheet) to 0% (RBAC)**
- Average permission reduction of **43.06%** (least privilege principle)
- Impersonate feature added for Superadmin to act as other roles while maintaining least privilege
- New architecture separates RBAC into independent RbacService (modular, cross-application capable)

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Mengganti sistem berbasis Google Sheets di PT Tirta Wangi Sejahtera (perusahaan air bersih) dengan sistem web yang diamankan RBAC. Menggunakan **Scenario-Driven Role Engineering** yang divalidasi dengan **Z3Prover** untuk verifikasi constraint secara formal. Berfokus pada **Separation of Duty (SoD)** untuk mencegah kolusi.

**Poin Utama:**
- Peran: Pelanggan, Pegawai Lapangan, Kasir, Manajemen Jurnal Transaksi, Direktur, Resepsionis, Finance, Superadmin
- 6 constraint dimodelkan (SoD, kardinalitas, temporal)
- Tingkat pelanggaran kolusi turun dari **72,73% (spreadsheet) menjadi 0% (RBAC)**
- Rata-rata pengurangan permission sebesar **43,06%** (prinsip least privilege)
- Fitur impersonate ditambahkan untuk Superadmin agar dapat bertindak sebagai peran lain sambil tetap mempertahankan prinsip least privilege
- Arsitektur baru memisahkan RBAC menjadi RbacService independen (modular, dapat digunakan lintas aplikasi)

---

### 5. `1785-5389-1-PB.pdf`

**Full Title:** Analisis Implementasi Model Kontrol Akses Berbasis Peran dan Enkripsi untuk Keamanan Data pada Sistem Basis Data Relasional

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Fatimah az Zahra, Muhammad Irwan Padli Nasution |
| **Institution** | UIN Sumatera Utara |
| **Journal** | Socius, Vol. 02, No. 12, Juni 2025, Hal. 561-567 |
| **Pages** | 7 |
| **Method** | Tinjauan literatur, deskriptif kualitatif |

#### 🇬🇧 English

**Summary:**  
Explores various security models for relational database systems, covering RBAC, ABAC (Attribute-Based Access Control), PBAC (Policy-Based Access Control), encryption, and audit trails. Discusses how these models address threats like unauthorized access, data manipulation, and insider threats.

**Key Points:**
- RBAC: assigns permissions to roles, not individuals; supports least privilege; easier to manage at scale
- ABAC: fine-grained control based on user/resource/environment attributes; more flexible but complex
- PBAC: considers time, location, device for access decisions; suitable for microservices/cloud
- Encryption: essential for data at rest and in transit; key management critical
- Audit trails: log all user activities; enable detection of suspicious behavior
- Human factor: >80% breaches caused by human error; training and policies essential
- Defense in depth: layered approach combining multiple security mechanisms

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Mengeksplorasi berbagai model keamanan untuk sistem basis data relasional, mencakup RBAC, ABAC (Attribute-Based Access Control), PBAC (Policy-Based Access Control), enkripsi, dan audit trail. Membahas bagaimana model-model ini mengatasi ancaman seperti akses tidak sah, manipulasi data, dan ancaman dari dalam.

**Poin Utama:**
- RBAC: memberikan izin kepada peran, bukan individu; mendukung least privilege; lebih mudah dikelola dalam skala besar
- ABAC: kontrol granular berdasarkan atribut pengguna/sumber daya/lingkungan; lebih fleksibel tetapi kompleks
- PBAC: mempertimbangkan waktu, lokasi, perangkat untuk keputusan akses; cocok untuk microservices/cloud
- Enkripsi: penting untuk data saat disimpan dan dikirim; manajemen kunci sangat kritis
- Audit trail: mencatat semua aktivitas pengguna; memungkinkan deteksi perilaku mencurigakan
- Faktor manusia: >80% pelanggaran disebabkan oleh kesalahan manusia; pelatihan dan kebijakan sangat penting
- Defense in depth: pendekatan berlapis yang menggabungkan berbagai mekanisme keamanan

---

### 6. `1976-Article Text-8897-1-10-20250723.pdf`

**Full Title:** Peningkatan Keamanan Sistem Informasi Berbasis Laravel 12 dengan Rate Limiting dan Role-Based Access Control (RBAC)

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Thomson Mary, Nia Febriyani |
| **Institution** | Universitas PGRI Sumatera Barat |
| **Journal** | JTEKSIS, Vol. 7 No. 3, Juli 2025 |
| **Pages** | 9 |
| **Tech Stack** | Laravel 12 + Spatie Permission + Rate Limiting |
| **Testing** | 8 aspek evaluasi (Inspeksi Kode, Best Practices, Keamanan, Performa, Operasi DB, Organisasi Kode, Error Handling, Manajemen File) |

#### 🇬🇧 English

**Summary:**  
Addresses hacking and redirection to online gambling sites at School XYZ website. Implements **Rate Limiting** (brute force prevention), **RBAC** (via Spatie Permission), and Laravel 12 security features. Average security score improved from **5.375 to 8.5625** (+3.19 points).

**Key Points:**
- 5-layer security approach: Rate Limiting, RBAC, Spatie Permission, Bcrypt hashing, CSRF protection
- Code Organization & Best Practices: +4.0 improvement
- Error Handling: +3.25 improvement
- Performance & DB Operations: +3.25 improvement
- User::all() replaced with pagination to prevent bottleneck
- DB::transaction() used for data integrity
- Laravel 12 receives 4-5 security updates per week from vendor

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Menangani masalah peretasan dan pengalihan ke situs judi online pada Website Sekolah XYZ. Mengimplementasikan **Rate Limiting** (pencegahan brute force), **RBAC** (melalui Spatie Permission), dan fitur keamanan Laravel 12. Skor keamanan rata-rata meningkat dari **5,375 menjadi 8,5625** (+3,19 poin).

**Poin Utama:**
- Pendekatan keamanan 5 lapis: Rate Limiting, RBAC, Spatie Permission, hashing Bcrypt, proteksi CSRF
- Organisasi Kode & Best Practices: peningkatan +4,0
- Error Handling: peningkatan +3,25
- Performa & Operasi DB: peningkatan +3,25
- User::all() diganti dengan pagination untuk mencegah bottleneck
- DB::transaction() digunakan untuk integritas data
- Laravel 12 menerima 4-5 pembaruan keamanan per minggu dari vendor

---

### 7. `5403-15846-1-PB.pdf`

**Full Title:** Implementasi Role-Based Access Control (RBAC) pada Sistem Informasi Manajemen Stok Obat

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Dea Agustina Purba, Nurmi Hidayasari |
| **Institution** | Politeknik Negeri Bengkalis |
| **Journal** | Sistemasi, Vol. 15, No. 2, 2026, Hal. 684-698 |
| **Pages** | 15 |
| **Development Method** | Waterfall |
| **Tech Stack** | Laravel 11 + MySQL + Spatie Permission |
| **Testing** | Black Box (23 skenario, 100% lolos), SUS (rata-rata 76, kategori Good) |

#### 🇬🇧 English

**Summary:**  
Replaces manual drug stock recording at **Apotek Pratama dr. Moris** with a web-based stock management system. Implements RBAC for 4 roles to prevent unauthorized access and improve data accuracy.

**Key Points:**
- 4 roles: Superadmin, Admin, Apoteker, Owner
- Features: drug/distributor management, stock in/out transactions, expired/low stock notifications, reporting
- Admin: manages drug data, distributor, stock-in transactions (cannot do stock-out)
- Apoteker: manages stock-out transactions (cannot do stock-in)
- SUS score: 76 (Good) - Superadmin 75, Admin 80, Apoteker 70, Owner 79
- RBAC validated at backend via `can` middleware - access denied even with direct URL access

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Mengganti pencatatan stok obat manual di **Apotek Pratama dr. Moris** dengan sistem manajemen stok berbasis web. Mengimplementasikan RBAC untuk 4 peran untuk mencegah akses tidak sah dan meningkatkan akurasi data.

**Poin Utama:**
- 4 peran: Superadmin, Admin, Apoteker, Owner
- Fitur: manajemen obat/distributor, transaksi obat masuk/keluar, notifikasi obat kedaluwarsa/stok menipis, pelaporan
- Admin: mengelola data obat, distributor, transaksi obat masuk (tidak bisa obat keluar)
- Apoteker: mengelola transaksi obat keluar (tidak bisa obat masuk)
- Skor SUS: 76 (Good) - Superadmin 75, Admin 80, Apoteker 70, Owner 79
- RBAC divalidasi di backend melalui middleware `can` - akses ditolak bahkan dengan akses URL langsung

---

### 8. `5958-16450-1-PB.pdf`

**Full Title:** Role-Based Access Control (RBAC) untuk Sistem Otorisasi Terpusat Berbasis Flask Studi Kasus PT. XYZ

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Yoga Agung Prasetia, Danny Manongga |
| **Institution** | Universitas Kristen Satya Wacana |
| **Journal** | JIPI, Vol. 9, No. 4, Desember 2024 |
| **Pages** | 11 |
| **Tech Stack** | Python Flask + PostgreSQL + PL/pgSQL |
| **Testing** | Test Case (5 skenario, semua lolos) |

#### 🇬🇧 English

**Summary:**  
Builds centralized authorization system for PT. XYZ (retail company) using RBAC model and **Python Flask Framework**. Maps access rights based on organizational positions (jabatan) rather than individual users.

**Key Points:**
- Architecture: Flask backend + PostgreSQL + JavaScript frontend
- Custom `@roles_required` decorator for route protection
- Session-based role storage after login
- PL/pgSQL function `get_menu(kode_jabatan)` returns JSON menu permissions
- Uses DAO (Data Access Object) pattern for database communication
- Access denied shows explicit "Jabatan anda tidak memiliki akses ke menu" message
- Limitation: UI not responsive on mobile devices

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Membangun sistem otorisasi terpusat untuk PT. XYZ (perusahaan ritel) menggunakan model RBAC dan **Python Flask Framework**. Memetakan hak akses berdasarkan jabatan dalam organisasi, bukan pengguna individu.

**Poin Utama:**
- Arsitektur: backend Flask + PostgreSQL + frontend JavaScript
- Decorator kustom `@roles_required` untuk proteksi route
- Penyimpanan peran berbasis sesi setelah login
- Fungsi PL/pgSQL `get_menu(kode_jabatan)` mengembalikan izin menu dalam format JSON
- Menggunakan pola DAO (Data Access Object) untuk komunikasi database
- Akses ditolak menampilkan pesan eksplisit "Jabatan anda tidak memiliki akses ke menu"
- Keterbatasan: UI tidak responsif di perangkat mobile

---

### 9. `7370-29745-1-PB.pdf`

**Full Title:** Implementasi Hak Akses untuk Meningkatkan Keamanan Manajemen Hotel ABC Berbasis Database MySQL

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Wahyu Nisfu Melati Sukma, Rikha Maisya Kotalima, Hisyam Abiansyah Gazani, Anindo Saka Fitri, Agung Brastama Putra |
| **Institution** | UPN "Veteran" Jawa Timur |
| **Conference** | SNESTIK V - Surabaya, 26 April 2025 |
| **Pages** | 8 |
| **Method** | Pendekatan eksperimental |
| **Database** | MySQL via CMD |

#### 🇬🇧 English

**Summary:**  
Implements MySQL-based access rights mechanism for Hotel ABC management system. Uses SQL GRANT/REVOKE commands through CMD terminal to manage access for manager, receptionist, and guest roles.

**Key Points:**
- 3 roles: Manajer (ALL PRIVILEGES), Resepsionis (SELECT/INSERT/UPDATE on specific tables), Tamu (manage own reservations only)
- Tables: login, reservasi, kamar, tamu, pembayaran
- Resepsionis cannot DELETE payment records - error shown on unauthorized access
- Guests can only see and manage their own reservations
- Limitation: not integrated with 2FA or complex audit logs

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Mengimplementasikan mekanisme hak akses berbasis MySQL untuk sistem manajemen Hotel ABC. Menggunakan perintah SQL GRANT/REVOKE melalui terminal CMD untuk mengelola akses peran manajer, resepsionis, dan tamu.

**Poin Utama:**
- 3 peran: Manajer (ALL PRIVILEGES), Resepsionis (SELECT/INSERT/UPDATE pada tabel tertentu), Tamu (hanya mengelola reservasi sendiri)
- Tabel: login, reservasi, kamar, tamu, pembayaran
- Resepsionis tidak bisa DELETE riwayat pembayaran - error muncul saat akses tidak sah
- Tamu hanya dapat melihat dan mengelola reservasi mereka sendiri
- Keterbatasan: belum terintegrasi dengan 2FA atau audit log yang kompleks

---

### 10. `87-+7226)+Rizal+Firmansyah,+Aulia+Hamdi,+Dini+Riandini+.pdf`

**Full Title:** Perancangan Sistem Autentikasi Multi-Role Berbasis RBAC pada Platform E-Learning Pemberdayaan Ekonomi Perempuan

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Rizal Firmansyah, Aulia Hamdi, Dini Riandini |
| **Institution** | Universitas Amikom Purwokerto |
| **Journal** | RABIT, Vol. 11 No. 1, Januari 2026 |
| **Pages** | 11 |
| **Development Method** | Waterfall |
| **Tech Stack** | ReactJS (frontend) + ExpressJS (backend) + PostgreSQL |
| **Testing** | Black Box (10 skenario, 100% valid) |

#### 🇬🇧 English

**Summary:**  
Builds multi-role authentication system for **UMI (Usaha Mandiri Ibu)** platform - an e-Learning system for empowering housewives' economic skills. Implements RBAC middleware to prevent privilege escalation between Peserta, Mentor, and Super Admin.

**Key Points:**
- 3 roles: Peserta (housewives/learners), Mentor (content providers/evaluators), Super Admin (system managers)
- JWT + role_id verification in ExpressJS middleware
- 403 Forbidden page for unauthorized access attempts (not just frontend menu hiding)
- Auto-registration for Super Admin and Mentor; Peserta must self-register with email verification
- audit_logs table records all login activities (timestamp, user_id, status)
- Mentor recorded as `mentor_id` in classes table; Peserta in enrollments table
- Limitation: Static RBAC (needs code changes for new roles); no 2FA yet

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Membangun sistem autentikasi multi-peran untuk platform **UMI (Usaha Mandiri Ibu)** - sistem e-Learning untuk memberdayakan keterampilan ekonomi ibu rumah tangga. Mengimplementasikan middleware RBAC untuk mencegah eskalasi hak akses antara Peserta, Mentor, dan Super Admin.

**Poin Utama:**
- 3 peran: Peserta (ibu rumah tangga/pembelajar), Mentor (penyedia materi/penilai), Super Admin (pengelola sistem)
- Verifikasi JWT + role_id di middleware ExpressJS
- Halaman 403 Forbidden untuk upaya akses tidak sah (bukan hanya menyembunyikan menu di frontend)
- Auto-registration untuk Super Admin dan Mentor; Peserta harus mendaftar sendiri dengan verifikasi email
- Tabel audit_logs mencatat semua aktivitas login (timestamp, user_id, status)
- Mentor tercatat sebagai `mentor_id` di tabel classes; Peserta di tabel enrollments
- Keterbatasan: RBAC statis (perlu perubahan kode untuk peran baru); belum ada 2FA

---

### 11. `9875-Article Text-25871-1-10-20251218.pdf`

**Full Title:** Implementasi Role-Based Access Control pada Sistem Informasi Layanan Administrasi pada Lembaga Bahasa UM Metro

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Maulana Firmansyah, Mustika, Pujianto |
| **Institution** | Universitas Muhammadiyah Metro |
| **Journal** | JMIK, Vol. 6 No. 2, Oktober 2025 |
| **Pages** | 10 |
| **Development Method** | RAD (Rapid Application Development) |
| **Tech Stack** | PHP + Laravel + MySQL |
| **Testing** | Black Box + Beta Testing |

#### 🇬🇧 English

**Summary:**  
Digitizes manual administrative services at Lembaga Bahasa UM Metro (serves 1,500+ students/semester). RBAC restricts access for 5 roles: Pendaftar, Staf Administrasi, Staf, Penerjemah, Kepala Lembaga. Features include online registration, payment proof upload, and automatic email notifications.

**Key Points:**
- 5 roles with distinct dashboards and workflows
- EPT (English Proficiency Test) registration and translation service management
- Staf creates test groups, inputs scores, assigns translators
- Email notifications for status updates
- Role access management page allows dynamic permission configuration
- 12 of 22 tables have relationships
- Successfully replaced Excel-based manual process

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Mendigitalisasi layanan administrasi manual di Lembaga Bahasa UM Metro (melayani 1.500+ mahasiswa/semester). RBAC membatasi akses untuk 5 peran: Pendaftar, Staf Administrasi, Staf, Penerjemah, Kepala Lembaga. Fitur mencakup pendaftaran online, unggah bukti bayar, dan notifikasi email otomatis.

**Poin Utama:**
- 5 peran dengan dashboard dan alur kerja yang berbeda
- Pendaftaran EPT (English Proficiency Test) dan manajemen layanan penerjemahan
- Staf membuat grup tes, menginput nilai, menugaskan penerjemah
- Notifikasi email untuk pembaruan status
- Halaman manajemen akses peran memungkinkan konfigurasi izin secara dinamis
- 12 dari 22 tabel memiliki relasi
- Berhasil menggantikan proses manual berbasis Excel

---

### 12. `Annisa+Hafsah+4997.pdf`

**Full Title:** Keamanan Data dalam Sistem Database

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | Annisa Hafsah, Aininta Alivia Br. Kaban, Said Luthfi Ramadhan, Nurbaiti |
| **Institution** | UIN Sumatera Utara |
| **Journal** | JINU, Vol.2, No.4, Juli 2025 |
| **Pages** | 15 |
| **Method** | Deskriptif kualitatif, studi literatur + studi kasus |

#### 🇬🇧 English

**Summary:**  
Analyzes effectiveness of data protection mechanisms in database management systems using MySQL and PostgreSQL simulations. Covers encryption, RBAC, and threat detection/response systems for confidentiality, integrity, and availability.

**Key Points:**
- Encryption transforms readable data into unreadable format; hybrid cryptography (public + private key) provides strongest protection
- RBAC vs traditional DAC/MAC: RBAC simplifies management by grouping users by position
- MySQL: popular RDBMS, client-server architecture, multi-user support
- PostgreSQL: ORDBMS, granular column-level access control, supports stored procedures/triggers
- PostgreSQL outperforms MySQL for very large record counts
- Organizational awareness crucial - training and strong authentication policies needed
- Weak passwords remain major vulnerability

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Menganalisis efektivitas mekanisme perlindungan data pada sistem manajemen basis data menggunakan simulasi MySQL dan PostgreSQL. Mencakup enkripsi, RBAC, dan sistem deteksi/respons ancaman untuk kerahasiaan, integritas, dan ketersediaan.

**Poin Utama:**
- Enkripsi mengubah data yang dapat dibaca menjadi format yang tidak dapat dibaca; kriptografi hibrida (kunci publik + privat) memberikan perlindungan terkuat
- RBAC vs DAC/MAC tradisional: RBAC menyederhanakan manajemen dengan mengelompokkan pengguna berdasarkan jabatan
- MySQL: RDBMS populer, arsitektur client-server, dukungan multi-user
- PostgreSQL: ORDBMS, kontrol akses granular tingkat kolom, mendukung stored procedure/trigger
- PostgreSQL mengungguli MySQL untuk jumlah record yang sangat besar
- Kesadaran organisasi sangat penting - pelatihan dan kebijakan autentikasi kuat diperlukan
- Password lemah tetap menjadi kerentanan utama

---

### 13. `Article+Text+0501-105-116.pdf`

**Full Title:** Analisis Implementasi Sistem Keamanan Basis Data Berbasis Role-Based Access Control (RBAC) pada Aplikasi Enterprise Resource Planning

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Authors** | M Sahyudi, Erliyan Redy Susanto |
| **Institution** | Universitas Teknokrat Indonesia |
| **Journal** | SATESI, Vol. 5 No. 1, 2025 |
| **Pages** | 12 |
| **Method** | Systematic Literature Review (SLR) dengan protokol PRISMA |
| **Data Sources** | IEEE Xplore, ACM, ScienceDirect, Scopus, Web of Science (2019-2024) |

#### 🇬🇧 English

**Summary:**  
SLR analyzing RBAC implementation in ERP, cloud, mobile, and multi-domain systems. Synthesizes 10 key articles to evaluate RBAC effectiveness for data privacy, regulatory compliance, and access policy complexity. **Final selected: 10 articles from 1,000+ initial.**

**Key Points:**
- AI/ML integration: decision tree and random forest for user behavior analysis; up to **37% security increase**
- Automation reduces operational costs by **42%** and management time by **65%** vs manual approaches
- 10 synthesized studies cover: backup/recovery security, trust-based RBAC, mobile cloud access control, semantic business roles, blockchain-based RBAC, OAuth 2.0 integration
- 3 critical novelty aspects: (1) quantitative effectiveness in cloud ERP, (2) AI integration factors, (3) adaptive framework for cross-regional regulations
- Practical recommendations for organizations of all scales (large enterprises, SMEs, startups)
- Compliance implications: GDPR, HIPAA, PCI DSS, FERPA, PDPA (Indonesia)

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
SLR yang menganalisis implementasi RBAC dalam sistem ERP, cloud, mobile, dan multi-domain. Mensintesis 10 artikel kunci untuk mengevaluasi efektivitas RBAC dalam privasi data, kepatuhan regulasi, dan kompleksitas kebijakan akses. **Terakhir dipilih: 10 artikel dari 1.000+ awal.**

**Poin Utama:**
- Integrasi AI/ML: decision tree dan random forest untuk analisis perilaku pengguna; peningkatan keamanan hingga **37%**
- Otomatisasi mengurangi biaya operasional sebesar **42%** dan waktu pengelolaan hingga **65%** dibanding pendekatan manual
- 10 studi yang disintesis mencakup: keamanan backup/recovery, RBAC berbasis kepercayaan, kontrol akses cloud mobile, peran bisnis semantik, RBAC berbasis blockchain, integrasi OAuth 2.0
- 3 aspek kebaruan kritis: (1) efektivitas kuantitatif dalam cloud ERP, (2) faktor integrasi AI, (3) framework adaptif untuk regulasi lintas regional
- Rekomendasi praktis untuk organisasi berbagai skala (perusahaan besar, UKM, startup)
- Implikasi kepatuhan: GDPR, HIPAA, PCI DSS, FERPA, PDPA (Indonesia)

---

### 14. `IGNITE+Vol+3+No+3+Juli+2025+hal+11-22.pdf`

**Full Title:** Analisis Keamanan Database dalam Menghadapi Ancaman Kebocoran Data di Perusahaan Teknologi Informasi

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Author** | Nisa Alifatuzzahra |
| **Institution** | UIN Sumatera Utara Medan |
| **Journal** | IGNITE, Vol. 3, No. 3, Juli 2025 |
| **Pages** | 12 |
| **Method** | Studi kasus kualitatif, SLR |

#### 🇬🇧 English

**Summary:**  
Analyzes database security mechanisms (encryption + access control) for preventing data breaches in IT companies. Covers external threats (SQL Injection, ransomware, DDoS, MITM) and internal factors (misconfiguration, weak passwords, employee negligence).

**Key Points:**
- Indonesia faced ~190 million cyber attack attempts (Jan-Aug 2020 per BSSN)
- External threats: SQL Injection, ransomware, MITM attacks, DDoS
- Internal threats: misconfiguration, improper access management, weak passwords, lack of training
- Solutions recommended: AES-256 encryption, RBAC, strict input validation, firewall, IDS/IPS, real-time monitoring
- Advanced approaches: Zero Trust Architecture (ZTA), SOAR, CTEM
- AI/ML for real-time behavior pattern analysis and anomaly detection
- Employee security training critical - human error major breach factor
- Regular backup and disaster recovery planning essential

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Menganalisis mekanisme keamanan database (enkripsi + kontrol akses) untuk mencegah kebocoran data di perusahaan TI. Mencakup ancaman eksternal (SQL Injection, ransomware, DDoS, MITM) dan faktor internal (kesalahan konfigurasi, password lemah, kelalaian karyawan).

**Poin Utama:**
- Indonesia menghadapi ~190 juta upaya serangan siber (Jan-Agu 2020 menurut BSSN)
- Ancaman eksternal: SQL Injection, ransomware, serangan MITM, DDoS
- Ancaman internal: kesalahan konfigurasi, manajemen akses yang tidak tepat, password lemah, kurangnya pelatihan
- Solusi yang direkomendasikan: enkripsi AES-256, RBAC, validasi input ketat, firewall, IDS/IPS, monitoring real-time
- Pendekatan lanjutan: Zero Trust Architecture (ZTA), SOAR, CTEM
- AI/ML untuk analisis pola perilaku dan deteksi anomali secara real-time
- Pelatihan keamanan karyawan sangat kritis - kesalahan manusia faktor utama kebocoran
- Backup rutin dan rencana pemulihan bencana sangat penting

---

### 15. `Jiforty-V6N2-4.pdf`

**Full Title:** Studi Perbandingan Model Keamanan Data pada Cloud Computing

| Attribute / Atribut | Details / Detail |
|-----------|---------|
| **Author** | Allan Desi Alexander |
| **Institution** | Universitas Bhayangkara Jakarta Raya |
| **Journal** | JIFORTY, Vol. 6, No. 2, Desember 2025 |
| **Pages** | 10 |
| **Method** | Systematic Literature Review (PRISMA) |
| **Data Sources** | Scopus, SINTA, IEEE Xplore, ScienceDirect, ACM, SpringerLink (2013-2025) |

#### 🇬🇧 English

**Summary:**  
Comprehensive analysis comparing data security models in cloud ecosystems: cryptography (AES, RSA, ECC), access control (RBAC vs ABAC), and risk management. **65-87 studies selected from 1,000+ initial.**

**Key Points:**
- **Encryption comparison:**
  - AES: superior speed, low CPU/memory - best for bulk data
  - RSA: high latency, memory-intensive - best for key management
  - ECC: equivalent security to RSA with smaller keys - better for resource-limited devices
  - DES: obsolete, vulnerable to brute force
- **RBAC vs ABAC:**
  - RBAC: static role-based; risk of "role explosion"; single-layer security
  - ABAC: dynamic attribute-based (subject, object, context); fine-grained; multi-layer; avg 194.89ms evaluation latency
  - RBAC + ML: 37% security improvement, 42% cost reduction
- Cloud threats: data breach, DDoS, insecure APIs, insider threats, loss of governance
- Emerging tech: blockchain (immutable audit logs), ML/DL (anomaly detection), Federated Learning (privacy-preserving AI training)
- Hybrid cryptography recommended: AES for data + RSA/ECC for key exchange
- Post-quantum cryptography (PQC) needed for future resilience

#### 🇮🇩 Bahasa Indonesia

**Ringkasan:**  
Analisis komprehensif yang membandingkan model keamanan data dalam ekosistem cloud: kriptografi (AES, RSA, ECC), kontrol akses (RBAC vs ABAC), dan manajemen risiko. **65-87 studi dipilih dari 1.000+ awal.**

**Poin Utama:**
- **Perbandingan enkripsi:**
  - AES: kecepatan unggul, CPU/memori rendah - terbaik untuk data massal
  - RSA: latensi tinggi, intensif memori - terbaik untuk manajemen kunci
  - ECC: keamanan setara RSA dengan kunci lebih kecil - lebih baik untuk perangkat dengan sumber daya terbatas
  - DES: usang, rentan terhadap brute force
- **RBAC vs ABAC:**
  - RBAC: berbasis peran statis; risiko "role explosion"; keamanan satu lapis
  - ABAC: berbasis atribut dinamis (subjek, objek, konteks); granular; multi-lapis; latensi evaluasi rata-rata 194,89ms
  - RBAC + ML: peningkatan keamanan 37%, pengurangan biaya 42%
- Ancaman cloud: kebocoran data, DDoS, API tidak aman, ancaman internal, hilangnya tata kelola
- Teknologi mutakhir: blockchain (audit log yang tidak dapat diubah), ML/DL (deteksi anomali), Federated Learning (pelatihan AI yang menjaga privasi)
- Kriptografi hibrida direkomendasikan: AES untuk data + RSA/ECC untuk pertukaran kunci
- Kriptografi pasca-kuantum (PQC) diperlukan untuk ketahanan masa depan

---

## Common Themes Across Papers / Tema Umum di Seluruh Paper

| Theme / Tema | Frequency | Details / Detail |
|-------|-----------|---------|
| **RBAC Implementation** | 15/15 | Semua paper membahas RBAC dalam konteks tertentu |
| **Laravel Framework** | 6/15 | Paper #1, #4, #6, #7, #11 menggunakan Laravel |
| **MySQL Database** | 5/15 | Paper #2, #7, #9, #11, #12 |
| **PostgreSQL Database** | 5/15 | Paper #2, #3, #8, #10, #12 |
| **Waterfall Method** | 4/15 | Paper #1, #7, #10 |
| **Black Box Testing** | 7/15 | Pendekatan pengujian paling umum |
| **Spatie Permission** | 4/15 | Paket RBAC populer untuk Laravel |
| **Encryption** | 5/15 | Paper #2, #5, #12, #14, #15 |
| **Multi-tenant / Cloud** | 4/15 | Paper #1, #5, #13, #15 |
| **Separation of Duty** | 2/15 | Paper #4, #13 |

---

## Technology Stack Summary / Ringkasan Stack Teknologi

| Technology / Teknologi | Papers Using It |
|------------|-----------------|
| Laravel (PHP) | #1, #4, #6, #7, #11 |
| MySQL | #2, #7, #9, #11, #12 |
| PostgreSQL | #2, #3, #8, #10, #12 |
| Spatie Permission | #1, #4, #6, #7 |
| Filament Shield | #1 |
| Python Flask | #8 |
| ReactJS + ExpressJS | #10 |
| pgAdmin 4 / DBeaver | #3 |

---

## Key Metrics Across Papers / Metrik Utama di Seluruh Paper

| Paper | Testing Method | Pass Rate | Notable Metric |
|-------|---------------|-----------|----------------|
| #1 | Black Box (8 skenario) | 100% | Isolasi 23 kantor |
| #4 | White Box (67 kasus) + Black Box (37 kasus) | 100% | 95,25% coverage; 72,73%→0% tingkat kolusi |
| #6 | Evaluasi 8 aspek | N/A | Skor 5,375→8,5625 (+3,19) |
| #7 | Black Box (23 skenario) + SUS | 100% | SUS rata-rata 76 (Good) |
| #10 | Black Box (10 skenario) | 100% | Eskalasi hak akses dicegah |
| #13 | SLR (10 artikel dari 1000+) | N/A | 37% peningkatan keamanan; 42% pengurangan biaya |
| #15 | SLR (65-87 studi dari 1000+) | N/A | AES tercepat; ABAC latensi 194,89ms |

---

*End of summary / Akhir ringkasan. Last updated / Terakhir diperbarui: April 12, 2026.*
