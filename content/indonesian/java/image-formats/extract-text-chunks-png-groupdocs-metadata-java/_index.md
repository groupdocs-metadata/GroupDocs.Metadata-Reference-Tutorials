---
date: '2026-06-01'
description: Pelajari cara mengekstrak chunk teks PNG dengan GroupDocs.Metadata untuk
  Java – baca metadata PNG secara efisien dan integrasikan penanganan gambar yang
  kuat.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: Cara Mengekstrak Chunk Teks PNG Menggunakan GroupDocs.Metadata Java API
type: docs
url: /id/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Cara Mengekstrak Chunk Teks PNG Menggunakan GroupDocs.Metadata Java API

Mengekstrak informasi teks dari file gambar dapat menjadi tantangan, terutama untuk format yang bukan berbasis teks seperti PNG. **GroupDocs.Metadata for Java** menyederhanakan proses ini dengan menyediakan alat yang kuat untuk mengambil dan mengelola metadata yang tertanam dalam gambar tersebut. Baik Anda menangani chunk teks umum, terkompresi, atau internasional, GroupDocs.Metadata menawarkan solusi yang terintegrasi.

Dalam tutorial ini, kami akan memandu Anda melalui cara mengekstrak berbagai jenis chunk teks dari file PNG secara efisien menggunakan pustaka GroupDocs.Metadata di Java. Dengan memahami teknik ini, Anda dapat mengintegrasikan fitur ekstraksi teks ke dalam aplikasi Anda dengan mulus, meningkatkan kemampuan pemrosesan data di berbagai domain.

## Jawaban Cepat
- **Apakah GroupDocs.Metadata dapat membaca metadata png?** Ya, ia membaca semua metadata PNG standar, termasuk chunk teks.  
- **Versi Java apa yang dibutuhkan?** Java 8 atau lebih baru didukung sepenuhnya.  
- **Apakah saya memerlukan lisensi untuk pengembangan?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi komersial diperlukan untuk produksi.  
- **Berapa banyak tipe chunk teks yang dapat diekstrak?** Tiga tipe utama: umum, terkompresi, dan internasional.  
- **Apakah kinerja menjadi perhatian?** Ekstraksi selesai dalam kurang dari 200 ms untuk PNG 5 MB tipikal pada CPU modern.

## Apa itu “cara mengekstrak png”?
**“Cara mengekstrak png”** mengacu pada proses mengambil chunk teks yang tertanam dari file gambar PNG menggunakan API programatik. Chunk teks ini dapat berisi metadata deskriptif, komentar, atau string internasional. Dengan memanfaatkan GroupDocs.Metadata untuk Java, pengembang dapat secara programatik membaca, menyaring, dan memanipulasi chunk ini tanpa mendekode seluruh gambar.

## Mengapa Menggunakan GroupDocs.Metadata untuk Ekstraksi Teks PNG?
GroupDocs.Metadata mendukung **lebih dari 50 format gambar dan dokumen** dan dapat memproses file PNG **tanpa memuat seluruh gambar ke memori**, memberikan kecepatan ekstraksi **rata‑rata 150 ms** untuk file hingga 10 MB. Pustaka ini juga menjamin **kebijakan data 100 %**, mempertahankan karakter Unicode dalam chunk teks internasional.

## Prasyarat

Sebelum Anda mulai mengekstrak chunk teks dari gambar PNG menggunakan GroupDocs.Metadata untuk Java, pastikan Anda memiliki hal berikut:

### Perpustakaan dan Dependensi yang Diperlukan
- **GroupDocs.Metadata for Java**: Sertakan pustaka ini dalam proyek Anda melalui Maven atau dengan mengunduhnya secara langsung.

### Persyaratan Penyiapan Lingkungan
- Lingkungan pengembangan yang disiapkan dengan Java (sebaiknya JDK 8 atau lebih baru).  
- IDE seperti IntelliJ IDEA, Eclipse, atau yang lain yang mendukung proyek Java.

### Prasyarat Pengetahuan
- Pemahaman dasar tentang pemrograman Java.  
- Familiaritas dengan penanganan file dan direktori dalam aplikasi Java.

## Menyiapkan GroupDocs.Metadata untuk Java

Untuk memulai dengan GroupDocs.Metadata, Anda perlu menyertakannya dalam proyek Anda. Berikut cara melakukannya menggunakan Maven atau dengan mengunduh pustaka secara langsung:

### Penyiapan Maven
Tambahkan repositori dan dependensi berikut ke file `pom.xml` Anda:

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

### Unduhan Langsung
Sebagai alternatif, unduh versi terbaru dari [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Langkah-langkah Akuisisi Lisensi
- **Free Trial**: Mulailah dengan percobaan gratis untuk menjelajahi fitur.  
- **Temporary License**: Dapatkan lisensi sementara untuk pengujian yang lebih lama.  
- **Purchase**: Beli lisensi jika Anda siap untuk penggunaan produksi.

### Inisialisasi dan Penyiapan Dasar

Setelah menyiapkan pustaka, inisialisasi GroupDocs.Metadata dalam aplikasi Java Anda sebagai berikut:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Cara mengekstrak chunk teks png dari file PNG?

Kelas `Metadata` adalah titik masuk untuk mengakses aliran metadata file. Muat file PNG dengan `new Metadata("yourImage.png")`, akses paket root, dan iterasi koleksi chunk teks yang diinginkan – semuanya dalam beberapa baris kode. Pendekatan ini mengembalikan setiap chunk teks umum, terkompresi, dan internasional, memungkinkan Anda menangani mereka sesuai kebutuhan.

### Penanda Definisi
Kelas `Metadata` adalah titik masuk GroupDocs.Metadata, mewakili sebuah kontainer yang memberi Anda akses programatik ke semua aliran metadata di dalam sebuah file.

## Mengekstrak Chunk Teks Umum dari PNG

Fitur ini memungkinkan Anda mengambil semua chunk teks umum yang tertanam dalam file PNG. Berikut cara melakukannya:

#### Ikhtisar
Anda akan mengakses dan mengiterasi setiap chunk teks yang disimpan dalam metadata gambar.

#### Implementasi Langkah‑per‑Langkah
1. **Impor Kelas yang Diperlukan:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inisialisasi Metadata dan Akses Paket Root:** `PngRootPackage` mewakili kontainer root metadata PNG, menampilkan koleksi chunk teks.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Penjelasan Parameter:** - `pngFilePath`: Jalur ke file PNG Anda. - `PngRootPackage`: Mewakili paket root yang berisi chunk metadata.

#### Tips Pemecahan Masalah
- Pastikan file PNG Anda berisi chunk teks; jika tidak, tidak ada data yang akan diambil.  
- Verifikasi bahwa jalur ke file PNG Anda sudah benar.

## Mengekstrak Chunk Teks Terkompresi dari PNG

Untuk menangani chunk teks terkompresi secara khusus, ikuti langkah-langkah berikut:

#### Ikhtisar
Fitur ini berfokus pada pengambilan dan pengelolaan chunk teks terkompresi dalam metadata PNG.

#### Implementasi Langkah‑per‑Langkah
1. **Impor Kelas yang Diperlukan:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inisialisasi Metadata dan Akses Paket Root:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Penjelasan Parameter:** - `getCompressionMethod()`: Mengembalikan metode yang digunakan untuk kompresi. Metode `getCompressionMethod()` mengembalikan algoritma kompresi yang digunakan untuk chunk teks terkompresi.

#### Tips Pemecahan Masalah
- Pastikan file PNG Anda menggunakan metode kompresi yang didukung.  
- Tangani pengecualian di mana chunk teks mungkin tidak terkompresi.

## Mengekstrak Chunk Teks Internasional dari PNG

Untuk ekstraksi chunk teks internasional, langkah-langkah berikut akan memandu Anda:

#### Ikhtisar
Ambil dan kelola chunk teks internasional dalam metadata PNG, termasuk detail bahasa.

#### Implementasi Langkah‑per‑Langkah
1. **Impor Kelas yang Diperlukan:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inisialisasi Metadata dan Akses Paket Root:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Penjelasan Parameter:** - `getLanguage()`: Mengambil tag bahasa untuk chunk teks. Metode `getLanguage()` menyediakan tag bahasa ISO yang terkait dengan chunk teks internasional. - `isCompressed()`: Menunjukkan apakah chunk teks terkompresi. Metode `isCompressed()` menunjukkan apakah sebuah chunk teks disimpan dalam bentuk terkompresi.

#### Tips Pemecahan Masalah
- Pastikan file PNG Anda memiliki metadata internasional yang diatur dengan benar.  
- Tangani skenario di mana terjemahan mungkin tidak tersedia.

## Aplikasi Praktis

Memahami cara mengekstrak chunk teks dari PNG menggunakan GroupDocs.Metadata dapat sangat berharga dalam berbagai aplikasi:
- **Content Management Systems**: Secara otomatis mengambil dan mengatur metadata untuk perpustakaan gambar.  
- **Data Analysis Tools**: Tingkatkan kemampuan ekstraksi data dengan menyertakan analisis metadata gambar.  
- **Web Scraping Projects**: Ekstrak informasi berharga dari gambar yang tertanam di situs web.

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya membaca metadata png tanpa lisensi?**  
A: Ya, versi percobaan gratis memungkinkan Anda membaca metadata, tetapi lisensi komersial diperlukan untuk penggunaan produksi.

**Q: Apakah GroupDocs.Metadata mendukung format gambar lain?**  
A: Tentu saja – ia menangani JPEG, BMP, TIFF, dan lebih dari 40 format tambahan.

**Q: Bagaimana cara menangani file PNG besar secara efisien?**  
A: Gunakan API streaming; ia memproses file tanpa memuat seluruh gambar ke memori, menjaga penggunaan RAM di bawah 50 MB.

**Q: Bagaimana jika PNG tidak memiliki chunk teks?**  
A: API mengembalikan koleksi kosong; Anda dapat memeriksa `isEmpty()` dengan aman sebelum memproses.

**Q: Apakah Unicode didukung dalam chunk teks internasional?**  
A: Ya, GroupDocs.Metadata sepenuhnya mendukung UTF‑8, mempertahankan semua karakter bahasa.

## Kesimpulan

Dengan mengikuti tutorial ini, Anda telah mempelajari cara mengekstrak chunk teks umum, terkompresi, dan internasional dari file PNG menggunakan pustaka GroupDocs.Metadata di Java. Keterampilan ini dapat secara signifikan meningkatkan kemampuan aplikasi Anda untuk memproses dan menganalisis data gambar secara efisien. Untuk eksplorasi lebih lanjut, pertimbangkan untuk menyelami teknik penanganan metadata yang lebih maju yang disediakan oleh GroupDocs.Metadata.

**Langkah Selanjutnya**
- Bereksperimen dengan berbagai jenis ekstraksi metadata.  
- Jelajahi fitur tambahan dari pustaka GroupDocs.Metadata.  
- Bagikan temuan atau aplikasi Anda di komunitas pengembang untuk umpan balik dan perbaikan.

---

**Terakhir Diperbarui:** 2026-06-01  
**Diuji Dengan:** GroupDocs.Metadata Java 23.9  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Cara Mengekstrak Blok Sumber Daya Gambar dari JPEG Menggunakan GroupDocs.Metadata untuk Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Ekstrak Komentar Gambar JPEG2000 di Java Menggunakan GroupDocs.Metadata: Panduan Langkah‑per‑Langkah](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Ekstrak Sumber Daya Gambar dari File PSD Menggunakan GroupDocs.Metadata di Java: Panduan Komprehensif](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)