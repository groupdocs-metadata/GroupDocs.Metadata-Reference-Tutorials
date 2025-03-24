---
title: .NET में RAR अभिलेखागार से मूल मेटाडेटा गुण पढ़ें
linktitle: .NET में RAR अभिलेखागार से मूल मेटाडेटा गुण पढ़ें
second_title: GroupDocs.Metadata .NET एपीआई
description: C# में .NET के लिए GroupDocs.Metadata का उपयोग करके RAR संग्रह से मेटाडेटा गुण निकालना सीखें। फ़ाइल विवरणों को आसानी से एक्सप्लोर करें।
weight: 10
url: /hi/net/archive-metadata/read-native-metadata-rar-archives/
---
## परिचय
RAR (रोशल आर्काइव) एक लोकप्रिय फ़ाइल प्रारूप है जिसका उपयोग डेटा संपीड़न और संग्रह के लिए किया जाता है। .NET अनुप्रयोगों में RAR फ़ाइलों के साथ काम करते समय, इन अभिलेखागारों में एम्बेडेड मेटाडेटा गुणों को पढ़ना और निकालना अक्सर आवश्यक होता है। यह ट्यूटोरियल आपको RAR अभिलेखागार से मूल मेटाडेटा गुणों तक पहुँचने और निकालने के लिए .NET के लिए GroupDocs.Metadata का उपयोग करने की प्रक्रिया के माध्यम से मार्गदर्शन करेगा।
## आवश्यक शर्तें

आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- C# प्रोग्रामिंग भाषा की बुनियादी समझ।
- आपके विकास मशीन पर Visual Studio स्थापित है।
-  .NET लाइब्रेरी स्थापित करने के लिए GroupDocs.Metadata (देखें[लिंक को डाउनलोड करें](https://releases.groupdocs.com/metadata/net/)).
- परीक्षण प्रयोजनों के लिए RAR संग्रह फ़ाइल तक पहुंच।

## नामस्थान आयात करें
आरंभ करने के लिए, अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करें:
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```

## चरण 1: RAR संग्रह लोड करें
 सबसे पहले, एक आरंभ करें`Metadata` अपनी RAR संग्रह फ़ाइल लोड करके ऑब्जेक्ट:
```csharp
using (Metadata metadata = new Metadata("YourZipFile.rar"))
{
    var root = metadata.GetRootPackage<RarRootPackage>();
```
## चरण 2: RAR संग्रह में कुल प्रविष्टियों तक पहुँचें
RAR संग्रह में प्रविष्टियों (फ़ाइलों/फ़ोल्डरों) की कुल संख्या प्राप्त करें:
```csharp
Console.WriteLine(root.RarPackage.TotalEntries);
```
## चरण 3: संग्रह में फ़ाइलों के माध्यम से पुनरावृति करें
विशिष्ट मेटाडेटा गुणों तक पहुँचने के लिए RAR संग्रह के भीतर प्रत्येक फ़ाइल के माध्यम से लूप करें:
```csharp
foreach (var file in root.RarPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## निष्कर्ष
इस ट्यूटोरियल में, आपने सीखा कि .NET के लिए GroupDocs.Metadata का उपयोग करके RAR अभिलेखागार से मेटाडेटा गुण कैसे निकालें। यह लाइब्रेरी आपके .NET अनुप्रयोगों की क्षमताओं को बढ़ाते हुए, विभिन्न फ़ाइल स्वरूपों में एम्बेडेड मेटाडेटा तक पहुंचने और उपयोग करने की प्रक्रिया को सरल बनाती है।

## अक्सर पूछे जाने वाले प्रश्न
### .NET के लिए GroupDocs.Metadata क्या है?
.NET के लिए GroupDocs.Metadata एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को RAR जैसे अभिलेखागार सहित विभिन्न फ़ाइल स्वरूपों में मेटाडेटा के साथ काम करने की अनुमति देती है।
### मैं .NET के लिए GroupDocs.Metadata के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### क्या GroupDocs.Metadata RAR के अलावा अन्य संग्रह प्रारूपों का समर्थन करता है?
हां, GroupDocs.Metadata ZIP, TAR और 7z सहित संग्रह प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### क्या मैं इस लाइब्रेरी का उपयोग करके मेटाडेटा गुणों को संशोधित कर सकता हूं और उन्हें RAR संग्रह में अपडेट कर सकता हूं?
हाँ, GroupDocs.Metadata आपको समर्थित फ़ाइल स्वरूपों में मेटाडेटा गुणों को अद्यतन करने, हटाने और जोड़ने की अनुमति देता है।
### मुझे GroupDocs.Metadata के लिए अतिरिक्त सहायता या सहायता कहां मिल सकती है?
 दौरा करना[GroupDocs.Metadata फ़ोरम](https://forum.groupdocs.com/c/metadata/14) सामुदायिक समर्थन और चर्चा के लिए।