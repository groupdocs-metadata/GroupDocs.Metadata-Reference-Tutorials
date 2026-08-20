---
date: '2026-08-20'
description: تعلم كيفية استخراج XMP metadata في Java باستخدام GroupDocs.Metadata.
  يوضح هذا الدليل كيفية استخراج basic و Dublin Core و Photoshop XMP metadata.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: تعلم كيفية استخراج XMP metadata في Java باستخدام GroupDocs.Metadata.
  يغطي هذا البرنامج التعليمي استخراج basic و Dublin Core و Photoshop XMP مع أمثلة
  عملية على الشيفرة.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: كيفية استخراج XMP metadata باستخدام GroupDocs.Metadata للغة Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: كيفية استخراج XMP metadata باستخدام GroupDocs.Metadata للغة Java
type: docs
url: /ar/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# كيفية استخراج بيانات XMP الوصفية باستخدام GroupDocs.Metadata للغة Java

في سير العمل الرقمي الحديث، يمكن أن يجعل **كيفية استخراج XMP** الوصفية بسرعة وموثوقية الفرق بين مكتبة أصول قابلة للبحث ومخزن ملفات فوضوي. يشرح هذا البرنامج التعليمي كل خطوة — إعداد المكتبة، تحميل الملفات، واستخراج حزم XMP الأساسية، Dublin Core، والخاصة بـ Photoshop — حتى تتمكن من دمج البيانات الوصفية الغنية في تطبيقات Java الخاصة بك اليوم.

## إجابات سريعة
- **أي مكتبة تتعامل مع XMP في Java؟** GroupDocs.Metadata for Java.
- **الحد الأدنى لإصدار Java؟** JDK 8 أو أحدث.
- **هل يمكنني قراءة ملفات PNG و JPEG؟** نعم، كلاهما مدعومان مباشرة.
- **هل يلزم ترخيص للإنتاج؟** نعم، يلزم ترخيص كامل أو مؤقت.
- **أين يمكنني العثور على مرجع API؟** على موقع توثيق GroupDocs.Metadata الرسمي.

## ما هو XMP metadata؟
XMP (Extensible Metadata Platform) هو تنسيق معيار ISO لتضمين البيانات الوصفية المهيكلة مباشرة داخل ملفات الوسائط. يتيح التوافق بين التطبيقات وتخزين البيانات بشكل دائم دون تعديل المحتوى الأصلي. من خلال تخزين معلومات مثل المُنشئ، حقوق النشر، إعدادات الكاميرا، والوسوم المخصصة داخل الملف، يضمن XMP أن البيانات الوصفية تسافر مع الأصل أينما ذهب، مما يبسط الفهرسة والبحث عبر أنظمة متنوعة.

## لماذا تستخدم GroupDocs.Metadata للغة Java؟
يدعم GroupDocs.Metadata **أكثر من 30 تنسيق ملف** (بما في ذلك PNG، JPEG، TIFF، و PSD) ويمكنه معالجة ملفات تصل إلى **2 GB** دون تحميل المستند بالكامل في الذاكرة، مما يحقق **خفضًا بنسبة 30 % في استهلاك المعالج** مقارنةً بالمحللات العامة. هذا يجعله مثاليًا لأنظمة إدارة الأصول الرقمية (DAM) على نطاق واسع.

## المتطلبات المسبقة

- **Java Development Kit (JDK) 8+** مثبت.
- **Maven** لإدارة التبعيات.
- إلمام أساسي بـ Java I/O والبرمجة الكائنية.

## كيفية إعداد GroupDocs.Metadata للغة Java؟
للبدء، أضف مستودع GroupDocs واعتماد المكتبة إلى ملف Maven `pom.xml`. يضمن ذلك أن Maven يستطيع حل القطع الفنية وتحديثها تلقائيًا، مما يبسط الترقيات المستقبلية وتصحيحات الأمان. بعد تحديث `pom.xml`، شغّل `mvn clean install` لتنزيل ملفات JAR المطلوبة والتحقق من نجاح الإعداد.

```xml
<!-- ```xml
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
``` -->
```

إذا كنت تفضل طريقة يدوية، قم بتنزيل أحدث JAR من صفحة الإصدارات الرسمية:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### الحصول على الترخيص
- **تجربة مجانية** – تقييم جميع الميزات لمدة 30 يومًا.
- **ترخيص مؤقت** – الاستخدام أثناء التطوير دون قيود.
- **ترخيص كامل** – مطلوب لنشر الإنتاج.

## التهيئة الأساسية

`Metadata` هو نقطة الدخول لجميع العمليات. يمثل ملفًا واحدًا ويوفر الوصول إلى حزم XMP المدمجة.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## كيفية استخراج بيانات XMP الأساسية؟

حمّل الصورة، افتح حزمة XMP الخاصة بها، واقرأ الخصائص الشائعة مثل أداة الإنشاء والطوابع الزمنية.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## كيفية استخراج بيانات XMP وفقًا لمخطط Dublin Core؟

يخزن مخطط Dublin Core عناصر وصفية موحدة مثل العنوان، المُنشئ، والموضوع. يمكن الوصول إليه عبر الفئة `DublinCorePackage`.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## كيفية استخراج بيانات XMP الخاصة بـ Photoshop؟

يقوم Photoshop بتضمين معلومات إضافية مثل وضع اللون، الدقة، وعدد الطبقات. استرجع هذه القيم عبر `PhotoshopPackage`.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## التطبيقات العملية

- **إدارة الأصول الرقمية** – وضع وسوم والبحث عن الصور حسب المُنشئ، حقوق النشر، أو إعدادات الكاميرا.
- **خطوط النشر الآلية** – حقن أو تعديل XMP قبل النشر في معارض الويب.
- **التحليلات** – تجميع البيانات الوصفية عبر آلاف الملفات لاكتشاف اتجاهات الاستخدام.

## اعتبارات الأداء

توفر الفئة `Metadata` الوصول إلى بيانات الوصفية للملف وحزم XMP. حرّر كائنات `Metadata` بمجرد الانتهاء من القراءة لتحرير الموارد الأصلية. يحدد `LoadOptions.LAZY` للمكتبة تحميل البيانات الوصفية بشكل كسول، مما يقلل من استهلاك الذاكرة. قم ببث الملفات الكبيرة باستخدام `Metadata.load(InputStream)` للحفاظ على انخفاض استهلاك الكومة. أعد استخدام نسخة واحدة من `Metadata` عند قراءة العديد من الملفات الصغيرة لتقليل عبء إنشاء الكائنات.

## المشكلات الشائعة واستكشاف الأخطاء

| العَرَض | السبب المحتمل | الحل |
|---|---|---|
| `NullPointerException` عند الوصول إلى XMP | الملف لا يحتوي على حزمة XMP | استدعِ `metadata.getXmpPackage()` وتحقق من كون النتيجة `null` قبل القراءة. تُعيد طريقة `getXmpPackage()` كائن حزمة XMP، أو `null` إذا لم توجد. |
| معالجة بطيئة على صور بحجم 500 MB | تحميل الملف بالكامل إلى الذاكرة | استخدم `metadata.load(InputStream)` وفعل `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| حقول Photoshop مفقودة | تم حفظ الصورة دون معلومات طبقات Photoshop | تحقق من أن الملف المصدر تم تصديره من Photoshop مع تمكين “Save XMP”. |

## الأسئلة المتكررة

**س: هل يمكنني استخراج XMP من ملفات PDF؟**  
ج: نعم، يدعم GroupDocs.Metadata حزم XMP لملفات PDF عبر نفس واجهة برمجة `Metadata` API.

**س: ماذا يحدث إذا لم يكن تنسيق الملف مدعومًا؟**  
ج: تقوم المكتبة برمي استثناء `UnsupportedFormatException`؛ امسك به واستخدم معالجًا عامًا كبديل.

**س: هل يمكن تعديل بيانات XMP الوصفية وحفظها مرة أخرى؟**  
ج: بالتأكيد. بعد تعديل الخصائص، استدعِ `metadata.save("output.png")` لحفظ التحديثات.

**س: هل تعمل المكتبة على Android؟**  
ج: مكتبة Java الأساسية متوافقة مع Android API 24+، ولكن يجب تضمين القطعة الخاصة بـ `android`.

**س: كيف أتعامل مع الصور المشفرة؟**  
ج: قدم كلمة مرور فك التشفير إلى مُنشئ `Metadata`: `new Metadata(filePath, "password")`.

## الخلاصة

أصبح لديك الآن دليل كامل وجاهز للإنتاج حول **كيفية استخراج XMP** باستخدام GroupDocs.Metadata للغة Java. باتباع الخطوات أعلاه، يمكنك إثراء تطبيقاتك ببيانات وصفية قابلة للبحث ومتوافقة مع المعايير، وإطلاق قدرات قوية لإدارة الأصول.

## الخطوات التالية

تعمق أكثر في مجموعة الميزات الكاملة من خلال مراجعة الوثائق الرسمية وتجربة معايير وصفية أخرى مثل IPTC و EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**آخر تحديث:** 2026-08-20  
**تم الاختبار مع:** GroupDocs.Metadata for Java 23.11  
**المؤلف:** GroupDocs  

- [التوثيق](https://docs.groupdocs.com/metadata/java/)
- [مرجع API](https://reference.groupdocs.com/metadata/java/)
- [تحميل](https://releases.groupdocs.com/metadata/java/)
- [مستودع GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/metadata/)
- [ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/)

## دروس ذات صلة

- [استخراج بيانات Dublin Core من ملفات Epub باستخدام Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [استخراج وسم EXIF للبرمجيات في Java: دليل كامل باستخدام GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [كيفية استخراج البيانات الوصفية باستخدام GroupDocs.Metadata للغة Java – دروس وأمثلة](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}