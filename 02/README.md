# Materi Minggu 2: Model Layanan Cloud Computing

**AI yang digunakan:** Claude Opus 5.5 (Anthropic)

**Prompt:**

> **Peran:** Kamu adalah asisten akademik untuk mata kuliah Business Cloud Design.
>
> **Konteks:** Saya mahasiswa Sistem Informasi semester 7. Terlampir materi Pertemuan 2 berjudul "Model Layanan Cloud Computing" (file `02--model-layanan-cloud-computing.pdf`).
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

## 1. Pengertian Cloud Services

*Cloud services* adalah berbagai layanan yang disediakan vendor cloud secara *on-demand* kepada organisasi untuk memfasilitasi berbagai fungsi dan aplikasi melalui Internet.

## 2. Keuntungan Menggunakan Cloud Services

- **Power of scaling:** kapasitas mudah ditambah atau dikurangi.
- **Secure environment:** lingkungan yang aman.
- **Increased flexibility:** fleksibilitas lebih tinggi.
- **Cost reduction:** biaya berkurang.
- **Higher speed:** layanan lebih cepat tersedia.

## 3. Model Utama Cloud Services

Tiga model utama adalah **SaaS**, **PaaS**, dan **IaaS**, ditambah model turunan seperti NaaS, IDaaS, dan AIaaS.

## 4. SaaS (Software as a Service)

- Menyediakan software langsung ke end user melalui Internet. UI/UX berbasis web, tidak ada aplikasi yang diinstal di sisi pengguna (kecuali kasus khusus, misalnya plugin browser).
- Semua komponen berada di server vendor; arsitektur yang dipakai umumnya **multitenant**.
- **Jenis:** email dan kolaborasi, CRM, healthcare, billing/invoicing, data management, document management, office apps, social networking.
- **Contoh:** Dropbox, Google Docs, Microsoft 365, Mailchimp, Slack, Asana, Trello, GitHub, Assembla.

| Keuntungan | Kekurangan |
|---|---|
| Universal access | Bergantung pada koneksi Internet |
| Scalable | Keamanan data |
| Hemat waktu dan biaya | Kinerja ditentukan kualitas koneksi |
| Selalu ter-update | Fitur terbatas |

**Contoh bisnis:** UMKM memakai Google Workspace untuk email dan dokumen tanpa perlu server sendiri.

## 5. PaaS (Platform as a Service)

- Menyediakan platform bagi developer untuk **membuat, menguji, menjalankan, dan men-deploy** aplikasi (web).
- Vendor biasanya menyediakan Docker image yang dikelola dengan **Kubernetes (K8s)**, ditambah tools untuk bahasa pemrograman yang didukung.

| Keuntungan | Kekurangan |
|---|---|
| Simple dan mudah | Risiko keamanan |
| Lingkungan pengembangan lebih lengkap | *Vendor lock-in* (sulit pindah vendor) |
| Biaya rendah | Kemungkinan perubahan kebijakan dari vendor |
| Multiplatform (laptop, mobile, komputer) | |
| Tools cepat dan fleksibel | |

**Tipe PaaS:**
- Berdasarkan deployment: public, private, hybrid.
- **CPaaS** (*Communication Platform as a Service*).
- **MPaaS** (*Mobile Platform as a Service*).
- OpenPaaS → SaaS.

## 6. IaaS (Infrastructure as a Service)

- Menyediakan infrastruktur komputasi: server, storage, VM, dan jaringan.
- **Contoh:** Google Compute Engine, Amazon EC2, Rackspace Managed Cloud.

| Keuntungan | Kekurangan |
|---|---|
| Hemat waktu dan biaya | Risiko keamanan |
| Scalable dan fleksibel | Kemungkinan masalah teknis |
| Akses ke sumber daya | Upgrade dan maintenance |
| Tidak terikat lokasi | Bergantung pada Internet |
| Pay per use | |
| Fokus pada pertumbuhan bisnis | |

## 7. NaaS (Network as a Service)

- Sebenarnya bagian dari IaaS.
- Infrastruktur dan fungsi jaringan disediakan sebagai layanan sesuai kebutuhan, tanpa organisasi harus membeli dan mengelola seluruh perangkat jaringan fisiknya.
- **Layanan:** VPN, bandwidth on demand, custom routing, multicast protocol, firewall, intrusion detection/prevention, WAN, content monitoring/filtering, antivirus.

## 8. IDaaS (Identity as a Service)

- Layanan cloud yang menyediakan **IAM** (*Identity and Access Management*, pengelolaan identitas dan hak akses pengguna).
- **Fitur:** informasi registrasi, directory services, authentication services, risk and event monitoring, profile management, **SSO** (*Single Sign-On*, satu login untuk banyak aplikasi).
- **Keuntungan:** pengguna tidak perlu banyak akun dan password, dan administrasi akun terpusat.

## 9. AIaaS (Artificial Intelligence as a Service)

- Layanan AI yang disediakan melalui cloud.
- Materi mengutip François Chollet (pembuat Keras): kecerdasan adalah **efisiensi dalam mempelajari keterampilan baru**, bukan keterampilan itu sendiri.
- **Masalah utama yang dipecahkan AIaaS:**
  - Mesin untuk AI sangat mahal dan masif.
  - Ketersediaan data serta tools untuk mengelola data.

**Contoh bisnis:** startup memakai API AI dari penyedia cloud untuk chatbot tanpa membeli GPU sendiri.

## 10. Layanan Lainnya

Disaster Recovery as a Service, Communication as a Service, Hardware as a Service, Desktop as a Service, Security as a Service, Healthcare as a Service, Transportation as a Service, dan lain-lain.

## Key Takeaways

- Cloud services adalah layanan *on-demand* dari vendor cloud melalui Internet, dengan manfaat utama skalabilitas, fleksibilitas, kecepatan, dan efisiensi biaya.
- SaaS untuk end user, PaaS untuk developer, dan IaaS untuk infrastruktur. Masing-masing punya trade-off; risiko yang sering muncul adalah keamanan, ketergantungan Internet, dan *vendor lock-in*.
- Model turunan (NaaS, IDaaS, AIaaS, dll.) menunjukkan bahwa hampir semua kebutuhan TI kini bisa diperoleh sebagai layanan (XaaS).
