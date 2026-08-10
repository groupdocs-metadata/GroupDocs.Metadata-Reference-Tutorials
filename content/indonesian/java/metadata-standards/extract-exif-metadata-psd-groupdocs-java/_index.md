---
date: '2026-08-10'
description: Pelajari cara mengekstrak metadata EXIF dari file PSD menggunakan GroupDocs.Metadata
  untuk Java. Panduan ini mencakup ekstraksi dasar, paket IFD, data GPS, dan contoh
  penggunaan dunia nyata.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Pelajari cara mengekstrak metadata EXIF dari file PSD menggunakan
  GroupDocs.Metadata untuk Java. Panduan langkah demi langkah, potongan kode, dan
  tips pemecahan masalah untuk pengembang.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Cara mengekstrak metadata EXIF dari file PSD dengan GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: Cara mengekstrak metadata EXIF dari file PSD dengan GroupDocs.Metadata
type: docs
url: /id/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Cara mengekstrak metadata EXIF dari file PSD dengan GroupDocs.Metadata

Mengekstrak **metadata EXIF** dari file PSD adalah langkah rutin namun kuat ketika Anda perlu mengaudit asal‑usul gambar, mengotomatisasi penandaan aset, atau membangun perpustakaan media yang dapat dicari. Dalam tutorial ini Anda akan menemukan **cara mengekstrak EXIF** dengan cepat menggunakan GroupDocs.Metadata untuk Java, melihat panggilan API yang tepat, dan belajar cara menangani paket IFD lanjutan serta koordinat GPS. Pada akhir tutorial Anda akan siap mengintegrasikan ekstraksi metadata ke dalam alur kerja berbasis Java apa pun.

## Jawaban Cepat
Kelas `Metadata` mewakili sebuah file dan menyediakan akses ke metadata-nya.

- **Apa baris kode pertama?** `Metadata metadata = new Metadata("sample.psd");`
- **Metode mana yang mengembalikan nama artis?** `metadata.getExif().getArtist();`
- **Bisakah saya membaca data GPS?** Ya – gunakan `metadata.getExif().getGpsInfo();`
- **Apakah saya memerlukan lisensi untuk produksi?** Lisensi GroupDocs.Metadata yang valid diperlukan setelah periode percobaan.
- **Versi Java yang didukung?** Java 8 atau lebih baru (hingga Java 21).

## Apa itu metadata EXIF?
Metadata EXIF (Exchangeable Image File Format) menyimpan pengaturan kamera, cap waktu pembuatan, dan data lokasi di dalam file gambar. GroupDocs.Metadata membaca informasi ini langsung dari struktur biner file PSD, menampilkannya melalui API Java yang bersih. Ini memungkinkan pengembang untuk secara programatis mengambil detail seperti model kamera, waktu paparan, dan koordinat GPS tanpa inspeksi manual.

## Mengapa menggunakan GroupDocs.Metadata untuk Java?
GroupDocs.Metadata mendukung **lebih dari 30 format file** (termasuk PSD, JPEG, PNG, TIFF) dan dapat memproses file hingga **2 GB** tanpa memuat seluruh dokumen ke memori. Perpustakaan ini mengekstrak **lebih dari 150 tag EXIF yang berbeda**, memastikan Anda memiliki seluruh set atribut kamera dan GPS yang diperlukan untuk analitik atau kepatuhan.

## Prasyarat
- **Java Development Kit (JDK) 8** atau yang lebih baru terpasang di mesin Anda.  
- **Maven** untuk manajemen dependensi.  
- **GroupDocs.Metadata untuk Java versi 24.12** (atau yang lebih baru).  
- Familiaritas dasar dengan kelas Java, objek, dan penanganan pengecualian.

### Perpustakaan dan dependensi yang diperlukan
| Dependensi | Koordinat Maven |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Penyiapan lingkungan
Anda sebaiknya memiliki IDE yang kompatibel dengan Maven seperti IntelliJ IDEA atau Eclipse. Buat proyek Maven baru atau tambahkan dependensi ke proyek yang sudah ada.

## Cara menyiapkan GroupDocs.Metadata untuk Java
GroupDocs.Metadata dapat ditambahkan ke proyek Maven dengan beberapa baris konfigurasi. Langkah‑langkah berikut menunjukkan cara menyertakan repositori dan dependensi sehingga perpustakaan tersedia di classpath.

### Penyiapan Maven
Add the following snippet to your `pom.xml` inside the `<dependencies>` section:

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

### Unduhan langsung
Sebagai alternatif, unduh JAR terbaru dari halaman rilis resmi: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Akuisisi lisensi
To run the library beyond the 30‑day trial, obtain a temporary or full license:

1. Kunjungi [License Purchase Page](https://purchase.groupdocs.com/temporary-license).  
2. Pilih **temporary** untuk pengujian atau **full** untuk produksi.  
3. Ikuti petunjuk di layar untuk menyematkan file lisensi (`metadata.lic`) ke classpath Java Anda.

### Inisialisasi dan penyiapan dasar
After the library is on the classpath, initialize it as shown below:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## Cara mengekstrak properti metadata EXIF dasar dari gambar PSD
Bagian ini menjelaskan cara memuat file PSD, mengakses kontainer EXIF, dan membaca tag paling umum seperti **artist**, **copyright**, dan **software**. Prosesnya melibatkan pembuatan instance `Metadata`, memanggil `getExif()`, dan kemudian mengambil properti individu dengan metode getter sederhana.

### Implementasi langkah‑demi‑langkah
1. **Buat instance `Metadata`** yang menunjuk ke file PSD Anda.  
2. **Panggil `getExif()`** untuk memperoleh kontainer EXIF.  
3. **Baca properti individu** seperti `getArtist()`, `getCopyright()`, dan `getSoftware()`.  
4. **Cetak atau simpan** nilai-nilai tersebut sesuai logika aplikasi Anda.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **Tip pro:** Objek `Metadata` secara otomatis mendeteksi format file, sehingga Anda dapat menggunakan kembali kode yang sama untuk file JPEG atau TIFF tanpa modifikasi.

## Cara mengekstrak properti paket EXIF IFD dari gambar PSD
Bagian IFD (Image File Directory) menyimpan detail teknis yang lebih dalam seperti **nomor seri kamera**, **model lensa**, dan **komentar pengguna**. `Ifd0` mewakili Image File Directory utama yang berisi informasi kamera dasar. Mengekstrak bidang‑bidang ini berguna untuk analisis forensik atau katalogisasi presisi tinggi.

### Langkah‑langkah implementasi
1. **Gunakan kembali instance `Metadata`** dari bagian sebelumnya.  
2. **Navigasikan ke kontainer IFD** melalui `metadata.getExif().getIfd0()`.  
3. **Baca properti** seperti `getBodySerialNumber()` dan `getUserComment()`.  
4. **Keluarkan data** atau petakan ke model domain Anda.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## Cara mengambil data GPS (lintang, bujur) dari file PSD
Banyak kamera modern menyematkan koordinat GPS dalam blok EXIF. `GpsInfo` menyimpan koordinat geografis yang diekstrak dari data EXIF. Panggil `metadata.getExif().getGpsInfo()` dan kemudian gunakan `getLatitude()`, `getLongitude()`, dan `getAltitude()` untuk memperoleh data lokasi yang tepat—tanpa parsing tambahan diperlukan.

### Langkah‑langkah terperinci
1. **Dapatkan objek info GPS**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Baca lintang dan bujur**: `gps.getLatitude()` mengembalikan `double` dalam derajat desimal.  
3. **Tangani data yang hilang**: API mengembalikan `null` jika tag tidak ada, jadi lindungi dari `NullPointerException`.

> **Kesalahan umum:** Beberapa file PSD menyimpan koordinat GPS dalam bentuk bilangan rasional; perpustakaan menormalkannya secara otomatis, tetapi file lama mungkin memerlukan konversi manual.

## Masalah umum dan pemecahan masalah
| Gejala | Penyebab kemungkinan | Perbaikan |
|---------|----------------------|-----------|
| `Unsupported format` exception | Using an older GroupDocs.Metadata version that doesn’t recognise PSD | Upgrade to version 24.12 or later |
| `NullPointerException` when calling `getArtist()` | EXIF tag not present in the source file | Check `metadata.getExif().hasArtist()` before reading |
| License error after 30 days | License file not found on the classpath | Place `metadata.lic` in `src/main/resources` or set `Metadata.setLicense("path/to/license")` |

## Pertanyaan yang sering diajukan
**Q: Bisakah saya mengekstrak metadata EXIF dari file PSD yang dilindungi kata sandi?**  
A: Ya. Muat file dengan `new Metadata("file.psd", "password")` dan kemudian akses data EXIF seperti biasa.

**Q: Apakah GroupDocs.Metadata mendukung pemrosesan batch banyak file PSD?**  
A: Tentu saja. Buat objek `Metadata` di dalam loop, atau gunakan pembantu `MetadataCollection` untuk memproses direktori secara efisien.

**Q: Versi Java apa yang secara resmi didukung?**  
A: Java 8 hingga Java 21 telah diuji sepenuhnya. Perpustakaan hanya menggunakan API standar, sehingga berfungsi pada JVM yang mematuhi standar.

**Q: Apakah memungkinkan menulis kembali data EXIF ke file PSD?**  
A: Ya. Setelah memodifikasi properti melalui objek `Exif`, panggil `metadata.save("output.psd")` untuk menyimpan perubahan.

**Q: Seberapa besar file PSD yang dapat ditangani perpustakaan tanpa kehabisan memori?**  
A: GroupDocs.Metadata men‑stream data dan dapat memproses file hingga **2 GB** pada mesin dengan RAM 8 GB tipikal, berkat arsitektur memori rendahnya.

## Kesimpulan
Anda kini tahu **cara mengekstrak metadata EXIF** dari file PSD menggunakan GroupDocs.Metadata untuk Java, mulai dari tag dasar hingga informasi IFD dan GPS lanjutan. Integrasikan potongan kode ini ke dalam pipeline pemrosesan gambar Anda untuk mengotomatisasi katalogisasi, pemeriksaan kepatuhan, atau layanan berbasis lokasi. Untuk eksplorasi lebih dalam, coba ekstrak metadata dari format lain yang didukung (JPEG, TIFF, PNG) atau bereksperimen dengan kemampuan menulis kembali untuk menyematkan tag khusus.

---

**Terakhir Diperbarui:** 2026-08-10  
**Diuji Dengan:** GroupDocs.Metadata 24.12 for Java  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Ekstrak Sumber Daya Gambar dari File PSD Menggunakan GroupDocs.Metadata di Java: Panduan Komprehensif](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Ekstrak Header PSD dan Info Layer Menggunakan GroupDocs.Metadata untuk Java: Panduan Komprehensif](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Ekstrak Properti MakerNote sebagai Tag TIFF/EXIF Menggunakan GroupDocs.Metadata di Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)