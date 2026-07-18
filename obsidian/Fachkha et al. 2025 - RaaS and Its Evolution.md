---
title: "Ransomware-as-a-Service and Its Evolution: Lessons from the Babuk, GandCrab, and Sodinokibi Families"
authors:
  - Fachkha, Claude
  - Razaulla, Salwa
  - Markarian, Christine
  - Gawanmeh, Amjad
  - Fung, Benjamin C. M.
  - Assi, Chadi
year: 2025
venue: University of Dubai / McGill University / Concordia University
volume: "-"
issn: "-"
paper_id: "-"
url: https://www.researchgate.net/publication/397058719_Ransomware-as-a-Service_and_Its_Evolution_Lessons_from_the_Babuk_GandCrab_and_Sodinokibi_Families
tags:
  - raas
  - ransomware
  - cybercrime
  - malware-evolution
  - concept-drift
  - machine-learning
  - binary-analysis
  - malware-classification
  - threat-intelligence
rating: 3
status: 🟡 reading
date_reviewed: 2026-04-27
type: research-paper
topic: ransomware
---

## 📌 Summary

Paper ini membahas perkembangan beberapa keluarga ransomware seperti Babuk, GandCrab, dan Sodinokibi. Peneliti menggunakan pendekatan contrastive learning untuk melihat perubahan perilaku ransomware dari waktu ke waktu atau yang disebut sebagai _concept drift_. Dari hasil analisisnya, terlihat bahwa RaaS bukan lagi sekadar malware biasa, tetapi sudah menjadi sistem yang terstruktur dengan pembagian tugas antara developer, affiliate, dan aktor lainnya.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Ransomware saat ini sudah jauh berbeda dibanding ransomware lama yang biasanya dijalankan oleh satu kelompok saja. Pada model RaaS, ada pemisahan peran antara pembuat malware, operator, affiliate, negosiator, hingga pihak yang menjual akses awal ke sistem korban atau Initial Access Broker (IAB). Model seperti ini membuat ransomware menjadi lebih sulit dilacak, lebih mudah berkembang, dan lebih fleksibel dalam menjalankan serangan. Selain itu, ransomware juga terus berubah. Variannya cepat berkembang, fitur dimodifikasi, pola API call berubah, dan banyak signature lama yang akhirnya tidak lagi efektif digunakan untuk deteksi.
- **Gap yang diisi:** Kebanyakan penelitian sebelumnya lebih fokus pada cara mendeteksi malware, hanya membahas satu keluarga ransomware, atau membahas ekonomi RaaS secara umum. Sedangkan paper ini mencoba melihat hubungan antara evolusi teknis ransomware dengan struktur ekosistem RaaS itu sendiri. Penelitian ini juga menunjukkan adanya code reuse dan hubungan antar varian ransomware yang membuat ekosistem RaaS semakin adaptif.
- **Signifikansi:** RaaS memungkinkan variasi malware secara cepat melalui mekanisme developer–affiliate, sehingga pendekatan signature-based dan supervised ML menjadi cepat usang.

---

## 🎯 Contribution

kontribusi utama paper ini ada pada cara mereka melihat ransomware bukan hanya sebagai software berbahaya, tetapi sebagai bagian dari ekosistem yang lebih besar.
1. Menggunakan contrastive learning untuk mendeteksi perubahan dan evolusi ransomware.  
2. Menunjukkan adanya hubungan dan kemiripan antar keluarga ransomware melalui code reuse dan lineage analysis. 
3. Memberikan gambaran bahwa RaaS bekerja secara modular dan memiliki pembagian peran yang jelas.
4. Menjelaskan bahwa ekosistem RaaS memiliki struktur yang menyerupai organisasi atau perusahaan kecil.
5. Memberikan petunjuk kenapa model seperti ini menarik bagi aktor kriminal maupun pihak lain karena scalable, murah, dan sulit diatribusi.

---

## ⚙️ Methodology

- **Pendekatan:** Penelitian ini menggunakan pendekatan malware analysis dengan beberapa teknik seperti contrastive learning, clustering, concept drift detection, dan lineage analysis. 
- **Sumber data:** Dataset malware berkisaran 107 ribu malware samples,10 ribu ransomware, dan 4.456 ransomware unik yang bersumber dari VirusTotal, VirusShare, Malware Bazaar, Ghidra, AVClass, UMAP, dan t-SNE dengan fokus keluarga utama Babuk, GandCrab, dan Sodinokibi.
- **Threat Model:** Paper ini mengasumsikan bahwa ransomware akan terus berevolusi. Affiliate dapat memodifikasi payload yang mereka gunakan sehingga deteksi tradisional menjadi kurang efektif. Selain itu, beberapa ransomware juga menggunakan teknik anti-debugging dan anti-analysis untuk menghindari proses investigasi.
- **Jenis penelitian:** Eksperimental (ML-based detection) 

---

## 📊 Key Results

### 1. RaaS Bersifat Modular

Salah satu hasil paling penting adalah terlihat jelas bahwa model RaaS memisahkan developer dan operator. Developer membuat ransomware kit, sedangkan affiliate menjalankan serangan dan hasil ransom kemudian dibagi sesuai kesepakatan. Model ini berbeda dari ransomware lama yang biasanya dijalankan langsung oleh satu kelompok tertutup.

### 2. Banyak Terjadi Code Reuse

Peneliti menemukan adanya kemiripan API call, pola instruksi, dan hubungan antar varian ransomware. Ini menunjukkan bahwa banyak keluarga ransomware berkembang dari basis kode yang sama. Hal ini membuat RaaS lebih mirip ekosistem software daripada malware individual.

### 3. Infrastruktur Anonim Sangat Penting

Pada kasus GandCrab, banyak ditemukan penggunaan TOR, onion service, dan tox.chat. Ini menunjukkan bahwa infrastruktur anonim merupakan bagian penting dalam operasional RaaS karena membantu komunikasi dan menyulitkan proses pelacakan.

### 4. Struktur Organisasi Mirip Perusahaan

Paper juga mengutip studi tentang kebocoran internal Conti yang memperlihatkan adanya pembagian kerja, spesialisasi peran, jalur komunikasi, negosiator, hingga proses recruitment. Dari sini terlihat bahwa beberapa grup RaaS sudah bekerja hampir seperti organisasi profesional.

### 5. Concept Drift Menjadi Strategi Bertahan

Perubahan kode pada ransomware ternyata bukan hanya soal teknis, tetapi juga bagian dari strategi untuk bertahan dari deteksi keamanan. Dengan terus berubah, ransomware menjadi lebih sulit dikenali oleh sistem keamanan tradisional.

---

## 🏛️ Case Study: Babuk, GandCrab, Sodinokibi Evolution

| Aspek          | Temuan                                   |
| -------------- | ---------------------------------------- |
| Fokus analisis | Assembly instruction, API calls, strings |
| Teknik utama   | Contrastive learning + drift detection   |
| Tool           | Ghidra                                   |
| Pola umum      | Code reuse antar varian                  |
| Evasion        | Anti-debugging, anonymized communication |

---

## 🛡️ Detection Framework (Proposed)

1. **Feature Extraction & Normalization** — Disassembly dan standardisasi instruction  
2. **Instruction Embeddings** — Representasi token-level & sequence-level (BERT-like)  
3. **Contrastive Learning** — Positive/negative pairs  
4. **Detection Module** — Cluster distance vs standar deviasi  
5. **Lineage Analysis** — UMAP pada API calls dan strings  

---

## ⚠️ Limitations

- Fokus utamanya masih cukup teknis, sehingga pembahasan soal governance atau struktur kekuasaan dalam ekosistem RaaS belum terlalu mendalam.
- Tidak ada observasi langsung terhadap forum dark web.
- Dataset untuk beberapa keluarga ransomware masih terbatas.
- Belum membahas hubungan geopolitik atau kemungkinan keterlibatan negara secara lebih jauh.

---

## 🔗 Related Papers & Concepts

- [[Iwasaki & Masaki 2025 - Banning ransomware payments]] — Membangun di atas fondasi Laszka et al. untuk menganalisis dampak kebijakan pelarangan pembayaran tebusan; secara eksplisit mengutip paper ini sebagai referensi utama.
- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks ekosistem RaaS modern yang relevan sebagai pembaruan atas asumsi "single attacker" dalam model Laszka.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Menjelaskan kompleksitas teknis evolusi ransomware yang menjadi konsekuensi dari model bisnis RaaS.
- [[Dhawan et al. 2025 - Splitting the Spoils]]
- [[Inside Conti: Unpacking the Leaked RaaS Organizational Model]]
- [[Tracking Code Reuse and Infrastructure Overlap in Ransomware-as-a-Service]]
- [[The Age of Ransomware: A Survey on the Evolution, Taxonomy, and Research Directions]]
- [[The Architecture of Modern RaaS: A Deep-Dive Technical and Economic Analysis of GandCrab Ransomware]]
- [[REvil (Sodinokibi) Analysis]]
- [[Babuk Ransomware Leak]]

### Key References dari Paper Ini
- Curran et al. — Analisis operasi RaaS  
- Konsep Concept Drift dalam ML  
- AVClass — Malware labeling  
- UNVEIL — Behavior-based ransomware detection  
- Dataset ransomware publik (malXhunter)  

---

## 💡 My Notes

- Paper ini menunjukkan bahwa evolusi malware adalah konsekuensi langsung dari model RaaS
- Concept drift bukan anomali, tetapi bagian inheren dari sistem RaaS  
- Sangat kuat di sisi teknis (ML & binary analysis) namun lemah di sisi ekosistem dan model bisnis  
- Tidak cukup untuk menjelaskan bagaimana RaaS bekerja, tetapi penting untuk menjelaskan apa yang dihasilkan oleh RaaS (continuous variation)  
- Perlu dikombinasikan dengan paper lain untuk mendapatkan gambaran sistemik

---

## 🏷️ Keywords

#raas #ransomware #malware-evolution #concept-drift #contrastive-learning #binary-analysis #malware-lineage #machine-learning #Cybercrime #AffiliateModel #InitialAccessBroker #CyberThreatIntelligence #ConceptDrift #MalwareEvolution #CybercrimeEcosystem #GandCrab #Babuk #Sodinokibi