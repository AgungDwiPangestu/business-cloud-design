# Materi Minggu 6: Desain High Availability dan Efisiensi Infrastruktur

**AI yang digunakan:** Claude Opus 5.5 (Anthropic)

**Prompt:**

> **Peran:** Kamu adalah asisten akademik untuk mata kuliah Business Cloud Design.
>
> **Konteks:** Saya mahasiswa Sistem Informasi semester 7. Terlampir materi Pertemuan 6 berjudul "Desain High Availability dan Efisiensi Infrastruktur" (file `06--business-cloud-design.pdf`).
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

## Pengantar: Dua Tujuan yang Harus Diseimbangkan

- **High Availability:** layanan tetap dapat digunakan saat komponen, jaringan, atau lokasi mengalami gangguan.
- **Efisiensi infrastruktur:** kapasitas, biaya, energi, dan kompleksitas sebanding dengan kebutuhan bisnis.
- **Tantangan:** meningkatkan ketahanan tanpa membangun kapasitas berlebihan.
- **Pertanyaan kunci:** layanan apa yang harus selalu tersedia, dan berapa biaya yang layak untuk mencapainya?

## 1. Fondasi HA dan Metrik

### Definisi

- **High Availability (HA)** adalah kemampuan layanan untuk tetap dapat diakses dengan tingkat gangguan yang dapat diterima.
- HA **bukan** berarti sistem tidak pernah gagal. Desain HA mengurangi peluang kegagalan dan mempercepat pemulihan.
- Availability dipengaruhi aplikasi, compute, storage, jaringan, identitas, DNS, fasilitas, dan operasional.
- Dari perspektif Sistem Informasi, ukur dampaknya terhadap proses bisnis dan pengguna, bukan hanya status server.

### Metrik

- **MTBF** (*Mean Time Between Failures*): rata-rata waktu antar kegagalan.
- **MTTR** (*Mean Time To Repair/Recover*): rata-rata waktu pemulihan.

> **Availability ≈ MTBF ÷ (MTBF + MTTR)**

| Target | Downtime maksimum per tahun |
|---|---|
| 99% | ± 3 hari 15 jam |
| 99,9% | ± 8 jam 46 menit |
| 99,99% | ± 52 menit 34 detik |
| 99,999% | ± 5 menit 15 detik |

### RTO dan RPO

| | Arti | Pertanyaan | Contoh |
|---|---|---|---|
| **RTO** (*Recovery Time Objective*) | Batas maksimum waktu layanan boleh mati | "Berapa lama boleh berhenti?" | Layanan akademik pulih dalam 2 jam |
| **RPO** (*Recovery Point Objective*) | Batas maksimum data yang boleh hilang (dalam rentang waktu) | "Berapa banyak data boleh hilang?" | Maksimal 15 menit data |

Target ditetapkan berdasarkan dampak bisnis, kewajiban layanan, dan biaya pemulihan.

### SPOF dan Failure Domain

- **SPOF** (*Single Point of Failure*): satu komponen yang jika gagal dapat menghentikan seluruh layanan.
- **Failure domain:** batas area dampak kegagalan, mulai dari host, rack, zona, region, hingga penyedia.

## 2. Pola Desain HA

### Redundansi

Struktur dasarnya: **pengguna → load balancer → app node A/B → database HA**.

- Redundansi bisa diterapkan pada compute, jaringan, daya, storage, database, DNS, dan jalur koneksi.
- Dua komponen yang berbagi sumber daya atau konfigurasi identik masih bisa **gagal bersamaan**.

### Load Balancing dan Health Check

- Load balancer mendistribusikan request ke beberapa instance aplikasi.
- Health check mendeteksi instance yang tidak sehat dan mengeluarkannya dari pool.
- **Algoritma umum:** round robin, least connections, weighted, latency-based.
- Pastikan sesi, file upload, dan cache tidak bergantung pada satu instance.
- Load balancer itu sendiri juga harus redundant atau memakai layanan terkelola yang HA.

### Stateful vs Stateless

| Stateful di instance | Stateless app tier |
|---|---|
| Sesi/file disimpan di server tertentu | Instance tidak menyimpan state penting secara lokal |
| Saat instance gagal, sesi/data ikut hilang | Sesi di shared cache, file di object storage |
| Sulit di-*scale* horizontal | Instance mudah ditambah, diganti, atau dipindah |

**Prinsip:** pisahkan compute dari state dan data persisten.

### Availability pada DBMS

| Pola | Karakteristik |
|---|---|
| **Primary–standby** | Satu node melayani write; standby mengambil alih saat failover |
| **Synchronous replication** | Write menunggu replikasi; konsistensi kuat, tetapi latency bisa naik |
| **Asynchronous replication** | Write tidak menunggu replika; performa lebih baik, tetapi berisiko kehilangan transaksi terakhir dan ada *replication lag* |
| **Backup** | Salinan untuk pemulihan; **bukan** pengganti replikasi atau HA |

- **Split-brain:** klaster terpecah dan tiap bagian merasa sebagai satu-satunya yang aktif, sehingga bisa terjadi dua node menulis data bersamaan.
- Pilih pola berdasarkan RPO, RTO, konsistensi transaksi, beban, dan biaya.

### Availability Zone dan Multi-Region

- **Multi-AZ:** melindungi dari kegagalan zona/lokasi lokal. Sering menjadi *baseline* HA.
- **Multi-region:** melindungi dari gangguan regional, tetapi lebih kompleks dan mahal. Dipilih jika dampak gangguan region membenarkan biayanya.

### Failover: Otomatis atau Manual?

| Otomatis | Manual / approved |
|---|---|
| Pemulihan cepat | Keputusan mempertimbangkan konteks |
| Risiko false positive, perpindahan berulang, split-brain | Lebih lambat, bergantung operator |
| Butuh health check dan *quorum* andal | Cocok untuk sistem kritis dengan change control ketat |

- **Fencing:** mengisolasi atau mematikan node/VM/pod yang bermasalah agar tidak mengganggu klaster.
- **Alur failover yang baik:** deteksi → keputusan → alih trafik → verifikasi data → pemulihan normal. Alur ini harus **diuji**.

## 3. Disaster Recovery dan Pengujian

### Strategi DR

| Strategi | Ciri | Biaya | RTO |
|---|---|---|---|
| **Backup & restore** | Pulihkan dari backup | Rendah | Lama |
| **Pilot light** | Komponen inti/data siap; kapasitas penuh dinyalakan saat bencana | ↑ | ↓ |
| **Warm standby** | Cadangan berjalan dengan kapasitas terbatas, di-*scale up* saat failover | ↑↑ | ↓↓ |
| **Hot standby** | Siap melayani dengan jeda minimal | Tertinggi | Tercepat |

Semakin cepat target pemulihan, semakin besar biaya kapasitas cadangan dan sinkronisasi.

### Backup Bukan HA

- Replikasi dapat ikut menyalin penghapusan, korupsi, atau ransomware.
- Backup perlu retensi, enkripsi, kontrol akses, dan pemisahan failure domain.
- **Prinsip 3-2-1:** 3 salinan, 2 jenis media, 1 salinan off-site/offline.
- **Uji restore berkala.** Job backup yang sukses tidak membuktikan data dapat dipulihkan.
- Dokumentasikan siapa yang berwenang, urutan restore, dan cara validasi hasil.

### Observability

| Metrics | Logs | Traces |
|---|---|---|
| Availability, latency, error rate, throughput, CPU, memori, replication lag | Catatan peristiwa untuk investigasi, audit, dan korelasi insiden | Melacak satu request lintas service untuk menemukan bottleneck |

- **SLO** mengubah harapan layanan menjadi target terukur.
- **Error budget:** batas maksimal kegagalan yang diizinkan dalam periode tertentu. Konsep dari **SRE** (*Site Reliability Engineering*) ini menyeimbangkan kecepatan rilis fitur dan stabilitas.

### Uji Ketahanan

- **Failover test:** matikan node secara terkontrol dan ukur waktu pemulihan.
- **Restore test:** pulihkan backup ke lingkungan terisolasi dan validasi integritasnya.
- **Load test:** beban normal, puncak, dan lonjakan mendadak.
- **Chaos experiment:** injeksi kegagalan terbatas dengan prosedur rollback.
- **Game day:** simulasi insiden lintas tim, termasuk komunikasi dan keputusan bisnis.

## 4. Efisiensi Infrastruktur

- **Right-sizing:** sesuaikan CPU, RAM, IOPS, dan kapasitas dengan pemakaian aktual.
- **Elasticity:** kapasitas naik-turun mengikuti demand.
- **Utilization:** hindari resource idle dan konsolidasikan beban tanpa mengorbankan SLA.

> Efisiensi = memenuhi kebutuhan layanan dengan total biaya dan risiko yang dapat diterima. Optimasi yang menurunkan biaya tetapi melanggar RTO/RPO **bukan** optimasi yang berhasil.

### Scaling

| Vertical | Horizontal | Autoscaling |
|---|---|---|
| Tambah CPU/RAM pada satu instance | Tambah jumlah instance | Aturan kapasitas berdasarkan metrik/jadwal |
| Mudah, tetapi ada batas maksimum dan SPOF tetap ada | Mendukung redundansi; aplikasi harus mendukung distribusi beban | Perlu threshold, cooldown, min/max, proteksi scale-in |

**Contoh aturan:** *scale out* saat CPU > 70% selama 5 menit; *scale in* saat CPU < 35% selama 15 menit.

### Efisiensi Storage, Jaringan, dan Data

- **Storage tiering:** data ditempatkan pada kelas layanan yang sesuai.
- **Lifecycle policy:** pindahkan atau hapus objek sesuai retensi dan regulasi.
- **Compression/deduplication:** menghemat kapasitas, dengan trade-off CPU dan latency.
- **Cache:** mengurangi beban backend; perlu strategi invalidasi.
- **CDN/edge caching:** menurunkan latency dan trafik ke origin.

### TCO dan Unit Economics

- **Komponen biaya:** compute, storage, database, egress, load balancer, backup/DR, observability, lisensi, tenaga operasional, migrasi, dan exit.
- **Ukur biaya per hasil:** per transaksi, per pengguna aktif, per GB diproses, per jam layanan tersedia. Bandingkan juga biaya normal dengan biaya saat failover.

### Trade-off

**Availability ↔ Efisiensi biaya ↔ Kompleksitas**, yang ditentukan oleh target bisnis. Tidak ada desain yang paling benar untuk semua sistem.

## 5. Studi Kasus: Portal Layanan Akademik

| Kondisi saat ini | Target | Kendala |
|---|---|---|
| Satu VM aplikasi, satu database, backup harian, lonjakan saat KRS | Availability 99,9%, RTO 2 jam, RPO 15 menit | Tim TI kecil, tidak boleh kehilangan transaksi pembayaran, lonjakan musiman, biaya terbatas |

**SPOF yang teridentifikasi:** VM aplikasi tunggal, database tunggal, backup harian (RPO 24 jam jauh di atas target 15 menit), dan tidak adanya load balancer.

**Arah solusi (salah satu kemungkinan):**
- Pengguna → DNS/WAF → load balancer → app node A & B → DB primary + replica/backup.
- Multi-AZ bila tersedia, failover database yang teruji, backup terisolasi, dan object storage untuk dokumen.
- Autoscaling terukur untuk periode KRS, monitoring SLO, dan prosedur insiden.
- Validasi RTO/RPO melalui simulasi.

## Key Takeaways

1. **Desain dari bisnis:** tetapkan layanan kritis, dampak downtime, SLA/SLO, RTO, dan RPO.
2. **Hilangkan SPOF:** redundansi, health check, failover, backup yang teruji, dan observability.
3. **Optimalkan dengan data:** right-sizing, autoscaling, tiering, dan evaluasi biaya per hasil.
4. Infrastruktur yang baik bukan yang paling mahal atau paling kompleks, melainkan yang **tepat** untuk kebutuhan bisnis.

## Referensi (dari materi)

- Google Cloud Architecture Framework – Reliability.
- AWS Well-Architected Framework – Reliability & Cost Optimization.
- Microsoft Azure Well-Architected Framework.
- NIST SP 800-34 Rev. 1 – *Contingency Planning Guide for Federal Information Systems*.
- Google SRE Book – https://sre.google/sre-book/table-of-contents/
