# Materi Minggu 7: Skalabilitas Berbasis Kontainer dan Virtualisasi

**AI yang digunakan:** Claude Opus 5.5 (Anthropic)

**Prompt:**

> **Peran:** Kamu adalah asisten akademik untuk mata kuliah Business Cloud Design.
>
> **Konteks:** Saya mahasiswa Sistem Informasi semester 7. Terlampir materi Pertemuan 7 berjudul "Skalabilitas Berbasis Kontainer & Virtualisasi" (file `07--business-cloud-design.pdf`).
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

## Agenda

1. Landasan skalabilitas: vertical vs horizontal scaling dan dampaknya pada efisiensi bisnis.
2. VM vs kontainer: hypervisor vs container engine, dan isolasi sistem.
3. Orkestrasi Kubernetes: auto-scaling, load balancing, self-healing cluster.
4. Analisis FinOps: kalkulasi TCO, optimasi biaya, strategi multi-cloud.

## 1. Landasan Skalabilitas

| Scale-up (Vertical Scaling) | Scale-out (Horizontal Scaling) |
|---|---|
| Upgrade CPU, RAM, disk pada **satu** server | Menambah node/replika secara elastis |
| Dibatasi spesifikasi maksimum hardware | Skalabilitas mengikuti beban trafik |
| Risiko downtime karena perlu restart | Mendukung HA; layanan tetap berjalan tanpa interupsi |

**Contoh bisnis:** saat trafik toko online melonjak, menambah replika aplikasi (scale-out) lebih aman daripada mengganti server dengan yang lebih besar (scale-up).

## 2. Arsitektur Virtual Machine (VM)

VM membagi hardware fisik menjadi beberapa mesin independen melalui lapisan **hypervisor**. Setiap VM menjalankan **Guest OS**-nya sendiri.

Susunan lapisannya: **Infrastructure (bare-metal server) → Hypervisor → Guest OS + App**.

| Tipe hypervisor | Penjelasan | Contoh |
|---|---|---|
| **Type 1 (bare-metal)** | Berjalan langsung di hardware | VMware ESXi, KVM |
| **Type 2 (hosted)** | Berjalan di atas OS host | VirtualBox, VMware Workstation |

Teknik virtualisasi:
- **PVM** (*Paravirtualization*): guest OS dimodifikasi agar bekerja sama dengan hypervisor.
- **HVM** (*Hardware-assisted Virtualization*): dibantu fitur hardware seperti Intel VT-x dan AMD-V.

## 3. Arsitektur Kontainer

Kontainer mengisolasi **proses** aplikasi tetapi **berbagi kernel OS host**, sehingga tidak ada overhead Guest OS terpisah.

Susunan lapisannya: **Infrastructure → Host OS (kernel shared) → Container engine (Docker/containerd) → App + bins/libs**.

Keunggulan menurut materi:
- **Startup dalam hitungan detik**, tanpa booting OS.
- **Paket konsisten**: kode, dependensi, dan environment dikemas bersama.
- **Efisiensi tinggi**: memori yang dipakai 30–50% lebih sedikit dibanding VM.

## 4. Perbandingan VM vs Kontainer

| Metrik | Virtual Machine | Kontainer (Docker) |
|---|---|---|
| Tingkat abstraksi | Hardware (hypervisor) | OS (kernel sharing) |
| Waktu boot | 2–5 menit | Hitungan detik/milidetik |
| Ukuran image | Besar (beberapa GB) | Ringan (MB) |
| Isolasi & keamanan | Isolasi keras (hardware level) | Isolasi proses |
| Kecepatan skalabilitas | Relatif lambat dan berat | Sangat cepat dan dinamis |

**Dampak bisnis:** menurut materi, rata-rata auto-scaling kontainer merespons lonjakan trafik dalam **< 3 detik**. Ini mencegah kerugian finansial akibat outage saat transaksi melonjak.

## 5. Orkestrasi dengan Kubernetes (K8s)

- **Auto-scaling (HPA, *Horizontal Pod Autoscaler*):** jumlah replika pod diatur otomatis berdasarkan pemakaian CPU/RAM.
- **Self-healing:** kontainer yang gagal di-restart otomatis, dan node yang tidak responsif diganti.
- **Load balancing:** trafik didistribusikan merata ke seluruh kontainer aktif.

## 6. Arsitektur Hibrida: VM + Kontainer (Standar Produksi)

| Lapisan infrastruktur (VM sebagai host) | Lapisan aplikasi (kontainer di dalam VM) |
|---|---|
| Isolasi tingkat penyewa (multi-tenancy), keamanan ketat, batas alokasi resource di cloud provider (AWS EC2, GCP Compute Engine) | Microservices berjalan di kontainer di atas VM untuk kemudahan deployment, portabilitas tinggi, dan scaling granular |

Pendekatan ini menggabungkan **isolasi kuat VM** dengan **kelincahan kontainer**.

## 7. FinOps dan Efisiensi Biaya (TCO)

Angka ilustratif dari materi:
- **Kebutuhan hardware:** VM butuh ~10 server fisik, sedangkan kontainer bare-metal ~4 server (CAPEX hemat ~60%).
- **Lisensi:** lisensi Guest OS dan CPU-core hypervisor berkurang hingga 80%.
- **Daya dan HVAC** (*Heating, Ventilation, and Air Conditioning*): konsolidasi server menurunkan biaya listrik dan pendingin (OPEX hemat ~60%).
- **Optimasi densitas:** utilisasi CPU/RAM hingga 80% per server fisik.
- **Pay-per-use precision:** membayar resource cloud sesuai detik pemakaian kontainer, sehingga instance menganggur berkurang.

> Catatan: angka di atas bersifat ilustratif. Seperti dibahas pada minggu 4–5, hasil nyata bergantung pada workload, utilisasi, dan asumsi yang setara.

## 8. Studi Kasus

| E-commerce flash sale | Perbankan digital |
|---|---|
| Lonjakan trafik 10× diatasi dengan auto-scaling ribuan pod kontainer dalam 30 detik, tanpa mengganggu modul pembayaran | Isolasi ketat VM untuk database finansial, kontainer untuk aplikasi mobile banking agar rilis fitur lebih cepat |

## Key Takeaways

- **Horizontal scaling** lebih elastis dan mendukung HA dibanding vertical scaling yang dibatasi hardware.
- **VM** unggul pada isolasi (hardware level); **kontainer** unggul pada kecepatan, ukuran, dan efisiensi karena berbagi kernel.
- **Kubernetes** memberi auto-scaling (HPA), self-healing, dan load balancing untuk kontainer.
- Standar produksi modern adalah **hibrida**: kontainer berjalan di atas VM.
- Kontainer berpotensi menurunkan CAPEX dan OPEX melalui konsolidasi dan densitas, tetapi tetap perlu dianalisis dengan TCO dan FinOps.
