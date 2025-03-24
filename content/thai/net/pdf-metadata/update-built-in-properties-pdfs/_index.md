---
title: อัปเดตคุณสมบัติในตัวในรูปแบบ PDF โดยใช้ .NET
linktitle: อัปเดตคุณสมบัติในตัวในรูปแบบ PDF โดยใช้ .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีอัปเดตคุณสมบัติเอกสาร PDF โดยใช้ C# และ GroupDocs.Metadata สำหรับ .NET แก้ไขผู้แต่ง ชื่อเรื่อง คำสำคัญ และอื่นๆ โดยทางโปรแกรม
weight: 15
url: /th/net/pdf-metadata/update-built-in-properties-pdfs/
---

# อัปเดตคุณสมบัติในตัวในรูปแบบ PDF โดยใช้ .NET

## การแนะนำ
ในบทช่วยสอนนี้ เราจะเรียนรู้วิธีใช้ GroupDocs.Metadata สำหรับ .NET เพื่ออัปเดตคุณสมบัติในตัวของเอกสาร PDF ไลบรารีนี้มีชุดเครื่องมือที่มีประสิทธิภาพในการจัดการข้อมูลเมตาภายในรูปแบบเอกสารต่างๆ เราจะอธิบายขั้นตอนที่จำเป็นในการแก้ไขคุณสมบัติ เช่น ผู้แต่ง ชื่อเรื่อง วันที่สร้าง คำสำคัญ ผู้สร้าง และผู้ผลิตในไฟล์ PDF โดยใช้ C#
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
-  GroupDocs.Metadata สำหรับ .NET Library: ดาวน์โหลดไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: ติดตั้ง Visual Studio เพื่อเขียนและรันโค้ด C#
- ความเข้าใจพื้นฐานของ C#: แนะนำให้คุ้นเคยกับภาษาการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ขั้นตอนที่ 1: เริ่มต้นวัตถุข้อมูลเมตา
 เริ่มต้นด้วยการเริ่มต้น a`Metadata`วัตถุที่มีเส้นทางไปยังไฟล์ PDF ของคุณ:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // รหัสของคุณจะไปที่นี่
}
```
## ขั้นตอนที่ 2: เข้าถึงแพ็คเกจรูท PDF
 ถัดไป ให้ดึงข้อมูลแพ็คเกจรูทสำหรับการใช้ PDF โดยเฉพาะ`GetRootPackage<PdfRootPackage>()`-
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## ขั้นตอนที่ 3: อัปเดตคุณสมบัติเอกสาร
 ตอนนี้ อัปเดตคุณสมบัติที่ต้องการของเอกสาร PDF ภายใน`PdfRootPackage`-
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## ขั้นตอนที่ 4: บันทึกการเปลี่ยนแปลง
หลังจากแก้ไขคุณสมบัติแล้ว ให้บันทึกการเปลี่ยนแปลงกลับไปยังไฟล์ PDF:
```csharp
metadata.Save("Your Output File Path");
```
## ขั้นตอนที่ 5: ดึงข้อมูลคุณสมบัติที่อัปเดต
หากต้องการตรวจสอบการเปลี่ยนแปลง ให้โหลดข้อมูลเมตาซ้ำและดึงคุณสมบัติที่อัปเดต:
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

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีใช้ประโยชน์จาก GroupDocs.Metadata สำหรับ .NET เพื่ออัปเดตคุณสมบัติในตัวของเอกสาร PDF โดยทางโปรแกรม ด้วยการทำตามขั้นตอนที่ระบุไว้ คุณสามารถจัดการและแก้ไขข้อมูลเมตาภายในไฟล์ PDF โดยใช้ C# ได้อย่างมีประสิทธิภาพ สำรวจฟีเจอร์และความสามารถเพิ่มเติมที่นำเสนอโดย GroupDocs.Metadata ได้อย่างอิสระเพื่อการจัดการข้อมูลเมตาที่ครอบคลุม

## คำถามที่พบบ่อย
### ถาม: GroupDocs.Metadata สำหรับ .NET คืออะไร
ตอบ: GroupDocs.Metadata สำหรับ .NET เป็นไลบรารีที่ช่วยให้นักพัฒนาสามารถอ่าน แก้ไข ลบ และจัดการข้อมูลเมตาในรูปแบบเอกสารต่างๆ โดยทางโปรแกรม
### ถาม: ฉันจะหาเอกสารสำหรับ GroupDocs.Metadata สำหรับ .NET ได้ที่ไหน
 ตอบ: คุณสามารถเข้าถึงเอกสารได้[ที่นี่](https://tutorials.groupdocs.com/metadata/net/).
### ถาม: ฉันจะดาวน์โหลด GroupDocs.Metadata สำหรับ .NET ได้อย่างไร
 ตอบ: คุณสามารถดาวน์โหลด GroupDocs.Metadata สำหรับ .NET ได้จาก[ลิงค์นี้](https://releases.groupdocs.com/metadata/net/).
### ถาม: มีการทดลองใช้ฟรีหรือไม่?
 ตอบ: ได้ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ถาม: ฉันจะรับการสนับสนุน GroupDocs.Metadata สำหรับ .NET ได้ที่ไหน
 ตอบ: หากต้องการความช่วยเหลือ โปรดไปที่ฟอรัม GroupDocs.Metadata[ที่นี่](https://forum.groupdocs.com/c/metadata/14).