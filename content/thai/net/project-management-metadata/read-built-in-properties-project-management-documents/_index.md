---
title: อ่านคุณสมบัติในตัวในเอกสารการจัดการโครงการ .NET
linktitle: อ่านคุณสมบัติในตัวในเอกสารการจัดการโครงการ .NET
second_title: GroupDocs.Metadata .NET API
description: เรียนรู้วิธีดึงข้อมูลเมตาจากเอกสารการจัดการโครงการโดยใช้ GroupDocs.Metadata สำหรับ .NET เพิ่มความสามารถในการประมวลผลเอกสารของคุณ
weight: 10
url: /th/net/project-management-metadata/read-built-in-properties-project-management-documents/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะเจาะลึกเกี่ยวกับการใช้ประโยชน์จาก GroupDocs.Metadata สำหรับ .NET เพื่อแยกคุณสมบัติในตัวจากเอกสารการจัดการโครงการอย่างมีประสิทธิภาพ ไลบรารีนี้มีฟังก์ชันการทำงานที่มีประสิทธิภาพสำหรับการจัดการข้อมูลเมตาในรูปแบบไฟล์ต่างๆ รวมถึง Microsoft Project ซึ่งช่วยให้นักพัฒนาสามารถเข้าถึงรายละเอียดเอกสารสำคัญโดยทางโปรแกรม เราจะแนะนำคุณตลอดกระบวนการทีละขั้นตอน โดยแจกแจงแต่ละตัวอย่างเพื่อให้มั่นใจถึงความชัดเจนและง่ายต่อการนำไปใช้
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
-  GroupDocs.Metadata สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารีจากไฟล์[หน้าดาวน์โหลด](https://releases.groupdocs.com/metadata/net/).
- สภาพแวดล้อมการพัฒนา: ติดตั้ง IDE ที่เข้ากันได้ (เช่น Visual Studio) บนเครื่องของคุณ
- ความรู้พื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และกรอบงาน .NET

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการรวมเนมสเปซที่จำเป็นในโครงการ C# ของคุณ:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## ขั้นตอนที่ 1: สร้างอินสแตนซ์ของวัตถุข้อมูลเมตา
 ขั้นแรก ให้ยกตัวอย่าง`Metadata` วัตถุโดยการระบุเส้นทางไฟล์อินพุต:
```csharp
using (Metadata metadata = new Metadata("YourInputFile"))
{
    // รหัสไปที่นี่
}
```
 แทนที่`"YourInputFile"` พร้อมเส้นทางไปยังเอกสารการจัดการโครงการของคุณ
## ขั้นตอนที่ 2: เข้าถึงข้อมูลเมตาการจัดการโครงการ
ถัดไป ดึงข้อมูลแพ็คเกจรูทเฉพาะสำหรับเอกสารการจัดการโครงการ:
```csharp
var root = metadata.GetRootPackage<ProjectManagementRootPackage>();
```
นี้`root` วัตถุจะอนุญาตให้เข้าถึงคุณสมบัติของเอกสาร
## ขั้นตอนที่ 3: ดึงคุณสมบัติเอกสาร
ตอนนี้คุณสามารถแยกคุณสมบัติที่มีอยู่แล้วภายในต่างๆ จากเอกสารการจัดการโครงการ:
```csharp
Console.WriteLine(root.DocumentProperties.Author);
Console.WriteLine(root.DocumentProperties.CreationDate);
Console.WriteLine(root.DocumentProperties.Company);
Console.WriteLine(root.DocumentProperties.Category);
Console.WriteLine(root.DocumentProperties.Keywords);
Console.WriteLine(root.DocumentProperties.Revision);
Console.WriteLine(root.DocumentProperties.Subject);
```
 แต่ละ`WriteLine` คำสั่งดึงข้อมูลคุณสมบัติเฉพาะ เช่น ผู้แต่ง วันที่สร้าง บริษัท หมวดหมู่ คำสำคัญ การแก้ไข และหัวเรื่อง

## บทสรุป
โดยสรุป GroupDocs.Metadata สำหรับ .NET ช่วยลดความยุ่งยากในการแยกข้อมูลเมตาจากเอกสารการจัดการโครงการ เมื่อทำตามบทช่วยสอนนี้ คุณจะได้เรียนรู้วิธีใช้ไลบรารีเพื่อเข้าถึงรายละเอียดเอกสารที่สำคัญโดยทางโปรแกรม

## คำถามที่พบบ่อย
### GroupDocs.Metadata สำหรับ .NET เข้ากันได้กับไฟล์ Microsoft Project เวอร์ชันต่างๆ หรือไม่
ใช่ ไลบรารีรองรับรูปแบบ Microsoft Project เวอร์ชันต่างๆ ทำให้คุณสามารถดึงข้อมูลเมตาจากไฟล์เวอร์ชันต่างๆ ได้
### ฉันสามารถแก้ไขและอัปเดตข้อมูลเมตาโดยใช้ GroupDocs.Metadata สำหรับ .NET ได้หรือไม่
ใช่ ไลบรารีมีวิธีการอัปเดตและแก้ไขคุณสมบัติเมตาดาต้าภายในรูปแบบเอกสารที่รองรับ
### GroupDocs.Metadata สำหรับ .NET รองรับรูปแบบเอกสารอื่นๆ นอกเหนือจากไฟล์การจัดการโครงการหรือไม่
ใช่ รองรับรูปแบบเอกสารที่หลากหลาย เช่น Word, Excel, PowerPoint, PDF และอีกมากมาย
### ฉันจะค้นหาการสนับสนุนและทรัพยากรเพิ่มเติมสำหรับ GroupDocs.Metadata สำหรับ .NET ได้ที่ไหน
 ท่านสามารถเยี่ยมชมได้ที่[ฟอรัม GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14) สำหรับการสนับสนุนและการอภิปรายของชุมชน
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Metadata สำหรับ .NET ได้อย่างไร
 คุณสามารถขอ[ใบอนุญาตชั่วคราวที่นี่](https://purchase.groupdocs.com/temporary-license/) เพื่อประเมินความสามารถทั้งหมดของห้องสมุด