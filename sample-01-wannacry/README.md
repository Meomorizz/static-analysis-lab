# Sample 01 — Static Analysis of WannaCry Executable

**Binary:** WannaCry.exe  
**Jenis Analisis:** Static Analysis  
**Platform:** Microsoft Windows  
**Format Binary:** Portable Executable (PE)  
**Status:** Completed

---

# Pendahuluan

Dokumen ini berisi hasil analisis statis terhadap binary **WannaCry.exe** sebagai bagian dari pembelajaran Reverse Engineering. Analisis dilakukan tanpa menjalankan executable sehingga seluruh informasi diperoleh melalui observasi terhadap struktur internal file menggunakan berbagai tools analisis executable.

Static Analysis merupakan tahapan awal yang penting karena mampu memberikan gambaran mengenai karakteristik binary, library yang digunakan, struktur file, hingga indikasi perilaku program tanpa menimbulkan risiko menjalankan executable secara langsung.

---

# Tujuan Analisis

Analisis ini dilakukan untuk:

- Mengidentifikasi karakteristik dasar executable.
- Memahami struktur Portable Executable (PE).
- Mengidentifikasi library Windows yang digunakan.
- Menemukan informasi penting melalui Strings Analysis.
- Mengamati struktur executable sebagai dasar proses Reverse Engineering.

---

# Tools yang Digunakan

Selama proses analisis digunakan beberapa tools berikut:

- Detect It Easy (DIE)
- PEStudio
- Ghidra
- IDA Free
- HxD
- CertUtil / SHA256SUM

---

# 1. Triage

Tahap triage dilakukan untuk memperoleh informasi awal mengenai executable sebelum memasuki analisis yang lebih mendalam.

| Atribut | Nilai |
|---------|-------|
| Nama File | WannaCry.exe |
| Format | PE32 / PE32+ |
| Arsitektur | x86 / x64 |
| Operating System | Microsoft Windows |
| Compiler | Microsoft Visual C/C++ |
| Packer | Packed / Compressed (.rsrc) |

Berdasarkan hasil identifikasi awal, executable menggunakan format **Portable Executable (PE)** yang merupakan format standar aplikasi pada sistem operasi Windows.

---

# 2. Hash File

Hash digunakan sebagai identitas unik executable sehingga memudahkan proses identifikasi maupun pencocokan dengan database malware.

| Algoritma | Nilai |
|-----------|-------|
| MD5 | `84c82835a5d21bbcf75a61706d8ab549` |
| SHA-256 | `ed01ebfbc9eb5bbea545af4d01bf5f1071661840480439c6e5babe8e080e41aa` |

Hash tersebut dapat digunakan untuk memastikan integritas file maupun mencari informasi tambahan pada platform analisis malware.

---

# 3. Header Analysis

Analisis header bertujuan untuk mengetahui informasi dasar executable seperti format file, arsitektur, entry point, image base, serta struktur section.

| Parameter | Hasil |
|-----------|-------|
| Format File | Portable Executable (PE) |
| Entry Point | PE32 Executable Entry Point |
| Image Base | PE32 Windows Executable |
| Architecture | x86 / x64 |
| Number of Sections | `.text`, `.rdata`, `.data`, `.rsrc` |

Hasil pemeriksaan menunjukkan bahwa executable masih menggunakan struktur Portable Executable standar Windows. Informasi tersebut memberikan gambaran mengenai bagaimana sistem operasi akan memuat program ke dalam memori ketika dijalankan.

<p align="center">
    <img src="./screenshots/PEHeader.png" width="850">
</p>

---

# 4. Section Analysis

Executable memiliki beberapa section utama yang menyimpan kode program maupun data yang diperlukan selama proses eksekusi.

| Section | Fungsi |
|---------|--------|
| `.text` | Menyimpan instruksi machine code |
| `.data` | Menyimpan data yang dapat berubah |
| `.rdata` | Menyimpan data read-only |
| `.rsrc` | Menyimpan resource program |

Keberadaan section tersebut menunjukkan bahwa executable masih mengikuti struktur PE standar. Setiap section memiliki fungsi yang berbeda sehingga membantu analis memahami bagaimana program diorganisasikan sebelum dilakukan analisis lebih lanjut.

---

# 5. Strings Analysis

Analisis strings dilakukan untuk menemukan teks yang tersimpan di dalam executable.

Beberapa string yang ditemukan antara lain:

```text
.doc
.docx
.xls
.xlsx
.pdf
.jpg
.zip
.wnry
CreateFile
WriteFile
MoveFile
RegSetValueExA
```

Keberadaan ekstensi berbagai jenis dokumen menunjukkan bahwa executable memiliki kemungkinan berinteraksi dengan file pengguna. Selain itu ditemukan beberapa nama Windows API yang berhubungan dengan operasi file dan registry sehingga memberikan gambaran awal mengenai kemampuan executable.

<p align="center">
    <img src="./screenshots/string.png" width="850">
</p>

---

# 6. Import Function Analysis

Import Table digunakan untuk mengetahui library Windows yang dipanggil oleh executable selama proses eksekusi.

| DLL | Fungsi |
|-----|--------|
| KERNEL32.dll | Operasi dasar sistem |
| USER32.dll | Antarmuka pengguna |
| ADVAPI32.dll | Registry dan Security API |
| MSVCRT.dll | Microsoft C Runtime |

Import library tersebut menunjukkan bahwa executable memanfaatkan berbagai Windows API untuk melakukan operasi dasar sistem, manipulasi file, pengelolaan registry, serta fungsi runtime yang disediakan oleh Microsoft C Runtime Library.

<p align="center">
    <img src="./screenshots/importfunc.png" width="850">
</p>

---

# 7. Indicators of Compromise (IOC)

| Jenis | Nilai |
|-------|-------|
| File Name | tasksche.exe |
| MD5 | 84c82835a5d21bbcf75a61706d8ab549 |
| SHA-256 | ed01ebfbc9eb5bbea545af4d01bf5f1071661840480439c6e5babe8e080e41aa |
| Compiler | Microsoft Visual C/C++ |
| Packer | Packed / Compressed |

Informasi IOC dapat dimanfaatkan sebagai identitas digital executable sehingga mempermudah proses identifikasi maupun korelasi terhadap laporan analisis lainnya.

---

# 8. Ringkasan Analisis

Selama proses Static Analysis diperoleh beberapa temuan penting, di antaranya:

- Binary menggunakan format Portable Executable (PE).
- Memiliki struktur section standar Windows.
- Menggunakan beberapa Windows API melalui Import Table.
- Ditemukan berbagai strings yang memberikan petunjuk mengenai karakteristik executable.
- Analisis dilakukan sepenuhnya tanpa menjalankan binary.

---

# 9. Kesimpulan

Static Analysis memberikan gambaran awal mengenai struktur internal executable tanpa perlu menjalankan program secara langsung. Informasi yang diperoleh dari Header Analysis, Section Analysis, Strings Analysis, Import Function Analysis, serta Hash File mampu membantu memahami karakteristik dasar executable sebelum dilakukan analisis lanjutan seperti Dynamic Analysis maupun proses Reverse Engineering yang lebih mendalam.

Melalui proses ini dapat disimpulkan bahwa metode Static Analysis merupakan tahapan yang aman dan efektif untuk mengidentifikasi struktur binary, memahami komponen penting executable, serta menyusun hipotesis awal mengenai fungsi program berdasarkan artefak yang tersedia.

---

# Disclaimer

Repository ini dibuat untuk tujuan edukasi sebagai bagian dari pembelajaran mata kuliah **Reverse Engineering**.

Binary asli tidak disertakan di dalam repository. Seluruh dokumentasi hanya berisi hasil observasi dan analisis yang dilakukan pada lingkungan laboratorium atau virtual machine untuk kepentingan pembelajaran keamanan siber.
