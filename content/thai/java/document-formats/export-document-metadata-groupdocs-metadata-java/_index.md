---
date: '2026-06-27'
description: เรียนรู้วิธีส่งออก metadata ไปยัง Excel ด้วย GroupDocs.Metadata ใน Java,
  ดึง metadata จากไฟล์, และสร้าง XML หรือ CSV สำหรับการรายงานตามข้อกำหนด
keywords:
- export metadata excel java
- extract metadata files java
- groupdocs maven dependency
schemas:
- author: GroupDocs
  dateModified: '2026-06-27'
  description: Learn how to export metadata to Excel using GroupDocs.Metadata in Java,
    extract metadata from files, and also generate XML or CSV for compliance reporting.
  headline: Export Metadata Excel Java with GroupDocs.Metadata – A Step‑By‑Step Guide
  type: TechArticle
- description: Learn how to export metadata to Excel using GroupDocs.Metadata in Java,
    extract metadata from files, and also generate XML or CSV for compliance reporting.
  name: Export Metadata Excel Java with GroupDocs.Metadata – A Step‑By‑Step Guide
  steps:
  - name: '**Initialize Metadata Object:** Create a new `Metadata` instance using
      the path of your document.'
    text: '**Initialize Metadata Object:** Create a new `Metadata` instance using
      the path of your document.'
  - name: '**Check for Null:** Verify that the `RootMetadataPackage` is not null to
      avoid exceptions.'
    text: '**Check for Null:** Verify that the `RootMetadataPackage` is not null to
      avoid exceptions.'
  - name: '**Initialize ExportManager:** Set up the manager using the root metadata
      package.'
    text: '**Initialize ExportManager:** Set up the manager using the root metadata
      package.'
  - name: '**Export Metadata:** Use the `export` method to save metadata into an Excel
      file.'
    text: '**Export Metadata:** Use the `export` method to save metadata into an Excel
      file.'
  - name: '**Initialize ExportManager:** Similar to exporting to Excel, initialize
      the manager.'
    text: '**Initialize ExportManager:** Similar to exporting to Excel, initialize
      the manager.'
  - name: '**Export Metadata:** Call the `export` method to save metadata as an XML
      file.'
    text: '**Export Metadata:** Call the `export` method to save metadata as an XML
      file.'
  - name: '**Initialize ExportManager:** Set up the manager with your root package.'
    text: '**Initialize ExportManager:** Set up the manager with your root package.'
  - name: '**Export Metadata:** Use the `export` method to generate a CSV file.'
    text: '**Export Metadata:** Use the `export` method to generate a CSV file.'
  - name: '**Digital Asset Management:** Export metadata to Excel for fast categorization,
      tagging, and bulk updates of media libraries.'
    text: '**Digital Asset Management:** Export metadata to Excel for fast categorization,
      tagging, and bulk updates of media libraries.'
  - name: '**Regulatory Audits:** Generate XML reports that align with industry‑standard
      schemas, ensuring you meet GDPR, HIPAA, or SOX requirements.'
    text: '**Regulatory Audits:** Generate XML reports that align with industry‑standard
      schemas, ensuring you meet GDPR, HIPAA, or SOX requirements.'
  type: HowTo
- questions:
  - answer: It creates a structured spreadsheet that can be filtered, sorted, and
      shared with business users for reporting or compliance checks.
    question: What does “export metadata to excel” achieve?
  - answer: GroupDocs.Metadata also supports XML and CSV exports, giving you flexible
      options for data interchange.
    question: Which formats can I export besides Excel?
  - answer: Yes – a free 30‑day trial or a temporary license provides full feature
      access without restrictions.
    question: Do I need a license to try this out?
  - answer: JDK 8 or higher; the library is fully compatible with Java 11, 17, and
      newer LTS releases.
    question: What Java version is required?
  - answer: Absolutely – combine try‑with‑resources with batch or parallel processing
      to handle high‑volume scenarios efficiently.
    question: Can I process many documents at once?
  type: FAQPage
title: ส่งออก Metadata ไปยัง Excel ด้วย Java และ GroupDocs.Metadata – คู่มือขั้นตอนโดยละเอียด
type: docs
url: /th/java/document-formats/export-document-metadata-groupdocs-metadata-java/
weight: 1
---

# ส่งออก Metadata Excel Java ด้วย GroupDocs.Metadata – คู่มือขั้นตอนต่อขั้นตอน

ในแอปพลิเคชันองค์กรสมัยใหม่, **export metadata excel java** เป็นความสามารถหลักที่ช่วยให้คุณแปลงคุณสมบัติเบื้องหลังของเอกสารให้เป็นสเปรดชีตที่สามารถค้นหาได้ ไม่ว่าคุณจะต้องตรวจสอบสัญญานับพัน, ป้อนข้อมูลลงในคลังข้อมูล, หรือเพียงแค่ให้ผู้ใช้ธุรกิจมองเห็นคุณลักษณะของไฟล์อย่างเป็นระเบียบ คู่มือนี้จะแสดงให้คุณเห็นอย่างชัดเจนว่าต้องอ่าน metadata ของเอกสารด้วย GroupDocs.Metadata และส่งออกเป็น Excel, XML หรือ CSV ด้วย Java.

## คำตอบอย่างรวดเร็ว
- **“export metadata to excel” ทำอะไรได้บ้าง?**  
  มันสร้างสเปรดชีตที่มีโครงสร้างซึ่งสามารถกรอง, เรียงลำดับ, และแชร์กับผู้ใช้ธุรกิจเพื่อการรายงานหรือการตรวจสอบความสอดคล้องได้.  
- **นอกจาก Excel แล้วฉันสามารถส่งออกเป็นรูปแบบใดได้บ้าง?**  
  GroupDocs.Metadata ยังรองรับการส่งออกเป็น XML และ CSV ให้คุณมีตัวเลือกที่ยืดหยุ่นสำหรับการแลกเปลี่ยนข้อมูล.  
- **ฉันต้องมีลิขสิทธิ์เพื่อทดลองใช้งานหรือไม่?**  
  ใช่ – การทดลองใช้ฟรี 30 วันหรือใบอนุญาตชั่วคราวจะให้การเข้าถึงคุณสมบัติทั้งหมดโดยไม่มีข้อจำกัด.  
- **ต้องการเวอร์ชัน Java ใด?**  
  JDK 8 หรือสูงกว่า; ไลบรารีนี้เข้ากันได้เต็มที่กับ Java 11, 17, และรุ่น LTS ใหม่ ๆ  
- **ฉันสามารถประมวลผลหลายเอกสารพร้อมกันได้หรือไม่?**  
  แน่นอน – ผสานการใช้ try‑with‑resources กับการประมวลผลแบบแบตช์หรือขนานเพื่อจัดการกับสถานการณ์ปริมาณสูงอย่างมีประสิทธิภาพ.

## สิ่งที่คุณจะได้เรียนรู้
- โหลดและเริ่มต้น metadata ของเอกสารโดยใช้ GroupDocs.Metadata  
- ส่งออก metadata ไปยังไฟล์ Excel, XML, และ CSV  
- ตัวอย่างการใช้งานจริงของ **extract metadata from files** สำหรับการรายงานการปฏิบัติตามข้อกำหนด  
- เคล็ดลับที่มุ่งเน้นประสิทธิภาพสำหรับนักพัฒนา Java ที่จัดการชุดเอกสารขนาดใหญ่  
- กรณีการใช้งานจริงเช่นการจัดการสินทรัพย์ดิจิทัล, ร่องรอยการตรวจสอบ, และการย้ายข้อมูล  

## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่ม, ตรวจสอบให้แน่ใจว่าคุณมี:
- **Java Development Kit (JDK):** เวอร์ชัน 8 หรือสูงกว่า.  
- **GroupDocs.Metadata Library:** เพิ่มผ่าน Maven หรือดาวน์โหลดไฟล์ JAR โดยตรง.  
- **IDE:** IntelliJ IDEA, Eclipse, NetBeans, หรือเครื่องมือแก้ไขใด ๆ ที่คุณชอบ.

### ไลบรารีและการพึ่งพาที่จำเป็น
สำหรับการรวมเข้ากับ GroupDocs.Metadata อย่างราบรื่น:

#### การตั้งค่า Maven
เพิ่มการกำหนดค่าต่อไปนี้ในไฟล์ `pom.xml` ของคุณ:

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

#### ดาวน์โหลดโดยตรง
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดโดยตรงจาก [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### การรับลิขสิทธิ์
เพื่อใช้ GroupDocs.Metadata อย่างเต็มที่:
- **Free Trial:** เข้าถึงคุณสมบัติทั้งหมดในช่วงทดลองใช้ 30 วัน.  
- **Temporary License:** รับใบอนุญาตชั่วคราวเพื่อทดสอบผลิตภัณฑ์โดยไม่มีข้อจำกัด.  
- **Purchase License:** สำหรับการใช้งานระยะยาวและการสนับสนุนระดับองค์กร.  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java
เริ่มต้นด้วยการเพิ่มการพึ่งพาที่จำเป็น เมื่อตั้งค่าเสร็จแล้ว, เริ่มต้นโปรเจกต์ของคุณ:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataSetup {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY";
        try (Metadata metadata = new Metadata(documentPath)) {
            // Basic initialization complete
        }
    }
}
```

## คู่มือการดำเนินการ
เราจะแบ่งการดำเนินการออกเป็นฟีเจอร์เฉพาะเพื่อความชัดเจน.

### การโหลดและการเริ่มต้น Metadata
**ภาพรวม:**  
ขั้นตอนแรกคือการโหลด metadata ของเอกสารของคุณเพื่อให้คุณสามารถ **read document metadata java** แบบและจัดการได้.

**คำนิยาม:**  
คลาส `Metadata` เป็นจุดเริ่มต้นของ GroupDocs.Metadata ที่แสดงแพ็กเกจ metadata ของไฟล์เดียวในหน่วยความจำ.

**ขั้นตอน:**
1. **Initialize Metadata Object:** สร้างอินสแตนซ์ `Metadata` ใหม่โดยใช้เส้นทางของเอกสารของคุณ.

    ```java
    import com.groupdocs.metadata.Metadata;
    import com.groupdocs.metadata.core.RootMetadataPackage;

    String documentPath = "YOUR_DOCUMENT_DIRECTORY";
    try (Metadata metadata = new Metadata(documentPath)) {
        RootMetadataPackage root = metadata.getRootPackage();
        if (root != null) {
            // Proceed with further operations...
        }
    }
    ```

2. **Check for Null:** ตรวจสอบว่า `RootMetadataPackage` ไม่เป็น null เพื่อหลีกเลี่ยงข้อยกเว้น.

### การส่งออก Metadata ไปยัง Excel
**ภาพรวม:**  
ส่งออก metadata ของเอกสารของคุณเป็นไฟล์ Excel เพื่อฟังก์ชันเช่นการเรียงลำดับ, การกรอง, และการวิเคราะห์ตาราง Pivot—เหมาะสำหรับการรายงาน **metadata export for compliance**.

**คำนิยาม:**  
`ExportManager` เป็นคลาสยูทิลิตี้ที่จัดการการแปลง `RootMetadataPackage` ไปยังรูปแบบผลลัพธ์ต่าง ๆ เช่น XLSX, XML, หรือ CSV.  
RootMetadataPackage แสดงถึงการรวบรวมแบบลำดับชั้นของคุณสมบัติ metadata ที่สกัดจากเอกสาร.  
ExportFormat เป็น enumeration ที่กำหนดประเภทผลลัพธ์ที่รองรับเช่น XLSX, XML, และ CSV.

**วิธีการส่งออก Metadata ไปยัง Excel ด้วย Java?**  
โหลดเอกสารด้วย `new Metadata("file.docx")`, รับแพ็กเกจรากของมัน, สร้างอินสแตนซ์ `ExportManager` ด้วยแพ็กเกจนั้น, แล้วเรียก `export` โดยระบุ `ExportFormat.XLSX`. กระบวนการสามขั้นตอนนี้จะเขียนสเปรดชีตที่จัดรูปแบบเต็มที่ซึ่งรักษาชื่อคุณสมบัติ, ค่า, และประเภทข้อมูล, พร้อมสำหรับการวิเคราะห์ทันที.

**ขั้นตอน:**
1. **Initialize ExportManager:** ตั้งค่าผู้จัดการโดยใช้แพ็กเกจ metadata ราก.

    ```java
    import com.groupdocs.metadata.export.ExportManager;
    import com.groupdocs.metadata.export.ExportFormat;

    String outputPathXls = "YOUR_OUTPUT_DIRECTORY/output.xls";
    if (root != null) {
        ExportManager manager = new ExportManager(root);
        manager.export(outputPathXls, ExportFormat.Xls);
    }
    ```

2. **Export Metadata:** ใช้เมธอด `export` เพื่อบันทึก metadata ลงในไฟล์ Excel.

### การส่งออก Metadata ไปยัง XML
**ภาพรวม:**  
XML เหมาะสำหรับการแลกเปลี่ยนข้อมูล; ขั้นตอนนี้แสดงวิธี **export metadata to xml** สำหรับระบบ downstream ที่ใช้ markup ที่มีโครงสร้าง.

**วิธีการส่งออก Metadata ไปยัง XML ด้วย Java?**  
สร้าง `ExportManager` ด้วยแพ็กเกจราก, จากนั้นเรียก `export` ด้วย `ExportFormat.XML`. ไฟล์ XML ที่ได้จะมีการแสดงผลแบบลำดับชั้นของคุณสมบัติมาตรฐานและกำหนดเองทั้งหมด, ทำให้การรวมกับเว็บเซอร์วิสหรือระบบเก่าเป็นเรื่องง่าย.

**ขั้นตอน:**
1. **Initialize ExportManager:** คล้ายกับการส่งออกไปยัง Excel, เริ่มต้นผู้จัดการ.

    ```java
    String outputPathXml = "YOUR_OUTPUT_DIRECTORY/output.xml";
    if (root != null) {
        ExportManager manager = new ExportManager(root);
        manager.export(outputPathXml, ExportFormat.Xml);
    }
    ```

2. **Export Metadata:** เรียกเมธอด `export` เพื่อบันทึก metadata เป็นไฟล์ XML.

### การส่งออก Metadata ไปยัง CSV
**ภาพรวม:**  
ไฟล์ CSV เหมาะสำหรับการวิเคราะห์อย่างรวดเร็วและสามารถนำเข้าไปยังเครื่องมือ BI — นี้แสดงวิธี **export metadata to csv** สำหรับการรายงานที่เบา.

**วิธีการส่งออก Metadata ไปยัง CSV ด้วย Java?**  
สร้างอินสแตนซ์ `ExportManager` ด้วยแพ็กเกจราก, จากนั้นเรียก `export` ด้วย `ExportFormat.CSV`. ผลลัพธ์ CSV จะทำให้ metadata แบนเป็นแถวของคู่ “Property, Value”, ทำให้โหลดเข้าสเปรดชีตหรือเครื่องมือ pipeline อย่างรวดเร็ว.

**ขั้นตอน:**
1. **Initialize ExportManager:** ตั้งค่าผู้จัดการด้วยแพ็กเกจรากของคุณ.

    ```java
    String outputPathCsv = "YOUR_OUTPUT_DIRECTORY/output.csv";
    if (root != null) {
        ExportManager manager = new ExportManager(root);
        manager.export(outputPathCsv, ExportFormat.Csv);
    }
    ```

2. **Export Metadata:** ใช้เมธอด `export` เพื่อสร้างไฟล์ CSV.

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับการส่งออก Metadata?
GroupDocs.Metadata รองรับ **70+ รูปแบบการนำเข้าและส่งออก**, รวมถึง DOCX, XLSX, PPTX, PDF, และรูปภาพกว่า 30 ประเภท. มันสามารถประมวลผลไฟล์ได้ถึง **2 GB** โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ, ให้ **ลดการใช้ CPU ลง 30 %** เมื่อเทียบกับพาร์เซอร์ทั่วไป. ความสามารถที่วัดได้เหล่านี้ทำให้เป็นตัวเลือกที่เชื่อถือได้สำหรับโครงการปฏิบัติตามข้อกำหนดในระดับใหญ่.

## การประยุกต์ใช้งานจริง
ต่อไปนี้เป็นสถานการณ์จริงที่ **metadata export for compliance** และ **extract metadata from files** มีประโยชน์:
1. **Digital Asset Management:** ส่งออก metadata ไปยัง Excel เพื่อการจัดประเภท, การแท็ก, และการอัปเดตเป็นกลุ่มของไลบรารีสื่ออย่างรวดเร็ว.  
2. **Regulatory Audits:** สร้างรายงาน XML ที่สอดคล้องกับสคีมามาตรฐานอุตสาหกรรม, เพื่อให้คุณปฏิบัติตามข้อกำหนด GDPR, HIPAA, หรือ SOX.  
3. **Data Migration Projects:** รักษาคุณสมบัติของไฟล์ต้นฉบับเมื่อย้ายเนื้อหาระหว่างระบบจัดการเนื้อหา, ลดความเสี่ยงของการสูญเสียข้อมูล.

## พิจารณาประสิทธิภาพ
เพื่อเพิ่มประสิทธิภาพเมื่อทำงานกับ GroupDocs.Metadata ใน Java:
- **การจัดการหน่วยความจำอย่างมีประสิทธิภาพ:** ใช้ try‑with‑resources (ตามที่แสดง) เพื่อปิดทรัพยากรโดยอัตโนมัติและปล่อยหน่วยความจำ.  
- **การประมวลผลแบบแบตช์:** ประมวลผลคอลเลกชันเอกสารขนาดใหญ่เป็นชิ้นส่วนแทนการโหลดทั้งหมดพร้อมกัน.  
- **การประมวลผลแบบขนาน:** ใช้ `ExecutorService` ของ Java เพื่อจัดการหลายไฟล์พร้อมกัน, ทำให้เร็วขึ้นถึง 2× บนเซิร์ฟเวอร์หลายคอร์.

## สรุป
บทแนะนำนี้ได้สำรวจวิธีใช้ไลบรารี GroupDocs.Metadata สำหรับ Java เพื่อ **export metadata to excel**, รวมถึง XML และ CSV, และวิธี **read document metadata java** สำหรับการปฏิบัติตามข้อกำหนดและการวิเคราะห์. ด้วยการทำตามขั้นตอนเหล่านี้, คุณสามารถจัดการและใช้ประโยชน์จาก metadata ของเอกสารได้อย่างมีประสิทธิภาพในแอปพลิเคชันจริง, ตั้งแต่ร่องรอยการตรวจสอบจนถึงการนำเข้าข้อมูลในคลังข้อมูล.

**ขั้นตอนต่อไป:**
- ทดลองกับประเภทไฟล์ต่าง ๆ และสำรวจฟีเจอร์เพิ่มเติมเช่นการจัดการคุณสมบัติกำหนดเองและการสนับสนุนการเข้ารหัส.  
- เข้าร่วม [GroupDocs forum](https://forum.groupdocs.com/c/metadata/) เพื่อเชื่อมต่อกับผู้ใช้คนอื่นและแบ่งปันข้อมูลเชิงลึก.  

## ส่วนคำถามที่พบบ่อย
1. **GroupDocs.Metadata คืออะไร?**  
   GroupDocs.Metadata เป็นไลบรารี Java ที่ให้การเข้าถึง metadata อย่างโปรแกรมเมติกสำหรับเอกสารกว่า 70 รูปแบบ, รองรับการอ่าน, เขียน, และส่งออก.  
2. **ฉันสามารถส่งออก metadata จากรูปแบบเอกสารใดก็ได้หรือไม่?**  
   ได้, ไลบรารีนี้รองรับรูปแบบหลากหลายรวมถึง Word, Excel, PowerPoint, PDF, รูปภาพ, และหลายประเภทของไฟล์บีบอัด.  
3. **ฉันจะจัดการกับปริมาณเอกสารจำนวนมากอย่างไร?**  
   ใช้การประมวลผลแบบแบตช์หรือการทำงานขนานโดยใช้ยูทิลิตี้ความพร้อมของ Java; นี้จะลดเวลาการประมวลผลโดยรวมและรักษาการใช้หน่วยความจำให้ต่ำ.  
4. **มีเอกสารสำหรับฟีเจอร์ขั้นสูงหรือไม่?**  
   มี, เอกสาร API รายละเอียดสามารถพบได้ที่ [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/).  
5. **ฉันจะขอรับการสนับสนุนหากพบปัญหาได้จากที่ไหน?**  
   เยี่ยมชม [free support forum](https://forum.groupdocs.com/c/metadata/) เพื่อรับความช่วยเหลือจากผู้เชี่ยวชาญของ GroupDocs และชุมชน.  

## คำถามที่พบบ่อย
**Q:** *ฉันสามารถใช้วิธีนี้ในแอปพลิเคชัน Spring Boot ได้หรือไม่?*  
**A:** แน่นอน. เพิ่ม dependency ของ Maven ไปใน `pom.xml`, ฉีด `Metadata` service เป็น Spring bean, และเรียกเมธอด export จากคอนโทรลเลอร์หรือชั้นบริการใดก็ได้.

**Q:** *ถ้าเอกสารของฉันถูกป้องกันด้วยรหัสผ่านจะทำอย่างไร?*  
**A:** ส่งรหัสผ่านไปยังคอนสตรัคเตอร์ `Metadata`; ไลบรารีจะถอดรหัสไฟล์ก่อนดึง metadata, รักษาการปฏิบัติตามความปลอดภัย.

**Q:** *มีขีดจำกัดขนาดของเอกสารที่ฉันสามารถประมวลผลได้หรือไม่?*  
**A:** ไลบรารีสามารถจัดการไฟล์ขนาดใหญ่ถึง 2 GB, แต่คุณควรตรวจสอบการใช้ heap ของ JVM และพิจารณาการสตรีมไบต์ขนาดใหญ่เพื่อหลีกเลี่ยงข้อผิดพลาด OutOfMemory.

**Q:** *ฉันจะรวมฟิลด์ metadata กำหนดเองในการส่งออกอย่างไร?*  
**A:** ใช้ API ของ `RootMetadataPackage` เพื่อแสดงรายการคุณสมบัติกำหนดเอง; พวกมันจะถูกเพิ่มโดยอัตโนมัติในผลลัพธ์ Excel, XML, หรือ CSV โดยไม่ต้องตั้งค่าเพิ่มเติม.

**Q:** *GroupDocs.Metadata ทำงานบนคอนเทนเนอร์ Linux หรือไม่?*  
**A:** ใช่, ไลบรารีเป็นแบบ platform‑agnostic และทำงานได้อย่างราบรื่นภายในคอนเทนเนอร์ Docker บน Linux, Windows, หรือ macOS.

## แหล่งข้อมูล
- **Documentation:** [GroupDocs.Metadata Java Docs](https://docs.groupdocs.com/metadata/java/)  
- **API Reference:** [Java API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Download:** [Latest Release](https://releases.groupdocs.com/metadata/java/)  
- **GitHub Repository:** [GroupDocs.Metadata for Java on GitHub](https://github.com/groupdocs-metadata)

---

**อัปเดตล่าสุด:** 2026-06-27  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12  
**ผู้เขียน:** GroupDocs  

## บทเรียนที่เกี่ยวข้อง
- [ส่งออก Metadata ไปยัง CSV ใน Java ด้วย GroupDocs.Metadata: คู่มือครบถ้วน](/metadata/java/working-with-metadata/export-metadata-csv-groupdocs-metadata-java/)
- [เข้าถึง Metadata ของเอกสาร Word ด้วย GroupDocs ใน Java: คู่มือเชิงลึก](/metadata/java/document-formats/access-word-metadata-groupdocs-java/)
- [วิธีดึง Metadata กำหนดเองจาก PDF ด้วย GroupDocs.Metadata ใน Java: คู่มือเชิงลึก](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)