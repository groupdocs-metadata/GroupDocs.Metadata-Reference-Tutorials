---
date: '2026-06-22'
description: Ismerje meg, hogyan olvassa a SevenZip metaadatokat Java-ban a GroupDocs.Metadata
  for Java segítségével, beleértve a compressed size Java és egyéb archive properties
  lekérését.
keywords:
- read sevenzip metadata java
- get compressed size java
- GroupDocs.Metadata Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  headline: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  name: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  steps:
  - name: Initialize Metadata Object
    text: The `Metadata` class represents the entry point for loading and interacting
      with archive files.
  - name: Obtain the Root Package
    text: The `getRootPackageGeneric()` method returns a generic view of the archive's
      root package, allowing you to work with entries without needing format‑specific
      code. - **Why Use `getRootPackageGeneric()`?** It provides a generalized view
      of the archive's contents, making it easier to iterate over its e
  - name: Iterate Over Archive Entries
    text: The `SevenZipPackage` class represents the SevenZip container, and each
      entry is exposed as a `SevenZipFileInfo` object. The `SevenZipFileInfo` class
      provides direct access to properties like name, compressed size, and modification
      date. - **Why Extract These Properties?** Knowing file sizes helps m
  - name: Clean Up Resources
    text: Calling `close()` on the `Metadata` instance releases native resources and
      avoids memory leaks in long‑running services. - **Why Dispose?** Properly disposing
      of objects helps prevent memory leaks in long‑running applications.
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java – a single‑API solution for over 70 archive
      and document formats.
    question: What library should I use?
  - answer: Yes – call `getSevenZipPackage().getFiles()` after initializing the `Metadata`
      object.
    question: Can I list files inside a SevenZip archive?
  - answer: A free trial works for evaluation; a full license is required for production.
    question: Do I need a license?
  - answer: JDK 8 or higher (compatible with Java 17 LTS).
    question: Which Java version is supported?
  - answer: Not mandatory, but Maven handles transitive dependencies automatically.
    question: Is Maven required?
  type: FAQPage
title: Hogyan olvassuk a SevenZip metaadatokat Java-ban a GroupDocs.Metadata használatával
type: docs
url: /hu/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# Hogyan olvassuk a SevenZip metaadatokat Java-ban a GroupDocs.Metadata segítségével

## Bevezetés

Küzdesz a metaadat-tulajdonságok elérésével és olvasásával a SevenZip archívumfájlokból Java használatával? Ez az útmutató végigvezet a **GroupDocs.Metadata** használatának folyamatán. Ez a hatékony könyvtár leegyszerűsíti a fontos információk, például fájlnevek, méretek és módosítási dátumok közvetlen kinyerését az archívumokból.

## Gyors válaszok
- **Milyen könyvtárat használjak?** GroupDocs.Metadata for Java – egy egyetlen‑API megoldás több mint 70 archívum- és dokumentumformátumhoz.  
- **Listázhatok fájlokat egy SevenZip archívumban?** Igen – hívd a `getSevenZipPackage().getFiles()` metódust a `Metadata` objektum inicializálása után.  
- **Szükségem van licencre?** Egy ingyenes próba a kiértékeléshez elegendő; a teljes licenc a termeléshez kötelező.  
- **Melyik Java verzió támogatott?** JDK 8 vagy újabb (kompatibilis a Java 17 LTS‑sel).  
- **Kell Maven?** Nem kötelező, de a Maven automatikusan kezeli a tranzitív függőségeket.

## Mi az a „how to read sevenzip” Java-ban?

A SevenZip metaadatok olvasása azt jelenti, hogy megnyitod a `.7z` konténert, felsorod minden bejegyzést, és kinyered a **compressed size**, **uncompressed size**, **file name** és **modification date** tulajdonságokat anélkül, hogy a tényleges fájlokat kibontanád. Ez a folyamat betekintést nyújt az archívum felépítésébe, lehetővé teszi a biztonsági mentés integritásának ellenőrzését, és segít a tárolókapacitás döntéseinek meghozatalában a teljes kibontás terhe nélkül.

## read sevenzip metadata java

A fő kulcsszó dedikált címsorban való használata segít az olvasóknak és a keresőmotoroknak egyaránt megérteni az útmutató fókuszát. Az alábbiakban részletesen bemutatjuk a **read sevenzip metadata java** hatékony elvégzéséhez szükséges lépéseket.

## Miért használjuk a GroupDocs.Metadata Java-t metaadatok kinyeréséhez?

A GroupDocs.Metadata csak a metaadatok kinyeréséhez szükséges fejlécinformációkat olvassa, így a művelet akár több gigabájtos archívumok esetén is ezredmásodpercek alatt befejeződik. Több mint **70+** archívum- és dokumentumformátumot támogat, akár **2 GB** méretű archívumokat is feldolgoz anélkül, hogy a teljes fájlt a memóriába töltené, és egységes API‑t biztosít minden támogatott típushoz.

## Előfeltételek

Mielőtt elkezdenéd a **GroupDocs.Metadata for Java** használatát, győződj meg róla, hogy a fejlesztői környezet megfelelően be van állítva. Szükséged lesz a következőkre:

- **Java Development Kit (JDK):** 8-as vagy újabb verzió.  
- **Maven:** Ajánlott a függőségek kezeléséhez, bár a JAR‑t manuálisan is hozzáadhatod.  
- **Alap Java ismeretek:** Osztályok, metódusok és kivételkezelés ismerete.

## A GroupDocs.Metadata beállítása Java-hoz

A GroupDocs.Metadata használatához add hozzá a projektedhez Maven‑en keresztül vagy töltsd le a könyvtárat közvetlenül.

### Maven használata

Add hozzá a következő konfigurációt a `pom.xml` fájlodhoz:

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

Alternatívaként töltsd le a legújabb verziót a [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) oldalról.

#### Licenc beszerzése

1. **Free Trial:** Kezd egy ingyenes próbával, hogy teszteld a GroupDocs.Metadata képességeit.  
2. **Temporary License:** Kérj ideiglenes licencet, ha hosszabb kiértékelési időre van szükséged.  
3. **Purchase:** Hosszú távú használathoz fontold meg a teljes licenc megvásárlását.  

A beállítások után lépjünk tovább a metaadat‑olvasási funkció megvalósítására.

## Implementációs útmutató

### Metaadatok elérése SevenZip archívumokból

Ebben a részben metaadat‑tulajdonságokat, például fájlneveket és méreteket nyerünk ki és jelenítünk meg egy SevenZip archívumból.

#### 1. lépés: Metadata objektum inicializálása

A `Metadata` osztály jelenti a belépési pontot az archívumfájlok betöltéséhez és kezeléséhez.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### 2. lépés: Gyökércsomag lekérése

A `getRootPackageGeneric()` metódus egy általános nézetet ad az archívum gyökércsomagjáról, lehetővé téve a bejegyzések kezelését formátum‑specifikus kód nélkül.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Miért használjuk a `getRootPackageGeneric()`‑t?** Általános nézetet biztosít az archívum tartalmáról, így könnyebb a bejegyzéseken iterálni anélkül, hogy a konkrét fájlformátumokkal kellene foglalkozni.

#### 3. lépés: Archívum bejegyzéseinek iterálása

A `SevenZipPackage` osztály képviseli a SevenZip konténert, és minden bejegyzés egy `SevenZipFileInfo` objektumként jelenik meg. A `SevenZipFileInfo` közvetlen hozzáférést biztosít olyan tulajdonságokhoz, mint a név, a tömörített méret és a módosítási dátum.

```java
int totalEntries = root.getSevenZipPackage().getTotalEntries();

for (SevenZipFile file : root.getSevenZipPackage().getFiles()) {
    String name = file.getName();
    long compressedSize = file.getCompressedSize();
    java.util.Date modificationDateTime = file.getModificationDateTime();
    long uncompressedSize = file.getUncompressedSize();

    // Output metadata properties for each file in the archive
    System.out.println("File Name: " + name);
    System.out.println("Compressed Size: " + compressedSize);
    System.out.println("Modification Date and Time: " + modificationDateTime);
    System.out.println("Uncompressed Size: " + uncompressedSize);
}
```

- **Miért nyerjük ki ezeket a tulajdonságokat?** A fájlméretek ismerete segít a tárolókapacitás kezelésében, míg a módosítási dátum kulcsfontosságú lehet a szinkronizációs feladatoknál. A `getCompressedSize()` hívás a Java módja a **get compressed size java** lekérésének minden egyes bejegyzésnél.

#### 4. lépés: Erőforrások felszabadítása

A `Metadata` példányon a `close()` meghívása felszabadítja a natív erőforrásokat és elkerüli a memória‑szivárgásokat hosszú‑távú szolgáltatásokban.

```java
} finally {
    metadata.dispose();
}
```

- **Miért kell felszabadítani?** Az objektumok megfelelő lezárása segít megelőzni a memória‑szivárgásokat hosszú‑távú alkalmazásokban.

## Hogyan nyerjünk ki metaadatokat hatékonyan?

Töltsd be a SevenZip archívumot egyetlen `Metadata` példány segítségével, hívd egyszer a `getRootPackageGeneric()`‑t, majd egy `for‑each` ciklussal streameld végig a bejegyzéseket. Ez a minta elkerüli az ismételt I/O‑t, csökkenti a GC‑nyomást, és O(n) időben befejeződik, ahol *n* a bejegyzések száma.

## Gyakorlati alkalmazások

A **read sevenzip metadata java** ismerete számos valós előnnyel jár:

1. **Adatbiztonsági mentés kezelése:** Gyorsan ellenőrizheted a mentési archívumok integritását és teljességét.  
2. **Fájl‑szinkronizációs eszközök:** A módosítási dátumok alapján döntheted el, mely fájlok igényelnek frissítést.  
3. **Tárolóoptimalizálás:** A tömörített és tömörítetlen méretek összehasonlításával tervezheted a kapacitást.  

Az integráció más rendszerekkel is lehetséges, így automatizálható a metaadat‑kinyerés a nagyobb adatkezelési munkafolyamatok részeként.

## Teljesítmény szempontok

Nagy archívumok esetén a GroupDocs.Metadata használatakor tartsd szem előtt a következő tippeket:

- **Kötegelt feldolgozás:** A fájlokat kötegekben dolgozd fel a memóriahatékony kezelés érdekében.  
- **Hatékony kivételkezelés:** Használj try‑with‑resources‑t az automatikus erőforrás‑kezeléshez.  
- **Aszinkron feldolgozás:** Implementálj aszinkron technikákat a nehéz munkaterhekhez.  

## Gyakori problémák és megoldások

| Probléma | Megoldás |
|----------|----------|
| **`NullPointerException` when accessing a file** | Ellenőrizd, hogy az archívum útvonala helyes-e, és a fájl nem sérült. |
| **Memory spikes on huge archives** | Engedélyezd a kötegelt feldolgozást vagy növeld a JVM heap méretét (`-Xmx`). |
| **License not recognized** | Győződj meg róla, hogy a licencfájl az alkalmazás munkakönyvtárában van, vagy állítsd be a `License.setLicense(path)` metódussal. |

## Gyakran feltett kérdések

**Q:** Mi a GroupDocs.Metadata?  
**A:** Egy Java könyvtár, amely különböző fájlformátumok metaadataival foglalkozik, beleértve a SevenZip archívumokat is.

**Q:** Használhatom a GroupDocs.Metadata‑t Maven nélkül?  
**A:** Igen, letöltheted a JAR‑t a hivatalos oldalról, és hozzáadhatod a projekt classpath‑jához.

**Q:** Hogyan kezeljem a nagy archívumokat hatékonyan?  
**A:** Alkalmazz kötegelt feldolgozást vagy aszinkron stream‑eket a memóriafogyasztás korlátozása érdekében.

**Q:** Hol találok részletesebb útmutatót?  
**A:** Lásd a [official documentation](https://docs.groupdocs.com/metadata/java/) oldalt a teljes API‑referenciáért.

**Q:** Mit tegyek, ha problémám adódik a könyvtárral?  
**A:** Kérdezz a közösségtől a [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) fórumon.

## Erőforrások

- **Dokumentáció:** Explore more at [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **Official documentation:** [official documentation](https://docs.groupdocs.com/metadata/java/)  
- **API Reference:** Check detailed API information at [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Download:** Get the latest version from [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/)  
- **GitHub Repository:** Access code samples on [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Free Support Forum:** Join discussions or ask questions at [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**Utolsó frissítés:** 2026-06-22  
**Tesztelve a következővel:** GroupDocs.Metadata 24.12 for Java  
**Szerző:** GroupDocs

## Kapcsolódó útmutatók

- [How to Read TAR Files and Extract Metadata with GroupDocs.Metadata for Java](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)
- [Update ZIP Comment Java – How to Update ZIP Archive Comments Using GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [Extract Video Metadata Java: How to Read AVI Files with GroupDocs.Metadata](/metadata/java/audio-video-formats/extract-avi-metadata-groupdocs-metadata-java/)