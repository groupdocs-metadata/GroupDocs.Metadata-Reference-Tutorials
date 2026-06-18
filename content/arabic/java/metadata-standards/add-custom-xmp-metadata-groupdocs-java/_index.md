---
date: '2026-06-12'
description: تعلم كيفية إنشاء حزم XMP مخصصة، وإدارة بيانات تعريف الملفات، وإضافة بيانات
  تعريف مخصصة إلى ملفات PDF باستخدام GroupDocs.Metadata للـ Java.
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
title: إنشاء حزمة XMP مخصصة باستخدام GroupDocs.Metadata للـ Java
type: docs
url: /ar/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/
weight: 1
---

# إنشاء حزمة XMP مخصصة باستخدام GroupDocs.Metadata للغة Java

في سير العمل الرقمي الحديث، **إنشاء حزم XMP مخصصة** أمر أساسي لتضمين بيانات وصفية غنية وقابلة للبحث مباشرة داخل الملفات. سواء كنت تتعامل مع الصور أو ملفات PDF أو الأصول المتعددة الوسائط، يوفر لك GroupDocs.Metadata للغة Java طريقة موثوقة لـ **إدارة بيانات ملف التعريف** و **إضافة بيانات وصفية مخصصة إلى ملفات PDF** دون الحاجة إلى قواعد بيانات خارجية. في هذا البرنامج التعليمي سنستعرض العملية بالكامل — من إعداد المكتبة إلى تضمين حزمة XMP كاملة المميزات — حتى تتمكن من بدء إثراء مستنداتك اليوم.

## إجابات سريعة
- **ما هي الخطوة الأولى؟** أضف GroupDocs.Metadata كاعتماد Maven أو قم بتنزيل ملف JAR.  
- **كم عدد أسطر الشيفرة؟** تحتاج فقط إلى ثلاث عبارات مختصرة لإنشاء وإرفاق حزمة XMP مخصصة.  
- **ما هي صيغ الملفات المدعومة؟** أكثر من 50 صيغة، بما في ذلك JPEG و PNG و PDF و DOCX و TIFF.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تعمل للتطوير؛ يلزم ترخيص دائم للإنتاج.  
- **هل يمكنني استخدامه مع Java 11+؟** نعم، المكتبة متوافقة مع Java 8 حتى Java 21.  

## ما هو “إنشاء حزمة XMP مخصصة”؟
*إنشاء حزمة XMP مخصصة* يعني بناء حزمة XMP تحتوي على حقول بيانات وصفية معرفة من قبل المستخدم وتضمينها في ملف مدعوم. تُخزن هذه الحزمة داخل قسم XMP الخاص بالملف، مما يجعل البيانات الوصفية قابلة للنقل والبحث بواسطة أي تطبيق يدعم XMP.

## لماذا تستخدم GroupDocs.Metadata للغة Java لإدارة بيانات ملف التعريف؟
يدعم GroupDocs.Metadata **أكثر من 50 صيغة إدخال وإخراج** ويمكنه معالجة ملفات تصل إلى **2 GB** دون تحميل المستند بالكامل إلى الذاكرة، مما يقلل استهلاك RAM بنسبة تصل إلى **80 %** على الأصول الكبيرة. كما توفر الـ API عمليات آمنة للمتعدد الخيوط، مما يتيح معالجة دفعات عالية الإنتاجية في بيئات المؤسسات.

## المتطلبات المسبقة
- **Java Development Kit** 8 أو أحدث (يوصى بـ Java 11+).  
- بيئة تطوير متكاملة مثل **IntelliJ IDEA** أو **Eclipse**.  
- تثبيت Maven لإدارة الاعتمادات.  
- فهم أساسي لفئات Java ومفاهيم البيانات الوصفية.

## إعداد GroupDocs.Metadata للغة Java
### إعداد Maven
أضف الاعتماد التالي إلى ملف `pom.xml` الخاص بك لتضمين GroupDocs.Metadata:

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

ارجع إلى [وثائق API](https://reference.groupdocs.com/metadata/java/) للحصول على توقيعات الطرق الكاملة.  
للحصول على مرجع API مفصل راجع [وثائق GroupDocs.Metadata Java](https://docs.groupdocs.com/metadata/java/).

**تحميل مباشر** – إذا كنت تفضل الإعداد اليدوي، احصل على أحدث ملف JAR من [إصدارات GroupDocs.Metadata للغة Java](https://releases.groupdocs.com/metadata/java/). يمكنك أيضًا مشاهدة صفحة [الإصدارات الأخيرة](https://releases.groupdocs.com/metadata/java/) للحصول على تفاصيل سجل التغييرات.

### الحصول على الترخيص
- **نسخة تجريبية مجانية** – تقييم جميع الميزات دون تكلفة.  
- **ترخيص مؤقت** – احصل على مفتاح محدود الوقت لاختبار التطوير. ([احصل على ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/))  
- **شراء** – الحصول على ترخيص دائم للاستخدام في الإنتاج.

الكود المصدري والأمثلة متاحة على [GroupDocs Metadata على GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java).

## دليل التنفيذ
فيما يلي دليل خطوة بخطوة يوضح بالضبط كيفية **إنشاء حزمة XMP مخصصة** وتضمينها في ملف.

### كيفية إنشاء حزمة XMP مخصصة وإرفاقها بملف؟
حمّل الملف المستهدف باستخدام فئة `Metadata`، أنشئ `XmpPacketWrapper`، عرّف حقول XMP المخصصة الخاصة بك، وأخيرًا احفظ التغييرات. يتطلب هذا التدفق من البداية إلى النهاية ثلاث نداءات للطرق فقط بعد التهيئة. تضمن العملية تضمين حزمة XMP بشكل صحيح ويبقى الملف وظيفيًا بالكامل عبر جميع التطبيقات المدعومة.

### تهيئة كائن Metadata
`Metadata` هي الفئة الأساسية التي تمثل ملفًا وتوفر طرقًا لقراءة وكتابة بياناته الوصفية.  
```java
Metadata metadata = new Metadata("sample.pdf");
```

### إنشاء XmpPacketWrapper جديد
`XmpPacketWrapper` يعمل كحاوية لحزمة أو أكثر من حزم XMP، مما يسمح بتحديثات دفعة قبل الحفظ.  
```java
XmpPacketWrapper xmpWrapper = new XmpPacketWrapper();
```

### تعريف وتكوين حزمة XMP المخصصة
واجهة `IXmp` تتيح لك تعريف مخططات XMP مخصصة وتعيين قيم الخصائص داخل الحزمة.  
```java
IXmp customXmp = xmpWrapper.createPackage("http://mycompany.com/custom");
customXmp.setProperty("Creator", "John Doe");
customXmp.setProperty("Project", "Metadata Migration");
customXmp.setProperty("Version", "1.0");
```

### حفظ البيانات الوصفية المحدثة
`Metadata.save()` يكتب البيانات الوصفية المعدلة مرة أخرى إلى الملف الأصلي، مع الحفاظ على أي حزم XMP مضافة.  
```java
metadata.getXmp().addPacket(xmpWrapper);
metadata.save();
```

#### شرح المكونات الرئيسية
- **كائن Metadata** – المركز الرئيسي للوصول إلى بيانات ملف الوصفية.  
- **واجهة IXmp** – توفر طرقًا لقراءة/كتابة الحقول الخاصة بـ XMP.  
- **XmpPacketWrapper** – يحتفظ بحزمة أو أكثر من حزم XMP، مما يتيح تحديثات دفعة.  
- **حزمة XMP مخصصة** – المخطط الذي تعرفه أنت لتخزين معلومات إضافية.

## المشكلات الشائعة والحلول
- **صيغة ملف غير مدعومة** – تحقق من أن نوع الملف المستهدف موجود في قائمة الصيغ الرسمية (أكثر من 50 صيغة مدعومة).  
- **الترخيص غير موجود** – تأكد من وضع ملف الترخيص في الدليل الجذر للتطبيق أو تعيينه عبر `License.setLicense("license_path")`.  
- **نفاد الذاكرة في الملفات الكبيرة** – استخدم `metadata.setLoadOptions(LoadOptions.lazyLoad())` لمعالجة البيانات الوصفية بشكل كسول والحفاظ على انخفاض استهلاك الذاكرة.

للمزيد من المساعدة، زر منتدى [دعم GroupDocs](https://forum.groupdocs.com/c/metadata/).

## التطبيقات العملية
1. **إدارة الأصول الرقمية** – تضمين تراخيص وحقوق الاستخدام مباشرةً في الصور وملفات PDF.  
2. **تخصيص المحتوى** – إرفاق معرفات خاصة بالمستخدم إلى المستندات للتسليم المستهدف.  
3. **الامتثال التنظيمي** – تخزين سجلات التدقيق وسياسات الاحتفاظ داخل الملف نفسه، مما يبسط تدقيق الحوكمة.

## اعتبارات الأداء
- **تحسين الموارد** – معالجة البيانات الوصفية في وضع البث للحفاظ على استهلاك RAM أقل من **100 MB** للملفات التي تزيد عن **1 GB**.  
- **تحديثات الإصدارات** – حافظ على تحديث المكتبة؛ كل إصدار رئيسي يضيف دعمًا لصيغ جديدة ويحسن سرعة المعالجة بنسبة تصل إلى **30 %**.

## الخلاصة
باتباعك لهذا الدليل، أصبحت الآن تعرف كيفية **إنشاء حزم XMP مخصصة** باستخدام GroupDocs.Metadata للغة Java، مما يتيح لك **إدارة بيانات ملف الوصفية** بفعالية و**إضافة بيانات وصفية مخصصة إلى ملفات PDF** والعديد من الصيغ الأخرى. جرب مخططات XMP إضافية، دمج سير العمل في خط أنابيب CI الخاص بك، أو دمجه مع GroupDocs.Viewer لمعالجة المستندات من البداية إلى النهاية.

## الأسئلة المتكررة

**س: ما هي صيغ الملفات التي تدعم حزم XMP المخصصة؟**  
ج: أكثر من 50 صيغة — بما في ذلك JPEG و PNG و PDF و DOCX و TIFF — تدعم حقن حزم XMP. راجع القائمة الكاملة في [وثائق GroupDocs.Metadata](https://docs.groupdocs.com/metadata/java/).

**س: هل يمكنني تعديل بيانات XMP الوصفية الموجودة باستخدام GroupDocs.Metadata؟**  
ج: نعم، تتيح لك المكتبة قراءة وتعديل وحذف أي خاصية XMP باستخدام واجهة `IXmp`.

**س: كيف أتعامل مع الملفات التي لا تدعم XMP أصلاً؟**  
ج: بالنسبة للصيغ غير المدعومة، فكر في تغليف الملف في حاوية تدعم XMP (مثل التحويل إلى PDF) أو استخدام مخزن بيانات وصفية بديل.

**س: هل المكتبة متوافقة مع Java 17 LTS؟**  
ج: بالتأكيد — تم اختبار GroupDocs.Metadata مع Java 8 حتى Java 21، بما في ذلك جميع إصدارات LTS.

**س: ما هي الأخطاء الشائعة عند إضافة حزم XMP؟**  
ج: تشمل المشكلات الشائعة استخدام URI مساحة اسم غير صحيح، تجاوز الحد الأقصى لحجم الحزمة (≈ 2 MB)، أو محاولة الكتابة إلى ملف للقراءة فقط. تأكد من وجود الأذونات المناسبة والتحقق من صحة مخطط XML قبل الحفظ.

**آخر تحديث:** 2026-06-12  
**تم الاختبار مع:** GroupDocs.Metadata 23.12 للغة Java  
**المؤلف:** GroupDocs  

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

## دروس ذات صلة

- [إضافة بيانات XMP مخصصة إلى الملفات باستخدام GroupDocs.Metadata Java: دليل شامل](/metadata/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/)
- [كيفية إضافة بيانات وصفية إلى PDF باستخدام GroupDocs.Metadata للغة Java – دليل المطور](/metadata/java/document-formats/master-pdf-metadata-groupdocs-java/)
- [كيفية استخراج بيانات وصفية مخصصة من ملفات PDF باستخدام GroupDocs.Metadata في Java: دليل شامل](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)