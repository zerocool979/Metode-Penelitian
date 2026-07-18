---
title: "AI-Based Ransomware Detection: A Comprehensive Review"
authors:
  - Ferdous, Jannatul
  - Islam, Rafiqul
  - Mahboubi, Arash
  - Islam, Md Zahidul
year: 2024
venue: IEEE Access
volume: Vol. 12
pages: 136666–136695
doi: https://doi.org/10.1109/ACCESS.2024.3461965
url: https://ieeexplore.ieee.org/document/10681571
affiliation:
  - Charles Sturt University, Wagga Wagga / Albury / Port Macquarie / Bathurst, NSW, Australia
tags:
  - ransomware
  - ai-detection
  - machine-learning
  - deep-learning
  - feature-engineering
  - ransomware-datasets
  - static-analysis
  - dynamic-analysis
  - hybrid-analysis
  - transfer-learning
  - adversarial-ml
  - concept-drift
  - raas
  - survey
rating: 2
status: 🟡 reading
date_reviewed: 2026-06-14
type: journal-article
topic: ransomware-detection
peer_reviewed: false
note: Survey artikel IEEE Access; terindeks Scopus dan IEEE Xplore. Fokus pada sisi deteksi teknis berbasis AI, bukan pada ekosistem atau model bisnis RaaS. Relevansi terhadap program riset utama bersifat peripheral—berguna sebagai latar belakang teknis dan konteks tren ransomware.
---

## 📌 Summary

Paper ini menyajikan tinjauan sistematis (*comprehensive review*) terhadap teknik deteksi ransomware berbasis kecerdasan buatan (AI), mencakup literatur sejak tahun 2017. Kontribusi utamanya adalah pengembangan kerangka evaluasi sistematis (*systematic evaluation framework*) yang menilai setiap komponen model deteksi AI—mulai dari pengumpulan data, pra-pemrosesan, ekstraksi fitur, seleksi fitur, pelatihan model, hingga evaluasi kinerja—terhadap strategi serangan ransomware yang spesifik. Paper ini juga mengidentifikasi tren ransomware terkini (termasuk RaaS, IAB, dan *double/triple extortion*) serta menunjukkan arah riset masa depan seperti *transfer learning*, *adversarial ML*, dan deteksi *real-time*.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Metode deteksi ransomware konvensional (berbasis *signature* dan *rule-based*) semakin tidak efektif menghadapi ransomware modern yang bersifat polimorfik, menggunakan teknik *obfuscation*, dan terus berevolusi. Meskipun AI menawarkan solusi yang lebih adaptif, literatur yang ada belum secara eksplisit menghubungkan metode deteksi dengan strategi serangan spesifik yang dilawan.
- **Gap yang diisi:** Survei sebelumnya membahas ransomware secara umum (taksonomi, evolusi, mitigasi) namun tidak menyediakan kerangka evaluasi yang memetakan relasi antara *tipe serangan*, *algoritma AI*, dan *hasil deteksi* secara terstruktur. Paper ini mengisi gap tersebut dengan membangun matriks "Attack–Algorithm–Result" yang komprehensif (Tabel 7).
- **Signifikansi:** Volume serangan ransomware meningkat 73% dalam satu tahun (Q1 2024); biaya kejahatan siber diproyeksikan mencapai $10,5 triliun pada 2025. Memahami efektivitas relatif berbagai pendekatan AI menjadi krusial untuk pengembangan pertahanan yang lebih tangguh.

---

## 🎯 Contribution

1. **Kerangka Evaluasi Sistematis (Systematic Evaluation Framework):** Membangun cetak biru penilaian menyeluruh untuk setiap tahap pipeline deteksi ransomware berbasis AI, dari pengumpulan data hingga evaluasi kinerja, dilengkapi kriteria evaluasi per komponen.
2. **Matriks "Attack–Algorithm–Result" (Tabel 7):** Menganalisis dan memetakan korelasi antara tipe serangan ransomware spesifik (*crypto*, *zero-day*, *adversarial*, *extortion-based*), algoritma AI yang digunakan, dan hasil kinerja deteksi yang dicapai—sebuah pendekatan yang belum dilakukan survei sebelumnya.
3. **Inventarisasi Dataset Ransomware Publik dan Privat (Tabel 2):** Menyediakan katalog komprehensif sumber data yang tersedia beserta keunggulan, kekurangan, dan URL aksesnya.
4. **Taksonomi Fitur Deteksi (Tabel 3–5):** Mengkategorisasikan fitur-fitur statis, dinamis, dan jaringan yang digunakan dalam literatur, beserta fungsi API Windows yang relevan dan contoh penggunaannya.
5. **Identifikasi Gap Riset dan Arah Masa Depan:** Mengidentifikasi enam area yang kurang diteliti: keselarasan algoritma dengan strategi serangan, pendekatan *hybrid*, analisis memori, robustness terhadap serangan adversarial, *transfer learning*, dan deteksi *real-time*.

---

## ⚙️ Methodology

- **Pendekatan:** Tinjauan literatur sistematis (*systematic literature review*) berbasis kerangka evaluasi multi-komponen.
- **Cakupan Literatur:** Artikel jurnal, prosiding konferensi, dan sumber daring yang diterbitkan sejak 2017 hingga awal 2024; berfokus pada teknik ML dan DL untuk deteksi ransomware.
- **Struktur Analisis:** Setiap paper yang dikaji dievaluasi berdasarkan: (1) tipe serangan yang ditargetkan, (2) fitur yang digunakan (statis/dinamis/jaringan), (3) detail dataset (jumlah keluarga, sampel ransomware, sampel benign), (4) kode/tool yang digunakan, (5) model AI yang diterapkan (ML/DL), dan (6) metrik kinerja (akurasi, presisi, recall, F1-score).
- **Jenis Penelitian:** Deskriptif-analitis; tidak ada eksperimen teknis atau pengujian model baru.
- **Threat Model:** Implisit—mencakup berbagai kategori ransomware (crypto, locker, zero-day, adversarial, extortion-based) dengan berbagai vektor serangan.

### Taksonomi Tipe Ransomware yang Dibahas

| Tipe | Karakteristik Utama |
|------|---------------------|
| Crypto-ransomware | Enkripsi file; paling umum |
| Locker ransomware | Mengunci akses perangkat; relatif ringan |
| Zero-day ransomware | Mengeksploitasi kerentanan yang belum diketahui |
| Adversarial ransomware | Menggunakan teknik ML untuk menghindari deteksi |
| Single extortion | Hanya enkripsi (WannaCry, CryptoLocker) |
| Double extortion | Enkripsi + ancaman publikasi data |
| Triple extortion | Double + DDoS terhadap server korban |
| Quadruple extortion | Triple + menyerang pihak ketiga terkait |

---

## 📊 Key Results

### 1. Tren Ransomware yang Relevan dengan Konteks RaaS

Paper ini secara eksplisit mengidentifikasi **RaaS sebagai Tren #1** dalam lanskap ransomware kontemporer: model bisnis di mana developer ransomware menyewakan perangkat lunak mereka kepada afiliasi dengan imbalan persentase tebusan. Hal ini menurunkan *barrier to entry* secara signifikan. Tren pendamping yang relevan meliputi:
- **Initial Access Brokers (IABs)** sebagai Tren #4: entitas yang menjual akses jaringan perusahaan di forum underground, dicontohkan oleh DarkSide yang mengiklankan akses ke perusahaan AS beromzet di atas $400 juta.
- **Teknik extortion berlapis** sebagai Tren #2: evolusi dari enkripsi tunggal menuju *double*, *triple*, dan *quadruple extortion*.
- **Rust-based ransomware** sebagai Tren #5: penggunaan bahasa pemrograman modern (BlackCat/ALPHV) untuk meningkatkan kompleksitas dan menghindari deteksi.

### 2. Performa Model AI dalam Matriks "Attack–Algorithm–Result"

Dari analisis Tabel 7, diperoleh temuan komparatif kunci:
- Untuk **crypto-ransomware**: CNN-LSTM mencapai F1-score tertinggi (99,87), mengungguli SVM tradisional (96,7) dan SA-CNN (93,34). Model *ensemble* dan DL secara konsisten mengungguli pendekatan ML tunggal.
- Untuk **zero-day ransomware**: *Ensemble soft voting* (LR + RF + XGB) mencapai F1-score 96,41—menunjukkan bahwa kombinasi model lebih efektif untuk varian yang belum pernah terlihat.
- Untuk **adversarial attacks**: pendekatan *transfer learning* mencapai F1-score tertinggi (99), diikuti TGAN (98,7)—menunjukkan keunggulan model yang telah dilatih pada dataset besar untuk menghadapi manipulasi input.

### 3. Keunggulan Fitur Hibrida (Statis + Dinamis)

Studi-studi yang mengombinasikan fitur statis dan dinamis (misalnya SwiftR, RansHunt, RansomWall) secara konsisten menunjukkan performa lebih tinggi dan generalisasi yang lebih baik lintas keluarga ransomware dibanding pendekatan unimodal. Ini mencerminkan kebutuhan akan analisis multi-dimensi yang mencerminkan perilaku ransomware yang kompleks.

### 4. Tantangan Concept Drift

Paper ini secara eksplisit mengakui *concept drift* sebagai tantangan kritis: model DL berbasis ransomware menjadi kurang efektif dari waktu ke waktu karena ketidakmampuan mendeteksi perubahan data dan perilaku ransomware baru. Dataset yang kedaluwarsa (seperti Microsoft BIG 2015 dan Malimg 2011) memperparah masalah ini. Temuan ini berkorespondensi langsung dengan argumen Fachkha et al. (2025) bahwa *concept drift* adalah strategi bertahan inheren dalam model RaaS.

### 5. Ringkasan Statistik Kinerja Model AI

| Tipe Serangan | Algoritma Terbaik | F1-Score Tertinggi |
|---------------|-------------------|-------------------|
| Crypto-ransomware | CNN-LSTM | 99,87 |
| Zero-day | Ensemble (LR+RF+XGB) | 96,41 |
| Adversarial | Transfer Learning (CNN) | 99,00 |
| Extortion-based | CNN (berbasis perilaku) | 94,92 |

---

## 🏛️ Systematic Evaluation Framework — Komponen Utama

| Tahap | Kriteria Evaluasi Kunci |
|-------|------------------------|
| **Pengumpulan Data** | Keberagaman dataset, ukuran sampel, kemutakhiran, kemampuan benchmarking |
| **Analisis Data** | Statis (PE file), Dinamis (sandboxing), Hybrid |
| **Pra-pemrosesan** | Pembersihan data, integrasi, transformasi, reduksi, encoding kategorikal |
| **Ekstraksi Fitur** | Relevansi, skalabilitas, interpretabilitas |
| **Seleksi Fitur** | Fokus pada fitur kritis, reduksi redundansi, efisiensi komputasi |
| **Deteksi AI** | Performa terhadap tipe serangan spesifik (bukan hanya akurasi agregat) |
| **Evaluasi** | Akurasi, presisi, recall, F1-score; K-fold, train-test split, adversarial testing |

---

## ⚠️ Limitations

- **Tidak Ada Eksperimen Original:** Seluruh analisis berbasis tinjauan literatur sekunder; tidak ada model baru yang diuji atau dataset baru yang dibuat.
- **Fokus Teknis Sempit:** Paper ini secara eksklusif membahas deteksi berbasis AI dari perspektif teknis komputasional. Tidak ada pembahasan tentang struktur ekonomi, model bisnis, atau ekosistem sosial RaaS.
- **Absensi Analisis Aktor:** RaaS disebutkan hanya sebagai "tren" (2 paragraf), tanpa analisis mendalam tentang pembagian peran developer–afiliasi–IAB, mekanisme bagi hasil, atau dinamika vetting.
- **Dataset Terbatas pada Windows:** Sebagian besar dataset dan teknik analisis berfokus pada platform Windows (misalnya analisis PE file); keterwakilan platform lain (Linux, macOS, cloud) sangat terbatas.
- **Temporal Gap:** Beberapa dataset referensi yang dianalisis sudah kedaluwarsa (Microsoft BIG 2015, Malimg 2011), yang melemahkan validitas komparatif beberapa temuan.
- **Bias Venue Publikasi:** Meskipun diterbitkan di IEEE Access (terindeks Scopus), beberapa referensi yang dikutip berasal dari sumber berkualitas rendah atau tidak terverifikasi secara akademis.

---

## 🔗 Related Papers & Concepts

- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Memberikan penjelasan mekanistis mengapa deteksi AI berbasis *signature* dan *supervised ML* menjadi cepat usang: *concept drift* adalah bagian inheren dari strategi adaptasi RaaS, bukan sekadar anomali teknis. Paper Ferdous et al. mengkonfirmasi tantangan ini dari sisi riset deteksi.
- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks operasional untuk tren-tren yang diidentifikasi Ferdous et al. (RaaS, IAB, double extortion), tetapi dengan kedalaman analisis ekosistem yang jauh lebih kaya.
- [[Gray et al. 2023 - Money Over Morals]] — Menyediakan bukti empiris bahwa kompleksitas organisasi RaaS (yang hanya disinggung singkat dalam paper ini) adalah alasan mendasar mengapa model deteksi AI menghadapi tantangan konsistensi.
- [[Dhawan et al. 2025 - Splitting the Spoils]] — Menjelaskan mekanisme ekonomi di balik proliferasi afiliasi RaaS yang secara langsung menghasilkan diversitas varian ransomware yang menjadi beban utama bagi sistem deteksi AI.
- [[Concept Drift in Malware Detection]]
- [[Adversarial Machine Learning for Ransomware]]
- [[Transfer Learning in Cybersecurity]]
- [[Ransomware Dataset Benchmarking]]

### Key References dari Paper Ini
- Al-Rimy et al. (2018) — Taksonomi dan *countermeasures* ransomware; salah satu survei paling sering dikutip dalam domain ini.
- Beaman et al. (2021) — Analisis mutakhir (*state-of-the-art*) ransomware: deteksi, analisis, dan pencegahan.
- Razaulla et al. (2023) — Survei evolusi ransomware, taksonomi, dan arah riset dari tim yang sama dengan Fachkha et al.
- Oz et al. (2022) — Tinjauan komprehensif evolusi ransomware dan solusi pertahanan (ACM Computing Surveys).
- Sgandurra et al. (2016) — EldeRan: framework analisis dan deteksi ransomware dinamis; dataset yang masih banyak digunakan hingga kini.
- Gray et al. (2022) — Disebut sebagai referensi background untuk analisis bisnis Conti.

---

## 💡 My Notes

### Relevansi terhadap RQ1 (Perbedaan RaaS vs. Ransomware Konvensional)
Paper ini **tidak langsung menjawab RQ1**, namun berkontribusi pada kontekstualisasinya dari sudut pandang pertahanan. Fakta bahwa ransomware modern memerlukan pendekatan deteksi yang jauh lebih kompleks (DL, *ensemble*, *transfer learning*) dibanding signature tradisional secara implisit mengkonfirmasi bahwa ransomware modern—yang didominasi model RaaS—telah menjadi jauh lebih canggih dan adaptif. Angka-angka konkret di paper ini (73% peningkatan serangan dalam setahun, LockBit mendominasi 23% serangan Q1 2024) dapat digunakan untuk membuka bagian urgensi penelitian pada RQ1.

### Relevansi terhadap RQ2 (Ekosistem Aktor dan Interaksi)
Kontribusi minimal namun tidak nol. Identifikasi **RaaS dan IAB sebagai tren dominan** (Bagian II.E) memberikan konfirmasi dari perspektif komunitas keamanan teknis bahwa kedua entitas ini adalah aktor yang diakui secara luas. Contoh konkret DarkSide sebagai RaaS provider dan IAB yang menjual akses ke perusahaan AS di forum underground dapat digunakan sebagai ilustrasi singkat dalam pembahasan RQ2. Namun, untuk kedalaman analisis ekosistem, paper ini harus dikombinasikan dengan Gray et al. (2023) dan Dhawan et al. (2025).

### Relevansi terhadap RQ3 (Mekanisme Vetting dan Selektivitas)
**Tidak relevan secara langsung.** Paper ini tidak membahas mekanisme vetting afiliasi, selektivitas target, atau norma-norma operasional ekosistem RaaS sama sekali.

### Posisi Paper dalam Galeri Literatur
Paper Ferdous et al. (2024) berfungsi sebagai **latar belakang teknis** yang mengkonfirmasi "mengapa masalah ini sulit dipecahkan dari sisi pertahanan"—bukan sebagai sumber utama untuk menjawab RQ program riset utama. Penggunaannya paling tepat di bagian **pendahuluan atau latar belakang** untuk menunjukkan bahwa komunitas keamanan teknis telah mengakui kompleksitas ransomware modern, sehingga analisis dari sisi ekosistem dan tata kelola (yang menjadi fokus program riset utama) menjadi semakin penting.

---

## 🏷️ Keywords

#ransomware #ai-detection #machine-learning #deep-learning #feature-engineering #ransomware-datasets #static-analysis #dynamic-analysis #hybrid-analysis #transfer-learning #adversarial-ml #concept-drift #raas #survey #ieee-access #systematic-review #attack-algorithm-result #pe-file-analysis #ensemble-learning #real-time-detection #ferdous2024 #cnn-lstm #zero-day #extortion #lockbit #initial-access-broker
