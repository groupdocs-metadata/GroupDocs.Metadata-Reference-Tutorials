---
date: '2026-06-27'
description: Java ile dosya oluşturma zaman damgasını nasıl alacağınızı ve PowerPoint
  sunumlarından diğer belge özelliklerini GroupDocs.Metadata for Java ile nasıl çıkaracağınızı
  öğrenin. Belge yönetimi ve uyumluluk için idealdir.
keywords:
- java get file creation timestamp
- java extract document properties
- GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-27'
  description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  headline: How to java get file creation timestamp from Presentation Files Using
    GroupDocs.Metadata
  type: TechArticle
- description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  name: How to java get file creation timestamp from Presentation Files Using GroupDocs.Metadata
  steps:
  - name: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
    text: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
  - name: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
    text: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
  - name: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
    text: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
  - name: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
    text: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
  type: HowTo
- questions:
  - answer: 'The API returns `null` for unset fields. Use a conditional expression
      like `(author != null ? author : "N/A")` to provide a fallback value.'
    question: How do I handle missing metadata properties?
  - answer: Yes, beyond the built‑in properties you can read and write custom key/value
      pairs using the same API.
    question: Can GroupDocs.Metadata extract custom metadata fields?
  - answer: GroupDocs.Metadata works with PowerPoint (`.ppt`, `.pptx`) and also supports
      PDF, Word, Excel, and many image formats.
    question: Is there support for other presentation formats?
  - answer: A compatible JDK (8 or higher) and sufficient heap memory for the size
      of the documents you process (e.g., 1 GB heap for 500‑page presentations).
    question: What are the system requirements for GroupDocs.Metadata Java?
  - answer: 'Visit the official support forum for assistance: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)'
    question: Where can I get help if I run into problems?
  type: FAQPage
title: Java ile Sunum Dosyalarından Dosya Oluşturma Zaman Damgasını Alma - GroupDocs.Metadata
  Kullanarak
type: docs
url: /tr/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# GroupDocs.Metadata Kullanarak Sunum Dosyalarından java dosya oluşturma zaman damgasını nasıl alabilirsiniz

Metadata yönetimi, modern belge iş akışlarının temel taşlarından biridir ve **java get file creation timestamp** genellikle bir dosyanın kaynağını doğrulamak için ihtiyaç duyduğunuz ilk bilgidir. Bu adım adım kılavuzda, bir PowerPoint sunumundan oluşturma zaman damgasını nasıl okuyacağınızı, yazar, şirket ve anahtar kelimeler gibi ek özellikleri nasıl çekeceğinizi ve sonuçları herhangi bir Java tabanlı çözüme—belge yönetim sistemi, denetim izi oluşturucu veya uyumluluk panosu olsun—nasıl entegre edeceğinizi keşfedeceksiniz.

## Hızlı Yanıtlar
- **“java get file creation timestamp” ne anlama geliyor?** Bir dosyanın orijinal oluşturulma tarihini Java kodu aracılığıyla metadata API'leriyle almayı ifade eder.  
- **Bu işlemi hangi kütüphane gerçekleştiriyor?** Java için GroupDocs.Metadata, zaman damgalarını ve diğer yerleşik özellikleri okumak için temiz, format bağımsız bir API sağlar.  
- **Üretim ortamı için lisansa ihtiyacım var mı?** Evet—üretim için kalıcı bir lisans gereklidir; geliştirme ve test için ücretsiz deneme yeterlidir.  
- **Diğer metadata bilgilerini aynı anda çıkarabilir miyim?** Kesinlikle—yazar, şirket, kategori, anahtar kelimeler ve özel alanlar aynı API üzerinden erişilebilir.  
- **Hangi Java sürümü destekleniyor?** JDK 8 ve üzeri (Java 11, 17 ve sonrası ile uyumludur).

## “java get file creation timestamp” nedir?
`java get file creation timestamp` bir belgenin içinde depolanan **Created** metadata alanına erişerek dosyanın ilk oluşturulduğu anı almayı ifade eder. Bu zaman damgası, sürüm kontrolü, denetim izleri ve yasal uyumluluk için kritiktir çünkü içeriğin ne zaman ortaya çıktığını değiştirilemez bir kayıt sağlar.

## Belge özelliklerini çıkarmak için Java için GroupDocs.Metadata neden kullanılmalı?
GroupDocs.Metadata, onlarca dosya formatının düşük seviyeli ayrıştırmasını soyutlayarak iş mantığınıza odaklanmanızı sağlar. **50'den fazla giriş ve çıkış formatını** destekler—.pptx, .ppt, .pdf, .docx, .xlsx ve birçok görüntü türü dahil—ve tüm dosyayı belleğe yüklemeden çok sayfalı sunumları işleyebilir, büyük ölçekli ortamlar için bellek‑verimli bir çözüm sunar.

## Önkoşullar
- **GroupDocs.Metadata for Java** sürüm 24.12 ve üzeri.  
- Java Development Kit (JDK 8 veya daha yeni).  
- IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Java dosya I/O ve istisna yönetimi konusunda temel bilgi.

## Java için GroupDocs.Metadata Kurulumu

### Maven Kurulumu
Bağımlılıkları Maven ile yönetiyorsanız, `pom.xml` dosyanıza depo ve bağımlılığı ekleyin:

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

### Doğrudan İndirme
Alternatif olarak, kütüphaneyi resmi sürüm sayfasından indirebilirsiniz:  
[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

#### Lisans Edinme Adımları
- **Free Trial:** API'yi keşfetmek için ücretsiz deneme ile başlayın.  
- **Temporary License:** Sınırsız test için geçici bir anahtar alın.  
- **Purchase:** Üretim dağıtımları için tam lisans edinin.

### Temel Başlatma ve Kurulum
`Metadata`, Java için GroupDocs.Metadata içinde bir belgeye ait metadata'ya erişim sağlayan temel giriş sınıfıdır. Bağımlılık kurulduktan sonra bir `Metadata` nesnesi oluşturup sunum dosyanıza yönlendirin:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## Sunumdan java dosya oluşturma zaman damgasını nasıl alır ve diğer özellikleri nasıl çıkarırsınız?
`new Metadata("sample.pptx")` ile sunumu yükleyin, ardından `getCreatedTime()`, `getAuthor()`, `getCompany()` gibi uygun getter metodlarını çağırarak her bir bilgiyi alın. Bu tek‑nesne yaklaşımı, birkaç satır kodla tüm yerleşik özellikleri çekmenizi sağlar ve format‑spesifik ayrıştırıcılara ihtiyaç duymaz.

### Yazar Bilgisini Çıkarma
`getAuthor()` belge metadata'sında saklanan yazar adını döndürür; alan boşsa `null` döner.

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*Bu metod, bir veritabanına kaydedebileceğiniz, görüntüleyebileceğiniz veya loglayabileceğiniz düz bir `String` döndürür.*

### Oluşturulma Zamanını Çıkarma (java get file creation timestamp)
`getCreatedTime()` dosyanın ilk oluşturulduğu anı temsil eden bir `java.util.Date` nesnesi sağlar—tam olarak “java get file creation timestamp”nin tanımladığı şey budur.

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*Bu `Date` nesnesini `SimpleDateFormat` veya yeni `java.time` API'si ile biçimlendirerek görüntüleyebilir veya karşılaştırabilirsiniz.*

### Şirket Bilgisini Çıkarma
`getCompany()` sunumla ilişkili kuruluş adını döndürür; alan ayarlanmamışsa `null` döner.

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*Bu değer, belgeleri kurumsal kayıtlara veya CRM varlıklarına bağlamak için faydalıdır.*

### Çıkarabileceğiniz Ek Metadata
`getCategory()`, `getKeywords()` gibi metodlarla **Category**, **Keywords**, **Last Printed Date**, **Application Name** gibi diğer yerleşik alanları da aynı şekilde alabilirsiniz. Her getter aynı kalıpla çalışır: anında kullanılabilecek kısa, null‑güvenli bir değer döndürür.

## Pratik Uygulamalar
1. **Document Management Systems:** Sunumları yazar, şirket veya oluşturulma tarihine göre indeksleyerek hızlı arama ve geri getirme sağlayın.  
2. **Compliance Auditing:** Her arşivlenmiş slayt paketinin yasal saklama için depolanmadan önce bir oluşturulma zaman damgası içerdiğinden emin olun.  
3. **Automated Reporting:** Her bir sunumun kim tarafından ve ne zaman oluşturulduğunu listeleyen günlük özetler üretin, veriyi BI panolarına besleyin.  
4. **CRM Integration:** `Company` metadata'sını mevcut müşteri kayıtlarıyla eşleştirerek sunumların müşteri profillerine sorunsuz eklenmesini sağlayın.

## Performans Düşünceleri
- **Parallel Processing:** Binlerce dosyadan metadata çıkarırken her çıkarımı ayrı bir iş parçacığında çalıştırın veya CPU kullanımını maksimize etmek için bir iş parçacığı havuzu kullanın.  
- **Resource Management:** `Metadata` nesnesini otomatik olarak kapatmak ve yerel kaynakları serbest bırakmak için try‑with‑resources (örnekte gösterildiği gibi) kullanın.  
- **Batch Extraction:** GroupDocs.Metadata toplu işlemleri destekler; dosya yolu koleksiyonları üzerinde dönerken mümkün olduğunca tek bir `Metadata` örneğini yeniden kullanarak ek yükü azaltın.

## Yaygın Sorunlar ve Çözümler
- **Missing Metadata:** Bir getter `null` döndürürse, kaynak dosyada o özellik bulunmamaktadır. `null` değerlerine karşı koşullu kontroller veya varsayılan geri dönüşler ekleyin.  
- **Unsupported Format:** Dosyanın desteklenen bir PowerPoint formatı (`.pptx` veya `.ppt`) olduğundan emin olun. Desteklenmeyen bir tür yüklemeye çalışmak `UnsupportedFormatException` hatası üretir.  
- **License Errors:** Lisans dosyanızın sınıf yolunda doğru konumlandığından ve deneme süresinin dolmadığından emin olun; aksi takdirde API `LicenseException` fırlatır.

## Sıkça Sorulan Sorular

**S: Eksik metadata özellikleriyle nasıl başa çıkabilirim?**  
C: API ayarlanmamış alanlar için `null` döndürür. `(author != null ? author : "N/A")` gibi bir koşullu ifade kullanarak yedek değer sağlayabilirsiniz.

**S: GroupDocs.Metadata özel metadata alanlarını çıkarabilir mi?**  
C: Evet, yerleşik özelliklerin yanı sıra aynı API ile özel anahtar/değer çiftlerini okuyabilir ve yazabilirsiniz.

**S: Başka sunum formatları destekleniyor mu?**  
C: GroupDocs.Metadata PowerPoint (`.ppt`, `.pptx`) ile çalışır ve ayrıca PDF, Word, Excel ve birçok görüntü formatını da destekler.

**S: GroupDocs.Metadata Java için sistem gereksinimleri nelerdir?**  
C: Uyumlu bir JDK (8 veya üzeri) ve işlediğiniz belgelerin boyutuna göre yeterli heap belleği gerekir (örneğin 500 sayfalık bir sunum için 1 GB heap).

**S: Sorun yaşarsam nereden yardım alabilirim?**  
C: Resmi destek forumunu ziyaret edin: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## Kaynaklar

- **Documentation:** https://docs.groupdocs.com/metadata/java/
- **API Reference:** https://reference.groupdocs.com/metadata/java/
- **Download:** https://releases.groupdocs.com/metadata/java/
- **GitHub:** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
- **Free Support:** https://forum.groupdocs.com/c/metadata/
- **Temporary License:** https://purchase.groupdocs.com/temporary-license/

Bu kılavuzu izleyerek artık **java get file creation timestamp** ve **java extract document properties** işlemlerini PowerPoint sunumlarından GroupDocs.Metadata kullanarak yapabilirsiniz. Bu kod parçacıklarını projelerinize entegre ederek belge zekâsını artırın, uyumluluk iş akışlarını basitleştirin ve downstream analizleri güçlendirin.

**Son Güncelleme:** 2026-06-27  
**Test Edilen Versiyon:** GroupDocs.Metadata 24.12 for Java  
**Yazar:** GroupDocs

## İlgili Eğitimler

- [Java'da GroupDocs.Metadata Kullanarak PowerPoint Sunumlarından Metadata Nasıl Çıkarılır](/metadata/java/working-with-metadata/extract-presentation-metadata-groupdocs-java/)
- [Java Metadata Güncellemelerini Tarihe Göre Otomatikleştirme: GroupDocs.Metadata ile Verimli Dosya Yönetimi](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)
- [Metadata Yönetimini Ustalaştırın: Java için GroupDocs.Metadata ile Belge Özelliklerini ve Şifreleme Durumunu Tespit Etme](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)