# Materi Minggu 4: Ekonomi Private Cloud dan Capital Expenditure

**AI yang digunakan:** Claude Opus 5.5 (Anthropic)

**Prompt:**

> **Peran:** Kamu adalah asisten akademik untuk mata kuliah Business Cloud Design.
>
> **Konteks:** Saya mahasiswa Sistem Informasi semester 7. Terlampir materi Pertemuan 4 berjudul "Ekonomi Private Cloud dan Capital Expenditure" (file `04--business-cloud-design.pdf`).
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

## Capaian Pembelajaran

1. Menjelaskan karakteristik private cloud dan model biayanya.
2. Membedakan CAPEX, OPEX, biaya langsung, dan biaya tidak langsung.
3. Mengidentifikasi komponen *Total Cost of Ownership* (TCO) private cloud.
4. Membandingkan skenario private dan public cloud secara terstruktur.
5. Menyusun rekomendasi awal berbasis biaya, risiko, dan kebutuhan bisnis.

**Pemantik:** server sendiri (private cloud) atau public cloud, mana yang lebih murah? Jawabannya **tergantung** pola beban, risiko, dan timeline.

## 1. Fondasi: Terminologi

| Istilah | Arti |
|---|---|
| **Private cloud** | Lingkungan cloud khusus satu organisasi; bisa dikelola sendiri atau pihak ketiga |
| **On-premises** | Infrastruktur berada di lokasi organisasi; tidak otomatis berarti private cloud |
| **Virtualisasi** | Teknologi abstraksi server; virtualisasi saja belum menjadikan layanan sebagai cloud |
| **CAPEX** | *Capital Expenditure*, pengeluaran untuk memperoleh atau meningkatkan aset jangka panjang |
| **OPEX** | *Operational Expenditure*, biaya operasional yang timbul saat layanan dijalankan |

### Definisi Operasional Private Cloud

- Digunakan secara **eksklusif** oleh satu organisasi; resource bisa berada di data center sendiri, colocation, atau fasilitas provider.
- Karakteristik cloud tetap berlaku: self-service, resource pooling, elasticity, layanan terukur.
- Eksklusif tidak berarti seluruh komponen dimiliki organisasi.
- **Model pengelolaan:** self-managed, managed private cloud, atau kombinasi.

### Pilihan Arsitektur dan Konsekuensi Ekonominya

| Private on-premises | Hosted private cloud | Public cloud | Hybrid |
|---|---|---|---|
| Aset dan kontrol lebih besar; CAPEX tinggi; operasi ditanggung organisasi | Fasilitas pihak ketiga; biaya hosting/kontrak; tanggung jawab dibagi | Multi-tenant; biaya berbasis konsumsi; elastis dan cepat | Kombinasi; integrasi menambah biaya; fleksibel per workload |

**Tidak ada model yang selalu paling murah.** Bandingkan workload dan layanan yang setara.

## 2. Ekonomi Cloud

### Pendorong Ekonomi Private Cloud

- **Utilisasi:** berapa banyak kapasitas yang benar-benar terpakai?
- **Skala:** berapa banyak workload dan pengguna yang dilayani?
- **Umur aset:** berapa lama server dan storage tetap produktif?
- **SDM:** berapa biaya tim platform, keamanan, dan operasi?
- **Risiko:** downtime, pemulihan, kepatuhan, keamanan.
- **Kecepatan:** seberapa cepat layanan baru bisa diluncurkan?

### Peta Biaya Private Cloud

| Investasi awal | Operasi berulang | Biaya tersembunyi |
|---|---|---|
| Server dan akselerator | Listrik dan fasilitas | Waktu staf internal |
| Storage dan jaringan | Support dan maintenance | Pelatihan dan sertifikasi |
| Rack, power, pendinginan | Lisensi berlangganan | Kapasitas idle |
| Lisensi awal dan implementasi | Backup dan disaster recovery | Downtime dan pemulihan |
| Migrasi dan integrasi | Monitoring dan keamanan | Biaya keluar saat migrasi |

### Total Cost of Ownership (TCO)

> **TCO** = seluruh biaya untuk **memperoleh, menjalankan, melindungi, dan menghentikan** layanan.

- **Akuisisi:** hardware, software, setup.
- **Operasi:** SDM, listrik, support selama masa pakai.
- **Risiko dan akhir:** downtime, refresh, disposal.

Saat membandingkan alternatif, gunakan **timeline yang sama** (misalnya 3 atau 5 tahun), kapasitas yang sama, dan tingkat layanan yang sama.

### Unit Economics

| Metrik | Rumus |
|---|---|
| Biaya per VM-bulan | TCO periode ÷ total VM-bulan yang disediakan |
| Biaya per pengguna | TCO periode ÷ jumlah pengguna aktif |
| Biaya per transaksi | TCO periode ÷ volume transaksi relevan |

Metrik unit perlu disertai konteks: performa, availability, keamanan, dan pola pemakaian.

### Utilisasi

- Kapasitas yang dibeli **tidak sama** dengan kapasitas yang produktif.
- **Utilisasi rendah:** biaya tetap tersebar ke sedikit workload, sehingga biaya per unit naik.
- **Utilisasi sehat:** konsolidasi workload, tetapi tetap sisakan *headroom* untuk lonjakan dan kegagalan.
- Jangan mengejar utilisasi 100% jika mengorbankan kinerja dan ketahanan.

## 3. Investasi: CAPEX dan OPEX

### CAPEX

- Pengeluaran untuk aset yang memberi manfaat **lebih dari satu periode**, misalnya server, storage, jaringan, fasilitas, dan implementasi.
- **Dampak finansial:** arus kas keluar di awal; aset disusutkan sepanjang umur manfaat.
- **Pertanyaan desain:** apakah kapasitas akan dipakai cukup lama dan cukup tinggi untuk membenarkan investasi?

### OPEX dan Model Konsumsi

- **OPEX rutin:** daya, pendinginan, kontrak support, lisensi berulang, staf operasi.
- **Cloud consumption:** biaya mengikuti penggunaan, reservasi, kapasitas, atau kombinasinya.
- OPEX **tidak selalu murah**. Konsumsi tanpa kontrol bisa tumbuh cepat.

### Cara Berpikir CAPEX vs OPEX

| Dimensi | Private cloud (investasi aset) | Public cloud (konsumsi) |
|---|---|---|
| Arus kas | Besar di awal | Tersebar, mengikuti konsumsi |
| Kapasitas | Dibeli sebelum digunakan | Dapat ditambah/dikurangi |
| Risiko utilisasi | Ditanggung organisasi | Sebagian dialihkan ke provider |
| Kontrol | Fisik/konfigurasi lebih besar | Bergantung layanan dan kontrak |
| Tantangan | Overprovisioning, refresh, aset idle | *Bill shock*, lock-in, biaya berulang |

### Depresiasi dan Arus Kas

**Contoh:** aset server dan storage senilai Rp600 juta dengan umur manfaat 5 tahun (nilai residu diabaikan).

Depresiasi garis lurus = Rp600 juta ÷ 5 = **Rp120 juta/tahun**

Depresiasi adalah **alokasi biaya aset dalam laporan keuangan**, bukan pembayaran kas tahunan yang baru. Kas umumnya keluar saat aset dibeli.

### Kerangka Keputusan Investasi

1. **Kebutuhan:** workload, SLA, keamanan, regulasi.
2. **Kapasitas:** baseline, puncak, pertumbuhan, headroom.
3. **Biaya:** TCO, cash flow, unit economics.
4. **Risiko:** availability, skill, vendor, lock-in.
5. **Opsi:** build, buy, host, hybrid.
6. **Ukur ulang:** FinOps, utilisasi, biaya aktual.

**FinOps** (*Financial Operations*): kerangka kerja dan budaya yang menyatukan tim teknik, keuangan, dan bisnis untuk mengelola pengeluaran cloud bersama-sama.

## 4. Studi Kasus: Private Cloud untuk Kampus

**Kebutuhan:**
- 120 VM ekuivalen.
- Storage 80 TB.
- Availability 99,9%.
- Horizon analisis 5 tahun.

| | Private cloud | Public cloud |
|---|---|---|
| Biaya awal | CAPEX Rp1,2 M (termasuk implementasi) | Migrasi Rp0,1 M |
| Biaya tahunan | OPEX Rp0,3 M | Rp0,52 M (compute, storage, support) |
| **Total 5 tahun** | 1,2 + (0,3 × 5) = **Rp2,7 M** | 0,1 + (0,52 × 5) = **Rp2,7 M** |

Hasilnya **sama**. Artinya keputusan tidak bisa hanya berdasarkan total rupiah. Perhitungan di atas belum memasukkan diskonto, pajak, refresh hardware, nilai residu, biaya SDM, dan risiko. Perlu juga dicek apakah performa, SLA, backup, dan keamanannya benar-benar setara.

### Analisis Sensitivitas

- **Utilisasi turun:** kapasitas private idle, sehingga biaya per workload naik.
- **Kebutuhan tumbuh:** private mungkin perlu investasi tambahan, sementara public lebih elastis.
- **Harga cloud berubah:** diskon, kurs, *egress* (biaya data keluar dari cloud), dan pola konsumsi mengubah total biaya.
- Minimal uji skenario **rendah, dasar, dan tinggi**.

### Risiko Ekonomi yang Sering Terlewat

- **Technical debt:** perangkat lama dan integrasi khusus.
- **Skill dan staffing:** ketergantungan pada personel kunci.
- **Resilience:** biaya redundansi, backup, DR, dan pengujian.
- **Vendor lock-in:** biaya pindah, format data, kontrak.
- **Governance:** kapasitas tak terpakai, *shadow IT*, tagihan tanpa pemilik.

## Key Takeaways

- Private cloud adalah **keputusan layanan dan operasi**, bukan sekadar membeli server.
- TCO harus mencakup biaya langsung, tidak langsung, risiko, dan akhir masa pakai.
- CAPEX dan OPEX menjelaskan **pola pengeluaran**, bukan otomatis murah atau mahal.
- Perbandingan yang adil memerlukan workload, horizon, kapasitas, dan SLA yang sebanding.
- Setelah implementasi, ukur biaya aktual dengan metrik dan governance yang jelas (FinOps).

## Referensi (dari materi)

- NIST SP 800-145, *The NIST Definition of Cloud Computing* (2011).
- FinOps Foundation, *FinOps Framework*.
- AWS Well-Architected Framework – Cost Optimization Pillar.
- Microsoft Azure Cloud Adoption Framework – Cloud Economics.
