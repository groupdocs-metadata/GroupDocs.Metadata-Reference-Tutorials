---
title: Baca Properti Bawaan dari PDF di .NET
linktitle: Baca Properti Bawaan dari PDF di .NET
second_title: GroupDocs.Metadata .NET API
description: Pelajari cara membaca metadata PDF di .NET menggunakan GroupDocs.Metadata. Akses nama penulis, tanggal pembuatan, subjek, dan lainnya dengan kode C#.
weight: 10
url: /id/net/pdf-metadata/read-built-in-properties-pdfs/
---

# Baca Properti Bawaan dari PDF di .NET

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara memanfaatkan GroupDocs.Metadata untuk .NET untuk membaca properti bawaan dari file PDF. GroupDocs.Metadata adalah perpustakaan canggih yang memungkinkan pengembang bekerja dengan metadata yang terkait dengan berbagai format dokumen, termasuk PDF, dokumen Microsoft Office, gambar, dan banyak lagi. Dengan menggunakan perpustakaan ini, Anda dapat dengan mudah mengakses dan memanipulasi atribut metadata yang tertanam dalam file PDF, seperti nama penulis, tanggal pembuatan, subjek, dan lainnya.
## Prasyarat
Sebelum mendalami tutorial ini, pastikan Anda memiliki prasyarat berikut:
- Visual Studio: Pastikan Anda telah menginstal Visual Studio di mesin Anda.
-  GroupDocs.Metadata untuk .NET: Unduh dan instal GroupDocs.Metadata untuk .NET dari[Di Sini](https://releases.groupdocs.com/metadata/net/).
- Pengetahuan Dasar C#: Keakraban dengan bahasa pemrograman C# dan kerangka .NET.

## Impor Namespace
Mulailah dengan menambahkan namespace yang diperlukan ke proyek C# Anda:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Langkah 1: Muat Metadata PDF
Pertama, muat file PDF dan ekstrak metadatanya menggunakan GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // Akses paket root file PDF
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Ambil dan tampilkan properti bawaan
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // Properti tambahan dapat diakses dengan cara yang sama
    // ...
}
```
Selain membaca metadata, GroupDocs.Metadata memungkinkan operasi lanjutan seperti mengedit, menghapus, atau menambahkan properti metadata baru ke file PDF secara terprogram. Fleksibilitas ini memungkinkan pengelolaan metadata dokumen secara komprehensif dalam aplikasi .NET Anda.
## Kesimpulan
Dalam tutorial ini, kami telah membahas cara memanfaatkan GroupDocs.Metadata untuk .NET untuk mengekstrak properti bawaan dari file PDF menggunakan C#. Dengan mengintegrasikan perpustakaan ini ke dalam proyek Anda, Anda dapat menangani operasi metadata dokumen dengan lancar, memberikan kemampuan manajemen dokumen yang ditingkatkan.

## FAQ
### Bisakah GroupDocs.Metadata berfungsi dengan format dokumen lain?
Ya, GroupDocs.Metadata mendukung berbagai format dokumen seperti DOCX, XLSX, PPTX, PDF, JPG, PNG, dan lainnya.
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Metadata?
Ya, Anda dapat mengakses uji coba gratis GroupDocs.Metadata dari[Di Sini](https://releases.groupdocs.com/).
### Bagaimana cara mengubah properti metadata menggunakan GroupDocs.Metadata?
Anda dapat mengubah properti metadata secara terprogram dengan mengakses paket dokumen terkait dan menetapkan nilai baru.
### Apakah GroupDocs.Metadata mendukung .NET Core?
Ya, GroupDocs.Metadata kompatibel dengan .NET Framework dan .NET Core.
### Di mana saya dapat menemukan dukungan atau mengajukan pertanyaan terkait GroupDocs.Metadata?
 Untuk dukungan dan diskusi, kunjungi[Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).