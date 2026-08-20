---
date: '2026-08-20'
description: Ismerje meg, hogyan nyerhet ki XMP metaadatokat Java-ban a GroupDocs.Metadata
  használatával. Ez az útmutató bemutatja, hogyan nyerhet ki alap, Dublin Core és
  Photoshop XMP metaadatokat.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Ismerje meg, hogyan nyerhet ki XMP metaadatokat Java-ban a GroupDocs.Metadata
  használatával. Ez a bemutató alap, Dublin Core és Photoshop XMP kinyerést fed le
  gyakorlati kódrészletekkel.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Hogyan nyerhet ki XMP metaadatokat a GroupDocs.Metadata használatával Java-ban
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
title: Hogyan nyerhet ki XMP metaadatokat a GroupDocs.Metadata használatával Java-ban
type: docs
url: /hu/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan lehet XMP metaadatokat kinyerni a GroupDocs.Metadata for Java segítségével

A modern digitális munkafolyamatokban az **XMP metaadatok** gyors és megbízható kinyerése döntő lehet egy kereshető eszközkönyvtár és egy kaotikus fájlhalom között. Ez az útmutató végigvezet minden lépésen – a könyvtár beállításán, a fájlok betöltésén és az alap, Dublin Core és Photoshop‑specifikus XMP csomagok kinyerésén – hogy ma már be tudja integrálni a gazdag metaadatokat Java alkalmazásaiba.

## Gyors válaszok
- **Melyik könyvtár kezeli az XMP-t Java-ban?** GroupDocs.Metadata for Java.
- **Minimum Java verzió?** JDK 8 vagy újabb.
- **Olvashatok PNG és JPEG fájlokat?** Igen, mindkettő alapból támogatott.
- **Szükséges licenc a termeléshez?** Igen, teljes vagy ideiglenes licenc szükséges.
- **Hol találom az API referencia?** A hivatalos GroupDocs.Metadata dokumentációs oldalon.

## Mi az XMP metaadat?
Az XMP (Extensible Metadata Platform) egy ISO‑standard formátum a strukturált metaadatok közvetlenül a médiafájlokba ágyazására. Lehetővé teszi a különböző alkalmazások közötti interoperabilitást és a tartós adat tárolást anélkül, hogy módosítaná az eredeti tartalmat. Az olyan információk, mint a szerző, a szerzői jog, a kamera beállításai és az egyedi címkék tárolásával a fájlban, az XMP biztosítja, hogy a metaadatok az eszközzel együtt utaznak, egyszerűsítve a katalogizálást és a keresést különböző rendszerek között.

## Miért használjuk a GroupDocs.Metadata for Java-t?
A GroupDocs.Metadata **30+ fájlformátumot** támogat (beleértve a PNG, JPEG, TIFF és PSD formátumokat), és képes **2 GB**-ig terjedő fájlok feldolgozására anélkül, hogy a teljes dokumentumot a memóriába töltené, így **30 % CPU használatcsökkenést** ér el az általános elemzőkhöz képest. Ez ideálissá teszi nagy léptékű digitális eszközkezelő (DAM) rendszerekhez.

## Előfeltételek
- **Java Development Kit (JDK) 8+** telepítve.
- **Maven** a függőségkezeléshez.
- Alapvető ismeretek a Java I/O-val és az objektum‑orientált programozással.

## Hogyan állítsuk be a GroupDocs.Metadata for Java-t?
A kezdéshez adja hozzá a GroupDocs tárolót és a könyvtár függőségét a Maven `pom.xml` fájlhoz. Ez biztosítja, hogy a Maven fel tudja oldani a csomagokat és automatikusan naprakészen tartsa őket, ami egyszerűsíti a jövőbeni frissítéseket és biztonsági javításokat. A `pom.xml` frissítése után futtassa a `mvn clean install` parancsot a szükséges JAR-ok letöltéséhez és a beállítás sikerességének ellenőrzéséhez.

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

Ha manuális megközelítést részesít előnyben, töltse le a legújabb JAR-t a hivatalos kiadási oldalról:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Licenc beszerzése
- **Ingyenes próba** – minden funkció kipróbálása 30 napig.
- **Ideiglenes licenc** – fejlesztés során korlátozás nélkül használható.
- **Teljes licenc** – szükséges a termelési környezetben.

## Alapvető inicializálás

`Metadata` az összes művelet belépési pontja. Egyetlen fájlt képvisel, és hozzáférést biztosít a beágyazott XMP csomagokhoz.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Hogyan nyerjünk ki alap XMP metaadatokat?

Töltse be a képet, nyissa meg az XMP csomagját, és olvassa ki a gyakori tulajdonságokat, például a szerzőeszközt és az időbélyegeket.

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
       // Use the extracted properties as needed
   }
   ```
```

## Hogyan nyerjünk ki Dublin Core XMP metaadatokat?

A Dublin Core séma szabványos leíró elemeket tárol, mint például a cím, a szerző és a tárgy. Ehhez a `DublinCorePackage` osztályon keresztül férhet hozzá.

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
       // Use the extracted properties as needed
   }
   ```
```

## Hogyan nyerjünk ki Photoshop‑specifikus XMP metaadatokat?

A Photoshop további információkat ágyaz be, például a színmódot, a felbontást és a rétegszámot. Ezeket az értékeket a `PhotoshopPackage` segítségével érheti el.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Gyakorlati alkalmazások
- **Digitális eszközkezelés** – címkézze és keresse a képeket szerző, szerzői jog vagy kamera beállítások alapján.
- **Automatizált kiadási folyamatok** – injektálja vagy módosítsa az XMP-t a webgalériákba való közzététel előtt.
- **Elemzés** – aggregálja a metaadatokat több ezer fájlban, hogy felfedezze a használati trendeket.

## Teljesítménybeli szempontok
A `Metadata` osztály hozzáférést biztosít egy fájl metaadataihoz és XMP csomagjaihoz. A `Metadata` objektumokat a beolvasás befejezése után azonnal szabadítsa fel a natív erőforrások felszabadításához. A `LoadOptions.LAZY` azt mondja a könyvtárnak, hogy lazán töltse be a metaadatokat, csökkentve a memóriahasználatot. Nagy fájlok esetén használja a `Metadata.load(InputStream)` streaminget a heap használat alacsonyan tartásához. Egyetlen `Metadata` példány újrahasználata sok kis fájl olvasásakor csökkenti az objektum‑létrehozási költséget.

## Gyakori buktatók és hibaelhárítás

| Tünet | Valószínű ok | Megoldás |
|---|---|---|
| `NullPointerException` XMP elérésekor | A fájlnak nincs XMP csomagja | Hívja meg a `metadata.getXmpPackage()` metódust, és olvasás előtt ellenőrizze, hogy `null`-e. A `getXmpPackage()` metódus visszaadja az XMP csomag objektumát, vagy `null`-t, ha nincs. |
| Lassú feldolgozás 500 MB-os képeknél | A teljes fájl betöltése a memóriába | Használja a `metadata.load(InputStream)`-t és engedélyezze a `metadata.setLoadOptions(LoadOptions.LAZY)` beállítást. |
| Hiányzó Photoshop mezők | A kép Photoshop réteg információ nélkül lett mentve | Ellenőrizze, hogy a forrásfájl a Photoshopból “Save XMP” opcióval lett-e exportálva. |

## Gyakran feltett kérdések

**Q: Kinyerhetek XMP-t PDF fájlokból?**  
A: Igen, a GroupDocs.Metadata támogatja a PDF XMP csomagokat ugyanazon `Metadata` API-n keresztül.

**Q: Mi történik, ha a fájlformátum nem támogatott?**  
A: A könyvtár `UnsupportedFormatException` kivételt dob; ezt el kell kapni és egy általános kezelőre vissza kell térni.

**Q: Lehet módosítani az XMP metaadatokat és vissza menteni?**  
A: Természetesen. A tulajdonságok módosítása után hívja a `metadata.save("output.png")` metódust a frissítések mentéséhez.

**Q: Működik a könyvtár Androidon?**  
A: A core Java könyvtár kompatibilis az Android API 24+-tel, de be kell vonni a `android`‑specifikus artefaktot.

**Q: Hogyan kezeljem a titkosított képeket?**  
A: Adja meg a dekódoló jelszót a `Metadata` konstruktorban: `new Metadata(filePath, "password")`.

## Következtetés

Most már rendelkezik egy teljes, termelésre kész útmutatóval arról, **hogyan nyerhet ki XMP** metaadatokat a GroupDocs.Metadata for Java segítségével. A fenti lépések követésével gazdagíthatja alkalmazásait kereshető, szabványos metaadatokkal, és feloldhatja a hatékony eszközkezelési lehetőségeket.

## Következő lépések

Mélyedjen el a teljes funkciókészletben a hivatalos dokumentáció áttekintésével, és kísérletezzen más metaadat szabványokkal, például az IPTC-vel és az EXIF-fel.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Utolsó frissítés:** 2026-08-20  
**Tesztelve ezzel:** GroupDocs.Metadata for Java 23.11  
**Szerző:** GroupDocs  

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Kapcsolódó oktatóanyagok

- [Dublin Core metaadatok kinyerése Epub formátumban GroupDocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [EXIF szoftvercímke kinyerése Java-ban: Teljes útmutató a GroupDocs.Metadata használatával](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Hogyan nyerjünk ki metaadatokat a GroupDocs.Metadata for Java segítségével – Oktatóanyagok és példák](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}