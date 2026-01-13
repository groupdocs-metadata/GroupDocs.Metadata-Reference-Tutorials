---
date: '2026-01-13'
description: تعلم كيفية الحصول على عدد صفحات المخطط واستخراج إحصائيات النص من المخططات
  باستخدام GroupDocs.Metadata للغة Java. يتضمن إعدادًا خطوة بخطوة وأمثلة على الشيفرة.
keywords:
- get diagram page count
- extract text statistics diagrams
- GroupDocs.Metadata Java setup
- Java diagram metadata extraction
title: احصل على عدد صفحات المخطط باستخدام GroupDocs.Metadata لجافا
type: docs
url: /ar/java/diagram-formats/extract-text-statistics-diagrams-groupdocs-metadata-java/
weight: 1
---

# احصل على عدد صفحات المخطط باستخدام GroupDocs.Metadata للـ Java

في مشاريع البرمجيات الحديثة، القدرة على **الحصول على عدد صفحات المخطط** بسرعة يمكن أن توفر الكثير من الوقت—خاصة عندما تحتاج إلى إنشاء تقارير أو أتمتة خطوط توثيق المستندات. في هذا الدرس، ستتعلم كيفية استخدام GroupDocs.Metadata للـ Java لاستخراج كل من عدد الصفحات وإحصاءات نصية مفيدة أخرى من ملفات المخططات مثل VDX. سنستعرض الإعداد المطلوب، ونظهر لك الشيفرة الدقيقة التي تحتاجها، ونناقش سيناريوهات واقعية حيث تتألق هذه القدرة.

## إجابات سريعة
- **ماذا يعني “get diagram page count”?** يعيد إجمالي عدد الصفحات (أو الأوراق) داخل ملف المخطط.  
- **أي مكتبة توفر هذه الميزة؟** GroupDocs.Metadata للـ Java.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتقييم؛ الترخيص الدائم مطلوب للإنتاج.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.  
- **هل يمكنني معالجة عدة مخططات في حلقة؟** نعم—فقط أنشئ كائن `Metadata` لكل ملف داخل الحلقة.

## ما هو “get diagram page count”؟
الحصول على عدد صفحات المخطط يعني استعلام بيانات تعريف المخطط لاكتشاف عدد الصفحات أو اللوحات الفردية التي يحتويها الملف. هذه المعلومات هي جزء من إحصاءات المستند التي تعرضها GroupDocs.Metadata.

## لماذا نستخدم GroupDocs.Metadata للـ Java؟
- **استخراج سريع وخفيف** – لا حاجة لتصوير المخطط بالكامل.  
- **دعم واسع للصياغات** – يعمل مع VDX وVSDX والعديد من صيغ المخططات الأخرى.  
- **واجهة برمجة تطبيقات بسيطة** – بضع أسطر من الشيفرة تمنحك عدد الصفحات، المؤلف، تاريخ الإنشاء، وأكثر.

## المتطلبات المسبقة
- **GroupDocs.Metadata للـ Java** (الإصدار 24.12 أو أحدث).  
- **JDK 8+** مثبت على جهازك.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- Maven لإدارة التبعيات.

## إعداد GroupDocs.Metadata للـ Java

### باستخدام Maven
أضف المستودع والتبعيات إلى ملف `pom.xml` الخاص بك تمامًا كما هو موضح أدناه:

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

### تحميل مباشر
إذا كنت تفضل عدم استخدام Maven، احصل على أحدث ملف JAR من صفحة الإصدار الرسمية: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### الحصول على الترخيص
- **نسخة تجريبية** – حمّل واستكشف جميع الميزات دون تكلفة.  
- **ترخيص مؤقت** – اطلب مفتاحًا مؤقتًا للاختبار غير المحدود.  
- **ترخيص كامل** – اشترِ لاستخدام غير محدود في بيئة الإنتاج.

### التهيئة الأساسية

فيما يلي أقل كمية من الشيفرة اللازمة للبدء في العمل مع ملف مخطط. هذا المقتطف **يُهيئ كائن Metadata**، وهو نقطة الدخول لجميع العمليات اللاحقة، بما في ذلك الحصول على عدد صفحات المخطط.

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

## دليل التنفيذ – الحصول على عدد صفحات المخطط

الآن بعد أن أصبحت المكتبة جاهزة، دعنا نتعمق في الخطوات الدقيقة لاسترجاع عدد الصفحات.

### الخطوة 1: الحصول على الحزمة الجذرية

كل نوع مخطط له حزمة جذرية محددة تمنحك الوصول إلى بياناته التعريفية. استخدم الطريقة العامة `getRootPackageGeneric()` لجلبها.

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

### الخطوة 2: الوصول إلى إحصاءات المستند (Get Diagram Page Count)

مع الحزمة الجذرية في يدك، يمكنك استدعاء `getDocumentStatistics()` ثم `getPageCount()` للحصول على **عدد صفحات المخطط**.

```java
            int pageCount = root.getDocumentStatistics().getPageCount();
            System.out.println("Page Count: " + pageCount);
        }
    }
}
```

**شرح**: `getDocumentStatistics()` تُعيد كائنًا يحتوي على عدة مقاييس مفيدة، بما في ذلك عدد الصفحات. وبالتالي فإن المتغير `pageCount` يمثل إجمالي الصفحات في المخطط.

### الخطوة 3: معالجة الاستثناءات برفق

عمليات التعامل مع الملفات قد تفشل لأسباب متعددة (ملف مفقود، صيغة غير مدعومة، إلخ). احط الشيفرة بكتلة try‑catch لتظهر رسائل خطأ واضحة.

```java
        } catch (Exception e) {
            System.err.println("Error occurred while processing diagram metadata: " + e.getMessage());
        }
    }
}
```

**نصائح استكشاف الأخطاء وإصلاحها**  
- تأكد من أن مسار الملف (`inputPath`) يشير إلى ملف مخطط موجود.  
- تحقق من أن صيغة المخطط (مثل VDX) مدعومة من الإصدار الحالي لـ GroupDocs.Metadata.  
- إذا تلقيت خطأ ترخيص، تأكد من تطبيق مفتاح ترخيص تجريبي أو كامل صالح.

## تطبيقات عملية

| الحالة الاستخدامية | كيف يساعد عدد الصفحات |
|--------------------|-----------------------|
| **إدارة المشروع** | تقدير الجهد بسرعة عن طريق عد الصفحات في المخططات الانسيابية أو مخططات الهندسة. |
| **التقارير الآلية** | إنشاء جداول ملخص تُظهر كل مخطط وعدد صفحاته لمراجعات أصحاب المصلحة. |
| **تحليل البيانات** | إدخال مقاييس عدد الصفحات إلى لوحات التحكم لمراقبة نمو الوثائق مع مرور الوقت. |

## اعتبارات الأداء

- **إدارة الموارد**: استخدم `try‑with‑resources` في Java (كما هو موضح) لإغلاق كائن `Metadata` تلقائيًا وتحرير الذاكرة.  
- **المعالجة الدفعية**: عند التعامل مع العديد من المخططات، أعد استخدام كائن `Metadata` واحد لكل ملف وتجنب تحميل بيانات غير ضرورية.

## الخلاصة

أنت الآن تعرف كيف **تحصل على عدد صفحات المخطط** وتستخرج إحصاءات نصية أخرى باستخدام GroupDocs.Metadata للـ Java. يمكن دمج هذا النهج الخفيف في خطوط أتمتة أكبر، أدوات تقارير، أو أي تطبيق يحتاج إلى نظرة سريعة على ملفات المخططات.

### الخطوات التالية
- استكشف إحصاءات إضافية مثل المؤلف، تاريخ الإنشاء، والخصائص المخصصة.  
- اجمع منطق حساب عدد الصفحات مع فحص نظام الملفات لمعالجة مجلدات كاملة من المخططات.  
- اطلع على الموارد الرسمية للحصول على تغطية أعمق للواجهة البرمجية.

## قسم الأسئلة المتكررة

1. **ما صيغ الملفات التي يدعمها GroupDocs.Metadata للمخططات؟**  
   - يدعم VDX وVSDX والعديد من صيغ المخططات الشائعة المستخدمة في بيئات المؤسسات.

2. **هل يمكنني استخدام GroupDocs.Metadata مع مستندات غير مخططات؟**  
   - نعم، تعمل المكتبة مع ملفات PDF، Word، جداول البيانات، وأكثر، مقدمةً تجربة استخراج بيانات تعريف موحدة.

3. **كيف أتعامل مع صيغ الملفات غير المدعومة؟**  
   - تحقق من امتداد الملف مقابل القائمة المدعومة في الوثائق. بالنسبة للصيغ غير المعروفة، فكر في تحويلها إلى صيغة مدعومة أولاً.

4. **هل هناك حد لعدد المخططات التي يمكنني معالجتها في آن واحد؟**  
   - لا يوجد حد صريح، لكن معالجة دفعة كبيرة قد تتطلب الانتباه لاستخدام الذاكرة واستراتيجيات الخيوط.

5. **ماذا أفعل إذا واجهت خطأ في التهيئة؟**  
   - راجع مسار الملف، تأكد من إضافة ملفات JAR إلى مسار الفئة (classpath) بشكل صحيح، وتأكد من تطبيق ترخيص صالح (حتى لو كان تجريبيًا).

## موارد
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/) 

---

**آخر تحديث:** 2026-01-13  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 للـ Java  
**المؤلف:** GroupDocs