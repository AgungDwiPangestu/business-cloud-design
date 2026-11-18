# Materi Minggu 3: Private Cloud dan IT Alignment

**AI yang digunakan:** Claude Opus 5.5 (Anthropic)

**Prompt:**

> **Peran:** Kamu adalah asisten akademik untuk mata kuliah Business Cloud Design.
>
> **Konteks:** Saya mahasiswa Sistem Informasi semester 7. Terlampir materi Pertemuan 3 berjudul "Private Cloud dan IT Alignment" (file `03--private-cloud--IT-alignment.pdf`).
>
> **Tugas:** Buat rangkuman materi sesuai agenda pembahasan pertemuan ini.
>
> **Ketentuan:**
> 1. Gunakan Bahasa Indonesia akademik yang jelas dan ringkas.
> 2. Susun mengikuti urutan agenda pembahasan pada materi.
> 3. Jelaskan setiap konsep utama beserta definisi singkat dan contoh penerapannya dalam konteks bisnis.
> 4. Istilah teknis tetap dalam bahasa Inggris, disertai penjelasan singkat.
> 5. Akhiri dengan poin-poin kesimpulan (key takeaways).
> 6. Hanya gunakan informasi dari materi yang diberikan; jangan menambah klaim di luar materi tanpa menandainya.
>
> **Format keluaran:** Markdown dengan heading (`##`, `###`), bullet list, dan tabel bila perlu.

**Bagian yang disesuaikan dari keluaran prompt ada pada:** _[TODO: isi dengan bagian yang kamu edit]_

---

## Tujuan Pembelajaran

1. **Memahami:** menjelaskan private cloud serta perbedaannya dengan virtualisasi dan public cloud.
2. **Menganalisis:** menghubungkan sasaran bisnis, strategi TI, dan keputusan desain private cloud.
3. **Merancang:** menyusun prinsip arsitektur, tata kelola, KPI, dan roadmap implementasi.

> **Gagasan utama:** keberhasilan teknologi diukur dari **hasil bisnis**, bukan kecanggihan teknis.

## Bagian 1 – Private Cloud dalam Konteks Organisasi

### Apa itu Private Cloud?

- Model cloud yang menyediakan lingkungan komputasi untuk **satu organisasi**, dengan kontrol dan kebijakan yang ditetapkan organisasi tersebut.
- Bisa berada di data center sendiri atau dikelola pihak ketiga; lokasi fisik bukan satu-satunya penentu.
- Menggabungkan *resource pool*, otomasi, *self-service* terkontrol, pengukuran penggunaan, dan pengelolaan layanan.
- Bukan sekadar satu server, satu hypervisor, atau kumpulan VM.
- **Definisi praktis:** layanan infrastruktur yang dapat diminta, disediakan, diamankan, dan dipantau melalui mekanisme standar.

### Virtualisasi ≠ Private Cloud

| Virtualisasi | Private cloud |
|---|---|
| Abstraksi hardware agar beberapa VM berjalan di host yang sama | Lapisan layanan: katalog, otomasi, kontrol akses, kebijakan, monitoring, showback/chargeback |
| Fokus: efisiensi dan isolasi workload | Memerlukan proses operasi, pemilik layanan, dan tata kelola |

Virtualisasi dapat menjadi fondasi, tetapi belum otomatis menjadi cloud.

- **Showback:** biaya hanya ditunjukkan ke unit bisnis, tidak ditagihkan.
- **Chargeback:** biaya ditunjukkan dan benar-benar ditagihkan.

Keduanya bertujuan membangun *awareness* biaya dan mendorong perubahan perilaku.

### Private vs Public vs Hybrid

| Private | Public | Hybrid |
|---|---|---|
| Kontrol dan kustomisasi tinggi; organisasi menanggung kapasitas, operasi, dan keamanan | Kapasitas elastis dan layanan luas; perlu disiplin biaya, identitas, jaringan, dan vendor management | Memadukan lingkungan; butuh identitas, konektivitas, klasifikasi data, observability, dan governance lintas lingkungan |

### Kapan Private Cloud Layak Dipertimbangkan?

- Butuh kontrol atas data, konfigurasi, lokasi, atau ada persyaratan regulasi tertentu.
- Workload relatif stabil sehingga kapasitas bisa direncanakan.
- Ada kebutuhan platform bersama untuk banyak tim atau unit bisnis.
- Organisasi punya (atau mau membangun) kemampuan operasi, keamanan, otomasi, dan dukungan.
- Ada *business case* yang mempertimbangkan TCO, risiko, dan nilai layanan.

Private cloud **tidak otomatis paling tepat**. Kebutuhan yang sangat fluktuatif atau tim operasi yang belum siap dapat mengubah perhitungan.

## Bagian 2 – IT Alignment: dari Strategi ke Layanan

### Apa itu IT Alignment?

- Keselarasan strategi dan sasaran bisnis dengan strategi, portofolio, proses, arsitektur, dan investasi TI.
- Berlangsung **dua arah**: bisnis menjelaskan hasil yang dibutuhkan dan batasan risikonya, sedangkan TI menjelaskan pilihan, konsekuensi, dan kapabilitas yang diperlukan.
- Dijaga sepanjang siklus: perencanaan → desain → implementasi → operasi → evaluasi → perbaikan.
- **Uji sederhana:** dapatkah setiap keputusan desain dijelaskan kaitannya dengan hasil bisnis atau pengurangan risiko?

### Rantai Alignment

**Strategi bisnis → Kapabilitas → Arsitektur → Ukuran hasil**

Contoh:
1. **Strategi:** mempercepat peluncuran produk digital.
2. **Kapabilitas:** lingkungan pengembangan cepat dan keamanan data.
3. **Arsitektur:** katalog VM/container, jaringan tersegmentasi, backup, otomasi provisioning.
4. **Ukuran hasil:** waktu provisioning, availability, lead time rilis, biaya per layanan.

### Sasaran Bisnis dan Keputusan Cloud

| Sasaran | Keputusan desain |
|---|---|
| **Cepat** | Otomasi provisioning, self-service dengan approval sesuai risiko |
| **Andal** | SLO, redundansi, backup teruji, pemantauan, prosedur pemulihan |
| **Aman** | Klasifikasi data, *least privilege*, segmentasi, patching, logging, audit |
| **Efisien** | Utilisasi, biaya layanan, lifecycle VM, capacity planning, right-sizing |

- **SLO** (*Service Level Objective*): target kinerja terukur yang menentukan tingkat keandalan layanan.
- **Principle of Least Privilege:** pengguna atau sistem hanya diberi hak akses minimum yang benar-benar dibutuhkan.

### Peran dan Tanggung Jawab

| Peran | Tanggung jawab |
|---|---|
| Pimpinan bisnis | Menetapkan sasaran, prioritas, toleransi risiko, hasil yang diharapkan |
| CIO / IT leadership | Menyelaraskan strategi TI, investasi, arsitektur, kapabilitas |
| Platform team | Membangun platform, otomasi, kapasitas, reliability, dokumentasi |
| Security / finance | Menetapkan kontrol, menguji kepatuhan, mengevaluasi biaya dan risiko |

### Governance (Tata Kelola)

Pertanyaan yang harus punya jawaban jelas:
- Siapa yang boleh meminta layanan, dan siapa yang menyetujui permintaan berisiko tinggi?
- Workload dan data apa yang boleh ditempatkan di private cloud?
- Standar apa yang wajib dipenuhi (image, patch, backup, logging, jaringan, identitas)?
- Bagaimana kapasitas, biaya, dan pengecualian kebijakan ditinjau?
- Bagaimana perubahan, insiden, pemulihan, dan penghentian layanan dikelola?

Governance yang baik membuat **guardrail** jelas tanpa mengubah setiap permintaan menjadi birokrasi.

## Bagian 3 – Menerjemahkan Alignment ke Desain

### Arsitektur Logis

| Lapisan | Isi |
|---|---|
| **Layanan** | Katalog, portal/request, image VM, API, alur approval |
| **Kontrol** | Identitas/RBAC, kebijakan, inventory, kuota, audit trail |
| **Sumber daya** | Compute, storage, jaringan, hypervisor, backup, kapasitas cadangan |
| **Operasi** | Monitoring, logging, patching, incident/change management, uji restore |

**RBAC** (*Role-Based Access Control*): hak akses diberikan berdasarkan peran pekerjaan, bukan diatur manual per individu.

### Alur dari Strategi ke Platform

**Sasaran organisasi** (pertumbuhan, kualitas, efisiensi, kepatuhan) → **Kapabilitas** (agility, availability, security, cost transparency) → **Desain private cloud** (katalog, compute/storage/network, IAM, automation, backup) → **Operasi dan KPI** (SLO/SLA, provisioning time, utilization, restore test, cost per service).

Ada **loop umpan balik**: KPI dan pengalaman pengguna dipakai untuk memperbaiki strategi, layanan, dan kapasitas.

### Prinsip Desain

1. **Product thinking:** platform diperlakukan sebagai produk internal yang punya pengguna, katalog, roadmap, dan dukungan.
2. **Standardisasi:** sediakan jalur standar yang aman. Setiap pengecualian harus punya alasan, pemilik, dan masa berlaku.
3. **Automation first:** otomasi pekerjaan berulang yang rawan kesalahan, setelah prosesnya jelas.
4. **Security and resilience by design:** keamanan, backup, pemulihan, dan observability dibangun sejak awal.
5. **Measure outcomes:** ukur hasil layanan, bukan sekadar jumlah host atau VM.

### KPI: Jangan Hanya Mengukur Uptime

| Kecepatan | Keandalan | Efisiensi | Pengalaman & kontrol |
|---|---|---|---|
| Waktu request sampai VM siap; lead time perubahan | Availability, jumlah insiden, MTTR, keberhasilan backup, hasil uji restore | Utilisasi, biaya per workload, kapasitas menganggur | Kepuasan pengguna, baseline compliance, patch compliance, temuan audit |

- **MTTR** (*Mean Time to Repair*): rata-rata waktu untuk memperbaiki sistem yang bermasalah.
- **Baseline compliance:** standar minimum konfigurasi keamanan dan kebijakan yang wajib dipenuhi seluruh infrastruktur.

Setiap KPI perlu definisi, baseline, target, sumber data, pemilik, dan frekuensi review.

### TCO dan Business Case

- **Biaya investasi:** server, storage, jaringan, lisensi, ruang, daya, pendinginan.
- **Biaya operasi:** staf, dukungan vendor, patching, monitoring, backup, keamanan, refresh.
- **Biaya risiko:** downtime, kehilangan data, ketergantungan pada personel kunci.
- **Manfaat:** provisioning cepat, standardisasi, kontrol, utilisasi lebih tinggi.
- Bandingkan alternatif setara (private, public, managed service, hybrid) dengan **horizon dan asumsi yang sama**. Jangan membandingkan biaya server saja dengan tagihan cloud.

### Roadmap Implementasi

1. **Discover:** petakan strategi, stakeholder, aplikasi, data, risiko, KPI baseline, dan biaya saat ini.
2. **Design:** pilih workload awal, target layanan, arsitektur, guardrail, SLO, dan operating model.
3. **Pilot:** uji workload representatif, provisioning, keamanan, backup-restore, dan pengalaman pengguna.
4. **Scale:** perluas katalog, otomasi, showback, capacity planning, review KPI, dan perbaikan.

**Guardrail:** kebijakan dan batasan otomatis untuk mencegah tindakan berbahaya atau pelanggaran kepatuhan.

## Studi Kasus: Universitas dengan Layanan Digital

- **Tujuan:** mempercepat penyediaan lingkungan praktikum, menjaga data akademik, dan mengendalikan biaya.
- **Kondisi awal:** server terpisah per lab, permintaan VM manual, dan backup belum pernah diuji restore.
- **Batasan:** tim TI kecil, anggaran terbatas, lonjakan di awal semester, dan data sensitif.

**Contoh solusi (target ilustratif):**
- **Sasaran:** lingkungan praktikum siap ≤15 menit; 95% permintaan standar berjalan tanpa intervensi manual.
- **Kapabilitas:** katalog VM/container, kuota per mata kuliah, provisioning otomatis, segmentasi, *expiry policy*.
- **Kendali:** RBAC, image terpelihara, pemisahan data akademik, uji backup berkala.
- **KPI:** waktu provisioning, kegagalan permintaan, utilisasi host, keberhasilan restore test, biaya per image.
- **Risiko:** lonjakan awal semester dan VM terlantar. Mitigasinya capacity planning, kuota, expiry, dan alert.

## Risiko Alignment yang Sering Terjadi

| Risiko | Penjelasan |
|---|---|
| **Technology-first** | Platform dibeli sebelum kebutuhan dan hasil bisnis disepakati |
| **Ownership kabur** | Tidak jelas pemilik layanan, data, biaya, dan risiko |
| **Cloud-washing** | Virtualisasi diklaim sebagai cloud tanpa self-service, otomasi, atau governance |
| **Metrics theater** | Uptime dan kapasitas dilaporkan tanpa kaitan dengan dampak layanan |

## Key Takeaways

- **Private cloud** adalah kapabilitas layanan terkelola, bukan hanya hardware atau hypervisor.
- **IT alignment** menjaga strategi, investasi, arsitektur, operasi, dan hasil bisnis tetap terhubung, dan berlangsung dua arah.
- Keberhasilan diukur dari layanan yang berguna, aman, andal, terukur, dan terus diperbaiki.
- Mulailah dari masalah dan hasil bisnis, lalu pilih teknologi sebagai sarana untuk mencapainya.
