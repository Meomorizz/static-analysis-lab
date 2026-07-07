# Static Analysis Lab

Repository ini berisi dokumentasi hasil praktikum **Static Analysis** terhadap beberapa file **Portable Executable (PE)** sebagai bagian dari proses pembelajaran mata kuliah **Reverse Engineering**.

Static Analysis merupakan teknik analisis executable yang dilakukan tanpa menjalankan program secara langsung. Melalui metode ini, berbagai informasi penting mengenai struktur internal binary dapat diperoleh, seperti format file, PE Header, section, import library, strings, hash file, serta karakteristik executable.

Seluruh dokumentasi pada repository ini disusun sebagai catatan pembelajaran sekaligus portofolio hasil praktikum selama mempelajari analisis executable pada sistem operasi Windows.

---

# 🎯 Tujuan Repository

Repository ini dibuat dengan tujuan untuk:

- Mendokumentasikan hasil praktikum Static Analysis terhadap beberapa binary Portable Executable (PE).
- Memahami struktur dasar executable pada sistem operasi Windows.
- Mempelajari penggunaan berbagai tools Reverse Engineering untuk analisis statis.
- Mengidentifikasi karakteristik executable melalui PE Header, Sections, Import Table, Strings, dan Hash.
- Menyusun laporan analisis yang sistematis sebagai dokumentasi proses pembelajaran.

---

# 🛠 Tools yang Digunakan

Beberapa tools yang digunakan selama proses analisis antara lain:

- Detect It Easy (DIE)
- PEStudio
- Ghidra
- IDA Free
- HxD
- CertUtil / SHA256SUM

---

# 📂 Struktur Repository

```text
static-analysis-lab/
├── README.md
├── sample-01-wannacry/
│   ├── README.md
│   └── screenshots/
│       ├── pe-header.png
│       ├── hash.png
│       ├── import-function.png
│       └── strings.png
│
└── sample-02-Npp/
    ├── README.md
    └── screenshots/
        ├── pe-header.png
        ├── hash.png
        ├── import-function.png
        └── strings.png
```

Setiap folder berisi dokumentasi analisis terhadap satu executable beserta screenshot hasil observasi menggunakan tools Reverse Engineering.

---

# 📑 Daftar Analisis

| Sample | Binary | Metode | Status |
|---------|--------|--------|--------|
| Sample 01 | WannaCry.exe | Static Analysis | ✅ Selesai |
| Sample 02 | Npp Installer | Static Analysis | ✅ Selesai |

---

# 🔍 Metodologi Analisis

Setiap analisis dilakukan menggunakan alur yang sama agar dokumentasi lebih konsisten dan mudah dipahami.

Tahapan yang dilakukan meliputi:

1. Identifikasi informasi dasar executable.
2. Analisis PE Header.
3. Identifikasi Hash File.
4. Analisis Import Function.
5. Analisis Strings.
6. Dokumentasi hasil observasi.
7. Penyusunan kesimpulan berdasarkan hasil analisis.

Seluruh proses dilakukan tanpa menjalankan executable sehingga tetap berada pada kategori **Static Analysis**.

---

# 📚 Materi yang Dipelajari

Melalui repository ini saya mempelajari beberapa konsep penting dalam Reverse Engineering, antara lain:

- Portable Executable (PE) Format
- PE Header Analysis
- Section Analysis
- Import Function Analysis
- Strings Analysis
- Hash Identification
- Indicators of Compromise (IOC)
- Penggunaan tools Static Analysis
- Penyusunan laporan analisis executable

---

# 📄 Disclaimer

Repository ini dibuat untuk tujuan edukasi sebagai bagian dari pembelajaran mata kuliah **Reverse Engineering**.

Seluruh dokumentasi berisi hasil observasi dan analisis yang dilakukan menggunakan metode **Static Analysis** terhadap executable yang tersedia untuk keperluan pembelajaran. Repository ini **tidak menyertakan file executable, source code, maupun hasil dekompilasi secara utuh**. Seluruh isi dokumentasi ditulis berdasarkan hasil analisis pribadi dan hanya digunakan sebagai media pembelajaran serta dokumentasi praktikum.

---

# 📚 Referensi

- Microsoft Portable Executable (PE) Format Specification
- Detect It Easy (DIE) Documentation
- Ghidra Documentation
- PEStudio Documentation
