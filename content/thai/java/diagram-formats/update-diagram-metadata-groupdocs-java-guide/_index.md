---
date: '2026-06-17'
description: เรียนรู้วิธีเปลี่ยนเวลาการสร้างแผนภาพและทำให้การอัปเดต Metadata สำหรับไฟล์แผนภาพเป็นอัตโนมัติด้วย
  GroupDocs.Metadata ใน Java.
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: เปลี่ยนเวลาการสร้างแผนภาพใน Metadata ด้วย GroupDocs Java
type: docs
url: /th/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# เปลี่ยนเวลาการสร้างแผนภาพใน Metadata ด้วย GroupDocs Java

ในบทแนะนำแบบขั้นตอนนี้ คุณจะได้เรียนรู้วิธี **เปลี่ยนเวลาการสร้างแผนภาพ** และอัปเดตคุณสมบัติมาตรฐานอื่น ๆ ของไฟล์แผนภาพโดยใช้ไลบรารี GroupDocs.Metadata สำหรับ Java การทำอัตโนมัติของการเปลี่ยนแปลงเหล่านี้ช่วยประหยัดเวลาการแก้ไขด้วยมือหลายชั่วโมง รับประกันการใช้เวลาตราบเวลาอย่างสม่ำเสมอในคลังของคุณ และทำให้แผนภาพของคุณสามารถค้นหาได้ทันทีในระบบจัดการเอกสารใด ๆ

## คำตอบด่วน
- **เป้าหมายหลักคืออะไร?** เปลี่ยนเวลาการสร้างแผนภาพและเมตาดาต้าอื่น ๆ ในไฟล์แผนภาพ  
- **ไลบรารีใดที่ควรใช้?** GroupDocs.Metadata for Java.  
- **ฉันต้องการใบอนุญาตหรือไม่?** การทดลองใช้ฟรีเพียงพอสำหรับการทดสอบ; จำเป็นต้องมีใบอนุญาตเต็มรูปแบบสำหรับการใช้งานจริง.  
- **ฉันสามารถประมวลผลหลายแผนภาพเป็นชุดได้หรือไม่?** ใช่—ห่อหุ้มตรรกะเดียวกันในลูปหรือสตรีมแบบขนาน.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือสูงกว่า.

## อะไรคือ “การเปลี่ยนเวลาการสร้างแผนภาพ” ในเมตาดาต้าแผนภาพ?
การเปลี่ยนเวลาการสร้างจะเขียนทับเวลาตราบเวลาต้นฉบับที่เก็บอยู่ในไฟล์แผนภาพ (เช่น VDX หรือ VSDX) ด้วยค่า วันที่‑เวลา ใหม่ สิ่งนี้ทำให้คุณสามารถปรับเมตาดาต้าของไฟล์ให้สอดคล้องกับวันที่ประมวลผลหรือเก็บถาวรจริงแทนเวลาตราบเวลาต้นฉบับของผู้เขียน ซึ่งเป็นสิ่งสำคัญสำหรับการตรวจสอบและผลการค้นหาที่แม่นยำ

## ทำไมต้องอัตโนมัติการอัปเดตเมตาดาต้าสำหรับแผนภาพ?
การอัตโนมัติการอัปเดตเมตาดาต้าช่วยให้แผนภาพทุกไฟล์ปฏิบัติตามมาตรฐานการตั้งชื่อ การจัดประเภท และเวลาตราบเวลาเดียวกันโดยไม่มีข้อผิดพลาดจากมนุษย์ นอกจากนี้ยังเร่งการย้ายข้อมูลจำนวนมาก ลดความเสี่ยงด้านการปฏิบัติตามกฎระเบียบ และเพิ่มการค้นพบในแพลตฟอร์ม DMS ขององค์กร—ช่วยประหยัดแรงงานด้วยมือได้ถึง 70 % ในโครงการขนาดใหญ่

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK) 8+** ติดตั้งบนเครื่องของคุณ.  
- **IDE** เช่น IntelliJ IDEA หรือ Eclipse.  
- **Maven** (หรือการจัดการ JAR ด้วยตนเอง) สำหรับการจัดการ dependencies.  
- ความคุ้นเคยพื้นฐานกับคลาส Java, เมธอด, และการจัดการข้อยกเว้น.

### ไลบรารีและ dependencies ที่จำเป็น
เพิ่ม repository และ dependency ต่อไปนี้ในไฟล์ `pom.xml` ของคุณหากใช้ Maven:

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
หากคุณต้องการดาวน์โหลดโดยตรง ให้เยี่ยมชม [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) เพื่อรับเวอร์ชันล่าสุด

### การตั้งค่าสภาพแวดล้อม
- JDK 8 หรือใหม่กว่า.  
- IntelliJ IDEA, Eclipse หรือ IDE ที่รองรับ Java ใด ๆ.  

### ความรู้เบื้องต้นที่จำเป็น
ความเข้าใจในไวยากรณ์ของ Java และการทำ I/O ไฟล์พื้นฐานจะทำให้บทแนะนำนี้ราบรื่นขึ้น แต่ขั้นตอนต่าง ๆ จะอธิบายด้วยภาษาง่าย

## การตั้งค่า GroupDocs.Metadata สำหรับ Java
### คำแนะนำการติดตั้ง
**Maven Users:** โค้ดสแนปด้านบนจะเพิ่ม repository และ JAR ที่จำเป็นโดยอัตโนมัติ.  
**Direct Download Users:** หลังจากดาวน์โหลด JAR จาก [GroupDocs](https://releases.groupdocs.com/metadata/java/), เพิ่มลงใน classpath ของโปรเจคของคุณ.

### การรับใบอนุญาต
- **Free Trial:** ทดลองใช้ไลบรารีโดยไม่มีค่าใช้จ่าย.  
- **Temporary License:** รับใบอนุญาตชั่วคราวสำหรับการทดสอบต่อเนื่อง [here](https://purchase.groupdocs.com/temporary-license/).  
- **Purchase:** ซื้อใบอนุญาตเต็มรูปแบบสำหรับสภาพแวดล้อมการผลิต.

### การเริ่มต้นพื้นฐาน
`Metadata` คือคลาสหลักที่เป็นตัวแทนของคอนเทนเนอร์เมตาดาต้าของเอกสารและให้การเข้าถึงแบบอ่าน/เขียนต่อคุณสมบัติมาตรฐานทั้งหมด เพื่อเริ่มใช้ GroupDocs.Metadata ให้นำเข้าคลาสและเปิดไฟล์แผนภาพ:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```
เมื่อไลบรารีถูกเริ่มต้นแล้ว คุณสามารถแก้ไขคุณสมบัติมาตรฐานใด ๆ ได้ รวมถึงเวลาการสร้าง

## คู่มือการดำเนินการ
### วิธีการเปลี่ยนเวลาการสร้างในไฟล์แผนภาพ
ในส่วนนี้เราจะอธิบายขั้นตอนที่จำเป็นทั้งหมดเพื่อ **เปลี่ยนเวลาการสร้างแผนภาพ** และอัปเดตคุณสมบัติทั่วไปอื่น ๆ เช่น ผู้เขียน, บริษัท, และหมวดหมู่ กระบวนการประกอบด้วยการโหลดแผนภาพด้วย Metadata API, เข้าถึงแพ็กเกจราก, ตั้งค่าฟิลด์ที่ต้องการ, และสุดท้ายบันทึกการเปลี่ยนแปลงลงไฟล์ใหม่ เพื่อให้ไฟล์ต้นฉบับไม่ถูกแก้ไข

#### ขั้นตอนที่ 1: โหลดเอกสารแผนภาพ
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*คำอธิบาย:* ตัวสร้าง `Metadata` รับพาธไปยังไฟล์แผนภาพของคุณ บล็อก try‑with‑resources ทำให้ไฟล์ถูกปิดอย่างถูกต้องหลังจากดำเนินการ

#### ขั้นตอนที่ 2: เข้าถึงแพ็กเกจราก
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*คำอธิบาย:* แพ็กเกจรากให้คุณเข้าถึงฟิลด์เมตาดาต้ามาตรฐานทั้งหมดของแผนภาพโดยตรง

#### ขั้นตอนที่ 3: ตั้งค่าคุณสมบัติผู้สร้าง
```java
root.getDocumentProperties().setCreator("test author");
```  
*คำอธิบาย:* กำหนดชื่อผู้เขียนใหม่ แทนที่ `"test author"` ด้วยผู้สร้างจริง

#### ขั้นตอนที่ 4: เปลี่ยนเวลาการสร้าง
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*คำอธิบาย:* บรรทัดนี้ **เปลี่ยนเวลาการสร้าง** เป็นวันที่และเวลาปัจจุบันของระบบ คุณยังสามารถส่งออบเจกต์ `Date` เฉพาะได้หากต้องการเวลาตราบเวลาที่กำหนดเอง

#### ขั้นตอนที่ 5: กำหนดข้อมูลบริษัท
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*คำอธิบาย:* เก็บชื่อบริษัทที่เชื่อมโยงกับแผนภาพ—มีประโยชน์สำหรับการติดตามในองค์กร

#### ขั้นตอนที่ 6: ตั้งค่าหมวดหมู่เอกสาร
```java
root.getDocumentProperties().setCategory("test category");
```  
*คำอธิบาย:* จัดประเภทไฟล์ ช่วยให้คุณ **อัปเดตหมวดหมู่แผนภาพ** อย่างสม่ำเสมอในคลังของคุณ

#### ขั้นตอนที่ 7: เพิ่มคีย์เวิร์ด
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*คำอธิบาย:* คีย์เวิร์ดช่วยเพิ่มการค้นหา; คุณสามารถระบุคำใดก็ได้ที่เกี่ยวข้องกับเนื้อหาแผนภาพ

#### ขั้นตอนที่ 8: บันทึกการเปลี่ยนแปลง
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*คำอธิบาย:* บันทึกการแก้ไขทั้งหมดลงไฟล์ใหม่ โดยไม่กระทบไฟล์ต้นฉบับ

### ข้อผิดพลาดทั่วไปและการแก้ไขปัญหา
- **File Not Found:** ตรวจสอบพาธอินพุตและให้แน่ใจว่านามสกุลไฟล์ตรงกับรูปแบบจริง.  
- **Access Denied:** ตรวจสอบสิทธิ์การอ่าน/เขียนสำหรับไดเรกทอรีอินพุตและเอาต์พุต.  
- **Invalid Date Format:** ใช้วัตถุ `java.util.Date` หรือ `java.time` ที่เข้ากันได้กับ API.

## การประยุกต์ใช้ในทางปฏิบัติ
1. **การทำอัตโนมัติการเก็บเอกสาร** – เมื่อย้ายแผนภาพเก่าไปยังที่เก็บถาวรโดยอัตโนมัติ **เปลี่ยนเวลาการสร้างแผนภาพ** ให้เป็นวันที่เก็บถาวรและตั้งค่าหมวดหมู่เดียวกัน  
2. **Version Control Integration** – รักษาเวลาตราบเวลาให้สอดคล้องกับคอมมิตของ Git โดยอัปเดตเวลาการสร้างในแต่ละรุ่น  
3. **Enterprise DMS Standardization** – บังคับใช้นโยบายระดับบริษัทสำหรับผู้เขียน, บริษัท, และคีย์เวิร์ดในสินทรัพย์แผนภาพทั้งหมด

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Batch Processing:** ห่อขั้นตอนข้างต้นในลูปเพื่อจัดการหลายสิบไฟล์ในการรันเดียว.  
- **Memory Management:** ปล่อยแต่ละอินสแตนซ์ `Metadata` อย่างทันท่วงที (บล็อก try‑with‑resources ทำเช่นนี้โดยอัตโนมัติ).  
- **Asynchronous Execution:** สำหรับชุดข้อมูลขนาดใหญ่ พิจารณาใช้ `CompletableFuture` เพื่อรันการอัปเดตแบบขนานโดยไม่บล็อกเธรดหลัก.  
- **Quantified Capability:** GroupDocs.Metadata รองรับรูปแบบแผนภาพกว่า 30 แบบและสามารถประมวลผลไฟล์ขนาดสูงสุด 500 MB โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ ทำการอัปเดตภายในต่ำกว่า 200 ms ต่อไฟล์บนฮาร์ดแวร์เซิร์ฟเวอร์ทั่วไป

## สรุป
คุณได้เรียนรู้วิธี **เปลี่ยนเวลาการสร้างแผนภาพ** และอัปเดตคุณสมบัติมีเดต้าอื่น ๆ ของเอกสารแผนภาพโดยใช้ GroupDocs.Metadata ใน Java การทำอัตโนมัติขั้นตอนเหล่านี้ช่วยให้คุณรักษาเอกสารที่สอดคล้อง, ค้นหาได้, และเป็นไปตามข้อกำหนดทั่วทั้งองค์กร

**ขั้นตอนต่อไป**
- ทดลองใช้รูปแบบไฟล์อื่นที่รองรับโดย GroupDocs.Metadata (PDF, DOCX ฯลฯ).  
- ผสานโค้ดเข้ากับ pipeline CI/CD เพื่อบังคับใช้มาตรฐานเมตาดาต้าในทุกการสร้าง  

พร้อมลองใช้งานหรือยัง? ไปที่ [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) และเริ่มทำการอัตโนมัตเมตาดาต้าของคุณวันนี้

---

**อัปเดตล่าสุด:** 2026-06-17  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12  
**ผู้เขียน:** GroupDocs  

## คำถามที่พบบ่อย

**Q:** ฉันสามารถใช้วิธีนี้กับรูปแบบแผนภาพอื่นเช่น VSDX ได้หรือไม่?  
**A:** ใช่, API เดียวกันทำงานกับรูปแบบแผนภาพทั้งหมดที่ GroupDocs.Metadata รองรับ.

**Q:** ฉันต้องการใบอนุญาตสำหรับการสร้างเวอร์ชันพัฒนาไหม?  
**A:** การทดลองใช้ฟรีเพียงพอสำหรับการพัฒนาและทดสอบ; จำเป็นต้องมีใบอนุญาตเต็มรูปแบบสำหรับการใช้งานจริง

**Q:** ฉันจะอัปเดตหลายคุณสมบัติในหนึ่งคำสั่งได้อย่างไร?  
**A:** ตั้งค่าทุกคุณสมบัติบนออบเจกต์ `DocumentProperties` ก่อนเรียก `metadata.save(...)`; ไลบรารีจะเขียนทั้งหมดในครั้งเดียว

**Q:** การเขียนทับไฟล์ต้นฉบับปลอดภัยหรือไม่?  
**A:** แนะนำให้บันทึกเป็นไฟล์ใหม่ (ตามที่แสดง) และแทนที่ไฟล์ต้นฉบับเฉพาะเมื่อยืนยันว่าการอัปเดตสำเร็จ

**Q:** ถ้าฉันต้องการตั้งค่าวันที่สร้างแบบกำหนดเองแทนเวลาปัจจุบันจะทำอย่างไร?  
**A:** สร้างออบเจกต์ `java.util.Date` (หรือ `java.time`) ที่มีเวลาตราบเวลาที่ต้องการและส่งให้ `setTimeCreated`.

## บทแนะนำที่เกี่ยวข้อง
- [วิธีอัปเดตเมตาดาต้าแผนภาพ Java ด้วย GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [วิธีอัปเดตเมตาดาต้าผู้เขียน DXF ด้วย GroupDocs.Metadata สำหรับ Java – คู่มือเต็ม](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [อัตโนมัติการอัปเดตเมตาดาต้า Java ตามวันที่โดยใช้ GroupDocs.Metadata เพื่อการจัดการไฟล์ที่มีประสิทธิภาพ](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)