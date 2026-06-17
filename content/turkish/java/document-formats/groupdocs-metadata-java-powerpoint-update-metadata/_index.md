---
date: '2026-05-27'
description: Java'da pptx CreatedTime'ı ayarlamayı, PowerPoint metadata'sını güncellemek
  için GroupDocs Maven Dependency'yi kullanmayı ve PPTX oluşturulma tarihini nasıl
  değiştireceğinizi öğrenin.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Java'da PPTX CreatedTime'ı GroupDocs Maven Dependency ile Ayarlayın
type: docs
url: /tr/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Java'da GroupDocs.Metadata ile PPTX CreatedTime Ayarlama

Doğru meta veriler, modern belge iş akışlarında uyumluluk ve bulunabilirlik için gereklidir. **GroupDocs.Metadata** ile programlı olarak **Java'da PPTX CreatedTime ayarlayabilir**, yazar veya şirket gibi diğer yerleşik özelliklerin yanında **PPTX oluşturma tarihini değiştirebilirsiniz**. Bu öğretici, Maven kurulumundan API başlatmaya, meta verileri güncellemeye ve değiştirilmiş sunumu kaydetmeye kadar sizi adım adım yönlendirir—tüm bunlar net, üretim‑hazır kod ile.

## Hızlı Yanıtlar
- **Java'da PowerPoint meta verilerini güncelleyen kütüphane hangisidir?** GroupDocs.Metadata, GroupDocs Maven bağımlılığı aracılığıyla.  
- **PPTX CreatedTime özelliğini ayarlayabilir miyim?** Evet—`root.getDocumentProperties().setCreatedTime(yourDate)` kullanın.  
- **Üretim için lisans gerekli mi?** Değerlendirme için bir deneme sürümü çalışır; üretim dağıtımları için ticari lisans zorunludur.  
- **Örnekte hangi yapı aracı kullanılıyor?** Maven (JAR'ı manuel olarak da indirebilirsiniz).  
- **API, Java 8 ve üzerini destekliyor mu?** Kesinlikle—GroupDocs.Metadata, Java 8+ hedefler.

## GroupDocs Maven Bağımlılığı Nedir?
**GroupDocs Maven bağımlılığı**, en son GroupDocs.Metadata kütüphanesini Java projenize çeken Maven‑uyumlu bir depo girişidir. Bağımlılık yönetimini, geçişli kütüphaneleri otomatik olarak çözüp, her zaman en yeni ve güvenli sürümü kullanmanızı sağlayarak, manuel JAR indirme veya sürüm takibi ihtiyacını ortadan kaldırarak basitleştirir.

## PPTX Oluşturma Tarihini Değiştirmek İçin Neden GroupDocs.Metadata Kullanmalı?
GroupDocs.Metadata, PPTX oluşturma zaman damgalarının otomatik ve toplu‑hazır güncellemelerini sağlar, böylece her sunum kurumsal politikalar veya yasal gerekliliklere uygun olur. CreatedTime özelliğini programlı olarak ayarlayarak manuel düzenlemeden kaçınır, insan hatasını azaltır ve değişikliği CI/CD boru hatlarına veya göç betiklerine entegre ederek sorunsuz belge yönetimi sağlayabilirsiniz.

## Önkoşullar
- Java 8 veya üzeri yüklü.  
- IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Bağımlılık yönetimi için Maven.  
- GroupDocs deneme sürümüne veya satın alınmış lisansa erişim.

## Java'da PPTX CreatedTime Nasıl Ayarlanır?
`Metadata` sınıfı bir belgeyi temsil eder ve meta veri özelliklerine erişim sağlar.

PowerPoint dosyanızı `new Metadata("presentation.pptx")` ile yükleyin, kök paketi alın, istediğiniz `java.util.Date` ile `setCreatedTime` çağırın ve son olarak değişiklikleri yazmak için `save` metodunu çağırın. Bu uçtan uca akış, tüm slayt içeriği ve diğer özellikleri korurken oluşturma tarihini değiştirir.

### Maven Kurulumu
GroupDocs deposunu ve meta veri bağımlılığını `pom.xml` dosyanıza ekleyin:

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

> **Pro ipucu:** Sürüm numarasını güncel tutmak, en son hata düzeltmeleri ve performans iyileştirmelerinden yararlanmanızı sağlar.

### Doğrudan İndirme (Maven kullanmak istemezseniz)

Alternatif olarak, en son JAR'ı [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) adresinden indirebilirsiniz.

#### Lisans Edinme

GroupDocs.Metadata'i değerlendirmek için ücretsiz bir deneme ile başlayın veya geçici bir lisans isteyin. Üretim kullanımı için, bir lisansı [GroupDocs'un resmi web sitesinden](https://purchase.groupdocs.com/temporary-license/) satın alın.

## Temel Başlatma ve Kurulum

Kütüphane sınıf yolunda olduğunda, PowerPoint dosyanıza işaret eden bir `Metadata` örneği oluşturabilirsiniz:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Bu kod, sunumu bir try‑with‑resources bloğunda açar ve dosya tutamacının otomatik olarak serbest bırakılmasını garanti eder.

## Yerleşik Meta Verileri Güncellemek İçin Adım‑Adım Kılavuz

### Adım 1: Sunum Belgesini Yükleyin

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Dosyayı yüklemek, meta verileri okumanıza veya yazmanıza izin veren bir bağlantı kurar.

### Adım 2: Sunumun Kök Paketine Erişin

`root` nesnesi, sunumun temel paketine ve yerleşik özelliklerine erişim sağlar.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

`root` nesnesi tüm yerleşik belge özelliklerini ortaya çıkarır.

### Adım 3: Yerleşik Belge Özelliklerini Güncelleyin (oluşturma tarihi dahil)

`setCreatedTime`, belgeye yeni bir oluşturma zaman damgası atar.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Burada, yeni bir `Date` nesnesini `CreatedTime`'a atayarak **PPTX CreatedTime** nasıl ayarlanır gösteriyoruz. `new Date()` ifadesini ihtiyacınız olan herhangi bir zaman damgasıyla değiştirin.

### Adım 4: Güncellenmiş Sunumu Kaydedin

`save`, değiştirilmiş meta verileri bir dosyaya yazar.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

`save` çağrısı, değiştirilmiş meta verileri yeni bir PowerPoint dosyasına yazar, orijinali dokunulmaz bırakır.

## Sorun Giderme İpuçları
- **Dosya Bulunamadı:** Giriş yolunu ve dosya izinlerini iki kez kontrol edin.  
- **Sürüm Uyumsuzluğu:** `groupdocs-metadata` sürümünün Java çalışma ortamınızla eşleştiğinden emin olun.  
- **Özellik Güncellenmiyor:** `save` çağırmadan önce `setCreatedTime` (veya ilgili ayarlayıcı) metodunu çağırdığınızdan emin olun.

## Pratik Uygulamalar
1. **Kurumsal Markalaşma:** Dağıtımdan önce tüm slayt setlerine doğru şirket adı ve kategorisini otomatik olarak ekleyin.  
2. **Belge Yönetim Sistemleri:** Daha hızlı erişim için PPTX dosyalarını aranabilir meta verilerle zenginleştirin.  
3. **Eğitim Kaynakları:** Ders slaytları boyunca yazar ve müfredat bilgilerini güncel tutun.  
4. **İşbirliği Takibi:** Sorumluluğu sağlamak için katkıda bulunanların adlarını kaydedin.  
5. **CMS Entegrasyonu:** Meta veri değişikliklerini içerik yönetim platformunuzla gerçek zamanlı senkronize edin.

## Performans Düşünceleri
- **Toplu İşleme:** Dosya listesi üzerinde döngü yapın ve mümkün olduğunda tek bir `Metadata` örneğini yeniden kullanın.  
- **Bellek Yönetimi:** Yerel kaynakları hızlıca serbest bırakmak için her zaman try‑with‑resources (gösterildiği gibi) kullanın.  
- **Verimli Veri Yapıları:** Tekrarlayan çağrıları azaltmak için meta veri güncellemelerini uygulamadan önce bir haritada saklayın.

## Sıkça Sorulan Sorular

**S: GroupDocs Maven bağımlılığının temel amacı nedir?**  
C: Maven‑tabanlı Java projelerine en son GroupDocs.Metadata kütüphanesini eklemenin pratik bir yolunu sağlar.

**S: Diğer özellikleri etkilemeden PPTX oluşturma tarihini nasıl ayarlayabilirim?**  
C: `metadata.save()` çağırmadan önce `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` kullanın.

**S: Bu kodu geliştirme ortamında çalıştırmak için lisansa ihtiyacım var mı?**  
C: Geliştirme ve test için geçici bir deneme lisansı yeterlidir; üretim için tam lisans gereklidir.

**S: Özel meta veri alanlarını da güncelleyebilir miyim?**  
C: Evet—GroupDocs.Metadata, API'si aracılığıyla hem yerleşik hem de özel özellikleri destekler.

**S: Bir hata yaparsam değişiklikleri geri almanın bir yolu var mı?**  
C: Orijinal dosyanın bir kopyasını tutun veya üzerine yazmadan önce mevcut özellik değerlerini okuyun, ardından gerekirse geri yükleyin.

## Kaynaklar

- [Dokümantasyon](https://docs.groupdocs.com/metadata/java/)
- [API Referansı](https://apireference.groupdocs.com/metadata/java/)

---

**Son Güncelleme:** 2026-05-27  
**Test Edilen Versiyon:** GroupDocs.Metadata 24.12 for Java  
**Yazar:** GroupDocs  

## İlgili Öğreticiler

- [PowerPoint'te GroupDocs.Metadata Java API Kullanarak Özel Meta Verileri Güncelleme](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [GroupDocs.Metadata Java Kullanarak Word Belge Meta Verilerini Güncelleme: Tam Kılavuz](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Belge Yönetimi için Java'da GroupDocs.Metadata ile PDF Meta Verilerini Verimli Güncelleme](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)