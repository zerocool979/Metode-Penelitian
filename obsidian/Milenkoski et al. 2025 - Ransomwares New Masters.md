---
title: "Ransomware's New Masters: How States Are Hijacking Cybercrime"
authors:
  - Milenkoski, Aleksandar
  - Minier, Jiro
  - Vögele, Julian-Ferdinand
  - Smeets, Max
  - Grossman, Taylor
year: 2025
venue: Virtual Routes — Pharos Series
volume: Report No. 3
pages: 1-40
doi: "-"
url: https://virtual-routes.org/wp-content/uploads/2025/04/Virtual-Routes-Pharos-Report-Series-No.-3.pdf
affiliation:
  - SentinelLabs (Milenkoski)
  - Deutsche Cyber-Sicherheitsorganisation / DCSO (Minier)
  - Recorded Future — Insikt Group (Vögele)
  - ETH Zurich / RUSI / Stanford CISAC (Smeets)
  - Institute for Security and Technology (Grossman)
partner_organizations:
  - SentinelLabs
  - DCSO
  - Recorded Future
tags:
  - raas
  - ransomware
  - state-sponsored
  - geopolitics
  - russia
  - north-korea
  - china
  - iran
  - plausible-deniability
  - cyber-espionage
  - threat-intelligence
  - nation-state-actors
  - cybercrime-ecosystem
  - apt
  - hybrid-warfare
rating: 5
status: 🟡 reading
date_reviewed: 2026-06-14
type: policy-report
topic: ransomware-geopolitics
peer_reviewed: false
note: Laporan kebijakan non-peer-reviewed dari lembaga riset independen Virtual Routes. Dikembangkan bersama SentinelLabs, DCSO, dan Recorded Future. Kredibel secara analitis karena berbasis threat intelligence industri aktif, meskipun bukan publikasi akademik.
---

## 📌 Summary

Laporan ini menyajikan analisis komparatif terhadap penggunaan ransomware oleh kelompok-kelompok yang terhubung dengan empat negara: Rusia, Korea Utara, Tiongkok, dan Iran—yang secara kolektif disebut "Big Four." Temuan utamanya adalah bahwa motif dan metode penggunaan ransomware berbeda signifikan di antara keempat negara tersebut, namun terdapat tren konvergensi yang semakin nyata: negara-negara tidak lagi membangun operasi ransomware dari nol, melainkan mengintegrasikan diri ke dalam ekosistem kejahatan siber yang sudah ada—menggunakan afiliasi, membeli akses, atau mengadopsi varian ransomware komersial yang tersedia luas seperti LockBit. Laporan ini secara khusus relevan untuk memahami bagaimana ekosistem RaaS kriminal telah menjadi infrastruktur yang dimanfaatkan oleh aktor negara untuk mencapai tujuan strategis dengan menyamarkan asal-usul serangan.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Ransomware selama ini diasosiasikan dengan aktor kriminal non-negara. Namun, bukti yang terakumulasi menunjukkan bahwa aktor yang terhubung dengan negara semakin aktif menggunakannya—bukan hanya sebagai alat ekstorsi finansial, tetapi sebagai instrumen geopolitik. Laporan ini mengisi kekosongan analisis komparatif lintas-negara tentang bagaimana dan mengapa negara mengadopsi ransomware untuk tujuan strategis.
- **Gap yang diisi:** Literatur yang ada umumnya menganalisis ransomware negara secara terpisah (per negara atau per kelompok APT). Laporan ini memberikan kerangka komparatif yang memungkinkan identifikasi pola konvergensi dan divergensi di antara keempat aktor negara utama, serta menunjukkan arah perkembangan ke depan.
- **Signifikansi:** Entanglement (keterbeliatan) yang semakin dalam antara operasi ransomware negara dan kriminal secara langsung mempersulit atribusi, melemahkan deterrensi, dan berimplikasi pada bagaimana kebijakan respons—termasuk pelarangan pembayaran tebusan—akan bekerja dalam praktiknya.

---

## 🎯 Contribution

1. **Kerangka Komparatif Empat Negara:** Menyediakan analisis motif dan metode penggunaan ransomware lintas-negara (Rusia, Tiongkok, Korea Utara, Iran) dalam satu dokumen yang terpadu.
2. **Tipologi Fungsi Ransomware bagi Aktor Negara:** Mengidentifikasi empat fungsi utama ransomware dalam konteks negara—sebagai alat operasional konflik (Rusia), penyamaran spionase (Tiongkok), destabilisasi politik (Iran), dan sumber pendanaan (Korea Utara).
3. **Dokumentasi Tren Konvergensi:** Membuktikan bahwa batas antara ransomware kriminal dan negara semakin kabur, dengan negara-negara mengadopsi praktik terbaik ekosistem kriminal dan berpartisipasi aktif di dalamnya.
4. **Studi Kasus Spotlighted:** Menyediakan studi kasus mendalam untuk setiap negara—NotPetya/GRU Sandworm (Rusia), Conti-FSB, WannaCry/Lazarus (Korea Utara), Andariel/Maui (Korea Utara), i-Soon & Bronze Starlight (Tiongkok), SamSam & MuddyWater (Iran).
5. **Proyeksi Tren ke Depan:** Mengantisipasi deepening entanglement negara-kriminal, khususnya melalui mekanisme afiliasi RaaS yang dimanfaatkan oleh aktor negara.

---

## ⚙️ Methodology

- **Pendekatan:** Analisis komparatif berbasis threat intelligence industri; studi kasus historis dan kontemporer; sintesis laporan publik dari Mandiant, CISA, FBI, Microsoft Threat Intelligence, SentinelLabs, dan lembaga-lembaga sejenis.
- **Sumber Data:** Laporan atribusi pemerintah (DoJ, OFAC, CISA), riset threat intelligence perusahaan keamanan (Mandiant/Google Cloud, SentinelOne, Kaspersky, Secureworks, Unit 42), dokumen kebocoran internal (Conti leaks, i-Soon leaks), dan artikel investigatif.
- **Threat Model:** Mengasumsikan bahwa aktor negara beroperasi dalam spektrum yang luas—dari penggunaan ransomware yang sepenuhnya terkontrol negara, hingga "moonlighting" oleh individu yang bekerja untuk kontraktor negara, hingga kooptasi kelompok kriminal independen.
- **Jenis Penelitian:** Deskriptif-komparatif; bukan eksperimental. Tidak ada pengujian teknis malware atau analisis on-chain.
- **Keterbatasan Metodologis:** Analisis bergantung pada laporan publik yang mungkin tidak lengkap atau tunduk pada bias atribusi. Banyak insiden yang sulit diverifikasi secara teknis karena indikator teknis tidak selalu dipublikasikan secara terbuka.

---

## 📊 Key Results

### 1. Rusia: Ransomware sebagai Alat Operasional Konflik

Rusia merupakan hub ransomware global—Chainalysis memperkirakan 74% pendapatan ransomware global mengalir ke kelompok berbasis Rusia pada tahun 2021. Kelompok kriminal Rusia secara konsisten menghindari target berbahasa Rusia (malware sering memeriksa pengaturan bahasa sistem operasi dan menghapus diri jika mendeteksi bahasa CIS).

Koneksi langsung antara kelompok kriminal dan negara secara berkala terungkap: Evil Corp (Maksim Yakubets) memberikan bantuan langsung kepada FSB, dan kebocoran Conti mengungkapkan bahwa kelompok tersebut menerima permintaan penargetan spesifik dari FSB—termasuk usulan untuk menyerang Bellingcat.

Grup Sandworm (APT44/Unit 74455 GRU) merupakan aktor negara Rusia yang paling menonjol dalam penggunaan ransomware. Pola operasionalnya meliputi: NotPetya (2017) sebagai pseudo-ransomware destruktif; Hermetic Ransom/PartyTicket (Februari 2022) yang diluncurkan bersamaan dengan invasi penuh ke Ukraina; Prestige ransomware (Oktober 2022) yang menargetkan perusahaan transportasi dan logistik di Ukraina dan Polandia untuk mengganggu jalur pasokan pertahanan; serta RansomBoggs (November 2022).

**Kesimpulan analitis:** GRU menggunakan ransomware untuk mempercepat tempo operasional dalam konflik bersenjata—bukan terutama untuk keuntungan finansial.

### 2. Korea Utara: Ransomware sebagai Mesin Pendanaan Negara

Perkembangan ransomware Korea Utara mengikuti trajektori evolusi yang jelas: dari wiper destruktif (Jokra, Destover) → WannaCry yang gagal secara finansial (2017) → jeda pasca-WannaCry → ekspansi ransomware bertarget mulai 2020 (VHD, Hansom, Maui, H0lyGh0st, FakePenny).

Kelompok utama yang terlibat: Lazarus Group dan subgrupnya Andariel (APT45). Andariel secara eksplisit diidentifikasi oleh pemerintah AS sebagai unit dalam Reconnaissance General Bureau (RGB) Korea Utara yang menjalankan operasi ransomware untuk mendanai operasi spionase, termasuk membeli server virtual pribadi dari hasil tebusan.

Perkembangan signifikan: (a) Adopsi double extortion dan situs kebocoran data (H0lyGh0st); (b) Peningkatan dramatis tuntutan tebusan—FakePenny menuntut lebih dari $6 juta Bitcoin dalam satu kasus; (c) Integrasi ke dalam rantai nilai kriminal internasional—Andariel diduga beroperasi sebagai IAB atau afiliasi untuk operasi Play ransomware yang diduga terkait Rusia.

Estimasi 2023 pemerintah AS: sekitar setengah program rudal balistik Korea Utara didanai oleh pencurian siber dan pemerasan siber. Bandingkan: crypto thefts menghasilkan $1,3 miliar pada 2024, jauh melampaui pendapatan ransomware.

### 3. Tiongkok: Ransomware sebagai Kamuflase Spionase

Tiongkok berbeda fundamental dari tiga negara lainnya: tidak ada rekam jejak publik operasi wiper. Ransomware digunakan terutama untuk plausible deniability dalam kampanye spionase—mengalihkan perhatian, salah atribusi, atau menghapus bukti setelah intelijen diekstraksi.

Dua jalur penggunaan ransomware oleh aktor terhubung Tiongkok: (a) *Moonlighting* oleh individu yang bekerja untuk kontraktor negara (bukti dari kebocoran i-Soon yang menunjukkan tekanan finansial pada karyawan bergaji rendah); (b) Operasi terorganisir untuk tujuan gangguan geopolitik (ChamelGang/CamoFei menyerang AIIMS India pada November 2022 dan kepresidenan Brasil pada November 2022 bersamaan dengan pemilu).

Bronze Starlight (DEV-0401) adalah contoh kunci: sering berganti nama dan merotasi payload (LockFile, AtomSilo, NightSky, LockBit 2.0, Pandora), diduga beroperasi sebagai afiliasi LockBit pada 2022, namun dengan victimology, umur singkat strain, dan penggunaan malware spionase (HUI Loader, PlugX) yang tidak konsisten dengan kelompok kriminal bermotif finansial biasa.

Strategi diplomatik Tiongkok: secara konsisten mengklaim insiden ransomware adalah tindakan kelompok kriminal independen, sementara CVERC merilis laporan yang salah mengklasifikasikan Volt Typhoon sebagai kelompok ransomware—sebuah upaya menyamarkan operasi spionase sebagai aktivitas kriminal.

### 4. Iran: Ransomware sebagai Instrumen Destabilisasi Politik

Iran menggunakan ransomware terutama untuk tujuan geopolitik dengan tiga dimensi: destabilisasi (khususnya terhadap Israel), misattribusi/plausible deniability (seperti Project Signal melalui kontraktor Emen Net Pasargard), dan propaganda psikologis (publikasi serangan di media sosial).

Kelompok utama: MuddyWater (MOIS), Fox Kitten (IRGC-affiliated), Agrius, Pioneer Kitten, HomeLand Justice.

Tren baru yang signifikan: kelompok seperti Pioneer Kitten dan Lemon Sandstorm (dilaporkan CISA Agustus 2024) mulai memonetisasi akses dengan menjual kredensial di marketplace kriminal dan berkolaborasi dengan afiliasi ransomware seperti NoEscape dan ALPHV (BlackCat)—mekanisme yang mirip dengan model Korea Utara.

Tiga tren makro Iran: (1) Pergeseran dari wiper ke pseudo-ransomware untuk plausible deniability; (2) Keterlibatan aktif dalam rantai nilai RaaS dengan menyediakan initial access; (3) Penggunaan media sosial untuk amplifikasi propaganda dari serangan.

### 5. Tren Konvergensi: Deepening Entanglement

Meskipun motif berbeda, keempat negara menunjukkan pola konvergensi: adopsi praktik terbaik dari operasi ransomware kriminal (double extortion, situs kebocoran, negosiasi profesional); penggunaan RaaS off-the-shelf untuk mengurangi overhead pengembangan dan mempersulit atribusi; partisipasi aktif—bukan sekadar sebagai penerima manfaat—dalam ekosistem kriminal.

Implikasi kebijakan kritis: entanglement ini akan semakin dalam, sehingga respons kebijakan yang hanya menargetkan aktor kriminal non-negara akan semakin tidak memadai.

---

## 🏛️ Snapshot Studi Kasus Utama

| Negara | Aktor/Kelompok | Insiden Kunci | Fungsi Ransomware |
|--------|----------------|---------------|-------------------|
| **Rusia** | Sandworm (GRU Unit 74455) | NotPetya (2017), Prestige (2022) | Alat operasional konflik |
| **Rusia** | Evil Corp, Conti | Koneksi FSB, targeting Bellingcat | Kriminal dengan nexus negara |
| **Korea Utara** | Lazarus / Andariel (APT45) | WannaCry (2017), Maui (2021), FakePenny (2024) | Pendanaan program negara |
| **Tiongkok** | Bronze Starlight, ChamelGang | AIIMS India (2022), Brazilian Presidency (2022) | Kamuflase spionase & gangguan |
| **Tiongkok** | APT41 | Video gaming industry attack | Moonlighting finansial pribadi |
| **Iran** | MuddyWater, Fox Kitten | Pay2Key (2020), DarkBit (2023), Albania (2022) | Destabilisasi & propaganda |
| **Iran** | Pioneer Kitten | Kolaborasi dengan NoEscape, BlackCat (2024) | Monetisasi akses + politik |

---

## 🕸️ Mekanisme State-RaaS Entanglement (Tipologi)

Berdasarkan sintesis kasus-kasus dalam laporan, setidaknya ada **lima mekanisme** bagaimana negara mengintegrasikan diri ke dalam ekosistem RaaS:

1. **Kooptasi Langsung:** Negara memberikan permintaan penargetan kepada kelompok kriminal (contoh: FSB → Conti).
2. **Koneksi Relasional:** Individu dengan latar belakang intelijen menjadi pemimpin kelompok kriminal (contoh: Evil Corp/Yakubets via ayah mertua FSB).
3. **Moonlighting Kontraktor:** Karyawan kontraktor negara bergaji rendah menjalankan operasi ransomware untuk pendapatan tambahan (contoh: i-Soon/Tiongkok).
4. **Adopsi Kapabilitas RaaS:** Aktor negara menggunakan strain RaaS komersial off-the-shelf (contoh: Korea Utara menggunakan LockBit 2.0, Ryuk; Tiongkok via Bronze Starlight sebagai afiliasi LockBit).
5. **Partisipasi Rantai Nilai:** Aktor negara beroperasi sebagai IAB atau afiliasi dalam ekosistem RaaS kriminal, berbagi pendapatan tebusan (contoh: Pioneer Kitten/Iran, Andariel/Korea Utara dalam Play ransomware).

---

## ⚠️ Limitations

- **Sumber Bergantung pada Laporan Publik:** Analisis sepenuhnya bergantung pada apa yang dipublikasikan oleh pemerintah dan perusahaan keamanan swasta. Banyak operasi tidak pernah dipublikasikan atau sulit diverifikasi secara independen.
- **Masalah Atribusi yang Inheren:** Penggunaan infrastructure overlap, commodity malware, dan sering berganti nama membuat atribusi ke aktor negara bersifat probabilistik, bukan deterministik—terutama untuk Tiongkok.
- **Tidak Ada Analisis Kuantitatif:** Laporan tidak menyertakan data on-chain atau kuantifikasi pendapatan seperti dalam Gray et al. (2023) atau Dhawan et al. (2025). Tidak ada dataset yang dapat diverifikasi secara independen.
- **Cakupan Tidak Merata:** Bagian Rusia dan Korea Utara lebih kaya bukti dibandingkan Tiongkok dan Iran, karena perbedaan volume atribusi publik yang tersedia.
- **Tidak Membahas Ekosistem RaaS Secara Mendalam:** Fokus laporan adalah perilaku negara, bukan mekanisme internal RaaS. Komponen seperti mekanisme vetting afiliasi, struktur revenue sharing, atau peran IAB sebagai entitas mandiri tidak dianalisis.
- **Potensi Bias Lembaga:** Laporan dikembangkan bersama SentinelLabs, DCSO, dan Recorded Future—semua perusahaan keamanan yang memiliki kepentingan komersial dalam framing ancaman tertentu.

---

## 🔗 Related Papers & Concepts

- [[Gray et al. 2023 - Money Over Morals]] — Memberikan bukti empiris internal tentang bagaimana Conti menerima permintaan penargetan dari FSB yang dikonfirmasi oleh laporan Milenkoski et al. ini. Koneksi Conti-FSB yang disebut di sini dapat dilacak ke data kebocoran yang dianalisis Gray et al.
- [[Dhawan et al. 2025 - Splitting the Spoils]] — Membuktikan secara on-chain bahwa ekosistem RaaS komersial yang dimanfaatkan oleh negara beroperasi dengan mekanisme bagi hasil yang terdokumentasi. Konteks ini penting untuk memahami mengapa negara tertarik mengintegrasikan diri ke dalam ekosistem ini (biaya rendah, infrastruktur sudah ada, atribusi sulit).
- [[Laszka et al. 2017 - On the Economics of Ransomware]] — Model "single attacker" Laszka semakin tidak relevan ketika penyerang ternyata adalah aktor negara yang termotivasi oleh faktor non-finansial. Laporan ini memberikan konteks empiris mengapa model ekonomi ransomware membutuhkan perpanjangan untuk mencakup aktor negara.
- [[Iwasaki & Masaki 2025 - Banning ransomware payments]] — Argumen Iwasaki tentang dampak blanket ban menjadi semakin kompleks ketika korban tidak dapat membedakan apakah penyerangnya adalah kriminal murni atau aktor negara yang menyamar. "Shadow economy" yang dikhawatirkan Iwasaki berpotensi diisi oleh operasi negara yang memang dirancang untuk beroperasi di luar jangkauan regulasi.
- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks landscape RaaS kriminal yang menjadi infrastruktur yang digunakan oleh negara dalam laporan ini.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Mekanisme concept drift dan modularitas RaaS yang dijelaskan Fachkha et al. memudahkan negara untuk mengadopsi dan memodifikasi strain ransomware tanpa membuatnya dari awal.
- [[APT44 Unearthing Sandworm - Mandiant 2024]]
- [[i-Soon Leak Analysis]]
- [[Conti-FSB Connection]]
- [[North Korean Cyber Financial Operations]]

### Key References dari Laporan Ini
- Chainalysis (2021) — Estimasi 74% pendapatan ransomware global mengalir ke kelompok berbasis Rusia.
- Mandiant/Google Cloud — APT41, APT44/Sandworm, APT45/Andariel attribution reports.
- CISA advisories — Maui ransomware (2022), #StopRansomware DPRK (2023), Pioneer Kitten/Lemon Sandstorm (2024).
- SentinelOne — ChamelGang & Friends report (2024), i-Soon leak analysis (2024).
- Secureworks — Bronze Starlight / HUI Loader report (2022).
- US DoJ — Indictments: Evil Corp (2019), SamSam (2018), Andariel (2024), i-Soon (2025).
- Smeets, Max — *Ransom War: How Cyber Crime Became a Threat to National Security* (OUP, 2025).

---

## 💡 My Notes

### Relevansi terhadap RQ1 (Perbedaan RaaS vs. Ransomware Konvensional)
Laporan ini tidak langsung menjawab RQ1, tetapi memberikan dimensi tambahan yang kritis: motivasi penggunaan ransomware bukan hanya finansial. Fakta bahwa negara mengadopsi RaaS off-the-shelf (misalnya Bronze Starlight menggunakan LockBit 2.0 sebagai afiliasi) justru **mengkonfirmasi secara tidak langsung** bahwa ekosistem RaaS komersial telah mencapai tingkat maturitas sedemikian rupa sehingga mampu menarik aktor negara sebagai pengguna—ini adalah argumen kuat tentang "professionalisasi" RaaS sebagai pembeda dari ransomware konvensional.

### Relevansi terhadap RQ2 (Ekosistem Aktor dan Interaksi)
Ini adalah paper **paling penting** dalam vault untuk menggambarkan bagaimana aktor di luar ekosistem kriminal murni—yakni negara—berinteraksi dengan dan masuk ke dalam ekosistem RaaS. Lima tipologi mekanisme entanglement yang saya identifikasi di atas (kooptasi langsung, koneksi relasional, moonlighting, adopsi kapabilitas, partisipasi rantai nilai) dapat digunakan sebagai kerangka untuk memperluas peta aktor RQ2 melampaui developer–afiliasi–IAB yang murni kriminal.

### Relevansi terhadap RQ3 (Mekanisme Vetting dan Selektivitas)
Laporan ini mengungkapkan dimensi yang sangat relevan untuk RQ3: ketika aktor negara masuk ke dalam ekosistem RaaS, proses vetting afiliasi menjadi lebih kompleks. Pioneer Kitten (Iran) dan Andariel (Korea Utara) yang beroperasi sebagai afiliasi atau IAB dalam ekosistem kriminal mengindikasikan bahwa **proses vetting ekosistem RaaS tidak dirancang untuk menyaring aktor negara**—dan bahwa komunitas kriminal mungkin tidak peduli atau tidak tahu apakah mitra mereka terhubung dengan negara. Ini adalah argumen empiris yang kuat bahwa selektivitas afiliasi RaaS lebih didorong oleh kapabilitas teknis dan reputasi daripada oleh screening ideologis atau identitas.

### Catatan Kritis: State Actor sebagai Jembatan ke Analisis Kebijakan
Laporan ini menjadi jembatan kritis yang menghubungkan analisis ekosistem RaaS (RQ1-RQ3) dengan pertanyaan kebijakan yang lebih luas tentang tata kelola dan atribusi. Argumen bahwa "deepening entanglement" akan terus berlanjut secara langsung mendukung tesis bahwa ekosistem RaaS telah berkembang melampaui sekadar model bisnis kriminal—ia telah menjadi **infrastruktur geopolitik** yang dimanfaatkan oleh negara untuk mencapai tujuan strategis dengan *plausible deniability*.

Ini adalah koneksi yang belum secara eksplisit dibahas oleh paper akademis lain dalam vault ini, dan dapat menjadi **kontribusi orisinal** dalam paper akhir: mensintesis bahwa kompleksitas ekosistem RaaS (dibuktikan oleh Gray, Dhawan, Fachkha) menciptakan kondisi yang memungkinkan kooptasi oleh negara (dibuktikan oleh Milenkoski et al.).

### Potensi Kutipan Unggulan
- **Untuk framing urgensi:** Lonjakan dari gangguan operasional biasa ke ancaman nyata bagi keselamatan jiwa manusia (London hospitals/Qilin, 2024) adalah argumen kuat untuk pembuka paper.
- **Untuk argumen konvergensi:** "States are not building ransomware operations entirely from scratch. Instead, they are leveraging established ransomware infrastructure—relying on well-known affiliates, purchasing access, or deploying widely used strains like LockBit." (hal. 33) — gunakan parafrase, bukan kutipan langsung.
- **Untuk argumen vetting:** Fakta bahwa FBI mencatat bahwa aktor Iran (Pioneer Kitten) "menyembunyikan asal-usul Iran mereka dan tidak jelas tentang kebangsaan mereka saat berinteraksi dengan afiliasi ransomware" — ini membuktikan bahwa proses vetting ekosistem RaaS tidak mampu atau tidak berusaha mengidentifikasi aktor negara.

### Posisi dalam Galeri Literatur
Jika Gray et al. (2023) adalah *wajah dari dalam* ekosistem RaaS kriminal, maka Milenkoski et al. (2025) adalah *wajah dari luar*—bagaimana ekosistem tersebut dilihat dan dimanfaatkan oleh aktor negara. Keduanya bersama-sama membentuk gambaran lengkap bahwa ekosistem RaaS telah melampaui batas antara kejahatan dan geopolitik.


---

## 🏷️ Keywords

#raas #ransomware #state-sponsored #nation-state-actors #geopolitics #russia #north-korea #china #iran #plausible-deniability #cyber-espionage #apt #sandworm #lazarus #andariel #bronze-starlight #chamelgang #muddywater #pioneer-kitten #notpetya #wannacry #conti-fbs #entanglement #hybrid-warfare #cybercrime-ecosystem #threat-intelligence #milenkoski2025 #virtual-routes #pharos-series
