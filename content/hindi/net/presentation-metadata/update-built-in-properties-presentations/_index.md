---
title: .NET का उपयोग करके प्रस्तुतियों में अंतर्निहित गुण अपडेट करें
linktitle: .NET का उपयोग करके प्रस्तुतियों में अंतर्निहित गुण अपडेट करें
second_title: GroupDocs.Metadata .NET एपीआई
description: GroupDocs.Metadata, एक बहुमुखी मेटाडेटा हेरफेर लाइब्रेरी के साथ .NET का उपयोग करके प्रस्तुतियों में अंतर्निहित गुणों को अपडेट करना सीखें।
weight: 15
url: /hi/net/presentation-metadata/update-built-in-properties-presentations/
---
## परिचय
इस ट्यूटोरियल में, हम GroupDocs.Metadata for .NET की शक्तिशाली क्षमताओं पर गहराई से चर्चा करेंगे, जो .NET फ्रेमवर्क का उपयोग करके दस्तावेज़ों के भीतर मेटाडेटा में हेरफेर करने के लिए डिज़ाइन की गई एक व्यापक लाइब्रेरी है। विशेष रूप से, हम C# का उपयोग करके प्रोग्रामेटिक रूप से प्रस्तुतियों (.PPT और .PPTX फ़ाइलों) में अंतर्निहित गुणों को अपडेट करने पर ध्यान केंद्रित करेंगे।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित हैं:
- विजुअल स्टूडियो: आपके सिस्टम पर स्थापित.
-  .NET के लिए GroupDocs.Metadata: से डाउनलोड और इंस्टॉल किया गया[यहाँ](https://releases.groupdocs.com/metadata/net/).
- बुनियादी C# ज्ञान: C# प्रोग्रामिंग भाषा से परिचित होना।

## नामस्थान आयात करें
अपने C# प्रोजेक्ट में आवश्यक नामस्थान आयात करके प्रारंभ करें:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## चरण 1: प्रेजेंटेशन फ़ाइल लोड करें
 सबसे पहले, एक नया उदाहरण बनाएं`Metadata` अपनी प्रस्तुति फ़ाइल लोड करके:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## चरण 2: अंतर्निहित गुण अपडेट करें
अब, प्रेजेंटेशन के वांछित अंतर्निहित गुणों को अपडेट करें। उदाहरण के लिए, आप लेखक, निर्माण तिथि, कंपनी, श्रेणी, कीवर्ड आदि को संशोधित कर सकते हैं। यहाँ बताया गया है कि आप इसे कैसे कर सकते हैं:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## चरण 3: परिवर्तन सहेजें
गुणों को अद्यतन करने के बाद, परिवर्तनों को प्रस्तुति फ़ाइल में वापस सहेजें:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने पता लगाया कि प्रेजेंटेशन फ़ाइलों में अंतर्निहित गुणों को प्रोग्रामेटिक रूप से अपडेट करने के लिए .NET के लिए GroupDocs.Metadata का उपयोग कैसे करें। इन चरणों का पालन करके, आप अपने .NET अनुप्रयोगों में मेटाडेटा को कुशलतापूर्वक प्रबंधित और संशोधित कर सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### प्रश्न: .NET के लिए GroupDocs.Metadata क्या है?
उत्तर: .NET के लिए GroupDocs.Metadata, .NET फ्रेमवर्क के लिए एक शक्तिशाली मेटाडेटा हेरफेर लाइब्रेरी है, जो डेवलपर्स को विभिन्न दस्तावेज़ प्रारूपों में मेटाडेटा को पढ़ने, लिखने और संपादित करने की अनुमति देता है।
### प्रश्न: मुझे GroupDocs.Metadata के लिए दस्तावेज़ कहां मिल सकते हैं?
 उ: आप विस्तृत दस्तावेज़ तक पहुंच सकते हैं[यहाँ](https://tutorials.groupdocs.com/metadata/net/).
### प्रश्न: मैं GroupDocs.Metadata के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूं?
 उ: आप अस्थायी लाइसेंस प्राप्त कर सकते हैं[यहाँ](https://purchase.groupdocs.com/temporary-license/).
### प्रश्न: क्या GroupDocs.Metadata प्रस्तुतियों के अलावा अन्य फ़ाइल स्वरूपों का समर्थन करता है?
उत्तर: हाँ, GroupDocs.Metadata दस्तावेज़, स्प्रेडशीट, चित्र, वीडियो और बहुत कुछ सहित प्रारूपों की एक विस्तृत श्रृंखला का समर्थन करता है।
### प्रश्न: मुझे GroupDocs.Metadata के बारे में कहां से सहायता मिल सकती है या प्रश्न पूछ सकते हैं?
 उत्तर: सहायता और चर्चा के लिए कृपया यहां जाएं[GroupDocs.Metadata फ़ोरम](https://forum.groupdocs.com/c/metadata/14).