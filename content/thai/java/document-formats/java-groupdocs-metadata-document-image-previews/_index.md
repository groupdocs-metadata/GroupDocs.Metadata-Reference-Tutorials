---
date: '2026-02-06'
description: เรียนรู้วิธีสร้างการแสดงตัวอย่างเอกสารด้วย Java และส่งออกหน้าเป็นภาพโดยใช้
  GroupDocs.Metadata คู่มือนี้ครอบคลุมขั้นตอนการตั้งค่า การกำหนดค่า และการดำเนินการ.
keywords:
- document image preview
- GroupDocs Metadata Java
- creating document previews with Java
title: วิธีสร้างการแสดงตัวอย่างเอกสารใน Java ด้วย GroupDocs.Metadata
type: docs
url: /th/java/document-formats/java-groupdocs-metadata-document-image-previews/
weight: 1
---

# การเชี่ยวชาญการแสดงตัวอย่างภาพเอกสารใน Java ด้วย GroupDocs.Metadata

## บทนำ

หากคุณต้องการ **create document preview java** application—ไม่ว่าจะเป็นระบบจัดการเอกสาร, ห้องสมุดดิจิทัล, หรือฟีเจอร์ดูอย่างรวดเร็วในพอร์ทัลองค์กร—GroupDocs.Metadata ทำให้เรื่องนี้ง่ายดาย ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีโหลดเอกสาร, ตั้งค่า preview options, และส่งออกหน้าเป็นไฟล์ภาพ ทั้งหมดด้วยโค้ด Java ที่สะอาดและเข้าใจง่าย  

เราจะเดินผ่านขั้นตอนการทำงานทั้งหมด ตั้งแต่การตั้งค่า Maven จนถึงการสร้าง preview แบบ PNG สำหรับหน้าที่ระบุ พร้อมหรือยังที่จะเห็นเอกสารของคุณกลายเป็นภาพ? ไปกันเลย!

## คำตอบอย่างรวดเร็ว
- **“create document preview java” หมายถึงอะไร?** การสร้างภาพสแนปช็อต (เช่น PNG) ของหน้าต่าง ๆ ของเอกสารด้วยโค้ด Java  
- **ไลบรารีใดรองรับฟีเจอร์นี้โดยตรง?** GroupDocs.Metadata สำหรับ Java  
- **ฉันสามารถเลือกฟอร์แมตของภาพได้หรือไม่?** ได้—preview options ให้คุณเลือก PNG, JPEG, BMP ฯลฯ  
- **ต้องมีลิขสิทธิ์หรือไม่?** ทดลองใช้ฟรีสำหรับการประเมินผล; ต้องซื้อไลเซนส์สำหรับการใช้งานจริง  
- **สามารถ preview เฉพาะหน้าที่เลือกได้หรือไม่?** แน่นอน—ใช้ `setPageNumbers` เพื่อระบุหน้าที่ต้องการ  

## **create document preview java** คืออะไร?
การสร้าง preview ของเอกสารใน Java หมายถึงการเรนเดอร์หนึ่งหรือหลายหน้าของไฟล์ (DOCX, PDF, PPT ฯลฯ) ให้เป็นไฟล์ภาพโดยอัตโนมัติ ซึ่งช่วยให้สร้างแกลเลอรี์รูปย่อ, ตรวจสอบภาพอย่างรวดเร็ว, และผสานรวมกับ UI บนเว็บหรือเดสก์ท็อปได้อย่างราบรื่น  

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับการสร้าง preview?
- **ไม่มีการพึ่งพาไลบรารีภายนอก** – Java แท้, ไม่ต้องใช้ไบนารีเนทีฟ  
- **รองรับไฟล์กว่า 100 รูปแบบ** – ตั้งแต่ Office จนถึง CAD  
- **ควบคุมได้ละเอียด** – เลือกฟอร์แมตภาพ, DPI, และช่วงหน้าได้ตามต้องการ  
- **ประสิทธิภาพสูง** – ปรับให้ทำงานได้ดีกับเอกสารขนาดใหญ่และการประมวลผลเป็นชุด  

## ข้อกำหนดเบื้องต้น

- **ไลบรารีที่ต้องใช้:** GroupDocs.Metadata สำหรับ Java (เวอร์ชันล่าสุด)  
- **ระบบสร้าง:** โปรเจกต์ Maven (หรือเพิ่ม JAR ด้วยตนเอง)  
- **ทักษะที่ต้องมี:** ความคุ้นเคยกับ Java I/O, try‑with‑resources, และการจัดการข้อยกเว้น  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### ข้อมูลการติดตั้ง

เพิ่มรีโพซิทอรีของ GroupDocs และ dependency ลงใน `pom.xml` ของคุณ:

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

**ดาวน์โหลดโดยตรง**  
หรือคุณสามารถดาวน์โหลด JAR ล่าสุดจาก [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) แล้วเพิ่มลงใน classpath ของโปรเจกต์  

### การขอรับไลเซนส์

เริ่มต้นด้วยการทดลองใช้ฟรีหรือขอไลเซนส์ชั่วคราว สำหรับการใช้งานในโปรดักชัน ให้ซื้อไลเซนส์ที่นี่: [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)  

### การเริ่มต้นและตั้งค่าเบื้องต้น

โค้ดสั้น ๆ ด้านล่างแสดงวิธีเปิดเอกสารด้วย GroupDocs.Metadata อย่างน้อยที่สุด:

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;

public class LoadDocument {
    public static void main(String[] args) {
        // Replace with your actual document path
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            System.out.println("Document loaded successfully.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```

## คู่มือการใช้งาน

ต่อไปนี้เป็นการแบ่งโซลูชันออกเป็นสามฟีเจอร์หลัก แต่ละฟีเจอร์มีคำอธิบายสั้น ๆ และโค้ดที่ต้องใช้—ไม่มีโค้ดส่วนเกิน เพียงคัดลอกบล็อกเดิมมาใช้ได้เลย  

### ฟีเจอร์ 1: เริ่มต้น Metadata สำหรับการประมวลผลเอกสาร

**ภาพรวม**  
การโหลดเอกสารเป็นขั้นตอนแรกก่อนที่จะสร้าง preview ใด ๆ  

#### ขั้นตอนที่ 1 – นำเข้าคลาส  

```java
import com.groupdocs.metadata.Metadata;
import java.io.IOException;
```

#### ขั้นตอนที่ 2 – โหลดเอกสาร  

```java
String documentPath = "YOUR_DOCUMENT_DIRECTORY/document.docx";
try (Metadata metadata = new Metadata(documentPath)) {
    System.out.println("Document loaded successfully.");
} catch (IOException e) {
    e.printStackTrace();
}
```

**เคล็ดลับ**  
- ตรวจสอบเส้นทางไฟล์และสิทธิ์การอ่านก่อนรันโค้ด  
- ใช้เส้นทางแบบ absolute ระหว่างการทดสอบเพื่อหลีกเลี่ยงความสับสนของ classpath  

### ฟีเจอร์ 2: สร้าง Preview Options สำหรับหน้าต่าง ๆ ของเอกสาร

**ภาพรวม**  
ตั้งค่าการแสดง preview ว่าจะเป็นอย่างไรและจะเรนเดอร์หน้าใดบ้าง  

#### ขั้นตอนที่ 1 – นำเข้าคลาส Preview  

```java
import com.groupdocs.metadata.options.PreviewFormats;
import com.groupdocs.metadata.options.PreviewOptions;
import java.io.OutputStream;
```

#### ขั้นตอนที่ 2 – ตั้งค่า Preview Options  

```java
OutputStream outputStream = null; // Replace with actual implementation if needed

PreviewOptions previewOptions = new PreviewOptions(outputStream::write);
previewOptions.setPreviewFormat(PreviewFormats.PNG); // Set the format of the preview image
previewOptions.setPageNumbers(new int[]{1}); // Specify page numbers to generate previews for
```

**ทำไมต้องตั้งค่านี้**  
การเลือก `PNG` ให้คุณภาพ lossless ที่เหมาะกับรูปย่อ ปรับ `setPageNumbers` เพื่อ preview ช่วงหน้าที่ต้องการได้ตามใจ  

### ฟีเจอร์ 3: สร้าง Stream ของหน้าเพื่อบันทึกเป็นภาพ

**ภาพรวม**  
แต่ละภาพ preview ต้องถูกเขียนลงไฟล์หรือปลายทางอื่น  

#### ขั้นตอนที่ 1 – นำเข้าคลาส I/O  

```java
import java.io.FileOutputStream;
import java.io.File;
import java.io.OutputStream;
import java.io.IOException;
```

#### ขั้นตอนที่ 2 – สร้าง Stream และบันทึกภาพ  

```java
int pageNumber = 1; // Example page number

try {
    File outputFile = new File(String.format("YOUR_OUTPUT_DIRECTORY/result_%d.png", pageNumber));
    OutputStream stream = new FileOutputStream(outputFile);
    System.out.println("Page stream created for output.");
} catch (IOException e) {
    throw new RuntimeException(e);
}
```

**เคล็ดลับระดับมืออาชีพ:** ตรวจสอบให้แน่ใจว่า `YOUR_OUTPUT_DIRECTORY` มีอยู่แล้ว หรือสร้างโดยโปรแกรมด้วย `outputFile.getParentFile().mkdirs();`  

## วิธี **output page as image** ด้วย GroupDocs.Metadata

โดยการผสาน preview options จากฟีเจอร์ 2 กับ logic ของฟีเจอร์ 3 คุณสามารถเรนเดอร์หน้าใดก็ได้เป็นไฟล์ภาพได้ดังนี้  

1. เริ่มต้น `Metadata` (ฟีเจอร์ 1)  
2. สร้างอินสแตนซ์ `PreviewOptions`, ระบุ `PNG` และหน้าที่ต้องการ  
3. ส่ง lambda ที่เขียนไบต์ของ preview ไปยัง `OutputStream` ที่คุณสร้างในฟีเจอร์ 3  

กระบวนการนี้ทำให้คุณ **output page as image** อย่างมีประสิทธิภาพ แม้กับเอกสารขนาดใหญ่  

## การนำไปใช้ในสถานการณ์จริง

- **ระบบจัดการเอกสาร:** แสดงรูปย่อในไฟล์บราวเซอร์  
- **ห้องสมุดดิจิทัล:** ให้สัญญาณภาพอย่างรวดเร็วสำหรับหนังสือสแกน  
- **กฎหมาย/การเงิน:** ตรวจสอบหน้าในสัญญาอย่างรวดเร็ว  
- **แพลตฟอร์ม CMS:** สร้างภาพ preview อัตโนมัติสำหรับรายงานที่อัปโหลด  
- **E‑Learning:** ให้ผู้เรียนดูตัวอย่างสไลด์ก่อนดาวน์โหลด  

## ข้อควรพิจารณาด้านประสิทธิภาพ

- **จำกัดจำนวนหน้าต่อชุด:** การสร้างหลายหน้าในครั้งเดียวอาจทำให้ใช้หน่วยความจำสูงขึ้น  
- **ใช้ try‑with‑resources:** รับประกันว่า Stream จะถูกปิดอย่างถูกต้อง ป้องกันการรั่วไหล  
- **ตรวจสอบ heap ของ JVM:** PDF ขนาดใหญ่บางไฟล์อาจต้องเพิ่ม heap (`-Xmx`)  

## ปัญหาที่พบบ่อยและวิธีแก้

| Issue | Cause | Fix |
|-------|-------|-----|
| `NullPointerException` on `outputStream` | `outputStream` not initialized | Provide a real `OutputStream` (e.g., `new FileOutputStream(...)`). |
| No preview generated | Wrong page number | Verify the page exists; use `metadata.getPageCount()` to validate. |
| Permission error when writing file | Output directory is read‑only | Grant write permissions or choose a writable folder. |

## คำถามที่พบบ่อย

**Q: สามารถสร้าง preview ให้กับเอกสารที่มีรหัสผ่านได้หรือไม่?**  
A: ได้ เปิดเอกสารด้วยคอนสตรัคเตอร์ที่รับพารามิเตอร์รหัสผ่าน แล้วดำเนินการต่อด้วย preview options  

**Q: รองรับฟอร์แมตภาพใดบ้าง?**  
A: PNG, JPEG, BMP, และ GIF มีให้เลือกผ่าน `PreviewFormats`  

**Q: จะ preview หลายหน้าในคำสั่งเดียวอย่างไร?**  
A: ส่งอาร์เรย์ของหมายเลขหน้าให้ `previewOptions.setPageNumbers(new int[]{1,2,3});`  

**Q: มีวิธีควบคุมความละเอียดของภาพหรือไม่?**  
A: ปรับ DPI ด้วย `previewOptions.setDpi(int dpi)` (ค่าเริ่มต้นคือ 96 DPI)  

**Q: ไลบรารีนี้ทำงานบน Android ได้หรือไม่?**  
A: GroupDocs.Metadata เป็น Java แท้ จึงสามารถใช้บน Android ได้โดยเพิ่ม JAR ที่เหมาะสม แต่การเรนเดอร์ UI ต้องทำด้วยเฟรมเวิร์กของ Android  

## สรุป

คุณมีคู่มือครบถ้วนสำหรับการสร้างโซลูชัน **create document preview java** ที่ **output page as image** ด้วย GroupDocs.Metadata แล้ว โดยทำตามสามขั้นตอนหลัก—เริ่มต้น metadata, ตั้งค่า preview options, และเขียน stream ของภาพ—คุณสามารถผสาน preview คุณภาพสูงเข้าไปในแอปพลิเคชัน Java ใดก็ได้  

---  

**อัปเดตล่าสุด:** 2026-02-06  
**ทดสอบกับ:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs  

---