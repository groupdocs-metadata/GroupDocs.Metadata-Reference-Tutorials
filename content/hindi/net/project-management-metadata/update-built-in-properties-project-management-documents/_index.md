---
title: .NET प्रोजेक्ट प्रबंधन दस्तावेज़ों में अंतर्निहित गुण अपडेट करें
linktitle: .NET प्रोजेक्ट प्रबंधन दस्तावेज़ों में अंतर्निहित गुण अपडेट करें
second_title: GroupDocs.Metadata .NET एपीआई
description: .NET के लिए GroupDocs.Metadata के साथ .NET प्रोजेक्ट प्रबंधन दस्तावेज़ों में मेटाडेटा अपडेट करने का तरीका जानें। दस्तावेज़ प्रबंधन को कुशलतापूर्वक बढ़ाएँ।
weight: 12
url: /hi/net/project-management-metadata/update-built-in-properties-project-management-documents/
---
## परिचय
इस ट्यूटोरियल में, हम .NET के लिए GroupDocs.Metadata का उपयोग करके .NET प्रोजेक्ट प्रबंधन दस्तावेज़ों में अंतर्निहित गुणों को अपडेट करने का तरीका जानेंगे। यह लाइब्रेरी Microsoft Project (MPP) फ़ाइलों जैसे प्रोजेक्ट प्रबंधन दस्तावेज़ों सहित विभिन्न फ़ाइल स्वरूपों के लिए मेटाडेटा के कुशल हेरफेर को सक्षम बनाती है।
## आवश्यक शर्तें
नीचे दिए गए चरणों में आगे बढ़ने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
- आपकी मशीन पर विज़ुअल स्टूडियो स्थापित है।
- C# और .NET विकास की बुनियादी समझ।
-  .NET लाइब्रेरी के लिए GroupDocs.Metadata. आप इसे डाउनलोड कर सकते हैं[यहाँ](https://releases.groupdocs.com/metadata/net/).
- विकासात्मक वातावरण तक पहुंच.

## नामस्थान आयात करें
अपने C# प्रोजेक्ट में आवश्यक नेमस्पेस आयात करके आरंभ करें:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## चरण 1: दस्तावेज़ मेटाडेटा लोड करें
 सबसे पहले, एक उदाहरण बनाएं`Metadata` अपनी इनपुट फ़ाइल के पथ के साथ ऑब्जेक्ट:
```csharp
using (Metadata metadata = new Metadata("YourInputFile"))
{
    var root = metadata.GetRootPackage<ProjectManagementRootPackage>();
    // दस्तावेज़ गुणों तक पहुँचें
}
```
## चरण 2: दस्तावेज़ गुण अपडेट करें
अब, परियोजना प्रबंधन दस्तावेज़ के वांछित अंतर्निहित गुणों को अपडेट करें:
```csharp
root.DocumentProperties.Author = "test author";
root.DocumentProperties.CreationDate = DateTime.Now;
root.DocumentProperties.Company = "GroupDocs";
root.DocumentProperties.Comments = "test comment";
root.DocumentProperties.Keywords = "metadata, built-in, update";
// आवश्यकतानुसार और गुण जोड़ें
```
## चरण 3: संशोधित मेटाडेटा सहेजें
आवश्यक परिवर्तन करने के बाद, अद्यतन मेटाडेटा को वापस फ़ाइल में सहेजें:
```csharp
metadata.Save("YourInputFile");
```

## निष्कर्ष
इस ट्यूटोरियल में, हमने .NET के लिए GroupDocs.Metadata का उपयोग करके प्रोजेक्ट प्रबंधन दस्तावेज़ों के भीतर अंतर्निहित गुणों को अपडेट करने का तरीका बताया। इस लाइब्रेरी का लाभ उठाते हुए, डेवलपर्स कुशलतापूर्वक मेटाडेटा में हेरफेर कर सकते हैं, .NET अनुप्रयोगों के भीतर दस्तावेज़ प्रबंधन क्षमताओं को बढ़ा सकते हैं।

## अक्सर पूछे जाने वाले प्रश्न
### क्या GroupDocs.Metadata विभिन्न परियोजना प्रबंधन फ़ाइल स्वरूपों के साथ संगत है?
हां, GroupDocs.Metadata MPP (Microsoft Project) फ़ाइलों जैसे लोकप्रिय परियोजना प्रबंधन प्रारूपों का समर्थन करता है।
### क्या मैं अंतर्निहित दस्तावेज़ विवरण से परे अन्य मेटाडेटा गुणों में हेरफेर कर सकता हूं?
बिल्कुल! GroupDocs.Metadata फ़ाइल प्रकारों की एक विस्तृत श्रृंखला में मेटाडेटा को प्रबंधित करने के लिए व्यापक क्षमताएं प्रदान करता है।
### मुझे GroupDocs.Metadata के लिए अतिरिक्त दस्तावेज़ और समर्थन कहां मिल सकता है?
 दौरा करना[GroupDocs.मेटाडेटा दस्तावेज़ीकरण](https://tutorials.groupdocs.com/metadata/net/) विस्तृत जानकारी के लिए. विशिष्ट प्रश्नों के लिए, समुदाय से जुड़ें[ग्रुपडॉक्स फ़ोरम](https://forum.groupdocs.com/c/metadata/14).
### क्या GroupDocs.Metadata का परीक्षण करने के लिए कोई निःशुल्क परीक्षण उपलब्ध है?
 हाँ, आप निःशुल्क परीक्षण का उपयोग कर सकते हैं[यहाँ](https://releases.groupdocs.com/).
### मैं GroupDocs.Metadata के लिए अस्थायी लाइसेंस कैसे प्राप्त कर सकता हूँ?
 एक अस्थायी लाइसेंस प्राप्त करें[यहाँ](https://purchase.groupdocs.com/temporary-license/).