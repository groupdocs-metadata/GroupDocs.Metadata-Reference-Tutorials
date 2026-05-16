---
date: '2026-03-20'
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

# الحصول على عدد صفحات المخطط باستخدام GroupDocs.Metadata للـ Java

في مشاريع البرمجيات الحديثة، القدرة على **الحصول على عدد صفحات المخطط** بسرعة يمكن أن توفر الكثير من الوقت—خاصة عندما تحتاج إلى إنشاء تقارير أو أتمتة خطوط توثيق المستندات. يوضح لك هذا الدليل بالضبط كيفية استخدام GroupDocs.Metadata للـ Java لاستخراج عدد الصفحات وإحصاءات نصية مفيدة أخرى من ملفات المخططات مثل VDX و VSDX وغيرها.

## إجابات سريعة
- **ماذا يعني “الحصول على عدد صفحات المخطط”؟** يُعيد العدد الإجمالي للصفحات (أو الأوراق) داخل ملف المخطط.  
- **أي مكتبة توفر هذه الميزة؟** GroupDocs.Metadata للـ Java.  
- **هل أحتاج إلى ترخيص؟** النسخة التجريبية المجانية تكفي للتقييم؛ يلزم الحصول على ترخيص دائم للإنتاج.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.  
- **هل يمكنني معالجة مخططات متعددة في حلقة؟** نعم—فقط أنشئ كائن `Metadata` لكل ملف داخل الحلقة.

## ما هو “الحصول على عدد صفحات المخطط”؟
الحصول على عدد صفحات المخطط يعني استعلام بيانات التعريف الخاصة بالمخطط لاكتشاف عدد الصفحات أو اللوحات الفردية التي يحتويها الملف. هذه المعلومات هي جزء من إحصاءات المستند التي تُظهرها GroupDocs.Metadata.

## لماذا تستخدم GroupDocs.Metadata للـ Java؟
- **استخراج سريع وخفيف** – لا حاجة لتصوير المخطط بالكامل.  
- **دعم واسع للملفات** – يعمل مع VDX و VSDX والعديد من أنواع المخططات الأخرى.  
- **واجهة برمجة تطبيقات بسيطة** – بضع أسطر من الشيفرة تمنحك عدد الصفحات، المؤلف، تاريخ الإنشاء، وأكثر.  

## المتطلبات المسبقة
- **GroupDocs.Metadata للـ Java** (الإصدار 24.12 أو أحدث).  
- **JDK 8+** مثبت على جهازك.  
- بيئة تطوير متكاملة مثل IntelliJ IDEA أو Eclipse.  
- Maven لإدارة الاعتمادات.  

## إعداد GroupDocs.Metadata للـ Java

### استخدام Maven
أضف المستودع والاعتماد إلى ملف `pom.xml` الخاص بك تمامًا كما هو موضح أدناه:

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
إذا كنت تفضل عدم استخدام Maven، قم بتحميل أحدث ملف JAR من صفحة الإصدار الرسمية: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### الحصول على الترخيص
- **نسخة تجريبية مجانية** – قم بتحميل واستكشاف جميع الميزات دون تكلفة.  
- **ترخيص مؤقت** – اطلب مفتاحًا مؤقتًا للاختبار غير المحدود.  
- **ترخيص كامل** – اشترِ لاستخدام غير محدود في الإنتاج.  

## التهيئة الأساسية

فيما يلي الحد الأدنى من الشيفرة اللازمة للبدء في العمل مع ملف مخطط. يَـُـعِد هذا المقتطف **كائن Metadata**، وهو نقطة الدخول لجميع العمليات اللاحقة، بما في ذلك الحصول على عدد صفحات المخطط.

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

## كيفية قراءة إحصاءات المخطط باستخدام GroupDocs.Metadata للـ Java

الآن بعد أن أصبحت المكتبة جاهزة، دعنا نتبع الخطوات الدقيقة لاسترجاع عدد الصفحات وإحصاءات أخرى.

### الخطوة 1: الحصول على الحزمة الجذرية

كل نوع من المخططات له حزمة جذرية محددة توفر الوصول إلى بيانات التعريف الخاصة به. استخدم الطريقة العامة `getRootPackageGeneric()` لجلبها.

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

### الخطوة 2: الوصول إلى إحصاءات المستند (الحصول على عدد صفحات المخطط)

مع وجود الحزمة الجذرية، يمكنك استدعاء `getDocumentStatistics()` ثم `getPageCount()` للحصول على **عدد صفحات المخطط**.

```java
            int pageCount = root.getDocumentStatistics().getPageCount();
            System.out.println("Page Count: " + pageCount);
        }
    }
}
```

**شرح**: تُعيد `getDocumentStatistics()` كائنًا يحتوي على عدة مقاييس مفيدة، بما في ذلك عدد الصفحات. وبالتالي فإن المتغير `pageCount` يمثل إجمالي الصفحات في المخطط.

### الخطوة 3: معالجة الاستثناءات بلطف

يمكن أن تفشل العمليات المتعلقة بالملفات لأسباب متعددة (ملف مفقود، تنسيق غير مدعوم، إلخ). احط الشيفرة بكتلة try‑catch لتظهر رسائل خطأ واضحة.

```java
        } catch (Exception e) {
            System.err.println("Error occurred while processing diagram metadata: " + e.getMessage());
        }
    }
}
```

## التطبيقات العملية

| حالة الاستخدام | كيف يساعد عدد الصفحات |
|----------------|------------------------|
| **إدارة المشاريع** | تقدير الجهد بسرعة عن طريق عد الصفحات في المخططات الانسيابية أو مخططات الهندسة المعمارية. |
| **التقارير الآلية** | إنشاء جداول ملخصة تسرد كل مخطط وعدد صفحاته لمراجعات أصحاب المصلحة. |
| **تحليل البيانات** | إدخال مقاييس عدد الصفحات إلى لوحات التحكم لمراقبة نمو الوثائق مع مرور الوقت. |

## اعتبارات الأداء

- **إدارة الموارد**: استخدم try‑with‑resources في Java (كما هو موضح) لإغلاق كائن `Metadata` تلقائيًا وتحرير الذاكرة.  
- **معالجة دفعات**: عند التعامل مع العديد من المخططات، أعد استخدام كائن `Metadata` واحد لكل ملف وتجنب تحميل بيانات غير ضرورية.  

## المشكلات الشائعة والحلول

- **الملف غير موجود** – تحقق مرة أخرى من `inputPath` وتأكد من وجود الملف على القرص.  
- **تنسيق غير مدعوم** – تأكد من أن نوع المخطط الخاص بك (مثال: VDX) مدرج في قائمة التنسيقات المدعومة للإصدار الذي تستخدمه.  
- **خطأ ترخيص** – تأكد من تطبيق مفتاح ترخيص تجريبي أو كامل صالح قبل إنشاء كائن `Metadata`.  

## الأسئلة المتكررة

**س:** ما تنسيقات الملفات التي يدعمها GroupDocs.Metadata للمخططات؟  
**ج:** يدعم VDX و VSDX والعديد من تنسيقات المخططات الشائعة المستخدمة في بيئات المؤسسات.

**س:** هل يمكنني استخدام GroupDocs.Metadata مع مستندات غير المخططات؟  
**ج:** نعم، تعمل المكتبة مع ملفات PDF، وWord، وجداول البيانات، وأكثر، مما يوفر تجربة استخراج بيانات تعريف موحدة.

**س:** كيف أتعامل مع تنسيقات الملفات غير المدعومة؟  
**ج:** تحقق من امتداد الملف مقابل القائمة المدعومة في الوثائق. بالنسبة للتنسيقات غير المعروفة، فكر في تحويلها إلى نوع مدعوم أولاً.

**س:** هل هناك حد لعدد المخططات التي يمكنني معالجتها في آن واحد؟  
**ج:** لا يوجد حد صريح، لكن معالجة دفعة كبيرة جدًا قد تتطلب الانتباه لاستخدام الذاكرة واستراتيجيات الخيوط.

**س:** ماذا أفعل إذا واجهت خطأً في التهيئة؟  
**ج:** تحقق مرة أخرى من مسار الملف، وتأكد من إضافة ملفات JAR بشكل صحيح إلى classpath، وتأكد من تطبيق ترخيص صالح (حتى لو كان تجريبيًا).

## الخطوات التالية

- استكشاف إحصاءات إضافية مثل المؤلف، تاريخ الإنشاء، والخصائص المخصصة.  
- دمج منطق عدد الصفحات مع فحص نظام الملفات لمعالجة مجلدات كاملة من المخططات.  
- مراجعة مرجع API الرسمي للحصول على خيارات تخصيص أعمق.

## الموارد
- [الوثائق](https://docs.groupdocs.com/metadata/java/)
- [مرجع API](https://reference.groupdocs.com/metadata/java/)
- [تحميل](https://releases.groupdocs.com/metadata/java/)
- [مستودع GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [منتدى الدعم المجاني](https://forum.groupdocs.com/c/metadata/)
- [طلب ترخيص مؤقت](https://purchase.groupdocs.com/temporary-license/) 

---

**آخر تحديث:** 2026-03-20  
**تم الاختبار مع:** GroupDocs.Metadata 24.12 للـ Java  
**المؤلف:** GroupDocs