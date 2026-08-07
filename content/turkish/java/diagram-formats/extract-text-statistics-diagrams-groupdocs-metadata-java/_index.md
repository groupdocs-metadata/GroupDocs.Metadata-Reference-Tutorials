---
date: '2026-03-20'
description: GroupDocs.Metadata for Java kullanarak diyagram sayfa sayısını nasıl
  alacağınızı ve diyagramlardan metin istatistiklerini nasıl çıkaracağınızı öğrenin.
  Adım adım kurulum ve kod örnekleri dahil.
keywords:
- get diagram page count
- extract text statistics diagrams
- GroupDocs.Metadata Java setup
- Java diagram metadata extraction
title: GroupDocs.Metadata for Java ile Diyagram Sayfa Sayısını Al
type: docs
url: /tr/java/diagram-formats/extract-text-statistics-diagrams-groupdocs-metadata-java/
weight: 1
---

# GroupDocs.Metadata for Java kullanarak Diyagram Sayfa Sayısını Alın

Modern yazılım projelerinde, **diyagram sayfa sayısını** hızlı bir şekilde alabilmek çok zaman tasarrufu sağlar—özellikle raporlar oluşturmanız veya belgeleme hatlarını otomatikleştirmeniz gerektiğinde. Bu öğreticide, VDX, VSDX ve daha fazlası gibi diyagram dosyalarından sayfa sayısını ve diğer faydalı metin istatistiklerini çekmek için GroupDocs.Metadata for Java'nın nasıl kullanılacağını adım adım gösteriyoruz.

## Hızlı Yanıtlar
- **“diyagram sayfa sayısını al” ne anlama geliyor?** Bir diyagram dosyasındaki toplam sayfa (veya sayfa) sayısını döndürür.  
- **Bu özelliği hangi kütüphane sağlıyor?** GroupDocs.Metadata for Java.  
- **Lisans gerekli mi?** Değerlendirme için ücretsiz deneme çalışır; üretim için kalıcı lisans gereklidir.  
- **Hangi Java sürümü gerekiyor?** JDK 8 veya üzeri.  
- **Bir döngü içinde birden fazla diyagramı işleyebilir miyim?** Evet—döngünüzde her dosya için `Metadata` nesnesi oluşturmanız yeterlidir.

## “diyagram sayfa sayısını al” nedir?
Diyagram sayfa sayısını almak, dosyanın içinde kaç ayrı sayfa veya kanvas bulunduğunu öğrenmek için diyagramın meta verilerini sorgulamak anlamına gelir. Bu bilgi, GroupDocs.Metadata'nin sunduğu belge istatistiklerinin bir parçasıdır.

## Neden GroupDocs.Metadata for Java kullanmalı?
- **Hızlı, hafif çıkarım** – Tüm diyagramı render etmenize gerek yok.  
- **Geniş format desteği** – VDX, VSDX ve birçok diğer diyagram türüyle çalışır.  
- **Basit API** – Birkaç satır kodla sayfa sayısı, yazar, oluşturma tarihi ve daha fazlasını elde edersiniz.  

## Ön Koşullar
- **GroupDocs.Metadata for Java** (sürüm 24.12 veya daha yenisi).  
- **JDK 8+** makinenizde kurulu.  
- IntelliJ IDEA veya Eclipse gibi bir IDE.  
- Bağımlılık yönetimi için Maven.  

## GroupDocs.Metadata for Java Kurulumu

### Maven Kullanarak
Aşağıda gösterildiği gibi `pom.xml` dosyanıza depo ve bağımlılığı tam olarak ekleyin:

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
Maven kullanmak istemiyorsanız, resmi sürüm sayfasından en son JAR dosyasını alın: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Lisans Edinme
- **Ücretsiz Deneme** – Tüm özellikleri ücretsiz olarak indirin ve keşfedin.  
- **Geçici Lisans** – Sınırsız test için geçici bir anahtar isteyin.  
- **Tam Lisans** – Sınırsız üretim kullanımı için satın alın.

## Temel Başlatma
Aşağıda bir diyagram dosyasıyla çalışmaya başlamak için gereken en az kod örneği verilmiştir. Bu snippet **Metadata nesnesini başlatır**, ki bu nesne sayfa sayısını almayı da içeren tüm sonraki işlemler için giriş noktasıdır.

```java
import com.groupdocs.metadata.Metadata;

public class DiagramInitialization {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/input.vdx";
        try (Metadata metadata = new Metadata(inputPath)) {
            System.out.println("GroupDocs.Metadata initialized successfully.");
        }
    }
}
```

## GroupDocs.Metadata Java ile Diyagram İstatistiklerini Okuma
Kütüphane hazır olduğuna göre, sayfa sayısını ve diğer istatistikleri elde etmek için tam adımları inceleyelim.

### Adım 1: Kök Paketi Alın
Her diyagram tipinin meta verilerine erişim sağlayan belirli bir kök paketi vardır. Genel `getRootPackageGeneric()` metodunu kullanarak bunu alın.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.DiagramRootPackage;

public class DiagramReadDocumentStatistics {
    public static void main(String[] args) {
        String inputPath = "YOUR_DOCUMENT_DIRECTORY/input.vdx";
        
        try (Metadata metadata = new Metadata(inputPath)) {
            // Obtain the root package for the diagram document type
            DiagramRootPackage root = metadata.getRootPackageGeneric();
```

### Adım 2: Belge İstatistiklerine Erişin (Diyagram Sayfa Sayısını Al)
Kök paket elinizdeyken, `getDocumentStatistics()` ardından `getPageCount()` metodunu çağırarak **diyagram sayfa sayısını** alabilirsiniz.

```java
            int pageCount = root.getDocumentStatistics().getPageCount();
            System.out.println("Page Count: " + pageCount);
        }
    }
}
```

**Açıklama**: `getDocumentStatistics()` birkaç faydalı metriği tutan bir nesne döndürür; bunlar arasında sayfa sayısı da vardır. `pageCount` değişkeni bu nedenle diyagramdaki toplam sayfayı temsil eder.

### Adım 3: İstisnaları Zarifçe Ele Alın
Dosya ile ilgili işlemler birçok nedenden (dosya eksik, desteklenmeyen format vb.) başarısız olabilir. Açık hata mesajları göstermek için kodunuzu bir try‑catch bloğuna sarın.

```java
        } catch (Exception e) {
            System.err.println("Error occurred while processing diagram metadata: " + e.getMessage());
        }
    }
}
```

## Pratik Uygulamalar

| Kullanım Durumu | Sayfa Sayısının Sağladığı Fayda |
|-----------------|---------------------------------|
| **Proje Yönetimi** | Akış şemaları veya mimari diyagramlarda sayfa sayısını sayarak çabayı hızlıca tahmin edin. |
| **Otomatik Raporlama** | Paydaş incelemeleri için her diyagramı ve sayfa sayısını listeleyen özet tablolar oluşturun. |
| **Veri Analitiği** | Zaman içinde belge büyümesini izlemek için sayfa‑sayısı metriklerini panellere besleyin. |

## Performans Düşünceleri
- **Kaynak Yönetimi**: `Metadata` nesnesini otomatik olarak kapatmak ve belleği serbest bırakmak için Java’nın try‑with‑resources (gösterildiği gibi) kullanın.  
- **Toplu İşleme**: Çok sayıda diyagram işlerken, dosya başına tek bir `Metadata` örneği yeniden kullanın ve gereksiz veri yüklemesinden kaçının.  

## Yaygın Sorunlar ve Çözümleri
- **Dosya bulunamadı** – `inputPath` değerini iki kez kontrol edin ve dosyanın diskte mevcut olduğundan emin olun.  
- **Desteklenmeyen format** – Diyagram tipinizin (ör. VDX) kullandığınız sürümde desteklenen formatlar listesinde olduğundan emin olun.  
- **Lisans hatası** – `Metadata` nesnesi oluşturulmadan önce geçerli bir deneme veya tam lisans anahtarının uygulandığını doğrulayın.  

## Sık Sorulan Sorular

**S:** GroupDocs.Metadata tarafından diagramlar için hangi dosya formatları destekleniyor?  
**C:** VDX, VSDX ve kurumsal ortamlarda kullanılan birçok diğer yaygın diyagram formatını destekler.

**S:** GroupDocs.Metadata'ı diyagram dışı belgelerle kullanabilir miyim?  
**C:** Evet, kütüphane PDF, Word dosyaları, elektronik tablolar ve daha fazlası ile çalışır ve birleşik bir meta veri çıkarma deneyimi sunar.

**S:** Desteklenmeyen dosya formatlarıyla nasıl başa çıkabilirim?  
**C:** Dosyanın uzantısını belgelerdeki desteklenen listesiyle karşılaştırın. Bilinmeyen formatlar için önce desteklenen bir tipe dönüştürmeyi düşünün.

**S:** Aynı anda işleyebileceğim diyagram sayısında bir limit var mı?  
**C:** Katı bir limit yoktur, ancak çok büyük bir toplu işlem bellek kullanımı ve çoklu iş parçacığı stratejilerine dikkat gerektirebilir.

**S:** Başlatma hatası alırsam ne yapmalıyım?  
**C:** Dosya yolunu iki kez kontrol edin, JAR dosyalarının sınıf yolunuza doğru eklendiğinden emin olun ve geçerli bir lisans (deneme dahil) uygulandığını doğrulayın.

## Sonraki Adımlar
- Yazar, oluşturma tarihi ve özel özellikler gibi ek istatistikleri keşfedin.  
- Sayfa‑sayısı mantığını dosya sistemi taramasıyla birleştirerek tüm diyagram klasörlerini işleyin.  
- Daha derin özelleştirme seçenekleri için resmi API referansına göz atın.

## Kaynaklar
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License Application](https://purchase.groupdocs.com/temporary-license/) 

---

**Son Güncelleme:** 2026-03-20  
**Test Edilen Versiyon:** GroupDocs.Metadata 24.12 for Java  
**Yazar:** GroupDocs