---
date: '2026-03-20'
description: เรียนรู้วิธีรับจำนวนหน้าของไดอะแกรมและสกัดสถิติข้อความจากไดอะแกรมโดยใช้
  GroupDocs.Metadata สำหรับ Java พร้อมการตั้งค่าแบบขั้นตอนและตัวอย่างโค้ดที่รวมอยู่.
keywords:
- get diagram page count
- extract text statistics diagrams
- GroupDocs.Metadata Java setup
- Java diagram metadata extraction
title: ดึงจำนวนหน้าของ Diagram ด้วย GroupDocs.Metadata สำหรับ Java
type: docs
url: /th/java/diagram-formats/extract-text-statistics-diagrams-groupdocs-metadata-java/
weight: 1
---

# รับจำนวนหน้าของไดอะแกรมโดยใช้ GroupDocs.Metadata สำหรับ Java

ในโครงการซอฟต์แวร์สมัยใหม่ การ **รับจำนวนหน้าของไดอะแกรม** อย่างรวดเร็วสามารถประหยัดเวลาได้มาก—โดยเฉพาะเมื่อคุณต้องสร้างรายงานหรือทำงานอัตโนมัติในสายงานเอกสาร คู่มือฉบับนี้จะแสดงให้คุณเห็นวิธีใช้ GroupDocs.Metadata สำหรับ Java เพื่อดึงจำนวนหน้าและสถิติข้อความที่เป็นประโยชน์อื่น ๆ จากไฟล์ไดอะแกรม เช่น VDX, VSDX และอื่น ๆ

## คำตอบสั้น
- **“รับจำนวนหน้าของไดอะแกรม” หมายถึงอะไร?** จะคืนค่าจำนวนหน้าทั้งหมด (หรือแผ่น) ภายในไฟล์ไดอะแกรม  
- **ไลบรารีที่ให้ฟีเจอร์นี้คืออะไร?** GroupDocs.Metadata สำหรับ Java  
- **ต้องมีลิขสิทธิ์หรือไม่?** สามารถใช้รุ่นทดลองฟรีเพื่อประเมินผล; จำเป็นต้องมีลิขสิทธิ์ถาวรสำหรับการใช้งานในผลิตภัณฑ์  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือสูงกว่า  
- **สามารถประมวลผลหลายไดอะแกรมในลูปได้หรือไม่?** ได้—เพียงแค่สร้างอินสแตนซ์ `Metadata` สำหรับแต่ละไฟล์ภายในลูปของคุณ  

## “รับจำนวนหน้าของไดอะแกรม” คืออะไร?
การรับจำนวนหน้าของไดอะแกรมหมายถึงการสืบค้นเมตาดาต้าของไดอะแกรมเพื่อค้นหาว่าไฟล์มีหน้า (หรือแคนวาส) แยกกันกี่หน้า ข้อมูลนี้เป็นส่วนหนึ่งของสถิติเอกสารที่ GroupDocs.Metadata เปิดเผย

## ทำไมต้องใช้ GroupDocs.Metadata สำหรับ Java?
- **การสกัดข้อมูลที่เร็วและเบา** – ไม่ต้องเรนเดอร์ไดอะแกรมทั้งหมด  
- **รองรับรูปแบบไฟล์หลากหลาย** – ทำงานกับ VDX, VSDX และประเภทไดอะแกรมอื่น ๆ อีกมากมาย  
- **API ที่ง่าย** – เพียงไม่กี่บรรทัดของโค้ดก็สามารถรับจำนวนหน้า, ผู้เขียน, วันที่สร้าง และอื่น ๆ ได้  

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Metadata สำหรับ Java** (เวอร์ชัน 24.12 หรือใหม่กว่า)  
- **JDK 8+** ติดตั้งบนเครื่องของคุณ  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  
- Maven สำหรับจัดการ dependencies  

## การตั้งค่า GroupDocs.Metadata สำหรับ Java

### ใช้ Maven
เพิ่ม repository และ dependency ลงใน `pom.xml` ของคุณตามที่แสดงด้านล่างนี้อย่างแม่นยำ:

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
หากคุณไม่ต้องการใช้ Maven ให้ดาวน์โหลด JAR ล่าสุดจากหน้าปล่อยอย่างเป็นทางการ: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)  

### การรับลิขสิทธิ์
- **รุ่นทดลองฟรี** – ดาวน์โหลดและสำรวจทุกฟีเจอร์โดยไม่มีค่าใช้จ่าย  
- **ลิขสิทธิ์ชั่วคราว** – ขอคีย์ชั่วคราวสำหรับการทดสอบโดยไม่มีข้อจำกัด  
- **ลิขสิทธิ์เต็ม** – ซื้อเพื่อใช้งานในผลิตภัณฑ์โดยไม่จำกัดจำนวน  

## การเริ่มต้นพื้นฐาน

ด้านล่างเป็นโค้ดขั้นต่ำที่จำเป็นสำหรับเริ่มทำงานกับไฟล์ไดอะแกรม โค้ดนี้ **สร้างอ็อบเจกต์ Metadata** ซึ่งเป็นจุดเริ่มต้นสำหรับการดำเนินการต่อไปทั้งหมด รวมถึงการรับจำนวนหน้าของไดอะแกรม

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

## วิธีอ่านสถิติไดอะแกรมด้วย GroupDocs.Metadata Java

เมื่อไลบรารีพร้อมแล้ว เราจะเดินผ่านขั้นตอนที่แม่นยำเพื่อดึงจำนวนหน้าและสถิติอื่น ๆ

### ขั้นตอนที่ 1: รับ Root Package

แต่ละประเภทของไดอะแกรมมี root package เฉพาะที่ให้เข้าถึงเมตาดาต้า ใช้เมธอดทั่วไป `getRootPackageGeneric()` เพื่อดึงมันออกมา

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

### ขั้นตอนที่ 2: เข้าถึง Document Statistics (รับจำนวนหน้าของไดอะแกรม)

เมื่อได้ root package แล้ว คุณสามารถเรียก `getDocumentStatistics()` แล้วตามด้วย `getPageCount()` เพื่อ **รับจำนวนหน้าของไดอะแกรม** ได้

```java
            int pageCount = root.getDocumentStatistics().getPageCount();
            System.out.println("Page Count: " + pageCount);
        }
    }
}
```

**คำอธิบาย**: `getDocumentStatistics()` คืนอ็อบเจกต์ที่เก็บเมตริกที่เป็นประโยชน์หลายอย่าง รวมถึงจำนวนหน้า ตัวแปร `pageCount` จึงเป็นตัวแทนของจำนวนหน้าทั้งหมดในไดอะแกรม  

### ขั้นตอนที่ 3: จัดการข้อยกเว้นอย่างเหมาะสม

การทำงานที่เกี่ยวกับไฟล์อาจล้มเหลวได้หลายสาเหตุ (ไฟล์หาย, รูปแบบไม่รองรับ ฯลฯ) ให้ห่อโค้ดของคุณในบล็อก try‑catch เพื่อแสดงข้อความข้อผิดพลาดที่ชัดเจน

```java
        } catch (Exception e) {
            System.err.println("Error occurred while processing diagram metadata: " + e.getMessage());
        }
    }
}
```

## การประยุกต์ใช้ในเชิงปฏิบัติ

| กรณีการใช้งาน | วิธีที่จำนวนหน้าช่วยได้ |
|----------|--------------------------|
| **การจัดการโครงการ** | ประเมินความพยายามได้อย่างรวดเร็วโดยนับจำนวนหน้าของฟลอว์ชาร์ตหรือไดอะแกรมสถาปัตยกรรม |
| **การรายงานอัตโนมัติ** | สร้างตารางสรุปที่แสดงแต่ละไดอะแกรมและจำนวนหน้าของมันสำหรับการตรวจสอบของผู้มีส่วนได้ส่วนเสีย |
| **การวิเคราะห์ข้อมูล** | ป้อนเมตริกจำนวนหน้าเข้าสู่แดชบอร์ดเพื่อติดตามการเติบโตของเอกสารตามเวลา |

## ข้อควรพิจารณาด้านประสิทธิภาพ

- **การจัดการทรัพยากร**: ใช้ `try‑with‑resources` ของ Java (ตามที่แสดง) เพื่อปิดอ็อบเจกต์ `Metadata` อัตโนมัติและคืนหน่วยความจำ |
- **การประมวลผลเป็นชุด**: เมื่อจัดการไดอะแกรมจำนวนมาก ให้ใช้อินสแตนซ์ `Metadata` เพียงหนึ่งตัวต่อไฟล์และหลีกเลี่ยงการโหลดข้อมูลที่ไม่จำเป็น |

## ปัญหาทั่วไปและวิธีแก้

- **ไฟล์ไม่พบ** – ตรวจสอบ `inputPath` อีกครั้งและยืนยันว่าไฟล์มีอยู่บนดิสก์ |
- **รูปแบบไม่รองรับ** – ยืนยันว่าประเภทไดอะแกรมของคุณ (เช่น VDX) อยู่ในรายการรูปแบบที่รองรับสำหรับเวอร์ชันที่คุณใช้ |
- **ข้อผิดพลาดเรื่องลิขสิทธิ์** – ตรวจสอบให้แน่ใจว่ามีการใช้คีย์ลิขสิทธิ์ทดลองหรือเต็มที่ถูกต้องก่อนสร้างอ็อบเจกต์ `Metadata` |

## คำถามที่พบบ่อย

**ถาม:** ไฟล์รูปแบบใดบ้างที่ GroupDocs.Metadata รองรับสำหรับไดอะแกรม?  
**ตอบ:** รองรับ VDX, VSDX และรูปแบบไดอะแกรมทั่วไปอื่น ๆ ที่ใช้ในองค์กร  

**ถาม:** สามารถใช้ GroupDocs.Metadata กับเอกสารที่ไม่ใช่ไดอะแกรมได้หรือไม่?  
**ตอบ:** ใช่, ไลบรารีทำงานกับ PDF, Word, สเปรดชีต และอื่น ๆ อีกหลายประเภท โดยให้ประสบการณ์การสกัดเมตาดาต้าแบบรวมศูนย์  

**ถาม:** จะจัดการกับรูปแบบไฟล์ที่ไม่รองรับอย่างไร?  
**ตอบ:** ตรวจสอบนามสกุลไฟล์กับรายการที่รองรับในเอกสารประกอบ หากเป็นรูปแบบที่ไม่รู้จัก ให้พิจารณาแปลงเป็นประเภทที่รองรับก่อน  

**ถาม:** มีขีดจำกัดจำนวนไดอะแกรมที่สามารถประมวลผลพร้อมกันได้หรือไม่?  
**ตอบ:** ไม่มีขีดจำกัดที่แน่นอน แต่การประมวลผลชุดขนาดใหญ่มากอาจต้องคำนึงถึงการใช้หน่วยความจำและกลยุทธ์การทำงานหลายเธรด  

**ถาม:** ควรทำอย่างไรหากพบข้อผิดพลาดในการเริ่มต้น?  
**ตอบ:** ตรวจสอบเส้นทางไฟล์อีกครั้ง, ยืนยันว่า JAR ถูกเพิ่มลงใน classpath อย่างถูกต้อง, และยืนยันว่ามีการใช้ลิขสิทธิ์ที่ถูกต้อง (แม้เป็นรุ่นทดลอง)  

## ขั้นตอนต่อไป

- สำรวจสถิติอื่น ๆ เช่น ผู้เขียน, วันที่สร้าง, และคุณสมบัติกำหนดเอง  
- ผสานตรรกะการนับหน้าเข้ากับการสแกนไฟล์ระบบเพื่อประมวลผลโฟลเดอร์ไดอะแกรมทั้งหมด  
- ตรวจสอบเอกสาร API อย่างเป็นทางการเพื่อปรับแต่งขั้นสูงเพิ่มเติม  

## แหล่งข้อมูล
- [Documentation](https://docs.groupdocs.com/metadata/java/)  
- [API Reference](https://reference.groupdocs.com/metadata/java/)  
- [Download](https://releases.groupdocs.com/metadata/java/)  
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)  
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/)  

---

**อัปเดตล่าสุด:** 2026-03-20  
**ทดสอบด้วย:** GroupDocs.Metadata 24.12 for Java  
**ผู้เขียน:** GroupDocs