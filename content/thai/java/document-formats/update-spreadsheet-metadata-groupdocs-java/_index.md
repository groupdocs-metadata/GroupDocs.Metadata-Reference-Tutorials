---
date: '2026-03-22'
description: เรียนรู้วิธีเปลี่ยนวันที่สร้างไฟล์ Excel และอัปเดตเมตาดาต้า Excel ด้วย
  GroupDocs.Metadata สำหรับ Java. ทำตามคู่มือขั้นตอนต่อขั้นตอนนี้เพื่อเพิ่มคีย์เวิร์ดใน
  Excel และแก้ไขคุณสมบัติของเอกสาร.
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: เปลี่ยนวันที่สร้างไฟล์ Excel ด้วย GroupDocs.Metadata ใน Java
type: docs
url: /th/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# เปลี่ยนวันที่สร้างไฟล์ Excel ด้วย GroupDocs.Metadata ใน Java

ในสภาพแวดล้อมที่ขับเคลื่อนด้วยข้อมูลสมัยใหม่ การ **เปลี่ยนวันที่สร้างไฟล์ Excel** และการรักษาเมตาดาต้าอื่น ๆ ให้เป็นปัจจุบันสามารถปรับปรุงการจัดระเบียบเอกสาร การค้นหา และการปฏิบัติตามกฎระเบียบได้อย่างมาก ไม่ว่าคุณจะจัดการกับรายงานการเงิน ตัวติดตามโครงการ หรือข้อมูลเก็บถาวร เมตาดาต้าที่แม่นยำจะทำให้คนที่เหมาะสมพบไฟล์ที่เหมาะสมในเวลาที่เหมาะสม บทเรียนนี้จะพาคุณผ่านการใช้ไลบรารี GroupDocs.Metadata เพื่อ **เปลี่ยนวันที่สร้างไฟล์ Excel**, **เพิ่มคีย์เวิร์ดให้กับ Excel**, และ **แก้ไขคุณสมบัติของเอกสาร Excel** ในแอปพลิเคชัน Java.

## คำตอบด่วน
- **ฉันสามารถเปลี่ยนวันที่สร้างของไฟล์ Excel ได้หรือไม่?** ใช่, โดยใช้ `setCreatedTime` จาก GroupDocs.Metadata.  
- **ไลบรารีใดที่รองรับการอัปเดตเมตาดาต้า Excel ใน Java?** GroupDocs.Metadata for Java.  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีสามารถใช้งานเพื่อการประเมินได้; จำเป็นต้องมีไลเซนส์ถาวรสำหรับการใช้งานจริง.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า.  
- **ฉันสามารถเพิ่มคีย์เวิร์ดที่กำหนดเองให้กับเวิร์กบุ๊ก Excel ได้หรือไม่?** แน่นอน—ใช้ `setKeywords` บนคุณสมบัติของเอกสาร.

## “การเปลี่ยนวันที่สร้างไฟล์ Excel” คืออะไร?
การเปลี่ยนวันที่สร้างไฟล์ Excel หมายถึงการอัปเดตคุณสมบัติ *Created* ที่สร้างไว้ภายในไฟล์เวิร์กบุ๊ก คุณสมบัตินี้เป็นส่วนหนึ่งของเมตาดาต้า Office Open XML มาตรฐานและสามารถแก้ไขได้โดยโปรแกรมโดยไม่ต้องเปลี่ยนแปลงเนื้อหาแผ่นงานจริง

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับเมตาดาต้า Excel?
GroupDocs.Metadata ให้ API ระดับสูงที่ปลอดภัยต่อประเภท ซึ่งทำให้ซับซ้อนการจัดการ XML ระดับต่ำที่จำเป็นสำหรับรูปแบบ Office Open XML มันทำให้คุณสามารถ:
- **อัปเดตคุณสมบัติหลัก** เช่น ผู้เขียน, บริษัท, และวันที่สร้าง ในหนึ่งคำสั่ง.  
- **เพิ่มคีย์เวิร์ดให้กับ Excel** เพื่อปรับปรุงผลการค้นหาใน SharePoint, OneDrive หรือระบบไฟล์ท้องถิ่น.  
- **แก้ไขคุณสมบัติของเอกสาร Excel** โดยไม่ต้องเปิดเวิร์กบุ๊กใน Excel ซึ่งช่วยประหยัดเวลาและทรัพยากร.

## ข้อกำหนดเบื้องต้น
- Java Development Kit (JDK) 8 หรือใหม่กว่า.  
- IDE เช่น IntelliJ IDEA หรือ Eclipse.  
- ความคุ้นเคยพื้นฐานกับ Java file I/O.  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### การติดตั้ง

Add the GroupDocs.Metadata Maven repository and dependency to your `pom.xml`:

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

Alternatively, you can [ดาวน์โหลดเวอร์ชันล่าสุดโดยตรง](https://releases.groupdocs.com/metadata/java/) if you prefer a manual setup.

### การรับไลเซนส์

GroupDocs มีการทดลองใช้ฟรีเพื่อการประเมิน สำหรับการใช้งานจริง ให้รับไลเซนส์ชั่วคราวหรือถาวรจากผู้ขาย เยี่ยมชม [หน้าการซื้อของ GroupDocs](https://purchase.groupdocs.com/temporary-license/) สำหรับรายละเอียด.

#### การเริ่มต้นพื้นฐาน

Import the necessary classes in your Java source file:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## การดำเนินการแบบขั้นตอน

### ขั้นตอนที่ 1: เปิดเวิร์กบุ๊ก Excel

Provide the path to the source workbook and create a `Metadata` instance. The `try‑with‑resources` block ensures the file handle is closed automatically.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### ขั้นตอนที่ 2: อัปเดตคุณสมบัติเบื้องต้นของเมตาดาต้า

Now you can **change the Excel creation date**, set the author, company, category, and **add keywords to Excel**. The `new Date()` call captures the current timestamp, but you can supply any `java.util.Date` you need.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **เคล็ดลับ:** ใช้รูปแบบการตั้งชื่อคีย์เวิร์ดที่สอดคล้องกัน (เช่น `project:Q2, finance, confidential`) เพื่อทำให้การค้นหาในอนาคตมีประสิทธิภาพมากขึ้น.

### ขั้นตอนที่ 3: บันทึกเวิร์กบุ๊กที่อัปเดต

Specify an output path and persist the changes. The original file remains untouched, which is useful for audit trails.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## ปัญหาทั่วไปและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|---------|
| **ข้อผิดพลาดของเส้นทางไฟล์** | เส้นทางสัมพัทธ์/เต็มที่ไม่ถูกต้อง | ตรวจสอบ `inputFilePath` และ `outputFilePath` อีกครั้ง ใช้ `Paths.get(...)` สำหรับเส้นทางที่ไม่ขึ้นกับแพลตฟอร์ม. |
| **เวอร์ชันไลบรารีไม่เข้ากัน** | ใช้ GroupDocs.Metadata รุ่นเก่าที่ไม่รองรับเมธอด `setCreatedTime` | อัปเกรดเป็นเวอร์ชันล่าสุด (ตามที่แสดงในสแนปช็อต Maven). |
| **ไม่มีไลเซนส์** | ระยะเวลาทดลองหมดอายุ | ใช้ไลเซนส์ชั่วคราวหรือซื้อไลเซนส์เต็มผ่านหน้าการซื้อ. |
| **การใช้หน่วยความจำของเวิร์กบุ๊กขนาดใหญ่** | การโหลดไฟล์ Excel ขนาดใหญ่ใช้หน่วยความจำ heap | ประมวลผลไฟล์เป็นชุดและเพิ่ม heap ของ JVM (`-Xmx`) หากจำเป็น. |

## คำถามที่พบบ่อย

**Q:** เวอร์ชัน Java ใดที่ GroupDocs.Metadata รองรับ?  
**A:** Java 8 และใหม่กว่าได้รับการสนับสนุนเต็มที่.

**Q:** ฉันควรจัดการกับข้อยกเว้นเมื่ออัปเดตเมตาดาต้าอย่างไร?  
**A:** ห่อโค้ดด้วยบล็อก `try‑catch` และบันทึก `MetadataException` เพื่อจับข้อผิดพลาด I/O หรือรูปแบบใด ๆ

**Q:** ฉันสามารถอัปเดตไฟล์ Excel หลายไฟล์ในหนึ่งรอบได้หรือไม่?  
**A:** ได้, ทำการวนซ้ำผ่านคอลเลกชันของเส้นทางไฟล์, แต่ควรตรวจสอบการใช้หน่วยความจำสำหรับชุดใหญ่.

**Q:** สามารถย้อนกลับการเปลี่ยนแปลงเมตาดาต้าที่ทำไว้ได้หรือไม่?  
**A:** เก็บสำเนาสำรองของเวิร์กบุ๊กต้นฉบับก่อนทำการอัปเดต, แล้วกู้คืนหากจำเป็น.

**Q:** ฉันจะหาเอกสารรายละเอียดเพิ่มเติมได้จากที่ไหน?  
**A:** ดูคู่มืออย่างเป็นทางการที่ [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## การประยุกต์ใช้งานจริง

1. **การตรวจสอบการเงิน** – บันทึกว่าใครแก้ไขเวิร์กบุ๊กและเมื่อไหร่, เพื่อให้มีร่องรอยการตรวจสอบ.  
2. **การจัดการโครงการ** – ใส่แท็กคีย์เวิร์ดเฉพาะโครงการให้กับสเปรดชีตเพื่อการดึงข้อมูลอย่างรวดเร็ว.  
3. **การเก็บถาวรข้อมูล** – รักษาวันที่สร้างต้นฉบับและข้อมูลบริษัทเพื่อการปฏิบัติตามกฎระเบียบ.

## เคล็ดลับด้านประสิทธิภาพ

- จำกัดการดำเนินการเมตาดาต้าต่อรอบเพื่อหลีกเลี่ยงการใช้หน่วยความจำมากเกินไป.  
- ปิดอ็อบเจ็กต์ `Metadata` อย่างทันท่วงที (รูปแบบ `try‑with‑resources` ทำเช่นนี้โดยอัตโนมัติ).  
- สำหรับเวิร์กบุ๊กขนาดใหญ่มาก, พิจารณาประมวลผลบนเธรดเบื้องหลังเพื่อให้ UI ตอบสนอง.

## สรุป

You now know how to **change Excel creation date**, **add keywords to Excel**, and **modify Excel document properties** using GroupDocs.Metadata in Java. This capability empowers you to keep your spreadsheets well‑organized, searchable, and compliant with internal governance policies. As a next step, explore other metadata features such as custom properties or batch processing to further streamline your document management workflow.

---

**อัปเดตล่าสุด:** 2026-03-22  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs  

**แหล่งข้อมูล**
- [เอกสาร](https://docs.groupdocs.com/metadata/java/)
- [อ้างอิง API](https://reference.groupdocs.com/metadata/java/)
- [ดาวน์โหลด GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [ที่เก็บ GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [ฟอรั่มสนับสนุนฟรี](https://forum.groupdocs.com/c/metadata/)
- [ไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)