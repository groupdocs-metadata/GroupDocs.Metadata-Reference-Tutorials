---
date: '2026-08-20'
description: GroupDocs.Metadata kullanarak Java'da XMP meta verilerini nasıl çıkaracağınızı
  öğrenin. Bu kılavuz, temel, Dublin Core ve Photoshop XMP meta verilerini nasıl çıkaracağınızı
  gösterir.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: GroupDocs.Metadata kullanarak Java'da XMP meta verilerini nasıl çıkaracağınızı
  öğrenin. Bu öğretici, temel, Dublin Core ve Photoshop XMP çıkarımını pratik kod
  örnekleriyle kapsar.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: GroupDocs.Metadata for Java ile XMP meta verilerini nasıl çıkarılır
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: GroupDocs.Metadata for Java ile XMP meta verilerini nasıl çıkarılır
type: docs
url: /tr/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Java için GroupDocs.Metadata ile XMP meta verilerini nasıl çıkarılır

Modern dijital iş akışlarında, **XMP meta verilerini nasıl çıkarılır** sorusunun hızlı ve güvenilir bir şekilde yanıtlanması, aranabilir bir varlık kütüphanesi ile kaotik bir dosya dökümü arasındaki farkı yaratabilir. Bu öğretici, kütüphaneyi kurmaktan dosyaları yüklemeye ve temel, Dublin Core ve Photoshop‑özel XMP paketlerini çıkarmaya kadar her adımı size gösterir—böylece bugün Java uygulamalarınıza zengin meta verileri entegre edebilirsiniz.

## Hızlı cevaplar
- **Java'da XMP'yi hangi kütüphane yönetir?** GroupDocs.Metadata for Java.
- **Minimum Java sürümü?** JDK 8 veya üzeri.
- **PNG ve JPEG dosyalarını okuyabilir miyim?** Evet, her ikisi de kutudan çıkar çıkmaz desteklenir.
- **Üretim için lisans gerekli mi?** Evet, tam veya geçici bir lisans gereklidir.
- **API referansını nerede bulabilirim?** Resmi GroupDocs.Metadata dokümantasyon sitesinde.

## XMP meta verileri nedir?
XMP (Extensible Metadata Platform), medya dosyalarının içine yapılandırılmış meta verileri gömmek için kullanılan bir ISO standardı formattır. Uygulamalar arası birlikte çalışabilirliği ve orijinal içeriği değiştirmeden kalıcı veri depolamayı sağlar. Yaratıcı, telif hakkı, kamera ayarları ve özel etiketler gibi bilgileri dosyanın içinde saklayarak, XMP meta verilerinin varlıkla birlikte her yere taşınmasını garantiler; bu da çeşitli sistemlerde kataloglamayı ve aramayı basitleştirir.

## Neden GroupDocs.Metadata for Java kullanmalı?
GroupDocs.Metadata **30+ dosya formatını** (PNG, JPEG, TIFF ve PSD dahil) destekler ve **2 GB**'a kadar dosyaları bellek içinde tamamen yüklemeden işleyebilir; bu da genel ayrıştırıcılara kıyasla **CPU kullanımında %30 azalma** sağlar. Bu özellik, büyük ölçekli dijital varlık yönetimi (DAM) sistemleri için idealdir.

## Önkoşullar

- **Java Development Kit (JDK) 8+** yüklü.
- **Maven** bağımlılık yönetimi için.
- Java I/O ve nesne‑yönelimli programlamaya temel aşinalık.

## GroupDocs.Metadata for Java nasıl kurulur?
Başlamak için GroupDocs deposunu ve kütüphane bağımlılığını Maven `pom.xml` dosyanıza ekleyin. Bu, Maven'in artefaktları çözümlemesini ve otomatik olarak güncel tutmasını sağlar; böylece gelecekteki yükseltmeler ve güvenlik yamaları daha kolay yönetilir. `pom.xml` dosyasını güncelledikten sonra `mvn clean install` komutunu çalıştırarak gerekli JAR'ları indirin ve kurulumun başarılı olduğunu doğrulayın.

```xml
<!-- ```xml
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
``` -->
```

Manuel bir yaklaşımı tercih ediyorsanız, resmi sürüm sayfasından en yeni JAR dosyasını indirin:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Lisans edinme
- **Ücretsiz deneme** – tüm özellikleri 30 gün boyunca değerlendirin.
- **Geçici lisans** – geliştirme sırasında kısıtlama olmadan kullanın.
- **Tam lisans** – üretim ortamları için gereklidir.

## Temel başlatma

`Metadata` tüm işlemler için giriş noktasıdır. Tek bir dosyayı temsil eder ve gömülü XMP paketlerine erişim sağlar.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Kullanım sonrası kaynakların serbest bırakıldığından emin olun
metadata.dispose();
```
```

## Temel XMP meta verileri nasıl çıkarılır?

Görüntüyü yükleyin, XMP paketini açın ve yaratıcı araç, zaman damgaları gibi ortak özellikleri okuyun.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Gerekli olduğu gibi çıkarılan özellikleri kullanın
   }
   ```
```

## Dublin Core XMP meta verileri nasıl çıkarılır?

Dublin Core şeması, başlık, yaratıcı ve konu gibi standart tanımlayıcı öğeleri saklar. `DublinCorePackage` sınıfı üzerinden erişilir.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Gerekli olduğu gibi çıkarılan özellikleri kullanın
   }
   ```
```

## Photoshop‑özel XMP meta verileri nasıl çıkarılır?

Photoshop, renk modu, çözünürlük ve katman sayısı gibi ek bilgiler gömer. Bu değerler `PhotoshopPackage` aracılığıyla alınır.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Gerekli olduğu gibi çıkarılan özellikleri kullanın
   }
   ```
```

## Pratik uygulamalar

- **Dijital varlık yönetimi** – görüntüleri yaratıcı, telif hakkı veya kamera ayarlarıyla etiketleyip arayın.
- **Otomatik yayın akışları** – web galerilerine göndermeden önce XMP'yi ekleyin veya değiştirin.
- **Analitik** – binlerce dosyanın meta verilerini toplayarak kullanım trendlerini keşfedin.

## Performans değerlendirmeleri

`Metadata` sınıfı dosyanın meta verilerine ve XMP paketlerine erişim sağlar. Okuma işlemi tamamlandığında `Metadata` nesnelerini serbest bırakın; böylece yerel kaynaklar temizlenir. `LoadOptions.LAZY` ayarı, meta verilerin tembel yüklenmesini sağlayarak bellek tüketimini azaltır. Büyük dosyaları `Metadata.load(InputStream)` ile akıtmak yığın kullanımını düşük tutar. Çok sayıda küçük dosya okurken tek bir `Metadata` örneği yeniden kullanarak nesne oluşturma maliyetini düşürün.

## Yaygın hatalar ve sorun giderme

| Semptom | Muhtemel neden | Çözüm |
|---|---|---|
| `NullPointerException` XMP'ye erişirken | Dosyada XMP paketi yok | `metadata.getXmpPackage()` metodunu çağırın ve okumadan önce `null` kontrolü yapın. `getXmpPackage()` yöntemi XMP paket nesnesini döndürür, yoksa `null` verir. |
| 500 MB görüntülerde yavaş işleme | Tüm dosyayı belleğe yükleme | `metadata.load(InputStream)` kullanın ve `metadata.setLoadOptions(LoadOptions.LAZY)` etkinleştirin. |
| Photoshop alanları eksik | Görüntü Photoshop katman bilgisi olmadan kaydedildi | Kaynak dosyanın Photoshop'tan “Save XMP” seçeneğiyle dışa aktarıldığını doğrulayın. |

## Sıkça sorulan sorular

**Q: PDF dosyalarından XMP çıkarabilir miyim?**  
A: Evet, GroupDocs.Metadata aynı `Metadata` API'si üzerinden PDF XMP paketlerini destekler.

**Q: Desteklenmeyen bir dosya formatı ile karşılaşırsam ne olur?**  
A: Kütüphane `UnsupportedFormatException` hatası fırlatır; bunu yakalayarak genel bir işleyiciye yönlendirebilirsiniz.

**Q: XMP meta verilerini değiştirip geri kaydedebilir miyim?**  
A: Kesinlikle. Özellikleri değiştirdikten sonra `metadata.save("output.png")` çağrısıyla güncellemeleri kalıcı hale getirin.

**Q: Kütüphane Android'de çalışır mı?**  
A: Çekirdek Java kütüphanesi Android API 24+ ile uyumludur; ancak `android`‑özel artefaktı eklemeniz gerekir.

**Q: Şifreli görüntülerle nasıl başa çıkılır?**  
A: `Metadata` yapıcısına şifreyi sağlayın: `new Metadata(filePath, "password")`.

## Sonuç

Artık **Java için GroupDocs.Metadata ile XMP meta verilerini nasıl çıkarılır** konusunda eksiksiz, üretim‑hazır bir kılavuza sahipsiniz. Yukarıdaki adımları izleyerek uygulamalarınızı aranabilir, standart‑uyumlu meta verilerle zenginleştirebilir ve güçlü varlık‑yönetimi yeteneklerinin kilidini açabilirsiniz.

## Sonraki adımlar

Resmi dokümantasyonu inceleyerek tam özellik setine daha derinlemesine dalın ve IPTC ve EXIF gibi diğer meta veri standartlarıyla da deneyler yapın.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Son Güncelleme:** 2026-08-20  
**Test Edilen Versiyon:** GroupDocs.Metadata for Java 23.11  
**Yazar:** GroupDocs  

- [Dokümantasyon](https://docs.groupdocs.com/metadata/java/)
- [API Referansı](https://reference.groupdocs.com/metadata/java/)
- [İndir](https://releases.groupdocs.com/metadata/java/)
- [GitHub Deposu](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Ücretsiz Destek Forumu](https://forum.groupdocs.com/c/metadata/)
- [Geçici Lisans](https://purchase.groupdocs.com/temporary-license/)

## İlgili Öğreticiler

- [Dublin Core Meta Verilerini Epub'tan Çıkarma – Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Java'da EXIF Yazılım Etiketini Çıkarma: GroupDocs.Metadata Kullanarak Tam Kılavuz](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [GroupDocs.Metadata for Java ile Meta Veri Çıkarma – Öğreticiler ve Örnekler](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}