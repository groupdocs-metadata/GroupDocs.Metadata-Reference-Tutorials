---
date: '2026-06-12'
description: เรียนรู้วิธีสร้างแพ็กเกจ XMP แบบกำหนดเอง, จัดการเมตาดาต้าไฟล์และเพิ่มเมตาดาต้าแบบกำหนดเองลงใน
  PDF ด้วย GroupDocs.Metadata สำหรับ Java.
keywords:
- create custom xmp package
- manage file metadata
- add custom metadata pdf
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  headline: Create Custom XMP Package with GroupDocs.Metadata for Java
  type: TechArticle
- description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  name: Create Custom XMP Package with GroupDocs.Metadata for Java
  steps:
  - name: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
    text: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
  - name: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
    text: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
  - name: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
    text: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
  type: HowTo
- questions:
  - answer: Over 50 formats—including JPEG, PNG, PDF, DOCX, and TIFF—support XMP packet
      injection. See the full list in the [GroupDocs.Metadata documentation](https://docs.groupdocs.com/metadata/java/).
    question: What file formats support custom XMP packages?
  - answer: Yes, the library lets you read, modify, and delete any XMP property using
      the `IXmp` interface.
    question: Can I edit existing XMP metadata with GroupDocs.Metadata?
  - answer: For unsupported formats, consider wrapping the file in a container that
      does support XMP (e.g., converting to PDF) or using an alternative metadata
      store.
    question: How do I handle files that don’t natively support XMP?
  - answer: Absolutely—GroupDocs.Metadata is tested against Java 8 through Java 21,
      including all LTS releases.
    question: Is the library compatible with Java 17 LTS?
  - answer: Common pitfalls include using an incorrect namespace URI, exceeding the
      maximum packet size (≈ 2 MB), or attempting to write to a read‑only file. Ensure
      proper permissions and validate your XML schema before saving.
    question: What are typical errors when adding XMP packages?
  type: FAQPage
title: สร้างแพ็กเกจ XMP แบบกำหนดเองด้วย GroupDocs.Metadata สำหรับ Java
type: docs
url: /th/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/
weight: 1
---

# สร้างแพ็กเกจ XMP แบบกำหนดเองด้วย GroupDocs.Metadata สำหรับ Java

ในกระบวนการทำงานดิจิทัลสมัยใหม่, **การสร้างแพ็กเกจ XMP แบบกำหนดเอง** มีความสำคัญสำหรับการฝังเมตาดาต้าที่มีความหลากหลายและค้นหาได้โดยตรงภายในไฟล์ ไม่ว่าคุณจะจัดการกับรูปภาพ, PDF หรือสื่อมัลติมีเดีย, GroupDocs.Metadata สำหรับ Java ให้วิธีที่เชื่อถือได้ในการ **จัดการเมตาดาต้าไฟล์** และ **เพิ่มเมตาดาต้าแบบกำหนดเองลงใน PDF** โดยไม่ต้องใช้ฐานข้อมูลภายนอก ในบทแนะนำนี้เราจะพาคุณผ่านกระบวนการทั้งหมด—ตั้งแต่การตั้งค่าห้องสมุดจนถึงการฝังแพ็กเกจ XMP ที่ครบถ้วน—เพื่อให้คุณเริ่มเพิ่มคุณค่าให้กับเอกสารของคุณได้ทันที

## คำตอบสั้น
- **ขั้นตอนแรกคืออะไร?** เพิ่ม GroupDocs.Metadata เป็น dependency ของ Maven หรือดาวน์โหลดไฟล์ JAR.  
- **ต้องใช้บรรทัดโค้ดกี่บรรทัด?** เพียงสามคำสั่งสั้น ๆ เพียงพอสำหรับการสร้างและแนบแพ็กเกจ XMP แบบกำหนดเอง.  
- **ไฟล์ฟอร์แมตใดบ้างที่รองรับ?** มากกว่า 50 ฟอร์แมต รวมถึง JPEG, PNG, PDF, DOCX, และ TIFF.  
- **ต้องใช้ไลเซนส์หรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการพัฒนา; จำเป็นต้องมีไลเซนส์ถาวรสำหรับการใช้งานจริง.  
- **สามารถใช้กับ Java 11+ ได้หรือไม่?** ใช่, ไลบรารีเข้ากันได้กับ Java 8 ถึง Java 21.

## “สร้างแพ็กเกจ XMP แบบกำหนดเอง” คืออะไร?
*การสร้างแพ็กเกจ XMP แบบกำหนดเอง* หมายถึงการสร้างแพ็กเกจ XMP ที่มีฟิลด์เมตาดาต้าที่ผู้ใช้กำหนดและฝังลงในไฟล์ที่รองรับ แพ็กเกจนี้จะถูกเก็บไว้ในส่วน XMP ของไฟล์ ทำให้เมตาดาต้าสามารถพกพาและค้นหาได้โดยแอปพลิเคชันที่รองรับ XMP ใด ๆ

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java เพื่อจัดการเมตาดาต้าไฟล์?
GroupDocs.Metadata รองรับ **ฟอร์แมตเข้าและออกกว่า 50** และสามารถประมวลผลไฟล์ขนาดสูงสุด **2 GB** โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ ซึ่งช่วยลดการใช้ RAM ได้ถึง **80 %** สำหรับไฟล์ขนาดใหญ่ API ยังให้การทำงานแบบ thread‑safe ทำให้สามารถประมวลผลแบบแบตช์ที่มีอัตราการทำงานสูงในสภาพแวดล้อมองค์กรได้

## ข้อกำหนดเบื้องต้น
- **Java Development Kit** 8 หรือใหม่กว่า (แนะนำ Java 11+).  
- IDE เช่น **IntelliJ IDEA** หรือ **Eclipse**.  
- ติดตั้ง Maven เพื่อจัดการ dependency.  
- ความเข้าใจพื้นฐานเกี่ยวกับคลาส Java และแนวคิดเมตาดาต้า.

## การตั้งค่า GroupDocs.Metadata สำหรับ Java
### การตั้งค่า Maven
เพิ่ม dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณเพื่อรวม GroupDocs.Metadata:

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

ดูที่ [เอกสาร API](https://reference.groupdocs.com/metadata/java/) สำหรับลายเซ็นเมธอดทั้งหมด.  
สำหรับการอ้างอิง API อย่างละเอียด ดูที่ [เอกสาร GroupDocs.Metadata Java](https://docs.groupdocs.com/metadata/java/).

**ดาวน์โหลดโดยตรง** – หากคุณต้องการตั้งค่าด้วยตนเอง, ดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/). คุณยังสามารถดูหน้าที่ [Latest Releases](https://releases.groupdocs.com/metadata/java/) เพื่อดูรายละเอียดของบันทึกการเปลี่ยนแปลง.

### การรับไลเซนส์
- **ทดลองใช้ฟรี** – ประเมินคุณสมบัติทั้งหมดโดยไม่มีค่าใช้จ่าย.  
- **ไลเซนส์ชั่วคราว** – รับคีย์ที่มีระยะเวลาจำกัดสำหรับการทดสอบการพัฒนา. ([รับไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/))  
- **ซื้อ** – รับไลเซนส์ถาวรสำหรับการใช้งานในสภาพแวดล้อมการผลิต.

ซอร์สโค้ดและตัวอย่างพร้อมใช้งานบน [GroupDocs Metadata บน GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java).

## คู่มือการใช้งาน
ด้านล่างเป็นขั้นตอนแบบละเอียดที่แสดงอย่างชัดเจนวิธี **สร้างแพ็กเกจ XMP แบบกำหนดเอง** และฝังลงในไฟล์.

### วิธีสร้างแพ็กเกจ XMP แบบกำหนดเองและแนบลงในไฟล์?
โหลดไฟล์เป้าหมายของคุณด้วยคลาส `Metadata`, สร้าง `XmpPacketWrapper`, กำหนดฟิลด์ XMP แบบกำหนดเองของคุณ, และสุดท้ายบันทึกการเปลี่ยนแปลง กระบวนการจากต้นจนจบนี้ต้องการเพียงสามการเรียกเมธอดหลังจากการเริ่มต้นเท่านั้น กระบวนการนี้ทำให้แน่ใจว่าแพ็กเกจ XMP ถูกฝังอย่างถูกต้องและไฟล์ยังคงทำงานได้เต็มที่ในทุกแอปพลิเคชันที่รองรับ

### เริ่มต้นอ็อบเจ็กต์ Metadata
`Metadata` เป็นคลาสหลักที่แทนไฟล์และให้เมธอดสำหรับอ่านและเขียนเมตาดาต้าของไฟล์.  
```java
Metadata metadata = new Metadata("sample.pdf");
```

### สร้าง XmpPacketWrapper ใหม่
`XmpPacketWrapper` ทำหน้าที่เป็นคอนเทนเนอร์สำหรับหนึ่งหรือหลายแพ็กเกจ XMP, ช่วยให้สามารถอัปเดตเป็นชุดก่อนการบันทึก.  
```java
XmpPacketWrapper xmpWrapper = new XmpPacketWrapper();
```

### กำหนดและกำหนดค่าพา็กเกจ XMP แบบกำหนดเอง
อินเทอร์เฟซ `IXmp` ให้คุณกำหนดสกีม่า XMP แบบกำหนดเองและตั้งค่าคุณสมบัติภายในแพ็กเกจ.  
```java
IXmp customXmp = xmpWrapper.createPackage("http://mycompany.com/custom");
customXmp.setProperty("Creator", "John Doe");
customXmp.setProperty("Project", "Metadata Migration");
customXmp.setProperty("Version", "1.0");
```

### บันทึกเมตาดาต้าที่อัปเดต
`Metadata.save()` เขียนเมตาดาต้าที่แก้ไขแล้วกลับไปยังไฟล์ต้นฉบับ, ทำให้แพ็กเกจ XMP ที่เพิ่มเข้ามาถูกบันทึกอย่างถาวร.  
```java
metadata.getXmp().addPacket(xmpWrapper);
metadata.save();
```

#### คำอธิบายส่วนประกอบสำคัญ
- **Metadata Object** – ศูนย์กลางสำหรับการเข้าถึงเมตาดาต้าไฟล์.  
- **IXmp Interface** – ให้เมธอดสำหรับอ่าน/เขียนฟิลด์เฉพาะของ XMP.  
- **XmpPacketWrapper** – เก็บหนึ่งหรือหลายแพ็กเกจ XMP, ช่วยให้ทำการอัปเดตเป็นชุดได้.  
- **Custom XMP Package** – สกีม่าแบบกำหนดของคุณที่เก็บข้อมูลเพิ่มเติม.

## ปัญหาทั่วไปและวิธีแก้
- **ไฟล์ฟอร์แมตที่ไม่รองรับ** – ตรวจสอบว่าไฟล์เป้าหมายอยู่ในรายการฟอร์แมตอย่างเป็นทางการ (รองรับมากกว่า 50 ฟอร์แมต).  
- **ไม่พบไลเซนส์** – ตรวจสอบว่าไฟล์ไลเซนส์อยู่ในไดเรกทอรีรากของแอปพลิเคชันหรือกำหนดผ่าน `License.setLicense("license_path")`.  
- **หน่วยความจำเต็มเมื่อประมวลผลไฟล์ขนาดใหญ่** – ใช้ `metadata.setLoadOptions(LoadOptions.lazyLoad())` เพื่อประมวลผลเมตาดาต้าแบบ lazy และลดการใช้หน่วยความจำ.  

สำหรับความช่วยเหลือเพิ่มเติม, เยี่ยมชมฟอรั่ม [สนับสนุนของ GroupDocs](https://forum.groupdocs.com/c/metadata/).

## การประยุกต์ใช้งานจริง
1. **การจัดการสินทรัพย์ดิจิทัล** – ฝังลิขสิทธิ์และสิทธิการใช้งานโดยตรงลงในรูปภาพและ PDF.  
2. **การปรับเนื้อหาให้เป็นส่วนบุคคล** – แนบตัวระบุเฉพาะผู้ใช้ลงในเอกสารเพื่อการส่งมอบที่ตรงเป้าหมาย.  
3. **การปฏิบัติตามกฎระเบียบ** – เก็บบันทึกการตรวจสอบและนโยบายการเก็บรักษาไว้ในไฟล์เอง, ทำให้การตรวจสอบการกำกับดูแลง่ายขึ้น.

## การพิจารณาด้านประสิทธิภาพ
- **การเพิ่มประสิทธิภาพทรัพยากร** – ประมวลผลเมตาดาต้าในโหมดสตรีมมิ่งเพื่อให้การใช้ RAM อยู่ต่ำกว่า **100 MB** สำหรับไฟล์ที่ใหญ่กว่า **1 GB**.  
- **การอัปเดตเวอร์ชัน** – รักษาไลบรารีให้เป็นรุ่นล่าสุด; แต่ละการปล่อยเวอร์ชันหลักจะเพิ่มการสนับสนุนฟอร์แมตใหม่และปรับปรุงความเร็วการประมวลผลได้ถึง **30 %**.

## สรุป
โดยการทำตามคู่มือนี้ คุณจะรู้วิธี **สร้างแพ็กเกจ XMP แบบกำหนดเอง** ด้วย GroupDocs.Metadata สำหรับ Java, ทำให้คุณสามารถ **จัดการเมตาดาต้าไฟล์** อย่างมีประสิทธิภาพและ **เพิ่มเมตาดาต้าแบบกำหนดเองลงใน PDF** รวมถึงฟอร์แมตอื่น ๆ อีกหลายรูปแบบ ทดลองใช้สกีม่า XMP เพิ่มเติม, ผสานกระบวนการทำงานนี้เข้าสู่สาย CI ของคุณ, หรือรวมกับ GroupDocs.Viewer เพื่อการประมวลผลเอกสารแบบต้นจนจบ.

## คำถามที่พบบ่อย

**ถาม: ฟอร์แมตไฟล์ใดบ้างที่รองรับแพ็กเกจ XMP แบบกำหนดเอง?**  
ตอบ: มากกว่า 50 ฟอร์แมต—รวมถึง JPEG, PNG, PDF, DOCX, และ TIFF—รองรับการฉีดแพ็กเกจ XMP. ดูรายการเต็มใน [เอกสาร GroupDocs.Metadata](https://docs.groupdocs.com/metadata/java/).

**ถาม: ฉันสามารถแก้ไขเมตาดาต้า XMP ที่มีอยู่แล้วด้วย GroupDocs.Metadata ได้หรือไม่?**  
ตอบ: ใช่, ไลบรารีอนุญาตให้คุณอ่าน, แก้ไข, และลบคุณสมบัติ XMP ใด ๆ ผ่านอินเทอร์เฟซ `IXmp`.

**ถาม: ฉันจะจัดการไฟล์ที่ไม่รองรับ XMP โดยเนทีฟอย่างไร?**  
ตอบ: สำหรับฟอร์แมตที่ไม่รองรับ, พิจารณาใส่ไฟล์ในคอนเทนเนอร์ที่รองรับ XMP (เช่น แปลงเป็น PDF) หรือใช้ที่เก็บเมตาดาต้าแบบอื่น.

**ถาม: ไลบรารีเข้ากันได้กับ Java 17 LTS หรือไม่?**  
ตอบ: แน่นอน—GroupDocs.Metadata ได้รับการทดสอบกับ Java 8 ถึง Java 21 รวมถึงทุกเวอร์ชัน LTS.

**ถาม: ข้อผิดพลาดทั่วไปเมื่อเพิ่มแพ็กเกจ XMP มีอะไรบ้าง?**  
ตอบ: ข้อผิดพลาดทั่วไปรวมถึงการใช้ URI ของ namespace ไม่ถูกต้อง, เกินขนาดแพ็กเกจสูงสุด (≈ 2 MB), หรือพยายามเขียนลงไฟล์ที่เป็นแบบอ่าน‑อย่างเท่านั้น. ตรวจสอบสิทธิ์ที่เหมาะสมและตรวจสอบสกีม่า XML ของคุณก่อนบันทึก.

---

**อัปเดตล่าสุด:** 2026-06-12  
**ทดสอบด้วย:** GroupDocs.Metadata 23.12 for Java  
**ผู้เขียน:** GroupDocs  

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

```java
import com.groupdocs.metadata.Metadata;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Proceed with operations on metadata
}
```

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Get the root XMP package from the metadata
    IXmp root = (IXmp) metadata.getRootPackage();
```

```java
import com.groupdocs.metadata.core.XmpPacketWrapper;

// Create a new XmpPacketWrapper to hold custom packages
XmpPacketWrapper packet = new XmpPacketWrapper();
```

```java
import com.groupdocs.metadata.core.XmpPackage;
import com.groupdocs.metadata.core.XmpArray;
import com.groupdocs.metadata.core.XmpArrayType;

// Define and configure the custom XMP package
custom = new XmpPackage("gd", "GroupDocs Custom Package");
custom.set("CustomProperty", "CustomValue");

// Add it to the packet
packet.addPackage(custom);
```

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```

## บทเรียนที่เกี่ยวข้อง

- [เพิ่มเมตาดาต้า XMP แบบกำหนดเองลงในไฟล์ด้วย GroupDocs.Metadata Java: คู่มือเชิงลึก](/metadata/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/)
- [วิธีเพิ่มเมตาดาต้าใน PDF ด้วย GroupDocs.Metadata สำหรับ Java – คู่มือสำหรับนักพัฒนา](/metadata/java/document-formats/master-pdf-metadata-groupdocs-java/)
- [วิธีดึงเมตาดาต้าแบบกำหนดเองจาก PDF ด้วย GroupDocs.Metadata ใน Java: คู่มือเชิงลึก](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)