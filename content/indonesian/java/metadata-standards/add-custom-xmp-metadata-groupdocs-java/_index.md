---
date: '2026-06-12'
description: Pelajari cara membuat paket XMP kustom, mengelola metadata file, dan
  menambahkan metadata kustom ke PDF menggunakan GroupDocs.Metadata untuk Java.
keywords:
- create custom xmp package
- manage file metadata
- add custom metadata pdf
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  headline: Create Custom XMP Package with GroupDocs.Metadata for Java
  type: TechArticle
- description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  name: Create Custom XMP Package with GroupDocs.Metadata for Java
  steps:
  - name: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
    text: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
  - name: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
    text: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
  - name: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
    text: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
  type: HowTo
- questions:
  - answer: Over 50 formats—including JPEG, PNG, PDF, DOCX, and TIFF—support XMP packet
      injection. See the full list in the [GroupDocs.Metadata documentation](https://docs.groupdocs.com/metadata/java/).
    question: What file formats support custom XMP packages?
  - answer: Yes, the library lets you read, modify, and delete any XMP property using
      the `IXmp` interface.
    question: Can I edit existing XMP metadata with GroupDocs.Metadata?
  - answer: For unsupported formats, consider wrapping the file in a container that
      does support XMP (e.g., converting to PDF) or using an alternative metadata
      store.
    question: How do I handle files that don’t natively support XMP?
  - answer: Absolutely—GroupDocs.Metadata is tested against Java 8 through Java 21,
      including all LTS releases.
    question: Is the library compatible with Java 17 LTS?
  - answer: Common pitfalls include using an incorrect namespace URI, exceeding the
      maximum packet size (≈ 2 MB), or attempting to write to a read‑only file. Ensure
      proper permissions and validate your XML schema before saving.
    question: What are typical errors when adding XMP packages?
  type: FAQPage
title: Buat Paket XMP Kustom dengan GroupDocs.Metadata untuk Java
type: docs
url: /id/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/
weight: 1
---

# Buat Paket XMP Kustom dengan GroupDocs.Metadata untuk Java

Di alur kerja digital modern, **membuat paket XMP kustom** sangat penting untuk menyematkan metadata kaya dan dapat dicari langsung di dalam file. Baik Anda menangani gambar, PDF, atau aset multimedia, GroupDocs.Metadata untuk Java memberikan cara yang andal untuk **mengelola metadata file** dan **menambahkan metadata kustom ke PDF** tanpa basis data eksternal. Dalam tutorial ini kami akan membimbing Anda melalui seluruh proses—dari menyiapkan pustaka hingga menyematkan paket XMP lengkap—sehingga Anda dapat mulai memperkaya dokumen Anda hari ini.

## Jawaban Cepat
- **Apa langkah pertama?** Tambahkan GroupDocs.Metadata sebagai dependensi Maven atau unduh JAR.  
- **Berapa baris kode?** Hanya tiga pernyataan singkat yang diperlukan untuk membuat dan melampirkan paket XMP kustom.  
- **Format file apa yang didukung?** Lebih dari 50 format, termasuk JPEG, PNG, PDF, DOCX, dan TIFF.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengembangan; lisensi permanen diperlukan untuk produksi.  
- **Bisakah saya menggunakan ini dengan Java 11+?** Ya, pustaka kompatibel dengan Java 8 hingga Java 21.

## Apa itu “create custom xmp package”?
*Membuat paket XMP kustom* berarti membangun paket XMP yang berisi bidang metadata yang ditentukan pengguna dan menyematkannya ke dalam file yang didukung. Paket ini disimpan di dalam bagian XMP file, menjadikan metadata dapat dipindahkan dan dapat dicari oleh aplikasi yang mendukung XMP apa pun.

## Mengapa menggunakan GroupDocs.Metadata untuk Java untuk mengelola metadata file?
GroupDocs.Metadata mendukung **lebih dari 50 format input dan output** dan dapat memproses file hingga **2 GB** tanpa memuat seluruh dokumen ke memori, yang mengurangi konsumsi RAM hingga **80 %** pada aset besar. API juga menyediakan operasi yang thread‑safe, memungkinkan pemrosesan batch berkecepatan tinggi di lingkungan perusahaan.

## Prasyarat
- **Java Development Kit** 8 atau lebih baru (Java 11+ disarankan).  
- IDE seperti **IntelliJ IDEA** atau **Eclipse**.  
- Maven terpasang untuk manajemen dependensi.  
- Pemahaman dasar tentang kelas Java dan konsep metadata.

## Menyiapkan GroupDocs.Metadata untuk Java
### Pengaturan Maven
Tambahkan dependensi berikut ke file `pom.xml` Anda untuk menyertakan GroupDocs.Metadata:

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

Refer to the [Dokumentasi API](https://reference.groupdocs.com/metadata/java/) for full method signatures.  
For detailed API reference see the [Dokumen Java GroupDocs.Metadata](https://docs.groupdocs.com/metadata/java/).

**Unduhan Langsung** – Jika Anda lebih suka penyiapan manual, dapatkan JAR terbaru dari [rilisan GroupDocs.Metadata untuk Java](https://releases.groupdocs.com/metadata/java/). Anda juga dapat melihat halaman [Rilisan Terbaru](https://releases.groupdocs.com/metadata/java/) untuk detail catatan perubahan.

### Perolehan Lisensi
- **Uji Coba Gratis** – Evaluasi semua fitur tanpa biaya.  
- **Lisensi Sementara** – Dapatkan kunci berjangka waktu untuk pengujian pengembangan. ([Dapatkan Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/))  
- **Pembelian** – Peroleh lisensi permanen untuk penggunaan produksi.

The source code and examples are available on [GroupDocs Metadata di GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java).

## Panduan Implementasi
Berikut adalah panduan langkah demi langkah yang menunjukkan secara tepat cara **membuat paket XMP kustom** dan menyematkannya ke dalam file.

### Cara membuat paket XMP kustom dan melampirkannya ke file?
Muat file target Anda dengan kelas `Metadata`, bangun `XmpPacketWrapper`, definisikan bidang XMP kustom Anda, dan akhirnya simpan perubahan. Alur end‑to‑end ini hanya memerlukan tiga pemanggilan metode setelah inisialisasi. Proses ini memastikan paket XMP disematkan dengan benar dan file tetap berfungsi penuh di semua aplikasi yang didukung.

### Inisialisasi Objek Metadata
`Metadata` adalah kelas utama yang mewakili sebuah file dan menyediakan metode untuk membaca dan menulis metadata-nya.  
```java
Metadata metadata = new Metadata("sample.pdf");
```

### Buat XmpPacketWrapper Baru
`XmpPacketWrapper` berfungsi sebagai wadah untuk satu atau lebih paket XMP, memungkinkan pembaruan batch sebelum disimpan.  
```java
XmpPacketWrapper xmpWrapper = new XmpPacketWrapper();
```

### Definisikan dan Konfigurasikan Paket XMP Kustom
Antarmuka `IXmp` memungkinkan Anda mendefinisikan skema XMP kustom dan menetapkan nilai properti di dalam paket.  
```java
IXmp customXmp = xmpWrapper.createPackage("http://mycompany.com/custom");
customXmp.setProperty("Creator", "John Doe");
customXmp.setProperty("Project", "Metadata Migration");
customXmp.setProperty("Version", "1.0");
```

### Simpan Metadata yang Diperbarui
`Metadata.save()` menulis metadata yang telah dimodifikasi kembali ke file asli, menyimpan setiap paket XMP yang ditambahkan.  
```java
metadata.getXmp().addPacket(xmpWrapper);
metadata.save();
```

#### Penjelasan Komponen Kunci
- **Objek Metadata** – Pusat utama untuk mengakses metadata file.  
- **Antarmuka IXmp** – Menyediakan metode untuk membaca/menulis bidang khusus XMP.  
- **XmpPacketWrapper** – Menyimpan satu atau lebih paket XMP, memungkinkan pembaruan batch.  
- **Paket XMP Kustom** – Skema yang Anda definisikan untuk menyimpan informasi tambahan.

## Masalah Umum dan Solusinya
- **Format File Tidak Didukung** – Pastikan tipe file target muncul dalam daftar format resmi (lebih dari 50 format didukung).  
- **Lisensi Tidak Ditemukan** – Pastikan file lisensi ditempatkan di direktori root aplikasi atau diatur melalui `License.setLicense("license_path")`.  
- **Kehabisan Memori pada File Besar** – Gunakan `metadata.setLoadOptions(LoadOptions.lazyLoad())` untuk memproses metadata secara malas dan menjaga penggunaan memori tetap rendah.

For additional help, visit the [Dukungan GroupDocs](https://forum.groupdocs.com/c/metadata/) forum.

## Aplikasi Praktis
1. **Manajemen Aset Digital** – Menyematkan lisensi dan hak penggunaan langsung ke dalam gambar dan PDF.  
2. **Personalisasi Konten** – Menempelkan pengidentifikasi spesifik pengguna ke dokumen untuk pengiriman yang ditargetkan.  
3. **Kepatuhan Regulasi** – Menyimpan jejak audit dan kebijakan retensi di dalam file itu sendiri, menyederhanakan audit tata kelola.

## Pertimbangan Kinerja
- **Optimisasi Sumber Daya** – Proses metadata dalam mode streaming untuk menjaga penggunaan RAM di bawah **100 MB** untuk file yang lebih besar dari **1 GB**.  
- **Pembaruan Versi** – Jaga pustaka tetap terbaru; setiap rilis utama menambahkan dukungan untuk format baru dan meningkatkan kecepatan pemrosesan hingga **30 %**.

## Kesimpulan
Dengan mengikuti panduan ini Anda kini tahu cara **membuat paket XMP kustom** dengan GroupDocs.Metadata untuk Java, memungkinkan Anda **mengelola metadata file** secara efisien dan **menambahkan metadata kustom ke PDF** serta banyak format lainnya. Bereksperimenlah dengan skema XMP tambahan, integrasikan alur kerja ke dalam pipeline CI Anda, atau gabungkan dengan GroupDocs.Viewer untuk pemrosesan dokumen end‑to‑end.

## Pertanyaan yang Sering Diajukan

**Q: Format file apa yang mendukung paket XMP kustom?**  
A: Lebih dari 50 format—termasuk JPEG, PNG, PDF, DOCX, dan TIFF—mendukung penyuntikan paket XMP. Lihat daftar lengkap di [dokumentasi GroupDocs.Metadata](https://docs.groupdocs.com/metadata/java/).

**Q: Bisakah saya mengedit metadata XMP yang ada dengan GroupDocs.Metadata?**  
A: Ya, pustaka memungkinkan Anda membaca, memodifikasi, dan menghapus properti XMP apa pun menggunakan antarmuka `IXmp`.

**Q: Bagaimana cara menangani file yang tidak secara native mendukung XMP?**  
A: Untuk format yang tidak didukung, pertimbangkan membungkus file dalam wadah yang mendukung XMP (misalnya, mengonversi ke PDF) atau menggunakan penyimpanan metadata alternatif.

**Q: Apakah pustaka kompatibel dengan Java 17 LTS?**  
A: Tentu—GroupDocs.Metadata telah diuji pada Java 8 hingga Java 21, termasuk semua rilis LTS.

**Q: Apa kesalahan umum saat menambahkan paket XMP?**  
A: Kesalahan umum meliputi penggunaan URI namespace yang tidak tepat, melebihi ukuran maksimum paket (≈ 2 MB), atau mencoba menulis ke file yang hanya-baca. Pastikan izin yang tepat dan validasi skema XML Anda sebelum menyimpan.

**Last Updated:** 2026-06-12  
**Tested With:** GroupDocs.Metadata 23.12 untuk Java  
**Author:** GroupDocs  

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

```java
import com.groupdocs.metadata.Metadata;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Proceed with operations on metadata
}
```

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Get the root XMP package from the metadata
    IXmp root = (IXmp) metadata.getRootPackage();
```

```java
import com.groupdocs.metadata.core.XmpPacketWrapper;

// Create a new XmpPacketWrapper to hold custom packages
XmpPacketWrapper packet = new XmpPacketWrapper();
```

```java
import com.groupdocs.metadata.core.XmpPackage;
import com.groupdocs.metadata.core.XmpArray;
import com.groupdocs.metadata.core.XmpArrayType;

// Define and configure the custom XMP package
custom = new XmpPackage("gd", "GroupDocs Custom Package");
custom.set("CustomProperty", "CustomValue");

// Add it to the packet
packet.addPackage(custom);
```

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```

## Tutorial Terkait

- [Tambahkan Metadata XMP Kustom ke File dengan GroupDocs.Metadata Java: Panduan Komprehensif](/metadata/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/)
- [Cara Menambahkan Metadata ke PDF dengan GroupDocs.Metadata untuk Java – Panduan Pengembang](/metadata/java/document-formats/master-pdf-metadata-groupdocs-java/)
- [Cara Mengekstrak Metadata Kustom dari PDF Menggunakan GroupDocs.Metadata di Java: Panduan Komprehensif](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)