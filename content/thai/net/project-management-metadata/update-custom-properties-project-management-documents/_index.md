---
title: อัปเดตคุณสมบัติที่กำหนดเองในเอกสารการจัดการโครงการ .NET
linktitle: อัปเดตคุณสมบัติที่กำหนดเองในเอกสารการจัดการโครงการ .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีอัปเดตคุณสมบัติแบบกำหนดเองในเอกสารการจัดการโครงการ .NET โดยใช้ GroupDocs.Metadata สำหรับ .NET ปรับปรุงการจัดการข้อมูลเมตาในแอปพลิเคชันของคุณ
type: docs
weight: 13
url: /th/net/project-management-metadata/update-custom-properties-project-management-documents/
---
## การแนะนำ
ในขอบเขตของการพัฒนา .NET การจัดการเมตาดาต้าของเอกสารอย่างมีประสิทธิภาพถือเป็นสิ่งสำคัญสำหรับแอปพลิเคชันต่างๆ GroupDocs.Metadata สำหรับ .NET มอบโซลูชันที่มีประสิทธิภาพในการโต้ตอบกับข้อมูลเมตาในรูปแบบไฟล์ต่างๆ รวมถึงเอกสารการจัดการโครงการ เช่น ไฟล์ Microsoft Project (MPP) บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการอัปเดตคุณสมบัติแบบกำหนดเองภายในเอกสารการจัดการโครงการ .NET โดยใช้ GroupDocs.Metadata
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอนนี้ ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- สภาพแวดล้อมการพัฒนา: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio หรือ IDE อื่นที่ต้องการสำหรับการพัฒนา .NET บนระบบของคุณ
-  GroupDocs.Metadata สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Metadata สำหรับ .NET จาก[หน้าปล่อย](https://releases.groupdocs.com/metadata/net/).
- ความเข้าใจพื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และแนวคิดกรอบงาน .NET จะเป็นประโยชน์

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณเพื่อใช้ฟังก์ชัน GroupDocs.Metadata:
```csharp
using GroupDocs.Metadata.Formats.Document;
using System;
using GroupDocs.Metadata;
```
## ขั้นตอนที่ 1: โหลดเอกสาร
 ขั้นแรก ให้ยกตัวอย่าง a`Metadata` วัตถุโดยการโหลดเอกสารการจัดการโครงการ (เช่นไฟล์ MPP) โดยใช้เส้นทางไฟล์:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mpp"))
{
    var root = metadata.GetRootPackage<ProjectManagementRootPackage>();
```
## ขั้นตอนที่ 2: ตั้งค่าคุณสมบัติแบบกำหนดเอง
 เข้าถึง`DocumentProperties` จากแพ็คเกจรูทเพื่อตั้งค่าคุณสมบัติแบบกำหนดเอง:
```csharp
    root.DocumentProperties.Set("customProperty1", "some value");
    root.DocumentProperties.Set("customProperty2", 7);
    root.DocumentProperties.Set("customProperty3", true);
```
 แทนที่`"customProperty1"`, `"customProperty2"` , และ`"customProperty3"`ด้วยชื่อคุณสมบัติที่คุณกำหนดเองที่คุณต้องการ คุณสามารถตั้งค่าคุณสมบัติของประเภทต่างๆ ได้ เช่น สตริง, จำนวนเต็ม, บูลีน ฯลฯ
## ขั้นตอนที่ 3: บันทึกการเปลี่ยนแปลง
หลังจากตั้งค่าคุณสมบัติแบบกำหนดเองแล้ว ให้บันทึกข้อมูลเมตาที่แก้ไขกลับไปยังเอกสาร:
```csharp
    metadata.Save("YourOutputFile.mpp");
}
```
 แทนที่`"YourOutputFile.mpp"` ด้วยเส้นทางไฟล์ที่ต้องการเพื่อบันทึกเอกสารการจัดการโครงการที่อัปเดต

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีอัปเดตคุณสมบัติแบบกำหนดเองภายในเอกสารการจัดการโครงการ .NET โดยใช้ GroupDocs.Metadata สำหรับ .NET ด้วยการใช้ประโยชน์จากขั้นตอนเหล่านี้ คุณสามารถจัดการและจัดการข้อมูลเมตาได้อย่างมีประสิทธิภาพ เพิ่มประสิทธิภาพการทำงานและยูทิลิตี้ของแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### GroupDocs.Metadata สำหรับ .NET รองรับรูปแบบไฟล์ใดบ้าง
GroupDocs.Metadata สำหรับ .NET รองรับรูปแบบไฟล์ที่หลากหลาย รวมถึงเอกสาร Microsoft Office, PDF, รูปภาพ, ไฟล์เสียง และอื่นๆ
### ฉันสามารถดึงข้อมูลเมตาที่มีอยู่จากเอกสารโดยใช้ GroupDocs.Metadata สำหรับ .NET ได้หรือไม่
ได้ คุณสามารถแยกและอ่านข้อมูลเมตาจากไฟล์รูปแบบต่างๆ ได้โดยใช้ฟังก์ชันที่ GroupDocs.Metadata สำหรับ .NET มอบให้
### GroupDocs.Metadata สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Metadata สำหรับ .NET เข้ากันได้กับทั้งสภาพแวดล้อม .NET Framework และ .NET Core
### GroupDocs.Metadata สำหรับ .NET รองรับการแก้ไขข้อมูลเมตาในเอกสาร PDF หรือไม่
ใช่ GroupDocs.Metadata สำหรับ .NET ช่วยให้คุณสามารถอัปเดตและจัดการข้อมูลเมตาภายในไฟล์ PDF ได้อย่างราบรื่น
### ฉันจะรับการสนับสนุนด้านเทคนิคหรือความช่วยเหลือเกี่ยวกับ GroupDocs.Metadata สำหรับ .NET ได้ที่ไหน
 สำหรับการสนับสนุนทางเทคนิคและการสนทนาที่เกี่ยวข้องกับ GroupDocs.Metadata สำหรับ .NET โปรดไปที่[ฟอรั่มการสนับสนุน](https://forum.groupdocs.com/c/metadata/14).