---
title: "Money Over Morals: A Business Analysis of Conti Ransomware"
authors:
  - Gray, Ian W.
  - Cable, Jack
  - Brown, Benjamin
  - Cuiujuclu, Vlad
  - McCoy, Damon
year: 2023
venue: arXiv preprint (cs.CR)
volume: arXiv:2304.11681v1
pages: "-"
doi: https://arxiv.org/abs/2304.11681
url: https://arxiv.org/pdf/2304.11681v1
affiliation:
  - New York University (Gray, McCoy)
  - Independent Researcher (Cable)
  - University of Michigan (Brown)
  - Flashpoint (Cuiujuclu)
tags:
  - raas
  - ransomware
  - conti
  - blockchain-forensics
  - bitcoin
  - organizational-analysis
  - revenue-sharing
  - cybercrime-economics
  - on-chain-analysis
  - ransom-splitting
  - recruitment
  - role-analysis
  - leaked-data
  - wizard-spider
  - ryuk
rating: 5
status: 🟡 reading
date_reviewed: 2026-06-02
type: working-paper
topic: ransomware-economics
peer_reviewed: false
note: Preprint arXiv; disajikan sebagai studi kasus empiris pertama yang menganalisis struktur bisnis internal Conti secara komprehensif berbasis data kebocoran internal dan analisis on-chain Bitcoin.
---

## 📌 Summary

Paper ini menyajikan analisis empiris mendalam terhadap operasi bisnis Conti—salah satu kelompok RaaS terbesar—menggunakan data kebocoran log percakapan internal Jabber/Rocket.Chat yang terdiri dari lebih dari 168.000 pesan dan 666 alamat Bitcoin yang dianotasi secara manual. Dengan mengombinasikan analisis on-chain blockchain dan penilaian kualitatif struktur organisasi, paper ini membuktikan bahwa Conti beroperasi layaknya sebuah perusahaan kriminal terstruktur dengan pembagian peran, sistem penggajian, proses rekrutmen, dan strategi bagi hasil yang sistematis antara operator inti dan afiliasi.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Meskipun serangan ransomware berbasis model RaaS terus mendominasi lanskap ancaman siber dan mengekstraksi jutaan dolar dari satu serangan tunggal, pemahaman akademis yang tervalidasi tentang struktur internal, ekonomi operasional, dan dinamika organisasi kelompok RaaS masih sangat terbatas. Industri keamanan selama bertahun-tahun hanya bersandar pada inferensi anekdotal tentang cara kerja operasi ini.
- **Gap yang diisi:** Absennya analisis akademis yang dikalibrasi secara empiris tentang struktur bisnis dan ekonomi backend operasi RaaS modern. Paper ini mengisi gap tersebut dengan memanfaatkan sumber data primer yang langka—kebocoran internal operasional—untuk mengkonstruksi gambaran akurat tentang mekanisme bagi hasil, hierarki peran, strategi rekrutmen, dan aliran dana nyata Conti.
- **Signifikansi:** Tanpa pemahaman tentang struktur organisasi dan titik-titik intervensi ekonomis dalam operasi RaaS, respons penegakan hukum dan kebijakan akan bersifat sub-optimal. Identifikasi konsentrasi aliran dana di dua bursa utama (satu kluster tak berlabel dan Gemini) membuka peluang intervensi yang konkret dan terukur.

---

## 🎯 Contribution

1. **Anotasi dan Analisis On-Chain 666 Alamat Bitcoin:** Melakukan anotasi manual seluruh alamat Bitcoin yang ditemukan dalam kebocoran Conti berdasarkan fungsinya (gaji, reimbursement, pembayaran tebusan, klaim kepemilikan, layanan), kemudian melakukan analisis on-chain untuk memetakan aliran pendapatan dan pengeluaran operasional.
2. **Pengembangan Metodologi Identifikasi Pembayaran Tebusan:** Mengembangkan metodologi baru untuk mengidentifikasi alamat pembayaran tebusan yang belum diketahui sebelumnya berdasarkan pola perilaku *ransom splitting* pada persentase yang tepat. Metodologi ini berhasil mengidentifikasi $83,9 juta pembayaran tebusan yang sebelumnya tidak terdokumentasi, meningkatkan total pembayaran Conti yang diketahui publik lebih dari lima kali lipat.
3. **Analisis Kualitatif Struktur Bisnis dan Peran Organisasi:** Mengidentifikasi dan memetakan peran-peran utama dalam hierarki Conti (manajemen, pengembangan dan infrastruktur, operasi akses, negosiasi) beserta hubungan pelaporan, kompensasi per peran, dan mekanisme rekrutmen berdasarkan analisis konten 168.624 pesan.
4. **Dokumentasi Proses Rekrutmen Dua-Jalur:** Mengekspos strategi rekrutmen Conti yang menggunakan jalur rekrutmen ganda—forum underground ilisit dan platform rekrutmen licit yang sah (LinkedIn, HeadHunter, Avito)—untuk merekrut tenaga teknis yang tidak menyadari sifat kriminal pemberi kerja mereka.
5. **Identifikasi Titik Intervensi Penegakan Hukum:** Membuktikan bahwa hanya dua bursa yang bertanggung jawab atas lebih dari 90% pembayaran yang teridentifikasi ke Conti, menyediakan titik leverage yang dapat dieksploitasi oleh penegak hukum dan regulator.

---

## ⚙️ Methodology

- **Pendekatan:** Analisis empiris multimetode yang mengombinasikan anotasi data kualitatif, analisis on-chain cryptocurrency kuantitatif, dan penilaian struktur bisnis berbasis konten percakapan.

### Sumber Data & Sampel

| Komponen Data | Detail |
|---|---|
| **Log Percakapan Jabber** | 168.624 pesan, 463 pengguna unik, 665 alamat Bitcoin; periode Juli 2020–Februari 2022 |
| **Log Percakapan Rocket.Chat** | 88.110 pesan, 248 pengguna unik, 1 alamat Bitcoin; periode Agustus 2020–Februari 2022 |
| **Dataset Ransomwhere** | Dataset crowdsourced alamat pembayaran ransomware publik sebagai data pembanding dan validasi |
| **Crystal Blockchain** | Platform analitik blockchain komersial untuk anotasi kepemilikan alamat Bitcoin |
| **Blockchain.com API** | Data transaksi masuk dan keluar untuk seluruh alamat yang diidentifikasi |
| **CoinDesk API** | Kurs penutupan Bitcoin-USD historis untuk konversi nilai dolar |

### Prosedur Anotasi dan Analisis

- **Anotasi Alamat Bitcoin:** Setiap alamat Bitcoin dianotasi secara manual oleh tiga peneliti berdasarkan konteks 10 pesan sebelum dan sesudah penyebutan alamat. Kategori anotasi: Salary, Reimbursement, Ransom Payment Address, Claimed Ownership, Services, dan Victim Name. Inter-Annotator Agreement (IAA) diukur menggunakan Fleiss' Kappa pada sampel acak 100 pos (κ = 0,73, *substantial agreement*).
- **Identifikasi Pembayaran Tebusan:** Alamat dikategorikan sebagai kemungkinan pembayaran tebusan jika: (1) mengirim dana langsung/tidak langsung ke alamat dalam dataset kebocoran, (2) menunjukkan pola *splitting* pada persentase yang tepat kelipatan 5 (misal: 20%, 25%), dan (3) menerima lebih dari 99% dananya dari bursa berisiko rendah (misal: Gemini) atau kluster tak berlabel yang diidentifikasi.
- **Analisis Struktur Organisasi:** Alias pengguna (463 total) disortir berdasarkan *degree centrality* untuk mengidentifikasi aktor utama. Anotasi difokuskan pada 50 alias teratas yang mencakup kategori: Peran, Atasan Langsung, Hubungan Kerja, Alias Alternatif, dan Tugas. Satu anotator adalah penutur asli bahasa Rusia yang ahli dalam *underground criminal slang* (Феня/*Fenya*).

### Threat Model

Model mengasumsikan dua lapisan aktor utama: (1) operator inti Conti (pengembang, manajer, administratur infrastruktur) sebagai pekerja bergaji tetap, dan (2) afiliasi sebagai mitra berkomisi yang melakukan penyusupan, penempatan ransomware, dan negosiasi korban. Keduanya berinteraksi melalui saluran komunikasi terenkripsi (Jabber berbasis TOR) dan transaksi Bitcoin sebagai mekanisme pembayaran utama.

---

## 📊 Key Results

### 1. Struktur Ekonomi Conti: Pendapatan vs. Pengeluaran

| Sumber | Jumlah | Jumlah Alamat |
|---|---|---|
| Pembayaran tebusan (dalam dataset kebocoran) | $3,4 juta | 5 |
| Pembayaran tebusan (Ransomwhere) | $17,1 juta | 28 |
| Kemungkinan pembayaran tebusan (Conti) | $57,4 juta | 41 |
| Kemungkinan pembayaran tebusan (Ryuk) | $26,5 juta | 34 |
| **Total Pendapatan** | **$104,4 juta** | **107** |
| Gaji | $21,9 juta | 419 |
| Reimbursement/Gaji | $5,4 juta | 15 |
| Reimbursement | $3,8 juta | 227 |
| **Total Pengeluaran** | **$31,2 juta** | **661** |

Total pendapatan Conti ($77,9 juta dikombinasikan dengan sisa dana Ryuk) lebih dari dua kali lipat total pengeluaran operasional ($31,2 juta), mengkonfirmasi profitabilitas tinggi model bisnis RaaS. Gaji merupakan komponen pengeluaran terbesar baik dalam jumlah alamat (419) maupun nilai dolar ($21,9 juta).

### 2. Mekanisme Ransom Splitting

Dari 32 alamat pembayaran tebusan Conti yang terkonfirmasi, 17 (53%) menunjukkan pola *splitting* langsung ke dua dompet dengan persentase yang tepat. Persentase split berkisar antara 5% hingga 40%, dengan yang paling umum (9 alamat) adalah 20%—artinya operator inti Conti mengambil 20% sementara 80% sisanya diteruskan ke afiliasi. Temuan ini secara langsung mengkonfirmasi mekanisme bagi hasil sebagai praktik operasional sistematis dalam ekosistem RaaS, bukan anomali.

Perbandingan dengan Ryuk (pendahulu Conti): dari 41 alamat Ryuk, 17 menunjukkan splitting dengan persentase 10%–50%, paling umum 35%. Perbedaan ini mengindikasikan adanya evolusi dalam negosiasi bagi hasil antara operator dan afiliasi seiring berganti generasi.

### 3. Konsentrasi Aliran Dana dan Titik Intervensi

| Bursa/Sumber | Pembayaran Terkonfirmasi | Kemungkinan Pembayaran | Total |
|---|---|---|---|
| Kluster Tak Berlabel | $8,6 juta | $64,8 juta | $73,4 juta (~70%) |
| Gemini | $5,9 juta | $17,4 juta | $23,1 juta |
| Kraken | $1,0 juta | $0,2 juta | $1,2 juta |
| Coinbase | $0,4 juta | $0,6 juta | $1,1 juta |
| Binance | $0,6 juta | $0,0 juta | $0,6 juta |

Hanya dua sumber (kluster tak berlabel dan Gemini) bertanggung jawab atas lebih dari 90% pembayaran yang teridentifikasi ke Conti—sebuah konsentrasi yang menghadirkan titik intervensi yang kuat bagi penegak hukum dan regulator bursa kripto. Paradoks Gemini: sebagai bursa berlisensi AS yang menegakkan regulasi *Know Your Customer* (KYC), kehadiran Gemini sebagai sumber pembayaran utama mengindikasikan kelemahan serius dalam deteksi transaksi ransomware di tingkat bursa yang seharusnya patuh regulasi.

### 4. Struktur Organisasi dan Pembagian Peran

Conti terstruktur ke dalam beberapa sub-tim fungsional yang mencerminkan arsitektur organisasi korporat:

- **Manajemen:** Manajer senior (stern, defender, buza, mango, bentley) yang mengontrol pembayaran, operasi, pengembangan, dan fungsi HR. Kelima individu ini mendominasi jaringan komunikasi berdasarkan *degree centrality*.
- **Pengembangan dan Infrastruktur:** Pengembang C++ dan sysadmin bergaji tetap yang memelihara malware, server, proxy, dan alat uji antivirus. Contoh tim yang didokumentasikan oleh manajer *mango*: tim utama (52 orang, $97.447/bulan), *reverse engineering* (16 orang, $23.347/bulan), tim riset (6 orang, $12.500/bulan), tim OSINT (4 orang, $9.000/bulan).
- **Operasi Akses:** Tim yang bertanggung jawab atas penyusupan awal ke jaringan korban, memanfaatkan IAB eksternal atau kapabilitas internal, dengan alat seperti TrickBot, BazarLoader, dan Emotet.
- **Negosiasi:** Afiliasi yang mengelola komunikasi pasca-kompromi dengan korban melalui panel admin; operator mengelola situs kebocoran publik.

### 5. Strategi Rekrutmen Dua-Jalur

Conti menggunakan strategi rekrutmen yang memadukan jalur licit dan ilicit secara bersamaan:

- **Jalur Underground:** Forum kriminal seperti XSS dan Exploit untuk rekrutmen langsung afiliasi dan operator yang mengetahui sifat pekerjaan.
- **Jalur Licit:** Platform rekrutmen sah—Avito, HeadHunter, Profi.ru, LinkedIn—untuk merekrut tenaga teknis (C++ programmer, full-stack developer, pentester, UI/UX designer) yang tidak mengetahui identitas sebenarnya pemberi kerja. Karyawan dibayar dalam cryptocurrency dan berkomunikasi melalui messenger terenkripsi, menimbulkan kecurigaan yang kemudian "dikelola" oleh manajer dengan jawaban ambigu.

Pasca-insiden Colonial Pipeline (Mei 2021), ketika forum utama (XSS, Exploit, Raid Forums) melarang iklan ransomware, Conti beradaptasi dengan menggunakan Telegram, Jabber, dan forum RAMP (Ransom Anon Market Place) yang baru dibentuk untuk melanjutkan rekrutmen.

### 6. Kontinuitas Operasional: Conti sebagai Penerus Ryuk

Analisis mengkonfirmasi bahwa Conti merupakan *rebranding* dari Ryuk (bukan reorganisasi dari awal), yang keduanya dioperasikan oleh kelompok Wizard Spider. Bukti-buktinya meliputi: sisa dana Ryuk digunakan untuk mendanai operasi Conti awal, penggunaan TrickBot sebagai vektor infeksi awal yang sama, tumpang-tindih sekitar 18% alias dalam log Jabber Conti dengan anggota TrickBot, dan munculnya alias yang sama dalam dakwaan TrickBot dan kebocoran Conti.

---

## 🏛️ Snapshot Data Keuangan Aktor Utama

| Alias | Peran | Estimasi Pendapatan |
|---|---|---|
| tramp | Manajer Operasional | $1,2 juta |
| mango | Manajer Pengembangan & Infrastruktur | $470 ribu |
| baget | Pengembang | $400 ribu |
| bullet | (tidak dispesifikasi) | $280 ribu |
| andy | (tidak dispesifikasi) | $98 ribu |

---

## ⚠️ Limitations

- **Status Preprint dan Sumber Data Kebocoran:** Paper ini berbasis data kebocoran oleh pihak ketiga (peneliti keamanan Ukraina), yang memunculkan pertanyaan validitas dan etika. Meskipun data telah divalidasi secara ekstensif oleh komunitas keamanan dan penulis, kemungkinan manipulasi atau ketidaklengkapan tidak dapat sepenuhnya dikesampingkan.
- **Cakupan Alamat Bitcoin yang Tidak Lengkap:** Dataset berbasis kebocoran internal yang tidak mencakup seluruh alamat pembayaran tebusan Conti—Chainalysis mengidentifikasi $180 juta dari Conti di tahun 2021 saja, jauh melampaui $77,9 juta yang berhasil diidentifikasi dalam studi ini. Temuan ekonomi merupakan *lower bound* yang signifikan.
- **Pandangan Sepihak tentang Ekosistem:** Analisis hanya mencakup satu kelompok RaaS (Conti). Generalisasi temuan ke seluruh ekosistem RaaS memerlukan validasi lintas-kelompok—celah yang kemudian diisi oleh Dhawan et al. (2025).
- **Keterbatasan Identifikasi Kausal Splitting:** Pola transaksi *splitting* ke dua dompet diidentifikasi sebagai mekanisme bagi hasil berdasarkan inferensi perilaku on-chain, bukan konfirmasi eksplisit dari log percakapan yang mengaitkan secara langsung setiap transaksi split dengan nama afiliasi yang spesifik.
- **Absensi Analisis IAB sebagai Entitas Mandiri:** Peran *Initial Access Broker* (IAB) dibahas sebagai bagian dari "operasi akses" namun tidak diperlakukan sebagai entitas ekonomi yang sepenuhnya mandiri. Ini merupakan keterbatasan yang relevan mengingat semakin mandirinya ekosistem IAB dalam RaaS kontemporer.
- **Batas Temporal Data:** Data kebocoran mencakup periode Juli 2020–Februari 2022, sehingga tidak mencerminkan dinamika pasca-jatuhnya Conti (Mei 2022) dan evolusi model RaaS selanjutnya.

---

## 🔗 Related Papers & Concepts

- [[Dhawan et al. 2025 - Splitting the Spoils]] — Memperluas metodologi identifikasi *ransom splitting* yang dikembangkan Gray et al. ke seluruh universe 17 keluarga RaaS dan 57 keluarga *commodity ransomware*, mengkonfirmasi bahwa pola bagi hasil Conti (dokumentasi studi kasus tunggal) adalah praktik industri-luas dengan rasio rata-rata 85:15.
- [[Laszka et al. 2017 - On the Economics of Ransomware]] — Gray et al. memberikan konfirmasi empiris berbasis data internal nyata terhadap prediksi model game-theoretic Laszka tentang perilaku penyerang rasional yang mengoptimalkan tuntutan tebusan.
- [[Iwasaki & Masaki 2025 - Banning ransomware payments]] — Temuan Gray et al. tentang operasi Conti yang berjalan hampir sepenuhnya di luar jangkauan regulasi formal mendukung argumen Iwasaki bahwa *blanket ban* akan mendorong transaksi lebih dalam ke *shadow economy*.
- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks operasional komplementer terhadap studi kasus Colonial Pipeline/DarkSide yang melengkapi temuan struktural Conti dalam paper ini.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Mengkonfirmasi secara teknis pola *code reuse* dan modularitas yang dicerminkan oleh tumpang-tindih antara Ryuk dan Conti yang diidentifikasi dalam paper ini.
- [[Conti Leaks Analysis]]
- [[Wizard Spider Criminal Organization]]
- [[TrickBot Malware Infrastructure]]
- [[Cybercrime as Industrial Organization]]
- [[Ransom Splitting and Affiliate Revenue]]
- [[Bitcoin KYC and Law Enforcement Intervention]]

### Key References dari Paper Ini

- Chainalysis (2022) — Laporan *Crypto Crime Report* yang mendokumentasikan pendapatan Conti $180 juta di 2021 sebagai baseline pembanding.
- Huang et al. (2018) — *Tracking Ransomware End-to-end* (IEEE S&P) — metodologi pelacakan Bitcoin yang menjadi fondasi teknis analisis on-chain dalam paper ini.
- Paquet-Clouston et al. (2019) — *Ransomware Payments in the Bitcoin Ecosystem* — analisis pembayaran ransomware Bitcoin pra-2017 sebagai rujukan metodologis.
- Cong et al. (2022) — *An Anatomy of Crypto-Enabled Cybercrimes* — analisis lintas-kelompok awal yang menjadi komparator.
- Oosthoek et al. (2022) — *A Tale of Two Markets* — karakterisasi pergeseran dari *commodity ransomware* ke RaaS yang melengkapi temuan paper ini.
- Crowdstrike (2020) — Atribusi Wizard Spider sebagai operator bersama Conti, Ryuk, dan TrickBot.

---

## 💡 My Notes

### Relevansi terhadap RQ1 (Perbedaan RaaS vs. Ransomware Konvensional)
Paper ini adalah **bukti empiris terkuat** yang tersedia dalam vault ini untuk menggambarkan *seperti apa sesungguhnya* model bisnis RaaS dari dalam. Perbedaan antara sumber pendapatan (tebusan) dan struktur pengeluaran (gaji tetap + reimbursement) secara langsung menjawab pertanyaan tentang apa yang membedakan RaaS dari ransomware konvensional: adanya pemisahan peran yang dikompensasi secara berbeda (gaji tetap vs. komisi berbasis persentase). Angka konkret tentang pengeluaran gaji Conti ($21,9 juta) dapat digunakan sebagai ilustrasi bahwa RaaS bukan sekadar alat kejahatan, melainkan *organisasi kriminal dengan anggaran operasional*.

### Relevansi terhadap RQ2 (Ekosistem Aktor dan Interaksi)
Ini adalah paper paling rinci yang tersedia untuk mendeskripsikan **interaksi antar-aktor dalam ekosistem RaaS** secara internal. Pemetaan hierarki peran (stern/defender sebagai pemimpin → mango/buza sebagai manajer menengah → tim pengembang/peneliti → afiliasi) memberikan gambaran yang jauh lebih granular dibanding laporan industri pada umumnya. Untuk RQ2, gunakan paper ini sebagai sumber utama untuk menggambarkan **mekanisme koordinasi internal** kelompok RaaS, dan Dhawan et al. (2025) untuk gambaran **industri-luas**.

### Relevansi terhadap RQ3 (Mekanisme Vetting dan Selektivitas)
Paper ini memberikan bukti empiris paling langsung untuk RQ3 melalui dua jalur:

**Pertama**, dokumentasi proses rekrutmen (Figure 4: *flow chart* sumber rekrutmen) menunjukkan bahwa selektivitas afiliasi bukan hanya soal "siapa yang bisa membayar lisensi"—ada proses yang melibatkan referral/vouching dari anggota yang sudah ada, screening kandidat, dan uji kemampuan coding sebelum seseorang diterima. Ini mencerminkan **selektivitas berbasis kompetensi dan kepercayaan**, bukan sekadar motif finansial.

**Kedua**, dokumentasi tentang norma-norma operasional yang diberlakukan secara internal (larangan menyerang layanan kesehatan yang kemudian dilanggar sendiri) menunjukkan adanya **tata kelola informal** dalam ekosistem RaaS—bahwa vetting afiliasi juga berkaitan dengan kepatuhan pada norma kolektif yang menjaga reputasi kelompok.

### Posisi Paper Ini dalam Galeri Literatur

Gray et al. (2023) adalah **fondasi empiris** yang paling solid dalam vault ini, bukan karena metodologinya paling canggih, tetapi karena berbasis **data primer nyata** dari dalam operasi RaaS. Sementara Laszka (2017) membangun model teoritis dan Dhawan et al. (2025) membuktikan pola industri-luas secara statistik, Gray et al. memberikan "wajah manusiawi" pada abstraksi tersebut—nama alias, percakapan nyata, dan angka-angka konkret yang dapat dikutip sebagai ilustrasi deskriptif.

### Catatan Kritis: "Money Over Morals" sebagai Argumen Tata Kelola
Judul paper ini—diambil dari keputusan Conti menyerang rumah sakit Ireland (HSE) meskipun ada norma informal yang melarang serangan terhadap layanan kesehatan—adalah argumen tata kelola yang sangat kuat. Ini menunjukkan bahwa mekanisme *self-regulation* informal dalam ekosistem RaaS bersifat **fragil dan tidak dapat diandalkan**. Implikasi untuk RQ3: vetting afiliasi dan norma-norma operasional kelompok RaaS tidak menjamin kepatuhan etis—justru mengekspos bahwa tata kelola informal ekosistem kriminal ini pada akhirnya tunduk pada kalkulasi finansial, bukan pada norma yang diklaim.

### Potensi Kutipan Unggulan
- **Untuk deskripsi struktur internal RaaS:** Temuan bahwa total gaji bulanan satu tim saja ($146.294 untuk tim mango) sudah mencerminkan skala operasi yang melampaui banyak startup teknologi sah—efektif untuk mengilustrasikan profesionalisasi kejahatan siber.
- **Untuk argumen titik intervensi:** Fakta bahwa hanya dua entitas (kluster tak berlabel + Gemini) mengendalikan 90%+ pembayaran Conti adalah argumen yang sangat persuasif untuk policy brief tentang pentingnya regulasi bursa kripto.
- **Untuk argumen rekrutmen:** Strategi rekrutmen melalui platform licit seperti LinkedIn untuk peran seperti "UI/UX Designer" dan "Data Analyst" menunjukkan bahwa batas antara ekonomi kriminal dan tenaga kerja sah semakin kabur—relevan untuk diskusi tentang kompleksitas atribusi dan respons kebijakan ketenagakerjaan.

---

## 🏷️ Keywords

#raas #ransomware #conti #blockchain-forensics #bitcoin #organizational-analysis #revenue-sharing #cybercrime-economics #on-chain-analysis #ransom-splitting #recruitment #role-analysis #leaked-data #wizard-spider #ryuk #trickbot #jabber #conti-leaks #gray2023 #money-over-morals #vetting #affiliate-model #cybercrime-as-business #kyc-exchange #law-enforcement-intervention
