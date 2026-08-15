---
date: '2026-06-22'
description: تعلم كيفية الحصول على الحجم المضغوط في Java أثناء استخراج بيانات RAR
  الوصفية باستخدام GroupDocs.Metadata لـ Java. دليل خطوة بخطوة، عينات شفرة، وأفضل
  الممارسات.
keywords:
- get compressed size java
- groupdocs metadata java
- extract rar metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  headline: Get Compressed Size Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  name: Get Compressed Size Java with GroupDocs.Metadata
  steps:
  - name: Initialize the Metadata object
    text: Create a `Metadata` instance by providing the path to the RAR file. This
      object represents the archive in memory and gives you access to its internal
      structure.
  - name: Obtain the root package of the RAR archive
    text: Call `metadata.getRootPackage()` to retrieve the top‑level package that
      contains all entries. The returned `ArchivePackage` lets you enumerate files
      and folders inside the archive.
  - name: Retrieve total entry count
    text: Use `archivePackage.getEntries().size()` to know how many items are stored.
      Knowing the count helps you allocate progress‑tracking structures for batch
      jobs.
  - name: Iterate over each file and read its properties
    text: Loop through `archivePackage.getEntries()`. For every entry that represents
      a file (not a folder), call `entry.getCompressedSize()` to obtain its compressed
      size in bytes. You can also read `entry.getOriginalSize()` if you need the uncompressed
      size for ratio calculations. **Troubleshooting Tips** -
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java is a library that enables reading, updating,
      and managing metadata across more than 50 file formats, including RAR, ZIP,
      and 7z, without requiring file extraction.
    question: What is GroupDocs.Metadata for Java?
  - answer: Visit the [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)
      to acquire a temporary or permanent license; a free trial is available for development.
    question: How do I obtain a license for full access?
  - answer: Yes, the same API supports ZIP, 7z, and several other archive formats,
      allowing a unified codebase for all archive metadata tasks.
    question: Can I use GroupDocs.Metadata with other archive types besides RAR?
  - answer: The main issues are memory consumption and file‑handle limits; mitigate
      them by processing entries one‑by‑one and closing the `Metadata` object promptly.
    question: What are common pitfalls when handling large RAR files?
  - answer: The [GroupDocs free support forum](https://forum.groupdocs.com/c/metadata/)
      provides assistance from both the vendor’s engineers and the community.
    question: Where can I get support if I encounter problems?
  type: FAQPage
title: الحصول على الحجم المضغوط في Java باستخدام GroupDocs.Metadata
type: docs
url: /ar/java/archive-formats/extract-rar-metadata-groupdocs-java/
weight: 1
---

# الحصول على الحجم المضغوط Java باستخدام GroupDocs.Metadata

في التطبيقات الحديثة التي تركز على البيانات، **get compressed size java** هو طلب شائع عندما تحتاج إلى فحص حجم الملفات المخزنة داخل أرشيفات RAR دون استخراجها. سواء كنت تبني أداة للتحقق من النسخ الاحتياطية، أو نظام إدارة أصول رقمية، أو بوابة مشاركة ملفات، فإن قراءة هذه البيانات الوصفية توفر الوقت وموارد النظام. يوضح هذا الدليل كيفية استخدام GroupDocs.Metadata للـ Java لاسترجاع الحجم المضغوط لكل إدخال بسرعة وأمان وبأقل قدر من الشيفرة.

## إجابات سريعة
- **ما المكتبة المطلوبة؟** GroupDocs.Metadata for Java  
- **هل يمكنني استرجاع الأحجام المضغوطة؟** نعم – استدعِ `rarFile.getCompressedSize()` على كل إدخال  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تعمل للتطوير؛ الترخيص الكامل مطلوب للإنتاج  
- **ما نسخة Java المدعومة؟** Java 8+ (أي بيئة متوافقة مع Maven)  
- **هل المعالجة الدفعة ممكنة؟** بالتأكيد – كرّر عبر مجلد من ملفات RAR وأعد استخدام نفس الشيفرة  
- **كيف أتعامل مع الأرشيفات الكبيرة؟** عالج الإدخالات واحدة تلو الأخرى وأغلق كائن metadata عند الانتهاء  

## ما هو “get compressed size java” ولماذا هو مهم؟
**Get compressed size java** يقرأ حجم الملف كما هو مخزن داخل حاوية RAR. هذه القيمة تخبرك بمقدار المساحة التي يشغلها الملف بعد الضغط، مما يتيح لك التحقق من نسب الضغط، تقدير أوقات النقل، وعرض الأحجام الأصلية والمضغوطة في تقارير الجرد.

## كيفية الحصول على الحجم المضغوط java من أرشيفات RAR؟
حمّل أرشيف RAR باستخدام GroupDocs.Metadata، وتكرّر عبر إدخالاته، واستدعِ طريقة `getCompressedSize()` على كل إدخال ملف. هذه الطريقة تقرأ فقط رأس الأرشيف، لذا لا يحدث استخراج أو تحميل كامل للملف، مما يحافظ على استهلاك الذاكرة تحت 5 ميغابايت حتى للأرشيفات التي تتجاوز مئات الميجابايت.

### الخطوة 1: تهيئة كائن Metadata
أنشئ مثالًا من `Metadata` بتوفير مسار ملف RAR. هذا الكائن يمثل الأرشيف في الذاكرة ويمنحك الوصول إلى هيكله الداخلي.

### الخطوة 2: الحصول على الحزمة الجذرية لأرشيف RAR
استدعِ `metadata.getRootPackage()` لاسترجاع الحزمة العليا التي تحتوي على جميع الإدخالات. الـ `ArchivePackage` المسترجع يتيح لك تعداد الملفات والمجلدات داخل الأرشيف.

### الخطوة 3: استرجاع عدد الإدخالات الكلي
استخدم `archivePackage.getEntries().size()` لمعرفة عدد العناصر المخزنة. معرفة العدد تساعدك على تخصيص هياكل تتبع التقدم للوظائف الدفعية.

### الخطوة 4: التكرار على كل ملف وقراءة خصائصه
تكرّر عبر `archivePackage.getEntries()`. لكل إدخال يمثل ملفًا (ليس مجلدًا)، استدعِ `entry.getCompressedSize()` للحصول على حجمه المضغوط بالبايت. يمكنك أيضًا قراءة `entry.getOriginalSize()` إذا كنت بحاجة إلى الحجم غير المضغوط لحساب النسب.

**نصائح استكشاف الأخطاء**
- تحقق من أن `rarFilePath` يشير إلى ملف RAR موجود.  
- تأكد من أن التطبيق يمتلك أذونات القراءة للأرشيف.  
- إذا واجهت أخطاء “تنسيق غير مدعوم”، فتأكد من أن نسخة RAR متوافقة مع GroupDocs.Metadata (يدعم RAR 4 و RAR 5).  

## لماذا نستخدم GroupDocs.Metadata لملفات RAR؟
يوفر GroupDocs.Metadata واجهة برمجة تطبيقات عالية المستوى تقرأ رؤوس الأرشيف دون استخراج الملفات، مما يمنح وصولًا سريعًا إلى خصائص مثل الحجم المضغوط، الحجم الأصلي، والطوابع الزمنية. يعمل مع صيغ RAR 4 و RAR 5، يتعامل مع الأرشيفات الكبيرة بكفاءة، ويجرد التفاصيل الخاصة بالصيغة بحيث يمكن للمطورين كتابة شيفرة موحدة عبر أنواع الأرشيفات.

## حالات الاستخدام الشائعة
1. **أنظمة إدارة البيانات** – فهرسة محتويات الأرشيف تلقائيًا لإنشاء جرد قابل للبحث.  
2. **إدارة الأصول الرقمية** – إغناء مكتبات الوسائط بتفاصيل مستوى الأرشيف مثل الحجم المضغوط.  
3. **التحقق من النسخ الاحتياطية** – مقارنة الأحجام المضغوطة المخزنة بالقيم المتوقعة لاكتشاف الفساد.  
4. **منصات مشاركة الملفات** – عرض ملخصات الأرشيف دون استخراج الملفات بالكامل، مما يحسن تجربة المستخدم.  

## اعتبارات الأداء
- **الوصول فقط إلى الخصائص المطلوبة** – تجنّب استدعاء الطرق الثقيلة إذا كنت تحتاج فقط إلى أسماء الملفات وأحجامها.  
- **تحرير كائنات metadata** – استدعِ `metadata.close()` بعد المعالجة لتحرير الموارد الأصلية.  
- **المعالجة الدفعية** – عالج عدة ملفات RAR في حلقة، مع إعادة استخدام نفس JVM لتقليل عبء بدء التشغيل.  

## الأسئلة المتكررة

**س: ما هو GroupDocs.Metadata للـ Java؟**  
ج: GroupDocs.Metadata للـ Java هي مكتبة تمكّن من قراءة وتحديث وإدارة البيانات الوصفية عبر أكثر من 50 صيغة ملف، بما في ذلك RAR و ZIP و 7z، دون الحاجة لاستخراج الملف.

**س: كيف أحصل على ترخيص للوصول الكامل؟**  
ج: زر [صفحة شراء GroupDocs](https://purchase.groupdocs.com/temporary-license/) للحصول على ترخيص مؤقت أو دائم؛ نسخة تجريبية مجانية متاحة للتطوير.

**س: هل يمكنني استخدام GroupDocs.Metadata مع أنواع أرشيف أخرى غير RAR؟**  
ج: نعم، نفس الـ API يدعم ZIP و 7z والعديد من صيغ الأرشيف الأخرى، مما يسمح بقاعدة شيفرة موحدة لجميع مهام بيانات الأرشيف.

**س: ما هي المشكلات الشائعة عند التعامل مع ملفات RAR الكبيرة؟**  
ج: المشكلات الرئيسية هي استهلاك الذاكرة وحدود مقبض الملفات؛ قلل منها بمعالجة الإدخالات واحدة تلو الأخرى وإغلاق كائن `Metadata` بسرعة.

**س: أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟**  
ج: يوفر [منتدى الدعم المجاني لـ GroupDocs](https://forum.groupdocs.com/c/metadata/) المساعدة من مهندسي البائع والمجتمع.

## الموارد
- **التوثيق**: [GroupDocs Metadata Java Documentation](https://docs.groupdocs.com/metadata/java/)  
- **مرجع API**: [GroupDocs API Reference](https://reference.groupdocs.com/metadata/java/)  
- **التنزيل**: [Latest Version Downloads](https://releases.groupdocs.com/metadata/java/)  
- **GitHub**: [Source Code on GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **دعم مجاني**: [GroupDocs Forum](https://forum.groupdocs.com/c/metadata/)  
- **الإصدارات**: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)  
- **توثيق شامل**: [comprehensive documentation](https://docs.groupdocs.com/metadata/java/)  

## الخلاصة
أنت الآن تعرف **كيفية استخدام GroupDocs.Metadata** لاستخراج بيانات وصفية شاملة من أرشيفات RAR، بما في ذلك كيفية **get compressed size java** لكل إدخال. دمج هذا النمط في مشاريعك يعزز قدرات إدارة البيانات، يحسن التحقق من النسخ الاحتياطية، ويثري تجارب البحث عن الملفات دون عبء استخراج كامل.

### الخطوات التالية
استكشف ميزات إضافية مثل تحديث تعليقات الإدخالات أو استخراج معلومات التحقق (checksum) في التوثيق الرسمي، وفكّر في دمج استخراج البيانات الوصفية هذا مع خط أنابيب الفهرسة الحالي للحصول على مستودع أرشيف قابل للبحث بالكامل.

---

**آخر تحديث:** 2026-06-22  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 for Java  
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

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata object
        Metadata metadata = new Metadata("path/to/your/document");
        System.out.println("Metadata initialized successfully.");
    }
}
```

```java
// Specify the path to your input RAR file
String rarFilePath = "YOUR_DOCUMENT_DIRECTORY/input.rar";

// Initialize Metadata object with the specified RAR file path\ nMetadata metadata = new Metadata(rarFilePath);
```

```java
// Obtain the root package of the RAR archive
RarRootPackage root = metadata.getRootPackageGeneric();
```

```java
// Retrieve and print the total number of entries in the RAR package
int totalEntries = root.getRarPackage().getTotalEntries();
system.out.println("Total Entries: " + totalEntries);
```

```java
// Iterate over each file within the RAR archive
for (RarFile rarFile : root.getRarPackage().getFiles()) {
    // Print file name, compressed size, modification date time, and uncompressed size
    System.out.println("File Name: " + rarFile.getName());
    System.out.println("Compressed Size: " + rarFile.getCompressedSize());
    System.out.println("Modification Date Time: " + rarFile.getModificationDateTime());
    System.out.println("Uncompressed Size: " + rarFile.getUncompressedSize());
}
```

## دروس ذات صلة

- [استخراج تعليقات zip java باستخدام GroupDocs.Metadata – دليل](/metadata/java/archive-formats/extract-zip-metadata-groupdocs-java-guide/)  
- [تحديث تعليق ZIP Java – كيفية تحديث تعليقات أرشيف ZIP باستخدام GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)  
- [كيفية قراءة ملفات TAR واستخراج البيانات الوصفية باستخدام GroupDocs.Metadata للـ Java](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)