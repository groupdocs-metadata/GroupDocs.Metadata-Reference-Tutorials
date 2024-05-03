---
title: อัปเดตคุณสมบัติในตัวในสเปรดชีตโดยใช้ .NET
linktitle: อัปเดตคุณสมบัติในตัวในสเปรดชีตโดยใช้ .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีอัปเดตคุณสมบัติเมทาดาทาในตัวในไฟล์ Excel โดยใช้ GroupDocs.Metadata สำหรับ .NET แก้ไขผู้เขียน เวลาในการสร้าง บริษัท และอื่นๆ ด้วย C#
type: docs
weight: 14
url: /th/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีใช้ GroupDocs.Metadata สำหรับ .NET เพื่ออัปเดตคุณสมบัติในตัวในไฟล์สเปรดชีตโดยใช้ C# GroupDocs.Metadata เป็น API อันทรงพลังที่ช่วยให้นักพัฒนาสามารถอ่าน แก้ไข และลบคุณสมบัติของข้อมูลเมตาออกจากไฟล์รูปแบบต่างๆ รวมถึงสเปรดชีต เราจะมุ่งเน้นที่การปรับเปลี่ยนคุณสมบัติ เช่น ผู้เขียน เวลาในการสร้าง บริษัท หมวดหมู่ และคำสำคัญภายในไฟล์ Excel โดยเฉพาะ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio เวอร์ชันล่าสุด
-  GroupDocs.Metadata สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Metadata สำหรับ .NET จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/metadata/net/).
- ความรู้พื้นฐาน C#: ความเข้าใจภาษาการเขียนโปรแกรม C# และกรอบงาน .NET

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ขั้นตอนที่ 1: โหลดไฟล์สเปรดชีต
 ขั้นแรก ให้เริ่มต้น a`Metadata` วัตถุโดยการโหลดไฟล์สเปรดชีตอินพุต:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // เข้าถึงคุณสมบัติของเอกสารภายในรูท
}
```
## ขั้นตอนที่ 2: อัปเดตคุณสมบัติในตัว
 เข้าถึงคุณสมบัติเอกสารในตัวผ่านทาง`SpreadsheetRootPackage` และแก้ไขตามความจำเป็น:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
ตรวจสอบให้แน่ใจว่าได้เปลี่ยนตัวยึดตำแหน่ง (`YourAuthorName`, `YourCompany`, `YourCategory`ด้วยค่าจริงที่คุณต้องการตั้งค่าสำหรับคุณสมบัติ
## ขั้นตอนที่ 3: บันทึกการเปลี่ยนแปลง
หลังจากอัปเดตคุณสมบัติแล้ว ให้บันทึกการเปลี่ยนแปลงกลับไปยังไฟล์สเปรดชีต:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สาธิตวิธีใช้ GroupDocs.Metadata สำหรับ .NET เพื่ออัปเดตคุณสมบัติในตัวของไฟล์สเปรดชีตโดยทางโปรแกรม ด้วยการใช้ประโยชน์จาก API นี้ นักพัฒนาสามารถจัดการข้อมูลเมตาภายในเอกสาร Excel ได้อย่างมีประสิทธิภาพ เพิ่มประสิทธิภาพการจัดระเบียบข้อมูลและการเข้าถึง

## คำถามที่พบบ่อย
### GroupDocs.Metadata รองรับไฟล์รูปแบบใดบ้าง
GroupDocs.Metadata รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึงเอกสาร Microsoft Office, PDF, รูปภาพ, ไฟล์เสียง และอื่นๆ
### ฉันสามารถเรียกคุณสมบัติเมทาดาทาที่มีอยู่จากไฟล์ได้หรือไม่
ได้ คุณสามารถแยกและอ่านคุณสมบัติเมตาดาต้า เช่น ผู้เขียน วันที่สร้าง คำสำคัญ และคุณสมบัติที่กำหนดเองได้โดยใช้ GroupDocs.Metadata
### GroupDocs.Metadata เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Metadata เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### GroupDocs.Metadata ให้ทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถดาวน์โหลด GroupDocs.Metadata รุ่นทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Metadata ได้ที่ไหน
 สำหรับการสนับสนุนและการสนทนาโปรดไปที่[ฟอรัม GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).