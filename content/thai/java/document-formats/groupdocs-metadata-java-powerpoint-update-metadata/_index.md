---
date: '2026-05-27'
description: เรียนรู้วิธีตั้งค่า pptx CreatedTime ใน Java โดยใช้ GroupDocs Maven Dependency
  เพื่ออัปเดตเมตาดาต้าของ PowerPoint รวมถึงวิธีเปลี่ยนวันที่สร้างของ PPTX
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: ตั้งค่า CreatedTime ของ PPTX ใน Java ด้วย GroupDocs Maven Dependency
type: docs
url: /th/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# ตั้งค่า PPTX CreatedTime ใน Java ด้วย GroupDocs.Metadata

Metadata ที่แม่นยำเป็นสิ่งสำคัญสำหรับการปฏิบัติตามข้อกำหนดและการค้นพบในกระบวนการทำงานเอกสารสมัยใหม่ ด้วย **GroupDocs.Metadata** คุณสามารถตั้งค่า **PPTX CreatedTime ใน Java** อย่างโปรแกรมเมติกได้ ทำให้คุณสามารถ **เปลี่ยนวันที่สร้าง PPTX** พร้อมกับคุณสมบัติตามที่สร้างไว้เช่นผู้เขียนหรือบริษัท บทแนะนำนี้จะพาคุณผ่านการตั้งค่า Maven, การเริ่มต้น API, การอัปเดต metadata, และการบันทึกการนำเสนอที่แก้ไขแล้ว — ทั้งหมดด้วยโค้ดที่ชัดเจนและพร้อมใช้งานในสภาพแวดล้อมการผลิต

## คำตอบเร็ว
- **ไลบรารีใดที่อัปเดตเมตาดาต้า PowerPoint ใน Java?** GroupDocs.Metadata via the GroupDocs Maven dependency.  
- **ฉันสามารถตั้งค่าคุณสมบัติ PPTX CreatedTime ได้หรือไม่?** Yes—use `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **จำเป็นต้องมีใบอนุญาตสำหรับการผลิตหรือไม่?** A trial works for evaluation; a commercial license is mandatory for production deployments.  
- **เครื่องมือสร้างที่ใช้ในตัวอย่างคืออะไร?** Maven (you can also download the JAR manually).  
- **API รองรับ Java 8 และใหม่กว่าไหม?** Absolutely—GroupDocs.Metadata targets Java 8+.

## GroupDocs Maven Dependency คืออะไร?
**GroupDocs Maven dependency** คือรายการในที่เก็บที่เข้ากันได้กับ Maven ที่ดึงไลบรารี GroupDocs.Metadata เวอร์ชันล่าสุดเข้าสู่โครงการ Java ของคุณ มันทำให้การจัดการ dependencies ง่ายขึ้นโดยการแก้ไขไลบรารีที่ขึ้นต่อกันโดยอัตโนมัติ, รับประกันว่าคุณจะใช้เวอร์ชันที่ใหม่ที่สุดและปลอดภัยเสมอ, และขจัดความจำเป็นในการดาวน์โหลด JAR ด้วยตนเองหรือการติดตามเวอร์ชัน.

## ทำไมต้องใช้ GroupDocs.Metadata เพื่อเปลี่ยนวันที่สร้าง PPTX?
GroupDocs.Metadata ทำให้สามารถอัปเดต timestamps การสร้าง PPTX แบบอัตโนมัติและพร้อมสำหรับการประมวลผลเป็นชุด, ทำให้การนำเสนอทุกไฟล์สอดคล้องกับนโยบายของบริษัทหรือข้อกำหนดทางกฎหมาย โดยการตั้งค่า CreatedTime ผ่านโปรแกรม คุณจะหลีกเลี่ยงการแก้ไขด้วยมือ, ลดข้อผิดพลาดของมนุษย์, และสามารถรวมการเปลี่ยนแปลงนี้เข้าไปใน pipeline CI/CD หรือสคริปต์การย้ายข้อมูลเพื่อการจัดการเอกสารที่ไร้รอยต่อ.

## ข้อกำหนดเบื้องต้น
- Java 8 หรือสูงกว่า ติดตั้งแล้ว.  
- IDE เช่น IntelliJ IDEA หรือ Eclipse.  
- Maven สำหรับการจัดการ dependencies.  
- เข้าถึงการทดลองใช้ GroupDocs หรือใบอนุญาตที่ซื้อแล้ว.

## วิธีตั้งค่า PPTX CreatedTime ใน Java?
คลาส `Metadata` แสดงถึงเอกสารและให้การเข้าถึงคุณสมบัติ metadata ของมัน

โหลดไฟล์ PowerPoint ของคุณด้วย `new Metadata("presentation.pptx")`, ดึงแพ็กเกจราก, เรียก `setCreatedTime` ด้วย `java.util.Date` ที่ต้องการ, และสุดท้ายเรียก `save` เพื่อบันทึกการเปลี่ยนแปลง การไหลของขั้นตอนจากต้นจนจบนี้จะปรับวันที่สร้างโดยยังคงเนื้อหาและคุณสมบัติอื่นของสไลด์ทั้งหมดไว้

### การตั้งค่า Maven
เพิ่มรีโพซิทอรี GroupDocs และ dependency ของ metadata ลงในไฟล์ `pom.xml` ของคุณ:

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

> **เคล็ดลับ:** การอัปเดตหมายเลขเวอร์ชันให้เป็นปัจจุบันช่วยให้คุณได้รับประโยชน์จากการแก้ไขบั๊กและการปรับปรุงประสิทธิภาพล่าสุด.

### ดาวน์โหลดโดยตรง (หากคุณไม่ต้องการใช้ Maven)

หรือคุณสามารถดาวน์โหลด JAR เวอร์ชันล่าสุดจาก [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### การรับใบอนุญาต

เริ่มต้นด้วยการทดลองใช้ฟรีหรือขอใบอนุญาตชั่วคราวเพื่อประเมิน GroupDocs.Metadata สำหรับการใช้งานในสภาพแวดล้อมการผลิต, ให้ซื้อใบอนุญาตผ่าน [GroupDocs' official website](https://purchase.groupdocs.com/temporary-license/).

## การเริ่มต้นและการตั้งค่าพื้นฐาน

เมื่อไลบรารีอยู่ใน classpath แล้ว, คุณสามารถสร้างอินสแตนซ์ `Metadata` ที่ชี้ไปยังไฟล์ PowerPoint ของคุณ:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

## คู่มือขั้นตอนต่อขั้นตอนเพื่ออัปเดต Metadata ที่สร้างไว้

### ขั้นตอนที่ 1: โหลดเอกสารการนำเสนอ

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

การโหลดไฟล์สร้างการเชื่อมต่อที่ทำให้คุณสามารถอ่านหรือเขียน metadata ได้.

### ขั้นตอนที่ 2: เข้าถึงแพ็กเกจรากของการนำเสนอ

อ็อบเจ็กต์ `root` ให้การเข้าถึงแพ็กเกจหลักของการนำเสนอและคุณสมบัติตามที่สร้างไว้.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

อ็อบเจ็กต์ `root` เปิดเผยคุณสมบัติเอกสารที่สร้างไว้ทั้งหมด.

### ขั้นตอนที่ 3: อัปเดตคุณสมบัติเอกสารที่สร้างไว้ (รวมถึงวันที่สร้าง)

`setCreatedTime` กำหนด timestamp การสร้างใหม่ให้กับเอกสาร.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

ที่นี่เราจะแสดงวิธี **ตั้งค่า PPTX CreatedTime** โดยการกำหนดอ็อบเจ็กต์ `Date` ใหม่ให้กับ `CreatedTime`. แทนที่ `new Date()` ด้วย timestamp เฉพาะที่คุณต้องการ.

### ขั้นตอนที่ 4: บันทึกการนำเสนอที่อัปเดต

`save` เขียน metadata ที่แก้ไขแล้วกลับไปยังไฟล์.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

การเรียก `save` จะเขียน metadata ที่แก้ไขแล้วกลับไปยังไฟล์ PowerPoint ใหม่, โดยไม่ทำให้ไฟล์ต้นฉบับเปลี่ยนแปลง.

## เคล็ดลับการแก้ไขปัญหา
- **ไฟล์ไม่พบ:** ตรวจสอบเส้นทางอินพุตและสิทธิ์ของไฟล์อีกครั้ง.  
- **เวอร์ชันไม่ตรงกัน:** ตรวจสอบให้แน่ใจว่าเวอร์ชัน `groupdocs-metadata` ตรงกับ runtime ของ Java ของคุณ.  
- **คุณสมบัติไม่อัปเดต:** ยืนยันว่าคุณเรียก `setCreatedTime` (หรือ setter ที่เกี่ยวข้อง) ก่อนเรียก `save`.

## การประยุกต์ใช้งานจริง
1. **การสร้างแบรนด์ขององค์กร:** แทรกชื่อบริษัทและหมวดหมู่ที่ถูกต้องลงในสไลด์ทั้งหมดโดยอัตโนมัติก่อนการแจกจ่าย.  
2. **ระบบจัดการเอกสาร:** เพิ่ม metadata ที่ค้นหาได้ให้กับไฟล์ PPTX เพื่อการดึงข้อมูลที่เร็วขึ้น.  
3. **แหล่งข้อมูลการศึกษา:** รักษาข้อมูลผู้เขียนและหลักสูตรให้เป็นปัจจุบันในสไลด์การบรรยาย.  
4. **การติดตามการทำงานร่วมกัน:** บันทึกชื่อผู้ร่วมทำงานเพื่อรักษาความรับผิดชอบ.  
5. **การบูรณาการ CMS:** ซิงค์การเปลี่ยนแปลง metadata กับแพลตฟอร์มการจัดการเนื้อหาของคุณแบบเรียลไทม์.

## การพิจารณาประสิทธิภาพ
- **การประมวลผลเป็นชุด:** วนลูปไฟล์หลายไฟล์และใช้ `Metadata` อินสแตนซ์เดียวซ้ำเมื่อเป็นไปได้.  
- **การจัดการหน่วยความจำ:** ใช้ try‑with‑resources เสมอ (ตามที่แสดง) เพื่อปล่อยทรัพยากรเนทีฟโดยเร็ว.  
- **โครงสร้างข้อมูลที่มีประสิทธิภาพ:** เก็บการอัปเดต metadata ใน map ก่อนนำไปใช้เพื่อลดการเรียกซ้ำ.

## คำถามที่พบบ่อย

**Q: วัตถุประสงค์หลักของ GroupDocs Maven dependency คืออะไร?**  
A: มันให้วิธีที่สะดวกในการรวมไลบรารี GroupDocs.Metadata เวอร์ชันล่าสุดในโครงการ Java ที่ใช้ Maven.

**Q: ฉันจะตั้งค่าวันที่สร้าง PPTX โดยไม่กระทบคุณสมบัติอื่นได้อย่างไร?**  
A: ใช้ `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` ก่อนเรียก `metadata.save()`.

**Q: ฉันต้องการใบอนุญาตเพื่อรันโค้ดนี้ในขั้นพัฒนาไหม?**  
A: ใบอนุญาตทดลองชั่วคราวเพียงพอสำหรับการพัฒนาและทดสอบ; จำเป็นต้องมีใบอนุญาตเต็มสำหรับการผลิต.

**Q: ฉันสามารถอัปเดตฟิลด์ metadata แบบกำหนดเองได้หรือไม่?**  
A: ได้—GroupDocs.Metadata รองรับทั้งคุณสมบัติตามที่สร้างไว้และคุณสมบัติแบบกำหนดเองผ่าน API ของมัน.

**Q: มีวิธีการย้อนกลับการเปลี่ยนแปลงหากฉันทำผิดพลาดหรือไม่?**  
A: เก็บสำเนาไฟล์ต้นฉบับหรืออ่านค่าคุณสมบัติปัจจุบันก่อนเขียนทับ, จากนั้นกู้คืนหากจำเป็น.

## แหล่งข้อมูล

- [เอกสาร](https://docs.groupdocs.com/metadata/java/)
- [อ้างอิง API](https://apireference.groupdocs.com/metadata/java/)

---

**อัปเดตล่าสุด:** 2026-05-27  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs  

---

## บทแนะนำที่เกี่ยวข้อง

- [อัปเดต Metadata แบบกำหนดเองใน PowerPoint ด้วย GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [วิธีอัปเดต Metadata ของเอกสาร Word ด้วย GroupDocs.Metadata Java: คู่มือครบถ้วน](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [อัปเดต PDF Metadata อย่างมีประสิทธิภาพด้วย GroupDocs.Metadata ใน Java สำหรับการจัดการเอกสาร](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)