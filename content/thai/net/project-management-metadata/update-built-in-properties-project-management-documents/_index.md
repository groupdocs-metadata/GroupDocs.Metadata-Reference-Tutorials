---
title: อัปเดตคุณสมบัติในตัวในเอกสารการจัดการโครงการ .NET
linktitle: อัปเดตคุณสมบัติในตัวในเอกสารการจัดการโครงการ .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีอัปเดตข้อมูลเมตาในเอกสารการจัดการโครงการ .NET ด้วย GroupDocs.Metadata สำหรับ .NET เพิ่มประสิทธิภาพการจัดการเอกสารอย่างมีประสิทธิภาพ
weight: 12
url: /th/net/project-management-metadata/update-built-in-properties-project-management-documents/
---

# อัปเดตคุณสมบัติในตัวในเอกสารการจัดการโครงการ .NET

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีอัปเดตคุณสมบัติในตัวภายในเอกสารการจัดการโครงการ .NET โดยใช้ GroupDocs.Metadata สำหรับ .NET ไลบรารีนี้ช่วยให้สามารถจัดการข้อมูลเมตาสำหรับไฟล์รูปแบบต่างๆ ได้อย่างมีประสิทธิภาพ รวมถึงเอกสารการจัดการโครงการ เช่น ไฟล์ Microsoft Project (MPP)
## ข้อกำหนดเบื้องต้น
ก่อนที่จะดำเนินการตามขั้นตอนด้านล่าง ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความเข้าใจพื้นฐานเกี่ยวกับการพัฒนา C# และ .NET
-  GroupDocs.Metadata สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้[ที่นี่](https://releases.groupdocs.com/metadata/net/).
- การเข้าถึงสภาพแวดล้อมการพัฒนา

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ขั้นตอนที่ 1: โหลดข้อมูลเมตาของเอกสาร
 ขั้นแรก ให้ยกตัวอย่าง a`Metadata` วัตถุที่มีเส้นทางไปยังไฟล์อินพุตของคุณ:
```csharp
using (Metadata metadata = new Metadata("YourInputFile"))
{
    var root = metadata.GetRootPackage<ProjectManagementRootPackage>();
    // เข้าถึงคุณสมบัติของเอกสาร
}
```
## ขั้นตอนที่ 2: อัปเดตคุณสมบัติเอกสาร
ตอนนี้ อัพเดตคุณสมบัติในตัวที่ต้องการของเอกสารการจัดการโครงการ:
```csharp
root.DocumentProperties.Author = "test author";
root.DocumentProperties.CreationDate = DateTime.Now;
root.DocumentProperties.Company = "GroupDocs";
root.DocumentProperties.Comments = "test comment";
root.DocumentProperties.Keywords = "metadata, built-in, update";
// เพิ่มคุณสมบัติเพิ่มเติมตามความจำเป็น
```
## ขั้นตอนที่ 3: บันทึกข้อมูลเมตาที่แก้ไข
หลังจากทำการเปลี่ยนแปลงที่จำเป็นแล้ว ให้บันทึกข้อมูลเมตาที่อัปเดตกลับไปยังไฟล์:
```csharp
metadata.Save("YourInputFile");
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีอัปเดตคุณสมบัติในตัวภายในเอกสารการจัดการโครงการโดยใช้ GroupDocs.Metadata สำหรับ .NET ด้วยการใช้ประโยชน์จากไลบรารีนี้ นักพัฒนาสามารถจัดการข้อมูลเมตาได้อย่างมีประสิทธิภาพ เพิ่มความสามารถในการจัดการเอกสารภายในแอปพลิเคชัน .NET

## คำถามที่พบบ่อย
### GroupDocs.Metadata เข้ากันได้กับรูปแบบไฟล์การจัดการโครงการต่างๆ หรือไม่
ใช่ GroupDocs.Metadata รองรับรูปแบบการจัดการโครงการยอดนิยม เช่น ไฟล์ MPP (Microsoft Project)
### ฉันสามารถจัดการคุณสมบัติเมทาดาทาอื่นๆ นอกเหนือจากรายละเอียดเอกสารในตัวได้หรือไม่
อย่างแน่นอน! GroupDocs.Metadata มีความสามารถที่ครอบคลุมในการจัดการข้อมูลเมตาในไฟล์ประเภทต่างๆ มากมาย
### ฉันจะหาเอกสารและการสนับสนุนเพิ่มเติมสำหรับ GroupDocs.Metadata ได้จากที่ไหน
 เยี่ยมชม[เอกสาร GroupDocs.Metadata](https://tutorials.groupdocs.com/metadata/net/) สำหรับข้อมูลโดยละเอียด สำหรับข้อสงสัยเฉพาะเจาะจง มีส่วนร่วมกับชุมชนที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/metadata/14).
### มีการทดลองใช้ฟรีเพื่อทดสอบ GroupDocs.Metadata หรือไม่
 ใช่ คุณสามารถเข้าถึงการทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Metadata ได้อย่างไร
 ได้รับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/).