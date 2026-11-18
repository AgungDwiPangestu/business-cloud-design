# Materi Minggu 5: Metode Kuantitatif Ekonomi Infrastruktur untuk Deployment Cloud

**AI yang digunakan:** Claude Opus 5.5 (Anthropic)

**Prompt:**

> **Peran:** Kamu adalah asisten akademik untuk mata kuliah Business Cloud Design.
>
> **Konteks:** Saya mahasiswa Sistem Informasi semester 7. Terlampir materi Pertemuan 5 berjudul "Metode Kuantitatif Ekonomi Infrastruktur untuk Deployment Cloud" (file `05--business-cloud-design.pdf`).
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

1. Menjelaskan pentingnya analisis kuantitatif ekonomi infrastruktur untuk deployment cloud.
2. Mengidentifikasi biaya langsung, tidak langsung, transisi, dan risiko.
3. Menghitung TCO, ROI sederhana, dan payback period serta memahami batasannya.
4. Membandingkan private dan public cloud berdasarkan asumsi yang setara.
5. Menyusun rekomendasi dengan analisis sensitivitas dan faktor nonfinansial.

## 1. Konteks Keputusan dan Tujuan Analisis

- Infrastruktur adalah keputusan **investasi** sekaligus keputusan **operasional**.
- **Biaya terlihat:** server, storage, jaringan, lisensi, listrik, layanan cloud.
- **Biaya tersembunyi:** tenaga ahli, downtime, migrasi, keamanan, pelatihan, biaya ke vendor.
- Tujuannya bukan otomatis memilih biaya terendah, tetapi **nilai bisnis terbaik** dengan batasan yang jelas.
- **Pertanyaan kunci:** berapa biaya totalnya, apa manfaatnya, dan kapan manfaat itu menutup investasi?

## 2. Metode Kuantitatif dan Komponen Biaya

### Metode

| Metode | Fungsi |
|---|---|
| **Cost-benefit analysis** | Membandingkan CAPEX, OPEX, dan total biaya pada horizon yang sama |
| **TCO** | Biaya memperoleh, mengoperasikan, dan mengakhiri solusi |
| **ROI** | Manfaat bersih relatif terhadap biaya |
| **Payback period** | Waktu sampai manfaat kumulatif menutup investasi awal |
| **NPV** | Nilai kini arus kas bersih (memperhitungkan nilai waktu uang) |
| **Analisis sensitivitas** | Menguji dampak perubahan asumsi utama |

### Peta Komponen Biaya

- **CAPEX:** server, storage, jaringan, rak, UPS, fasilitas, implementasi.
- **OPEX:** listrik, pendinginan, konektivitas, cloud usage, dukungan, lisensi, backup, monitoring.
- **People cost:** sysadmin, keamanan, database, SRE, platform engineering, pelatihan, on-call.
- **Transition cost:** assessment, migrasi, pengujian, *parallel run*, perubahan proses.
- **Risk cost:** downtime, kehilangan data, insiden keamanan, over-provisioning, ketidakpastian harga.
- **Exit cost:** pemindahan data, penghapusan aman, terminasi kontrak, dan **egress**, yaitu biaya data keluar dari cloud (unduh file, respons API, sinkronisasi ke server lokal) yang sering dikenakan per GB.

### Langkah Membuat Model Ekonomi

1. Tetapkan ruang lingkup: workload, SLA, lokasi, kapasitas, keamanan, periode.
2. Tetapkan baseline setara: kapasitas, performa, availability, backup, pertumbuhan.
3. Pisahkan biaya satu kali dan berulang; tetapkan pemilik tiap asumsi.
4. Proyeksikan biaya per tahun, bukan satu angka bulanan.
5. Hitung TCO dan manfaat tanpa menghitung manfaat yang sama dua kali.
6. Uji skenario rendah, dasar, dan tinggi; dokumentasikan sumber dan tingkat keyakinannya.

### Rumus TCO

> **TCO = biaya awal + biaya operasional + biaya transisi + biaya risiko/keluar**

Aturan perbandingan:
- Horizon waktu sama.
- Cakupan layanan sama.
- Asumsi pertumbuhan dan utilisasi dinyatakan.
- Biaya pasti dipisahkan dari estimasi risiko.

### ROI, Payback, dan NPV

- **ROI sederhana (%)** = (manfaat finansial total − biaya total) ÷ biaya total × 100%. Mudah dikomunikasikan, tetapi tidak menunjukkan **kapan** arus kas terjadi.
- **Payback period:** waktu yang dibutuhkan agar investasi awal kembali melalui arus kas bersih.
- **NPV** (*Net Present Value*): selisih nilai sekarang arus kas masuk dan keluar. Metode ini memperhitungkan *time value of money* (uang hari ini lebih bernilai daripada jumlah yang sama di masa depan), sehingga lebih baik untuk membandingkan arus kas pada waktu berbeda.
- Pastikan definisi biaya konsisten: TCO penuh atau hanya investasi awal?

## 3. Simulasi TCO dan ROI (Horizon 3 Tahun)

Kasus: organisasi menjalankan ERP, portal pelanggan, dan analitik internal. Manfaat terukur sebesar **Rp1,2 miliar/tahun**, berasal dari pengurangan downtime, otomasi, dan percepatan proses.

> Manfaat harus divalidasi pemilik proses. Penghematan waktu tidak otomatis sama dengan penghematan kas.

### Input Biaya (Rp juta)

| Komponen | Private | Public |
|---|---|---|
| Investasi awal | 1.200 | 100 |
| Operasi infrastruktur/tahun | 300 | 480 |
| Tenaga ahli/tahun | 250 | 150 |
| Migrasi dan transisi (sekali) | 150 | 200 |
| Egress di akhir horizon | 0 | 80 |

### TCO 3 Tahun

- **Private:** 1.200 + (300 × 3) + (250 × 3) + 150 = **Rp3.000 juta**
- **Public:** 100 + (480 × 3) + (150 × 3) + 200 + 80 = **Rp2.270 juta**

Public cloud lebih rendah **Rp730 juta (≈24,3%)** pada asumsi dasar.

### ROI Sederhana

Manfaat kumulatif = 1.200 × 3 = **Rp3.600 juta**

- **Private:** (3.600 − 3.000) ÷ 3.000 = **20,0%**
- **Public:** (3.600 − 2.270) ÷ 2.270 ≈ **58,6%**

### Payback Period

| | Private | Public |
|---|---|---|
| Investasi + transisi awal | 1.200 + 150 = 1.350 | 100 + 200 = 300 |
| Manfaat bersih/tahun | 1.200 − (300 + 250) = 650 | 1.200 − (480 + 150) = 570 |
| **Payback** | 1.350 ÷ 650 ≈ **2,08 tahun** | 300 ÷ 570 ≈ **0,53 tahun** |

**Keterbatasan:** perhitungan ini belum memodelkan biaya akhir, perubahan kapasitas, pajak, diskonto, dan manfaat bertahap. Diskonto adalah tingkat suku bunga yang bisa diambil dari WACC, cost of equity, RRR, bunga pinjaman, atau inflasi.

## 4. Analisis Sensitivitas

Skenario: **biaya operasi public cloud naik 30%.**
- Rp480 juta naik menjadi Rp624 juta/tahun, atau tambahan Rp144 juta × 3 = Rp432 juta.
- TCO public menjadi **Rp2.702 juta**. Masih di bawah private (Rp3.000 juta), tetapi selisihnya turun menjadi **Rp298 juta**.

Variabel lain yang perlu diuji: pertumbuhan data, egress, GPU, lisensi, kurs, biaya tenaga ahli, dan utilisasi private cloud. Hindari **presisi semu**; gunakan skenario rendah, dasar, dan tinggi.

## 5. Private Cloud vs Public Cloud

| Dimensi | Private cloud | Public cloud |
|---|---|---|
| Biaya awal | Cenderung tinggi | Cenderung rendah |
| Biaya rutin | Lebih tetap; perlu perencanaan kapasitas | Variabel, mengikuti pemakaian |
| Skalabilitas | Dibatasi kapasitas tersedia | Elastis, relatif cepat |
| Kontrol teknis | Lebih langsung | Melalui layanan provider |
| Provisioning | Bergantung otomasi dan proses | Umumnya cepat |
| Operasi | Lebih banyak di organisasi | Berbagi dengan provider |
| Risiko utama | Overcapacity, refresh, skill | Cost sprawl, lock-in, egress |
| Cocok ketika | Kebutuhan stabil atau kontrol khusus | Beban berubah-ubah atau butuh time-to-market cepat |

### Kerangka Keputusan Deployment

1. **Regulasi dan data:** ada batas lokasi, isolasi, atau kontrol khusus?
2. **Pola beban:** stabil atau sangat fluktuatif?
3. **Kapabilitas:** mampukah tim mengoperasikan platform 24/7?
4. **Ekonomi:** bagaimana TCO 3–5 tahun dan biaya beban puncak?
5. **Strategi:** seberapa penting portabilitas dan menghindari lock-in?

Hasilnya bisa public, private, hybrid, atau keputusan berbeda untuk tiap workload.

### Hybrid Cloud

- Mengintegrasikan private dan public dengan konektivitas, identitas, operasi, dan tata kelola yang konsisten.
- **Contoh:** data sensitif dan sistem inti di private, sedangkan front-end dan beban musiman di public.
- **Biaya tambahan:** integrasi jaringan, replikasi data, observability ganda, skill lintas platform, kompleksitas keamanan.
- Pilih hybrid jika kebutuhan bisnis membenarkan kompleksitasnya, bukan karena terlihat paling fleksibel.

## 6. Kontrol Biaya: FinOps dan Tata Kelola

- **Tagging dan ownership:** setiap resource punya pemilik, aplikasi, lingkungan, dan cost center.
- **Rightsizing:** sesuaikan CPU/RAM/storage dengan penggunaan aktual.
- **Scheduling:** matikan resource nonproduksi saat tidak dipakai.
- **Budget, anomaly alert, forecast,** dan review biaya rutin lintas fungsi.
- **Reserved capacity** bisa menurunkan biaya, tetapi berisiko jika kebutuhan berubah.
- Pantau **unit economics** (biaya per transaksi, per pengguna aktif, per workload), bukan total tagihan saja.

## Latihan Kelompok

Perusahaan ritel dengan lonjakan trafik 4× saat kampanye:
- **Private:** TCO 3 tahun Rp2,4 M; perlu investasi tambahan saat puncak.
- **Public:** TCO dasar Rp2,0 M; bisa naik Rp350 juta saat kampanye jika tidak dikendalikan.
- **Syarat:** SLA 99,9%, backup teruji, tim operasi hanya 3 orang.

Tugasnya: rekomendasikan deployment, tulis 3 asumsi yang perlu divalidasi, dan tentukan 2 kontrol biaya/risiko. Penilaian didasarkan pada alasan, angka, risiko, dan asumsi, bukan pilihan cloud saja.

## Key Takeaways

- **TCO** menilai biaya siklus hidup, **ROI** menilai hasil relatif terhadap biaya, dan **payback** menilai kecepatan balik modal. NPV diperlukan jika waktu arus kas penting.
- Bandingkan kapasitas, SLA, keamanan, horizon, dan cakupan layanan yang setara.
- Private cloud memberi kontrol langsung; public cloud memberi elastisitas. Keduanya punya trade-off.
- Uji kesimpulan finansial dengan analisis sensitivitas, risiko, kapabilitas tim, dan strategi bisnis.
- Rekomendasi yang baik menyatakan angka, asumsi, ketidakpastian, dan kapan keputusan perlu ditinjau ulang.

## Referensi (dari materi)

- NIST SP 800-145, *The NIST Definition of Cloud Computing*.
- FinOps Foundation, *FinOps Framework* – https://www.finops.org/framework/
- AWS Cloud Financial Management, Microsoft Cost Management, Google Cloud FinOps.
- Storment, J. R., & Fuller, M. *Cloud FinOps: Collaborative, Real-Time Cloud Value Decision Making*. O'Reilly.
