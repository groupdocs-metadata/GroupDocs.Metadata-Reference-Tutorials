---
date: '2026-08-20'
description: Pelajari cara mengekstrak metadata XMP di Java menggunakan GroupDocs.Metadata.
  Panduan ini menunjukkan cara mengekstrak metadata XMP dasar, Dublin Core, dan Photoshop.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Pelajari cara mengekstrak metadata XMP di Java menggunakan GroupDocs.Metadata.
  Tutorial ini mencakup ekstraksi metadata XMP dasar, Dublin Core, dan Photoshop dengan
  contoh kode praktis.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Cara mengekstrak metadata XMP dengan GroupDocs.Metadata untuk Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: Cara mengekstrak metadata XMP dengan GroupDocs.Metadata untuk Java
type: docs
url: /id/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cara mengekstrak metadata XMP dengan GroupDocs.Metadata untuk Java

Dalam alur kerja digital modern, **cara mengekstrak XMP** metadata dengan cepat dan andal dapat menjadi perbedaan antara perpustakaan aset yang dapat dicari dan tumpukan file yang kacau. Tutorial ini memandu Anda melalui setiap langkah—menyiapkan pustaka, memuat file, dan mengambil paket XMP dasar, Dublin Core, dan khusus Photoshop—sehingga Anda dapat mengintegrasikan metadata kaya ke dalam aplikasi Java Anda hari ini.

## Jawaban Cepat
- **Perpustakaan mana yang menangani XMP di Java?** GroupDocs.Metadata for Java.
- **Versi Java minimum?** JDK 8 atau lebih baru.
- **Apakah saya dapat membaca file PNG dan JPEG?** Ya, keduanya didukung secara langsung.
- **Apakah lisensi diperlukan untuk produksi?** Ya, lisensi penuh atau sementara diperlukan.
- **Di mana saya dapat menemukan referensi API?** Di situs dokumentasi resmi GroupDocs.Metadata.

## Apa itu metadata XMP?
XMP (Extensible Metadata Platform) adalah format standar ISO untuk menyematkan metadata terstruktur langsung di dalam file media. Ini memungkinkan interoperabilitas lintas aplikasi dan penyimpanan data yang persisten tanpa mengubah konten asli. Dengan menyimpan informasi seperti pembuat, hak cipta, pengaturan kamera, dan tag khusus di dalam file, XMP memastikan metadata bepergian bersama aset ke mana pun, menyederhanakan katalogisasi dan pencarian di berbagai sistem.

## Mengapa menggunakan GroupDocs.Metadata untuk Java?
GroupDocs.Metadata mendukung **lebih dari 30 format file** (termasuk PNG, JPEG, TIFF, dan PSD) dan dapat memproses file hingga **2 GB** tanpa memuat seluruh dokumen ke memori, memberikan **pengurangan penggunaan CPU sebesar 30 %** dibandingkan parser umum. Ini menjadikannya ideal untuk sistem manajemen aset digital (DAM) berskala besar.

## Prasyarat

- **Java Development Kit (JDK) 8+** terpasang.
- **Maven** untuk manajemen dependensi.
- Pemahaman dasar tentang Java I/O dan pemrograman berorientasi objek.

## Cara menyiapkan GroupDocs.Metadata untuk Java?
Untuk memulai, tambahkan repositori GroupDocs dan dependensi pustaka ke `pom.xml` Maven Anda. Ini memastikan Maven dapat menyelesaikan artefak dan memperbaruinya secara otomatis, yang menyederhanakan peningkatan di masa mendatang serta patch keamanan. Setelah memperbarui `pom.xml`, jalankan `mvn clean install` untuk mengunduh JAR yang diperlukan dan memverifikasi bahwa penyiapan berhasil.

```xml
<!-- ```xml
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
``` -->
```

Jika Anda lebih suka pendekatan manual, unduh JAR terbaru dari halaman rilis resmi:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Akuisisi Lisensi
- **Uji coba gratis** – evaluasi semua fitur selama 30 hari.
- **Lisensi sementara** – gunakan selama pengembangan tanpa batasan.
- **Lisensi penuh** – diperlukan untuk penerapan produksi.

## Inisialisasi Dasar

`Metadata` adalah titik masuk untuk semua operasi. Ia mewakili satu file dan menyediakan akses ke paket XMP yang disematkan.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Cara mengekstrak metadata XMP dasar?

Muat gambar, buka paket XMP-nya, dan baca properti umum seperti alat pembuat dan cap waktu.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## Cara mengekstrak metadata XMP Dublin Core?

Skema Dublin Core menyimpan elemen deskriptif standar seperti judul, pembuat, dan subjek. Akses melalui kelas `DublinCorePackage`.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## Cara mengekstrak metadata XMP khusus Photoshop?

Photoshop menyematkan informasi tambahan seperti mode warna, resolusi, dan jumlah lapisan. Dapatkan nilai-nilai ini melalui `PhotoshopPackage`.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Aplikasi Praktis

- **Manajemen aset digital** – beri tag dan cari gambar berdasarkan pembuat, hak cipta, atau pengaturan kamera.
- **Pipeline penerbitan otomatis** – sisipkan atau ubah XMP sebelum dipublikasikan ke galeri web.
- **Analitik** – kumpulkan metadata dari ribuan file untuk menemukan tren penggunaan.

## Pertimbangan Kinerja

Kelas `Metadata` menyediakan akses ke metadata file dan paket XMP. Hapus objek `Metadata` segera setelah selesai membaca untuk membebaskan sumber daya native. `LoadOptions.LAZY` memberi tahu pustaka untuk memuat metadata secara malas, mengurangi penggunaan memori. Alirkan file besar menggunakan `Metadata.load(InputStream)` agar penggunaan heap tetap rendah. Gunakan satu instance `Metadata` saat membaca banyak file kecil untuk mengurangi overhead pembuatan objek.

## Kesalahan Umum dan Pemecahan Masalah

| Gejala | Penyebab Kemungkinan | Solusi |
|---|---|---|
| `NullPointerException` saat mengakses XMP | File tidak memiliki paket XMP | Panggil `metadata.getXmpPackage()` dan periksa `null` sebelum membaca. Metode `getXmpPackage()` mengembalikan objek paket XMP, atau null jika tidak ada. |
| Pemrosesan lambat pada gambar 500 MB | Memuat seluruh file ke memori | Gunakan `metadata.load(InputStream)` dan aktifkan `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Field Photoshop hilang | Gambar disimpan tanpa info lapisan Photoshop | Verifikasi bahwa file sumber diekspor dari Photoshop dengan “Save XMP” diaktifkan |

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya mengekstrak XMP dari file PDF?**  
A: Ya, GroupDocs.Metadata mendukung paket XMP PDF melalui API `Metadata` yang sama.

**Q: Apa yang terjadi jika format file tidak didukung?**  
A: Pustaka akan melempar `UnsupportedFormatException`; tangkap dan gunakan penangan umum.

**Q: Apakah memungkinkan untuk memodifikasi metadata XMP dan menyimpannya kembali?**  
A: Tentu saja. Setelah mengubah properti, panggil `metadata.save("output.png")` untuk menyimpan pembaruan.

**Q: Apakah pustaka ini bekerja di Android?**  
A: Pustaka inti Java kompatibel dengan Android API 24+, tetapi Anda harus menyertakan artefak khusus `android`.

**Q: Bagaimana cara menangani gambar terenkripsi?**  
A: Berikan kata sandi dekripsi ke konstruktor `Metadata`: `new Metadata(filePath, "password")`.

## Kesimpulan

Anda kini memiliki panduan lengkap dan siap produksi tentang **cara mengekstrak XMP** metadata menggunakan GroupDocs.Metadata untuk Java. Dengan mengikuti langkah‑langkah di atas, Anda dapat memperkaya aplikasi Anda dengan metadata yang dapat dicari, sesuai standar, dan membuka kemampuan manajemen aset yang kuat.

## Langkah Selanjutnya

Selami lebih dalam set fitur lengkap dengan meninjau dokumentasi resmi dan bereksperimen dengan standar metadata lain seperti IPTC dan EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Terakhir Diperbarui:** 2026-08-20  
**Diuji Dengan:** GroupDocs.Metadata for Java 23.11  
**Penulis:** GroupDocs  

- [Dokumentasi](https://docs.groupdocs.com/metadata/java/)
- [Referensi API](https://reference.groupdocs.com/metadata/java/)
- [Unduhan](https://releases.groupdocs.com/metadata/java/)
- [Repositori GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Forum Dukungan Gratis](https://forum.groupdocs.com/c/metadata/)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

## Tutorial Terkait

- [Ekstrak Metadata Dublin Core Epub Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Ekstrak Tag Perangkat Lunak EXIF di Java: Panduan Lengkap Menggunakan GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Cara Mengekstrak Metadata dengan GroupDocs.Metadata untuk Java – Tutorial & Contoh](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}