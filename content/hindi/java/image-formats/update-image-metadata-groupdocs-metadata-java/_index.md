---
date: '2026-06-12'
description: GroupDocs.Metadata for Java के साथ इमेज मेटाडाटा जावा को अपडेट करना सीखें,
  जिसमें Dublin Core, Camera Raw, XMP Basic, और Job Ticket योजनाएँ शामिल हैं।
keywords:
- update image metadata java
- GroupDocs.Metadata Java
- image metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to update image metadata java with GroupDocs.Metadata for
    Java, covering Dublin Core, Camera Raw, XMP Basic, and Job Ticket schemes.
  headline: How to update image metadata java using GroupDocs.Metadata
  type: TechArticle
- description: Learn how to update image metadata java with GroupDocs.Metadata for
    Java, covering Dublin Core, Camera Raw, XMP Basic, and Job Ticket schemes.
  name: How to update image metadata java using GroupDocs.Metadata
  steps:
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Create or Retrieve Dublin Core Package:**'
    text: '**Create or Retrieve Dublin Core Package:**'
  - name: '**Update Properties:**'
    text: '**Update Properties:**'
  - name: '**Save Changes:**'
    text: '**Save Changes:**'
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Create or Retrieve Camera Raw Package:**'
    text: '**Create or Retrieve Camera Raw Package:**'
  - name: '**Update Properties:**'
    text: '**Update Properties:**'
  - name: '**Save Changes:**'
    text: '**Save Changes:**'
  - name: '**Initialize the Metadata Object:**'
    text: '**Initialize the Metadata Object:**'
  - name: '**Replace Existing XMP Basic Package:**'
    text: '**Replace Existing XMP Basic Package:**'
  type: HowTo
- questions:
  - answer: Yes. After creating one `Metadata` instance, you can retrieve and modify
      any combination of packages before calling `save()` once.
    question: Can I update multiple metadata schemes in a single operation?
  - answer: Absolutely. Load the image into a `InputStream` from S3, pass the stream
      to the `Metadata` constructor, and save the result back to the cloud.
    question: Does the library work with images stored in cloud storage (e.g., AWS
      S3)?
  - answer: A valid commercial license is required for production deployments; a trial
      license is limited to evaluation and non‑commercial testing.
    question: Is a commercial license required for production use?
  - answer: GroupDocs.Metadata for Java supports JDK 8, 11, and 17, ensuring compatibility
      with both legacy and modern applications.
    question: What Java versions are officially supported?
  - answer: The API streams data and never loads the entire file into memory, allowing
      you to process very large images without excessive heap usage.
    question: How does the library handle large image files (e.g., >100 MB)?
  type: FAQPage
title: GroupDocs.Metadata का उपयोग करके इमेज मेटाडाटा जावा को कैसे अपडेट करें
type: docs
url: /hi/java/image-formats/update-image-metadata-groupdocs-metadata-java/
weight: 1
---

# GroupDocs.Metadata का उपयोग करके इमेज मेटाडेटा जावा को कैसे अपडेट करें

आधुनिक डिजिटल वर्कफ़्लो में, **updating image metadata java** संपत्तियों को खोज योग्य, अनुपालनयुक्त और डाउनस्ट्रीम प्रोसेसिंग के लिए तैयार रखने के लिए आवश्यक है। चाहे आप फोटो‑मैनेजमेंट ऐप, कंटेंट‑मैनेजमेंट सिस्टम, या स्वचालित अभिलेखीय पाइपलाइन बना रहे हों, प्रोग्रामेटिक रूप से मेटाडेटा संपादित करने की क्षमता अनगिनत मैनुअल घंटे बचाती है। यह गाइड आपको GroupDocs.Metadata for Java के साथ Dublin Core, Camera Raw, XMP Basic, और Basic Job Ticket मेटाडेटा स्कीम को संशोधित करने के लिए आवश्यक सभी चरणों के माध्यम से ले जाता है।

## त्वरित उत्तर
- **कौन सी लाइब्रेरी जावा में इमेज मेटाडेटा को संभालती है?** GroupDocs.Metadata for Java.  
- **क्या मैं एक ही पास में Dublin Core और XMP को अपडेट कर सकता हूँ?** Yes – instantiate a `Metadata` object and work with multiple packages before saving.  
- **क्या मुझे ट्रायल उपयोग के लिए लाइसेंस की आवश्यकता है?** A free trial license unlocks all features; a full license removes usage limits.  
- **कौन सा जावा संस्करण आवश्यक है?** JDK 8 or higher.  
- **क्या डिपेंडेंसी जोड़ने का एकमात्र तरीका Maven है?** Maven is recommended, but you can also download the JAR from the official releases page.

## GroupDocs.Metadata के साथ इमेज मेटाडेटा जावा को कैसे अपडेट करें?
`Metadata` वह मुख्य क्लास है जो इमेज के मेटाडेटा तक पढ़ने/लिखने की पहुंच प्रदान करता है। लक्ष्य इमेज को `Metadata` इंस्टेंस में लोड करें, वांछित मेटाडेटा पैकेज (जैसे, Dublin Core, Camera Raw) प्राप्त या बनाएं, आवश्यक प्रॉपर्टीज़ सेट करें, और `save()` को कॉल करके बदलाव डिस्क पर लिखें। यह प्रवाह JPEG, PNG, TIFF, और कई अन्य फ़ॉर्मेट्स के लिए काम करता है।

### GroupDocs.Metadata for Java को क्यों चुनें?
GroupDocs.Metadata **50+ input and output formats** का समर्थन करता है, कई‑सौ‑पृष्ठ इमेज फ़ाइलों को पूरी फ़ाइल को मेमोरी में लोड किए बिना प्रोसेस करता है, और एक फ़्लुएंट API प्रदान करता है जो आपको एक ही ऑपरेशन में कई मेटाडेटा स्कीम को अपडेट करने देता है। लाइब्रेरी पूरी तरह से थ्रेड‑सेफ़ है, जिससे यह हाई‑थ्रूपुट सर्वर वातावरण के लिए आदर्श बनती है।

## आवश्यकताएँ
- **Java Development Kit (JDK) 8+** – सुनिश्चित करें कि `java -version` 1.8 या नया रिपोर्ट करता है।  
- **Maven** – निर्भरता प्रबंधन के लिए; यदि चाहें तो आप Gradle भी उपयोग कर सकते हैं।  
- **Basic Java knowledge** – IntelliJ IDEA या Eclipse जैसे IDEs की परिचितता।  

## GroupDocs.Metadata for Java सेट अप करना
अपने Maven प्रोजेक्ट में लाइब्रेरी जोड़ने के लिए निम्नलिखित डिपेंडेंसी को अपने `pom.xml` फ़ाइल में डालें:

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

आप आधिकारिक रिलीज़ पेज से नवीनतम JAR भी डाउनलोड कर सकते हैं: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### लाइसेंस प्राप्ति
सभी फीचर्स का अन्वेषण करने के लिए एक मुफ्त ट्रायल लाइसेंस से शुरू करें। प्रोडक्शन डिप्लॉयमेंट के लिए, पूर्ण लाइसेंस खरीदें या [purchase page](https://purchase.groupdocs.com/temporary-license) के माध्यम से एक अस्थायी लाइसेंस अनुरोध करें। एक वैध लाइसेंस सभी ट्रायल प्रतिबंधों को हटाता है और प्रीमियम सपोर्ट अनलॉक करता है।

### बेसिक इनिशियलाइज़ेशन
`Metadata` क्लास इमेज फ़ाइलों पर सभी पढ़ने/लिखने ऑपरेशन्स के लिए एंट्री पॉइंट है। डिपेंडेंसी जोड़ने के बाद, आप लाइब्रेरी को इस प्रकार इनिशियलाइज़ कर सकते हैं:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataUpdater {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/GifWithXmp")) {
            // Your code to update metadata will go here
        }
    }
}
```

## विशिष्ट मेटाडेटा स्कीम अपडेट करना

### GroupDocs.Metadata for Java का उपयोग करके Dublin Core मेटाडेटा स्कीम को कैसे अपडेट करें?
`Metadata` इमेज मेटाडेटा तक पहुंचने का मुख्य एंट्री पॉइंट है। `DublinCorePackage` Dublin Core मेटाडेटा सेट को दर्शाता है और मानक वर्णनात्मक फ़ील्ड सेट करने की अनुमति देता है। यह आपको `format`, `rights`, और `subject` जैसे सार्वभौमिक फ़ील्ड सेट करने देता है। एक `Metadata` ऑब्जेक्ट बनाएं, `DublinCorePackage` प्राप्त करें, मान सेट करें, और फ़ाइल को सेव करें, जिससे मानकों‑अनुपालन वर्णनात्मक जानकारी सुनिश्चित हो।

1. **Metadata ऑब्जेक्ट को इनिशियलाइज़ करें:**  
   `Metadata` क्लास मेमोरी में एक सिंगल इमेज फ़ाइल का प्रतिनिधित्व करता है और सभी समर्थित मेटाडेटा पैकेजेज़ तक पहुंच प्रदान करता है.

   ```java
   try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/GifWithXmp")) {
       IXmp root = (IXmp) metadata.getRootPackage();
       if (root.getXmpPackage() != null) {
           // Further steps will be added here
       }
   }
   ```

2. **Dublin Core पैकेज बनाएं या प्राप्त करें:**  
   मौजूदा पैकेज प्राप्त करने के लिए `metadata.getDublinCorePackage()` का उपयोग करें या यदि यह मौजूद नहीं है तो नया इंस्टैंसिएट करें.

   ```java
   if (root.getXmpPackage().getSchemes().getDublinCore() == null) {
       root.getXmpPackage().getSchemes().setDublinCore(new XmpDublinCorePackage());
   }
   ```

3. **प्रॉपर्टीज़ अपडेट करें:**  
   `format`, `rights`, और `subject` जैसी प्रॉपर्टीज़ को सीधे पैकेज ऑब्जेक्ट पर सेट करें.

   ```java
   root.getXmpPackage().getSchemes().getDublinCore()
       .setFormat("image/gif")
       .setRights("Copyright (C) 2011-2021 GroupDocs. All Rights Reserved")
       .setSubject("test");
   ```

4. **परिवर्तनों को सेव करें:**  
   अपडेटेड मेटाडेटा को स्थायी करने के लिए `metadata.save(outputPath)` को कॉल करें.

   ```java
   metadata.save("YOUR_OUTPUT_DIRECTORY/OutputGif");
   ```

### GroupDocs.Metadata for Java के साथ Camera Raw मेटाडेटा को कैसे संशोधित करें?
`Metadata` इमेज मेटाडेटा पढ़ने और लिखने के लिए मुख्य क्लास है। `CameraRawPackage` एक्सपोज़र और शैडोज़ जैसी Camera Raw विशिष्ट मेटाडेटा तक पहुंच प्रदान करता है। Camera Raw मेटाडेटा शैडोज़, ऑटो‑ब्राइटनेस, और एक्सपोज़र जैसे तकनीकी शूटिंग पैरामीटर संग्रहीत करता है। इन फ़ील्ड्स को अपडेट करने से Lightroom जैसे टूल्स इमेज को सही ढंग से व्याख्या करते हैं, बैच प्रोसेसिंग में सुधार होता है और बड़े फोटो कलेक्शन में स्थिरता बनी रहती है।

1. **Metadata ऑब्जेक्ट को इनिशियलाइज़ करें:**  
   Dublin Core के लिए बनाया गया वही `Metadata` इंस्टेंस पुनः उपयोग करें.

2. **Camera Raw पैकेज बनाएं या प्राप्त करें:**  
   परिवर्तन करने से पहले मौजूदा `CameraRawPackage` की जाँच करें.

   ```java
   if (root.getXmpPackage().getSchemes().getCameraRaw() == null) {
       root.getXmpPackage().getSchemes().setCameraRaw(new XmpCameraRawPackage());
   }
   ```

3. **प्रॉपर्टीज़ अपडेट करें:**  
   इच्छित इमेज विशेषताओं को प्रतिबिंबित करने के लिए `shadows`, `autoBrightness`, और `exposure` जैसे सेटिंग्स को समायोजित करें.

   ```java
   root.getXmpPackage().getSchemes().getCameraRaw()
       .setShadows(50)
       .setAutoBrightness(true)
       .setAutoExposure(true)
       .setCameraProfile("test")
       .setExposure(0.0001);
   ```

4. **परिवर्तनों को सेव करें:**  
   अपने चुने हुए आउटपुट डायरेक्टरी में संशोधनों को स्थायी करें.

### GroupDocs.Metadata for Java का उपयोग करके XMP Basic मेटाडेटा को कैसे अपडेट करें?
`Metadata` इमेज मेटाडेटा को मैनिपुलेट करने के लिए कोर क्लास है। `XmpBasicPackage` कोर मेटाडेटा फ़ील्ड्स के लिए XMP Basic स्कीमा को दर्शाता है। XMP Basic में निर्माण तिथि, बेस URL, और रेटिंग जैसी कोर फ़ील्ड्स शामिल हैं। इन एट्रिब्यूट्स को अपडेट करने से कैटलॉगिंग में सुधार, सर्च प्रासंगिकता बढ़ती है, और कंटेंट मैनेजमेंट सिस्टम्स के साथ बेहतर इंटीग्रेशन सक्षम होता है, जिससे डिजिटल एसेट टूल्स उपयोगकर्ता‑परिभाषित मानदंडों के अनुसार इमेज को व्यवस्थित और प्रदर्शित कर सकें।

1. **Metadata ऑब्जेक्ट को इनिशियलाइज़ करें:**  
   ट्यूटोरियल के दौरान वही `Metadata` इंस्टेंस उपयोग करें.

2. **मौजूदा XMP Basic पैकेज को बदलें:**  
   यदि XMP Basic पैकेज अनुपलब्ध है, तो नया इंस्टैंसिएट करें और उसे `Metadata` ऑब्जेक्ट से संलग्न करें.

   ```java
   root.getXmpPackage().getSchemes().setXmpBasic(new XmpBasicPackage());
   ```

3. **प्रॉपर्टीज़ अपडेट करें:**  
   आवश्यकतानुसार `creationDate`, `baseURL`, और `rating` सेट करें.

   ```java
   root.getXmpPackage().getSchemes().getXmpBasic()
       .setCreateDate(new Date())
       .setBaseUrl("https://groupdocs.com")
       .setRating(5);
   ```

4. **परिवर्तनों को सेव करें:**  
   अपडेटेड मेटाडेटा को डिस्क पर लिखें.

### जावा में Basic Job Ticket मेटाडेटा स्कीम के साथ कैसे काम करें?
`Metadata` इमेज मेटाडेटा को संभालने के लिए मुख्य क्लास है। `BasicJobTicketPackage` जॉब टिकट मेटाडेटा को संभालता है, जिससे वर्कफ़्लो जानकारी को इमेज में एम्बेड किया जा सकता है। Basic Job Ticket स्कीमा जॉब आईडी, नाम, और URLs को सीधे इमेज फ़ाइल में एम्बेड करता है, जिससे डाउनस्ट्रीम सिस्टम प्रोसेसिंग चरणों को ट्रैक कर सकते हैं और इमेज को विशिष्ट टास्क से जोड़ सकते हैं। जॉब टिकट शामिल करने से ऑडिटेबिलिटी और ऑटोमेटेड पाइपलाइन में ऑपरेशनल एफिशिएंसी बढ़ती है।

1. **Metadata ऑब्जेक्ट को इनिशियलाइज़ करें:**  
   वही `Metadata` इंस्टेंस उपयोग जारी रखें.

2. **Basic Job Ticket पैकेज सेट करें:**  
   मौजूदा पैकेज प्राप्त करें या यदि अनुपलब्ध है तो नया बनाएं.

   ```java
   root.getXmpPackage().getSchemes().setBasicJobTicket(new XmpBasicJobTicketPackage());
   ```

3. **जॉब्स कॉन्फ़िगर करें:**  
   `id`, `name`, और `url` जैसी जॉब प्रॉपर्टीज़ परिभाषित करें ताकि डाउनस्ट्रीम प्रोसेसिंग सिस्टम इमेज के लाइफ़साइकल को ट्रैक कर सकें.

   ```java
   XmpJob job = new XmpJob();
   job.setID("1");
   job.setName("test job");
   job.setUrl("https://groupdocs.com");

   root.getXmpPackage().getSchemes().getBasicJobTicket()
       .setJobs(new XmpJob[]{job});
   ```

4. **परिवर्तनों को सेव करें:**  
   सभी जॉब‑टिकट जानकारी को आउटपुट फ़ोल्डर में स्थायी करें.

## व्यावहारिक अनुप्रयोग
- **फ़ोटोग्राफी स्टूडियो:** प्रत्येक एक्सपोर्टेड JPEG में कॉपीराइट और लाइसेंसिंग जानकारी को स्वचालित रूप से इन्जेक्ट करें, जिससे कानूनी अनुपालन सुनिश्चित हो।  
- **कंटेंट मैनेजमेंट सिस्टम (CMS):** अपलोडेड एसेट्स को Dublin Core और XMP डेटा से समृद्ध करें ताकि सर्च इंजन इमेज को अधिक प्रभावी ढंग से इंडेक्स कर सकें।  
- **डिजिटल एसेट मैनेजमेंट (DAM):** प्रोसेसिंग स्टेटस को एम्बेड करने के लिए Basic Job Ticket स्कीमा का उपयोग करें, जिससे जटिल पाइपलाइन में इमेज को ट्रेस करना आसान हो जाता है।

## सामान्य समस्याएँ और समाधान
- **Missing Package Errors:** प्रॉपर्टीज़ सेट करने से पहले हमेशा `get...Package()` मेथड कॉल करें; यदि यह `null` लौटाता है, तो पहले पैकेज को इंस्टैंसिएट करें।  
- **File Permission Problems:** अपने जावा प्रोसेस को पर्याप्त OS परमिशन के साथ चलाएँ, विशेषकर प्रोटेक्टेड डायरेक्टरीज़ में लिखते समय।  
- **Unsupported Formats:** GroupDocs.Metadata 50 से अधिक इमेज फ़ॉर्मेट्स को सपोर्ट करता है; यदि आप अज्ञात एक्सटेंशन का सामना करते हैं तो आधिकारिक डॉक्यूमेंटेशन देखें।

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं एक ही ऑपरेशन में कई मेटाडेटा स्कीम को अपडेट कर सकता हूँ?**  
A: हाँ। एक `Metadata` इंस्टेंस बनाने के बाद, आप `save()` को एक बार कॉल करने से पहले किसी भी पैकेज के संयोजन को प्राप्त और संशोधित कर सकते हैं।

**Q: क्या लाइब्रेरी क्लाउड स्टोरेज (जैसे AWS S3) में संग्रहीत इमेज के साथ काम करती है?**  
A: बिल्कुल। S3 से `InputStream` में इमेज लोड करें, स्ट्रीम को `Metadata` कन्स्ट्रक्टर में पास करें, और परिणाम को वापस क्लाउड में सेव करें।

**Q: क्या प्रोडक्शन उपयोग के लिए कमर्शियल लाइसेंस आवश्यक है?**  
A: प्रोडक्शन डिप्लॉयमेंट के लिए एक वैध कमर्शियल लाइसेंस आवश्यक है; ट्रायल लाइसेंस केवल मूल्यांकन और गैर‑कमर्शियल परीक्षण के लिए सीमित है।

**Q: कौन से जावा संस्करण आधिकारिक रूप से सपोर्टेड हैं?**  
A: GroupDocs.Metadata for Java JDK 8, 11, और 17 को सपोर्ट करता है, जिससे लेगेसी और आधुनिक दोनों एप्लिकेशन के साथ संगतता सुनिश्चित होती है।

**Q: लाइब्रेरी बड़े इमेज फ़ाइलों (जैसे >100 MB) को कैसे हैंडल करती है?**  
A: API डेटा को स्ट्रीम करता है और पूरी फ़ाइल को मेमोरी में लोड नहीं करता, जिससे आप अत्यधिक बड़े इमेज को अत्यधिक हीप उपयोग के बिना प्रोसेस कर सकते हैं।

## निष्कर्ष
इस गाइड में बताए गए चरणों का पालन करके, आपके पास अब GroupDocs.Metadata का उपयोग करके **updating image metadata java** के लिए एक पूर्ण, प्रोडक्शन‑रेडी वर्कफ़्लो है। आप Dublin Core, Camera Raw, XMP Basic, और Job Ticket जानकारी के साथ इमेज को आत्मविश्वास से समृद्ध कर सकते हैं, जिससे आपके डिजिटल एसेट अधिक खोज योग्य, अनुपालनयुक्त, और ऑटोमेटेड पाइपलाइन के लिए तैयार हो जाते हैं। लाइब्रेरी की अन्य सुविधाओं—जैसे मेटाडेटा एक्सट्रैक्शन और वैलिडेशन—का अन्वेषण करें ताकि आपकी एसेट‑मैनेजमेंट स्ट्रैटेजी और भी बेहतर हो सके।

---

**अंतिम अपडेट:** 2026-06-12  
**परीक्षित संस्करण:** GroupDocs.Metadata for Java 23.12  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [GroupDocs.Metadata Java का उपयोग करके Canon CR2 फ़ाइलों से मेटाडेटा निकालें: इमेज फ़ॉर्मेट्स के लिए एक व्यापक गाइड](/metadata/java/image-formats/extract-metadata-groupdocs-metadata-canon-cr2/)
- [डॉक्यूमेंट मैनेजमेंट के लिए जावा में GroupDocs.Metadata के साथ PDF मेटाडेटा को कुशलतापूर्वक अपडेट करें](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [GroupDocs.Metadata का उपयोग करके जावा में MP3 ID3v2 टैग्स को कैसे अपडेट करें - एक व्यापक गाइड](/metadata/java/audio-video-formats/update-mp3-id3v2-tags-groupdocs-metadata-java/)