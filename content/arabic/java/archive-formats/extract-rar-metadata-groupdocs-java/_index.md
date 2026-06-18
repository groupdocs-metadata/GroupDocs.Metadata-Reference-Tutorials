---
date: '2026-02-19'
description: تعلم كيفية الحصول على حجم الملف المضغوط في جافا أثناء استخراج بيانات
  RAR الوصفية باستخدام GroupDocs.Metadata لجافا. دليل خطوة بخطوة، عينات شفرة، وأفضل
  الممارسات.
keywords:
- extract RAR metadata Java
- manage archive metadata
- RAR file details extraction
title: احصل على الحجم المضغوط في جافا باستخدام GroupDocs.Metadata
type: docs
url: /ar/java/archive-formats/extract-rar-metadata-groupdocs-java/
weight: 1
---

# الحصول على حجم مضغوط Java باستخدام GroupDocs.Metadata

في التطبيقات الحديثة التي تركز على البيانات، **الحصول على حجم مضغوط java** للملفات داخل أرشيفات RAR هو مطلب شائع. سواءً كنت تبني أداة للتحقق من النسخ الاحتياطية، نظام إدارة أصول رقمية، أو تحتاج ببساطة إلى عرض ملخصات الأرشيف، فإن قراءة هذه البيانات الوصفية دون استخراج الأرشيف توفر الوقت والموارد. يوضح هذا الدليل كيفية استخدام GroupDocs.Metadata للـ Java لاستخراج بيانات RAR الوصفية الغنية—بما في ذلك الحجم المضغوط لكل مدخل—بسرعة وموثوقية.

## إجابات سريعة
- **ما المكتبة المطلوبة؟** GroupDocs.Metadata للـ Java  
- **هل يمكنني استرجاع الأحجام المضغوطة؟** نعم – استخدم `rarFile.getCompressedSize()`  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية تكفي للتطوير؛ الترخيص الكامل مطلوب للإنتاج  
- **ما نسخة Java المدعومة؟** Java 8+ (أي بيئة متوافقة مع Maven)  
- **هل المعالجة الدفعية ممكنة؟** بالتأكيد – يمكن حلقة عبر مجلد يحتوي على ملفات RAR وإعادة استخدام نفس الكود  
- **كيف أتعامل مع الأرشيفات الكبيرة؟** عالج المدخلات واحدةً تلو الأخرى وأغلق كائن البيانات الوصفية عند الانتهاء  

## ما هو “get compressed size java” ولماذا يهم؟
عملية **get compressed size java** تقرأ حجم الملف كما هو مخزن داخل حاوية RAR. معرفة هذه القيمة تمكنك من:

* التحقق من أن الأرشيف يتطابق مع نسب الضغط المتوقعة.  
* تقدير أوقات التحميل أو النقل دون استخراج البيانات بالكامل.  
* بناء جرد قابل للبحث يُظهر كلًا من الأحجام الأصلية والمضغوطة.

## المتطلبات المسبقة
قبل البدء، تأكد من وجود ما يلي:

- **GroupDocs.Metadata للـ Java** (أحدث إصدار).  
- بيئة تطوير متوافقة مع Maven (IDE، JDK 8+).  
- معرفة أساسية بـ Java (إدخال/إخراج الملفات، الحلقات، ومفاهيم البرمجة الكائنية).  

## إعداد GroupDocs.Metadata للـ Java
يمكنك إضافة المكتبة عبر Maven أو تحميلها مباشرة.

### إعداد Maven
أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك:

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

### التحميل المباشر
بدلاً من ذلك، حمّل من [إصدارات GroupDocs.Metadata للـ Java](https://releases.groupdocs.com/metadata/java/).

**الحصول على الترخيص**: ابدأ بنسخة تجريبية مجانية أو احصل على ترخيص مؤقت. للوصول الكامل في بيئة الإنتاج، اشترِ ترخيصًا من البائع.

قم بتهيئة GroupDocs.Metadata في مشروعك:

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

## دليل التنفيذ – استخراج بيانات RAR الوصفية والحصول على الحجم المضغوط

### كيف تحصل على حجم مضغوط java من أرشيفات RAR؟
فيما يلي شرح خطوة‑بخطوة يوضح بالضبط كيفية قراءة الحجم المضغوط لكل مدخل.

#### الخطوة 1: تهيئة كائن البيانات الوصفية
```java
// Specify the path to your input RAR file
String rarFilePath = "YOUR_DOCUMENT_DIRECTORY/input.rar";

// Initialize Metadata object with the specified RAR file path\ nMetadata metadata = new Metadata(rarFilePath);
```

#### الخطوة 2: الحصول على الحزمة الجذرية لأرشيف RAR
```java
// Obtain the root package of the RAR archive
RarRootPackage root = metadata.getRootPackageGeneric();
```

#### الخطوة 3: استرجاع إجمالي عدد المدخلات
```java
// Retrieve and print the total number of entries in the RAR package
int totalEntries = root.getRarPackage().getTotalEntries();
system.out.println("Total Entries: " + totalEntries);
```

#### الخطوة 4: التكرار على كل ملف وقراءة خصائصه
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

**نصائح استكشاف الأخطاء**  
- تأكد من أن `rarFilePath` يشير إلى ملف RAR موجود.  
- تأكد من أن التطبيق يمتلك صلاحيات القراءة للأرشيف.  
- إذا واجهت أخطاء “تنسيق غير مدعوم”، تحقق من أن نسخة RAR متوافقة مع GroupDocs.Metadata (يدعم RAR 4 و RAR 5).  

## لماذا نستخدم GroupDocs.Metadata لملفات RAR؟
- **لا حاجة للاستخراج** – تُقرأ البيانات الوصفية مباشرة من رأس الأرشيف.  
- **اتساق عبر الصيغ** – نفس الـ API يعمل مع ZIP و 7z وصيغ أرشيف أخرى.  
- **مركز على الأداء** – يتم الوصول فقط إلى الحقول المطلوبة، مما يحافظ على استهلاك الذاكرة منخفضًا.  

## حالات الاستخدام الشائعة
1. **أنظمة إدارة البيانات** – فهرسة محتويات الأرشيف تلقائيًا لجرد قابل للبحث.  
2. **إدارة الأصول الرقمية** – إثراء مكتبات الوسائط بتفاصيل مستوى الأرشيف.  
3. **التحقق من النسخ الاحتياطية** – مقارنة الأحجام المضغوطة المخزنة مع القيم المتوقعة.  
4. **منصات مشاركة الملفات** – عرض ملخصات الأرشيف دون استخراج كامل.  

## اعتبارات الأداء
- **الوصول فقط إلى الخصائص المطلوبة** – تجنب استدعاء طرق ثقيلة إذا كنت تحتاج فقط إلى أسماء الملفات وأحجامها.  
- **تحرير كائنات البيانات الوصفية** – استدعِ `metadata.close()` عند الانتهاء لتحرير الموارد الأصلية.  
- **المعالجة الدفعية** – عالج عدة ملفات RAR في حلقة، مع إعادة استخدام نفس الـ JVM لتقليل تكلفة بدء التشغيل.  

## الأسئلة المتكررة

**س: ما هو GroupDocs.Metadata للـ Java؟**  
ج: مكتبة قوية تسهّل قراءة، تحديث، وإدارة البيانات الوصفية عبر صيغ ملفات متعددة، بما في ذلك أرشيفات RAR.

**س: كيف أحصل على ترخيص للوصول الكامل؟**  
ج: زر [صفحة شراء GroupDocs](https://purchase.groupdocs.com/temporary-license/) للحصول على ترخيص مؤقت أو دائم.

**س: هل يمكنني استخدام GroupDocs.Metadata مع أنواع أرشيف أخرى غير RAR؟**  
ج: نعم، يدعم صيغ أرشيف متعددة بما في ذلك ZIP و 7z.

**س: ما هي بعض المشكلات الشائعة عند العمل مع البيانات الوصفية في Java؟**  
ج: التعامل مع ملفات كبيرة وإدارة الذاكرة بفعالية قد تكون تحديًا.

**س: أين يمكنني الحصول على الدعم إذا واجهت مشاكل؟**  
ج: تواصل مع [منتدى الدعم المجاني لـ GroupDocs](https://forum.groupdocs.com/c/metadata/) للحصول على مساعدة من الخبراء والمجتمع.

## الموارد
- **الوثائق**: [توثيق GroupDocs Metadata Java](https://docs.groupdocs.com/metadata/java/)  
- **مرجع API**: [مرجع GroupDocs API](https://reference.groupdocs.com/metadata/java/)  
- **التحميل**: [تحميل أحدث الإصدارات](https://releases.groupdocs.com/metadata/java/)  
- **GitHub**: [الكود المصدر على GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **الدعم المجاني**: [منتدى GroupDocs](https://forum.groupdocs.com/c/metadata/)

## الخلاصة
أنت الآن تعرف **كيفية استخدام GroupDocs.Metadata** لاستخراج بيانات وصفية شاملة من أرشيفات RAR، بما في ذلك **الحصول على حجم مضغوط java** لكل مدخل. دمج هذا المقتطف في مشاريعك يعزز قدرات إدارة البيانات، يحسن من التحقق من النسخ الاحتياطية، ويثري تجارب البحث عن الملفات.

### الخطوات التالية
استكشف المزيد من ميزات GroupDocs.Metadata في [وثائقهم الشاملة](https://docs.groupdocs.com/metadata/java/) أو تعمق أكثر في برمجة Java للتعامل المتقدم مع البيانات الوصفية.

---

**آخر تحديث:** 2026-02-19  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 للـ Java  
**المؤلف:** GroupDocs  

---