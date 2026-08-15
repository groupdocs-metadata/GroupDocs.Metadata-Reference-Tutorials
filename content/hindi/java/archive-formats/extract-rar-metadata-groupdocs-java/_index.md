---
date: '2026-06-22'
description: GroupDocs.Metadata for Java का उपयोग करके RAR मेटाडेटा निकालते समय Java
  में संपीड़ित आकार कैसे प्राप्त करें, जानें। चरण‑दर‑चरण गाइड, कोड सैंपल, और सर्वोत्तम
  प्रथाएँ।
keywords:
- get compressed size java
- groupdocs metadata java
- extract rar metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  headline: Get Compressed Size Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  name: Get Compressed Size Java with GroupDocs.Metadata
  steps:
  - name: Initialize the Metadata object
    text: Create a `Metadata` instance by providing the path to the RAR file. This
      object represents the archive in memory and gives you access to its internal
      structure.
  - name: Obtain the root package of the RAR archive
    text: Call `metadata.getRootPackage()` to retrieve the top‑level package that
      contains all entries. The returned `ArchivePackage` lets you enumerate files
      and folders inside the archive.
  - name: Retrieve total entry count
    text: Use `archivePackage.getEntries().size()` to know how many items are stored.
      Knowing the count helps you allocate progress‑tracking structures for batch
      jobs.
  - name: Iterate over each file and read its properties
    text: Loop through `archivePackage.getEntries()`. For every entry that represents
      a file (not a folder), call `entry.getCompressedSize()` to obtain its compressed
      size in bytes. You can also read `entry.getOriginalSize()` if you need the uncompressed
      size for ratio calculations. **Troubleshooting Tips** -
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java is a library that enables reading, updating,
      and managing metadata across more than 50 file formats, including RAR, ZIP,
      and 7z, without requiring file extraction.
    question: What is GroupDocs.Metadata for Java?
  - answer: Visit the [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)
      to acquire a temporary or permanent license; a free trial is available for development.
    question: How do I obtain a license for full access?
  - answer: Yes, the same API supports ZIP, 7z, and several other archive formats,
      allowing a unified codebase for all archive metadata tasks.
    question: Can I use GroupDocs.Metadata with other archive types besides RAR?
  - answer: The main issues are memory consumption and file‑handle limits; mitigate
      them by processing entries one‑by‑one and closing the `Metadata` object promptly.
    question: What are common pitfalls when handling large RAR files?
  - answer: The [GroupDocs free support forum](https://forum.groupdocs.com/c/metadata/)
      provides assistance from both the vendor’s engineers and the community.
    question: Where can I get support if I encounter problems?
  type: FAQPage
title: GroupDocs.Metadata के साथ Java में संपीड़ित आकार प्राप्त करें
type: docs
url: /hi/java/archive-formats/extract-rar-metadata-groupdocs-java/
weight: 1
---

# GroupDocs.Metadata के साथ जावा में संपीड़ित आकार प्राप्त करें

आधुनिक डेटा‑केंद्रित अनुप्रयोगों में, **get compressed size java** एक सामान्य आवश्यकता है जब आपको RAR संग्रहों में संग्रहीत फ़ाइलों के आकार को बिना निकालें निरीक्षण करना होता है। चाहे आप बैकअप‑वेरिफिकेशन यूटिलिटी, डिजिटल‑एसेट‑मैनेजमेंट सिस्टम, या फ़ाइल‑शेयरिंग पोर्टल बना रहे हों, इस मेटाडेटा को पढ़ने से समय और सिस्टम संसाधन दोनों बचते हैं। यह गाइड आपको GroupDocs.Metadata for Java का उपयोग करके प्रत्येक प्रविष्टि का संपीड़ित आकार तेज़, सुरक्षित और न्यूनतम कोड के साथ प्राप्त करने के चरण दिखाता है।

## त्वरित उत्तर
- **कौनसी लाइब्रेरी आवश्यक है?** GroupDocs.Metadata for Java  
- **क्या मैं संपीड़ित आकार प्राप्त कर सकता हूँ?** हाँ – प्रत्येक प्रविष्टि पर `rarFile.getCompressedSize()` कॉल करें  
- **क्या मुझे लाइसेंस चाहिए?** विकास के लिए एक मुफ्त ट्रायल काम करता है; उत्पादन के लिए पूर्ण लाइसेंस आवश्यक है  
- **कौनसा Java संस्करण समर्थित है?** Java 8+ (कोई भी Maven‑संगत पर्यावरण)  
- **क्या बैच प्रोसेसिंग संभव है?** बिल्कुल – RAR फ़ाइलों के फ़ोल्डर पर लूप करें और वही कोड पुनः उपयोग करें  
- **मैं बड़े संग्रहों को कैसे संभालूँ?** प्रविष्टियों को एक‑एक करके प्रोसेस करें और समाप्त होने पर metadata ऑब्जेक्ट को बंद करें  

## “get compressed size java” क्या है और यह क्यों महत्वपूर्ण है?
**Get compressed size java** RAR कंटेनर के भीतर संग्रहीत फ़ाइल का आकार पढ़ता है। यह मान आपको बताता है कि संपीड़न के बाद फ़ाइल कितनी जगह घेरती है, जिससे आप संपीड़न अनुपात की जाँच, ट्रांसफ़र समय का अनुमान, और इन्वेंट्री रिपोर्ट में मूल और संपीड़ित दोनों आकार प्रस्तुत कर सकते हैं।

## RAR संग्रहों से get compressed size java कैसे प्राप्त करें?
GroupDocs.Metadata के साथ RAR संग्रह लोड करें, उसकी प्रविष्टियों पर इटररेट करें, और प्रत्येक फ़ाइल प्रविष्टि पर `getCompressedSize()` मेथड कॉल करें। यह तरीका केवल संग्रह हेडर पढ़ता है, इसलिए कोई एक्सट्रैक्शन या पूरी फ़ाइल लोड नहीं होती, जिससे कई सौ मेगाबाइट के संग्रहों के लिए भी मेमोरी उपयोग 5 MB से कम रहता है।

### चरण 1: Metadata ऑब्जेक्ट को इनिशियलाइज़ करें
`Metadata` इंस्टेंस बनाएं, RAR फ़ाइल का पाथ प्रदान करके। यह ऑब्जेक्ट मेमोरी में संग्रह का प्रतिनिधित्व करता है और आपको उसकी आंतरिक संरचना तक पहुंच देता है।

### चरण 2: RAR संग्रह का रूट पैकेज प्राप्त करें
`metadata.getRootPackage()` कॉल करके वह टॉप‑लेवल पैकेज प्राप्त करें जिसमें सभी प्रविष्टियां होती हैं। लौटाया गया `ArchivePackage` आपको संग्रह के भीतर फ़ाइलों और फ़ोल्डरों को सूचीबद्ध करने देता है।

### चरण 3: कुल प्रविष्टियों की संख्या प्राप्त करें
`archivePackage.getEntries().size()` का उपयोग करके पता लगाएँ कि कितनी वस्तुएँ संग्रहीत हैं। संख्या जानने से आपको बैच जॉब्स के लिए प्रोग्रेस‑ट्रैकिंग संरचनाएँ आवंटित करने में मदद मिलती है।

### चरण 4: प्रत्येक फ़ाइल पर इटररेट करें और उसकी प्रॉपर्टीज़ पढ़ें
`archivePackage.getEntries()` पर लूप करें। प्रत्येक प्रविष्टि जो फ़ाइल का प्रतिनिधित्व करती है (फ़ोल्डर नहीं), उसके लिए `entry.getCompressedSize()` कॉल करके बाइट्स में संपीड़ित आकार प्राप्त करें। यदि आपको अनुपात गणना के लिए अनसंपीड़ित आकार चाहिए तो आप `entry.getOriginalSize()` भी पढ़ सकते हैं।

**समस्या निवारण टिप्स**  
- `rarFilePath` यह सुनिश्चित करें कि यह मौजूद RAR फ़ाइल की ओर इशारा करता है।  
- सुनिश्चित करें कि एप्लिकेशन के पास संग्रह के लिए पढ़ने की अनुमति है।  
- यदि आपको “unsupported format” त्रुटियां मिलती हैं, तो पुष्टि करें कि RAR संस्करण GroupDocs.Metadata के साथ संगत है (यह RAR 4 और RAR 5 का समर्थन करता है)।

## RAR फ़ाइलों के लिए GroupDocs.Metadata का उपयोग क्यों करें?
GroupDocs.Metadata एक हाई‑लेवल API प्रदान करता है जो फ़ाइलों को एक्सट्रैक्ट किए बिना आर्काइव हेडर पढ़ता है, जिससे संपीड़ित आकार, मूल आकार, और टाइमस्टैम्प जैसी प्रॉपर्टीज़ तक तेज़ पहुंच मिलती है। यह RAR 4 और RAR 5 फ़ॉर्मैट्स के साथ काम करता है, बड़े संग्रहों को कुशलता से संभालता है, और फ़ॉर्मैट‑विशिष्ट विवरणों को एब्स्ट्रैक्ट करता है ताकि डेवलपर्स सभी आर्काइव प्रकारों के लिए समान कोड लिख सकें।

## सामान्य उपयोग केस
1. **Data Management Systems** – खोज योग्य इन्वेंट्री के लिए स्वचालित रूप से आर्काइव सामग्री को कैटलॉग करें।  
2. **Digital Asset Management** – संपीड़ित आकार जैसी आर्काइव‑लेवल विवरणों से मीडिया लाइब्रेरी को समृद्ध करें।  
3. **Backup Verification** – भ्रष्टाचार का पता लगाने के लिए संग्रहीत संपीड़ित आकारों की अपेक्षित मानों से तुलना करें।  
4. **File‑Sharing Platforms** – फ़ाइलों को पूरी तरह एक्सट्रैक्ट किए बिना आर्काइव सारांश दिखाएँ, जिससे उपयोगकर्ता अनुभव सुधरता है।  

## प्रदर्शन संबंधी विचार
- **केवल आवश्यक प्रॉपर्टीज़ तक पहुँचें** – यदि आपको केवल फ़ाइल नाम और आकार चाहिए तो भारी मेथड कॉल करने से बचें।  
- **metadata ऑब्जेक्ट्स को डिस्पोज करें** – प्रोसेसिंग के बाद `metadata.close()` कॉल करके नेटिव रिसोर्सेज़ मुक्त करें।  
- **बैच प्रोसेसिंग** – लूप में कई RAR फ़ाइलों को प्रोसेस करें, स्टार्टअप ओवरहेड कम करने के लिए वही JVM पुनः उपयोग करें।  

## अक्सर पूछे जाने वाले प्रश्न

**प्र: GroupDocs.Metadata for Java क्या है?**  
A: GroupDocs.Metadata for Java एक लाइब्रेरी है जो 50 से अधिक फ़ाइल फ़ॉर्मैट्स, जिसमें RAR, ZIP, और 7z शामिल हैं, के मेटाडेटा को पढ़ने, अपडेट करने और प्रबंधित करने में सक्षम बनाती है, बिना फ़ाइल एक्सट्रैक्शन की आवश्यकता के।

**प्र: पूर्ण एक्सेस के लिए लाइसेंस कैसे प्राप्त करूँ?**  
A: पूर्ण लाइसेंस प्राप्त करने के लिए [GroupDocs खरीद पृष्ठ](https://purchase.groupdocs.com/temporary-license/) पर जाएँ; विकास के लिए एक मुफ्त ट्रायल उपलब्ध है।

**प्र: क्या मैं RAR के अलावा अन्य आर्काइव प्रकारों के साथ GroupDocs.Metadata का उपयोग कर सकता हूँ?**  
A: हाँ, वही API ZIP, 7z, और कई अन्य आर्काइव फ़ॉर्मैट्स का समर्थन करता है, जिससे सभी आर्काइव मेटाडेटा कार्यों के लिए एकीकृत कोडबेस संभव होता है।

**प्र: बड़े RAR फ़ाइलों को संभालते समय सामान्य समस्याएँ क्या हैं?**  
A: मुख्य समस्याएँ मेमोरी खपत और फ़ाइल‑हैंडल सीमाएँ हैं; इन्हें एक‑एक करके प्रविष्टियों को प्रोसेस करके और `Metadata` ऑब्जेक्ट को तुरंत बंद करके कम किया जा सकता है।

**प्र: यदि मुझे समस्याएँ आती हैं तो मैं समर्थन कहाँ प्राप्त कर सकता हूँ?**  
A: समर्थन के लिए [GroupDocs मुफ्त समर्थन फ़ोरम](https://forum.groupdocs.com/c/metadata/) देखें, जहाँ विक्रेता के इंजीनियर और समुदाय दोनों मदद प्रदान करते हैं।

## संसाधन
- **डॉक्यूमेंटेशन**: [GroupDocs Metadata Java डॉक्यूमेंटेशन](https://docs.groupdocs.com/metadata/java/)  
- **API रेफ़रेंस**: [GroupDocs API रेफ़रेंस](https://reference.groupdocs.com/metadata/java/)  
- **डाउनलोड**: [नवीनतम संस्करण डाउनलोड्स](https://releases.groupdocs.com/metadata/java/)  
- **GitHub**: [GitHub पर स्रोत कोड](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **मुफ़्त समर्थन**: [GroupDocs फ़ोरम](https://forum.groupdocs.com/c/metadata/)  
- **रिलीज़**: [GroupDocs.Metadata for Java रिलीज़](https://releases.groupdocs.com/metadata/java/)  
- **व्यापक डॉक्यूमेंटेशन**: [व्यापक डॉक्यूमेंटेशन](https://docs.groupdocs.com/metadata/java/)

## निष्कर्ष
अब आप जानते हैं **how to use GroupDocs.Metadata** को RAR संग्रहों से व्यापक मेटाडेटा निकालने के लिए, जिसमें प्रत्येक प्रविष्टि के लिए **get compressed size java** शामिल है। इस पैटर्न को अपने प्रोजेक्ट्स में एकीकृत करें ताकि डेटा‑मैनेजमेंट क्षमताएँ बढ़ें, बैकअप वेरिफिकेशन सुधरे, और फ़ाइल‑सर्च अनुभव समृद्ध हों बिना पूर्ण एक्सट्रैक्शन के ओवरहेड के।

### अगले कदम
आधिकारिक डॉक्यूमेंटेशन में प्रविष्टि टिप्पणियों को अपडेट करने या चेकसम जानकारी निकालने जैसी अतिरिक्त सुविधाओं का अन्वेषण करें, और इस मेटाडेटा एक्सट्रैक्शन को अपने मौजूदा इंडेक्सिंग पाइपलाइन के साथ मिलाने पर विचार करें ताकि एक पूरी तरह से खोज योग्य आर्काइव रिपॉजिटरी बन सके।

---

**अंतिम अपडेट:** 2026-06-22  
**परीक्षण किया गया:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs  

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

```java
// Specify the path to your input RAR file
String rarFilePath = "YOUR_DOCUMENT_DIRECTORY/input.rar";

// Initialize Metadata object with the specified RAR file path\ nMetadata metadata = new Metadata(rarFilePath);
```

```java
// Obtain the root package of the RAR archive
RarRootPackage root = metadata.getRootPackageGeneric();
```

```java
// Retrieve and print the total number of entries in the RAR package
int totalEntries = root.getRarPackage().getTotalEntries();
system.out.println("Total Entries: " + totalEntries);
```

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

## संबंधित ट्यूटोरियल

- [GroupDocs.Metadata का उपयोग करके zip टिप्पणियों को निकालें java – गाइड](/metadata/java/archive-formats/extract-zip-metadata-groupdocs-java-guide/)
- [ZIP टिप्पणी अपडेट करें Java – GroupDocs.Metadata का उपयोग करके ZIP आर्काइव टिप्पणियों को अपडेट करने का तरीका](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [GroupDocs.Metadata for Java के साथ TAR फ़ाइलें पढ़ें और मेटाडेटा निकालें](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)