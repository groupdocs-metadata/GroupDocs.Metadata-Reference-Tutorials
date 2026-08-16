---
date: '2026-08-15'
description: GroupDocs.Metadata का उपयोग करके Java में IPTC कीवर्ड कैसे जोड़ें, सीखें,
  जिससे डिजिटल एसेट मैनेजमेंट और सर्चेबिलिटी में सुधार हो।
keywords:
- add iptc keywords java
- groupdocs metadata java
- java add image metadata
lastmod: '2026-08-15'
og_description: GroupDocs.Metadata का उपयोग करके Java में IPTC कीवर्ड जोड़ें और डिजिटल
  एसेट मैनेजमेंट को बढ़ाएँ। चरण‑दर‑चरण सेटअप, कोड, और सर्वोत्तम प्रथाएँ सीखें।
og_image_alt: Guide showing Java code that adds IPTC keywords with GroupDocs.Metadata
og_title: Java में GroupDocs.Metadata के साथ IPTC कीवर्ड जोड़ें
schemas:
- author: GroupDocs
  dateModified: '2026-08-15'
  description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  headline: Add IPTC keywords in Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  name: Add IPTC keywords in Java with GroupDocs.Metadata
  steps:
  - name: create a constants class
    text: The `Constants` class stores reusable values such as file locations and
      the license string.
  - name: initialize metadata and set the IPTC package
    text: '`Metadata` is the entry point for reading and writing any supported metadata
      format. It abstracts file handling so you don’t need to manage streams manually.
      The code below checks whether an IPTC package already exists; if not, it creates
      one, guaranteeing a place for keyword storage.'
  - name: add keywords to the IPTC record
    text: IptcDataSet represents a single IPTC metadata entry such as a keyword. Each
      keyword is added as an `IptcDataSet` entry. You can add as many keywords as
      required; the library automatically handles duplicate detection.
  - name: retrieve and display IPTC keywords
    text: '`metadata.getIptc().getKeywords()` returns the list of keyword strings
      stored in the IPTC package. After saving, you can read back the keywords to
      confirm they were persisted correctly. This verification step is useful for
      unit tests and debugging.'
  type: HowTo
- questions:
  - answer: No. IPTC is an image‑specific standard; for PDFs you would use XMP or
      PDF‑specific metadata fields.
    question: Can I add IPTC keywords to PDF files?
  - answer: Yes—it handles JPEG, TIFF, PNG, BMP, and WebP, preserving existing metadata
      while adding new IPTC entries.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: The IPTC specification allows up to 64 keywords per image; GroupDocs.Metadata
      enforces this limit automatically.
    question: How many keywords can I store?
  - answer: Absolutely. The library is compiled for Java 8+ and works seamlessly on
      Java 11, 17, and newer LTS releases.
    question: Is the library compatible with Java 11?
  - answer: Retrieve the keyword list, remove the unwanted entry, then call `metadata.getIptc().setKeywords(updatedList)`
      and save the file.
    question: What if I need to remove a keyword?
  type: FAQPage
tags:
- add iptc keywords
- groupdocs metadata
- java metadata handling
- digital asset management
- image metadata
title: Java में GroupDocs.Metadata के साथ IPTC कीवर्ड जोड़ें
type: docs
url: /hi/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/
weight: 1
---

# Java में GroupDocs.Metadata के साथ IPTC कीवर्ड जोड़ें

इमेज मेटाडाटा को प्रबंधित करना किसी भी डिजिटल एसेट मैनेजमेंट (DAM) रणनीति के लिए आवश्यक है। इस ट्यूटोरियल में आप GroupDocs.Metadata लाइब्रेरी का उपयोग करके **Java में IPTC कीवर्ड कैसे जोड़ें** सीखेंगे, फिर उन कीवर्ड को पुनः प्राप्त करके बदलावों की पुष्टि करेंगे। अंत तक, आपके पास एक पुन: उपयोग योग्य पैटर्न होगा जिसे आप बैच‑प्रोसेसिंग जॉब्स, कंटेंट‑मैनेजमेंट पाइपलाइन्स, या किसी भी Java‑आधारित मीडिया वर्कफ़्लो में एम्बेड कर सकते हैं।

## त्वरित उत्तर
- **Java में IPTC कीवर्ड जोड़ने वाली लाइब्रेरी कौन सी है?** GroupDocs.Metadata for Java.  
- **क्या मुझे लाइसेंस की आवश्यकता है?** एक फ्री ट्रायल विकास के लिए काम करता है; उत्पादन के लिए एक पेड लाइसेंस आवश्यक है।  
- **क्या मैं एक साथ कई कीवर्ड जोड़ सकता हूँ?** हाँ—सिर्फ प्रत्येक कीवर्ड को IPTC पैकेज में जोड़ें।  
- **क्या बड़े फ़ाइल हैंडलिंग का समर्थन है?** GroupDocs.Metadata फ़ाइलों को 2 GB तक प्रोसेस करता है बिना पूरी फ़ाइल को मेमोरी में लोड किए।  
- **कौन सा Java संस्करण आवश्यक है?** JDK 8 या उससे ऊपर, Maven 3 या बाद का।

## Java में IPTC कीवर्ड जोड़ना क्या है?
**Java में IPTC कीवर्ड जोड़ना** Java कोड का उपयोग करके इमेज फ़ाइलों में IPTC‑मानक कीवर्ड टैग को प्रोग्रामेटिक रूप से डालने को दर्शाता है। यह ऑपरेशन इमेज के मेटाडाटा को समृद्ध करता है, जिससे वह DAM सिस्टम में खोज योग्य बनता है और वेब एसेट्स के SEO में सुधार होता है। यह मीडिया एसेट टैगिंग के उद्योग मानकों के अनुपालन को भी बनाए रखने में मदद करता है।

## Java के लिए GroupDocs.Metadata का उपयोग क्यों करें?
GroupDocs.Metadata **150+ मेटाडाटा मानकों** (EXIF, IPTC, XMP सहित) का समर्थन करता है और **फ़ाइलों को 2 GB तक** बिना पूरी तरह मेमोरी में लोड किए प्रोसेस कर सकता है, जिससे CPU और RAM उपयोग में लगभग 30 % तक कमी आती है, साधारण फ़ाइल‑स्ट्रीम तरीकों की तुलना में। API टाइप‑सेफ़, अच्छी तरह दस्तावेज़ित है, और परिवर्तन को स्थायी करने के लिए एक‑लाइन कॉल प्रदान करता है।

## पूर्वापेक्षाएँ

- **GroupDocs.Metadata for Java** (संस्करण 24.12 या बाद)।  
- Java Development Kit 8 या नया।  
- Maven 3 इंस्टॉल और कॉन्फ़िगर किया हुआ।  
- IntelliJ IDEA या Eclipse जैसे IDE (वैकल्पिक लेकिन अनुशंसित)।  

### आवश्यक लाइब्रेरी
Add the GroupDocs.Metadata dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

आप लाइब्रेरी को **GroupDocs.Metadata for Java releases** पेज से डाउनलोड कर सकते हैं: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

## Java में IPTC कीवर्ड कैसे जोड़ें?

सबसे पहले, GroupDocs.Metadata API का उपयोग करके लक्ष्य इमेज फ़ाइल लोड करें, फिर जांचें कि IPTC पैकेज मौजूद है या यदि नहीं है तो एक बनाएं, और अंत में इच्छित कीवर्ड को IPTC Keywords संग्रह में जोड़ें। नीचे दिए गए चरण इस वर्कफ़्लो के प्रत्येक भाग को विस्तार से दर्शाते हैं।

### चरण 1: एक कॉन्स्टैंट्स क्लास बनाएं
`Constants` क्लास फ़ाइल स्थान और लाइसेंस स्ट्रिंग जैसे पुन: उपयोग योग्य मान संग्रहीत करता है।

```java
public class Constants {
    public static final String YOUR_DOCUMENT_DIRECTORY = "path/to/your/document";
    public static final String OUTPUT_DIRECTORY = "path/to/output/directory";
}
```

### चरण 2: मेटाडाटा इनिशियलाइज़ करें और IPTC पैकेज सेट करें
`Metadata` किसी भी समर्थित मेटाडाटा फ़ॉर्मेट को पढ़ने और लिखने के लिए प्रवेश बिंदु है। यह फ़ाइल हैंडलिंग को एब्स्ट्रैक्ट करता है ताकि आपको स्ट्रीम्स को मैन्युअली मैनेज करने की जरूरत न पड़े।

नीचे दिया गया कोड जांचता है कि क्या IPTC पैकेज पहले से मौजूद है; यदि नहीं, तो यह एक बनाता है, जिससे कीवर्ड संग्रहण के लिए स्थान सुनिश्चित हो जाता है।

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcRecordSet;

public class InitializeMetadataAndIPTCPackage {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            if (root.getIptcPackage() == null) {
                root.setIptcPackage(new IptcRecordSet());
            }
        } catch (Exception e) {
            System.out.println("Error initializing metadata: " + e.getMessage());
        }
    }
}
```

### चरण 3: IPTC रिकॉर्ड में कीवर्ड जोड़ें
IptcDataSet एकल IPTC मेटाडाटा एंट्री जैसे कि कीवर्ड को दर्शाता है। प्रत्येक कीवर्ड को `IptcDataSet` एंट्री के रूप में जोड़ा जाता है। आप जितने भी कीवर्ड आवश्यक हों जोड़ सकते हैं; लाइब्रेरी स्वचालित रूप से डुप्लिकेट डिटेक्शन संभालती है।

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcDataSet;
import com.groupdocs.metadata.core.IptcRecordType;
import com.groupdocs.metadata.core.IptcApplicationRecordDataSet;

public class AddKeywordsToIPTC {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            IptcDataSet dataSet1 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 1");
            IptcDataSet dataSet2 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 2");
            IptcDataSet dataSet3 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 3");

            root.getIptcPackage().add(dataSet1);
            root.getIptcPackage().add(dataSet2);
            root.getIptcPackage().add(dataSet3);

            metadata.save(Constants.OUTPUT_DIRECTORY);
        } catch (Exception e) {
            System.out.println("Error adding keywords: " + e.getMessage());
        }
    }
}
```

### चरण 4: IPTC कीवर्ड पुनः प्राप्त करें और प्रदर्शित करें
`metadata.getIptc().getKeywords()` IPTC पैकेज में संग्रहीत कीवर्ड स्ट्रिंग्स की सूची लौटाता है। सहेजने के बाद, आप कीवर्ड को पुनः पढ़ सकते हैं यह पुष्टि करने के लिए कि वे सही ढंग से स्थायी हुए हैं। यह सत्यापन चरण यूनिट टेस्ट और डिबगिंग के लिए उपयोगी है।

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.MetadataProperty;

public class RetrieveAndDisplayKeywords {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.OUTPUT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            MetadataProperty keywordsProperty = root.getIptcPackage().getApplicationRecord()
                                                    .get_Item((byte)IptcApplicationRecordDataSet.Keywords.getRawValue());

            for (Object value : keywordsProperty.getValue()) {
                System.out.println(value);
            }
        } catch (Exception e) {
            System.out.println("Error retrieving keywords: " + e.getMessage());
        }
    }
}
```

## Java में IPTC कीवर्ड कैसे पुनः प्राप्त करें?

`metadata.getIptc().getKeywords()` IPTC पैकेज में संग्रहीत कीवर्ड स्ट्रिंग्स की सूची लौटाता है। आप फिर सूची पर इटरेट कर सकते हैं, प्रत्येक एंट्री को लॉग कर सकते हैं, या तेज़ पुनः प्राप्ति के लिए उन्हें सर्च इंडेक्स में फीड कर सकते हैं। यह मेथड `List<String>` लौटाता है जिसमें IPTC पैकेज में संग्रहीत सभी कीवर्ड होते हैं, जिससे आप उन्हें तुरंत प्रदर्शित या प्रोसेस कर सकते हैं।

## सामान्य समस्याएँ और ट्रबलशूटिंग
- **IPTC पैकेज गायब:** यदि इमेज में IPTC ब्लॉक नहीं है, तो `metadata.getIptc()` `null` लौटाता है। कीवर्ड जोड़ने से पहले हमेशा `metadata.addIptc()` कॉल करें।  
- **लाइसेंस त्रुटियाँ:** सुनिश्चित करें कि ट्रायल या कमर्शियल लाइसेंस फ़ाइल `Constants.LICENSE_PATH` में सही ढंग से संदर्भित है। लाइसेंस न होने पर `LicenseException` फेंका जाता है।  
- **बड़ी फ़ाइलें:** 2 GB से बड़ी इमेज के लिए, प्रोसेसिंग को चंक्स में विभाजित करें या GroupDocs.Metadata द्वारा प्रदान किए गए स्ट्रीमिंग API का उपयोग करें ताकि `OutOfMemoryError` से बचा जा सके।  

## अक्सर पूछे जाने वाले प्रश्न

**प्र: क्या मैं PDF फ़ाइलों में IPTC कीवर्ड जोड़ सकता हूँ?**  
उ: नहीं। IPTC एक इमेज‑विशिष्ट मानक है; PDF के लिए आप XMP या PDF‑विशिष्ट मेटाडाटा फ़ील्ड्स का उपयोग करेंगे।

**प्र: क्या GroupDocs.Metadata अन्य इमेज फ़ॉर्मेट्स का समर्थन करता है?**  
उ: हाँ—यह JPEG, TIFF, PNG, BMP, और WebP को संभालता है, मौजूदा मेटाडाटा को संरक्षित रखते हुए नए IPTC एंट्रीज़ जोड़ता है।

**प्र: मैं कितने कीवर्ड स्टोर कर सकता हूँ?**  
उ: IPTC स्पेसिफिकेशन प्रति इमेज अधिकतम 64 कीवर्ड की अनुमति देता है; GroupDocs.Metadata इस सीमा को स्वचालित रूप से लागू करता है।

**प्र: क्या लाइब्रेरी Java 11 के साथ संगत है?**  
उ: बिल्कुल। लाइब्रेरी Java 8+ के लिए कंपाइल की गई है और Java 11, 17, और नए LTS रिलीज़ पर सहजता से काम करती है।

**प्र: यदि मुझे कोई कीवर्ड हटाना हो तो क्या करें?**  
उ: कीवर्ड सूची प्राप्त करें, अनचाहे एंट्री को हटाएँ, फिर `metadata.getIptc().setKeywords(updatedList)` कॉल करें और फ़ाइल सहेजें।

## निष्कर्ष

अब आपके पास GroupDocs.Metadata के साथ **Java में IPTC कीवर्ड जोड़ने** के लिए एक पूर्ण, प्रोडक्शन‑रेडी पैटर्न है। मेटाडाटा ऑब्जेक्ट को इनिशियलाइज़ करके, यह सुनिश्चित करके कि IPTC पैकेज मौजूद है, कीवर्ड जोड़कर, और परिणामों की पुष्टि करके, आप किसी भी Java‑आधारित DAM या कंटेंट‑मैनेजमेंट वर्कफ़्लो में मजबूत टैगिंग को एकीकृत कर सकते हैं। अतिरिक्त मेटाडाटा प्रकार—EXIF, XMP, और कस्टम टैग्स—की खोज करें ताकि अपने एसेट्स को और समृद्ध बना सकें।

**अगले कदम**
- फ़ोल्डर में इमेज को बैच‑प्रोसेस करने के लिए सैंपल को विस्तारित करें।  
- कीवर्ड जोड़ने को स्वचालित इमेज एनालिसिस (जैसे, AI‑जनित टैग्स) के साथ संयोजित करें।  
- लोकेशन‑आधारित खोज को सक्षम करने के लिए EXIF GPS डेटा पढ़ने/लिखने के लिए GroupDocs.Metadata के API का अन्वेषण करें।

---

**अंतिम अपडेट:** 2026-08-15  
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

## संबंधित ट्यूटोरियल्स

- [BMP हेडर निकालें Java – GroupDocs.Metadata इमेज ट्यूटोरियल्स](/metadata/java/image-formats/)
- [java इमेज मेटाडाटा निकालें – Java में GroupDocs.Metadata का उपयोग करके Panasonic MakerNote मेटाडाटा निकालें](/metadata/java/image-formats/extract-panasonic-maker-note-groupdocs-metadata-java/)
- [तारीख के आधार पर Java मेटाडाटा अपडेट को स्वचालित करें GroupDocs.Metadata का उपयोग करके प्रभावी फ़ाइल प्रबंधन के लिए](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)