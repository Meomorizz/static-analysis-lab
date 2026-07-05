# Static Analysis Lab

Repository ini berisi dokumentasi hasil praktikum **Static Analysis** terhadap beberapa binary **Portable Executable (PE)** sebagai bagian dari pembelajaran mata kuliah **Reverse Engineering**.

Seluruh analisis dilakukan menggunakan pendekatan **Static Analysis**, yaitu proses mengamati struktur internal executable tanpa menjalankan program secara langsung. Melalui metode ini, berbagai informasi penting seperti format file, struktur section, import library, strings, hash, hingga karakteristik executable dapat diperoleh sebagai dasar sebelum melakukan analisis lanjutan.

Repository ini dibuat sebagai portofolio pembelajaran sekaligus dokumentasi proses analisis yang dilakukan selama perkuliahan.

---

# Tujuan Repository

Repository ini bertujuan untuk:

- Mendokumentasikan hasil analisis statis terhadap binary PE.
- Memahami struktur Portable Executable (PE) pada sistem operasi Windows.
- Mempelajari penggunaan berbagai tools Reverse Engineering.
- Mengidentifikasi karakteristik executable melalui header, section, strings, dan import table.
- Melatih kemampuan membuat laporan analisis yang sistematis dan mudah dipahami.

---

# Tools yang Digunakan

Beberapa tools yang digunakan selama proses analisis antara lain:

- Detect It Easy (DIE)
- PEStudio
- Ghidra
- IDA Free
- HxD
- CertUtil / SHA256SUM


# Daftar Analisis

| Sample | Binary | Jenis Analisis | Status |
|---------|--------|----------------|--------|
| Sample 01 | WannaCry.exe | Static Analysis | ✅ Selesai |
| Sample 02 | Binary PE Sample | Static Analysis | 🔄 Dalam Proses |

---

# Metodologi Analisis

Setiap laporan analisis disusun menggunakan alur yang sama agar proses dokumentasi lebih terstruktur.

Tahapan analisis meliputi:

1. Triage awal terhadap executable.
2. Identifikasi hash file (MD5 & SHA-256).
3. Pemeriksaan format Portable Executable (PE).
4. Analisis Header dan Section.
5. Analisis Strings.
6. Analisis Import Table.
7. Penyusunan kesimpulan berdasarkan hasil observasi.

Seluruh proses dilakukan tanpa mengeksekusi binary sehingga analisis tetap berada pada kategori **Static Analysis**.

---

# Hasil Pembelajaran

Melalui repository ini saya mempelajari beberapa konsep penting dalam Reverse Engineering, antara lain:

- Struktur Portable Executable (PE)
- Header Analysis
- Section Analysis
- Import Function Analysis
- Strings Analysis
- Indicators of Compromise (IOC)
- Penggunaan tools analisis executable
- Dokumentasi hasil analisis secara sistematis

---

# Disclaimer

Repository ini dibuat untuk **tujuan edukasi** sebagai bagian dari pembelajaran mata kuliah **Reverse Engineering**.

Binary asli tidak diunggah ke repository ini. Seluruh dokumentasi hanya berisi hasil observasi dan analisis terhadap executable yang dilakukan pada lingkungan laboratorium/virtual machine untuk kepentingan penelitian dan pembelajaran keamanan siber.
