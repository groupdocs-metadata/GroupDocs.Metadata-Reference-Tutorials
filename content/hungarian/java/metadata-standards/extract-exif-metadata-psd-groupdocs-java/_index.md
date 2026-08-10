---
date: '2026-08-10'
description: Ismerje meg, hogyan lehet EXIF metaadatokat kinyerni PSD fájlokból a
  GroupDocs.Metadata for Java használatával. Ez az útmutató bemutatja az alapvető
  kinyerést, az IFD csomagokat, a GPS adatokat és a gyakorlati példákat.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Ismerje meg, hogyan lehet EXIF metaadatokat kinyerni PSD fájlokból
  a GroupDocs.Metadata for Java használatával. Lépésről‑lépésre útmutató, kódrészletek
  és hibaelhárítási tippek fejlesztőknek.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Hogyan lehet EXIF metaadatokat kinyerni PSD fájlokból a GroupDocs.Metadata
  segítségével
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
title: Hogyan lehet EXIF metaadatokat kinyerni PSD fájlokból a GroupDocs.Metadata
  segítségével
type: docs
url: /hu/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Hogyan lehet EXIF metaadatokat kinyerni PSD fájlokból a GroupDocs.Metadata segítségével

Az **EXIF metaadatok** kinyerése PSD fájlokból egy rutinszerű, de hatékony lépés, amikor a képek eredetét kell ellenőrizni, az eszközök címkézését automatizálni vagy kereshető média könyvtárakat építeni. Ebben az útmutatóban gyorsan felfedezheti, **hogyan kell EXIF-et kinyerni** a GroupDocs.Metadata for Java segítségével, megtekintheti a pontos API hívásokat, és megtanulhatja, hogyan kezelje a fejlett IFD csomagokat és a GPS koordinátákat. A végére készen áll majd a metaadatok kinyerésének integrálására bármely Java‑alapú munkafolyamatba.

## Gyors válaszok
A `Metadata` osztály egy fájlt képvisel, és hozzáférést biztosít a metaadataihoz.

- **Mi a kódsor első sora?** `Metadata metadata = new Metadata("sample.psd");`
- **Melyik metódus adja vissza a művész nevét?** `metadata.getExif().getArtist();`
- **Olvashatok GPS adatokat?** Igen – használja a `metadata.getExif().getGpsInfo();`
- **Szükségem van licencre a termeléshez?** Érvényes GroupDocs.Metadata licenc szükséges a próbaidőszak után.
- **Támogatott Java verzió?** Java 8 vagy újabb (akár Java 21-ig).

## Mi az EXIF metaadat?
Az EXIF (Exchangeable Image File Format) metaadatok a fényképezőgép beállításait, a létrehozás időbélyegét és a helyadatokat tárolják a képfájlokban. A GroupDocs.Metadata ezt az információt közvetlenül a PSD fájlok bináris struktúrájából olvassa ki, és egy tiszta Java API-n keresztül teszi elérhetővé. Lehetővé teszi a fejlesztők számára, hogy programozottan lekérjék a részleteket, például a fényképezőgép modelljét, az expozíciós időt és a GPS koordinátákat manuális ellenőrzés nélkül.

## Miért használjuk a GroupDocs.Metadata-et Java-hoz?
A GroupDocs.Metadata **30+ fájlformátumot** támogat (beleértve a PSD, JPEG, PNG, TIFF formátumokat) és képes **2 GB**-ig terjedő fájlokat feldolgozni anélkül, hogy a teljes dokumentumot a memóriába töltené. A könyvtár **150+ különböző EXIF címkét** nyer ki, biztosítva, hogy rendelkezzen a teljes kamera- és GPS attribútumkészlettel, amely az elemzésekhez vagy a megfelelőséghez szükséges.

## Előfeltételek
- **Java Development Kit (JDK) 8** vagy újabb telepítve a gépén.  
- **Maven** a függőségkezeléshez.  
- **GroupDocs.Metadata for Java 24.12** verzió (vagy újabb).  
- Alapvető ismeretek a Java osztályokról, objektumokról és a kivételkezelésről.

### Szükséges könyvtárak és függőségek
| Függőség | Maven koordináták |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Környezet beállítása
Rendelkeznie kell egy Maven‑kompatibilis IDE-vel, például IntelliJ IDEA vagy Eclipse. Hozzon létre egy új Maven projektet, vagy adja hozzá a függőséget egy meglévőhöz.

## Hogyan állítsuk be a GroupDocs.Metadata-et Java-hoz
A GroupDocs.Metadata néhány konfigurációs sorral hozzáadható egy Maven projekthez. A következő lépések bemutatják, hogyan lehet felvenni a tárolót és a függőséget, hogy a könyvtár elérhető legyen az osztályúton.

### Maven beállítás
Adja hozzá a következő kódrészletet a `pom.xml` fájl `<dependencies>` szakaszába:

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

### Közvetlen letöltés
Alternatívaként töltse le a legújabb JAR-t a hivatalos kiadási oldalról: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Licenc beszerzése
A könyvtár 30‑napos próbaidőszak után történő futtatásához szerezzen be egy ideiglenes vagy teljes licencet:

1. Látogassa meg a [License Purchase Page](https://purchase.groupdocs.com/temporary-license) oldalt.  
2. Válassza a **temporary** (ideiglenes) teszteléshez vagy a **full** (teljes) termeléshez.  
3. Kövesse a képernyőn megjelenő utasításokat a licencfájl (`metadata.lic`) beágyazásához a Java osztályútra.

### Alapvető inicializálás és beállítás
Miután a könyvtár az osztályúton van, inicializálja az alábbiak szerint:

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

## Hogyan nyerjünk ki alapvető EXIF metaadat tulajdonságokat egy PSD képből
Ez a szakasz bemutatja, hogyan töltsünk be egy PSD fájlt, érjünk hozzá az EXIF tárolóhoz, és olvassuk el a leggyakoribb címkéket, például a **artist**, **copyright**, és **software** címkéket. A folyamat magában foglalja egy `Metadata` példány létrehozását, a `getExif()` meghívását, majd az egyes tulajdonságok egyszerű getter metódusokkal történő lekérését.

### Lépésről‑lépésre megvalósítás
1. **Hozzon létre egy `Metadata` példányt**, amely a PSD fájlra mutat.  
2. **Hívja meg a `getExif()`-t**, hogy megkapja az EXIF tárolót.  
3. **Olvassa el az egyes tulajdonságokat**, például a `getArtist()`, `getCopyright()`, és `getSoftware()`.  
4. **Nyomtassa vagy tárolja** az értékeket az alkalmazás logikája szerint.

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

> **Pro tip:** A `Metadata` objektum automatikusan felismeri a fájlformátumot, így ugyanazt a kódot újra felhasználhatja JPEG vagy TIFF fájlokhoz módosítás nélkül.

## Hogyan nyerjünk ki EXIF IFD csomag tulajdonságokat egy PSD képből
Az IFD (Image File Directory) szakasz mélyebb technikai részleteket tartalmaz, például **camera serial number**, **lens model**, és **user comments**. Az `Ifd0` a fő Image File Directory-t jelenti, amely alapvető kamera információkat tartalmaz. Ezeknek a mezőknek a kinyerése hasznos a forenzikus elemzéshez vagy a nagy pontosságú katalógushoz.

### Implementációs lépések
1. **Használja újra a `Metadata` példányt** az előző szakaszból.  
2. **Navigáljon az IFD tárolóhoz** a `metadata.getExif().getIfd0()` segítségével.  
3. **Olvassa el a tulajdonságokat**, például a `getBodySerialNumber()` és a `getUserComment()`.  
4. **Adja ki az adatokat** vagy térképezze őket a domain modelljére.

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

## Hogyan nyerjünk ki GPS adatokat (szélesség, hosszúság) egy PSD fájlból
Sok modern fényképezőgép beágyazza a GPS koordinátákat az EXIF blokkba. A `GpsInfo` a EXIF adatokból kinyert földrajzi koordinátákat tárolja. Hívja meg a `metadata.getExif().getGpsInfo()`-t, majd használja a `getLatitude()`, `getLongitude()`, és `getAltitude()` metódusokat a pontos helyadatok megszerzéséhez – további feldolgozás nem szükséges.

### Részletes lépések
1. **Szerezze be a GPS információs objektumot**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Olvassa el a szélességet és hosszúságot**: `gps.getLatitude()` egy `double` típusú értéket ad vissza decimális fokokban.  
3. **Hiányzó adatok kezelése**: Az API `null`-t ad vissza, ha a címke hiányzik, ezért óvakodjon a `NullPointerException`-től.

> **Common pitfall:** Néhány PSD fájl racionális számokként tárolja a GPS koordinátákat; a könyvtár automatikusan normalizálja őket, de a régebbi fájlok esetén manuális konverzióra lehet szükség.

## Gyakori problémák és hibaelhárítás
| Tünet | Valószínű ok | Megoldás |
|---------|--------------|-----|
| `Unsupported format` kivétel | Régebbi GroupDocs.Metadata verzió használata, amely nem ismeri fel a PSD-t | Frissítsen a 24.12 vagy újabb verzióra |
| `NullPointerException` a `getArtist()` hívásakor | Az EXIF címke nem található a forrásfájlban | Ellenőrizze a `metadata.getExif().hasArtist()`-t a beolvasás előtt |
| Licenc hiba 30 nap után | A licencfájl nem található az osztályúton | Helyezze a `metadata.lic`-et a `src/main/resources` könyvtárba vagy állítsa be a `Metadata.setLicense("path/to/license")`-t |

## Gyakran ismételt kérdések

**Q:** Kinyerhetek EXIF metaadatokat egy jelszóval védett PSD fájlból?  
**A:** Igen. Töltse be a fájlt a `new Metadata("file.psd", "password")` segítségével, majd a szokásos módon férjen hozzá az EXIF adatokhoz.

**Q:** A GroupDocs.Metadata támogatja a több PSD fájl kötegelt feldolgozását?  
**A:** Teljes mértékben. Hozzon létre egy `Metadata` objektumot egy cikluson belül, vagy használja a `MetadataCollection` segédeszközt a könyvtárak hatékony feldolgozásához.

**Q:** Mely Java verziók vannak hivatalosan támogatva?  
**A:** A Java 8-tól a Java 21-ig teljesen tesztelt. A könyvtár csak standard API-kat használ, így bármely kompatibilis JVM-en működik.

**Q:** Lehetséges az EXIF adatokat visszaírni egy PSD fájlba?  
**A:** Igen. A `Exif` objektumon keresztül módosított tulajdonságok után hívja meg a `metadata.save("output.psd")`-t a változások mentéséhez.

**Q:** Mekkora PSD fájlt képes a könyvtár kezelni memóriahiány nélkül?  
**A:** A GroupDocs.Metadata adatfolyamot használ, és tipikus 8 GB RAM-os gépen akár **2 GB**-ig terjedő fájlokat is képes feldolgozni alacsony memóriaigénye miatt.

## Következtetés
Most már tudja, **hogyan kell EXIF** metaadatokat kinyerni PSD fájlokból a GroupDocs.Metadata for Java segítségével, az alapvető címkéktől a fejlett IFD és GPS információkig. Integrálja ezeket a kódrészleteket a képfeldolgozó csővezetékébe az automatikus katalogizálás, a megfelelőségi ellenőrzések vagy a helyalapú szolgáltatások érdekében. Mélyebb felfedezéshez próbáljon metaadatokat kinyerni más támogatott formátumokból (JPEG, TIFF, PNG), vagy kísérletezzen a visszaírási lehetőségekkel egyedi címkék beágyazásához.

---

**Utoljára frissítve:** 2026-08-10  
**Tesztelt verzió:** GroupDocs.Metadata 24.12 for Java  
**Szerző:** GroupDocs

## Kapcsolódó útmutatók

- [Képerőforrások kinyerése PSD fájlokból a GroupDocs.Metadata használatával Java-ban: Átfogó útmutató](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [PSD fejléc és réteg információk kinyerése a GroupDocs.Metadata for Java használatával: Átfogó útmutató](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [MakerNote tulajdonságok kinyerése TIFF/EXIF címkékként a GroupDocs.Metadata Java használatával](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)