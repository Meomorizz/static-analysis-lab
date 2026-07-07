# Sample 02 — Static Analysis of Notepad++ Installer

**Sample:** npp.8.9.6.2.Installer.x64.exe  
**Analysis Type:** Static Analysis  
**Operating System:** Microsoft Windows  
**Format:** Portable Executable (PE32)  
**Analysis Date:** _(Isi sesuai tanggal analisis)_

---

# 📖 Pendahuluan

Dokumen ini berisi hasil analisis statis terhadap file installer **Notepad++ v8.9.6.2 x64** menggunakan metode **Static Analysis**. Analisis dilakukan tanpa menjalankan executable sehingga informasi diperoleh melalui pemeriksaan struktur internal file Portable Executable (PE).

Tujuan analisis ini adalah memahami karakteristik dasar executable, mengidentifikasi struktur PE, library yang digunakan, strings yang terdapat di dalam binary, serta import function yang dimanfaatkan oleh aplikasi.

---

# 1. Informasi File

| Atribut | Nilai |
|---------|-------|
| Nama File | npp.8.9.6.2.Installer.x64.exe |
| Format | PE32 |
| Operating System | Microsoft Windows |
| Arsitektur | x86 (GUI) |
| Compiler | Microsoft Visual C/C++ |
| Linker | Microsoft Linker 6.0 |
| Installer | NSIS (Nullsoft Scriptable Install System) |
| Overlay | NSIS Data |

---

# 2. Tools yang Digunakan

Analisis dilakukan menggunakan beberapa tools berikut.

- Detect It Easy (DIE)
- PE Viewer
- Windows Terminal

---

# 3. PE Header Analysis

Tahap pertama dilakukan dengan mengidentifikasi informasi dasar executable menggunakan Detect It Easy.

Dari hasil analisis diketahui bahwa file menggunakan format **Portable Executable (PE32)** dengan target sistem operasi Microsoft Windows. Executable dikompilasi menggunakan **Microsoft Visual C/C++** dan memanfaatkan **NSIS (Nullsoft Scriptable Install System)** sebagai installer.

Informasi ini menunjukkan bahwa file merupakan installer resmi aplikasi Notepad++ yang dibangun menggunakan framework instalasi NSIS.

| Parameter | Hasil |
|-----------|-------|
| File Format | PE32 |
| Operating System | Windows |
| Architecture | x86 |
| Compiler | Microsoft Visual C/C++ |
| Installer | NSIS |
| Linker | Microsoft Linker 6.0 |

![PE Header](screenshots/pe-header.png)

---

# 4. Hash Analysis

Hash digunakan sebagai identitas unik executable sehingga memudahkan proses identifikasi maupun verifikasi integritas file.

Berdasarkan hasil analisis diperoleh nilai hash sebagai berikut.

| Algoritma | Nilai |
|-----------|-------|
| MD5 | c84f188a37397bf5b607eb02a4bfde05 |

Nilai hash dapat digunakan untuk memastikan bahwa file yang dianalisis identik dengan file yang diperoleh dari sumber resmi.

![Hash Analysis](screenshots/hash.png)

---

# 5. Import Function Analysis

Executable memanfaatkan beberapa Dynamic Link Library (DLL) bawaan Windows untuk menjalankan fungsi-fungsi sistem.

Beberapa library yang berhasil diidentifikasi antara lain:

| DLL | Fungsi |
|-----|--------|
| ADVAPI32.dll | Registry dan Security API |
| SHELL32.dll | Operasi Shell Windows |
| ole32.dll | COM Library |
| COMCTL32.dll | Windows Common Controls |
| USER32.dll | Antarmuka Pengguna |

Keberadaan import library tersebut menunjukkan bahwa installer memanfaatkan Windows API untuk melakukan konfigurasi sistem, manipulasi registry, pengelolaan antarmuka pengguna, serta proses instalasi aplikasi.

![Import Function](screenshots/import-function.png)

---

# 6. Strings Analysis

Analisis strings dilakukan untuk menemukan informasi tekstual yang tersimpan di dalam executable.

Beberapa string yang berhasil ditemukan antara lain:

```text
ole32.dll
ImageList_Destroy
ImageList_DrawMasked
ImageList_Create
COMCTL32.dll
DrawTextW
FillRect
GetClientRect
BeginPaint
DefWindowProcW
```

Sebagian besar string yang ditemukan berkaitan dengan komponen antarmuka pengguna (GUI) Windows serta library sistem yang digunakan selama proses instalasi.

Informasi ini memberikan gambaran awal mengenai fungsi executable tanpa perlu menjalankannya.

![Strings Analysis](screenshots/strings.png)

---

# 7. Ringkasan Hasil Analisis

Berdasarkan proses Static Analysis diperoleh beberapa informasi penting sebagai berikut.

- Executable menggunakan format **Portable Executable (PE32)**.
- Target sistem operasi adalah Microsoft Windows.
- Installer dibuat menggunakan **NSIS (Nullsoft Scriptable Install System)**.
- Dikompilasi menggunakan Microsoft Visual C/C++.
- Memanfaatkan beberapa Windows API melalui import library.
- Ditemukan berbagai strings yang berkaitan dengan komponen GUI Windows.
- Analisis dilakukan sepenuhnya tanpa menjalankan executable.

---

# 8. Kesimpulan

Static Analysis memberikan gambaran awal mengenai struktur internal executable tanpa perlu menjalankan program secara langsung.

Dari hasil analisis dapat diketahui bahwa installer Notepad++ menggunakan format **Portable Executable (PE32)**, dikompilasi menggunakan Microsoft Visual C/C++, serta memanfaatkan NSIS sebagai framework instalasi. Selain itu, executable menggunakan berbagai Windows API melalui import library dan menyimpan sejumlah strings yang berkaitan dengan antarmuka pengguna Windows.

Informasi tersebut sangat berguna sebagai tahap awal dalam proses Reverse Engineering karena membantu memahami karakteristik executable sebelum dilakukan analisis yang lebih mendalam seperti Dynamic Analysis.

---

# 📄 Disclaimer

Dokumen ini dibuat untuk tujuan edukasi sebagai bagian dari pembelajaran mata kuliah Reverse Engineering.

Executable yang dianalisis merupakan installer resmi **Notepad++** yang tersedia untuk umum. Analisis dilakukan menggunakan metode Static Analysis tanpa menjalankan maupun memodifikasi file executable.