---
date: '2026-06-22'
description: Pelajari cara mengekstrak tanda tangan font OpenType dan detail tanda
  tangan digital dari font OpenType menggunakan GroupDocs.Metadata untuk Java. Panduan
  ini membantu mengamankan dokumen Anda.
keywords:
- extract opentype font signature
- groupdocs metadata java
- digital signature flags opentype
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  headline: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract OpenType font signature and digital signature
    details from OpenType fonts using GroupDocs.Metadata for Java. This guide helps
    secure your documents.
  name: How to Extract OpenType Font Signature in Java Using GroupDocs.Metadata
  steps:
  - name: Initialize the `Metadata` instance pointing to your font file.
    text: Initialize the `Metadata` instance pointing to your font file.
  - name: Retrieve the `DigitalSignaturePackage`.
    text: Retrieve the `DigitalSignaturePackage`.
  - name: Print or log the flag values.
    text: Print or log the flag values.
  - name: Re‑use the same `Metadata` initialization as above.
    text: Re‑use the same `Metadata` initialization as above.
  - name: Loop through each `CmsSignature` in the package.
    text: Loop through each `CmsSignature` in the package.
  - name: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
    text: Extract properties such as `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`,
      and `getSignerInfo()`.
  - name: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
    text: '**Document Verification:** Automate checks for signed font files in a content‑management
      system.'
  - name: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
    text: '**Digital Asset Management:** Validate font authenticity before deploying
      them in branding projects.'
  - name: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
    text: '**Security Audits:** Review signature details to ensure compliance with
      internal security policies.'
  type: HowTo
- questions:
  - answer: '`DigitalSignaturePackage` will be `null`; always check for this condition
      before accessing flags or details.'
    question: Can I extract signatures from a font that has no digital signature?
  - answer: The examples target version **24.12**, but newer releases remain backward
      compatible for OpenType fonts.
    question: Which version of GroupDocs.Metadata is required?
  - answer: A trial license works for evaluation; a full license is required for production
      use.
    question: Do I need a special license to read signatures?
  - answer: Download the font to a temporary local file, then pass its path to `Metadata`.
      The library works with any file accessible via a local path.
    question: How do I handle fonts stored in a cloud bucket?
  - answer: GroupDocs.Metadata supplies raw signature data; you can feed the certificate
      chain and hash values into a separate crypto library to perform full verification.
    question: Is it possible to verify the signature’s cryptographic validity?
  type: FAQPage
title: Cara Mengekstrak Tanda Tangan Font OpenType di Java Menggunakan GroupDocs.Metadata
type: docs
url: /id/java/document-formats/extract-digital-signatures-opentype-fonts-java/
weight: 1
---

# Cara Mengekstrak Tanda Tangan Font OpenType di Java dengan GroupDocs.Metadata

Dalam aplikasi modern, **mengekstrak tanda tangan font OpenType** penting untuk memastikan keaslian font dan melindungi aset digital Anda. Tutorial ini menunjukkan, langkah demi langkah, cara mengambil baik flag tanda tangan maupun detail kriptografi lengkap dari font OpenType menggunakan **GroupDocs.Metadata untuk Java**. Baik Anda membangun pipeline konten yang berfokus pada keamanan atau hanya perlu mengaudit perpustakaan font, teknik di bawah ini akan membuat alur kerja Anda dapat diandalkan dan cepat.

## Jawaban Cepat
- **Apa pustaka yang saya perlukan?** GroupDocs.Metadata untuk Java (v24.12)  
- **Versi Java mana yang diperlukan?** JDK 8 atau lebih baru  
- **Apakah saya memerlukan lisensi?** Trial gratis dapat digunakan untuk evaluasi; lisensi penuh diperlukan untuk produksi  
- **Bisakah saya memproses beberapa font?** Ya – pemrosesan batch atau bersamaan didukung  
- **Apakah kode ini thread‑safe?** Buat instance `Metadata` baru per thread; objeknya sendiri tidak thread‑safe  

## Apa itu Tanda Tangan Font OpenType?
**Tanda tangan font OpenType** adalah blok kriptografi yang disematkan di dalam font yang membuktikan file tidak diubah sejak ditandatangani. Ia berisi waktu penandatanganan, rantai sertifikat, pengidentifikasi algoritma hash, dan informasi pencabutan opsional. Ia juga mencakup pengidentifikasi algoritma tanda tangan, rantai sertifikat penandatangan, serta daftar pencabutan opsional, memungkinkan verifikasi menyeluruh atas integritas dan asal font.

## Mengapa Menggunakan GroupDocs.Metadata untuk Java?
GroupDocs.Metadata mendukung **lebih dari 50 format input dan output** (termasuk DOCX, PDF, PPTX, HTML, dan berbagai tipe gambar) dan dapat membaca tanda tangan OpenType tanpa memuat seluruh file ke memori, memungkinkan Anda memproses koleksi font ratusan halaman secara efisien.

## Prasyarat
- **Java Development Kit (JDK):** Versi 8 atau lebih baru.  
- **IDE:** IDE yang kompatibel dengan Java apa pun (IntelliJ IDEA, Eclipse, VS Code, dll.).  
- **Maven:** Untuk manajemen dependensi.  

### Pustaka dan Dependensi yang Diperlukan
Tambahkan koordinat Maven GroupDocs.Metadata ke `pom.xml` Anda. Ini akan menarik paket yang tepat untuk contoh-contoh.

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

### Akuisisi Lisensi
- **Trial Gratis:** Mulai dengan trial gratis untuk menjelajahi fitur.  
- **Lisensi Sementara:** Dapatkan lisensi sementara melalui [halaman lisensi GroupDocs](https://purchase.groupdocs.com/temporary-license).  
- **Pembelian:** Untuk penggunaan produksi, beli lisensi penuh.

## Cara Mengekstrak Tanda Tangan Font OpenType Menggunakan GroupDocs.Metadata
Kelas `Metadata` adalah API inti GroupDocs.Metadata untuk mengakses metadata dokumen tanpa memuat seluruh file.  
Untuk membaca tanda tangan font, buat objek `Metadata` dengan path ke file .otf lalu akses `DigitalSignaturePackage`‑nya. Pendekatan ini memuat hanya struktur metadata yang diperlukan, menghindari parsing penuh font dan menjaga penggunaan memori tetap rendah. Instance `Metadata` sebaiknya digunakan dalam blok try‑with‑resources untuk memastikan pembuangan yang tepat.

Muat file font Anda dengan `new Metadata("font.otf")` di dalam blok try‑with‑resources. Kelas `Metadata` adalah titik masuk GroupDocs.Metadata untuk membaca tipe dokumen yang didukung, termasuk font OpenType. Objek ini otomatis menutup, mencegah kebocoran sumber daya.

### Cara Mengekstrak Flag Tanda Tangan Digital
Objek `DigitalSignaturePackage` mengumpulkan semua informasi terkait tanda tangan untuk font, termasuk flag dan tanda tangan individu.  
**Jawaban langsung:** Panggil `metadata.getDigitalSignaturePackage().getFlags()` setelah membuka font; set flag yang dikembalikan memberi tahu Anda apakah tanda tangan valid, dicabut, atau memiliki kondisi khusus. Panggilan tunggal ini memberi pemeriksaan cepat sebelum Anda menyelami detail lebih dalam. Flag direpresentasikan sebagai enumerasi yang dapat diperiksa untuk menentukan status penandatanganan, keberadaan timestamp, dan kebijakan apa pun yang diterapkan saat penandatanganan.

1. Inisialisasi instance `Metadata` yang menunjuk ke file font Anda.  
2. Dapatkan `DigitalSignaturePackage`.  
3. Cetak atau log nilai flag.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        System.out.println(root.getDigitalSignaturePackage().getFlags());
    }
}
```

**Penjelasan**  
- `documentPath` – path absolut atau relatif ke font OpenType.  
- Blok try‑with‑resources menjamin objek `Metadata` ditutup secara otomatis, menghindari kebocoran memori.

### Cara Mengekstrak Informasi Tanda Tangan Digital Detail
`CmsSignature` mewakili tanda tangan CMS/PKCS#7 individual yang disematkan dalam font, menyediakan akses ke properti kriptografinya.  
**Jawaban langsung:** Iterasi melalui `metadata.getDigitalSignaturePackage().getSignatures()`; setiap objek `CmsSignature` menampilkan waktu penandatanganan, algoritma digest, konten terenkapsulasi, dan detail sertifikat, memungkinkan Anda membangun laporan audit lengkap. Untuk setiap tanda tangan Anda dapat mengambil rantai sertifikat penandatangan, memverifikasi algoritma hash, dan mengekstrak token timestamp untuk mengonfirmasi kapan tanda tangan diterapkan.

1. Gunakan kembali inisialisasi `Metadata` yang sama seperti di atas.  
2. Loop melalui setiap `CmsSignature` dalam paket.  
3. Ekstrak properti seperti `getSignTime()`, `getDigestAlgorithms()`, `getCertificates()`, dan `getSignerInfo()`.

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY"; // Replace with your input file path
try (Metadata metadata = new Metadata(documentPath)) {
    OpenTypeRootPackage root = metadata.getRootPackageGeneric();
    
    if (root.getDigitalSignaturePackage() != null) {
        for (CmsSignature signature : root.getDigitalSignaturePackage().getSignatures()) {
            System.out.println(signature.getSignTime());
            
            if (signature.getDigestAlgorithms() != null) {
                for (com.groupdocs.metadata.core.Oid signatureDigestAlgorithm : signature.getDigestAlgorithms()) {
                    printOid(signatureDigestAlgorithm);
                }
            }

            if (signature.getEncapsulatedContent() != null) {
                System.out.println(signature.getEncapsulatedContent().getContentType());
                System.out.println(signature.getEncapsulatedContent().getContentRawData().length);
            }

            if (signature.getCertificates() != null) {
                for (com.groupdocs.metadata.core.CmsCertificate certificate : signature.getCertificates()) {
                    System.out.println(certificate.getNotAfter());
                    System.out.println(certificate.getNotBefore());
                    System.out.println(certificate.getRawData().length);
                }
            }

            if (signature.getSigners() != null) {
                for (com.groupdocs.metadata.core.CmsSigner signerInfoEntry : signature.getSigners()) {
                    System.out.println(signerInfoEntry.getSignatureValue());
                    printOid(signerInfoEntry.getDigestAlgorithm());
                    printOid(signerInfoEntry.getSignatureAlgorithm());
                    System.out.println(signerInfoEntry.getSigningTime());
                }
            }
        }
    }
}
```

**Penjelasan Bagian Kunci**  
- **Waktu Tanda Tangan:** Stempel waktu saat tanda tangan diterapkan.  
- **Algoritma Digest & OID:** Algoritma hashing yang digunakan (mis., SHA‑256).  
- **Konten Terkapsul:** Data tambahan apa pun yang dibungkus di dalam tanda tangan.  
- **Sertifikat:** Tanggal berlaku dan ukuran data mentah membantu memverifikasi identitas penandatangan.  
- **Penandatangan:** Menyediakan pilihan algoritma masing‑masing penandatangan dan stempel waktu penandatanganan.

#### Tips Pemecahan Masalah
- Jika font tidak memiliki tanda tangan digital, `getDigitalSignaturePackage()` mengembalikan `null`. Selalu periksa `null` sebelum mengakses flag atau tanda tangan.  
- Pastikan Anda menggunakan versi **GroupDocs.Metadata** yang sama seperti yang didefinisikan dalam dependensi Maven untuk menghindari masalah kompatibilitas.  

## Aplikasi Praktis
Mengekstrak tanda tangan font OpenType berguna dalam banyak skenario dunia nyata:

1. **Verifikasi Dokumen:** Otomatiskan pemeriksaan file font yang ditandatangani dalam sistem manajemen konten.  
2. **Manajemen Aset Digital:** Validasi keaslian font sebelum menyebarkannya dalam proyek branding.  
3. **Audit Keamanan:** Tinjau detail tanda tangan untuk memastikan kepatuhan terhadap kebijakan keamanan internal.  

## Pertimbangan Kinerja
- **Manajemen Sumber Daya:** Gunakan try‑with‑resources untuk menutup objek `Metadata` dengan cepat.  
- **Pemrosesan Batch:** Proses font dalam grup untuk meminimalkan overhead I/O; GroupDocs.Metadata dapat menangani ribuan file tanpa memuat setiap font secara keseluruhan ke memori.  
- **Konkruensi:** Jalankan instance `Metadata` terpisah pada thread paralel untuk beban kerja skala besar; pustaka tidak thread‑safe per instance, jadi isolasi setiap instance per thread.  

## Pertanyaan yang Sering Diajukan

**T: Bisakah saya mengekstrak tanda tangan dari font yang tidak memiliki tanda tangan digital?**  
J: `DigitalSignaturePackage` akan `null`; selalu periksa kondisi ini sebelum mengakses flag atau detail.

**T: Versi GroupDocs.Metadata mana yang diperlukan?**  
J: Contoh menargetkan versi **24.12**, tetapi rilis yang lebih baru tetap kompatibel mundur untuk font OpenType.

**T: Apakah saya memerlukan lisensi khusus untuk membaca tanda tangan?**  
J: Lisensi trial dapat digunakan untuk evaluasi; lisensi penuh diperlukan untuk penggunaan produksi.

**T: Bagaimana cara menangani font yang disimpan di bucket cloud?**  
J: Unduh font ke file lokal sementara, lalu berikan path-nya ke `Metadata`. Pustaka bekerja dengan file apa pun yang dapat diakses melalui path lokal.

**T: Apakah memungkinkan untuk memverifikasi validitas kriptografis tanda tangan?**  
J: GroupDocs.Metadata menyediakan data tanda tangan mentah; Anda dapat memasukkan rantai sertifikat dan nilai hash ke pustaka kripto terpisah untuk melakukan verifikasi penuh.

## Kesimpulan
Dengan mengikuti panduan ini, Anda kini tahu **cara mengekstrak informasi tanda tangan font OpenType** dan data tanda tangan digital detail menggunakan **GroupDocs.Metadata untuk Java**. Mengintegrasikan langkah‑langkah ini ke dalam aplikasi Anda memperkuat keamanan dokumen, menyederhanakan validasi aset, dan mendukung inisiatif kepatuhan.

**Langkah Selanjutnya**  
- Bereksperimen dengan pemrosesan batch untuk menangani perpustakaan font besar secara efisien.  
- Gabungkan data yang diekstrak dengan alat audit keamanan Anda untuk pelaporan kepatuhan otomatis.  
- Jelajahi kemampuan metadata lain dari GroupDocs.Metadata, seperti mengedit atau menghapus tanda tangan bila diperlukan.

---

**Last Updated:** 2026-06-22  
**Tested With:** GroupDocs.Metadata 24.12  
**Author:** GroupDocs

## Tutorial Terkait

- [Akses Metadata Dokumen Word dengan GroupDocs di Java: Panduan Komprehensif](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [Cara Mengekstrak Metadata Kustom dari PDF Menggunakan GroupDocs.Metadata di Java: Panduan Komprehensif](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)