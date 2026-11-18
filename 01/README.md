# Materi Minggu 1: Paradigma Cloud Computing dan Gerakan Open Source

**AI yang digunakan:** Claude Opus 5.5 (Anthropic)

**Prompt:**

> **Peran:** Kamu adalah asisten akademik untuk mata kuliah Business Cloud Design.
>
> **Konteks:** Saya mahasiswa Sistem Informasi semester 7. Terlampir materi Pertemuan 1 berjudul "Paradigma Cloud Computing dan Gerakan Open Source" (file `01--paradigma-cloud-comp-dan-open-source.pdf`).
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

## 1. Apa itu Cloud Computing?

Menurut **NIST**, cloud computing adalah model yang memungkinkan akses jaringan yang mudah, tersedia di mana saja, dan sesuai permintaan (*on-demand*) ke kumpulan sumber daya komputasi yang dapat dikonfigurasi (jaringan, server, storage, aplikasi, layanan). Sumber daya ini dapat disediakan dan dilepas dengan cepat, dengan upaya manajemen atau interaksi dengan penyedia yang minimal.

**Contoh bisnis:** toko online cukup menyewa server dari penyedia cloud saat diperlukan, tanpa membeli dan merawat server sendiri.

## 2. Sejarah Cloud Computing

| Tahun | Peristiwa |
|---|---|
| 1950-an | Era mainframe; John McCarthy mengemukakan teori *time-sharing system* |
| 1961 | McCarthy memprediksi komputasi kelak menjadi utilitas seperti air dan listrik (*grid computing*) |
| 1969 | ARPANET |
| 1990 | WWW oleh Tim Berners-Lee, lahir era *client-server computing* |
| 1997 | Prof. Ramnath Chellappa (Emory University) memakai istilah *cloud computing* |
| 1999 | Salesforce.com |
| 2002 | AWS |
| 2006 | Amazon EC2 |
| 2009 | Google Cloud |

## 3. Karakteristik Cloud Computing

- **On-demand self-service:** pengguna mendapatkan sumber daya (storage, waktu server) secara otomatis dan instan tanpa interaksi manusia dengan penyedia.
- **Broad network access:** layanan diakses lewat jaringan dari berbagai perangkat (smartphone, tablet, laptop) dan lokasi.
- **Resource pooling:** penyedia mengelola kumpulan besar sumber daya fisik dan virtual untuk melayani banyak pelanggan sekaligus.
- **Rapid elasticity:** kapasitas (CPU, memori, storage) bertambah atau berkurang otomatis mengikuti permintaan.
- **Measured service:** penggunaan dipantau dan dilaporkan otomatis sehingga memungkinkan penagihan *pay-per-use*.
- **Multitenancy:** satu instance software/hardware melayani banyak *tenant* (penyewa), dengan data masing-masing tetap terisolasi.

## 4. Kelebihan dan Kekurangan

**Kelebihan:**
- **Ekonomis**, walau tidak selalu; tergantung banyak faktor, termasuk SDM. Model harga: *subscription*, bulanan, per jam/detik, dan *transient/spot* (harga diskon untuk kapasitas lebih).
- Kapasitas storage praktis tak terbatas.
- Akses universal.
- Mudah di-*scale*.
- Backup dan recovery tersedia.
- Keamanan dan keandalan.

**Kekurangan:**
- Bergantung pada koneksi Internet.
- Isu privasi data.
- Risiko *downtime*.
- Biaya bisa lebih tinggi daripada on-premises (atau lebih rendah).

## 5. Model Layanan Cloud Computing

Tiga kelompok besar:

| Model | Target pengguna |
|---|---|
| **SaaS** (Software as a Service) | End user |
| **PaaS** (Platform as a Service) | Developer |
| **IaaS** (Infrastructure as a Service) | Network/infrastructure architect |

Saat ini berkembang menjadi **XaaS** (*Everything as a Service*, juga ditulis `*aaS`): semua perangkat komputasi dapat disediakan sebagai layanan, misalnya Backend as a Service dan Data as a Service.

## 6. Model Deployment

- **Public cloud**
- **Private cloud** (on-premise)
- **Hybrid cloud**
- **Community cloud**

## 7. Perusahaan Penyedia Cloud

- **Global:** AWS, Google, Alibaba, Heroku, Microsoft, Oracle, IBM.
- **Indonesia:** Biznet Gio, Telkom Telstra, Lintasarta.

## 8. SaaS – Software as a Service

- Pengguna mendapat fungsionalitas software **tanpa instalasi dan maintenance** di komputernya; software berbasis web disediakan oleh provider.
- **Contoh:** Microsoft 365, Google Docs.
- Web adalah antarmuka paling umum untuk SaaS.
- **Frontend** adalah komponen antarmuka, terdiri dari:
  - **UI** (User Interface): keindahan tampilan.
  - **UX** (User Experience): kepuasan saat menggunakan produk.
- **Jenis frontend:**
  - Mobile: native, hybrid/WebView.
  - Web: HTML-CSS-JS, Vue, Angular, React.
  - Headless: curl, wget.
  - GUI: native, Electron.
  - TUI: ncurses, aplikasi console.
- **Backend** adalah sisi server yang menjalankan logika aplikasi.

## 9. PaaS – Platform as a Service

- Menyediakan platform lengkap (hardware, software, infrastruktur) untuk **membangun, menjalankan, dan mengelola aplikasi**, tanpa biaya dan kompleksitas membangun sendiri.
- **Penggunaan:** development framework, analytics/BI, layanan tambahan (workflow, directory, security, scheduling), API dan microservices, IoT, dan layanan AI.
- **Kunci kemudahan PaaS adalah teknologi container.** Platform dikemas sebagai *image* lalu dijalankan dengan **Docker** (container engine), seolah berjalan di hardware asli. Ekosistemnya mencakup Docker, Docker Compose, dan Docker Swarm.
- **Serverless:** organisasi tidak perlu menyediakan server sendiri karena server disediakan provider. Pendekatan ini erat kaitannya dengan arsitektur **microservices**.
- Container dapat menjadi endpoint API. Hubungan antar-container diorkestrasi dengan Docker Swarm atau **Kubernetes** yang berjalan di atas IaaS.
- **Contoh provider:** DigitalOcean, AWS Elastic Beanstalk, Google App Engine, Microsoft Azure, Salesforce, Red Hat OpenShift, Mendix, IBM Cloud, SAP Cloud Platform, Engine Yard.

## 10. IaaS – Infrastructure as a Service

- Menyediakan API tingkat tinggi untuk sumber daya dasar: komputasi fisik, lokasi, partisi data, keamanan, dan backup. Layanan diberikan secara *on-demand* dengan sistem bayar **pay-as-you-go**.
- **Hypervisor** untuk menjalankan VM: Xen, KVM, VMware, VirtualBox, Hyper-V, LXD.
- **Software orkestrasi cloud:** Apache CloudStack, OpenNebula, OpenStack.
- **Komponen:** data center fisik, sumber daya komputasi, jaringan, dan storage.
- **BMaaS** (*Bare Metal as a Service*) memberi akses langsung ke hardware. Cocok untuk HPC, big data, dan GPU computing, tetapi provisioning-nya lebih lambat.
- Untuk kebutuhan kontrol tinggi (misalnya data sensitif), organisasi bisa membuat **Virtual Private Cloud** di public cloud. Caranya dengan subnet, range IP, virtual firewall, security group, network ACL, site-to-site VPN, dan load balancing.
- **Provisioning engine:** RackHD, xCAT, Foreman.

## 11. Cloud Computing dan Open Source

- **Fondasi teknologi:** hampir seluruh infrastruktur cloud modern dibangun di atas open source (Linux, KVM, Kubernetes). Open source memberi cetak biru yang fleksibel dan bebas *vendor lock-in*.
- **Katalis aksesibilitas:** cloud mendemokratisasi teknologi. Perusahaan tidak perlu membeli hardware mahal untuk mencoba teknologi baru, dan biayanya masuk anggaran operasional (OPEX).
- **Siklus inovasi cepat:** kode open source dapat dijalankan di cloud dalam hitungan menit, sehingga *time-to-market* menjadi jauh lebih cepat.

## 12. Bagaimana Cloud + Open Source Menciptakan *Business Value Added*?

- **Kolaborasi:** komunitas terbuka dan infrastruktur elastis menghasilkan *business agility* dengan biaya minimum.
- **Kedaulatan data dan efisiensi biaya:** open source di private cloud memungkinkan organisasi seperti bank atau instansi pemerintah berinovasi dengan aman, mematuhi regulasi (UU PDP), dan memangkas biaya lisensi.
- **Standardisasi global:** inovasi bersifat universal, sehingga integrasi, migrasi, dan kolaborasi tidak terkunci pada satu ekosistem.
- **Efek domino:** komunitas open source menciptakan inovasi → cloud menyediakannya sebagai layanan siap pakai → bisnis menciptakan nilai baru secara instan tanpa risiko finansial besar.

## Key Takeaways

- Cloud computing adalah **model penyediaan layanan** yang *on-demand*, elastis, dan terukur, bukan sekadar "server di internet".
- SaaS, PaaS, dan IaaS melayani pengguna yang berbeda (end user, developer, infrastructure architect) dan kini berkembang menjadi XaaS.
- Container (Docker) dan orkestrasi (Kubernetes) adalah kunci kemudahan PaaS; hypervisor dan orkestrator cloud adalah fondasi IaaS.
- Open source adalah fondasi teknologi cloud, dan kombinasi keduanya mempercepat inovasi serta menciptakan nilai bisnis dengan biaya rendah.
