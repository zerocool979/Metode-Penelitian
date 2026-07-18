---
title: "Splitting the Spoils: The Economics of Ransomware as a Service"
authors:
  - Dhawan, Anirudh
  - Foley, Sean
  - Mollica, Vito
year: 2025
venue: SSRN Preprint (Working Paper)
volume: "-"
pages: "-"
doi: https://ssrn.com/abstract=5713117
url: https://ssrn.com/abstract=5713117
affiliation:
  - Indian Institute of Management Bangalore (Dhawan)
  - Macquarie University (Foley & Mollica)
tags:
  - raas
  - ransomware
  - blockchain-forensics
  - bitcoin
  - revenue-sharing
  - security-economics
  - cybercrime-industry
  - affiliate-model
  - negotiation-analysis
  - big-game-hunting
  - double-extortion
  - cryptocurrency
  - on-chain-analysis
rating: 5
status: 🟡 reading
date_reviewed: 2026-05-20
type: working-paper
topic: ransomware-economics
peer_reviewed: false
note: "Preprint; belum melewati peer review formal per Oktober 2025. Konferensi: Forensic Finance Conference."
---

## 📌 Summary

Paper ini menyajikan bukti empiris pertama berbasis data *on-chain* Bitcoin dalam skala industri untuk membuktikan bahwa model Ransomware-as-a-Service (RaaS) telah diadopsi secara luas—bukan hanya oleh beberapa keluarga ransomware tertentu—dan bahwa mekanisme bagi hasil (*revenue sharing*) antara developer dan afiliasi berjalan secara konsisten dengan rasio rata-rata 85:15. Dengan mengombinasikan analisis transaksi blockchain, analisis transkip negosiasi berbantuan LLM (GPT-4.1), dan regresi panel, paper ini membuktikan bahwa RaaS telah mentransformasi ransomware dari kejahatan sporadis menjadi industri semi-formal yang tumbuh secara eksponensial.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Pertumbuhan pesat ransomware pasca-2018 belum sepenuhnya dapat dijelaskan oleh faktor teknis semata. Diperlukan pemahaman tentang struktur ekonomi dan organisasional yang memungkinkan industri ini tumbuh secara sistemik dan berskala besar.
- **Gap yang diisi:** Studi sebelumnya (Gray et al., 2022; Cong et al., 2025) hanya mendokumentasikan mekanisme bagi hasil di *satu* keluarga RaaS spesifik (Conti dan DarkSide secara terpisah). Tidak ada studi yang mengkonfirmasi apakah pola ini merupakan praktik *industri-luas* atau sekadar perilaku satu-dua aktor. Paper ini mengisi gap tersebut dengan menganalisis seluruh ekosistem secara komparatif menggunakan data blockchain dari 17 keluarga RaaS dan 57 keluarga *commodity ransomware*.
- **Signifikansi:** Jika RaaS adalah praktik industri-luas (bukan anomali), maka regulator menghadapi ancaman yang jauh lebih terstruktur dan resisten terhadap pendekatan penegakan hukum konvensional, karena model bisnisnya mampu beradaptasi, menarik rekrutmen afiliasi, dan tumbuh secara eksponensial seiring usia dan reputasi.

---

## 🎯 Contribution

1. **Bukti On-Chain Industri-Luas untuk Model Bagi Hasil RaaS:** Membuktikan secara empiris—pertama kali menggunakan seluruh universe transaksi Bitcoin—bahwa mekanisme *ransom splitting* adalah praktik yang diadopsi secara konsisten oleh keluarga RaaS, bukan fenomena satu atau dua aktor.
2. **Kuantifikasi Rasio Bagi Hasil (85:15):** Mendokumentasikan bahwa afiliasi (*hacker*) menerima rata-rata 85% dari total tebusan, sementara developer (*ransomware family*) mengambil 15% sebagai biaya lisensi atas perangkat lunaknya.
3. **Analisis Pertumbuhan Eksponensial RaaS vs. Pertumbuhan Negatif-Eksponensial *Commodity Ransomware*:** Membuktikan secara kuantitatif bahwa model RaaS menghasilkan pertumbuhan pendapatan yang eksponensial seiring usia keluarga ransomware, sementara *commodity ransomware* memuncak di tahun pertama lalu menurun.
4. **Analisis Negosiasi Berbasis LLM:** Pertama kali menerapkan LLM (GPT-4.1) secara sistematis pada 215 transkrip negosiasi ransomware untuk mendokumentasikan fitur-fitur organisasional dan retorika aktor RaaS.
5. **Analisis Korelasi Bitcoin dan Aktivitas Ransomware:** Mengkuantifikasi hubungan *co-evolutionary* antara volatilitas dan tingkat kongesti Bitcoin dengan volume dan struktur pembayaran ransomware menggunakan model Vector Error Correction (VECM).

---

## ⚙️ Methodology

- **Pendekatan:** Studi empiris kuantitatif multimetode yang mengombinasikan analisis *on-chain* blockchain, regresi panel (*cluster-level*), regresi deret waktu (VECM), dan analisis teks berbantuan LLM.

### Sumber Data & Sampel

| Komponen Data | Detail |
|---|---|
| **Alamat Dompet Ransomware** | 7.693 alamat dari dataset Ransomwhere (crowdsourced + sumber industri); 7.507 alamat RaaS dan 186 alamat *commodity ransomware* |
| **Klasifikasi Keluarga** | 17 keluarga RaaS, 57 keluarga *commodity ransomware* berdasarkan laporan industri dan penegakan hukum |
| **Periode Blockchain** | 18 Oktober 2013 – 16 Juni 2022 (Blok terakhir: #741,050) |
| **Algoritma Clustering** | Heuristik *multiple-input clustering* (Meiklejohn et al., 2016; Ron & Shamir, 2013); menghasilkan 150 kluster RaaS dan 138 kluster *commodity ransomware* |
| **Transkip Negosiasi** | 215 sesi negosiasi dari 20 keluarga ransomware (2020–2025); dari Ransomchats (GitHub) dan data LockBit yang bocor (Mei 2025) |
| **Data Bitcoin** | Harga, volatilitas, dan waktu konfirmasi transaksi dari Blockchain.com dan WalletExplorer.com |

### Struktur Analisis

- **Analisis On-Chain:** Inspeksi pola transaksi *outgoing* (jumlah alamat penerima, persentase bagi hasil) untuk mendeteksi mekanisme *ransom splitting*.
- **Regresi Cluster-Level:** Variabel dependen: ukuran tebusan (*size*), frekuensi serangan (*ransoms*), usia kluster, dll. Variabel independen utama: dummy RaaS.
- **Regresi Usia-Pendapatan:** Menguji interaksi antara `RaaS × Age` terhadap total pendapatan tebusan.
- **VECM:** Menguji hubungan jangka pendek antara karakteristik Bitcoin (volatilitas mingguan, waktu konfirmasi transaksi) dengan aktivitas ransomware, setelah mengontrol kointegrasi jangka panjang (Johansen test).
- **Analisis Negosiasi (LLM):** GPT-4.1 digunakan untuk menjawab serangkaian pertanyaan terstruktur pada setiap transkrip di empat tema: *setup* organisasional penyerang, sikap penyerang, sikap korban, dan detail negosiasi.

### Threat Model
Model mengasumsikan dua tipe pelaku terpisah: (1) *ransomware family* (developer) yang menciptakan perangkat lunak dan mengoperasikan infrastruktur, dan (2) *affiliate* (hacker) yang menyusup ke sistem korban dan menanam ransomware. Keduanya terikat oleh kesepakatan implisit yang ditopang reputasi, bukan kontrak legal.

---

## 📊 Key Results

### 1. Bukti On-Chain: Mekanisme *Ransom Splitting* adalah Praktik Industri

Lebih dari 85% alamat Bitcoin RaaS mengirimkan dana keluar (*outgoing*) ke **tepat dua alamat penerima**, berbanding ~50% pada *commodity ransomware*. Proporsi transaksi *outgoing* dengan dua tujuan pada RaaS adalah **29% lebih tinggi** dari *commodity ransomware* (signifikan pada level 1%). Rata-rata persentase bagi hasil pada transaksi dua-tujuan RaaS berkisar 60%–90%, terkonsentrasi di kisaran 80–85%, yang konsisten dengan model bagi hasil. Ini berbeda tajam dengan *commodity ransomware* yang mendekati 100% (tidak ada pembagian).

**Rasio bagi hasil rata-rata: Afiliasi 85% — Developer 15%.**

Heterogenitas antar keluarga ada: NetWalker (85:15), Conti (75:25), REvil (90:10), DarkSide (~93:7).

### 2. Skala Ekonomi: RaaS vs. *Commodity Ransomware*

Dari September 2010 hingga Juni 2022, total pendapatan ransomware mencapai minimal 32.447 BTC (~$170 juta). Meskipun keluarga RaaS hanya mencatat 60% dari jumlah transaksi masuk, mereka menerima **>90% dari total nilai tebusan** (~$153 juta). Rata-rata tebusan per serangan: RaaS **$14.580**, vs. *commodity ransomware* **$2.470** (selisih ~6×).

### 3. Pergeseran Paradigma Ransomware Pasca-2020

Volume harian ransomware rata-rata hanya **$22.500 hingga akhir 2019**, lalu melonjak **~15×** menjadi rata-rata **$332.500 pasca-2020**. Bersamaan dengan itu, terjadi pergeseran struktural dari model *high-volume, low-value* (banyak serangan kecil) menjadi *low-volume, high-value* (sedikit serangan, tebusan sangat besar). Kontribusi akselerator: pandemi COVID-19 yang memaksa perpindahan ke *remote work* dengan kontrol keamanan yang lemah, serta adopsi taktik *double extortion*.

### 4. Pertumbuhan Eksponensial Berbasis Reputasi

Keluarga RaaS menunjukkan pertumbuhan tebusan rata-rata yang **hampir eksponensial** seiring usia: dari $4.000–$65.000 pada 3 tahun pertama hingga ~$500.000 pada tahun ke-3 dan ke-4. Regresi interaksi `RaaS × Age` signifikan positif: setiap pertambahan usia 1 bulan, total pendapatan tebusan RaaS lebih tinggi **~$43.680** dibanding *commodity ransomware* pada usia yang sama. Sebaliknya, *commodity ransomware* memuncak di tahun pertama dan mengikuti **jalur negatif-eksponensial**.

Mekanisme: reputasi memungkinkan akses ke afiliasi yang lebih kompeten, yang mampu menyusup ke organisasi yang lebih besar untuk mengekstraksi tebusan yang jauh lebih tinggi.

### 5. Fitur Organisasional dari Analisis Negosiasi

Analisis LLM terhadap 215 transkip negosiasi menunjukkan:

| Dimensi                      | Temuan                                                                                                                                                                            |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Struktur Organisasi**      | 197/215 chat mengindikasikan aktor bukan individu; ~120 chat merujuk pada tim internal lain (rata-rata 1,5 tim); 71% chat diselenggarakan melalui kanal "customer support" khusus |
| **Retorika Profesionalisme** | Nada negosiasi: ramah/netral >85% kasus; hostile <15%; 55% kasus menjanjikan *security report* pasca-serangan                                                                     |
| **Rasionalitas Kriminal**    | Penyerang memposisikan diri sebagai "konsultan keamanan siber"—merasionalisasikan serangan sebagai layanan mengekspos kerentanan, bukan pencurian                                 |
| **Dinamika Negosiasi**       | 189/215 chat berisi negosiasi; rata-rata 2,25 *counter-offer*; durasi negosiasi rata-rata 18 hari; diskon rata-rata yang diraih korban: **43%** dari tuntutan awal                |
| **Dampak pada Korban**       | 68 chat menyebut dampak operasional; 113 chat: korban tampak panik; hanya ~6% kasus korban menolak membayar                                                                       |

### 6. Korelasi dengan Karakteristik Bitcoin (VECM)

- **Volatilitas Bitcoin (+) → Aktivitas RaaS (+):** Setelah periode volatilitas Bitcoin tinggi, aktivitas transaksi RaaS meningkat (koefisien VECM positif dan signifikan). Komoditas ransomware tidak sensitif. Interpretasi: RaaS memanfaatkan popularitas Bitcoin yang meningkat untuk memperbesar nilai tebusan riil.
- **Volatilitas Bitcoin (+) → Porsi Afiliasi (+):** Di saat volatilitas tinggi, persentase yang diterima afiliasi naik—mengindikasikan afiliasi menuntut bagi hasil lebih besar atau bermitra dengan developer berbiaya lebih rendah.
- **Kongesti Jaringan Bitcoin (+) → Aktivitas Ransomware (-):** Kedua jenis ransomware mengurangi serangan setelah periode kongesti tinggi. Menariknya, meskipun ransomware sendiri berkontribusi pada kongesti blockchain (Sokolov, 2021), mereka tetap responsif terhadapnya.

### Ringkasan Statistik Kunci

| Metrik | RaaS | *Commodity Ransomware* |
|---|---|---|
| Rata-rata tebusan per serangan | $14.580 | $2.470 |
| Total pendapatan (2010–2022) | ~$153 juta (90%) | ~$17 juta (10%) |
| % transaksi *outgoing* ke 2 tujuan | ~85% alamat | ~50% alamat |
| Sensitivitas harga Bitcoin | Rendah | Tinggi |
| Pola pertumbuhan | Eksponensial | Negatif-eksponensial |
| Usia aktif kluster (rata-rata) | Lebih pendek (-6 bulan) | Lebih panjang |

---

## ⚠️ Limitations

- **Status Preprint:** Paper ini belum melewati proses peer review formal per Oktober 2025. Temuan-temuannya, meskipun metodologinya solid, harus diperlakukan dengan kehati-hatian yang sepadan sebelum publikasi final.
- **Keterbatasan Data Ransomwhere:** Dataset alamat dompet berbasis pelaporan mandiri (*crowdsourced*) oleh korban, sehingga sangat mungkin merupakan *lower bound* dari total aktivitas—banyak serangan yang tidak dilaporkan dan karenanya tidak masuk sampel.
- **Batas Waktu Data On-Chain:** Data blockchain hanya mencakup hingga Juni 2022 (sebelum periode dominasi penuh LockBit 3.0 dan generasi RaaS terbaru). Tren pasca-2022 tidak tercakup dalam analisis kuantitatif utama.
- **Identifikasi Kausal Keterbatasan:** Pembuktian mekanisme *ransom splitting* berdasarkan pola transaksi dua-tujuan adalah *inference* berbasis observasi perilaku blockchain, bukan konfirmasi langsung dari dokumen internal afiliasi. Tidak dapat dikesampingkan adanya penjelasan alternatif untuk pola transfer dua-tujuan.
- **Absensi IAB (Initial Access Broker):** Model analisis hanya memetakan dua aktor utama (developer dan afiliasi). Peran IAB sebagai aktor mandiri yang menjual akses awal tidak dianalisis secara terpisah dari peran afiliasi, sehingga pemisahan peran ekosistem dalam paper ini masih belum lengkap dibanding kondisi nyata.
- **Rasionalitas Aktor:** Analisis negosiasi dengan LLM bergantung pada asumsi bahwa transkip yang tersedia representatif. Transkip yang bocor (khususnya dari LockBit) mungkin tidak mewakili distribusi negosiasi yang sesungguhnya—keluarga dengan negosiasi "bermasalah" atau yang tidak pernah dikompromikan mungkin tidak ada di sampel.
- **Fokus pada Bitcoin:** Analisis *on-chain* hanya mencakup Bitcoin. Beralihnya sebagian keluarga RaaS modern ke mata uang kripto yang lebih anonim seperti Monero atau ZCash membatasi cakupan analisis untuk serangan pasca-2022.

---

## 🔗 Related Papers & Concepts

- [[Laszka et al. 2017 - On the Economics of Ransomware]] — Fondasi teori ekonomi game-theoretic tentang insentif pembayaran tebusan dan investasi backup; paper Dhawan et al. mengkonfirmasi empiris apa yang Laszka modelkan secara teoretis, khususnya bahwa penyerang rasional mengoptimalkan tuntutan tebusan berdasarkan kesediaan bayar korban.
- [[Iwasaki & Masaki 2025 - Banning ransomware payments]] — Argumen Iwasaki tentang *blanket ban* yang mendorong transaksi ke *shadow economy* mendapat dukungan empiris kuat dari temuan Dhawan et al. bahwa mekanisme bagi hasil dan jaringan afiliasi beroperasi penuh di luar jangkauan regulasi formal.
- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks studi kasus operasional (Colonial Pipeline, LockBit) yang komplementer dengan data kuantitatif agregat yang disajikan Dhawan et al.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Menjelaskan mekanisme teknis *concept drift* dan modularitas RaaS yang secara langsung memungkinkan skalabilitas afiliasi yang terdokumentasi dalam paper ini.
- [[RaaS Revenue Sharing Model]]
- [[Bitcoin Blockchain Forensics]]
- [[Big Game Hunting Ransomware Strategy]]
- [[Ransomware Negotiation Dynamics]]
- [[Cybercrime as Industrial Organization]]
- [[Moral Rationalization in Cybercrime]]

### Key References dari Paper Ini

- Gray et al. (2022) — *Money over morals: A business analysis of Conti ransomware* — dokumentasi bagi hasil di Conti (studi kasus tunggal yang diperluas oleh paper ini ke level industri).
- Cong et al. (2025) — *An anatomy of crypto-enabled cybercrimes* (Management Science) — dokumentasi bagi hasil di DarkSide.
- Oosthoek et al. (2023) — *A tale of two markets: Investigating the ransomware payments economy* (CACM) — baseline perbandingan RaaS vs. *commodity ransomware*.
- Paquet-Clouston et al. (2019) — *Ransomware payments in the Bitcoin ecosystem* — metodologi pelacakan Bitcoin sebelumnya (data hingga 2017).
- Sokolov (2021) — *Ransomware activity and blockchain congestion* (JFE) — bukti bahwa ransomware itu sendiri berkontribusi pada kongesti blockchain.
- Meiklejohn et al. (2016) — Algoritma *clustering* heuristik Bitcoin yang diadopsi dalam paper ini.
- Hack & Wu (2021) — *"We wait, because we know you." Inside the ransomware negotiation economics* (NCC Group) — analisis negosiasi awal yang menjadi basis pengembangan analisis LLM dalam paper ini.

---

## 💡 My Notes

### Relevansi terhadap RQ1 (Perbedaan RaaS vs. Ransomware Konvensional)
Ini adalah paper paling kuat untuk menjawab RQ1 secara empiris. Tabel perbandingan antara RaaS dan *commodity ransomware, menyediakan data konkret tentang perbedaan ukuran tebusan, frekuensi serangan, pola pertumbuhan, dan sensitivitas Bitcoin. Tidak ada paper lain dalam vault ini yang menyediakan angka perbandingan sekuat ini. Argumen "RaaS mengubah ransomware dari *high-volume, low-value* menjadi *low-volume, high-value*" adalah poin utama yang harus masuk ke bagian pendahuluan dan analisis RQ1.

### Relevansi terhadap RQ2 (Ekosistem Aktor dan Interaksi)
Temuan rasio 85:15 adalah **angka konkret terbaik** yang tersedia dalam literatur untuk menggambarkan mekanisme distribusi peran dan insentif antara developer dan afiliasi. Ini bisa menjadi "anchor data" dalam penjelasan ekosistem di bab metodologi atau analisis. Penting juga: temuan bahwa blockchain berfungsi sebagai mekanisme *enforcement* informal (afiliasi bisa *verifikasi sendiri* apakah mereka sudah dibayar dengan benar lewat blockchain publik) adalah insight struktural yang sangat relevan untuk menjelaskan mengapa ekosistem ini bisa beroperasi tanpa kontrak legal.

### Relevansi terhadap RQ3 (Mekanisme Vetting dan Selektivitas)
Paper ini tidak membahas mekanisme *vetting* secara langsung, tetapi temuan tentang bagaimana **reputasi** mendorong pertumbuhan eksponensial dan bagaimana keluarga RaaS menjaga *social contract* dengan afiliasi memberikan fondasi untuk argumen bahwa selektivitas afiliasi bukan hanya soal motif finansial, tetapi juga tentang membangun ekosistem reputasional yang sustain. Hubungkan dengan catatan Fachkha (Conti leak menunjukkan adanya recruitment & specialization) untuk membangun argumen RQ3.

### Catatan Kritis: Ketidakhadiran IAB
Kelemahan struktural terbesar paper ini untuk agenda riset kita adalah **tidak dipisahkannya peran IAB dari peran afiliasi**. Dalam analisis mereka, "affiliate" dan "hacker" diperlakukan sebagai satu aktor yang sama, padahal dalam ekosistem RaaS modern, IAB (yang menjual *initial access*) dan operator serangan aktif bisa merupakan entitas yang sama sekali berbeda. Ini bisa menjadi *research gap* yang kita kritisi secara eksplisit: "Dhawan et al. membuktikan mekanisme bagi hasil dua pihak, namun model dua-aktor ini mengabaikan lapisan ketiga IAB yang semakin mandiri dalam ekosistem RaaS kontemporer."

### Catatan Metodologis
Penggunaan GPT-4.1 untuk analisis negosiasi adalah inovasi metodologis yang signifikan tetapi juga rentan terhadap *prompt-induced bias*. Pertanyaan-pertanyaan yang diajukan bersifat *leading* dalam beberapa hal (misal: "Does the attacker appear to be friendly or hostile or neutral?"—kategori ini sudah mengarahkan ke framing tertentu). Dalam literature review, ini bisa dicatat sebagai limitasi metodologis yang perlu diakui, tetapi tidak mengurangi validitas pola besar yang ditemukan.

### Potensi Kutipan Unggulan
- **Untuk definisi RaaS:** "Unlike traditional *commodity* ransomware—where a single operator both develops malware and launches attacks—RaaS separates these functions. Specialized developers create ransomware strains and 'lease' them to affiliates who infiltrate victims' systems."
- **Untuk argumen bagi hasil:** Angka 85:15 dan fakta bahwa rasio ini dapat diverifikasi publik lewat blockchain adalah argumen yang sangat kuat untuk menggambarkan *quasi-contractual governance* tanpa hukum formal.
- **Untuk argumen pertumbuhan:** Transformasi dari $22.500/hari (pra-2020) menjadi $332.500/hari (pasca-2020)—lonjakan 15× dalam 1 tahun—adalah statistik yang sangat efektif untuk membuka bagian urgensi penelitian.

---

## 🏷️ Keywords

#raas #ransomware #blockchain-forensics #bitcoin #revenue-sharing #security-economics #cybercrime-industry #affiliate-model #negotiation-analysis #big-game-hunting #double-extortion #cryptocurrency #on-chain-analysis #ransom-splitting #commodity-ransomware #llm-analysis #dhawan2025 #forensic-finance #social-contract #reputasi-kriminal
