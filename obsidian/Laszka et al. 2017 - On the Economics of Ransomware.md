---
title: On the Economics of Ransomware
authors:
  - Laszka, Aron
  - Farhang, Sadegh
  - Grossklags, Jens
year: 2017
venue: arXiv preprint (cs.CR)
volume: arXiv:1707.06247v3
pages: "-"
doi: https://arxiv.org/abs/1707.06247
url: https://arxiv.org/pdf/1707.06247v3
tags:
  - ransomware
  - security-economics
  - game-theory
  - backup-investment
  - ransom-payment
  - nash-equilibrium
  - cyber-extortion
  - deterrence
  - security-investment
  - behavioral-economics
rating: 5
status: 🟡 reading
date_reviewed: 2026-06-13
type: working-paper
topic: ransomware-economics
---

## 📌 Summary

Paper ini mempresentasikan model teoritis permainan (*game-theoretic model*) pertama yang secara eksplisit memodelkan interaksi strategis antara organisasi korban dan penyerang ransomware. Fokus utamanya adalah pada keputusan investasi cadangan data (*backup*) sebagai mekanisme mitigasi, serta keputusan pembayaran tebusan pasca-serangan. Penulis membuktikan secara formal bahwa investasi cadangan data yang terkoordinasi secara industri-luas dapat berfungsi sebagai deterren efektif terhadap serangan ransomware—sebuah temuan yang unik karena tidak berlaku untuk bentuk ancaman siber lainnya seperti pencurian data.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Meskipun ransomware telah diakui sebagai ancaman teoritis dan praktis selama lebih dari dua dekade, pemahaman strategis tentang dinamika interaksi adversarial antara organisasi korban dan pelaku ransomware masih sangat terbatas. Keputusan investasi cadangan data dan keputusan pembayaran tebusan sering diperlakukan sebagai isu teknis semata, bukan sebagai masalah ekonomi yang saling berkaitan.
- **Gap yang diisi:** Belum ada model game-theoretic yang secara formal menangkap keterkaitan antara keputusan investasi cadangan pra-insiden, keputusan pembayaran tebusan pasca-serangan, dan respons strategis penyerang. Literatur sebelumnya fokus pada aspek teknis malware atau dampak finansial secara agregat, namun mengabaikan analisis keseimbangan strategis antar aktor.
- **Signifikansi:** Tanpa pemahaman ekonomi yang tepat, kebijakan dan rekomendasi keamanan bersifat sub-optimal. Model ini menunjukkan bahwa ada kesenjangan (*gap*) signifikan antara keputusan individual yang rasional (*Nash equilibrium*) dan hasil yang paling menguntungkan secara kolektif (*social optimum*), yang mengimplikasikan perlunya mekanisme koordinasi industri.

---

## 🎯 Contribution

1. **Model Game-Theoretic Pertama untuk Ransomware:** Membangun model keamanan multi-tahap dan multi-defender pertama yang secara khusus dirancang untuk ekosistem ransomware, yang mencakup keputusan investasi cadangan, pembayaran tebusan, dan respons penyerang dalam satu kerangka formal.
2. **Formalisasi Kondisi Pembayaran Tebusan (Lemma 1):** Membuktikan secara matematis bahwa sebuah organisasi akan membayar tebusan jika dan hanya jika nilai tebusan yang diminta tidak melebihi kerugian permanen akibat kehilangan data yang dinormalisasi terhadap tingkat cadangan (*backup effort*).
3. **Kuantifikasi Nilai Deterensi Backup Terkoordinasi:** Membuktikan bahwa investasi cadangan yang dikoordinasikan secara industri-luas dapat memiliki efek deterensi terhadap penyerang—fenomena yang unik untuk ransomware dan tidak dapat diamati pada ancaman siber berbasis eksfiltrasi data.
4. **Analisis Efek Substitusi (*Substitution Effect*):** Mengidentifikasi dan mengkuantifikasi eksternalitas negatif antar kelompok organisasi, di mana peningkatan daya tarik satu kelompok sebagai target secara strategis mengalihkan serangan dari kelompok lain.
5. **Perbandingan Keseimbangan vs. Optimalitas Sosial:** Menyediakan analisis numeris yang memperlihatkan kesenjangan konsisten antara ekuilibrium Nash (keputusan individual) dan optimum sosial (koordinasi kolektif), sebagai dasar argumen untuk intervensi kebijakan.

---

## ⚙️ Methodology

- **Pendekatan:** Pemodelan ekonomi-keamanan berbasis teori permainan (*game-theoretic security economics*), dikombinasikan dengan analisis numeris untuk validasi dan ilustrasi.
- **Struktur Model:** Permainan keamanan multi-tahap, multi-defender (*multi-stage, multi-defender security game*) dengan struktur sebagai berikut:
  - **Aktor Defender:** Organisasi-organisasi dari dua kelompok berbeda (misal: rumah sakit dan universitas), masing-masing membuat keputusan cadangan data secara independen.
  - **Aktor Penyerang:** Satu entitas tunggal yang merepresentasikan pelaku kriminal, yang memutuskan apakah akan terlibat, seberapa besar upaya serangan terhadap masing-masing kelompok, dan berapa besar tebusan yang diminta.
  - **Tahap I:** Organisasi memilih tingkat upaya cadangan (*backup effort*) **b**; penyerang memilih upaya serangan **a₁**, **a₂**, dan tuntutan tebusan **r** secara simultan.
  - **Tahap II:** Setiap organisasi dikompromikan dengan probabilitas **Vⱼ(a₁, a₂)** dan memilih apakah akan membayar tebusan atau tidak.
- **Konsep Solusi:** *Subgame perfect Nash equilibrium* (SPNE) sebagai konsep solusi utama; *social optimum* sebagai pembanding normatif.
- **Fungsi Probabilitas Infeksi:** Probabilitas infeksi dimodelkan sebagai fungsi yang meningkat terhadap upaya serangan namun dengan *diminishing marginal utility*: **Vⱼ(a₁, a₂) = aⱼ / (D + (a₁ + a₂))**, di mana **D** adalah kesulitan dasar serangan.
- **Threat Model:** Penyerang diasumsikan sebagai entitas rasional tunggal yang memaksimalkan ekspektasi keuntungan. Model tidak secara eksplisit mempertimbangkan kompetisi antar penyerang, namun menyatakan bahwa ekstensi ke arah ini bersifat *straightforward*.
- **Dataset/Testbed:** Tidak ada dataset empiris; validasi dilakukan melalui analisis numeris dengan nilai parameter yang dikalibrasi terhadap laporan industri (IBM, Proofpoint, FBI). Parameter dasar: \|G\| = 100, W = 100, β = 0.9, F = 5, L = 5, T = 10, C_B = 1, D = 10, C_A = 10, C_D = 10.

---

## 📊 Key Results

### 1. Kondisi Pembayaran Tebusan (Lemma 1)
Sebuah organisasi i akan membayar tebusan jika dan hanya jika nilai tebusan yang diminta **r ≤ Lⱼ / bᵢ**. Implikasinya: semakin tinggi upaya cadangan (bᵢ), semakin rendah ambang batas tebusan yang bersedia dibayar. Ini menciptakan insentif langsung bagi penyerang untuk meminta tebusan yang tidak terlalu tinggi agar diterima korban.

### 2. Strategi Cadangan Optimal (Lemma 2 & 3)
- **Tanpa ancaman serangan:** Strategi cadangan optimal adalah **bᵢ* = √(β·Fⱼ / C_B)**, yang hanya dipengaruhi oleh risiko kegagalan acak dan biaya cadangan.
- **Dengan ancaman serangan:** Strategi cadangan bergantung pada perbandingan nilai tebusan yang diminta dengan rasio **Lⱼ / r**. Jika tebusan tinggi (r > Lⱼ / b_low), organisasi mengalkulasikan risiko ransomware secara penuh dan meningkatkan cadangan ke level **b_high = √(β(Fⱼ + Vⱼ·Lⱼ) / C_B)**. Jika tebusan rendah, organisasi berperilaku seolah tidak ada ancaman.

### 3. Deterensi melalui Investasi Cadangan Terkoordinasi (Proposisi 1)
Kondisi ekuilibrium di mana penyerang memilih untuk **tidak menyerang** dapat terpenuhi jika investasi cadangan organisasi cukup tinggi. Fenomena deterensi ini bersifat unik untuk ransomware karena cadangan data adalah *private good* yang tidak bergantung pada interdependensi teknis—berbeda dengan kontrol preventif seperti *firewall*, di mana efek deterensi tidak diamati pada ancaman eksfiltrasi data.

### 4. Kesenjangan Ekuilibrium vs. Optimum Sosial
Terdapat kesenjangan (*gap*) yang konsisten dan signifikan antara keputusan individual (ekuilibrium Nash) dan hasil yang dikoordinasikan secara sosial (optimum sosial), terutama pada:
- **Biaya cadangan rendah-menengah (C_B):** Pada rentang ini, deterensi adalah strategi yang optimal secara sosial, namun tidak tercapai dalam ekuilibrium individual karena masalah *free-riding*.
- **Faktor diskon perilaku (β) rendah:** Ketika organisasi kurang mempedulikan kerugian masa depan (*present bias*), investasi cadangan menurun di bawah level sosial-optimal.

### 5. Efek Substitusi Antar Kelompok
Ketika kerugian permanen satu kelompok (misal: L₁) meningkat, kelompok tersebut menjadi target yang lebih menarik bagi penyerang, yang mengalihkan upaya serangan ke kelompok tersebut. Akibatnya, kelompok lain (kelompok 2) justru mendapatkan manfaat berupa berkurangnya intensitas serangan terhadap mereka. Efek substitusi ini paling kuat pada serangan bertarget (*spear-phishing*) di mana upaya penyerang bersifat fokus.

### Ringkasan Parameter dan Fungsi Utama

| Simbol | Deskripsi |
|--------|-----------|
| **bᵢ** | Upaya cadangan organisasi i (frekuensi & cakupan backup) |
| **aⱼ** | Upaya serangan penyerang terhadap kelompok j |
| **r** | Nilai tebusan yang diminta penyerang |
| **Vⱼ(a₁,a₂)** | Probabilitas infeksi organisasi i ∈ Gⱼ |
| **Fⱼ** | Biaya kehilangan data akibat kegagalan acak |
| **Lⱼ** | Biaya kehilangan data permanen akibat ransomware |
| **Tⱼ** | Kerugian akibat gangguan bisnis sementara |
| **β** | Faktor diskon perilaku (*present bias*) |
| **C_B, C_A, C_D** | Biaya satuan cadangan, serangan, dan pengembangan ransomware |

---

## ⚠️ Limitations

- **Penyederhanaan Aktor Penyerang:** Model mengasumsikan satu penyerang tunggal yang rasional. Realita ekosistem RaaS melibatkan multiple aktor (developer, afiliasi, IAB) dengan insentif yang heterogen dan tidak selalu selaras—sebuah kompleksitas yang tidak tertangkap oleh model ini.
- **Absensi Mekanisme Preventif:** Model secara eksplisit mengecualikan keputusan investasi preventif (misal: *firewall*, patching, MFA). Hanya investasi mitigasi (*backup*) yang dimodelkan, sehingga analisis tidak bersifat holistik dari perspektif manajemen risiko keamanan.
- **Asumsi Rasionalitas Penyerang:** Penyerang diasumsikan selalu menepati janji pemulihan data (*decryption*) pasca pembayaran untuk menjaga reputasi komersial. Dalam praktiknya, terdapat kasus di mana penyerang tidak memenuhi janji ini atau kunci dekripsi sudah rusak.
- **Model Statis Satu Periode:** Analisis tidak menangkap dinamika jangka panjang, seperti bagaimana reputasi kelompok penyerang terbentuk, bagaimana organisasi memperbarui strategi mereka berdasarkan pengalaman, atau bagaimana ekosistem RaaS berevolusi dari waktu ke waktu.
- **Konteks Pra-RaaS:** Paper ini ditulis pada tahun 2017, sebelum model RaaS (Ransomware-as-a-Service) berkembang menjadi ekosistem yang kompleks dengan pemisahan peran developer–affiliate–IAB. Oleh karena itu, model tidak mencerminkan struktur organisasi pelaku serangan ransomware modern.
- **Validasi Empiris Terbatas:** Analisis numeris menggunakan parameter yang dikalibrasi secara teoretis, bukan data empiris yang divalidasi. Akibatnya, besaran kuantitatif hasilnya sulit diterjemahkan langsung ke konteks dunia nyata.

---

## 🔗 Related Papers & Concepts

- [[Iwasaki & Masaki 2025 - Banning ransomware payments]] — Membangun di atas fondasi Laszka et al. untuk menganalisis dampak kebijakan pelarangan pembayaran tebusan; secara eksplisit mengutip paper ini sebagai referensi utama.
- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks ekosistem RaaS modern yang relevan sebagai pembaruan atas asumsi "single attacker" dalam model Laszka.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Menjelaskan kompleksitas teknis evolusi ransomware yang menjadi konsekuensi dari model bisnis RaaS.
- [[Backup Investment as Security Deterrence]]
- [[Nash Equilibrium in Cybersecurity]]
- [[Social Optimum vs. Nash Equilibrium in Security]]
- [[Present Bias in Security Investment]]
- [[Ransomware Payments Deterrence]]

### Key References dari Paper Ini

- Young & Yung (1996) — *Cryptovirology: Extortion-based security threats and countermeasures* — asal-usul konsep ransomware.
- Young & Yung (2017) — *Cryptovirology: The birth, neglect, and explosion of ransomware* — retrospektif dua dekade ancaman ransomware.
- Grossklags et al. (2008) — *Secure or insure?: A game-theoretic analysis* — fondasi pemodelan keamanan game-theoretic yang diadopsi paper ini.
- Fultz & Grossklags (2009) — Memperkenalkan penyerang yang bertindak strategis dalam model pertahanan terdistribusi.
- Brandt, George & Sandler (2016) — *Why concessions should not be made to terrorist kidnappers* — analogi penculikan yang digunakan untuk memahami konsekuensi pembayaran tebusan.
- O'Gorman & McDonald (2012) — Analisis kampanye ransomware dan dampak finansialnya (Symantec).
- Kharraz et al. (2016) — Deteksi ransomware berbasis monitoring repositori data (UNVEIL).

---

## 💡 My Notes

- **Relevansi Utama terhadap RQ1 & RQ2:** Paper ini adalah **fondasi teoritis ekonomi** yang paling solid untuk menjawab mengapa model bisnis RaaS secara inheren menghasilkan keseimbangan yang sub-optimal bagi masyarakat. Argumen "gap antara Nash equilibrium dan social optimum" dapat digunakan untuk menjelaskan mengapa koordinasi antar organisasi (dan antar negara) sangat diperlukan tetapi sulit terwujud.

- **Jembatan ke Laszka → Iwasaki:** Secara kronologis, paper Laszka et al. (2017) ini adalah cikal bakal langsung dari paper Iwasaki (2025). Iwasaki mengembangkan model tiga tahap yang lebih kompleks dengan menambahkan variabel pelaporan insiden dan *safe harbor*, tetapi premis dasarnya—bahwa pilihan pembayaran memengaruhi insentif investasi keamanan—berasal dari sini. Koneksi ini penting untuk ditunjukkan dalam *literature review* sebagai jalur perkembangan teori.

- **Keterbatasan Kritis untuk Konteks Penelitian Kita:** Model "single attacker" dalam paper ini sudah **tidak mencukupi** untuk menggambarkan ekosistem RaaS modern yang melibatkan developer, afiliasi, dan IAB dengan insentif terpisah. Kelemahan ini justru dapat dijadikan *research gap* eksplisit: "Laszka et al. menunjukkan dampak deterensi dari koordinasi korban, namun model mereka belum mampu menangkap bagaimana struktur insentif berlapis dalam ekosistem RaaS memengaruhi dinamika tersebut."

- **Temuan Kritis—Efek Substitusi sebagai Eksternalitas Negatif:** Temuan efek substitusi antar kelompok target (Bagian 4.2) sangat relevan untuk memahami mengapa penegakan hukum yang memfokuskan tekanan pada satu jenis target (misal: infrastruktur kritis) dapat mengalihkan serangan ke sektor yang lebih rentan (misal: pendidikan atau kesehatan tanpa kapasitas pertahanan yang memadai).

- **Catatan Metodologis:** Penggunaan *subgame perfect Nash equilibrium* (SPNE) sebagai konsep solusi memungkinkan analisis backward induction yang rapi, tetapi asumsi rasionalitas sempurna semua aktor membatasi aplikabilitas empiris. Dalam konteks menulis literature review, tandai bahwa paper ini adalah analisis normatif, bukan deskriptif.

---

## 🏷️ Keywords

#ransomware #security-economics #game-theory #backup-investment #ransom-payment #nash-equilibrium #social-optimum #cyber-extortion #deterrence #behavioral-economics #present-bias #multi-stage-game #security-investment #coordination-problem #substitution-effect #ransomware-economics #laszka2017
