---
title: .NET का उपयोग करके PDF में अंतर्निहित गुण अपडेट करें
linktitle: .NET का उपयोग करके PDF में अंतर्निहित गुण अपडेट करें
second_title: GroupDocs.Metadata .NET एपीआई
description: .NET के लिए C# और GroupDocs.Metadata का उपयोग करके PDF दस्तावेज़ गुणों को अपडेट करना सीखें। प्रोग्रामेटिक रूप से लेखक, शीर्षक, कीवर्ड और बहुत कुछ संशोधित करें।
weight: 15
url: /hi/net/pdf-metadata/update-built-in-properties-pdfs/
type: docs
---
# .NET का उपयोग करके PDF में अंतर्निहित गुण अपडेट करें

## परिचय
इस ट्यूटोरियल में, हम सीखेंगे कि PDF दस्तावेज़ों के अंतर्निहित गुणों को अपडेट करने के लिए .NET के लिए GroupDocs.Metadata का उपयोग कैसे करें। यह लाइब्रेरी विभिन्न दस्तावेज़ प्रारूपों के भीतर मेटाडेटा में हेरफेर करने के लिए उपकरणों का एक शक्तिशाली सेट प्रदान करती है। हम C# का उपयोग करके PDF फ़ाइल में लेखक, शीर्षक, निर्माण तिथि, कीवर्ड, निर्माता और निर्माता जैसे गुणों को संशोधित करने के लिए आवश्यक चरणों से गुजरेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित चीज़ें मौजूद हैं:
-  .NET लाइब्रेरी के लिए GroupDocs.Metadata: लाइब्रेरी को यहाँ से डाउनलोड करें[यहाँ](https://releases.groupdocs.com/metadata/net/).
- विज़ुअल स्टूडियो: C# कोड लिखने और निष्पादित करने के लिए विज़ुअल स्टूडियो स्थापित करें।
- C# की बुनियादी समझ: C# प्रोग्रामिंग भाषा से परिचित होना अनुशंसित है।

## नामस्थान आयात करें
अपने C# प्रोजेक्ट में आवश्यक नामस्थानों को शामिल करके आरंभ करें:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## चरण 1: मेटाडेटा ऑब्जेक्ट को आरंभ करें
 आरंभ करने से शुरू करें`Metadata`अपनी पीडीएफ फ़ाइल के पथ के साथ ऑब्जेक्ट करें:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // आपका कोड यहां जाएगा
}
```
## चरण 2: पीडीएफ रूट पैकेज तक पहुंचें
 इसके बाद, विशेष रूप से पीडीएफ का उपयोग करने के लिए रूट पैकेज पुनः प्राप्त करें`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## चरण 3: दस्तावेज़ गुण अद्यतन करें
 अब, पीडीएफ दस्तावेज़ के वांछित गुणों को अपडेट करें`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## चरण 4: परिवर्तन सहेजें
गुणों को संशोधित करने के बाद, परिवर्तनों को वापस पीडीएफ फ़ाइल में सहेजें:
```csharp
metadata.Save("Your Output File Path");
```
## चरण 5: अद्यतन गुण पुनः प्राप्त करें
परिवर्तनों को सत्यापित करने के लिए, मेटाडेटा को पुनः लोड करें और अद्यतन गुणों को पुनः प्राप्त करें:
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने पता लगाया कि पीडीएफ दस्तावेज़ों की अंतर्निहित संपत्तियों को प्रोग्रामेटिक रूप से अपडेट करने के लिए .NET के लिए GroupDocs.Metadata का लाभ कैसे उठाया जाए। उल्लिखित चरणों का पालन करके, आप C# का उपयोग करके पीडीएफ फाइलों के भीतर मेटाडेटा को कुशलतापूर्वक प्रबंधित और संशोधित कर सकते हैं। व्यापक मेटाडेटा हेरफेर के लिए GroupDocs.Metadata द्वारा दी जाने वाली अधिक सुविधाओं और क्षमताओं का पता लगाने के लिए स्वतंत्र महसूस करें।

## अक्सर पूछे जाने वाले प्रश्न
### प्रश्न: .NET के लिए GroupDocs.Metadata क्या है?
A: GroupDocs.Metadata for .NET एक लाइब्रेरी है जो डेवलपर्स को प्रोग्रामेटिक रूप से विभिन्न दस्तावेज़ प्रारूपों में मेटाडेटा को पढ़ने, संपादित करने, हटाने और हेरफेर करने की अनुमति देती है।
### प्रश्न: मैं .NET के लिए GroupDocs.Metadata हेतु दस्तावेज़ कहां पा सकता हूं?
 उत्तर: आप दस्तावेज़ तक पहुंच सकते हैं[यहाँ](https://tutorials.groupdocs.com/metadata/net/).
### प्रश्न: मैं .NET के लिए GroupDocs.Metadata कैसे डाउनलोड कर सकता हूं?
 A: आप .NET के लिए GroupDocs.Metadata को यहां से डाउनलोड कर सकते हैं[इस लिंक](https://releases.groupdocs.com/metadata/net/).
### प्रश्न: क्या कोई निःशुल्क परीक्षण उपलब्ध है?
 उत्तर: हां, आप निःशुल्क परीक्षण संस्करण प्राप्त कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### प्रश्न: मुझे .NET के लिए GroupDocs.Metadata हेतु समर्थन कहां से मिल सकता है?
 उत्तर: सहायता के लिए, GroupDocs.Metadata फ़ोरम पर जाएँ[यहाँ](https://forum.groupdocs.com/c/metadata/14).