---
title: "Cybersecurity of remote work migration: A study on the VPN security landscape post covid-19 outbreak"
authors:
  - Qollakaj, Kushtrim
  - Einler Larsson, Lukas
year: 2023
venue: Blekinge Institute of Technology (BTH) - Bachelor Thesis
volume: "-"
pages: 1-46
doi: "-"
url: https://www.diva-portal.org/smash/get/diva2:1778036/FULLTEXT03.pdf
affiliation:
  - Faculty of Computing, Blekinge Institute of Technology, Sweden
tags:
  - vpn-security
  - initial-access-broker
  - iab
  - remote-work
  - mitre-attack
  - ransomware-access
  - apt
  - threat-intelligence
  - attack-vector
rating: 4
status: 🟡 reading
date_reviewed: 2026-05-28
type: academic-thesis
topic: initial-access-vectors
peer_reviewed: false
note: Tesis sarjana yang sangat berguna untuk memetakan TTPs (Tactics, Techniques, and Procedures) dari Initial Access Brokers (IABs) dan bagaimana aktor negara (APTs) memanfaatkan kerentanan infrastruktur jaringan korporat.
---

## 📌 Summary

Tesis ini mengkaji dampak migrasi kerja jarak jauh (*remote work*) pasca-wabah COVID-19 terhadap lanskap keamanan *Virtual Private Network* (VPN). Melalui tinjauan literatur sistematis (SLR) terhadap 81 laporan intelijen ancaman industri dan 25 makalah akademis, penulis mendokumentasikan lonjakan masif serangan terhadap VPN korporat, memetakan taktik spesifik penyerang menggunakan kerangka MITRE ATT&CK, dan merumuskan kerangka kerja *VPN hardening* untuk memitigasi eksploitasi akses awal oleh broker kriminal maupun aktor negara.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Transisi kerja jarak jauh yang mendadak memaksa 99% organisasi untuk mengorbankan postur keamanan demi ketersediaan akses. Pergeseran ini secara drastis memperluas permukaan serangan (*attack surface*), memindahkan perimeter keamanan dari jaringan korporat yang terkendali ke jaringan rumah yang rentan.
- **Gap yang diisi:** Meskipun banyak laporan insiden keamanan yang membahas peretasan VPN secara individual, terdapat kekosongan dalam agregasi taktik dan teknik operasional (*Modus Operandi*) penyerang secara sistematis menggunakan standar kerangka MITRE ATT&CK.
- **Signifikansi:** Kerentanan pada sistem VPN (seperti Fortinet, Pulse Secure, Citrix) tidak hanya mengakibatkan gangguan akses, melainkan memberikan penyerang—khususnya *Initial Access Brokers* (IAB) dan *Advanced Persistent Threats* (APT)—pijakan jaringan internal penuh yang memungkinkan pergerakan lateral (*lateral movement*) dan penyebaran ransomware berskala besar.

---

## 🎯 Contribution

1. **Pemetaan MITRE ATT&CK Komprehensif:** Mengonstruksi vektor serangan end-to-end yang mengagregasi taktik operasional dari berbagai insiden besar (melibatkan Cisco, Clearsky/Fox Kitten, Mandiant, CrowdStrike).
2. **Kuantifikasi Dampak Migrasi Remote Work:** Menyediakan data agregat terkait lonjakan serangan spesifik (misalnya, peningkatan 1919% pada serangan SSL-VPN Fortinet dan 1527% pada Pulse Connect Secure).
3. **Dokumentasi Tren Initial Access Broker (IAB):** Mengidentifikasi dan mendokumentasikan lonjakan sebesar 112% dalam aktivitas penjual IAB di forum *dark web* selama periode 2022.
4. **VPN Hardening Framework:** Menghasilkan kerangka kerja praktis empat pilar (Otentikasi Kuat, Enkripsi Robust, Manajemen Patch, dan Audit Berkelanjutan) untuk menutup celah akses awal.

---

## ⚙️ Methodology

- **Pendekatan:** *Systematic Literature Review* (SLR) Ganda.
- **SLR 1 (Fokus Lanskap Ancaman):** Menganalisis 81 laporan sekunder non-akademik (data kuantitatif dan kualitatif) dari firma keamanan siber terkemuka (CISA, Mandiant, CrowdStrike, Kaspersky, dll.) yang diterbitkan antara 2020–2023.
- **SLR 2 (Fokus Mitigasi):** Menganalisis 25 makalah riset *peer-reviewed* dari ACM, Scopus, dan IEEE untuk merumuskan kerangka kerja pertahanan.
- **Kerangka Analisis:** Menggunakan standar *MITRE ATT&CK Framework v13* untuk mengekstrak dan memetakan taktik, teknik, dan sub-teknik dari setiap laporan insiden.

---

## 📊 Key Results

### 1. Ledakan Aktivitas Initial Access Brokers (IAB)
Laporan ini mengonfirmasi komoditisasi akses jaringan. Penyerang mengeksploitasi kerentanan VPN bukan selalu untuk melancarkan serangan akhir, melainkan untuk mengekstraksi kredensial. CrowdStrike mencatat **peningkatan penjual IAB sebesar 112% di dark web pada tahun 2022**.

### 2. Vektor Akses Awal (Initial Access TTPs)
Eksploitasi VPN difokuskan pada dua teknik utama dalam MITRE ATT&CK:
* **T1190 (Exploit Public-Facing Application):** Pemanfaatan *zero-day* atau kerentanan yang belum di-*patch* (CVE-2018-13379 pada Fortinet, CVE-2019-11510 pada Pulse Secure).
* **T1078 (Valid Accounts):** Penggunaan kredensial yang dicuri melalui *spear-phishing*, *voice-phishing* (vishing), atau *credential stuffing* untuk masuk secara sah.

### 3. Konvergensi Taktik APT (Aktor Negara) dan Kriminal
Makalah ini menyoroti bahwa grup APT yang disponsori negara (misalnya: APT34/Iran dalam kampanye "Fox Kitten", dan UNC2630/Tiongkok) menggunakan infrastruktur eksploitasi VPN komersial yang *sama persis* dengan yang digunakan oleh afiliasi ransomware (seperti grup RagnarLocker). Mereka menggunakan pijakan ini untuk tujuan yang berbeda: spionase (APT) vs. pemerasan (Ransomware).

### 4. Eksekusi dan Modifikasi Infrastruktur (Defense Evasion)
Penyerang tidak sekadar mencuri data; mereka memodifikasi *binaries* aplikasi VPN (Pulse Secure) untuk memintas otentikasi multi-faktor (MFA) di masa depan (Teknik T1554 - *Compromise Client Software Binary*), menunjukkan tingkat kecanggihan teknis yang tinggi untuk menjaga persistensi akses.

---

## ⚠️ Limitations

- Tesis ini sangat bergantung pada laporan *threat intelligence* komersial yang mungkin memiliki bias pemasaran vendor atau tidak mempublikasikan detail forensik secara utuh.
- Mengandalkan interpretasi subjektif penulis saat memetakan narasi laporan insiden ke dalam kode teknik MITRE ATT&CK.
- Tidak ada eksperimen teknis *hands-on* atau pembuatan dataset serangan orisinal (murni analisis literatur sekunder).

---

## 🔗 Related Papers & Concepts

- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks ekosistem RaaS dan studi kasus Colonial Pipeline yang melengkapi studi kasus Boeing dan Royal Mail dalam laporan ini; keduanya sama-sama bersifat *entry-level* dan deskriptif.
- [[Gray et al. 2023 - Money Over Morals]] — Memberikan analisis empiris struktur organisasi dan bagi hasil RaaS (Conti) yang jauh lebih dalam dibanding angka 20-30% yang dikutip Bhattarai dari Trend Micro tanpa verifikasi independen.
- [[Dhawan et al. 2025 - Splitting the Spoils]] — Menyediakan data on-chain tentang rasio bagi hasil RaaS secara industri-luas (85:15 afiliasi:developer), yang dapat digunakan untuk mengkontekstualisasikan klaim 20-30% pada laporan ini—menunjukkan adanya variasi rasio antar sumber yang perlu dikritisi.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Menjelaskan secara teknis mengapa *concept drift* dan modularitas kode menjadi strategi bertahan RaaS; relevan untuk mengonfirmasi temuan anti-analisis/anti-VM pada LockBit 3.0 dalam laporan ini.
- [[Milenkoski et al. 2025 - Ransomwares New Masters]] (Tumpang tindih antara taktik APT negara dan aktor ransomware)
- [[Initial Access Broker (IAB)]]
- [[MITRE ATT&CK - Ransomware]]
- [[Concept Drift in Malware Detection]]

### Key References dari Tesis Ini
- CrowdStrike (2023) — *Global Threat Report* (Sumber data peningkatan 112% IAB).
- Mandiant (2021) — *Check Your Pulse: Suspected APT Actors Leverage Authentication Bypass Techniques and Pulse Secure Zero-Day*.
- ClearSky (2020) — *Fox Kitten Campaign Widespread Iranian Espionage-Offensive Campaign*.

---

## 💡 My Notes

**Sintesis Tata Kelola & Ekosistem RaaS (Fokus RQ2 & Aktor Negara):**

Tesis ini adalah jembatan teknis yang esensial untuk menjelaskan **"Bagaimana IAB benar-benar mendapatkan barang dagangannya?"** dalam konteks RQ2. 

Banyak literatur tata kelola RaaS mengasumsikan bahwa akses awal (kredensial VPN atau RDP) *tiba-tiba* tersedia di pasar gelap. Qollakaj & Larsson membuktikan bahwa akuisisi akses awal adalah operasi teknis skala industri yang masif. Peningkatan 112% penjual IAB membuktikan bahwa **IAB telah bermutasi menjadi entitas ekonomi yang sepenuhnya mandiri** dalam ekosistem RaaS. Mereka tidak perlu berafiliasi dengan developer ransomware (seperti LockBit atau Conti); mereka cukup fokus menjadi "penambang bahan baku" (akses VPN) untuk kemudian dilelang.

**Koneksi dengan State-Sponsored Actors (Batasan Scope / "Jebakan"):**
Tesis ini mendokumentasikan kampanye "Fox Kitten" dari Iran dan operasi APT Tiongkok yang mengeksploitasi celah VPN yang identik dengan yang digunakan kelompok kriminal. Ini memberikan dasar argumentasi yang sangat rasional mengapa negara tertarik menggunakan ekosistem RaaS: **Infrastruktur aksesnya sudah dikomoditisasi**. Intelijen negara tidak perlu repot meretas perusahaan dari nol; mereka cukup *membeli* akses VPN yang telah dieksploitasi oleh IAB kriminal di *dark web*, menyusup untuk melakukan spionase intelijen, lalu mungkin menanam ransomware komoditas sebagai pengalih perhatian (*plausible deniability*). Operasi IAB mengaburkan batas antara kejahatan murni dan spionase negara secara operasional.

---

## 🏷️ Keywords

#initial-access-broker #iab #vpn-vulnerability #remote-work-security #mitre-attack #apt34 #fox-kitten #ransomware-access #threat-intelligence #credential-harvesting #state-sponsored-nexus #cybercrime-supply-chain