---
date: '2026-01-26'
description: เรียนรู้วิธีอ่านเวลาที่สร้างใน Java และดึงคุณสมบัติอื่น ๆ ของเอกสารจากการนำเสนอ
  PowerPoint ด้วย GroupDocs.Metadata สำหรับ Java เหมาะสำหรับการจัดการเอกสารและการปฏิบัติตามกฎระเบียบ.
keywords:
- read created time java
- java extract document properties
- presentation metadata
title: วิธีอ่านเวลาสร้างใน Java จากไฟล์พรีเซนเทชันโดยใช้ GroupDocs.Metadata – คู่มือแบบขั้นตอนต่อขั้นตอน
type: docs
url: /th/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# วิธีอ่าน created time java จากไฟล์งานนำเสนอโดยใช้ GroupDocs.Metadata

การจัดการเมตาดาต้าเป็นหัวใจสำคัญของกระบวนการทำงานกับเอกสารสมัยใหม่ ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีอ่าน created time java** และดึงคุณสมบัติที่เป็นประโยชน์อื่น ๆ เช่น ผู้เขียน, บริษัท, และคำสำคัญ จากงานนำเสนอ PowerPoint โดยใช้ **GroupDocs.Metadata for Java** เมื่อเสร็จแล้วคุณจะพร้อมนำข้อมูลเหล่านี้ไปผสานกับระบบจัดการเอกสาร, รายงานการปฏิบัติตาม, หรือแอปพลิเคชันที่พัฒนาโดย Java ที่ต้องการเข้าใจแหล่งกำเนิดของไฟล์

## คำตอบอย่างรวดเร็ว
- **What does “read created time java” mean?** เป็นกระบวนการดึงค่า timestamp ของการสร้างไฟล์ผ่านโค้ด Java  
- **Which library supports this?** GroupDocs.Metadata for Java ให้ API ที่เรียบง่ายสำหรับคุณสมบัติการนำเสนอที่มีมาในตัวทั้งหมด  
- **Do I need a license?** การทดลองใช้ฟรีสามารถใช้สำหรับการพัฒนาได้; จำเป็นต้องมีใบอนุญาตถาวรสำหรับการใช้งานในสภาพแวดล้อมการผลิต  
- **Can I extract other properties at the same time?** ได้—ผู้เขียน, บริษัท, ประเภท, และอื่น ๆ สามารถดึงได้ผ่าน API เดียวกัน  
- **What Java version is required?** JDK 8 หรือสูงกว่า  

## “read created time java” คืออะไร?
การอ่าน created time ของเอกสารใน Java หมายถึงการเข้าถึงฟิลด์เมตาดาต้าที่เก็บเวลาที่ไฟล์ถูกสร้างขึ้นครั้งแรก ค่าตัว timestamp นี้สำคัญสำหรับการควบคุมเวอร์ชัน, การตรวจสอบประวัติ, และการยืนยันการปฏิบัติตาม  

## ทำไมต้องใช้ GroupDocs.Metadata for Java เพื่อดึงคุณสมบัติของเอกสาร?
GroupDocs.Metadata แยกความซับซ้อนของรูปแบบไฟล์ต่าง ๆ ทำให้คุณสามารถมุ่งเน้นที่ตรรกะธุรกิจแทนการแยกวิเคราะห์ระดับต่ำ มันรองรับ PowerPoint, PDF, Word, และรูปภาพหลายประเภท ทำให้เป็นตัวเลือกที่หลากหลายสำหรับโครงการ Java ใด ๆ ที่ต้องการ **java extract document properties** อย่างเชื่อถือได้  

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Metadata for Java** เวอร์ชัน 24.12 หรือใหม่กว่า  
- Java Development Kit (JDK 8 หรือใหม่กว่า)  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  
- ความรู้พื้นฐานการจัดการไฟล์ด้วย Java  

## การตั้งค่า GroupDocs.Metadata for Java

### การตั้งค่า Maven
หากคุณจัดการ dependencies ด้วย Maven ให้เพิ่ม repository และ dependency ลงในไฟล์ `pom.xml` ของคุณ:

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

### ดาวน์โหลดโดยตรง
หรือคุณสามารถดาวน์โหลดไลบรารีจากหน้าการปล่อยอย่างเป็นทางการ:

[การปล่อย GroupDocs.Metadata for Java](https://releases.groupdocs.com/metadata/java/)

#### ขั้นตอนการรับใบอนุญาต
- **Free Trial:** เริ่มต้นด้วยการทดลองใช้ฟรีเพื่อสำรวจ API  
- **Temporary License:** รับคีย์ชั่วคราวสำหรับการทดสอบโดยไม่มีข้อจำกัด  
- **Purchase:** ซื้อใบอนุญาตเต็มรูปแบบสำหรับการใช้งานในสภาพแวดล้อมการผลิต  

### การเริ่มต้นและตั้งค่าเบื้องต้น
เมื่อ dependency ถูกเพิ่มแล้ว ให้สร้างอ็อบเจกต์ `Metadata` และชี้ไปที่ไฟล์งานนำเสนอของคุณ:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## วิธี java extract document properties จากงานนำเสนอ
ด้านล่างนี้เราจะอธิบายคุณสมบัติ built‑in ที่พบบ่อยที่สุด พร้อมแสดงวิธีอ่านอย่างละเอียด

### การดึงข้อมูลผู้เขียน
**Overview:** ดึงชื่อของผู้ที่สร้างงานนำเสนอ

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*เมธอด `getAuthor()` จะคืนค่าชื่อผู้เขียนหรือ `null` หากฟิลด์ว่าง*

### การดึง Created Time (read created time java)
**Overview:** รับค่า timestamp ที่บ่งบอกว่าไฟล์ถูกสร้างครั้งแรกเมื่อใด

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*เมธอด `getCreatedTime()` ให้วัตถุ `java.util.Date` ที่แสดงช่วงเวลาการสร้าง—ตรงกับที่ “read created time java” หมายถึง*

### การดึงข้อมูลบริษัท
**Overview:** ดึงชื่อองค์กรที่เชื่อมโยงกับงานนำเสนอ

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*เมธอด `getCompany()` จะคืนค่าข้อมูลเมตาดาต้าของบริษัทหรือ `null` หากไม่ได้ตั้งค่า*

### เมตาดาต้าเพิ่มเติมที่คุณสามารถดึงได้
คุณสามารถดึงฟิลด์ built‑in อื่น ๆ เช่น **Category**, **Keywords**, **Last Printed Date**, และ **Application Name** ด้วยเมธอดเช่น `getCategory()`, `getKeywords()`, เป็นต้น  

## การประยุกต์ใช้งานจริง
- **Document Management Systems:** ทำดัชนีงานนำเสนอโดยผู้เขียน, บริษัท, หรือวันที่สร้างเพื่อการดึงข้อมูลที่รวดเร็ว  
- **Compliance Auditing:** ตรวจสอบว่าเมตาดาต้าที่จำเป็น (เช่น timestamp การสร้าง) มีอยู่ก่อนทำการเก็บถาวร  
- **Automated Reporting:** สร้างรายงานสรุปที่ระบุว่าใครสร้างสไลด์เด็คแต่ละชุดและเมื่อไหร่  
- **CRM Integration:** เชื่อมโยงงานนำเสนอกับบันทึกลูกค้าโดยใช้ฟิลด์เมตาดาต้าของบริษัท  

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Parallel Processing:** เมื่อจัดการชุดไฟล์ขนาดใหญ่ ให้ประมวลผลไฟล์ในเธรดแยกเพื่อเพิ่มอัตราการทำงาน  
- **Resource Management:** ใช้ try‑with‑resources (ตามตัวอย่าง) เพื่อปิดสตรีมโดยอัตโนมัติและหลีกเลี่ยงการรั่วของหน่วยความจำ  
- **Batch Extraction:** GroupDocs.Metadata รองรับการทำงานแบบแบตช์; พิจารณาอ่านหลายไฟล์ในลูปเดียวเพื่อประสิทธิภาพ  

## ปัญหาทั่วไปและวิธีแก้
- **Missing Metadata:** หากคุณสมบัติคืนค่า `null` หมายความว่าไฟล์ต้นทางไม่มีข้อมูลนั้น ให้ตรวจสอบค่า `null` ตามที่แสดง  
- **Unsupported Format:** ตรวจสอบว่าไฟล์เป็นรูปแบบ PowerPoint ที่รองรับ (`.pptx`, `.ppt`)  
- **License Errors:** ตรวจสอบว่าไฟล์ใบอนุญาตวางอยู่ในตำแหน่งที่ถูกต้องหรือระยะทดลองใช้ยังไม่หมดอายุ  

## คำถามที่พบบ่อย

**Q: ฉันจะจัดการกับคุณสมบัติเมตาดาต้าที่หายไปอย่างไร?**  
A: API จะคืนค่า `null` สำหรับฟิลด์ที่ไม่ได้ตั้งค่า ใช้เงื่อนไขเช่น `(author != null ? author : "N/A")` เพื่อให้ค่าตัวสำรอง  

**Q: GroupDocs.Metadata สามารถดึงฟิลด์เมตาดาต้ากำหนดเองได้หรือไม่?**  
A: ได้, นอกเหนือจากคุณสมบัติ built‑in คุณสามารถอ่านและเขียนคู่คีย์/ค่าแบบกำหนดเองโดยใช้ API เดียวกัน  

**Q: มีการสนับสนุนรูปแบบงานนำเสนออื่น ๆ หรือไม่?**  
A: GroupDocs.Metadata ทำงานกับ PowerPoint (`.ppt`, `.pptx`) รวมถึง PDF, Word, และรูปภาพหลายประเภท  

**Q: ความต้องการระบบสำหรับ GroupDocs.Metadata Java คืออะไร?**  
A: JDK ที่เข้ากันได้ (8 หรือสูงกว่า) และหน่วยความจำ heap เพียงพอสำหรับขนาดของเอกสารที่คุณประมวลผล  

**Q: จะหาความช่วยเหลือได้จากที่ไหนหากเจอปัญหา?**  
A: เยี่ยมชมฟอรั่มสนับสนุนของ GroupDocs เพื่อขอความช่วยเหลือ: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)  

## แหล่งข้อมูล
- **เอกสาร:** https://docs.groupdocs.com/metadata/java/  
- **อ้างอิง API:** https://reference.groupdocs.com/metadata/java/  
- **ดาวน์โหลด:** https://releases.groupdocs.com/metadata/java/  
- **GitHub:** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java  
- **สนับสนุนฟรี:** https://forum.groupdocs.com/c/metadata/  
- **ใบอนุญาตชั่วคราว:** https://purchase.groupdocs.com/temporary-license/  

โดยทำตามคู่มือนี้ คุณจะรู้วิธี **read created time java** และ **java extract document properties** จากงานนำเสนอ PowerPoint ด้วย GroupDocs.Metadata นำโค้ดตัวอย่างเหล่านี้ไปใช้ในโครงการของคุณเพื่อเพิ่มความฉลาดให้กับเอกสารและทำให้กระบวนการปฏิบัติตามเป็นไปอย่างราบรื่น  

**Last Updated:** 2026-01-26  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs