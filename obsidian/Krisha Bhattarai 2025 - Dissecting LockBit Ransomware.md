---
title: "Dissecting LockBit Ransomware: From Infection to Impact"
authors:
  - Bhattarai, Krisha
year: 2025
venue: Independent Research Report (Technical/Forensic Report)
volume: "-"
pages: 1-30
doi: https://doi.org/10.13140/RG.2.2.13204.87687
url: https://www.researchgate.net/publication/403254660_Dissecting_LockBit_Ransomware_From_Infection_to_Impact
affiliation:
  - "-"
tags:
  - lockbit
  - raas
  - ransomware
  - malware-analysis
  - digital-forensics
  - case-study
  - revenue-sharing
  - colonial-vector
  - mitre-attack
  - boeing
  - royal-mail
  - anti-analysis
  - persistence
rating: 2
status: 🟡 reading
date_reviewed: 2026-06-14
type: technical-report
topic: ransomware-forensics
peer_reviewed: false
note: Laporan teknis berbasis hands-on malware analysis (lab forensik) terhadap sampel LockBit 3.0. Fokus utamanya adalah analisis forensik teknis (infection chain, persistence, encryption behaviour), bukan ekosistem bisnis RaaS. Relevansi terhadap program riset utama bersifat suplementer—berguna sebagai bukti teknis pendukung dan studi kasus, tetapi tidak menjawab RQ inti secara langsung.
---

## 📌 Summary

Laporan ini menyajikan analisis forensik terhadap ransomware LockBit, khususnya varian LockBit 3.0 (LockBit Black), melalui kombinasi tinjauan studi kasus dunia nyata (Boeing dan Royal Mail) dan analisis malware praktis di lingkungan virtual terisolasi. Penulis mengeksekusi sampel LockBit yang diperoleh dari MalwareBazaar di dalam mesin virtual Windows 10, kemudian mengamati perilaku malware menggunakan serangkaian alat forensik (Process Monitor, Process Explorer, Regshot, Autoruns, Registry Explorer, dan Any.run). Hasil analisis menunjukkan siklus infeksi lengkap—mulai dari enkripsi file, pembuatan ransom note, perubahan wallpaper, hingga upaya membangun persistence—serta mengonfirmasi penggunaan teknik anti-analisis dan anti-VM oleh LockBit untuk menghindari deteksi di lingkungan sandbox.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** LockBit telah menjadi salah satu operator RaaS paling aktif dan merusak secara global, namun pemahaman teknis yang mendalam tentang bagaimana malware ini secara aktual berperilaku pada level sistem (file, registry, proses) sering kali hanya tersedia dalam bentuk laporan vendor yang terfragmentasi.
- **Gap yang diisi:** Banyak studi kasus insiden LockBit (seperti Boeing dan Royal Mail) mendokumentasikan dampak bisnis dan operasional, tetapi tidak disertai bukti forensik langsung tentang mekanisme teknis di balik infeksi tersebut. Laporan ini mencoba menjembatani narasi insiden tingkat tinggi dengan observasi forensik langsung terhadap sampel malware.
- **Signifikansi:** Memahami jejak forensik (artefak registry, perilaku proses, pola I/O disk) dari LockBit penting untuk mendukung deteksi, investigasi insiden, dan strategi mitigasi proaktif, terutama mengingat LockBit menargetkan infrastruktur kritis seperti kesehatan, manufaktur, dan logistik.

---

## 🎯 Contribution

1. **Tinjauan Studi Kasus Dunia Nyata:** Menyajikan dua studi kasus rinci—serangan LockBit terhadap Boeing (2023) dan Royal Mail (2023)—yang menggambarkan dampak operasional, finansial, dan reputasional dari serangan RaaS terhadap infrastruktur penting.
2. **Pemetaan TTPs berbasis MITRE ATT&CK:** Menyusun kerangka method-opportunity-motive serta memetakan teknik LockBit (T1190, T1566, T1078, T1547.001, T1136, T1068, T1027, T1562, T1003, T1021, T1534) ke dalam tahapan kill chain.
3. **Demonstrasi Forensik Langsung:** Melakukan eksekusi sampel LockBit 3.0 nyata di lingkungan virtual terisolasi dan mendokumentasikan perilaku malware secara hands-on, termasuk proses enkripsi, pembuatan ransom note, dan perubahan wallpaper.
4. **Dokumentasi Perilaku Anti-Analisis:** Mengonfirmasi bahwa LockBit memiliki mekanisme anti-VM dan anti-sandbox yang menghambat eksekusi penuh di lingkungan analisis terkontrol (Any.run).
5. **Rekomendasi Mitigasi Praktis:** Memberikan daftar langkah mitigasi dasar (backup offline, VSS, patching, least privilege, monitoring) sebagai respons terhadap temuan forensik.

---

## ⚙️ Methodology

- **Pendekatan:** Kombinasi tinjauan studi kasus kualitatif (literature/case study review) dengan analisis malware praktis (hands-on dynamic dan static analysis) dalam lingkungan virtual terisolasi.
- **Sumber Data:**
  - Studi kasus: laporan media dan investigatif (SecurityWeek, TechCrunch, CyberScoop, CPO Magazine, Cybersecurity Dive, dll.) terkait insiden Boeing dan Royal Mail.
  - Sampel malware: satu sampel LockBit (varian terkait BlackMatter/LockBit) diunduh dari MalwareBazaar (bazaar.abuse.ch).
- **Lab Setup:** Mesin virtual Windows 10 dengan konfigurasi *host-only network* dan *guest isolation* (drag-and-drop serta clipboard dinonaktifkan) untuk mencegah malware keluar dari sandbox. Nilai registry "identifier" pada hive HKLM dihapus untuk mengurangi kemungkinan malware mendeteksi lingkungan virtual.
- **Alat Analisis:** Process Monitor, Process Explorer, Regshot, Autoruns, Registry Explorer, Wireshark, Detect It Easy (DIE), dan sandbox Any.run.
- **Prosedur:** Sampel diekstrak dari arsip terenkripsi (password "infected"), dieksekusi, lalu perilakunya diamati secara real-time (proses, penggunaan CPU, I/O disk, perubahan registry, perubahan wallpaper, pembuatan ransom note, dan enkripsi file dummy).
- **Threat Model:** Implisit—malware diasumsikan sebagai payload LockBit 3.0 yang dijalankan oleh afiliasi pasca-akses awal; fokus analisis adalah perilaku payload pada tahap eksekusi/impact, bukan tahap akses awal atau eksfiltrasi data.
- **Jenis Penelitian:** Deskriptif-eksperimental (malware analysis hands-on) dikombinasikan dengan deskriptif-analitis (case study review).

---

## 📊 Key Results

### 1. Model Bisnis dan Evolusi LockBit
LockBit dioperasikan sebagai platform RaaS di mana developer menyediakan tooling yang dapat dikustomisasi kepada afiliasi dengan skema bagi hasil sekitar **20-30% untuk operator LockBit**, sementara afiliasi mengambil porsi mayoritas setelah dipotong biaya akses awal. LockBit berevolusi melalui tiga generasi utama: LockBit 1.0 (2019-2020, fokus kecepatan enkripsi), LockBit 2.0 (2021-2022, penyebaran otomatis via Active Directory dan adopsi *double extortion*), dan LockBit 3.0/LockBit Black (2022-sekarang, dilengkapi kemampuan anti-analisis, anti-debugging, program *bug bounty* internal, dan fitur yang dapat dikustomisasi afiliasi).

### 2. Studi Kasus Boeing (2023)
LockBit mengklaim telah mencuri data sensitif Boeing dan menuntut tebusan sebesar **USD 200 juta**, yang ditolak Boeing. Sekitar **43 GB data dipublikasikan** di leak site LockBit, memengaruhi lebih dari 5.000 akun dan mengekspos data seperti log Citrix, backup email, serta dokumen audit. Vektor akses awal diduga melalui eksploitasi kerentanan **Citrix Bleed (CVE-2023-4966)**.

### 3. Studi Kasus Royal Mail (2023)
LockBit Black menyerang Royal Mail pada Januari 2023, mengenkripsi jaringan internal dan menuntut tebusan hingga **USD 80 juta**, yang juga ditolak. Insiden ini mengganggu layanan pos internasional selama lebih dari enam minggu, memengaruhi seluruh 11.500 kantor pos di Inggris, membocorkan sekitar 43-45 GB data, dan menyebabkan kerugian sekitar **£10 juta** serta penurunan pendapatan parsel internasional sebesar 6,5%.

### 4. Method, Opportunity, Motive (MOM Framework)
- **Method:** Akses awal melalui RDP, phishing, atau eksploitasi aplikasi publik; diikuti lateral movement, eskalasi privilese, penghapusan shadow copy dan log, serta penyebaran payload enkripsi ke seluruh jaringan.
- **Opportunity:** Kelemahan keamanan organisasi umum (manajemen kredensial lemah, patching tertinggal, akses remote yang tidak terlindungi) memperluas peluang eksploitasi, terutama pada sektor manufaktur, logistik, dan kesehatan.
- **Motive:** Motif utama adalah finansial melalui ekstorsi ganda (*double extortion*), dengan motif sekunder berupa pemeliharaan reputasi dan pembuktian kapabilitas teknis di komunitas kriminal.

### 5. Hasil Demonstrasi Forensik
- **Infeksi Berhasil Dieksekusi:** Sampel LockBit 3.0 berhasil mengenkripsi seluruh file dummy, mengubah ekstensi dan isi file menjadi data acak (gibberish), serta mengubah wallpaper desktop menjadi tampilan "LockBit Black" dengan pesan ancaman.
- **Ransom Note:** File `fu28x4MDV.README.txt` dibuat secara otomatis berisi instruksi pembayaran tebusan dan tautan Tor untuk negosiasi.
- **Aktivitas Sistem Tinggi:** Penggunaan CPU mencapai 100% dengan I/O disk yang signifikan (puluhan ribu *read/write operations*, hingga 1,4 GB *write bytes*), mengindikasikan proses enkripsi aktif berskala besar.
- **Upaya Persistence:** Autoruns mendeteksi entri startup registry yang mencurigakan, meskipun beberapa gagal dieksekusi karena file rujukan tidak ditemukan—mengindikasikan upaya persistence yang tidak sepenuhnya berhasil dalam konteks lab ini.
- **Anti-Analisis Terkonfirmasi:** Ketika dijalankan di sandbox Any.run, sampel menunjukkan indikasi aktivitas berbahaya namun tidak berjalan sepenuhnya sesuai perilaku yang diamati di VM lokal—mengonfirmasi adanya mekanisme deteksi sandbox/anti-VM pada LockBit 3.0.

### 6. Rekomendasi Mitigasi
Laporan merekomendasikan: backup data offline secara berkala, konfigurasi Volume Shadow Copy Service (VSS) yang benar, patching rutin, penerapan prinsip *least privilege* dan segmentasi jaringan, serta penggunaan log analysis, endpoint monitoring, dan intrusion detection untuk deteksi dini.

---

## ⚠️ Limitations

- **Tidak Ada Eksperimen pada Tahap Akses Awal atau Eksfiltrasi:** Analisis hanya mencakup tahap eksekusi/impact (enkripsi, ransom note, perubahan sistem); tahap initial access, lateral movement, dan eksfiltrasi data tidak diuji secara teknis, hanya dibahas secara naratif berdasarkan laporan pihak ketiga.
- **Eksekusi Tidak Sepenuhnya Sempurna:** Mekanisme anti-analisis LockBit menyebabkan beberapa fungsi (terutama di sandbox Any.run) tidak berjalan sebagaimana mestinya, sehingga sebagian perilaku malware (misalnya manipulasi layanan backup/recovery) tidak teramati.
- **Sampel Tunggal:** Analisis hanya menggunakan satu sampel malware; generalisasi terhadap seluruh varian LockBit 3.0 atau afiliasi lain memiliki keterbatasan.
- **Tidak Ada Analisis Ekosistem atau Tata Kelola:** Laporan ini sama sekali tidak membahas struktur organisasi RaaS, mekanisme vetting afiliasi, dinamika bagi hasil secara empiris (di luar angka 20-30% yang dikutip dari sumber sekunder), atau peran IAB sebagai entitas mandiri.
- **Ketergantungan pada Sumber Sekunder untuk Studi Kasus:** Studi kasus Boeing dan Royal Mail bersumber dari laporan media/investigatif, bukan dokumen primer (misalnya transkrip negosiasi atau data on-chain), sehingga validitasnya bergantung pada akurasi pelaporan pihak ketiga.
- **Venue Non-Akademik:** Laporan ini tidak melalui proses peer-review formal dan tampaknya merupakan laporan riset independen/tugas akhir teknis, sehingga kredibilitas metodologisnya berada di bawah standar jurnal akademik atau preprint yang terindeks.

---

## 🔗 Related Papers & Concepts

- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks ekosistem RaaS dan studi kasus Colonial Pipeline yang melengkapi studi kasus Boeing dan Royal Mail dalam laporan ini; keduanya sama-sama bersifat *entry-level* dan deskriptif.
- [[Iwasaki & Masaki 2025 - Banning ransomware payments]] — Membangun di atas fondasi Laszka et al. untuk menganalisis dampak kebijakan pelarangan pembayaran tebusan; secara eksplisit mengutip paper ini sebagai referensi utama.
- [[Gray et al. 2023 - Money Over Morals]] — Memberikan analisis empiris struktur organisasi dan bagi hasil RaaS (Conti) yang jauh lebih dalam dibanding angka 20-30% yang dikutip Bhattarai dari Trend Micro tanpa verifikasi independen.
- [[Dhawan et al. 2025 - Splitting the Spoils]] — Menyediakan data on-chain tentang rasio bagi hasil RaaS secara industri-luas (85:15 afiliasi:developer), yang dapat digunakan untuk mengkontekstualisasikan klaim 20-30% pada laporan ini—menunjukkan adanya variasi rasio antar sumber yang perlu dikritisi.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Menjelaskan secara teknis mengapa *concept drift* dan modularitas kode menjadi strategi bertahan RaaS; relevan untuk mengonfirmasi temuan anti-analisis/anti-VM pada LockBit 3.0 dalam laporan ini.
- [[Qollakaj et al. 2023 - Cybersecurity of remote work migration]] — Memetakan TTPs initial access broker dan eksploitasi VPN/RDP yang menjadi prasyarat bagi tahap eksekusi payload LockBit yang didemonstrasikan dalam laporan ini.
- [[LockBit Ransomware Analysis]]
- [[MITRE ATT&CK - Ransomware]]
- [[Double Extortion Tactics]]
- [[Anti-Analysis and Anti-Sandbox Techniques]]
- [[Colonial Pipeline Attack]]

### Key References dari Laporan Ini
- Felipe Castaño et al. (2025) — *Inside LockBit: Technical, Behavioral, and Financial Anatomy of a Ransomware Empire* (arXiv) — kemungkinan sumber data finansial dan model bagi hasil yang lebih rinci dan layak ditelusuri lebih lanjut.
- Trend Micro (2025) — Sumber klaim rasio bagi hasil 20-30% untuk operator LockBit.
- MITRE ATT&CK (2023) — Pemetaan teknik T1190, T1566, T1078, dan lain-lain untuk LockBit.
- Oladipupo Akinyemi et al. (2023) — Analisis LockBit 3.0 dalam insiden NHS/Advanced (Cornell University) — relevan untuk studi kasus sektor kesehatan.
- World Economic Forum (2024) — Liputan Operation Cronos yang menumbangkan infrastruktur LockBit.
- Per Håkon Meland et al. (2020) — *The Ransomware-as-a-Service economy within the darknet* (Computers & Security) — kemungkinan sumber akademik yang relevan untuk argumen ekosistem RaaS.

---

## 💡 My Notes

### Relevansi terhadap RQ1 (Perbedaan RaaS vs. Ransomware Konvensional)
Kontribusi laporan ini terhadap RQ1 bersifat **ilustratif, bukan analitis**. Narasi evolusi LockBit 1.0 → 2.0 → 3.0 memberikan contoh konkret tentang bagaimana model RaaS memungkinkan iterasi cepat fitur (double extortion, anti-analysis, kustomisasi afiliasi)—sebuah pola yang sejalan dengan argumen *concept drift* pada Fachkha et al. (2025). Namun, angka bagi hasil 20-30% yang dikutip tidak divalidasi secara independen dan **berbeda signifikan** dari temuan empiris Dhawan et al. (2025) yang melaporkan rasio rata-rata 85:15 (afiliasi:developer). Perbedaan ini perlu dicatat sebagai potensi *research gap* atau setidaknya catatan kehati-hatian: sumber-sumber industri (Trend Micro) mungkin menggunakan definisi "bagi hasil" yang berbeda (misalnya biaya lisensi vs. potongan langsung dari tebusan) dibanding studi on-chain.

### Relevansi terhadap RQ2 (Ekosistem Aktor dan Interaksi)
Laporan ini **tidak menambah substansi baru** untuk RQ2. Tidak ada pembahasan tentang interaksi developer-afiliasi-IAB secara terstruktur; istilah "afiliasi" hanya disebut sebagai pelaksana lapangan tanpa analisis hubungan organisasional. Studi kasus Boeing dan Royal Mail dapat digunakan sebagai *ilustrasi dampak* dalam pendahuluan, tetapi tidak memberikan wawasan ekosistem sebagaimana Gray et al. (2023) atau Milenkoski et al. (2025).

### Relevansi terhadap RQ3 (Mekanisme Vetting dan Selektivitas)
**Tidak relevan secara langsung.** Tidak ada pembahasan mekanisme vetting, rekrutmen, atau norma operasional afiliasi LockBit dalam laporan ini.

### Posisi Laporan dalam Galeri Literatur
Laporan Bhattarai berfungsi sebagai **bukti forensik pendukung tingkat teknis-rendah** (low-level technical evidence) yang dapat memperkuat argumen tentang *bagaimana payload RaaS bekerja secara nyata* di endpoint korban—melengkapi gambaran ekonomi-organisasional dari Gray et al. dan Dhawan et al. dengan "jejak digital" konkret (registry artifacts, proses, perilaku enkripsi). Penggunaannya paling tepat sebagai **referensi singkat pada bagian latar belakang teknis** (misalnya untuk menjelaskan secara konkret apa yang dimaksud "double extortion" atau "anti-analysis techniques" pada level malware), bukan sebagai sumber utama untuk menjawab RQ inti program riset.

### Catatan Kritis tentang Validitas Data
Beberapa klaim kuantitatif dalam laporan (rasio bagi hasil 20-30%, tuntutan tebusan Boeing/Royal Mail) bersumber dari laporan media dan vendor tanpa cross-check terhadap data primer. Saat mensitasi laporan ini dalam paper utama, sebaiknya angka-angka tersebut diperlakukan sebagai *klaim industri* (perlu dibandingkan dengan Dhawan et al. dan Gray et al. yang berbasis data on-chain), bukan sebagai fakta yang telah divalidasi secara independen.

### Potensi Penggunaan dalam Paper
- **Untuk ilustrasi double extortion:** Studi kasus Boeing dan Royal Mail dapat digunakan sebagai contoh konkret dampak *double extortion* terhadap infrastruktur kritis di bagian pendahuluan.
- **Untuk ilustrasi anti-analysis sebagai strategi bertahan:** Temuan bahwa sampel LockBit gagal berjalan penuh di sandbox Any.run dapat digunakan sebagai bukti pendukung argumen Fachkha et al. (2025) tentang *concept drift* dan evasi sebagai strategi inheren ekosistem RaaS—meskipun perlu diparafrase, bukan dikutip langsung.
- **Untuk evolusi teknis LockBit:** Tabel evolusi LockBit 1.0–3.0 dapat menjadi referensi singkat saat menjelaskan bagaimana platform RaaS terus diperbarui oleh developer untuk menjaga daya tarik bagi afiliasi.

---

## 🏷️ Keywords

#lockbit #raas #ransomware #malware-analysis #digital-forensics #case-study #double-extortion #anti-analysis #anti-vm #persistence #mitre-attack #boeing #royal-mail #citrix-bleed #process-monitor #regshot #autoruns #any-run #lockbit3 #bhattarai2025
