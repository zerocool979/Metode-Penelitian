---
title: "Banning ransomware payments: unintended effects on cybersecurity investment and incident reporting"
authors:
  - Iwasaki, Masaki
year: 2025
venue: International Cybersecurity Law Review
volume: Vol. 6
pages: 17-27
doi: https://doi.org/10.1365/s43439-025-00137-5
tags:
  - ransomware-payments
  - cybersecurity-investment
  - incident-reporting
  - safe-harbor
  - economic-incentives
  - cyber-law
  - policy-analysis
rating: 5
status: 🟡 reading
date_reviewed: 2026-06-07
type: journal-article
topic: ransomware-policy
---

## 📌 Summary

Paper ini menggunakan pendekatan ekonomi untuk menganalisis dampak dari usulan kebijakan larangan pembayaran uang tebusan (*ransomware payments ban*). Meskipun kebijakan ini dirancang untuk memutus aliran dana kriminal dan memaksa perusahaan memperkuat pertahanan mereka, Iwasaki membuktikan bahwa pelarangan total (*blanket ban*) secara paradoks dapat menurunkan tingkat investasi keamanan siber dan mendorong organisasi untuk menyembunyikan insiden serangan. Sebagai solusinya, penulis menawarkan kerangka alternatif yang mengombinasikan standardisasi keamanan siber, perluasan undang-undang pelaporan pelanggaran data, serta penyediaan jalur *conditional safe harbor* bagi korban.

---

## ❓ Problem Statement

- **Masalah yang diangkat:** Kebijakan pelarangan total pembayaran tebusan ransomware dianggap sebagai solusi mutlak untuk melumpuhkan model bisnis penyerang, namun berpotensi memicu konsekuensi negatif yang tidak terduga bagi organisasi dan masyarakat luas.
- **Gap yang diisi:** Model-model ekonomi ransomware sebelumnya belum mengeksplorasi analisis terperinci mengenai sanksi pembayaran tebusan secara holistik yang mengaitkannya langsung dengan insentif investasi pra-insiden dan pelaporan pasca-insiden.
- **Signifikansi:** Menghilangkan opsi pembayaran secara total dalam situasi kritis dapat memicu keruntuhan operasional yang ireversibel, kebangkrutan, hingga ancaman keselamatan jiwa (seperti serangan pada rumah sakit). Hal ini juga berisiko mendorong ekosistem tebusan masuk ke area bawah tanah (*shadow economy*) yang tidak terpantau.

---

## 🎯 Contribution

1. **Integrasi Analisis Holistik:** Mengintegrasikan variabel investasi keamanan siber, pelaporan insiden, dan pembayaran tebusan ke dalam satu model analisis ekonomi yang utuh.
2. **Pembuktian Paradoks Insentif:** Membuktikan secara teoretis bahwa mempertahankan opsi legal untuk membayar tebusan pada kondisi darurat justru dapat memperkuat motivasi perusahaan untuk berinvestasi pada keamanan siber.
3. **Formulasi Kebijakan Tiga Pilar:** Menyusun draf kebijakan alternatif berbasis regulasi pragmatis (Standardisasi, Transparansi Pelaporan, dan *Safe Harbor*) untuk menggantikan pendekatan *blanket ban* yang kaku.

---

## ⚙️ Methodology

- **Pendekatan:** Analisis ekonomi mikro normatif dan pemodelan keputusan berbasis asumsi rasionalitas agen ekonomi (*rational economic agents*).
- **Struktur Pemodelan:** Interaksi disederhanakan menjadi model keputusan tiga tahap antara satu korporasi sebagai potensi korban dan satu pelaku kriminal:
  * *Tahap 1:* Korporasi memutuskan tingkat investasi keamanan siber pra-insiden.
  * *Tahap 2:* Kriminal memutuskan untuk menyerang atau tidak, serta memilih menggunakan ransomware enkripsi biasa atau metode ganda (*data-stealing ransomware*).
  * *Tahap 3:* Jika serangan berhasil, kriminal meminta tebusan dan korban memutuskan opsi pembayaran berbasis perbandingan keuntungan bersih.
- **Konteks Hukum:** Berfokus pada dinamika regulasi siber di Amerika Serikat (seperti advisories OFAC & FinCEN, CFAA, aturan SEC, proposal CIRCIA oleh CISA, serta NY SHIELD Act) sebagai baseline analisis.

---

## 📊 Key Results & Framework

- **Kegagalan Deteksi Blanket Ban:** Efektivitas pelarangan total sangat bergantung pada kemampuan pemerintah mendeteksi transaksi ilegal. Mengingat penyerang memanfaatkan mata uang kripto dan pencucian uang yang canggih, penegakan sanksi yang buta justru mendorong korban menyembunyikan serangan demi kelangsungan bisnisnya.
- **Mekanisme Paradoks Investasi:** Investasi keamanan siber memiliki nilai utilitas yang lebih tinggi jika perusahaan memiliki opsi bertahan hidup. Pertahanan yang kuat meminimalkan biaya restorasi mandiri dan mencegah pencurian data (*data-theft prevention*) walaupun enkripsi tetap terjadi. Jika larangan total diterapkan dan bisnis dipastikan hancur saat enkripsi sukses, motivasi margin untuk berinvestasi siber di awal justru menurun.

### Komponen Kerangka Kerja Alternatif (3 Pilar)

| Pilar Kebijakan               | Detail Mekanisme                                                                                                                                                                           | Dampak terhadap Insentif                                                                            |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- |
| **Standardisasi Keamanan**    | Mengodifikasi parameter keamanan siber yang dianggap "layak" (*reasonable security standards*) secara konkret seperti model NY SHIELD Act, dilengkapi sanksi denda administratif.          | Meningkatkan kesadaran korporat dan memberikan panduan investasi yang jelas.                        |
| **Perluasan Hukum Pelaporan** | Memperluas definisi ambang batas pelaporan insiden pelanggaran data agar mencakup *unauthorized access* secara umum, bukan hanya *unauthorized acquisition* (pencurian data konvensional). | Menutup celah teknis bagi perusahaan untuk menghindari keterbukaan publik pasca-insiden.            |
| **Conditional Safe Harbor**   | Memberikan pembebasan sanksi hukum atas pembayaran tebusan HANYA jika korban memenuhi standar keamanan minimum pra-insiden dan melapor dalam jendela waktu ketat pasca-serangan.           | Mendorong transparansi kolektif, mitigasi risiko *underinvestment*, dan menjaga resiliensi ekonomi. |

---

## ⚠️ Limitations

- Pemodelan disederhanakan pada pola interaksi satu-lawan-satu (*one corporation and one criminal*), belum mencakup kompleksitas rantai pasok (*supply chain*).
- Analisis sangat bergantung pada premis bahwa pelaku kejahatan siber bertindak rasional untuk selalu menepati janji dekripsi mereka demi menjaga reputasi komersial grupnya.
- Dokumen berfokus pada ekosistem hukum dan korporasi di wilayah Amerika Serikat, sehingga memerlukan penyesuaian khusus jika diadopsi ke dalam yurisdiksi hukum negara lain.

---

## 🔗 Related Papers & Concepts

- [[Iwasaki & Masaki 2025 - Banning ransomware payments]] — Membangun di atas fondasi Laszka et al. untuk menganalisis dampak kebijakan pelarangan pembayaran tebusan; secara eksplisit mengutip paper ini sebagai referensi utama.
- [[Masakapalli & Vodapally 2025 - RaaS Emerging Threats]] — Memberikan konteks ekosistem RaaS modern yang relevan sebagai pembaruan atas asumsi "single attacker" dalam model Laszka.
- [[Fachkha et al. 2025 - RaaS and Its Evolution]] — Menjelaskan kompleksitas teknis evolusi ransomware yang menjadi konsekuensi dari model bisnis RaaS.
- [[Ransomware Payments Regulation]]
- [[Cybersecurity Economics and Incentives]]
- [[Data Breach Notification Laws]]
- [[Safe Harbor Compliance]]

### Key References dari Paper Ini
- Cartwright et al. (2019) — *To pay or not: game theoretic models of ransomware*.
- Laszka et al. (2017) — *On the economics of ransomware*.
- Iwasaki (2024) — *Cybersecurity coordination in supply chains and competition rules*.
- Westbrook (2022) — *Safe harbor for ransomware payments: protecting stakeholders, hardening targets and defending national security*.

---

## 💡 My Notes

- **Koneksi Riset Utama (RQ3):** Paper ini memberikan landasan teoritis yang luar biasa kuat untuk menjawab argumen tata kelola organisasi pada RQ3.Penulis membuktikan bahwa tata kelola kaku dari regulator (*blanket ban*) melahirkan *perverse incentives* yang justru melemahkan keamanan siber nasional dan mendorong interaksi ke area bawah tanah (*shadow economy*).
- **Nexus dengan Aktor Negara:** Kita bisa menggunakan tesis Iwasaki mengenai "transaksi di bawah bayang-bayang sanksi" untuk menjelaskan mengapa aktor negara (*state-sponsored actors*) tertarik memelihara ekosistem RaaS. Ketika regulasi formal membuat korban ketakutan untuk melapor, ruang gelap tersebut menjadi inkubator operasional yang ideal bagi intelijen negara untuk melakukan kooptasi taktis tanpa terdeteksi publik (*plausible deniability*).

---

## 🏷️ Keywords

#ransomware-payments #cybersecurity-investment #incident-reporting #safe-harbor #economic-incentives #cybersec-policy #cyber-law #incentive-design #blanket-ban #shiled-act #ofac