---
date: '2026-06-17'
description: Pelajari cara mengubah waktu pembuatan diagram dan mengotomatiskan pembaruan
  metadata untuk file diagram menggunakan GroupDocs.Metadata di Java.
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: Ubah Waktu Pembuatan Diagram dalam Metadata dengan GroupDocs Java
type: docs
url: /id/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Ubah Waktu Pembuatan Diagram dalam Metadata dengan GroupDocs Java

Dalam tutorial langkah‑demi‑langkah ini Anda akan menemukan cara **mengubah waktu pembuatan diagram** dan memperbarui properti bawaan lainnya dari file diagram menggunakan pustaka GroupDocs.Metadata untuk Java. Mengotomatisasi perubahan ini menghemat jam kerja manual, menjamin konsistensi cap waktu di seluruh repositori Anda, dan membuat diagram Anda dapat dicari secara instan dalam sistem manajemen dokumen apa pun.

## Jawaban Cepat
- **Apa tujuan utama?** Ubah waktu pembuatan diagram dan metadata lainnya dalam file diagram.  
- **Pustaka mana yang harus saya gunakan?** GroupDocs.Metadata for Java.  
- **Apakah saya memerlukan lisensi?** Uji coba gratis sudah cukup untuk pengujian; lisensi penuh diperlukan untuk produksi.  
- **Bisakah saya memproses banyak diagram secara batch?** Ya—bungkus logika yang sama dalam loop atau aliran paralel.  
- **Versi Java apa yang diperlukan?** JDK 8 atau lebih tinggi.

## Apa itu “mengubah waktu pembuatan diagram” dalam metadata diagram?
Mengubah waktu pembuatan menimpa cap waktu asli yang disimpan di dalam file diagram (seperti VDX atau VSDX) dengan nilai tanggal‑waktu baru. Ini memungkinkan Anda menyelaraskan metadata file dengan tanggal pemrosesan atau pengarsipan yang sebenarnya, bukan cap waktu asli penulis, yang penting untuk jejak audit dan hasil pencarian yang akurat.

## Mengapa mengotomatisasi pembaruan metadata untuk diagram?
Mengotomatisasi metadata memastikan setiap diagram mengikuti standar penamaan, kategorisasi, dan cap waktu yang sama tanpa kesalahan manusia. Ini juga mempercepat migrasi massal, mengurangi risiko kepatuhan, dan meningkatkan kemampuan penemuan dalam platform DMS perusahaan—menghemat hingga 70 % upaya manual dalam proyek berskala besar.

## Prasyarat
- **Java Development Kit (JDK) 8+** terpasang di mesin Anda.  
- **IDE** seperti IntelliJ IDEA atau Eclipse.  
- **Maven** (atau penanganan JAR manual) untuk manajemen dependensi.  
- Pemahaman dasar tentang kelas Java, metode, dan penanganan pengecualian.

### Perpustakaan dan Dependensi yang Diperlukan
Tambahkan repositori dan dependensi berikut ke file `pom.xml` Anda jika menggunakan Maven:

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
Jika Anda lebih suka mengunduh langsung, kunjungi [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) untuk mendapatkan versi terbaru.

### Penyiapan Lingkungan
- JDK 8 atau lebih baru.  
- IntelliJ IDEA, Eclipse, atau IDE kompatibel Java apa pun.  

### Prasyarat Pengetahuan
Pemahaman tentang sintaks Java dan I/O file dasar akan membuat tutorial lebih lancar, tetapi langkah‑langkahnya dijelaskan dengan bahasa yang sederhana.

## Menyiapkan GroupDocs.Metadata untuk Java
### Instruksi Instalasi
**Pengguna Maven:** Potongan kode di atas menambahkan repositori dan JAR yang diperlukan secara otomatis.  
**Pengguna Unduhan Langsung:** Setelah mengunduh JAR dari [GroupDocs](https://releases.groupdocs.com/metadata/java/), tambahkan ke classpath proyek Anda.

### Perolehan Lisensi
- **Free Trial:** Jelajahi pustaka tanpa biaya.  
- **Temporary License:** Dapatkan lisensi sementara untuk pengujian lanjutan [di sini](https://purchase.groupdocs.com/temporary-license/).  
- **Purchase:** Dapatkan lisensi penuh untuk lingkungan produksi.

### Inisialisasi Dasar
`Metadata` adalah kelas inti yang mewakili kontainer metadata dokumen dan menyediakan akses baca/tulis ke semua properti bawaan. Untuk mulai menggunakan GroupDocs.Metadata, impor kelas tersebut dan buka file diagram:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

## Panduan Implementasi
### Cara mengubah waktu pembuatan dalam file diagram
Pada bagian ini kami akan menjelaskan setiap langkah yang diperlukan untuk **mengubah waktu pembuatan diagram** dan memperbarui properti umum lainnya seperti penulis, perusahaan, dan kategori. Prosesnya melibatkan memuat diagram dengan Metadata API, mengakses paket root, mengatur bidang yang diinginkan, dan akhirnya menyimpan perubahan ke file baru, memastikan file asli tetap tidak tersentuh.

#### Langkah 1: Muat Dokumen Diagram
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Penjelasan:* Konstruktor `Metadata` menerima path ke file diagram Anda. Blok try‑with‑resources memastikan file ditutup dengan benar setelah operasi.

#### Langkah 2: Akses Paket Root
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Penjelasan:* Paket root memberi Anda akses langsung ke semua bidang metadata bawaan untuk diagram.

#### Langkah 3: Atur Properti Pembuat
```java
root.getDocumentProperties().setCreator("test author");
```  
*Penjelasan:* Menetapkan nama penulis baru. Ganti `"test author"` dengan pembuat yang sebenarnya.

#### Langkah 4: Ubah Waktu Pembuatan
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Penjelasan:* Baris ini **mengubah waktu pembuatan** menjadi tanggal dan waktu sistem saat ini. Anda juga dapat memberikan instance `Date` tertentu jika memerlukan cap waktu khusus.

#### Langkah 5: Tentukan Informasi Perusahaan
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Penjelasan:* Menyimpan nama perusahaan yang terkait dengan diagram—berguna untuk pelacakan perusahaan.

#### Langkah 6: Atur Kategori Dokumen
```java
root.getDocumentProperties().setCategory("test category");
```  
*Penjelasan:* Mengkategorikan file, membantu Anda **memperbarui kategori diagram** secara konsisten di seluruh repositori.

#### Langkah 7: Tambahkan Kata Kunci
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Penjelasan:* Kata kunci meningkatkan kemampuan pencarian; Anda dapat mencantumkan istilah apa pun yang relevan dengan konten diagram.

#### Langkah 8: Simpan Perubahan
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Penjelasan:* Menyimpan semua modifikasi ke file baru, meninggalkan file asli tidak tersentuh.

### Kesulitan Umum & Pemecahan Masalah
- **File Not Found:** Verifikasi path input dan pastikan ekstensi file cocok dengan format sebenarnya.  
- **Access Denied:** Periksa izin baca/tulis untuk direktori input dan output.  
- **Invalid Date Format:** Gunakan objek `java.util.Date` atau `java.time` yang kompatibel dengan API.  

## Aplikasi Praktis
1. **Automating Document Archiving** – Saat memindahkan diagram lama ke arsip, secara otomatis **mengubah waktu pembuatan diagram** ke tanggal pengarsipan dan menetapkan kategori seragam.  
2. **Version Control Integration** – Jaga cap waktu tetap sinkron dengan commit Git dengan memperbarui waktu pembuatan pada setiap rilis.  
3. **Enterprise DMS Standardization** – Terapkan kebijakan perusahaan secara menyeluruh untuk penulis, perusahaan, dan kata kunci di semua aset diagram.

## Pertimbangan Kinerja
- **Batch Processing:** Bungkus langkah‑langkah di atas dalam loop untuk menangani puluhan file dalam satu kali jalankan.  
- **Memory Management:** Lepaskan setiap instance `Metadata` dengan cepat (blok try‑with‑resources melakukannya secara otomatis).  
- **Asynchronous Execution:** Untuk batch besar, pertimbangkan `CompletableFuture` untuk menjalankan pembaruan secara paralel tanpa memblokir thread utama.  
- **Quantified Capability:** GroupDocs.Metadata mendukung lebih dari 30 format diagram dan dapat memproses file hingga 500 MB tanpa memuat seluruh dokumen ke memori, memberikan pembaruan dalam kurang dari 200 ms per file pada perangkat keras server tipikal.

## Kesimpulan
Anda sekarang tahu cara **mengubah waktu pembuatan diagram** dan memperbarui properti metadata bawaan lainnya untuk dokumen diagram menggunakan GroupDocs.Metadata di Java. Dengan mengotomatisasi langkah‑langkah ini, Anda dapat mempertahankan dokumentasi yang konsisten, dapat dicari, dan mematuhi standar di seluruh organisasi Anda.

**Langkah Selanjutnya**
- Eksperimen dengan format file lain yang didukung oleh GroupDocs.Metadata (PDF, DOCX, dll.).  
- Integrasikan kode ke dalam pipeline CI/CD untuk menegakkan standar metadata pada setiap build.  

Siap mencobanya? Kunjungi [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) dan mulailah mengimplementasikan otomatisasi metadata Anda sendiri hari ini.

---

**Terakhir Diperbarui:** 2026-06-17  
**Diuji Dengan:** GroupDocs.Metadata 24.12  
**Penulis:** GroupDocs  

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya menggunakan pendekatan ini dengan format diagram lain seperti VSDX?**  
A: Ya, API yang sama bekerja untuk semua format diagram yang didukung oleh GroupDocs.Metadata.

**Q: Apakah saya memerlukan lisensi untuk build pengembangan?**  
A: Uji coba gratis sudah cukup untuk pengembangan dan pengujian; lisensi penuh diperlukan untuk penerapan produksi.

**Q: Bagaimana saya dapat memperbarui beberapa properti dalam satu panggilan?**  
A: Atur setiap properti pada objek `DocumentProperties` sebelum memanggil `metadata.save(...)`; pustaka akan menulis semuanya sekaligus.

**Q: Apakah aman menimpa file asli?**  
A: Disarankan untuk menyimpan ke file baru (seperti yang ditunjukkan) dan mengganti file asli hanya setelah memastikan pembaruan berhasil.

**Q: Bagaimana jika saya perlu mengatur tanggal pembuatan khusus alih-alih waktu saat ini?**  
A: Buat `java.util.Date` (atau instance `java.time`) dengan cap waktu yang diinginkan dan berikan ke `setTimeCreated`.

## Tutorial Terkait

- [Cara Memperbarui Metadata Diagram Java dengan GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [Cara Memperbarui Metadata Penulis DXF dengan GroupDocs.Metadata untuk Java – Panduan Lengkap](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Otomatisasi Pembaruan Metadata Java berdasarkan Tanggal Menggunakan GroupDocs.Metadata untuk Manajemen File yang Efisien](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)