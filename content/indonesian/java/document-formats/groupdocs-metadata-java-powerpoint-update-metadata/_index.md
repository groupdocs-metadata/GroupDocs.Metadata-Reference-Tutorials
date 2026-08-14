---
date: '2026-05-27'
description: Pelajari cara mengatur CreatedTime pptx di Java menggunakan dependensi
  GroupDocs Maven untuk memperbarui metadata PowerPoint, termasuk cara mengubah tanggal
  pembuatan PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Atur CreatedTime PPTX di Java dengan Dependensi GroupDocs Maven
type: docs
url: /id/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Atur CreatedTime PPTX di Java dengan GroupDocs.Metadata

Metadata yang akurat sangat penting untuk kepatuhan dan kemampuan penemuan dalam alur kerja dokumen modern. Dengan **GroupDocs.Metadata** Anda dapat secara programatis **set PPTX CreatedTime in Java**, memungkinkan Anda **change PPTX creation date** bersama properti bawaan lainnya seperti penulis atau perusahaan. Tutorial ini memandu Anda melalui pengaturan Maven, inisialisasi API, memperbarui metadata, dan menyimpan presentasi yang telah dimodifikasi—semua dengan kode yang jelas dan siap produksi.

## Jawaban Cepat
- **Perpustakaan mana yang memperbarui metadata PowerPoint di Java?** GroupDocs.Metadata via the GroupDocs Maven dependency.  
- **Apakah saya dapat mengatur properti PPTX CreatedTime?** Yes—use `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Apakah lisensi diperlukan untuk produksi?** A trial works for evaluation; a commercial license is mandatory for production deployments.  
- **Alat build apa yang digunakan contoh ini?** Maven (you can also download the JAR manually).  
- **Apakah API mendukung Java 8 dan yang lebih baru?** Absolutely—GroupDocs.Metadata targets Java 8+.

## Apa Itu Dependensi Maven GroupDocs?
**GroupDocs Maven dependency** adalah entri repositori yang kompatibel dengan Maven yang menarik pustaka GroupDocs.Metadata terbaru ke dalam proyek Java Anda. Ini menyederhanakan manajemen dependensi dengan secara otomatis menyelesaikan pustaka transitive, menjamin Anda selalu menggunakan versi terbaru dan paling aman, serta menghilangkan kebutuhan untuk mengunduh JAR secara manual atau melacak versi.

## Mengapa Menggunakan GroupDocs.Metadata untuk Mengubah Tanggal Pembuatan PPTX?
GroupDocs.Metadata memungkinkan pembaruan otomatis, siap batch, dari timestamp pembuatan PPTX, memastikan setiap presentasi mematuhi kebijakan perusahaan atau persyaratan hukum. Dengan secara programatis mengatur properti CreatedTime Anda menghindari pengeditan manual, mengurangi kesalahan manusia, dan dapat mengintegrasikan perubahan ke dalam pipeline CI/CD atau skrip migrasi untuk manajemen dokumen yang mulus.

## Prasyarat
- Java 8 atau lebih tinggi terpasang.  
- IDE seperti IntelliJ IDEA atau Eclipse.  
- Maven untuk penanganan dependensi.  
- Akses ke trial GroupDocs atau lisensi yang dibeli.

## Cara Mengatur PPTX CreatedTime di Java?

Kelas `Metadata` mewakili sebuah dokumen dan menyediakan akses ke properti metadata-nya.

Muat file PowerPoint Anda dengan `new Metadata("presentation.pptx")`, ambil paket root, panggil `setCreatedTime` dengan `java.util.Date` yang diinginkan, dan akhirnya panggil `save` untuk menulis perubahan. Alur end‑to‑end ini memodifikasi tanggal pembuatan sambil mempertahankan semua konten slide dan properti lainnya.

### Pengaturan Maven
Tambahkan repositori GroupDocs dan dependensi metadata ke `pom.xml` Anda:

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

> **Pro tip:** Menjaga nomor versi tetap terbaru memastikan Anda mendapatkan perbaikan bug dan peningkatan performa terkini.

### Unduhan Langsung (jika Anda lebih suka tidak menggunakan Maven)

Sebagai alternatif, unduh JAR terbaru dari [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Akuisisi Lisensi

Mulailah dengan trial gratis atau minta lisensi sementara untuk mengevaluasi GroupDocs.Metadata. Untuk penggunaan produksi, beli lisensi melalui [GroupDocs' official website](https://purchase.groupdocs.com/temporary-license/).

## Inisialisasi dan Pengaturan Dasar

Setelah pustaka berada di classpath, Anda dapat membuat instance `Metadata` yang menunjuk ke file PowerPoint Anda:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Kode ini membuka presentasi dalam blok try‑with‑resources, menjamin bahwa handle file dilepaskan secara otomatis.

## Panduan Langkah‑per‑Langkah untuk Memperbarui Metadata Bawaan

### Langkah 1: Muat Dokumen Presentasi

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Memuat file membangun koneksi yang memungkinkan Anda membaca atau menulis metadata.

### Langkah 2: Akses Paket Root Presentasi

Objek `root` memberikan akses ke paket inti presentasi dan properti bawaan nya.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

Objek `root` menampilkan semua properti dokumen bawaan.

### Langkah 3: Perbarui Properti Dokumen Bawaan (termasuk tanggal pembuatan)

`setCreatedTime` menetapkan timestamp pembuatan baru ke dokumen.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Di sini kami menunjukkan cara **set PPTX CreatedTime** dengan menetapkan objek `Date` baru ke `CreatedTime`. Ganti `new Date()` dengan timestamp spesifik apa pun yang Anda perlukan.

### Langkah 4: Simpan Presentasi yang Diperbarui

`save` menulis metadata yang dimodifikasi kembali ke sebuah file.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

Pemanggilan `save` menulis metadata yang dimodifikasi kembali ke file PowerPoint baru, meninggalkan file asli tidak tersentuh.

## Tips Pemecahan Masalah
- **File Not Found:** Periksa kembali jalur input dan izin file.  
- **Version Mismatch:** Pastikan versi `groupdocs-metadata` cocok dengan runtime Java Anda.  
- **Property Not Updating:** Verifikasi bahwa Anda memanggil `setCreatedTime` (atau setter yang relevan) sebelum memanggil `save`.

## Aplikasi Praktis

1. **Corporate Branding:** Secara otomatis menyisipkan nama perusahaan dan kategori yang tepat ke semua deck slide sebelum distribusi.  
2. **Document Management Systems:** Memperkaya file PPTX dengan metadata yang dapat dicari untuk pengambilan yang lebih cepat.  
3. **Educational Resources:** Menjaga informasi penulis dan kurikulum tetap terbaru di seluruh slide kuliah.  
4. **Collaboration Tracking:** Mencatat nama kontributor untuk menjaga akuntabilitas.  
5. **CMS Integration:** Menyinkronkan perubahan metadata dengan platform manajemen konten Anda secara real time.

## Pertimbangan Kinerja
- **Batch Processing:** Loop melalui daftar file dan gunakan kembali satu instance `Metadata` bila memungkinkan.  
- **Memory Management:** Selalu gunakan try‑with‑resources (seperti yang ditunjukkan) untuk membebaskan sumber daya native dengan cepat.  
- **Efficient Data Structures:** Simpan pembaruan metadata dalam peta sebelum menerapkannya untuk mengurangi panggilan berulang.

## Pertanyaan yang Sering Diajukan

**Q: Apa tujuan utama dependensi Maven GroupDocs?**  
A: Ini menyediakan cara yang nyaman untuk menyertakan pustaka GroupDocs.Metadata terbaru dalam proyek Java berbasis Maven.

**Q: Bagaimana cara mengatur tanggal pembuatan PPTX tanpa memengaruhi properti lain?**  
A: Gunakan `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` sebelum memanggil `metadata.save()`.

**Q: Apakah saya memerlukan lisensi untuk menjalankan kode ini dalam pengembangan?**  
A: Lisensi trial sementara cukup untuk pengembangan dan pengujian; lisensi penuh diperlukan untuk produksi.

**Q: Bisakah saya memperbarui bidang metadata khusus juga?**  
A: Ya—GroupDocs.Metadata mendukung baik properti bawaan maupun khusus melalui API-nya.

**Q: Apakah ada cara untuk mengembalikan perubahan jika saya membuat kesalahan?**  
A: Simpan salinan file asli atau baca nilai properti yang ada sebelum menimpa mereka, lalu pulihkan jika diperlukan.

## Sumber Daya

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://apireference.groupdocs.com/metadata/java/)

---

**Terakhir Diperbarui:** 2026-05-27  
**Diuji Dengan:** GroupDocs.Metadata 24.12 for Java  
**Penulis:** GroupDocs  

## Tutorial Terkait

- [Update Custom Metadata in PowerPoint Using GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [How to Update Word Document Metadata Using GroupDocs.Metadata Java: A Complete Guide](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Efficiently Update PDF Metadata with GroupDocs.Metadata in Java for Document Management](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)