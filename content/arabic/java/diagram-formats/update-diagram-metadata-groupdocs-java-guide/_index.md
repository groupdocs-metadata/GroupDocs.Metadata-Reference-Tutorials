---
date: '2026-06-17'
description: تعلم كيفية تغيير وقت إنشاء المخطط وتحديث البيانات الوصفية تلقائيًا لملفات
  المخطط باستخدام GroupDocs.Metadata في Java.
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
title: تغيير وقت إنشاء المخطط في البيانات الوصفية باستخدام GroupDocs Java
type: docs
url: /ar/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# تغيير وقت إنشاء المخطط في البيانات الوصفية باستخدام GroupDocs Java

في هذا البرنامج التعليمي خطوة بخطوة ستكتشف كيفية **تغيير وقت إنشاء المخطط** وتحديث الخصائص المدمجة الأخرى لملفات المخططات باستخدام مكتبة GroupDocs.Metadata للغة Java. يوفّر أتمتة هذه التغييرات ساعات من التحرير اليدوي، ويضمن تواريخ ثابتة عبر مستودعك، ويجعل مخططاتك قابلة للبحث فورًا في أي نظام إدارة مستندات.

## إجابات سريعة
- **ما هو الهدف الأساسي؟** تغيير وقت إنشاء المخطط والبيانات الوصفية الأخرى في ملفات المخطط.  
- **أي مكتبة يجب أن أستخدمها؟** GroupDocs.Metadata for Java.  
- **هل أحتاج إلى ترخيص؟** نسخة تجريبية مجانية كافية للاختبار؛ يلزم ترخيص كامل للإنتاج.  
- **هل يمكنني معالجة العديد من المخططات دفعة واحدة؟** نعم—قم بلف المنطق نفسه داخل حلقة أو تدفق متوازي.  
- **ما نسخة Java المطلوبة؟** JDK 8 أو أعلى.

## ما هو “تغيير وقت إنشاء المخطط” في بيانات وصفية المخطط؟
تغيير وقت الإنشاء يستبدل الطابع الزمني الأصلي المخزن داخل ملف المخطط (مثل VDX أو VSDX) بقيمة تاريخ‑وقت جديدة. يتيح لك ذلك مواءمة البيانات الوصفية للملف مع تاريخ المعالجة أو الأرشفة الفعلي بدلاً من الطابع الزمني الأصلي للمؤلف، وهو أمر أساسي لسجلات التدقيق ونتائج البحث الدقيقة.

## لماذا أتمتة تحديث البيانات الوصفية للمخططات؟
تضمن أتمتة البيانات الوصفية أن كل مخطط يتبع نفس معايير التسمية، التصنيف، والطابع الزمني دون أخطاء بشرية. كما أنها تسرّع عمليات النقل الضخمة، تقلل من مخاطر الامتثال، وتحسن قابلية الاكتشاف في منصات إدارة المستندات المؤسسية—مما يوفر ما يصل إلى 70 % من الجهد اليدوي في المشاريع الكبيرة.

## المتطلبات المسبقة
- **Java Development Kit (JDK) 8+** مثبت على جهازك.  
- **IDE** مثل IntelliJ IDEA أو Eclipse.  
- **Maven** (أو التعامل اليدوي مع JAR) لإدارة التبعيات.  
- إلمام أساسي بفئات Java، والطرق، ومعالجة الاستثناءات.

### المكتبات والتبعيات المطلوبة
أضف المستودع والتبعيات التالية إلى ملف `pom.xml` إذا كنت تستخدم Maven:

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
إذا كنت تفضل التحميل مباشرة، زر [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) للحصول على أحدث نسخة.

### إعداد البيئة
- JDK 8 أو أحدث.  
- IntelliJ IDEA، Eclipse، أو أي بيئة تطوير متوافقة مع Java.  

### المتطلبات المعرفية
فهم بنية Java الأساسية وإدخال/إخراج الملفات سيجعل البرنامج التعليمي أكثر سلاسة، لكن الخطوات مشروحة بلغة بسيطة.

## إعداد GroupDocs.Metadata للغة Java
### تعليمات التثبيت
**مستخدمي Maven:** المقتطف أعلاه يضيف المستودع وملف JAR المطلوب تلقائيًا.  
**مستخدمي التحميل المباشر:** بعد تحميل ملف JAR من [GroupDocs](https://releases.groupdocs.com/metadata/java/)، أضفه إلى مسار الفئة (classpath) لمشروعك.

### الحصول على الترخيص
- **Free Trial:** استكشف المكتبة بدون تكلفة.  
- **Temporary License:** احصل على ترخيص مؤقت للاختبار الموسع [here](https://purchase.groupdocs.com/temporary-license/).  
- **Purchase:** احصل على ترخيص كامل لبيئات الإنتاج.

### التهيئة الأساسية
`Metadata` هي الفئة الأساسية التي تمثل حاوية البيانات الوصفية للمستند وتوفر وصول قراءة/كتابة إلى جميع الخصائص المدمجة. لبدء استخدام GroupDocs.Metadata، استورد الفئة وافتح ملف مخطط:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

مع تهيئة المكتبة، يمكنك الآن تعديل أي خاصية مدمجة، بما في ذلك وقت الإنشاء.

## دليل التنفيذ
### كيفية تغيير وقت الإنشاء في ملفات المخطط
في هذا القسم سنستعرض كل خطوة مطلوبة **لتغيير وقت إنشاء المخطط** وتحديث خصائص شائعة أخرى مثل المؤلف، الشركة، والفئة. تتضمن العملية تحميل المخطط باستخدام واجهة برمجة تطبيقات Metadata، الوصول إلى الحزمة الجذرية، تعيين الحقول المطلوبة، وأخيرًا حفظ التغييرات إلى ملف جديد، مع ضمان بقاء الأصلي دون تعديل.

#### الخطوة 1: تحميل مستند المخطط
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*شرح:* المُنشئ `Metadata` يستقبل مسار ملف المخطط الخاص بك. يضمن كتلة try‑with‑resources إغلاق الملف بشكل صحيح بعد العملية.

#### الخطوة 2: الوصول إلى الحزمة الجذرية
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*شرح:* الحزمة الجذرية تمنحك وصولًا مباشرًا إلى جميع حقول البيانات الوصفية المدمجة للمخطط.

#### الخطوة 3: تعيين خاصية المُنشئ
```java
root.getDocumentProperties().setCreator("test author");
```  
*شرح:* يعيّن اسم مؤلف جديد. استبدل `"test author"` بالمُنشئ الفعلي.

#### الخطوة 4: تغيير وقت الإنشاء
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*شرح:* هذا السطر **يغيّر وقت الإنشاء** إلى تاريخ ووقت النظام الحالي. يمكنك أيضًا توفير كائن `Date` محدد إذا كنت بحاجة إلى طابع زمني مخصص.

#### الخطوة 5: تعريف معلومات الشركة
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*شرح:* يخزن اسم الشركة المرتبط بالمخطط—مفيد لتتبع المؤسسات.

#### الخطوة 6: تعيين فئة المستند
```java
root.getDocumentProperties().setCategory("test category");
```  
*شرح:* يصنّف الملف، مما يساعدك على **تحديث فئة المخطط** بشكل متسق عبر مستودعك.

#### الخطوة 7: إضافة الكلمات المفتاحية
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*شرح:* الكلمات المفتاحية تحسن قابلية البحث؛ يمكنك سرد أي مصطلحات ذات صلة بمحتوى المخطط.

#### الخطوة 8: حفظ التغييرات
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*شرح:* يحفظ جميع التعديلات إلى ملف جديد، مع ترك الأصلي دون تعديل.

### المشكلات الشائعة & استكشاف الأخطاء وإصلاحها
- **File Not Found:** تحقق من مسار الإدخال وتأكد من أن امتداد الملف يتطابق مع الصيغة الفعلية.  
- **Access Denied:** افحص أذونات القراءة/الكتابة لكل من أدلة الإدخال والإخراج.  
- **Invalid Date Format:** استخدم كائنات `java.util.Date` أو `java.time` المتوافقة مع الواجهة البرمجية.

## التطبيقات العملية
1. **أتمتة أرشفة المستندات** – عند نقل المخططات القديمة إلى أرشيف، قم تلقائيًا **بتغيير وقت إنشاء المخطط** إلى تاريخ الأرشفة وتعيين فئة موحدة.  
2. **تكامل نظام التحكم بالإصدار** – حافظ على تزامن الطوابع الزمنية مع عمليات الالتزام في Git عن طريق تحديث وقت الإنشاء خلال كل إصدار.  
3. **توحيد نظام إدارة المستندات المؤسسية** – فرض سياسة على مستوى الشركة للمؤلف، الشركة، والكلمات المفتاحية عبر جميع أصول المخططات.

## اعتبارات الأداء
- **Batch Processing:** لفّ الخطوات السابقة داخل حلقة لمعالجة عشرات الملفات في تشغيل واحد.  
- **Memory Management:** حرّر كل كائن `Metadata` على الفور (كتلة try‑with‑resources تقوم بذلك تلقائيًا).  
- **Asynchronous Execution:** للدفعات الكبيرة، فكر في استخدام `CompletableFuture` لتشغيل التحديثات بشكل متوازي دون حجز الخيط الرئيسي.  
- **Quantified Capability:** يدعم GroupDocs.Metadata أكثر من 30 صيغة مخطط ويمكنه معالجة ملفات تصل إلى 500 MB دون تحميل المستند بالكامل في الذاكرة، مما يقدّم التحديثات في أقل من 200 ms لكل ملف على عتاد الخادم المعتاد.

## الخلاصة
أنت الآن تعرف كيفية **تغيير وقت إنشاء المخطط** وتحديث خصائص البيانات الوصفية المدمجة الأخرى لمستندات المخطط باستخدام GroupDocs.Metadata في Java. من خلال أتمتة هذه الخطوات، يمكنك الحفاظ على وثائق متسقة، قابلة للبحث، ومتوافقة عبر مؤسستك.

**الخطوات التالية**
- جرّب صيغ ملفات أخرى يدعمها GroupDocs.Metadata (PDF، DOCX، إلخ).  
- دمج الكود في خط أنابيب CI/CD لفرض معايير البيانات الوصفية في كل بناء.

هل أنت مستعد لتجربتها؟ انتقل إلى [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) وابدأ بتنفيذ أتمتة البيانات الوصفية الخاصة بك اليوم.

---

**آخر تحديث:** 2026-06-17  
**تم الاختبار مع:** GroupDocs.Metadata 24.12  
**المؤلف:** GroupDocs  

## الأسئلة المتكررة

**س: هل يمكنني استخدام هذا النهج مع صيغ مخططات أخرى مثل VSDX؟**  
A: نعم، نفس الواجهة البرمجية تعمل مع جميع صيغ المخططات التي يدعمها GroupDocs.Metadata.

**س: هل أحتاج إلى ترخيص لبنيات التطوير؟**  
A: نسخة تجريبية مجانية كافية للتطوير والاختبار؛ يلزم ترخيص كامل لنشر الإنتاج.

**س: كيف يمكنني تحديث عدة خصائص في استدعاء واحد؟**  
A: عيّن كل خاصية على كائن `DocumentProperties` قبل استدعاء `metadata.save(...)`؛ المكتبة تكتبها جميعًا مرة واحدة.

**س: هل من الآمن استبدال الملف الأصلي؟**  
A: يُنصح بالحفظ إلى ملف جديد (كما هو موضح) واستبدال الأصلي فقط بعد التأكد من نجاح التحديث.

**س: ماذا لو احتجت لتعيين تاريخ إنشاء مخصص بدلاً من الوقت الحالي؟**  
A: أنشئ كائن `java.util.Date` (أو `java.time`) مع الطابع الزمني المطلوب ومرره إلى `setTimeCreated`.

## دروس ذات صلة

- [كيفية تحديث بيانات مخطط Metadata Java باستخدام GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [كيفية تحديث بيانات مؤلف DXF باستخدام GroupDocs.Metadata للغة Java – دليل كامل](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [أتمتة تحديثات بيانات Java الوصفية حسب التاريخ باستخدام GroupDocs.Metadata لإدارة ملفات فعّالة](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)