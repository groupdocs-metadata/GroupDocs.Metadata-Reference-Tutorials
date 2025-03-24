---
title: قم بتحديث الخصائص المضمنة في جداول البيانات باستخدام .NET
linktitle: قم بتحديث الخصائص المضمنة في جداول البيانات باستخدام .NET
second_title: GroupDocs.Metadata .NET API
description: تعرف على كيفية تحديث خصائص بيانات التعريف المضمنة في ملفات Excel باستخدام GroupDocs.Metadata لـ .NET. قم بتعديل المؤلف ووقت الإنشاء والشركة والمزيد باستخدام لغة C#.
weight: 14
url: /ar/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## مقدمة
في هذا البرنامج التعليمي، سوف نستكشف كيفية استخدام GroupDocs.Metadata لـ .NET لتحديث الخصائص المضمنة في ملفات جداول البيانات باستخدام C#. GroupDocs.Metadata عبارة عن واجهة برمجة تطبيقات قوية تتيح للمطورين قراءة خصائص بيانات التعريف وتحريرها وإزالتها من تنسيقات الملفات المختلفة، بما في ذلك جداول البيانات. سنركز بشكل خاص على تعديل الخصائص مثل المؤلف ووقت الإنشاء والشركة والفئة والكلمات الرئيسية داخل ملفات Excel.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من أن لديك ما يلي:
- Visual Studio: قم بتثبيت أحدث إصدار من Visual Studio.
-  GroupDocs.Metadata لـ .NET: قم بتنزيل وتثبيت GroupDocs.Metadata لـ .NET من[صفحة التحميل](https://releases.groupdocs.com/metadata/net/).
- المعرفة الأساسية لـ C#: فهم لغة البرمجة C# وإطار عمل .NET.

## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية في مشروع C# الخاص بك:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## الخطوة 1: قم بتحميل ملف جدول البيانات
 أولاً، قم بتهيئة أ`Metadata` كائن عن طريق تحميل ملف جدول البيانات الإدخال:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // الوصول إلى خصائص المستند داخل الجذر
}
```
## الخطوة 2: تحديث الخصائص المضمنة
 قم بالوصول إلى خصائص المستند المضمنة من خلال`SpreadsheetRootPackage` وتعديلها حسب الحاجة:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
تأكد من استبدال العناصر النائبة (`YourAuthorName`, `YourCompany`, `YourCategory`بالقيم الفعلية التي تريد تعيينها للخصائص.
## الخطوة 3: حفظ التغييرات
بعد تحديث الخصائص، احفظ التغييرات مرة أخرى في ملف جدول البيانات:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## خاتمة
في هذا البرنامج التعليمي، أوضحنا كيفية استخدام GroupDocs.Metadata لـ .NET لتحديث الخصائص المضمنة لملفات جداول البيانات برمجيًا. ومن خلال الاستفادة من واجهة برمجة التطبيقات هذه، يمكن للمطورين إدارة البيانات التعريفية بكفاءة داخل مستندات Excel، مما يعزز تنظيم البيانات وإمكانية الوصول إليها.

## الأسئلة الشائعة
### ما هي تنسيقات الملفات التي يدعمها GroupDocs.Metadata؟
يدعم GroupDocs.Metadata مجموعة واسعة من تنسيقات الملفات، بما في ذلك مستندات Microsoft Office وملفات PDF والصور والملفات الصوتية والمزيد.
### هل يمكنني استرداد خصائص البيانات التعريفية الموجودة من الملفات؟
نعم، يمكنك استخراج وقراءة خصائص بيانات التعريف مثل المؤلف وتاريخ الإنشاء والكلمات الأساسية والخصائص المخصصة باستخدام GroupDocs.Metadata.
### هل GroupDocs.Metadata متوافق مع .NET Core؟
نعم، GroupDocs.Metadata متوافق مع كل من .NET Framework و.NET Core.
### هل توفر GroupDocs.Metadata نسخة تجريبية مجانية؟
 نعم، يمكنك تنزيل نسخة تجريبية مجانية من GroupDocs.Metadata من[هنا](https://releases.groupdocs.com/).
### أين يمكنني العثور على دعم لـ GroupDocs.Metadata؟
 للحصول على الدعم والمناقشات، قم بزيارة[منتدى GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).