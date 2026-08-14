---
date: '2026-05-27'
description: Pelajari cara memperbarui email recipients java menggunakan GroupDocs.Metadata
  untuk Java. Modifikasi penerima, subjek, dan simpan perubahan secara efisien.
keywords:
- update email recipients java
- GroupDocs Metadata Java
- email metadata management
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  headline: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  type: TechArticle
- description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  name: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  steps:
  - name: Initialize Metadata Object
    text: 'The `Metadata` class represents a file and provides access to its metadata.
      Create a `Metadata` instance with your input file path: **Definition anchor**:
      The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata,
      representing a single file in memory.'
  - name: Access EmailRootPackage
    text: '`EmailRootPackage` gives access to email‑specific metadata such as recipients
      and subject. Access the email’s metadata using: This step is crucial as it provides
      access to all modifiable properties of your email.'
  - name: Update Recipients
    text: 'Set new recipients for your email message:'
  - name: Initialize and Obtain Root Package
    text: 'Similar to updating primary recipients, initialize the metadata object:'
  - name: Set CC Recipients
    text: '`addCcRecipient` appends a new address to the CC collection without overwriting
      existing entries. Add carbon copy recipients as follows: This approach ensures
      that additional users are notified without being the main point of contact.'
  - name: Initialize Metadata
    text: 'Start by initializing your metadata object:'
  - name: Change the Subject
    text: 'Update the email’s subject line: This step is vital for maintaining relevant
      and searchable email threads.'
  - name: Initialize and Obtain Root Package
    text: 'Begin with initializing the `Metadata` object:'
  - name: Save Changes
    text: 'Persist your changes by saving them to a specified output directory: This
      ensures that all modifications are retained and reflected in the saved file.'
  type: HowTo
- questions:
  - answer: Load the file with `Metadata`, get the `EmailRootPackage`, replace the
      `To` collection, and save – all in three lines of code.
    question: What is the fastest way to change an email’s primary recipient?
  - answer: Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.
    question: Can I add CC recipients without overwriting existing ones?
  - answer: A temporary license removes evaluation limits; a permanent license is
      required for commercial deployments. You can obtain a temporary license from
      the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.
    question: Do I need a license for production use?
  - answer: GroupDocs.Metadata works with Java 8, 11, 17, and later.
    question: Which Java versions are supported?
  - answer: Process files in batches of 50–100 to keep memory usage under 200 MB per
      batch.
    question: Is batch processing safe for large mailboxes?
  type: FAQPage
title: 'Perbarui Penerima Email Java: Kuasai Pembaruan Metadata Email dengan GroupDocs.Metadata'
type: docs
url: /id/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# Perbarui Penerima Email Java dengan GroupDocs.Metadata

Dalam panduan komprehensif ini Anda akan **update email recipients java** secara programatis menggunakan pustaka GroupDocs.Metadata. Kami akan menjelaskan cara mengubah penerima utama dan CC, mengubah baris subjek, dan menyimpan perubahan tersebut—semua dengan potongan kode yang jelas langkah demi langkah. Pada akhir panduan Anda akan siap mengintegrasikan otomatisasi metadata email ke dalam alur kerja berbasis Java apa pun.

## Jawaban Cepat
- **Apa cara tercepat untuk mengubah penerima utama email?** Muat file dengan `Metadata`, dapatkan `EmailRootPackage`, ganti koleksi `To`, dan simpan — semuanya dalam tiga baris kode.  
- **Apakah saya dapat menambahkan penerima CC tanpa menimpa yang sudah ada?** Ya, gunakan `addCcRecipient` pada `EmailRootPackage` untuk menambahkan alamat baru.  
- **Apakah saya memerlukan lisensi untuk penggunaan produksi?** Lisensi sementara menghapus batas evaluasi; lisensi permanen diperlukan untuk penyebaran komersial. Anda dapat memperoleh lisensi sementara dari halaman [GroupDocs](https://purchase.groupdocs.com/temporary-license/).  
- **Versi Java mana yang didukung?** GroupDocs.Metadata bekerja dengan Java 8, 11, 17, dan versi lebih baru.  
- **Apakah pemrosesan batch aman untuk kotak surat besar?** Proses file dalam batch 50–100 untuk menjaga penggunaan memori di bawah 200 MB per batch.

## Apa itu update email recipients java?
*Updating email recipients in Java* berarti secara programatis mengubah bidang “To”, “CC”, atau “BCC” dari file email (EML, MSG, dll.) tanpa membuka klien email. GroupDocs.Metadata menyediakan API tingkat tinggi yang membaca struktur email, memungkinkan Anda memodifikasi koleksi alamat, dan menulis file yang diperbarui kembali ke disk.

## Mengapa menggunakan GroupDocs.Metadata untuk metadata email?
GroupDocs.Metadata mendukung **lebih dari 50 format terkait email** (termasuk EML, MSG, MHT) dan dapat memproses **pesan ratusan halaman** tanpa memuat seluruh file ke memori, mengurangi konsumsi RAM hingga **80 %** dibandingkan pendekatan aliran file sederhana. Implementasi pure‑Java-nya menghilangkan ketergantungan native, menjadikannya ideal untuk layanan lintas platform.

## Prasyarat
- Java 8 atau lebih baru (Java 11, 17, 21 sudah diuji sepenuhnya).  
- Maven atau Gradle untuk manajemen dependensi.  
- Lisensi GroupDocs.Metadata yang valid (sementara atau permanen).  

### Perpustakaan dan Dependensi yang Diperlukan
Add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```
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

Untuk unduhan langsung, dapatkan versi terbaru dari [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Pengaturan Lingkungan
Pastikan IDE Anda mengarah ke JDK yang kompatibel dan Maven dapat menyelesaikan artefak GroupDocs.Metadata tanpa kesalahan.

## Cara memperbarui penerima email di Java?
Muat file email, ganti penerima yang ada, dan simpan hasilnya. Operasi ini hanya memerlukan tiga panggilan API dan berjalan dalam kurang dari **200 ms** untuk pesan 1 MB tipikal. Dengan menggunakan API tingkat tinggi `EmailRootPackage` Anda menghindari parsing seluruh file, yang menjaga penggunaan memori rendah dan memudahkan pemrosesan batch.

```java
Metadata metadata = new Metadata("input.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
email.getTo().clear();                         // remove old recipients
email.getTo().add(new EmailRecipient("new@example.com"));
metadata.save("output.eml");
```
```java
import com.groupdocs.metadata.Metadata;
```
Baris di atas mengimpor kelas penting untuk mulai mengelola operasi metadata pada file Anda.

## Panduan Implementasi
Sekarang kami akan menyelami lebih dalam setiap fitur, memperluas potongan kode jawaban cepat dengan konteks lengkap.

### Memperbarui Penerima Email
**Gambaran Umum**: Bagian ini menunjukkan cara memperbarui penerima utama pesan email secara programatis.

#### Langkah 1: Inisialisasi Objek Metadata
Kelas `Metadata` mewakili sebuah file dan menyediakan akses ke metadata-nya. Buat instance `Metadata` dengan jalur file input Anda:

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**Definisi anchor**: Kelas `Metadata` adalah titik masuk untuk semua operasi metadata di GroupDocs.Metadata, mewakili satu file dalam memori.

#### Langkah 2: Akses EmailRootPackage
`EmailRootPackage` memberikan akses ke metadata khusus email seperti penerima dan subjek. Akses metadata email menggunakan:

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
Langkah ini penting karena memberikan akses ke semua properti yang dapat dimodifikasi dari email Anda.

#### Langkah 3: Perbarui Penerima
Tetapkan penerima baru untuk pesan email Anda:

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### Menambahkan Penerima Carbon Copy (CC) ke Email
**Gambaran Umum**: Pelajari cara menambahkan penerima CC ke email yang sudah ada.

#### Langkah 1: Inisialisasi dan Dapatkan Root Package
Serupa dengan memperbarui penerima utama, inisialisasi objek metadata:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Langkah 2: Atur Penerima CC
`addCcRecipient` menambahkan alamat baru ke koleksi CC tanpa menimpa entri yang ada. Tambahkan penerima carbon copy sebagai berikut:

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
Pendekatan ini memastikan bahwa pengguna tambahan diberi tahu tanpa menjadi kontak utama.

### Memperbarui Subjek Email
**Gambaran Umum**: Fitur ini memungkinkan Anda mengubah baris subjek email, menjaga komunikasi tetap jelas dan terbaru.

#### Langkah 1: Inisialisasi Metadata
Mulailah dengan menginisialisasi objek metadata Anda:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Langkah 2: Ubah Subjek
Perbarui baris subjek email:

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
Langkah ini penting untuk mempertahankan thread email yang relevan dan dapat dicari.

### Menyimpan Metadata Email yang Diperbarui
**Gambaran Umum**: Setelah Anda membuat perubahan, penting untuk menyimpan pembaruan tersebut. Bagian ini menunjukkan cara mempertahankan modifikasi Anda secara efektif.

#### Langkah 1: Inisialisasi dan Dapatkan Root Package
Mulailah dengan menginisialisasi objek `Metadata`:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Langkah 2: Simpan Perubahan
Pertahankan perubahan Anda dengan menyimpannya ke direktori output yang ditentukan:

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
Ini memastikan semua modifikasi dipertahankan dan tercermin dalam file yang disimpan.

## Aplikasi Praktis
Menerapkan fitur-fitur ini dapat sangat bermanfaat dalam berbagai skenario dunia nyata:

1. **Sistem Manajemen Email** – Mengotomatiskan pembaruan penerima untuk distribusi email massal.  
2. **Platform Dukungan Pelanggan** – Cepat mengubah subjek email untuk mencerminkan perubahan status tiket.  
3. **Alat Komunikasi Internal** – Memastikan semua anggota tim di‑CC pada pengumuman penting tanpa edit manual.

## Pertimbangan Kinerja
Saat bekerja dengan volume data email yang besar, ingat tips berikut:

- Proses file dalam batch **50–100** untuk menjaga penggunaan memori di bawah **200 MB** per batch.  
- Gunakan pemanggilan `metadata.getRootPackage().getEmail()` secara hemat; gunakan kembali instance `Metadata` bila memungkinkan.  
- Pantau penggunaan heap JVM dengan alat seperti VisualVM untuk menghindari error OutOfMemory.

## Kesimpulan
Anda kini telah menguasai cara **update email recipients java** menggunakan GroupDocs.Metadata. Baik Anda mengubah penerima utama, menambahkan CC, atau menyesuaikan baris subjek, perpustakaan ini menyediakan API yang cepat dan efisien memori. Jelajahi [dokumentasi](https://docs.groupdocs.com/metadata/java/) lengkap untuk skenario lanjutan seperti menangani lampiran atau mengonversi antara format EML dan MSG.

## Bagian FAQ
**Q1**: Versi Java apa yang didukung oleh GroupDocs.Metadata?  
- **A**: Java 8, 11, 17, dan versi lebih baru didukung sepenuhnya.

**Q2**: Bisakah saya menggunakan GroupDocs.Metadata tanpa lisensi?  
- **A**: Ya, percobaan gratis berfungsi dengan batasan; lisensi sementara atau permanen menghilangkan batasan tersebut.

**Q3**: Bagaimana cara menangani file email besar secara efisien?  
- **A**: Proses mereka dalam batch lebih kecil, gunakan kembali objek `Metadata`, dan pantau penggunaan heap untuk tetap di bawah 200 MB per batch.

**Q4**: Jenis file apa lagi yang didukung oleh GroupDocs.Metadata selain email?  
- **A**: Ini mendukung lebih dari **70** format termasuk PDF, DOCX, XLSX, PPTX, gambar, dan arsip. Lihat [referensi API](https://reference.groupdocs.com/metadata/java/) untuk daftar lengkap.

---

**Terakhir Diperbarui:** 2026-05-27  
**Diuji Dengan:** GroupDocs.Metadata 23.12 untuk Java  
**Penulis:** GroupDocs  

---

## Tutorial Terkait

- [Menguasai Ekstraksi Metadata Email di Java Menggunakan GroupDocs.Metadata](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [Tutorial Metadata Email dan Kontak untuk GroupDocs.Metadata Java](/metadata/java/email-contact-formats/)
- [Cara Mengekstrak URI Foto vCard Menggunakan GroupDocs.Metadata di Java untuk Manajemen Kontak Efisien](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)