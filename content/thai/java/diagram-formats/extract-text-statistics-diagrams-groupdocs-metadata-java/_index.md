---
date: '2026-01-13'
description: เรียนรู้วิธีรับจำนวนหน้าของไดอะแกรมและดึงสถิติข้อความจากไดอะแกรมโดยใช้
  GroupDocs.Metadata สำหรับ Java พร้อมการตั้งค่าแบบขั้นตอนและตัวอย่างโค้ดรวมอยู่ด้วย
keywords:
- get diagram page count
- extract text statistics diagrams
- GroupDocs.Metadata Java setup
- Java diagram metadata extraction
title: รับจำนวนหน้าของ Diagram ด้วย GroupDocs.Metadata สำหรับ Java
type: docs
url: /th/java/diagram-formats/extract-text-statistics-diagrams-groupdocs-metadata-java/
weight: 1
---

# รับจำนวนหน้าของแผนภาพโดยใช้ GroupDocs.Metadata สำหรับ Java

ในโครงการซอฟต์แวร์สมัยใหม่ การ **รับจำนวนหน้าของแผนภาพ** อย่างรวดเร็วสามารถประหยัดเวลาได้มาก—โดยเฉพาะเมื่อคุณต้องสร้างรายงานหรือทำงานอัตโนมัติใน pipeline ของเอกสาร ในบทแนะนำนี้ คุณจะได้เรียนรู้วิธีใช้ GroupDocs.Metadata สำหรับ Java เพื่อดึงจำนวนหน้าและสถิติข้อความที่เป็นประโยชน์อื่น ๆ จากไฟล์แผนภาพ เช่น VDX เราจะอธิบายขั้นตอนการตั้งค่าที่จำเป็น แสดงโค้ดที่ต้องใช้อย่างแม่นยำ และพูดถึงสถานการณ์จริงที่ความสามารถนี้โดดเด่น

## คำตอบอย่างรวดเร็ว
- **“รับจำนวนหน้าของแผนภาพ” หมายถึงอะไร?** จะคืนค่าจำนวนหน้าทั้งหมด (หรือแผ่น) ภายในไฟล์แผนภาพ  
- **ไลบรารีใดให้ฟีเจอร์นี้?** GroupDocs.Metadata สำหรับ Java  
- **ต้องใช้ไลเซนส์หรือไม่?** ทดลองใช้ฟรีสำหรับการประเมิน; จำเป็นต้องมีไลเซนส์ถาวรสำหรับการใช้งานในโปรดักชัน  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือสูงกว่า  
- **สามารถประมวลผลหลายแผนภาพในลูปได้หรือไม่?** ได้—เพียงสร้างอินสแตนซ์ `Metadata` สำหรับแต่ละไฟล์ภายในลูปของคุณ  

## “รับจำนวนหน้าของแผนภาพ” คืออะไร?
การรับจำนวนหน้าของแผนภาพหมายถึงการสอบถามเมตาดาต้าของแผนภาพเพื่อค้นหาว่าไฟล์มีหน้า (หรือแคนวาส) แยกกันกี่หน้า ข้อมูลนี้เป็นส่วนหนึ่งของสถิติเอกสารที่ GroupDocs.Metadata เปิดเผย

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java?
- **การสกัดข้อมูลที่เร็วและเบา** – ไม่ต้องเรนเดอร์แผนภาพทั้งหมด  
- **รองรับรูปแบบหลากหลาย** – ทำงานกับ VDX, VSDX และรูปแบบแผนภาพอื่น ๆ มากมาย  
- **API ที่ง่าย** – เพียงไม่กี่บรรทัดของโค้ดคุณก็จะได้จำนวนหน้า, ผู้เขียน, วันที่สร้าง และอื่น ๆ  

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Metadata สำหรับ Java** (เวอร์ชัน 24.12 หรือใหม่กว่า)  
- **JDK 8+** ติดตั้งบนเครื่องของคุณ  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  
- Maven สำหรับการจัดการ dependency  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### ใช้ Maven
เพิ่ม repository และ dependency ลงใน `pom.xml` ของคุณตามที่แสดงด้านล่างนี้อย่างแม่นยำ

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
หากคุณไม่ต้องการใช้ Maven ให้ดาวน์โหลด JAR ล่าสุดจากหน้า release อย่างเป็นทางการ: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### การรับไลเซนส์
- **ทดลองใช้ฟรี** – ดาวน์โหลดและสำรวจทุกฟีเจอร์โดยไม่มีค่าใช้จ่าย  
- **ไลเซนส์ชั่วคราว** – ขอคีย์ชั่วคราวสำหรับการทดสอบโดยไม่มีข้อจำกัด  
- **ไลเซนส์เต็ม** – ซื้อเพื่อใช้งานในโปรดักชันโดยไม่จำกัด  

### การเริ่มต้นพื้นฐาน

ด้านล่างเป็นโค้ดขั้นต่ำที่จำเป็นสำหรับการเริ่มทำงานกับไฟล์แผนภาพ โค้ดนี้ **สร้างอ็อบเจ็กต์ Metadata** ซึ่งเป็นจุดเริ่มต้นสำหรับการดำเนินการต่อทั้งหมด รวมถึงการรับจำนวนหน้าของแผนภาพ

```java
import com.groupdocs.metadata.Metadata;

public class DiagramInitialization {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/input.vdx";
        try (Metadata metadata = new Metadata(inputPath)) {
            System.out.println("GroupDocs.Metadata initialized successfully.");
        }
    }
}
```

## คู่มือการทำงาน – รับจำนวนหน้าของแผนภาพ

เมื่อไลบรารีพร้อมแล้ว ให้ดำเนินตามขั้นตอนต่อไปนี้เพื่อดึงจำนวนหน้า

### ขั้นตอนที่ 1: รับ Root Package

แต่ละประเภทของแผนภาพมี root package เฉพาะที่ให้เข้าถึงเมตาดาต้า ใช้วิธี `getRootPackageGeneric()` เพื่อดึงมันออกมา

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.DiagramRootPackage;

public class DiagramReadDocumentStatistics {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/input.vdx";
        
        try (Metadata metadata = new Metadata(inputPath)) {
            // Obtain the root package for the diagram document type
            DiagramRootPackage root = metadata.getRootPackageGeneric();
```

### ขั้นตอนที่ 2: เข้าถึง Document Statistics (รับจำนวนหน้าของแผนภาพ)

เมื่อได้ root package แล้ว คุณสามารถเรียก `getDocumentStatistics()` แล้วตามด้วย `getPageCount()` เพื่อ **รับจำนวนหน้าของแผนภาพ** ได้

```java
            int pageCount = root.getDocumentStatistics().getPageCount();
            System.out.println("Page Count: " + pageCount);
        }
    }
}
```

**คำอธิบาย**: `getDocumentStatistics()` คืนอ็อบเจ็กต์ที่เก็บเมตริกที่เป็นประโยชน์หลายอย่าง รวมถึงจำนวนหน้า ตัวแปร `pageCount` จึงหมายถึงจำนวนหน้าทั้งหมดในแผนภาพ

### ขั้นตอนที่ 3: จัดการข้อยกเว้นอย่างเหมาะสม

การทำงานกับไฟล์อาจล้มเหลวได้หลายสาเหตุ (ไฟล์หาย, รูปแบบไม่รองรับ ฯลฯ) ให้ห่อโค้ดของคุณในบล็อก try‑catch เพื่อแสดงข้อความข้อผิดพลาดที่ชัดเจน

```java
        } catch (Exception e) {
            System.err.println("Error occurred while processing diagram metadata: " + e.getMessage());
        }
    }
}
```

**เคล็ดลับการแก้ปัญหา**  
- ตรวจสอบให้แน่ใจว่าเส้นทางไฟล์ (`inputPath`) ชี้ไปยังไฟล์แผนภาพที่มีอยู่จริง  
- ยืนยันว่ารูปแบบแผนภาพ (เช่น VDX) ได้รับการสนับสนุนโดยเวอร์ชันปัจจุบันของ GroupDocs.Metadata  
- หากได้รับข้อผิดพลาดเกี่ยวกับไลเซนส์ ให้ตรวจสอบว่ามีการใช้คีย์ทดลองหรือไลเซนส์เต็มที่ถูกต้อง  

## การใช้งานในเชิงปฏิบัติ

| กรณีการใช้งาน | วิธีที่จำนวนหน้าช่วยได้ |
|----------|--------------------------|
| **การจัดการโครงการ** | ประเมินความพยายามอย่างรวดเร็วโดยนับจำนวนหน้าของแผนผังหรือแผนภาพสถาปัตยกรรม |
| **การสร้างรายงานอัตโนมัติ** | สร้างตารางสรุปที่แสดงแผนภาพแต่ละไฟล์พร้อมจำนวนหน้าเพื่อการตรวจสอบของผู้มีส่วนได้ส่วนเสีย |
| **การวิเคราะห์ข้อมูล** | ป้อนเมตริกจำนวนหน้าเข้าสู่แดชบอร์ดเพื่อติดตามการเติบโตของเอกสารตามเวลา |

## พิจารณาด้านประสิทธิภาพ

- **การจัดการทรัพยากร**: ใช้ try‑with‑resources ของ Java (ตามตัวอย่าง) เพื่อปิดอ็อบเจ็กต์ `Metadata` โดยอัตโนมัติและคืนหน่วยความจำ  
- **การประมวลผลเป็นชุด**: เมื่อจัดการหลายแผนภาพ ให้ใช้อินสแตนซ์ `Metadata` เดียวต่อไฟล์และหลีกเลี่ยงการโหลดข้อมูลที่ไม่จำเป็น  

## สรุป

คุณได้เรียนรู้วิธี **รับจำนวนหน้าของแผนภาพ** และดึงสถิติข้อความอื่น ๆ ด้วย GroupDocs.Metadata สำหรับ Java วิธีที่เบานี้สามารถผสานรวมเข้าไปใน pipeline การอัตโนมัติที่ใหญ่ขึ้น, เครื่องมือสร้างรายงาน, หรือแอปพลิเคชันใด ๆ ที่ต้องการข้อมูลเชิงลึกอย่างรวดเร็วเกี่ยวกับไฟล์แผนภาพ

### ขั้นตอนต่อไป
- สำรวจสถิติเพิ่มเติมเช่น ผู้เขียน, วันที่สร้าง, และคุณสมบัติกำหนดเอง  
- ผสานตรรกะการนับหน้าเข้ากับการสแกนระบบไฟล์เพื่อประมวลผลโฟลเดอร์ของแผนภาพทั้งหมด  
- ตรวจสอบแหล่งข้อมูลอย่างเป็นทางการเพื่อเรียนรู้ API อย่างละเอียด  

## ส่วนคำถามที่พบบ่อย (FAQ)

1. **ไฟล์ฟอร์แมตใดบ้างที่ GroupDocs.Metadata รองรับสำหรับแผนภาพ?**  
   - รองรับ VDX, VSDX และรูปแบบแผนภาพทั่วไปอื่น ๆ ที่ใช้ในองค์กร  

2. **ฉันสามารถใช้ GroupDocs.Metadata กับเอกสารที่ไม่ใช่แผนภาพได้หรือไม่?**  
   - ใช่, ไลบรารีทำงานกับ PDF, Word, สเปรดชีต และอื่น ๆ อีกมากมาย ให้ประสบการณ์การสกัดเมตาดาต้าแบบรวมศูนย์  

3. **จะจัดการกับไฟล์ฟอร์แมตที่ไม่รองรับอย่างไร?**  
   - ตรวจสอบนามสกุลไฟล์กับรายการที่สนับสนุนในเอกสาร หากเป็นฟอร์แมตที่ไม่รู้จัก ให้พิจารณาแปลงเป็นฟอร์แมตที่รองรับก่อน  

4. **มีขีดจำกัดจำนวนแผนภาพที่สามารถประมวลผลพร้อมกันหรือไม่?**  
   - ไม่มีขีดจำกัดที่แน่นอน แต่การประมวลผลชุดขนาดใหญ่อาจต้องคำนึงถึงการใช้หน่วยความจำและกลยุทธ์การทำงานหลายเธรด  

5. **จะทำอย่างไรหากพบข้อผิดพลาดในการเริ่มต้น?**  
   - ตรวจสอบเส้นทางไฟล์, ยืนยันว่า JAR ถูกเพิ่มเข้าไปใน classpath อย่างถูกต้อง, และตรวจสอบว่ามีการใช้ไลเซนส์ที่ถูกต้อง (แม้เป็นแบบทดลอง)  

## แหล่งข้อมูล
- [Documentation](https://docs.groupdocs.com/metadata/java/)  
- [API Reference](https://reference.groupdocs.com/metadata/java/)  
- [Download](https://releases.groupdocs.com/metadata/java/)  
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)  
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)  

---

**อัปเดตล่าสุด:** 2026-01-13  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs