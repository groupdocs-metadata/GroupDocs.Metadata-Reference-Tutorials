---
title: Perbarui Properti Bawaan dalam PDF menggunakan .NET
linktitle: Perbarui Properti Bawaan dalam PDF menggunakan .NET
second_title: GroupDocs.Metadata .NET API
description: Pelajari cara memperbarui properti dokumen PDF menggunakan C# dan GroupDocs.Metadata untuk .NET. Ubah penulis, judul, kata kunci, dan lainnya secara terprogram.
weight: 15
url: /id/net/pdf-metadata/update-built-in-properties-pdfs/
type: docs
---
# Perbarui Properti Bawaan dalam PDF menggunakan .NET

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggunakan GroupDocs.Metadata untuk .NET untuk memperbarui properti bawaan dokumen PDF. Pustaka ini menyediakan seperangkat alat canggih untuk memanipulasi metadata dalam berbagai format dokumen. Kami akan memandu langkah-langkah yang diperlukan untuk mengubah properti seperti penulis, judul, tanggal pembuatan, kata kunci, pembuat, dan produser dalam file PDF menggunakan C#.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki hal berikut:
-  GroupDocs.Metadata untuk .NET Library: Unduh perpustakaan dari[Di Sini](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: Instal Visual Studio untuk menulis dan mengeksekusi kode C#.
- Pemahaman Dasar C#: Disarankan untuk menguasai bahasa pemrograman C#.

## Impor Namespace
Mulailah dengan memasukkan namespace yang diperlukan dalam proyek C# Anda:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Langkah 1: Inisialisasi Objek Metadata
 Mulailah dengan inisialisasi a`Metadata`objek dengan jalur ke file PDF Anda:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Kode Anda akan ditempatkan di sini
}
```
## Langkah 2: Akses Paket Root PDF
 Selanjutnya, ambil paket root khusus untuk PDF menggunakan`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Langkah 3: Perbarui Properti Dokumen
 Sekarang, perbarui properti dokumen PDF yang diinginkan di dalam`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Langkah 4: Simpan Perubahan
Setelah memodifikasi properti, simpan perubahan kembali ke file PDF:
```csharp
metadata.Save("Your Output File Path");
```
## Langkah 5: Ambil Properti yang Diperbarui
Untuk memverifikasi perubahan, muat ulang metadata dan ambil properti yang diperbarui:
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## Kesimpulan
Dalam tutorial ini, kita mempelajari cara memanfaatkan GroupDocs.Metadata untuk .NET untuk memperbarui properti bawaan dokumen PDF secara terprogram. Dengan mengikuti langkah-langkah yang diuraikan, Anda dapat mengelola dan mengubah metadata dalam file PDF secara efisien menggunakan C#. Jangan ragu untuk menjelajahi lebih banyak fitur dan kemampuan yang ditawarkan oleh GroupDocs.Metadata untuk manipulasi metadata yang komprehensif.

## FAQ
### T: Apa itu GroupDocs.Metadata untuk .NET?
J: GroupDocs.Metadata for .NET adalah perpustakaan yang memungkinkan pengembang membaca, mengedit, menghapus, dan memanipulasi metadata dalam berbagai format dokumen secara terprogram.
### T: Di mana saya dapat menemukan dokumentasi GroupDocs.Metadata untuk .NET?
 J: Anda dapat mengakses dokumentasinya[Di Sini](https://tutorials.groupdocs.com/metadata/net/).
### T: Bagaimana cara mengunduh GroupDocs.Metadata untuk .NET?
 J: Anda dapat mengunduh GroupDocs.Metadata untuk .NET dari[Link ini](https://releases.groupdocs.com/metadata/net/).
### T: Apakah tersedia uji coba gratis?
 A: Ya, Anda bisa mendapatkan versi uji coba gratis[Di Sini](https://releases.groupdocs.com/).
### T: Di mana saya bisa mendapatkan dukungan untuk GroupDocs.Metadata untuk .NET?
 J: Untuk dukungan, kunjungi forum GroupDocs.Metadata[Di Sini](https://forum.groupdocs.com/c/metadata/14).