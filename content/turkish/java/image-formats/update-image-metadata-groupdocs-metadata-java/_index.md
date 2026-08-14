---
date: '2026-06-12'
description: Java için GroupDocs.Metadata ile görüntü meta verilerini nasıl güncelleyeceğinizi
  öğrenin; Dublin Core, Camera Raw, XMP Basic ve Job Ticket şemalarını kapsar.
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
title: GroupDocs.Metadata kullanarak Java'da görüntü meta verilerini nasıl güncelleyin
type: docs
url: /tr/java/image-formats/update-image-metadata-groupdocs-metadata-java/
weight: 1
---

# GroupDocs.Metadata kullanarak Java'da görüntü meta verilerini güncelleme

Modern dijital iş akışlarında, **updating image metadata java** varlıkların aranabilir, uyumlu ve sonraki işleme hazır olmasını sağlamak için gereklidir. Fotoğraf yönetimi uygulaması, içerik yönetim sistemi ya da otomatik arşivleme hattı oluşturuyor olun, meta verileri programlı olarak düzenleme yeteneği sayısız manuel saat tasarrufu sağlar. Bu kılavuz, GroupDocs.Metadata for Java ile Dublin Core, Camera Raw, XMP Basic ve Basic Job Ticket meta veri şemalarını değiştirmek için gereken tüm adımları size gösterir.

## Hızlı Yanıtlar
- **Java'da görüntü meta verilerini hangi kütüphane yönetir?** GroupDocs.Metadata for Java.  
- **Dublin Core ve XMP'yi tek seferde güncelleyebilir miyim?** Evet – bir `Metadata` nesnesi oluşturun ve kaydetmeden önce birden fazla paketle çalışın.  
- **Deneme kullanımı için lisansa ihtiyacım var mı?** Ücretsiz deneme lisansı tüm özelliklerin kilidini açar; tam lisans kullanım sınırlamalarını kaldırır.  
- **Hangi Java sürümü gereklidir?** JDK 8 veya üzeri.  
- **Bağımlılığı eklemenin tek yolu Maven mi?** Maven önerilir, ancak JAR dosyasını resmi sürüm sayfasından da indirebilirsiniz.  

## GroupDocs.Metadata ile Java'da görüntü meta verilerini nasıl güncellerim?
`Metadata`, bir görüntünün meta verilerine okuma/yazma erişimi sağlayan birincil sınıftır. Hedef görüntüyü bir `Metadata` örneğine yükleyin, istenen meta veri paketini (ör. Dublin Core, Camera Raw) alın veya oluşturun, gerekli özellikleri ayarlayın ve değişiklikleri diske yazmak için `save()` metodunu çağırın. Bu akış JPEG, PNG, TIFF ve birçok diğer format için çalışır.

### Neden GroupDocs.Metadata for Java'ı seçmelisiniz?
GroupDocs.Metadata **50+ giriş ve çıkış formatını** destekler, çok sayfalı görüntü dosyalarını tüm dosyayı belleğe yüklemeden işler ve tek bir işlemde birden fazla meta veri şemasını güncellemenizi sağlayan akıcı bir API sunar. Kütüphane tamamen iş parçacığı güvenlidir, bu da yüksek verimli sunucu ortamları için idealdir.

## Önkoşullar
- **Java Development Kit (JDK) 8+** – `java -version` komutunun 1.8 veya daha yeni bir sürüm rapor ettiğinden emin olun.  
- **Maven** – bağımlılık yönetimi için; isterseniz Gradle da kullanabilirsiniz.  
- **Temel Java bilgisi** – IntelliJ IDEA veya Eclipse gibi IDE'lere aşina olmak.  

## GroupDocs.Metadata for Java'ı Kurma
Kütüphaneyi Maven projenize eklemek için aşağıdaki bağımlılığı `pom.xml` dosyanıza ekleyin:

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

Ayrıca en son JAR dosyasını resmi sürüm sayfasından indirebilirsiniz: [GroupDocs.Metadata for Java sürümleri](https://releases.groupdocs.com/metadata/java/).

### Lisans Edinme
Tüm özellikleri keşfetmek için ücretsiz bir deneme lisansı ile başlayın. Üretim dağıtımları için tam bir lisans satın alın veya [satın alma sayfası](https://purchase.groupdocs.com/temporary-license) üzerinden geçici bir lisans isteyin. Geçerli bir lisans tüm deneme kısıtlamalarını kaldırır ve premium desteğin kilidini açar.

### Temel Başlatma
`Metadata` sınıfı, görüntü dosyalarında tüm okuma/yazma işlemleri için giriş noktasıdır. Bağımlılığı ekledikten sonra kütüphaneyi aşağıdaki gibi başlatabilirsiniz:

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

## Belirli Meta Veri Şemalarını Güncelleme

### GroupDocs.Metadata for Java kullanarak Dublin Core meta veri şemasını nasıl güncellerim?
`Metadata`, görüntü meta verilerine erişim için ana giriş noktasıdır. `DublinCorePackage`, Dublin Core meta veri kümesini temsil eder ve standart tanımlayıcı alanların ayarlanmasına izin verir. `format`, `rights` ve `subject` gibi evrensel alanları ayarlamanızı sağlar. Bir `Metadata` nesnesi oluşturun, `DublinCorePackage`'i alın, değerleri ayarlayın ve dosyayı kaydedin; böylece standartlara uygun tanımlayıcı bilgiler elde edilir.

1. **Metadata Nesnesini Başlatın:**  
   `Metadata` sınıfı, bellekte tek bir görüntü dosyasını temsil eder ve desteklenen tüm meta veri paketlerine erişim sağlar.

   ```java
   try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/GifWithXmp")) {
       IXmp root = (IXmp) metadata.getRootPackage();
       if (root.getXmpPackage() != null) {
           // Further steps will be added here
       }
   }
   ```

2. **Dublin Core Paketi Oluşturun veya Alın:**  
   `metadata.getDublinCorePackage()` metodunu kullanarak mevcut paketi alın veya yoksa yeni bir tane oluşturun.

   ```java
   if (root.getXmpPackage().getSchemes().getDublinCore() == null) {
       root.getXmpPackage().getSchemes().setDublinCore(new XmpDublinCorePackage());
   }
   ```

3. **Özellikleri Güncelleyin:**  
   `format`, `rights` ve `subject` gibi özellikleri paket nesnesi üzerinde doğrudan ayarlayın.

   ```java
   root.getXmpPackage().getSchemes().getDublinCore()
       .setFormat("image/gif")
       .setRights("Copyright (C) 2011-2021 GroupDocs. All Rights Reserved")
       .setSubject("test");
   ```

4. **Değişiklikleri Kaydedin:**  
   Güncellenen meta verileri kalıcı hale getirmek için `metadata.save(outputPath)` metodunu çağırın.

   ```java
   metadata.save("YOUR_OUTPUT_DIRECTORY/OutputGif");
   ```

### GroupDocs.Metadata for Java ile Camera Raw meta verilerini nasıl değiştiririm?
`Metadata`, görüntü meta verilerini okuma ve yazma için birincil sınıftır. `CameraRawPackage`, pozlama ve gölgeler gibi Camera Raw'a özgü meta verilere erişim sağlar. Camera Raw meta verileri gölgeler, otomatik parlaklık ve pozlama gibi teknik çekim parametrelerini saklar. Bu alanları güncellemek, Lightroom gibi araçların görüntüyü doğru yorumlamasını sağlar, toplu işleme iyileştirir ve büyük fotoğraf koleksiyonları arasında tutarlılığı korur.

1. **Metadata Nesnesini Başlatın:**  
   Dublin Core için oluşturduğunuz aynı `Metadata` örneğini yeniden kullanın.

2. **Camera Raw Paketi Oluşturun veya Alın:**  
   Değişiklik yapmadan önce mevcut bir `CameraRawPackage` olup olmadığını kontrol edin.

   ```java
   if (root.getXmpPackage().getSchemes().getCameraRaw() == null) {
       root.getXmpPackage().getSchemes().setCameraRaw(new XmpCameraRawPackage());
   }
   ```

3. **Özellikleri Güncelleyin:**  
   İstenilen görüntü özelliklerini yansıtmak için `shadows`, `autoBrightness` ve `exposure` gibi ayarları değiştirin.

   ```java
   root.getXmpPackage().getSchemes().getCameraRaw()
       .setShadows(50)
       .setAutoBrightness(true)
       .setAutoExposure(true)
       .setCameraProfile("test")
       .setExposure(0.0001);
   ```

4. **Değişiklikleri Kaydedin:**  
   Değişiklikleri seçtiğiniz çıktı dizinine kalıcı hale getirin.

### GroupDocs.Metadata for Java kullanarak XMP Basic meta verilerini nasıl güncellerim?
`Metadata`, görüntü meta verilerini manipüle etmek için kullanılan temel sınıftır. `XmpBasicPackage`, temel meta veri alanları için XMP Basic şemasını temsil eder. XMP Basic, oluşturulma tarihi, temel URL ve derecelendirme gibi temel alanları kapsar. Bu nitelikleri güncellemek kataloglamayı geliştirir, arama alaka düzeyini artırır ve içerik yönetim sistemleriyle daha iyi entegrasyon sağlar; böylece dijital varlık araçları görüntüleri kullanıcı tanımlı kriterlere göre düzenler ve gösterir.

1. **Metadata Nesnesini Başlatın:**  
   Tutorial boyunca aynı `Metadata` örneğini kullanın.

2. **Mevcut XMP Basic Paketi Değiştirin:**  
   Eğer bir XMP Basic paketi eksikse, yeni bir tane oluşturun ve `Metadata` nesnesine ekleyin.

   ```java
   root.getXmpPackage().getSchemes().setXmpBasic(new XmpBasicPackage());
   ```

3. **Özellikleri Güncelleyin:**  
   Gerekli olduğunda `creationDate`, `baseURL` ve `rating` değerlerini ayarlayın.

   ```java
   root.getXmpPackage().getSchemes().getXmpBasic()
       .setCreateDate(new Date())
       .setBaseUrl("https://groupdocs.com")
       .setRating(5);
   ```

4. **Değişiklikleri Kaydedin:**  
   Güncellenen meta verileri diske geri yazın.

### Java'da Basic Job Ticket meta veri şemasıyla nasıl çalışılır?
`Metadata`, görüntü meta verilerini işlemek için birincil sınıftır. `BasicJobTicketPackage`, iş bileti meta verilerini yönetir ve iş akışı bilgilerini görüntülere gömmeyi sağlar. Basic Job Ticket şeması, iş kimliklerini, adlarını ve URL'leri doğrudan görüntü dosyasına ekler; böylece sonraki sistemler işleme aşamalarını izleyebilir ve görüntüleri belirli görevlerle ilişkilendirebilir. İş biletlerini eklemek, otomatik hatlarda denetlenebilirliği ve operasyonel verimliliği artırır.

1. **Metadata Nesnesini Başlatın:**  
   Aynı `Metadata` örneğini kullanmaya devam edin.

2. **Basic Job Ticket Paketini Ayarlayın:**  
   Mevcut paketi alın veya yoksa yeni bir tane oluşturun.

   ```java
   root.getXmpPackage().getSchemes().setBasicJobTicket(new XmpBasicJobTicketPackage());
   ```

3. **İşleri Yapılandırın:**  
   `id`, `name` ve `url` gibi iş özelliklerini tanımlayarak sonraki işleme sistemlerinin görüntünün yaşam döngüsünü izlemesini sağlayın.

   ```java
   XmpJob job = new XmpJob();
   job.setID("1");
   job.setName("test job");
   job.setUrl("https://groupdocs.com");

   root.getXmpPackage().getSchemes().getBasicJobTicket()
       .setJobs(new XmpJob[]{job});
   ```

4. **Değişiklikleri Kaydedin:**  
   Tüm iş bileti bilgilerini çıktı klasörüne kalıcı hale getirin.

## Pratik Uygulamalar
- **Fotoğraf Stüdyoları:** Her dışa aktarılan JPEG'e telif hakkı ve lisans bilgilerini otomatik olarak ekleyin, yasal uyumu sağlayın.  
- **İçerik Yönetim Sistemleri (CMS):** Yüklenen varlıkları Dublin Core ve XMP verileriyle zenginleştirerek arama motorlarının görüntüleri daha etkili indekslemesini sağlayın.  
- **Dijital Varlık Yönetimi (DAM):** İşleme durumunu gömmek için Basic Job Ticket şemasını kullanın; böylece görüntüleri karmaşık hatlar içinde izlemek kolaylaşır.  

## Yaygın Sorunlar ve Çözümler
- **Eksik Paket Hataları:** Özellikleri ayarlamadan önce her zaman `get...Package()` metodunu çağırın; eğer `null` dönerse, önce paketi oluşturun.  
- **Dosya İzin Problemleri:** Özellikle korumalı dizinlere yazarken Java sürecinizi yeterli işletim sistemi izinleriyle çalıştırın.  
- **Desteklenmeyen Formatlar:** GroupDocs.Metadata 50'den fazla görüntü formatını destekler; bilinmeyen bir uzantıyla karşılaşırsanız resmi belgeleri kontrol edin.  

## Sıkça Sorulan Sorular

**Q: Tek bir işlemde birden fazla meta veri şemasını güncelleyebilir miyim?**  
A: Evet. Bir `Metadata` örneği oluşturduktan sonra, paketlerin herhangi bir kombinasyonunu alıp değiştirebilir ve `save()` metodunu bir kez çağırabilirsiniz.

**Q: Kütüphane, bulut depolama (ör. AWS S3) içinde saklanan görüntülerle çalışır mı?**  
A: Kesinlikle. Görüntüyü S3'ten bir `InputStream` olarak yükleyin, akışı `Metadata` yapıcısına geçirin ve sonucu tekrar buluta kaydedin.

**Q: Üretim kullanımı için ticari bir lisans gerekli mi?**  
A: Üretim dağıtımları için geçerli bir ticari lisans gereklidir; deneme lisansı sadece değerlendirme ve ticari olmayan testlerle sınırlıdır.

**Q: Resmi olarak hangi Java sürümleri destekleniyor?**  
A: GroupDocs.Metadata for Java, JDK 8, 11 ve 17'yi destekler; bu sayede hem eski hem de modern uygulamalarla uyumluluk sağlar.

**Q: Kütüphane büyük görüntü dosyalarını (ör. >100 MB) nasıl yönetir?**  
A: API verileri akış olarak işler ve dosyanın tamamını belleğe yüklemez; bu sayede aşırı heap kullanımı olmadan çok büyük görüntüleri işleyebilirsiniz.

## Sonuç
Bu kılavuzdaki adımları izleyerek, GroupDocs.Metadata kullanarak **updating image metadata java** için eksiksiz, üretim‑hazır bir iş akışına sahip oldunuz. Görüntüleri Dublin Core, Camera Raw, XMP Basic ve Job Ticket bilgileriyle güvenle zenginleştirebilir, dijital varlıklarınızı daha aranabilir, uyumlu ve otomatik hatlara hazır hâle getirebilirsiniz. Kütüphanenin meta veri çıkarma ve doğrulama gibi diğer özelliklerini keşfederek varlık yönetimi stratejinizi daha da güçlendirin.

---

**Son Güncelleme:** 2026-06-12  
**Test Edilen Versiyon:** GroupDocs.Metadata for Java 23.12  
**Yazar:** GroupDocs

## İlgili Eğitimler

- [GroupDocs.Metadata Java Kullanarak Canon CR2 Dosyalarından Meta Veri Çıkarma: Görüntü Formatları için Kapsamlı Rehber](/metadata/java/image-formats/extract-metadata-groupdocs-metadata-canon-cr2/)
- [Belge Yönetimi için Java'da GroupDocs.Metadata ile PDF Meta Verilerini Verimli Şekilde Güncelleme](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [GroupDocs.Metadata ile Java'da MP3 ID3v2 Etiketlerini Güncelleme - Kapsamlı Rehber](/metadata/java/audio-video-formats/update-mp3-id3v2-tags-groupdocs-metadata-java/)