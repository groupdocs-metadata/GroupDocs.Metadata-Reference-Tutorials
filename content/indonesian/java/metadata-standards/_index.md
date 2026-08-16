---
date: 2026-07-26
description: Panduan langkah demi langkah untuk membaca metadata IPTC menggunakan
  GroupDocs.Metadata untuk Java, serta cara menambahkan XMP, mengekstrak EXIF, dan
  menulis metadata XMP.
keywords:
- read iptc metadata
- how to add xmp
- how to extract exif
- write xmp metadata
- read xmp properties
lastmod: 2026-07-26
og_description: Pelajari cara membaca metadata IPTC dengan GroupDocs.Metadata untuk
  Java. Tutorial ini juga mencakup cara menambahkan XMP, mengekstrak EXIF, dan menulis
  metadata XMP di Java.
og_image_alt: 'Guide: read IPTC metadata using GroupDocs.Metadata Java library'
og_title: Baca Metadata IPTC dengan GroupDocs.Metadata untuk Java – Panduan Lengkap
schemas:
- author: GroupDocs
  dateModified: '2026-07-26'
  description: Step‑by‑step guide to read IPTC metadata using GroupDocs.Metadata for
    Java, plus how to add XMP, extract EXIF, and write XMP metadata.
  headline: Read IPTC Metadata with GroupDocs.Metadata for Java
  type: TechArticle
- description: Step‑by‑step guide to read IPTC metadata using GroupDocs.Metadata for
    Java, plus how to add XMP, extract EXIF, and write XMP metadata.
  name: Read IPTC Metadata with GroupDocs.Metadata for Java
  steps:
  - name: Initialise the Metadata object
    text: The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata.
      Provide the file path and optional load options.
  - name: Access IPTC tags
    text: Call `metadata.getIptc()` to obtain the IPTC handler, then `getAllTags()`
      returns a `Map<String, String>` containing every available IPTC field.
  - name: Process the tags
    text: Iterate over the map, log the values, or store them in your database. You
      can also filter for specific keys such as “Keywords” or “Creator”.
  - name: (Optional) Read EXIF or XMP in the same session
    text: Use `metadata.getExif()` or `metadata.getXmp()` to pull additional metadata
      without reopening the file. This is useful when you need to combine IPTC keywords
      with camera settings.
  type: HowTo
- questions:
  - answer: Yes, GroupDocs.Metadata extracts IPTC embedded in PDF/X‑4 files, returning
      the same tag map as with images.
    question: Can I read IPTC metadata from PDF files?
  - answer: “How to add XMP” focuses on embedding a new XMP package, while “write
      XMP metadata” refers to updating existing XMP properties; both use the same
      API methods.
    question: How does “how to add xmp” differ from “write xmp metadata”?
  - answer: The library extracts EXIF from RAW, JPEG, TIFF, and PSD files; for proprietary
      RAW types, ensure the latest version is installed.
    question: Is “how to extract exif” supported for RAW formats?
  - answer: Yes, `metadata.getXmp().getProperties()` returns a dictionary of all XMP
      key‑value pairs, satisfying the “read xmp properties” requirement.
    question: Does the library support reading XMP properties directly?
  - answer: Version 22.11 or newer includes full EXIF support for Java; earlier releases
      lack some newer camera tags.
    question: What version of GroupDocs.Metadata is required for “extract exif java”?
  type: FAQPage
tags:
- iptc metadata
- groupdocs metadata
- java document processing
- exif extraction
- xmp handling
title: Baca Metadata IPTC dengan GroupDocs.Metadata untuk Java
type: docs
url: /id/java/metadata-standards/
weight: 4
---

# Baca Metadata IPTC dengan GroupDocs.Metadata untuk Java

Jika Anda perlu **membaca metadata IPTC** dari gambar, PDF, atau media lain dalam aplikasi Java, Anda berada di tempat yang tepat. Tutorial ini memandu Anda menggunakan pustaka GroupDocs.Metadata untuk mengekstrak tag IPTC, menunjukkan cara menambahkan paket XMP khusus, dan bahkan memperagakan cara mengambil informasi EXIF bila diperlukan. Pada akhir tutorial, Anda akan memiliki pendekatan yang jelas dan siap produksi yang bekerja pada lebih dari 50 format file dan dapat menangani dokumen ratusan halaman tanpa memuat seluruh file ke memori.

## Jawaban Cepat
- **Apa itu metadata IPTC?** Ini adalah sekumpulan tag standar untuk mendeskripsikan konten gambar, seperti kata kunci, pembuat, dan hak cipta.
- **Pustaka mana yang membaca IPTC di Java?** GroupDocs.Metadata untuk Java menyediakan API sederhana untuk membaca dan menulis IPTC.
- **Apakah saya juga dapat membaca EXIF dan XMP?** Ya – pustaka yang sama mendukung ekstraksi EXIF dan XMP dalam satu panggilan.
- **Apakah saya memerlukan lisensi?** Lisensi sementara dapat digunakan untuk evaluasi; lisensi penuh diperlukan untuk produksi.
- **Versi Java apa yang didukung?** Java 8 sampai 17 sepenuhnya kompatibel.

## Apa itu metadata IPTC yang dibaca?
*Read IPTC metadata* berarti mengambil tag deskriptif standar yang tertanam dalam file gambar. Tag ini memungkinkan manajemen aset yang dapat dicari, kategorisasi otomatis, dan kepatuhan pada alur kerja penerbitan, memungkinkan aplikasi mengindeks, memfilter, dan menampilkan media berdasarkan pembuat, kata kunci, hak cipta, dan properti penting lainnya.

## Mengapa menggunakan GroupDocs.Metadata untuk Java?
GroupDocs.Metadata mendukung **lebih dari 50 format input dan output**—termasuk JPEG, TIFF, PSD, PDF, dan EPUB—dan dapat memproses **dokumen hingga 1 GB** tanpa memuat seluruh file ke RAM. Pustaka ini juga menawarkan operasi **thread‑safe**, streaming berperforma tinggi, dan validasi bawaan standar metadata, menjadikannya ideal untuk pipeline aset digital berskala perusahaan yang memerlukan keandalan dan kecepatan.

## Prasyarat
- Java 8 atau yang lebih baru terpasang.
- Sistem build Maven atau Gradle.
- Pustaka GroupDocs.Metadata untuk Java (tambahkan dependensi Maven yang ditunjukkan dalam dokumentasi resmi).
- File lisensi sementara atau penuh (letakkan di resources proyek Anda).

## Cara membaca metadata IPTC langkah demi langkah
Muat file Anda, dapatkan handler IPTC, dan ambil peta tag—semua dalam alur kerja tiga langkah yang ringkas dan dapat dibungkus dalam metode utilitas untuk penggunaan kembali di seluruh basis kode Anda.

**Jawaban langsung (45 kata):**  
Buat objek `Metadata` untuk file target, panggil `metadata.getIptc().getAllTags()` untuk memperoleh peta nama tag dan nilai, lalu iterasi peta tersebut untuk mencatat, menyimpan, atau memproses lebih lanjut informasi IPTC sesuai kebutuhan.

Kelas `Metadata` adalah titik masuk utama yang memuat file dan menyediakan akses ke bagian‑bagian metadata-nya.

### Langkah 1: Inisialisasi objek Metadata
Kelas `Metadata` adalah titik masuk untuk semua operasi metadata di GroupDocs.Metadata. Berikan jalur file dan opsi pemuatan opsional.

### Langkah 2: Akses tag IPTC
Panggil `metadata.getIptc()` untuk memperoleh handler IPTC, kemudian `getAllTags()` mengembalikan `Map<String, String>` yang berisi setiap bidang IPTC yang tersedia.

### Langkah 3: Proses tag
Iterasi peta, catat nilai, atau simpan ke basis data Anda. Anda juga dapat memfilter kunci tertentu seperti “Keywords” atau “Creator”.

### Langkah 4: (Opsional) Baca EXIF atau XMP dalam sesi yang sama
Gunakan `metadata.getExif()` atau `metadata.getXmp()` untuk mengambil metadata tambahan tanpa membuka kembali file. Ini berguna ketika Anda perlu menggabungkan kata kunci IPTC dengan pengaturan kamera.

## Cara menambahkan metadata XMP ke file?
Menyisipkan paket XMP khusus bersamaan dengan data IPTC yang ada sangat mudah: bangun paket XMP, lampirkan ke objek metadata, dan simpan file. Operasi ini mempertahankan metadata yang ada sambil memperluas file dengan properti baru yang sesuai standar.

**Jawaban langsung (48 kata):**  
Instansiasi `XmpPackage`, isi dengan properti XMP khusus Anda, tambahkan paket ke file melalui `metadata.getXmp().addPackage(xmpPackage)`, dan akhirnya panggil `metadata.save()` untuk menulis perubahan kembali ke disk, memastikan blok XMP baru terintegrasi sepenuhnya.

Kelas `XmpPackage` mewakili kontainer untuk properti XMP khusus yang dapat disisipkan ke dalam file.

## Kesulitan umum dan pemecahan masalah
- **Bagian IPTC hilang:** Beberapa file PNG tidak memiliki IPTC; selalu periksa `metadata.getIptc().isPresent()` sebelum mengakses tag.
- **Gambar besar:** Untuk file lebih dari 200 MB, aktifkan mode streaming melalui `LoadOptions.setUseMemoryCache(true)` untuk menghindari `OutOfMemoryError`. Kelas `LoadOptions` memungkinkan Anda mengkonfigurasi cara file dimuat, seperti mengaktifkan streaming cache memori.
- **Kesalahan lisensi:** Pastikan jalur file lisensi benar; jika tidak, pustaka berjalan dalam mode percobaan dan mungkin membatasi jumlah file yang diproses.

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya membaca metadata IPTC dari file PDF?**  
**J: Ya, GroupDocs.Metadata mengekstrak IPTC yang tertanam dalam file PDF/X‑4, mengembalikan peta tag yang sama seperti pada gambar.**

**T: Bagaimana “cara menambahkan xmp” berbeda dari “menulis metadata xmp”?**  
**J: “Cara menambahkan XMP” berfokus pada penyisipan paket XMP baru, sedangkan “menulis metadata XMP” mengacu pada pembaruan properti XMP yang sudah ada; keduanya menggunakan metode API yang sama.**

**T: Apakah “cara mengekstrak exif” didukung untuk format RAW?**  
**J: Pustaka mengekstrak EXIF dari file RAW, JPEG, TIFF, dan PSD; untuk tipe RAW proprietari, pastikan versi terbaru telah diinstal.**

**T: Apakah pustaka mendukung pembacaan properti XMP secara langsung?**  
**J: Ya, `metadata.getXmp().getProperties()` mengembalikan kamus semua pasangan kunci‑nilai XMP, memenuhi kebutuhan “membaca properti xmp”.**

**T: Versi GroupDocs.Metadata apa yang diperlukan untuk “extract exif java”?**  
**J: Versi 22.11 atau yang lebih baru mencakup dukungan EXIF penuh untuk Java; rilis sebelumnya tidak memiliki beberapa tag kamera terbaru.**

---

**Terakhir Diperbarui:** 2026-07-26  
**Diuji Dengan:** GroupDocs.Metadata untuk Java 23.5  
**Penulis:** GroupDocs  

---  

## Tutorial yang Tersedia

### [Menambahkan Metadata XMP Kustom ke File dengan GroupDocs.Metadata Java&#58; Panduan Komprehensif](./add-custom-xmp-metadata-groupdocs-java/)
Pelajari cara menambahkan paket metadata XMP kustom ke file menggunakan GroupDocs.Metadata untuk Java. Tingkatkan manajemen data file dengan tutorial langkah demi langkah ini.

### [Manajemen Metadata EXIF di Java&#58; Panduan Lengkap Menggunakan GroupDocs.Metadata](./exif-metadata-management-java-groupdocs-metadata/)
Pelajari cara mengelola metadata EXIF secara efisien dalam aplikasi Java menggunakan GroupDocs.Metadata, mencakup penyiapan, pembaruan, dan penyimpanan perubahan.

### [Ekstrak Metadata Dublin Core dari File EPUB Menggunakan GroupDocs.Metadata di Java](./extract-dublin-core-metadata-epub-groupdocs-java/)
Pelajari cara mengekstrak metadata Dublin Core dari file EPUB menggunakan pustaka GroupDocs.Metadata untuk Java. Panduan ini mencakup penyiapan, implementasi, dan aplikasi praktis.

### [Ekstrak Metadata Dublin Core dari Dokumen Word Menggunakan Java dengan GroupDocs.Metadata](./extract-dublin-core-metadata-word-docs-java/)
Pelajari cara mengekstrak metadata Dublin Core dari dokumen Word menggunakan pustaka GroupDocs.Metadata di Java. Ikuti panduan langkah demi langkah ini untuk meningkatkan proses manajemen dokumen Anda.

### [Ekstrak Metadata EXIF dari File PSD Menggunakan GroupDocs.Metadata untuk Java | Panduan Komprehensif](./extract-exif-metadata-psd-groupdocs-java/)
Pelajari cara mengekstrak metadata EXIF dari file PSD menggunakan GroupDocs.Metadata untuk Java. Panduan ini mencakup teknik ekstraksi metadata dasar dan lanjutan.

### [Ekstrak Tag Perangkat Lunak EXIF di Java&#58; Panduan Lengkap Menggunakan GroupDocs.Metadata](./master-exif-data-java-groupdocs-metadata/)
Pelajari cara mengekstrak tag perangkat lunak dari data EXIF gambar menggunakan GroupDocs.Metadata untuk Java. Tingkatkan manajemen aset digital dan pengalaman pengguna.

### [Ekstrak Metadata XMP Menggunakan GroupDocs.Metadata untuk Java&#58; Panduan Komprehensif](./extract-xmp-metadata-groupdocs-metadata-java/)
Pelajari cara mengekstrak dan mengelola metadata XMP di Java dengan GroupDocs.Metadata. Panduan ini mencakup metadata dasar, Dublin Core, dan spesifik Photoshop.

### [Cara Mengekstrak Metadata Dublin Core Menggunakan GroupDocs.Metadata untuk Java&#58; Panduan Lengkap](./extract-dublin-core-metadata-groupdocs-java/)
Pelajari cara mengekstrak dan mengelola metadata Dublin Core di Java menggunakan GroupDocs.Metadata. Panduan ini mencakup penyiapan, implementasi, dan aplikasi praktis.

### [Cara Mengekstrak Metadata EXIF dari Gambar TIFF Menggunakan GroupDocs.Metadata di Java](./extract-exif-metadata-groupdocs-java-tiff/)
Pelajari cara mengekstrak dan mengelola metadata EXIF dari file TIFF menggunakan GroupDocs.Metadata untuk Java. Tingkatkan aplikasi manajemen aset digital Anda dengan informasi gambar yang detail.

### [Cara Mengekstrak Metadata IPTC dari Gambar TIFF Menggunakan GroupDocs.Metadata untuk Java](./extract-iptc-metadata-tiff-groupdocs-java/)
Pelajari cara mengekstrak metadata IPTC dari gambar TIFF secara efisien menggunakan GroupDocs.Metadata untuk Java. Sederhanakan manajemen data gambar Anda dengan panduan langkah demi langkah ini.

### [Cara Membaca dan Mengelola Metadata DICOM di Java Menggunakan GroupDocs.Metadata](./master-dicom-metadata-groupdocs-metadata-java/)
Pelajari cara mengekstrak dan mengelola metadata DICOM secara efisien dalam aplikasi Java Anda menggunakan pustaka GroupDocs.Metadata yang kuat.

### [Cara Membaca dan Mengelola Metadata EXIF di Java Menggunakan GroupDocs.Metadata](./read-exif-metadata-groupdocs-java/)
Pelajari cara mengekstrak dan memanfaatkan metadata EXIF dari gambar menggunakan GroupDocs.Metadata untuk Java. Panduan ini mencakup penyiapan, pembacaan tag, dan aplikasi praktis.

### [Cara Menghapus Metadata EXIF dari JPEG Menggunakan GroupDocs.Metadata untuk Java&#58; Panduan Komprehensif](./remove-exif-metadata-jpeg-groupdocs-java/)
Pelajari cara menghapus metadata EXIF sensitif dari file JPEG menggunakan GroupDocs.Metadata untuk Java. Tingkatkan privasi dan optimalkan gambar Anda dengan panduan langkah demi langkah ini.

### [Cara Menetapkan Metadata IPTC dengan GroupDocs.Metadata di Java&#58; Panduan Lengkap](./set-iptc-metadata-groupdocs-java-guide/)
Pelajari cara mengelola dan menetapkan metadata IPTC yang hilang secara efisien menggunakan GroupDocs.Metadata untuk Java. Tingkatkan aplikasi manajemen gambar Anda hari ini.

### [Penanganan Metadata Java dengan GroupDocs&#58; Tambah & Ambil Kata Kunci IPTC untuk Manajemen Aset Digital](./java-metadata-groupdocs-add-retrieve-iptc-keywords/)
Pelajari cara menambahkan dan mengambil kata kunci IPTC secara efisien menggunakan GroupDocs.Metadata di Java, meningkatkan manajemen aset digital.

### [Menguasai GroupDocs.Metadata Java&#58; Ekstrak Metadata IPTC dari JPEG dengan Mudah](./reading-iptc-metadata-jpeg-groupdocs-metadata-java/)
Pelajari cara mengekstrak metadata IPTC dari file JPEG menggunakan GroupDocs.Metadata untuk Java. Panduan langkah demi langkah untuk mengelola aset digital secara efisien.

### [Menguasai Manajemen Metadata IPTC Java dengan GroupDocs.Metadata untuk Java](./java-iptc-metadata-groupdocs-metadata/)
Pelajari cara mengelola dan menyesuaikan metadata IPTC dalam aplikasi Java menggunakan GroupDocs.Metadata. Tingkatkan organisasi dokumen, kemampuan pencarian, dan manajemen aset.

### [Baca Metadata IPTC di Java Menggunakan Pustaka GroupDocs.Metadata](./groupdocs-metadata-java-read-iptc-datasets/)
Pelajari cara membaca dan mengelola metadata IPTC dalam gambar menggunakan pustaka GroupDocs.Metadata di Java. Temukan instruksi langkah demi langkah, praktik terbaik, dan aplikasi praktis.

## Sumber Daya Tambahan

- [Dokumentasi GroupDocs.Metadata untuk Java](https://docs.groupdocs.com/metadata/java/)
- [Referensi API GroupDocs.Metadata untuk Java](https://reference.groupdocs.com/metadata/java/)
- [Unduh GroupDocs.Metadata untuk Java](https://releases.groupdocs.com/metadata/java/)
- [Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata)
- [Dukungan Gratis](https://forum.groupdocs.com/)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

## Tutorial Terkait

- [Penanganan Metadata Java dengan GroupDocs&#58; Tambah & Ambil Kata Kunci IPTC untuk Manajemen Aset Digital](/metadata/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/)
- [Ekstrak Metadata XMP Menggunakan GroupDocs.Metadata untuk Java&#58; Panduan Komprehensif](/metadata/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/)
- [Ekstrak Metadata EXIF dari File PSD Menggunakan GroupDocs.Metadata untuk Java | Panduan Komprehensif](/metadata/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/)