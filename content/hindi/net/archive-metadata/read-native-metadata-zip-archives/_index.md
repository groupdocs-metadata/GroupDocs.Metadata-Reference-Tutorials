---
title: .NET में ZIP अभिलेखागार से मूल मेटाडेटा गुण पढ़ें
linktitle: .NET में ZIP अभिलेखागार से मूल मेटाडेटा गुण पढ़ें
second_title: GroupDocs.Metadata .NET एपीआई
description: .NET के लिए GroupDocs.Metadata का उपयोग करके ZIP संग्रह से मेटाडेटा निकालने का तरीका जानें। मूल गुण पढ़ने के लिए चरण-दर-चरण निर्देशों का अन्वेषण करें।
weight: 13
url: /hi/net/archive-metadata/read-native-metadata-zip-archives/
---

# .NET में ZIP अभिलेखागार से मूल मेटाडेटा गुण पढ़ें

## परिचय
ज़िप अभिलेखागार का उपयोग आम तौर पर फ़ाइलों को संपीड़ित करने और एक साथ बंडल करने के लिए किया जाता है। .NET अनुप्रयोगों में ज़िप फ़ाइलों के साथ काम करते समय, इन अभिलेखागार से मेटाडेटा गुण निकालना अक्सर आवश्यक होता है। इस ट्यूटोरियल में, हम चरण दर चरण ZIP फ़ाइलों से मूल मेटाडेटा गुणों को पढ़ने के लिए .NET के लिए GroupDocs.Metadata का उपयोग करने का तरीका जानेंगे।
## आवश्यक शर्तें
आरंभ करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- .NET लाइब्रेरी के लिए GroupDocs.Metadata स्थापित किया गया। आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/metadata/net/).
- C# और .NET विकास परिवेश का बुनियादी ज्ञान।

## नामस्थान आयात करें
अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करके प्रारंभ करें:
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```
## चरण 1: मेटाडेटा ऑब्जेक्ट को आरंभ करें
 सबसे पहले, एक बनाएं`Metadata` अपनी ज़िप फ़ाइल को पथ प्रदान करके ऑब्जेक्ट करें।
```csharp
using (Metadata metadata = new Metadata("Your Input File.zip"))
{
    // यहां मेटाडेटा निष्कर्षण विधियों तक पहुंचें
}
```
## चरण 2: ज़िप रूट पैकेज तक पहुंचें
इसके बाद, ज़िप फ़ाइल के लिए रूट पैकेज पुनर्प्राप्त करें।
```csharp
var root = metadata.GetRootPackage<ZipRootPackage>();
```
## चरण 3: ज़िप पुरालेख गुण पढ़ें
अब आप ज़िप संग्रह की विभिन्न संपत्तियों तक पहुंच सकते हैं, जैसे टिप्पणी और प्रविष्टियों की कुल संख्या।
```csharp
Console.WriteLine(root.ZipPackage.Comment);
Console.WriteLine(root.ZipPackage.TotalEntries);
```
## चरण 4: फ़ाइलों के माध्यम से पुनरावृति करें
व्यक्तिगत फ़ाइल मेटाडेटा तक पहुँचने के लिए ज़िप संग्रह के भीतर प्रत्येक फ़ाइल के माध्यम से पुनरावृति करें।
```csharp
foreach (var file in root.ZipPackage.Files)
{
    Console.WriteLine("File Name: " + file.Name);
    Console.WriteLine("Compressed Size: " + file.CompressedSize);
    Console.WriteLine("Compression Method: " + file.CompressionMethod);
    Console.WriteLine("File Flags: " + file.Flags);
    Console.WriteLine("Modification Date Time: " + file.ModificationDateTime);
    Console.WriteLine("Uncompressed Size: " + file.UncompressedSize);
    // यदि आवश्यक हो तो फ़ाइल नाम को डिकोड करें
    var encoding = Encoding.UTF8;
    Console.WriteLine("Decoded File Name: " + encoding.GetString(file.RawName));
}
```

## निष्कर्ष
इस ट्यूटोरियल में, आपने सीखा कि ज़िप अभिलेखागार से मेटाडेटा गुण निकालने के लिए .NET के लिए GroupDocs.Metadata का उपयोग कैसे करें। यह संपीड़ित फ़ाइलों से निपटने वाले अनुप्रयोगों के लिए अमूल्य हो सकता है, जिससे आप प्रत्येक फ़ाइल के भीतर एम्बेडेड आवश्यक विवरणों तक पहुंच प्राप्त कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### .NET के लिए GroupDocs.Metadata क्या है?
.NET के लिए GroupDocs.Metadata एक शक्तिशाली लाइब्रेरी है जो डेवलपर्स को विभिन्न फ़ाइल स्वरूपों से जुड़े मेटाडेटा को पढ़ने, लिखने और हेरफेर करने की अनुमति देती है।
### मैं GroupDocs.Metadata के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?
 आप यहां से अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### मुझे .NET के लिए GroupDocs.Metadata का संपूर्ण दस्तावेज़ कहां मिल सकता है?
 दस्तावेज़ तक पहुँचा जा सकता है[यहाँ](https://tutorials.groupdocs.com/metadata/net/).
### क्या मैं .NET के लिए GroupDocs.Metadata निःशुल्क आज़मा सकता हूँ?
 हाँ, आप निःशुल्क परीक्षण संस्करण डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं .NET के लिए GroupDocs.Metadata के बारे में समर्थन कैसे प्राप्त कर सकता हूँ या प्रश्न कैसे पूछ सकता हूँ?
 समर्थन और चर्चा के लिए, यहां जाएं[GroupDocs.Metadata फ़ोरम](https://forum.groupdocs.com/c/metadata/14).