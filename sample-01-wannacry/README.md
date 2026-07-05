# Sample 01 — Static Analysis of WannaCry Binary

**Sample:** WannaCry.exe  
**Analysis Type:** Static Analysis  
**Operating System:** Microsoft Windows  
**Format:** Portable Executable (PE)  
**Analysis Date:** _(Isi sesuai tanggal analisis)_  

---

# Pendahuluan

Dokumen ini berisi hasil analisis statis terhadap binary **WannaCry.exe** menggunakan beberapa tools Reverse Engineering. Analisis dilakukan tanpa menjalankan executable sehingga seluruh informasi diperoleh melalui pemeriksaan struktur internal file Portable Executable (PE).

Tujuan analisis ini adalah memahami karakteristik dasar executable, mengidentifikasi library yang digunakan, memperoleh informasi dari strings, serta mengamati struktur binary sebagai langkah awal dalam proses Reverse Engineering.

---

# 1. Triage

Tahap pertama adalah melakukan identifikasi awal terhadap executable.

| Atribut | Nilai |
|---------|-------|
| Nama File | WannaCry.exe |
| Format | PE32 / PE32+ |
| Arsitektur | x86 / x64 |
| Operating System | Microsoft Windows |
| Compiler | Microsoft Visual C/C++ |
| Packer | Packed / Compressed (.rsrc) |

---

# 2. Hash File

Hash digunakan sebagai identitas unik executable sehingga dapat membantu proses identifikasi maupun pencarian informasi pada database malware.

| Algoritma | Nilai |
|-----------|-------|
| MD5 | `84c82835a5d21bbcf75a61706d8ab549` |
| SHA-256 | `ed01ebfbc9eb5bbea545af4d01bf5f1071661840480439c6e5babe8e080e41aa` |

---

# 3. Tools yang Digunakan

Analisis dilakukan menggunakan beberapa tools berikut.

- Detect It Easy (DIE)
- PEStudio
- Ghidra
- IDA Free
- HxD
- CertUtil / SHA256SUM

---

# 4. Header Analysis

Header Analysis dilakukan untuk memperoleh informasi dasar mengenai executable.

Beberapa informasi penting yang berhasil diidentifikasi antara lain:

| Parameter | Hasil |
|-----------|-------|
| File Format | Portable Executable (PE) |
| Entry Point | PE32 Executable Entry Point |
| Image Base | PE32 Windows Executable |
| Architecture | x86 / x64 |
| Number of Sections | .text, .rdata, .data, .rsrc |

### Hasil Analisis

Header menunjukkan bahwa executable menggunakan format **Portable Executable (PE)** yang merupakan format standar pada sistem operasi Windows.

Informasi seperti Entry Point dan Image Base memberikan gambaran bagaimana executable dipetakan ke dalam memori sebelum dijalankan oleh sistem operasi.

> **Screenshot**
>
> Tambahkan screenshot hasil Detect It Easy atau PEStudio.
>
> **Referensi PPT Kelompok 7:** gunakan slide yang menampilkan hasil identifikasi PE Header / Detect It Easy.

---

# 5. Section Analysis

Executable terdiri atas beberapa section dengan fungsi yang berbeda.

| Section | Fungsi |
|---------|--------|
| `.text` | Menyimpan instruksi machine code |
| `.data` | Menyimpan data yang dapat berubah |
| `.rdata` | Menyimpan data read-only |
| `.rsrc` | Menyimpan resource program |

### Hasil Analisis

Seluruh section yang ditemukan merupakan section standar pada executable Windows.

Section `.text` berisi instruksi yang akan dieksekusi prosesor, sedangkan `.data` dan `.rdata` menyimpan berbagai informasi yang digunakan selama program berjalan. Section `.rsrc` umumnya digunakan untuk menyimpan icon, dialog, maupun resource lain yang dimiliki executable.

> **Screenshot**
>
> Gunakan screenshot tampilan Section View dari PEStudio atau DIE.
>
> **Referensi PPT Kelompok 7:** slide yang menampilkan daftar section executable.

---

# 6. Strings Analysis

Analisis strings dilakukan untuk menemukan informasi tekstual yang tersimpan di dalam executable.

Beberapa string yang berhasil ditemukan antara lain:

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

### Hasil Analisis

Strings memberikan petunjuk awal mengenai kemungkinan perilaku executable.

Keberadaan ekstensi dokumen seperti `.doc`, `.xlsx`, `.pdf`, dan `.jpg` menunjukkan bahwa executable berinteraksi dengan berbagai jenis file. Selain itu, ditemukan nama beberapa Windows API yang berkaitan dengan operasi file dan registry.

> **Screenshot**
>
> Tambahkan hasil Strings Analysis.
>
> **Referensi PPT Kelompok 7:** slide yang menampilkan hasil Strings.

---

# 7. Import Function Analysis

Executable memanfaatkan beberapa library bawaan Windows.

| DLL | Fungsi |
|-----|--------|
| KERNEL32.dll | Operasi dasar sistem |
| USER32.dll | Antarmuka pengguna |
| ADVAPI32.dll | Registry & Security API |
| MSVCRT.dll | Microsoft C Runtime |

### Hasil Analisis

Import table menunjukkan bahwa executable menggunakan berbagai Windows API untuk menjalankan fungsi-fungsi sistem.

Informasi ini membantu memperkirakan kemampuan executable tanpa perlu menjalankannya, misalnya operasi file, akses registry, maupun komunikasi dengan sistem operasi.

> **Screenshot**
>
> Tambahkan tampilan Import Table.
>
> **Referensi PPT Kelompok 7:** slide yang memperlihatkan daftar import DLL.

---

# 8. Indicators of Compromise (IOC)

| Jenis | Nilai |
|-------|-------|
| Nama File | tasksche.exe |
| MD5 | 84c82835a5d21bbcf75a61706d8ab549 |
| SHA-256 | ed01ebfbc9eb5bbea545af4d01bf5f1071661840480439c6e5babe8e080e41aa |
| Compiler | Microsoft Visual C/C++ |
| Packer | Packed / Compressed |

IOC dapat digunakan sebagai identitas digital executable sehingga memudahkan proses identifikasi pada berbagai platform analisis malware.

---

# 9. Ringkasan Hasil Analisis

Berdasarkan hasil Static Analysis diperoleh beberapa informasi berikut:

- Binary menggunakan format Portable Executable (PE).
- Memiliki struktur section standar Windows.
- Menggunakan beberapa Windows API melalui import library.
- Ditemukan berbagai strings yang memberikan gambaran awal mengenai karakteristik executable.
- Analisis dilakukan tanpa menjalankan program sehingga tidak diperoleh informasi mengenai perilaku runtime.

---

# 10. Kesimpulan

Static Analysis merupakan tahapan awal yang penting dalam proses Reverse Engineering karena mampu memberikan banyak informasi tanpa harus mengeksekusi executable.

Melalui analisis terhadap header, section, strings, import table, dan hash file, diperoleh gambaran umum mengenai struktur internal binary serta karakteristik executable. Informasi tersebut dapat dijadikan dasar untuk menentukan langkah analisis berikutnya, seperti Dynamic Analysis atau proses Reverse Engineering yang lebih mendalam.

---

# Disclaimer

Dokumen ini dibuat untuk tujuan edukasi sebagai bagian dari pembelajaran mata kuliah Reverse Engineering.

Binary asli tidak disertakan di dalam repository. Seluruh analisis dilakukan pada lingkungan laboratorium/virtual machine untuk kepentingan pembelajaran keamanan siber.
