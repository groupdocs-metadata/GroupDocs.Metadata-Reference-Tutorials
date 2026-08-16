---
date: '2026-08-10'
description: GroupDocs.Metadata for Java का उपयोग करके PSD फ़ाइलों से EXIF मेटाडेटा
  निकालना सीखें। यह गाइड बेसिक एक्सट्रैक्शन, IFD पैकेजेज, GPS डेटा, और रियल‑वर्ल्ड
  यूज़ केस को कवर करता है।
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: GroupDocs.Metadata for Java का उपयोग करके PSD फ़ाइलों से EXIF मेटाडेटा
  निकालना सीखें। स्टेप‑बाय‑स्टेप गाइड, कोड स्निपेट्स, और डेवलपर्स के लिए ट्रबलशूटिंग
  टिप्स।
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: GroupDocs.Metadata के साथ PSD फ़ाइलों से EXIF मेटाडेटा निकालने का तरीका
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: GroupDocs.Metadata के साथ PSD फ़ाइलों से EXIF मेटाडेटा निकालने का तरीका
type: docs
url: /hi/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# GroupDocs.Metadata के साथ PSD फ़ाइलों से EXIF मेटाडेटा निकालना

PSD फ़ाइलों से **EXIF मेटाडेटा** निकालना एक नियमित लेकिन शक्तिशाली कदम है जब आपको इमेज की उत्पत्ति का ऑडिट करना हो, एसेट टैगिंग को स्वचालित करना हो, या खोज योग्य मीडिया लाइब्रेरी बनानी हो। इस ट्यूटोरियल में आप GroupDocs.Metadata for Java के साथ **EXIF को जल्दी से निकालना** सीखेंगे, सटीक API कॉल देखेंगे, और उन्नत IFD पैकेज और GPS कॉर्डिनेट्स को कैसे संभालना है, यह जानेंगे। अंत तक आप किसी भी Java‑आधारित वर्कफ़्लो में मेटाडेटा एक्सट्रैक्शन को एकीकृत करने के लिए तैयार हो जाएंगे।

## त्वरित उत्तर
`Metadata` क्लास एक फ़ाइल का प्रतिनिधित्व करती है और उसके मेटाडेटा तक पहुँच प्रदान करती है।

- **पहली कोड लाइन क्या है?** `Metadata metadata = new Metadata("sample.psd");`
- **कौन सा मेथड कलाकार का नाम लौटाता है?** `metadata.getExif().getArtist();`
- **क्या मैं GPS डेटा पढ़ सकता हूँ?** हाँ – उपयोग करें `metadata.getExif().getGpsInfo();`
- **क्या उत्पादन के लिए लाइसेंस चाहिए?** ट्रायल अवधि के बाद एक वैध GroupDocs.Metadata लाइसेंस आवश्यक है।
- **समर्थित Java संस्करण?** Java 8 या बाद का (Java 21 तक)।

## EXIF मेटाडेटा क्या है?
EXIF (Exchangeable Image File Format) मेटाडेटा कैमरा सेटिंग्स, निर्माण टाइमस्टैम्प, और स्थान डेटा को इमेज फ़ाइलों के अंदर संग्रहीत करता है। GroupDocs.Metadata इस जानकारी को सीधे PSD फ़ाइलों की बाइनरी संरचना से पढ़ता है, और इसे एक साफ़ Java API के माध्यम से उपलब्ध कराता है। यह डेवलपर्स को प्रोग्रामेटिक रूप से कैमरा मॉडल, एक्सपोज़र टाइम, और GPS कॉर्डिनेट्स जैसी विवरण प्राप्त करने की सुविधा देता है, बिना मैन्युअल निरीक्षण के।

## Java के लिए GroupDocs.Metadata क्यों उपयोग करें?
GroupDocs.Metadata **30+ फ़ाइल फ़ॉर्मेट** (जैसे PSD, JPEG, PNG, TIFF) का समर्थन करता है और **2 GB** तक की फ़ाइलों को पूरी दस्तावेज़ को मेमोरी में लोड किए बिना प्रोसेस कर सकता है। यह लाइब्रेरी **150 से अधिक अलग-अलग EXIF टैग** निकालती है, जिससे आपको विश्लेषण या अनुपालन के लिए आवश्यक कैमरा और GPS एट्रिब्यूट्स का पूरा सेट मिलता है।

## पूर्वापेक्षाएँ
- **Java Development Kit (JDK) 8** या उससे नया आपके मशीन पर स्थापित हो।  
- **Maven** निर्भरता प्रबंधन के लिए।  
- **GroupDocs.Metadata for Java संस्करण 24.12** (या नया)।  
- Java क्लासेस, ऑब्जेक्ट्स, और एक्सेप्शन हैंडलिंग की बुनियादी समझ।

### आवश्यक लाइब्रेरी और निर्भरताएँ
| निर्भरता | Maven निर्देशांक |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### पर्यावरण सेटअप
आपके पास IntelliJ IDEA या Eclipse जैसे Maven‑संगत IDE होना चाहिए। एक नया Maven प्रोजेक्ट बनाएं या मौजूदा प्रोजेक्ट में निर्भरता जोड़ें।

## Java के लिए GroupDocs.Metadata कैसे सेटअप करें
GroupDocs.Metadata को कुछ कॉन्फ़िगरेशन लाइनों के साथ Maven प्रोजेक्ट में जोड़ा जा सकता है। नीचे दिए गए चरण दिखाते हैं कि रिपॉज़िटरी और निर्भरता को कैसे शामिल किया जाए ताकि लाइब्रेरी क्लासपाथ पर उपलब्ध हो।

### Maven सेटअप
`pom.xml` के `<dependencies>` सेक्शन के अंदर निम्न स्निपेट जोड़ें:

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

### प्रत्यक्ष डाउनलोड
वैकल्पिक रूप से, आधिकारिक रिलीज़ पेज से नवीनतम JAR डाउनलोड करें: [GroupDocs.Metadata for Java रिलीज़](https://releases.groupdocs.com/metadata/java/)।

### लाइसेंस प्राप्ति
लाइब्रेरी को 30‑दिन के ट्रायल के बाद चलाने के लिए, एक अस्थायी या पूर्ण लाइसेंस प्राप्त करें:

1. लाइसेंस खरीद पेज पर जाएँ ([License Purchase Page](https://purchase.groupdocs.com/temporary-license)).  
2. टेस्टिंग के लिए **temporary** और प्रोडक्शन के लिए **full** चुनें।  
3. स्क्रीन पर दिखाए गए निर्देशों का पालन करके लाइसेंस फ़ाइल (`metadata.lic`) को अपने Java क्लासपाथ में एम्बेड करें।

### बुनियादी इनिशियलाइज़ेशन और सेटअप
लाइब्रेरी को क्लासपाथ पर जोड़ने के बाद, नीचे दिखाए अनुसार इसे इनिशियलाइज़ करें:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## PSD इमेज से बेसिक EXIF मेटाडेटा प्रॉपर्टीज़ कैसे निकालें
यह सेक्शन बताता है कि PSD फ़ाइल को कैसे लोड करें, EXIF कंटेनर तक कैसे पहुँचें, और **artist**, **copyright**, और **software** जैसे सबसे सामान्य टैग पढ़ें। प्रक्रिया में एक `Metadata` इंस्टेंस बनाना, `getExif()` कॉल करना, और फिर सरल गेटर मेथड्स से व्यक्तिगत प्रॉपर्टीज़ प्राप्त करना शामिल है।

### चरण‑दर‑चरण कार्यान्वयन
1. `Metadata` इंस्टेंस बनाएं जो आपके PSD फ़ाइल की ओर इशारा करता हो।  
2. EXIF कंटेनर प्राप्त करने के लिए `getExif()` कॉल करें।  
3. `getArtist()`, `getCopyright()`, और `getSoftware()` जैसे व्यक्तिगत प्रॉपर्टीज़ पढ़ें।  
4. अपने एप्लिकेशन लॉजिक के अनुसार मानों को प्रिंट या स्टोर करें।

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **Pro tip:** `Metadata` ऑब्जेक्ट फ़ाइल फ़ॉर्मेट को स्वचालित रूप से पहचानता है, इसलिए आप JPEG या TIFF फ़ाइलों के लिए वही कोड बिना बदलाव के पुनः उपयोग कर सकते हैं।

## PSD इमेज से EXIF IFD पैकेज प्रॉपर्टीज़ कैसे निकालें
IFD (Image File Directory) सेक्शन में **camera serial number**, **lens model**, और **user comments** जैसी गहरी तकनीकी जानकारी होती है। `Ifd0` प्राथमिक Image File Directory को दर्शाता है जिसमें बेसिक कैमरा जानकारी होती है। इन फ़ील्ड्स को निकालना फॉरेंसिक विश्लेषण या हाई‑प्रिसिशन कैटलॉगिंग के लिए उपयोगी है।

### कार्यान्वयन चरण
1. पिछले सेक्शन से `Metadata` इंस्टेंस को पुनः उपयोग करें।  
2. `metadata.getExif().getIfd0()` के माध्यम से IFD कंटेनर पर जाएँ।  
3. `getBodySerialNumber()` और `getUserComment()` जैसे प्रॉपर्टीज़ पढ़ें।  
4. डेटा आउटपुट करें या इसे अपने डोमेन मॉडल में मैप करें।

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## PSD फ़ाइल से GPS डेटा (अक्षांश, देशांतर) कैसे प्राप्त करें
बहुत से आधुनिक कैमरों में GPS कॉर्डिनेट्स EXIF ब्लॉक में एम्बेड होते हैं। `GpsInfo` EXIF डेटा से निकाले गए भौगोलिक कॉर्डिनेट्स रखता है। `metadata.getExif().getGpsInfo()` कॉल करें और फिर `getLatitude()`, `getLongitude()`, और `getAltitude()` का उपयोग करके सटीक स्थान डेटा प्राप्त करें—कोई अतिरिक्त पार्सिंग आवश्यक नहीं।

### विस्तृत चरण
1. `GpsInfo` ऑब्जेक्ट प्राप्त करें: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. अक्षांश और देशांतर पढ़ें: `gps.getLatitude()` दशमलव डिग्री में `double` लौटाता है।  
3. गुम डेटा को संभालें: यदि टैग मौजूद नहीं है तो API `null` लौटाता है, इसलिए `NullPointerException` से बचें।  

> **Common pitfall:** कुछ PSD फ़ाइलें GPS कॉर्डिनेट्स को रैशनल नंबर में संग्रहीत करती हैं; लाइब्रेरी उन्हें स्वचालित रूप से सामान्य करती है, लेकिन पुरानी फ़ाइलों को मैन्युअल रूपांतरण की आवश्यकता हो सकती है।

## सामान्य समस्याएँ और ट्रबलशूटिंग
| लक्षण | संभावित कारण | समाधान |
|---------|--------------|-----|
| `Unsupported format` exception | पुराने GroupDocs.Metadata संस्करण का उपयोग करना जो PSD को पहचानता नहीं है | संस्करण 24.12 या बाद में अपग्रेड करें |
| `NullPointerException` when calling `getArtist()` | स्रोत फ़ाइल में EXIF टैग मौजूद नहीं है | पढ़ने से पहले `metadata.getExif().hasArtist()` जांचें |
| License error after 30 days | क्लासपाथ पर लाइसेंस फ़ाइल नहीं मिली | `metadata.lic` को `src/main/resources` में रखें या `Metadata.setLicense("path/to/license")` सेट करें |

## अक्सर पूछे जाने वाले प्रश्न

**Q: क्या मैं पासवर्ड‑सुरक्षित PSD फ़ाइल से EXIF मेटाडेटा निकाल सकता हूँ?**  
A: हाँ। फ़ाइल को `new Metadata("file.psd", "password")` से लोड करें और फिर सामान्य रूप से EXIF डेटा तक पहुँचें।

**Q: क्या GroupDocs.Metadata कई PSD फ़ाइलों की बैच प्रोसेसिंग का समर्थन करता है?**  
A: बिल्कुल। लूप के भीतर `Metadata` ऑब्जेक्ट बनाएं, या डायरेक्टरीज़ को कुशलतापूर्वक प्रोसेस करने के लिए `MetadataCollection` हेल्पर का उपयोग करें।

**Q: आधिकारिक रूप से कौन से Java संस्करण समर्थित हैं?**  
A: Java 8 से लेकर Java 21 तक पूरी तरह परीक्षण किए गए हैं। लाइब्रेरी केवल मानक API का उपयोग करती है, इसलिए यह किसी भी कम्प्लायंट JVM पर काम करती है।

**Q: क्या EXIF डेटा को PSD फ़ाइल में वापस लिखना संभव है?**  
A: हाँ। `Exif` ऑब्जेक्ट के माध्यम से प्रॉपर्टीज़ संशोधित करने के बाद, `metadata.save("output.psd")` कॉल करके बदलाव सहेजें।

**Q: लाइब्रेरी कितनी बड़ी PSD फ़ाइल को बिना मेमोरी खत्म हुए संभाल सकती है?**  
A: GroupDocs.Metadata डेटा को स्ट्रीम करता है और सामान्य 8 GB RAM मशीन पर **2 GB** तक की फ़ाइलें प्रोसेस कर सकता है, इसकी लो‑मेमोरी आर्किटेक्चर के कारण।

## निष्कर्ष
अब आप GroupDocs.Metadata for Java का उपयोग करके PSD फ़ाइलों से **EXIF मेटाडेटा निकालना** जानते हैं, बेसिक टैग से लेकर उन्नत IFD और GPS जानकारी तक। इन स्निपेट्स को अपने इमेज‑प्रोसेसिंग पाइपलाइन में एकीकृत करें ताकि कैटलॉगिंग, अनुपालन जांच, या लोकेशन‑आधारित सेवाओं को स्वचालित किया जा सके। अधिक गहन अन्वेषण के लिए, अन्य समर्थित फ़ॉर्मेट (JPEG, TIFF, PNG) से मेटाडेटा निकालने की कोशिश करें या कस्टम टैग एम्बेड करने के लिए राइट‑बैक क्षमताओं के साथ प्रयोग करें।

---

**अंतिम अपडेट:** 2026-08-10  
**परीक्षित संस्करण:** GroupDocs.Metadata 24.12 for Java  
**लेखक:** GroupDocs

## संबंधित ट्यूटोरियल

- [Java में GroupDocs.Metadata का उपयोग करके PSD फ़ाइलों से इमेज रिसोर्सेज निकालें: एक व्यापक गाइड](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Java के लिए GroupDocs.Metadata का उपयोग करके PSD हेडर और लेयर जानकारी निकालें: एक व्यापक गाइड](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Java में GroupDocs.Metadata का उपयोग करके MakerNote प्रॉपर्टीज़ को TIFF/EXIF टैग्स के रूप में निकालें](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)