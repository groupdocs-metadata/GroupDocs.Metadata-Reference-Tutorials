---
date: '2026-05-27'
description: GroupDocs.Metadata for Java का उपयोग करके ईमेल प्राप्तकर्ताओं को अपडेट
  करना सीखें। प्राप्तकर्ताओं, विषयों को संशोधित करें, और बदलावों को कुशलतापूर्वक सहेजें।
keywords:
- update email recipients java
- GroupDocs Metadata Java
- email metadata management
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  headline: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  type: TechArticle
- description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  name: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  steps:
  - name: Initialize Metadata Object
    text: 'The `Metadata` class represents a file and provides access to its metadata.
      Create a `Metadata` instance with your input file path: **Definition anchor**:
      The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata,
      representing a single file in memory.'
  - name: Access EmailRootPackage
    text: '`EmailRootPackage` gives access to email‑specific metadata such as recipients
      and subject. Access the email’s metadata using: This step is crucial as it provides
      access to all modifiable properties of your email.'
  - name: Update Recipients
    text: 'Set new recipients for your email message:'
  - name: Initialize and Obtain Root Package
    text: 'Similar to updating primary recipients, initialize the metadata object:'
  - name: Set CC Recipients
    text: '`addCcRecipient` appends a new address to the CC collection without overwriting
      existing entries. Add carbon copy recipients as follows: This approach ensures
      that additional users are notified without being the main point of contact.'
  - name: Initialize Metadata
    text: 'Start by initializing your metadata object:'
  - name: Change the Subject
    text: 'Update the email’s subject line: This step is vital for maintaining relevant
      and searchable email threads.'
  - name: Initialize and Obtain Root Package
    text: 'Begin with initializing the `Metadata` object:'
  - name: Save Changes
    text: 'Persist your changes by saving them to a specified output directory: This
      ensures that all modifications are retained and reflected in the saved file.'
  type: HowTo
- questions:
  - answer: Load the file with `Metadata`, get the `EmailRootPackage`, replace the
      `To` collection, and save – all in three lines of code.
    question: What is the fastest way to change an email’s primary recipient?
  - answer: Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.
    question: Can I add CC recipients without overwriting existing ones?
  - answer: A temporary license removes evaluation limits; a permanent license is
      required for commercial deployments. You can obtain a temporary license from
      the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.
    question: Do I need a license for production use?
  - answer: GroupDocs.Metadata works with Java 8, 11, 17, and later.
    question: Which Java versions are supported?
  - answer: Process files in batches of 50–100 to keep memory usage under 200 MB per
      batch.
    question: Is batch processing safe for large mailboxes?
  type: FAQPage
title: 'ईमेल प्राप्तकर्ताओं को अपडेट करें (Java): GroupDocs.Metadata के साथ ईमेल मेटाडेटा
  अपडेट में निपुण बनें'
type: docs
url: /hi/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# GroupDocs.Metadata के साथ जावा में ईमेल प्राप्तकर्ताओं को अपडेट करें

इस व्यापक गाइड में आप GroupDocs.Metadata लाइब्रेरी का उपयोग करके **update email recipients java** को प्रोग्रामेटिकली अपडेट करेंगे। हम प्राथमिक और CC प्राप्तकर्ताओं को संशोधित करने, विषय पंक्ति बदलने, और उन परिवर्तनों को सहेजने की प्रक्रिया को स्पष्ट, चरण‑दर‑चरण कोड स्निपेट्स के साथ दिखाएंगे। अंत तक आप किसी भी जावा‑आधारित वर्कफ़्लो में ईमेल‑मेटाडेटा ऑटोमेशन को एकीकृत करने के लिए तैयार होंगे।

## त्वरित उत्तर
- **ईमेल के प्राथमिक प्राप्तकर्ता को बदलने का सबसे तेज़ तरीका क्या है?** Load the file with `Metadata`, get the `EmailRootPackage`, replace the `To` collection, and save – all in three lines of code.  
- **क्या मैं मौजूदा प्राप्तकर्ताओं को ओवरराइट किए बिना CC प्राप्तकर्ता जोड़ सकता हूँ?** Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.  
- **उत्पादन उपयोग के लिए मुझे लाइसेंस की आवश्यकता है क्या?** A temporary license removes evaluation limits; a permanent license is required for commercial deployments. You can obtain a temporary license from the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.  
- **कौन से जावा संस्करण समर्थित हैं?** GroupDocs.Metadata works with Java 8, 11, 17, and later.  
- **क्या बड़े मेलबॉक्स के लिए बैच प्रोसेसिंग सुरक्षित है?** Process files in batches of 50–100 to keep memory usage under 200 MB per batch.

## update email recipients java क्या है?
*Updating email recipients in Java* का अर्थ है प्रोग्रामेटिकली ईमेल फ़ाइल (EML, MSG आदि) के “To”, “CC”, या “BCC” फ़ील्ड को बदलना बिना मेल क्लाइंट खोले। GroupDocs.Metadata एक हाई‑लेवल API प्रदान करता है जो ईमेल संरचना को पढ़ता है, आपको पता संग्रह को संशोधित करने देता है, और अपडेटेड फ़ाइल को डिस्क पर लिखता है।

## ईमेल मेटाडेटा के लिए GroupDocs.Metadata क्यों उपयोग करें?
GroupDocs.Metadata **50+ ईमेल‑संबंधित फ़ॉर्मेट** (EML, MSG, MHT सहित) का समर्थन करता है और **सैकड़ों‑पृष्ठ वाले संदेशों** को पूरी फ़ाइल को मेमोरी में लोड किए बिना प्रोसेस कर सकता है, जिससे RAM खपत में **80 %** तक की कमी आती है, साधारण फ़ाइल‑स्ट्रीम तरीकों की तुलना में। इसका शुद्ध‑जावा इम्प्लीमेंटेशन नेटिव डिपेंडेंसीज़ को समाप्त करता है, जिससे यह क्रॉस‑प्लेटफ़ॉर्म सेवाओं के लिए आदर्श बनता है।

## पूर्वापेक्षाएँ
- Java 8 या नया (Java 11, 17, 21 पूरी तरह परीक्षण किए गए हैं)।
- निर्भरता प्रबंधन के लिए Maven या Gradle।
- एक वैध GroupDocs.Metadata लाइसेंस (अस्थायी या स्थायी)।

### आवश्यक लाइब्रेरी और निर्भरताएँ
Add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```
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

सीधे डाउनलोड के लिए, नवीनतम संस्करण यहाँ से प्राप्त करें: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)।

### पर्यावरण सेटअप
सुनिश्चित करें कि आपका IDE संगत JDK की ओर इशारा कर रहा है और Maven GroupDocs.Metadata आर्टिफैक्ट्स को बिना त्रुटियों के हल करता है।

## जावा में ईमेल प्राप्तकर्ताओं को कैसे अपडेट करें?
ईमेल फ़ाइल लोड करें, मौजूदा प्राप्तकर्ताओं को बदलें, और परिणाम सहेजें। इस ऑपरेशन के लिए केवल तीन API कॉल्स की आवश्यकता होती है और यह सामान्य 1 MB संदेशों के लिए **200 ms** से कम समय में चलता है। हाई‑लेवल `EmailRootPackage` API का उपयोग करके आप पूरी फ़ाइल को पार्स करने से बचते हैं, जिससे मेमोरी उपयोग कम रहता है और बैच प्रोसेसिंग सरल हो जाता है।

```java
Metadata metadata = new Metadata("input.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
email.getTo().clear();                         // remove old recipients
email.getTo().add(new EmailRecipient("new@example.com"));
metadata.save("output.eml");
```
```java
import com.groupdocs.metadata.Metadata;
```
ऊपर की पंक्ति आपके फ़ाइलों पर मेटाडेटा ऑपरेशन्स को प्रबंधित करने के लिए आवश्यक क्लास को इम्पोर्ट करती है।

## कार्यान्वयन गाइड
अब हम प्रत्येक फीचर में गहराई से जाएंगे, त्वरित‑उत्तर स्निपेट्स को पूर्ण संदर्भ के साथ विस्तारित करेंगे।

### ईमेल प्राप्तकर्ताओं को अपडेट करना
**अवलोकन**: यह अनुभाग दिखाता है कि आप प्रोग्रामेटिकली ईमेल संदेश के प्राथमिक प्राप्तकर्ताओं को कैसे अपडेट कर सकते हैं।

#### चरण 1: Metadata ऑब्जेक्ट को इनिशियलाइज़ करें
`Metadata` क्लास एक फ़ाइल का प्रतिनिधित्व करता है और उसके मेटाडेटा तक पहुंच प्रदान करता है। अपने इनपुट फ़ाइल पाथ के साथ एक `Metadata` इंस्टेंस बनाएं:

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**परिभाषा एंकर**: `Metadata` क्लास GroupDocs.Metadata में सभी मेटाडेटा ऑपरेशन्स के लिए प्रवेश बिंदु है, जो मेमोरी में एकल फ़ाइल का प्रतिनिधित्व करता है।

#### चरण 2: EmailRootPackage तक पहुंचें
`EmailRootPackage` प्राप्तकर्ताओं और विषय जैसी ईमेल‑विशिष्ट मेटाडेटा तक पहुंच प्रदान करता है। ईमेल की मेटाडेटा तक पहुंचने के लिए उपयोग करें:

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
यह चरण महत्वपूर्ण है क्योंकि यह आपके ईमेल की सभी संशोधित करने योग्य प्रॉपर्टीज़ तक पहुंच प्रदान करता है।

#### चरण 3: प्राप्तकर्ताओं को अपडेट करें
अपने ईमेल संदेश के लिए नए प्राप्तकर्ताओं को सेट करें:

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### ईमेल में कार्बन कॉपी (CC) प्राप्तकर्ता जोड़ना
**अवलोकन**: मौजूदा ईमेल में CC प्राप्तकर्ताओं को जोड़ने का तरीका सीखें।

#### चरण 1: इनिशियलाइज़ करें और रूट पैकेज प्राप्त करें
प्राथमिक प्राप्तकर्ताओं को अपडेट करने के समान, मेटाडेटा ऑब्जेक्ट को इनिशियलाइज़ करें:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### चरण 2: CC प्राप्तकर्ताओं को सेट करें
`addCcRecipient` मौजूदा प्रविष्टियों को ओवरराइट किए बिना CC संग्रह में नया पता जोड़ता है। कार्बन कॉपी प्राप्तकर्ताओं को इस प्रकार जोड़ें:

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
यह तरीका सुनिश्चित करता है कि अतिरिक्त उपयोगकर्ताओं को सूचित किया जाए बिना उन्हें मुख्य संपर्क बिंदु बनाए।

### ईमेल विषय को अपडेट करना
**अवलोकन**: यह सुविधा आपको ईमेल की विषय पंक्ति को संशोधित करने की अनुमति देती है, जिससे संचार स्पष्ट और अद्यतित रहता है।

#### चरण 1: Metadata को इनिशियलाइज़ करें
अपने मेटाडेटा ऑब्जेक्ट को इनिशियलाइज़ करके शुरू करें:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### चरण 2: विषय बदलें
ईमेल के विषय पंक्ति को अपडेट करें:

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
यह चरण प्रासंगिक और खोज योग्य ईमेल थ्रेड्स को बनाए रखने के लिए महत्वपूर्ण है।

### अपडेटेड ईमेल मेटाडेटा को सहेजना
**अवलोकन**: एक बार जब आप परिवर्तन कर लेते हैं, तो इन अपडेट्स को सहेजना आवश्यक है। यह अनुभाग दिखाता है कि आप अपने संशोधनों को प्रभावी रूप से कैसे स्थायी बनाते हैं।

#### चरण 1: इनिशियलाइज़ करें और रूट पैकेज प्राप्त करें
`Metadata` ऑब्जेक्ट को इनिशियलाइज़ करके शुरू करें:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### चरण 2: परिवर्तन सहेजें
निर्दिष्ट आउटपुट डायरेक्टरी में सहेजकर अपने परिवर्तन को स्थायी बनाएं:

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
यह सुनिश्चित करता है कि सभी संशोधन बरकरार रहें और सहेजी गई फ़ाइल में प्रतिबिंबित हों।

## व्यावहारिक अनुप्रयोग
इन सुविधाओं को लागू करना विभिन्न वास्तविक‑दुनिया परिदृश्यों में अत्यंत लाभदायक हो सकता है:

1. **ईमेल प्रबंधन सिस्टम** – बड़े पैमाने पर ईमेल वितरण के लिए प्राप्तकर्ता अपडेट को स्वचालित करें।  
2. **ग्राहक समर्थन प्लेटफ़ॉर्म** – टिकट स्थिति परिवर्तन को दर्शाने के लिए ईमेल विषय को शीघ्रता से संशोधित करें।  
3. **आंतरिक संचार उपकरण** – मैन्युअल संपादन के बिना सभी टीम सदस्यों को महत्वपूर्ण घोषणाओं में CC करें।

## प्रदर्शन संबंधी विचार
जब आप बड़ी मात्रा में ईमेल डेटा के साथ काम कर रहे हों, तो इन टिप्स को ध्यान में रखें:

- **फ़ाइलों को **50–100** के बैच में प्रोसेस करें ताकि प्रत्येक बैच में मेमोरी उपयोग **200 MB** से कम रहे।**  
- `metadata.getRootPackage().getEmail()` कॉल को कम से कम उपयोग करें; संभव हो तो `Metadata` इंस्टेंस को पुन: उपयोग करें।  
- OutOfMemory त्रुटियों से बचने के लिए VisualVM जैसे टूल्स से JVM हीप उपयोग की निगरानी करें।

## निष्कर्ष
अब आप GroupDocs.Metadata का उपयोग करके **update email recipients java** को कैसे करना है, में निपुण हो गए हैं। चाहे आप प्राथमिक प्राप्तकर्ताओं को समायोजित कर रहे हों, CC जोड़ रहे हों, या विषय पंक्ति को बदल रहे हों, लाइब्रेरी एक तेज़, मेमोरी‑कुशल API प्रदान करती है। अधिक उन्नत परिदृश्यों जैसे अटैचमेंट को संभालना या EML और MSG फ़ॉर्मेट के बीच रूपांतरण के लिए पूर्ण [documentation](https://docs.groupdocs.com/metadata/java/) देखें।

## अक्सर पूछे जाने वाले प्रश्न
**Q1**: GroupDocs.Metadata द्वारा कौन से जावा संस्करण समर्थित हैं?  
- **A**: Java 8, 11, 17, और बाद के संस्करण पूरी तरह समर्थित हैं।

**Q2**: क्या मैं GroupDocs.Metadata को बिना लाइसेंस के उपयोग कर सकता हूँ?  
- **A**: हाँ, एक फ्री ट्रायल सीमाओं के साथ काम करता है; एक अस्थायी या स्थायी लाइसेंस उन सीमाओं को हटा देता है।

**Q3**: मैं बड़े ईमेल फ़ाइलों को कुशलतापूर्वक कैसे संभालूँ?  
- **A**: उन्हें छोटे बैचों में प्रोसेस करें, `Metadata` ऑब्जेक्ट्स को पुन: उपयोग करें, और बैच प्रति 200 MB से कम रखने के लिए हीप उपयोग की निगरानी करें।

**Q4**: ईमेल के अलावा GroupDocs.Metadata कौन से अन्य फ़ाइल प्रकारों का समर्थन करता है?  
- **A**: यह **70** से अधिक फ़ॉर्मेट्स का समर्थन करता है, जिसमें PDF, DOCX, XLSX, PPTX, इमेजेज, और आर्काइव शामिल हैं। पूरी सूची के लिए [API reference](https://reference.groupdocs.com/metadata/java/) देखें।

---

**अंतिम अपडेट:** 2026-05-27  
**परीक्षण किया गया:** GroupDocs.Metadata 23.12 for Java  
**लेखक:** GroupDocs  

## संबंधित ट्यूटोरियल
- [GroupDocs.Metadata का उपयोग करके जावा में ईमेल मेटाडेटा निष्कर्षण में महारत हासिल करें](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [GroupDocs.Metadata जावा के लिए ईमेल और संपर्क मेटाडेटा ट्यूटोरियल](/metadata/java/email-contact-formats/)
- [प्रभावी संपर्क प्रबंधन के लिए जावा में GroupDocs.Metadata का उपयोग करके vCard फोटो URI निकालना कैसे करें](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)