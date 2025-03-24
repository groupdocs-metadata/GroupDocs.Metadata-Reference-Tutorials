---
title: อ่านคุณสมบัติในตัวจาก PDF ใน .NET
linktitle: อ่านคุณสมบัติในตัวจาก PDF ใน .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีอ่านข้อมูลเมตา PDF ใน .NET โดยใช้ GroupDocs.Metadata เข้าถึงชื่อผู้แต่ง วันที่สร้าง หัวข้อ และอื่นๆ ด้วยรหัส C#
weight: 10
url: /th/net/pdf-metadata/read-built-in-properties-pdfs/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ประโยชน์จาก GroupDocs.Metadata สำหรับ .NET เพื่ออ่านคุณสมบัติในตัวจากไฟล์ PDF GroupDocs.Metadata เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถทำงานกับเมตาดาต้าที่เกี่ยวข้องกับรูปแบบเอกสารต่างๆ รวมถึง PDF, เอกสาร Microsoft Office, รูปภาพ และอื่นๆ ด้วยการใช้ไลบรารีนี้ คุณสามารถเข้าถึงและจัดการแอตทริบิวต์ข้อมูลเมตาที่ฝังอยู่ในไฟล์ PDF เช่น ชื่อผู้แต่ง วันที่สร้าง หัวข้อ และอื่นๆ ได้อย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
-  GroupDocs.Metadata สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Metadata สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/metadata/net/).
- ความรู้พื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และกรอบงาน .NET

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการเพิ่มเนมสเปซที่จำเป็นให้กับโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ขั้นตอนที่ 1: โหลดข้อมูลเมตา PDF
ขั้นแรก ให้โหลดไฟล์ PDF และแยกข้อมูลเมตาโดยใช้ GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // เข้าถึงแพ็คเกจรูทของไฟล์ PDF
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // ดึงข้อมูลและแสดงคุณสมบัติในตัว
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // สามารถเข้าถึงคุณสมบัติเพิ่มเติมได้ในทำนองเดียวกัน
    // -
}
```
นอกเหนือจากการอ่านเมตาดาต้าแล้ว GroupDocs.Metadata ยังช่วยให้ดำเนินการขั้นสูง เช่น การแก้ไข การลบ หรือการเพิ่มคุณสมบัติเมทาดาทาใหม่ลงในไฟล์ PDF โดยทางโปรแกรม ความยืดหยุ่นนี้ช่วยให้สามารถจัดการข้อมูลเมตาของเอกสารภายในแอปพลิเคชัน .NET ของคุณได้อย่างครอบคลุม
## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการใช้ GroupDocs.Metadata สำหรับ .NET เพื่อแยกคุณสมบัติในตัวจากไฟล์ PDF โดยใช้ C# ด้วยการรวมไลบรารีนี้เข้ากับโปรเจ็กต์ของคุณ คุณสามารถจัดการการดำเนินการเมตาดาต้าของเอกสารได้อย่างราบรื่น โดยให้ความสามารถในการจัดการเอกสารที่ได้รับการปรับปรุง

## คำถามที่พบบ่อย
### GroupDocs.Metadata สามารถทำงานร่วมกับรูปแบบเอกสารอื่นได้หรือไม่
ใช่ GroupDocs.Metadata รองรับรูปแบบเอกสารที่หลากหลาย เช่น DOCX, XLSX, PPTX, PDF, JPG, PNG และอื่นๆ
### GroupDocs.Metadata มีการทดลองใช้ฟรีหรือไม่
ใช่ คุณสามารถเข้าถึง GroupDocs.Metadata รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะแก้ไขคุณสมบัติเมทาดาทาโดยใช้ GroupDocs.Metadata ได้อย่างไร
คุณสามารถแก้ไขคุณสมบัติเมทาดาทาโดยทางโปรแกรมโดยการเข้าถึงแพ็คเกจเอกสารที่เกี่ยวข้องและตั้งค่าใหม่
### GroupDocs.Metadata รองรับ .NET Core หรือไม่
ใช่ GroupDocs.Metadata เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันจะรับการสนับสนุนหรือถามคำถามที่เกี่ยวข้องกับ GroupDocs.Metadata ได้ที่ไหน
 สำหรับการสนับสนุนและการสนทนาโปรดไปที่[ฟอรัม GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).