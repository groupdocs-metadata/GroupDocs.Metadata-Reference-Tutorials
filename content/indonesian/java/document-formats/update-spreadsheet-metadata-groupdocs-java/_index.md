---
date: '2026-03-22'
description: Pelajari cara mengubah tanggal pembuatan Excel dan memperbarui metadata
  Excel menggunakan GroupDocs.Metadata untuk Java. Ikuti panduan langkah demi langkah
  ini untuk menambahkan kata kunci ke Excel dan memodifikasi properti dokumen.
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: Ubah Tanggal Pembuatan Excel Menggunakan GroupDocs.Metadata di Java
type: docs
url: /id/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# Mengubah Tanggal Pembuatan Excel Menggunakan GroupDocs.Metadata di Java

Dalam lingkungan modern yang berbasis data, **mengubah tanggal pembuatan Excel** dan menjaga metadata lainnya tetap terbaru dapat secara dramatis meningkatkan organisasi dokumen, kemampuan pencarian, dan kepatuhan. Baik Anda menangani laporan keuangan, pelacak proyek, atau data arsip, metadata yang akurat memastikan orang yang tepat menemukan file yang tepat pada waktu yang tepat. Tutorial ini memandu Anda menggunakan pustaka GroupDocs.Metadata untuk **mengubah tanggal pembuatan Excel**, **menambahkan kata kunci ke Excel**, dan **memodifikasi properti dokumen Excel** dalam aplikasi Java.

## Quick Answers
- **Apakah saya dapat mengubah tanggal pembuatan file Excel?** Ya, dengan menggunakan `setCreatedTime` dari GroupDocs.Metadata.  
- **Perpustakaan mana yang mendukung pembaruan metadata Excel di Java?** GroupDocs.Metadata untuk Java.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk evaluasi; lisensi permanen diperlukan untuk produksi.  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih tinggi.  
- **Bisakah saya menambahkan kata kunci khusus ke workbook Excel?** Tentu—gunakan `setKeywords` pada properti dokumen.

## Apa itu “mengubah tanggal pembuatan Excel”?
Mengubah tanggal pembuatan Excel berarti memperbarui properti *Created* bawaan yang disimpan di dalam file workbook. Properti ini merupakan bagian dari metadata standar Office Open XML dan dapat diedit secara programatis tanpa mengubah konten lembar kerja sebenarnya.

## Mengapa menggunakan GroupDocs.Metadata untuk metadata Excel?
GroupDocs.Metadata menawarkan API tingkat tinggi yang tipe‑aman yang mengabstraksi penanganan XML tingkat rendah yang diperlukan oleh format Office Open XML. Ini memungkinkan Anda:

- **Perbarui properti inti** seperti penulis, perusahaan, dan tanggal pembuatan dalam satu panggilan.  
- **Tambahkan kata kunci ke Excel** untuk meningkatkan hasil pencarian di SharePoint, OneDrive, atau sistem file lokal.  
- **Modifikasi properti dokumen Excel** tanpa membuka workbook di Excel, yang menghemat waktu dan sumber daya.  

## Prasyarat
- Java Development Kit (JDK) 8 atau lebih baru.  
- IDE seperti IntelliJ IDEA atau Eclipse.  
- Familiaritas dasar dengan I/O file Java.  

## Menyiapkan GroupDocs.Metadata untuk Java

### Instalasi

Tambahkan repositori Maven GroupDocs.Metadata dan dependensinya ke `pom.xml` Anda:

```xml
<repositories>
   <repository>
      <id>repository.groupdocs.com</id>
      <name>GroupDocs Repository</name>
      <url>https://releases.groupdocs.com/metadata/java/</url>
   </repository>
</repositories>

<dependencies>
   <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-metadata</artifactId>
      <version>24.12</version>
   </dependency>
</dependencies>
```

Atau, Anda dapat [mengunduh versi terbaru secara langsung](https://releases.groupdocs.com/metadata/java/) jika Anda lebih suka penyiapan manual.

### Akuisisi Lisensi

GroupDocs menawarkan percobaan gratis untuk evaluasi. Untuk penggunaan produksi, dapatkan lisensi sementara atau permanen dari vendor. Kunjungi [halaman pembelian GroupDocs](https://purchase.groupdocs.com/temporary-license/) untuk detail.

#### Inisialisasi Dasar

Impor kelas yang diperlukan dalam file sumber Java Anda:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Implementasi Langkah‑per‑Langkah

### Langkah 1: Buka Workbook Excel

Berikan jalur ke workbook sumber dan buat instance `Metadata`. Blok `try‑with‑resources` memastikan handle file ditutup secara otomatis.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Langkah 2: Perbarui Properti Metadata Bawaan

Sekarang Anda dapat **mengubah tanggal pembuatan Excel**, mengatur penulis, perusahaan, kategori, dan **menambahkan kata kunci ke Excel**. Pemanggilan `new Date()` menangkap stempel waktu saat ini, tetapi Anda dapat menyediakan `java.util.Date` apa pun yang diperlukan.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **Tip profesional:** Gunakan konvensi penamaan yang konsisten untuk kata kunci (mis., `project:Q2, finance, confidential`) agar pencarian di masa depan lebih efektif.

### Langkah 3: Simpan Workbook yang Diperbarui

Tentukan jalur output dan simpan perubahan. File asli tetap tidak tersentuh, yang berguna untuk jejak audit.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Masalah Umum dan Solusinya

| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| **Kesalahan jalur file** | Jalur relatif/absolut yang tidak tepat | Periksa kembali `inputFilePath` dan `outputFilePath`. Gunakan `Paths.get(...)` untuk jalur yang independen platform. |
| **Versi perpustakaan tidak kompatibel** | Menggunakan GroupDocs.Metadata versi lama yang tidak mendukung metode `setCreatedTime` | Tingkatkan ke versi terbaru (seperti yang ditunjukkan dalam potongan Maven). |
| **Lisensi hilang** | Periode percobaan telah berakhir | Terapkan lisensi sementara atau beli lisensi penuh melalui halaman pembelian. |
| **Penggunaan memori workbook besar** | Memuat file Excel yang sangat besar mengonsumsi ruang heap | Proses file secara batch dan tingkatkan heap JVM (`-Xmx`) jika diperlukan. |

## Pertanyaan yang Sering Diajukan

**Q: Versi Java apa yang didukung oleh GroupDocs.Metadata?**  
**A:** Java 8 dan yang lebih baru sepenuhnya didukung.

**Q: Bagaimana saya harus menangani pengecualian saat memperbarui metadata?**  
**A:** Bungkus kode dalam blok `try‑catch` dan log `MetadataException` untuk menangkap kesalahan I/O atau format apa pun.

**Q: Bisakah saya memperbarui beberapa file Excel dalam satu kali jalan?**  
**A:** Ya, iterasi melalui koleksi jalur file, tetapi pantau penggunaan memori untuk batch besar.

**Q: Apakah memungkinkan untuk mengembalikan perubahan yang dibuat pada metadata?**  
**A:** Simpan cadangan workbook asli sebelum menerapkan pembaruan, kemudian pulihkan jika diperlukan.

**Q: Di mana saya dapat menemukan dokumentasi lebih detail?**  
**A:** Lihat panduan resmi di [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## Aplikasi Praktis

1. **Audit Keuangan** – Catat siapa yang memodifikasi workbook dan kapan, menyediakan jejak audit.  
2. **Manajemen Proyek** – Tandai spreadsheet dengan kata kunci spesifik proyek untuk pengambilan cepat.  
3. **Pengarsipan Data** – Pertahankan tanggal pembuatan asli dan informasi perusahaan untuk kepatuhan.

## Tips Kinerja

- Batasi operasi metadata per run untuk menghindari konsumsi memori berlebih.  
- Tutup objek `Metadata` dengan cepat (pola `try‑with‑resources` melakukannya secara otomatis).  
- Untuk workbook yang sangat besar, pertimbangkan memprosesnya pada thread latar belakang agar UI tetap responsif.

## Kesimpulan

Anda kini tahu cara **mengubah tanggal pembuatan Excel**, **menambahkan kata kunci ke Excel**, dan **memodifikasi properti dokumen Excel** menggunakan GroupDocs.Metadata di Java. Kemampuan ini memungkinkan Anda menjaga spreadsheet tetap terorganisir dengan baik, dapat dicari, dan mematuhi kebijakan tata kelola internal. Sebagai langkah selanjutnya, jelajahi fitur metadata lainnya seperti properti khusus atau pemrosesan batch untuk lebih menyederhanakan alur kerja manajemen dokumen Anda.

---

**Terakhir Diperbarui:** 2026-03-22  
**Diuji Dengan:** GroupDocs.Metadata 24.12 untuk Java  
**Penulis:** GroupDocs  

**Sumber Daya**
- [Dokumentasi](https://docs.groupdocs.com/metadata/java/)
- [Referensi API](https://reference.groupdocs.com/metadata/java/)
- [Unduh GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [Repositori GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/metadata/)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)