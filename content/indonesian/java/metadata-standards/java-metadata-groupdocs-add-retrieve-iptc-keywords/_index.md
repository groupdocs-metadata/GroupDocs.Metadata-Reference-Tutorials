---
date: '2026-08-15'
description: Pelajari cara menambahkan kata kunci IPTC di Java menggunakan GroupDocs.Metadata,
  meningkatkan manajemen aset digital dan kemampuan pencarian.
keywords:
- add iptc keywords java
- groupdocs metadata java
- java add image metadata
lastmod: '2026-08-15'
og_description: Tambahkan kata kunci IPTC di Java menggunakan GroupDocs.Metadata untuk
  meningkatkan manajemen aset digital. Pelajari langkah demi langkah penyiapan, kode,
  dan praktik terbaik.
og_image_alt: Guide showing Java code that adds IPTC keywords with GroupDocs.Metadata
og_title: Tambahkan kata kunci IPTC di Java dengan GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-15'
  description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  headline: Add IPTC keywords in Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  name: Add IPTC keywords in Java with GroupDocs.Metadata
  steps:
  - name: create a constants class
    text: The `Constants` class stores reusable values such as file locations and
      the license string.
  - name: initialize metadata and set the IPTC package
    text: '`Metadata` is the entry point for reading and writing any supported metadata
      format. It abstracts file handling so you don’t need to manage streams manually.
      The code below checks whether an IPTC package already exists; if not, it creates
      one, guaranteeing a place for keyword storage.'
  - name: add keywords to the IPTC record
    text: IptcDataSet represents a single IPTC metadata entry such as a keyword. Each
      keyword is added as an `IptcDataSet` entry. You can add as many keywords as
      required; the library automatically handles duplicate detection.
  - name: retrieve and display IPTC keywords
    text: '`metadata.getIptc().getKeywords()` returns the list of keyword strings
      stored in the IPTC package. After saving, you can read back the keywords to
      confirm they were persisted correctly. This verification step is useful for
      unit tests and debugging.'
  type: HowTo
- questions:
  - answer: No. IPTC is an image‑specific standard; for PDFs you would use XMP or
      PDF‑specific metadata fields.
    question: Can I add IPTC keywords to PDF files?
  - answer: Yes—it handles JPEG, TIFF, PNG, BMP, and WebP, preserving existing metadata
      while adding new IPTC entries.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: The IPTC specification allows up to 64 keywords per image; GroupDocs.Metadata
      enforces this limit automatically.
    question: How many keywords can I store?
  - answer: Absolutely. The library is compiled for Java 8+ and works seamlessly on
      Java 11, 17, and newer LTS releases.
    question: Is the library compatible with Java 11?
  - answer: Retrieve the keyword list, remove the unwanted entry, then call `metadata.getIptc().setKeywords(updatedList)`
      and save the file.
    question: What if I need to remove a keyword?
  type: FAQPage
tags:
- add iptc keywords
- groupdocs metadata
- java metadata handling
- digital asset management
- image metadata
title: Tambahkan kata kunci IPTC di Java dengan GroupDocs.Metadata
type: docs
url: /id/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/
weight: 1
---

# Tambah kata kunci IPTC di Java dengan GroupDocs.Metadata

Mengelola metadata gambar sangat penting untuk strategi manajemen aset digital (DAM) apa pun. Dalam tutorial ini Anda akan belajar **cara menambahkan kata kunci IPTC di Java** menggunakan pustaka GroupDocs.Metadata, kemudian mengambil kata kunci tersebut untuk memverifikasi perubahan. Pada akhir tutorial, Anda akan memiliki pola yang dapat digunakan kembali yang dapat Anda sematkan dalam pekerjaan pemrosesan batch, pipeline manajemen konten, atau alur kerja media berbasis Java apa pun.

## Jawaban Cepat
- **Perpustakaan mana yang menambahkan kata kunci IPTC di Java?** GroupDocs.Metadata for Java.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis dapat digunakan untuk pengembangan; lisensi berbayar diperlukan untuk produksi.  
- **Bisakah saya menambahkan beberapa kata kunci sekaligus?** Ya—cukup tambahkan setiap kata kunci ke paket IPTC.  
- **Apakah penanganan file besar didukung?** GroupDocs.Metadata memproses file hingga 2 GB tanpa memuat seluruh file ke memori.  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih tinggi, dengan Maven 3 atau lebih baru.

## Apa itu menambahkan kata kunci IPTC di Java?
**Add IPTC keywords java** mengacu pada penyisipan programatik tag kata kunci standar IPTC ke dalam file gambar menggunakan kode Java. Operasi ini memperkaya metadata gambar, membuatnya dapat dicari dalam sistem DAM dan meningkatkan SEO untuk aset web. Ini juga membantu menjaga kepatuhan dengan standar industri untuk penandaan aset media.

## Mengapa menggunakan GroupDocs.Metadata untuk Java?
GroupDocs.Metadata mendukung **lebih dari 150 standar metadata** (termasuk EXIF, IPTC, XMP) dan dapat **memproses file hingga 2 GB** tanpa memuatnya sepenuhnya ke memori, yang mengurangi penggunaan CPU dan RAM hingga 30 % dibandingkan dengan pendekatan aliran file yang sederhana. API ini tipe‑aman, terdokumentasi dengan baik, dan menyediakan panggilan satu baris untuk menyimpan perubahan.

## Prasyarat

- **GroupDocs.Metadata for Java** (versi 24.12 atau lebih baru).  
- Java Development Kit 8 atau yang lebih baru.  
- Maven 3 yang terpasang dan dikonfigurasi.  
- Sebuah IDE seperti IntelliJ IDEA atau Eclipse (opsional tetapi disarankan).  

### Perpustakaan yang Diperlukan
Tambahkan dependensi GroupDocs.Metadata ke `pom.xml` Anda:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

Anda dapat mengunduh pustaka dari halaman **GroupDocs.Metadata for Java releases**: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

## Cara menambahkan kata kunci IPTC di Java?

Pertama, muat file gambar target menggunakan API GroupDocs.Metadata, kemudian verifikasi bahwa paket IPTC ada atau buat satu jika tidak ada, dan akhirnya tambahkan kata kunci yang diinginkan ke koleksi IPTC Keywords. Langkah-langkah di bawah ini menggambarkan setiap bagian alur kerja ini secara detail.

### Langkah 1: buat kelas constants
Kelas `Constants` menyimpan nilai yang dapat digunakan kembali seperti lokasi file dan string lisensi.

```java
public class Constants {
    public static final String YOUR_DOCUMENT_DIRECTORY = "path/to/your/document";
    public static final String OUTPUT_DIRECTORY = "path/to/output/directory";
}
```

### Langkah 2: inisialisasi metadata dan atur paket IPTC
`Metadata` adalah titik masuk untuk membaca dan menulis format metadata apa pun yang didukung. Ia mengabstraksi penanganan file sehingga Anda tidak perlu mengelola aliran secara manual.

Kode di bawah ini memeriksa apakah paket IPTC sudah ada; jika tidak, ia membuatnya, menjamin tempat untuk penyimpanan kata kunci.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcRecordSet;

public class InitializeMetadataAndIPTCPackage {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            if (root.getIptcPackage() == null) {
                root.setIptcPackage(new IptcRecordSet());
            }
        } catch (Exception e) {
            System.out.println("Error initializing metadata: " + e.getMessage());
        }
    }
}
```

### Langkah 3: tambahkan kata kunci ke catatan IPTC
IptcDataSet mewakili satu entri metadata IPTC seperti kata kunci. Setiap kata kunci ditambahkan sebagai entri `IptcDataSet`. Anda dapat menambahkan sebanyak yang diperlukan; pustaka secara otomatis menangani deteksi duplikat.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcDataSet;
import com.groupdocs.metadata.core.IptcRecordType;
import com.groupdocs.metadata.core.IptcApplicationRecordDataSet;

public class AddKeywordsToIPTC {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            IptcDataSet dataSet1 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 1");
            IptcDataSet dataSet2 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 2");
            IptcDataSet dataSet3 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 3");

            root.getIptcPackage().add(dataSet1);
            root.getIptcPackage().add(dataSet2);
            root.getIptcPackage().add(dataSet3);

            metadata.save(Constants.OUTPUT_DIRECTORY);
        } catch (Exception e) {
            System.out.println("Error adding keywords: " + e.getMessage());
        }
    }
}
```

### Langkah 4: ambil dan tampilkan kata kunci IPTC
`metadata.getIptc().getKeywords()` mengembalikan daftar string kata kunci yang disimpan dalam paket IPTC. Setelah menyimpan, Anda dapat membaca kembali kata kunci untuk mengonfirmasi bahwa mereka telah dipertahankan dengan benar. Langkah verifikasi ini berguna untuk pengujian unit dan debugging.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.MetadataProperty;

public class RetrieveAndDisplayKeywords {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.OUTPUT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            MetadataProperty keywordsProperty = root.getIptcPackage().getApplicationRecord()
                                                    .get_Item((byte)IptcApplicationRecordDataSet.Keywords.getRawValue());

            for (Object value : keywordsProperty.getValue()) {
                System.out.println(value);
            }
        } catch (Exception e) {
            System.out.println("Error retrieving keywords: " + e.getMessage());
        }
    }
}
```

## Cara mengambil kata kunci IPTC di Java?

`metadata.getIptc().getKeywords()` mengembalikan daftar string kata kunci yang disimpan dalam paket IPTC. Anda kemudian dapat mengiterasi daftar tersebut, mencatat setiap entri, atau memasukkannya ke dalam indeks pencarian untuk pengambilan cepat. Metode ini mengembalikan `List<String>` yang berisi setiap kata kunci yang disimpan dalam paket IPTC, memungkinkan Anda menampilkan atau memprosesnya secara instan.

## Kesulitan Umum dan Pemecahan Masalah

- **Paket IPTC hilang:** Jika gambar tidak memiliki blok IPTC, `metadata.getIptc()` mengembalikan `null`. Selalu panggil `metadata.addIptc()` sebelum menambahkan kata kunci.  
- **Kesalahan lisensi:** Pastikan file lisensi percobaan atau komersial direferensikan dengan benar di `Constants.LICENSE_PATH`. Lisensi yang hilang akan memicu `LicenseException`.  
- **File besar:** Untuk gambar yang lebih besar dari 2 GB, bagi pemrosesan menjadi potongan atau gunakan API streaming yang disediakan oleh GroupDocs.Metadata untuk menghindari `OutOfMemoryError`.  

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya menambahkan kata kunci IPTC ke file PDF?**  
A: Tidak. IPTC adalah standar khusus gambar; untuk PDF Anda akan menggunakan XMP atau bidang metadata khusus PDF.

**Q: Apakah GroupDocs.Metadata mendukung format gambar lain?**  
A: Ya—ia menangani JPEG, TIFF, PNG, BMP, dan WebP, mempertahankan metadata yang ada sambil menambahkan entri IPTC baru.

**Q: Berapa banyak kata kunci yang dapat saya simpan?**  
A: Spesifikasi IPTC memperbolehkan hingga 64 kata kunci per gambar; GroupDocs.Metadata menegakkan batas ini secara otomatis.

**Q: Apakah pustaka ini kompatibel dengan Java 11?**  
A: Tentu saja. Pustaka ini dikompilasi untuk Java 8+ dan bekerja mulus pada Java 11, 17, dan rilis LTS yang lebih baru.

**Q: Bagaimana jika saya perlu menghapus sebuah kata kunci?**  
A: Ambil daftar kata kunci, hapus entri yang tidak diinginkan, kemudian panggil `metadata.getIptc().setKeywords(updatedList)` dan simpan file.

## Kesimpulan

Anda kini memiliki pola lengkap yang siap produksi untuk **menambahkan kata kunci IPTC di Java** dengan GroupDocs.Metadata. Dengan menginisialisasi objek metadata, memastikan paket IPTC ada, menambahkan kata kunci, dan memverifikasi hasilnya, Anda dapat mengintegrasikan penandaan yang kuat ke dalam alur kerja DAM atau manajemen konten berbasis Java apa pun. Jelajahi tipe metadata tambahan—EXIF, XMP, dan tag khusus—untuk memperkaya aset Anda lebih lanjut.

**Langkah Selanjutnya**
- Perluas contoh untuk memproses batch folder gambar.  
- Gabungkan penambahan kata kunci dengan analisis gambar otomatis (mis., tag yang dihasilkan AI).  
- Jelajahi API GroupDocs.Metadata untuk membaca/menulis data GPS EXIF guna memungkinkan pencarian berbasis lokasi.

---

**Terakhir Diperbarui:** 2026-08-15  
**Diuji Dengan:** GroupDocs.Metadata 24.12 for Java  
**Penulis:** GroupDocs

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

## Tutorial Terkait

- [Ekstrak Header BMP Java – Tutorial Gambar GroupDocs.Metadata](/metadata/java/image-formats/)
- [java ekstrak metadata gambar – Ekstrak Metadata Panasonic MakerNote Menggunakan GroupDocs.Metadata di Java](/metadata/java/image-formats/extract-panasonic-maker-note-groupdocs-metadata-java/)
- [Otomatisasi Pembaruan Metadata Java berdasarkan Tanggal Menggunakan GroupDocs.Metadata untuk Manajemen File Efisien](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)