---
date: '2026-01-26'
description: Tanulja meg, hogyan olvassa ki a létrehozás időpontját Java-ban, és hogyan
  nyerje ki a PowerPoint-prezentációk egyéb dokumentumtulajdonságait a GroupDocs.Metadata
  for Java segítségével. Ideális dokumentumkezeléshez és megfelelőséghez.
keywords:
- read created time java
- java extract document properties
- presentation metadata
title: Hogyan olvassuk ki a létrehozás időpontját Java‑ban a prezentációs fájlokból
  a GroupDocs.Metadata használatával – Lépésről lépésre útmutató
type: docs
url: /hu/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# Hogyan olvassuk ki a létrehozás időpontját Java-ban prezentációs fájlokból a GroupDocs.Metadata segítségével

A metaadatok kezelése a modern dokumentumfolyamatok alapköve. Ebben az útmutatóban megtanulod, **hogyan olvassuk ki a létrehozás időpontját Java-ban**, és hogyan nyerheted ki a további hasznos tulajdonságokat – például a szerzőt, a céget és a kulcsszavakat – egy PowerPoint‑prezentációból a **GroupDocs.Metadata for Java** használatával. A végére készen állsz arra, hogy ezeket az adatokat beépítsd dokumentumkezelő rendszerekbe, megfelelőségi jelentésekbe vagy bármely Java‑alapú alkalmazásba, amelynek szüksége van a fájl eredetének megismerésére.

## Gyors válaszok
- **Mit jelent a “read created time java”?** Ez a fájl létrehozási időbélyegének Java‑kóddal történő lekérdezését jelenti.  
- **Melyik könyvtár támogatja ezt?** A GroupDocs.Metadata for Java tiszta API‑t biztosít az összes beépített prezentációs tulajdonsághoz.  
- **Szükség van licencre?** Fejlesztéshez egy ingyenes próbaelérhető; a termeléshez állandó licenc szükséges.  
- **Kivonhatok más tulajdonságokat is egyszerre?** Igen – a szerző, a cég, a kategória és még sok más elérhető ugyanazon API‑n keresztül.  
- **Milyen Java‑verzió szükséges?** JDK 8 vagy újabb.

## Mi az a “read created time java”?
A dokumentum létrehozási időpontjának Java‑ban történő olvasása azt jelenti, hogy hozzáférünk a metaadatmezőhöz, amely tárolja, mikor jött létre a fájl. Ez az időbélyeg elengedhetetlen a verziókezeléshez, audit nyomvonalakhoz és a megfelelőség ellenőrzéséhez.

## Miért használjuk a GroupDocs.Metadata for Java‑t a dokumentumtulajdonságok kinyeréséhez?
A GroupDocs.Metadata elrejti a különböző fájlformátumok bonyolultságát, így a vállalati logikára koncentrálhatsz ahelyett, hogy alacsony szintű elemzéssel foglalkoznál. Támogatja a PowerPoint‑ot, PDF‑et, Word‑et és számos képformátumot, így sokoldalú választás minden Java‑projekt számára, amelynek **java extract document properties** megbízhatóan kell kinyernie.

## Előfeltételek
- **GroupDocs.Metadata for Java** verzió 24.12 vagy újabb.  
- Java Development Kit (JDK 8 vagy újabb).  
- IntelliJ IDEA vagy Eclipse fejlesztőkörnyezet.  
- Alapvető Java‑fájlkezelési ismeretek.

## A GroupDocs.Metadata for Java beállítása

### Maven beállítás
Ha Maven‑nel kezeled a függőségeket, add hozzá a tárolót és a függőséget a `pom.xml`‑hez:

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
Alternatívaként letöltheted a könyvtárat a hivatalos kiadási oldalról:  
[GroupDocs.Metadata for Java kiadások](https://releases.groupdocs.com/metadata/java/)

#### Licencbeszerzési lépések
- **Ingyenes próba:** Kezdd egy ingyenes próbával, hogy felfedezd az API‑t.  
- **Ideiglenes licenc:** Szerezz be egy ideiglenes kulcsot korlátlan teszteléshez.  
- **Vásárlás:** Szerezz teljes licencet a termelési telepítésekhez.

### Alapvető inicializálás és beállítás
Miután a függőség a helyén van, hozz létre egy `Metadata` objektumot, és mutasd rá a prezentációs fájlra:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## Hogyan **java extract document properties** egy prezentációból
Az alábbiakban a leggyakoribb beépített tulajdonságokon vezetünk végig, pontosan bemutatva, hogyan olvassuk ki őket.

### Szerző információjának kinyerése
**Áttekintés:** A prezentációt létrehozó személy nevének lekérdezése.

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*Az `getAuthor()` metódus a szerző karakterláncát adja vissza, vagy `null`‑t, ha a mező üres.*

### Létrehozási idő (read created time java) kinyerése
**Áttekintés:** A fájl első létrehozásának időpontját jelző időbélyeg lekérdezése.

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*Az `getCreatedTime()` egy `java.util.Date` objektumot ad vissza, amely a létrehozás pillanatát reprezentálja – pontosan azt, amire a “read created time java” kifejezés utal.*

### Céginformáció kinyerése
**Áttekintés:** A prezentációhoz kapcsolódó szervezet nevének lekérdezése.

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*Az `getCompany()` metódus a cég metaadatait adja vissza, vagy `null`‑t, ha nincs beállítva.*

### További metaadatok, amelyeket kinyerhetsz
Ugyanígy lekérheted a többi beépített mezőt, például **Category**, **Keywords**, **Last Printed Date**, és **Application Name** a `getCategory()`, `getKeywords()` stb. metódusokkal.

## Gyakorlati alkalmazások
1. **Dokumentumkezelő rendszerek:** Indexeld a prezentációkat szerző, cég vagy létrehozási dátum alapján a gyors visszakereséshez.  
2. **Megfelelőségi audit:** Ellenőrizd, hogy a szükséges metaadat (pl. létrehozási időbélyeg) jelen van‑e a archiválás előtt.  
3. **Automatizált jelentéskészítés:** Készíts összefoglaló jelentéseket, amelyek felsorolják, ki és mikor hozta létre az egyes diavetítéseket.  
4. **CRM integráció:** Kösd össze a prezentációkat ügyfélrekordokkal a cég metaadatmező segítségével.

## Teljesítménybeli szempontok
- **Párhuzamos feldolgozás:** Nagy mennyiségű fájl esetén dolgozd fel a dokumentumokat külön szálakon a teljesítmény növelése érdekében.  
- **Erőforrás-kezelés:** Használj try‑with‑resources (ahogy a példában látható) a stream‑ek automatikus lezárásához és a memória‑szivárgások elkerüléséhez.  
- **Kötegelt kinyerés:** A GroupDocs.Metadata támogatja a tömeges műveleteket; fontold meg több fájl egyidejű beolvasását egy ciklusban a hatékonyság érdekében.

## Gyakori problémák és megoldások
- **Hiányzó metaadat:** Ha egy tulajdonság `null`‑t ad vissza, az azt jelenti, hogy a forrásfájl egyszerűen nem tartalmazza azt az információt. Kezeld a `null` értékeket a bemutatott módon.  
- **Nem támogatott formátum:** Győződj meg róla, hogy a fájl támogatott PowerPoint‑formátum (`.pptx`, `.ppt`).  
- **Licenc hibák:** Ellenőrizd, hogy a licencfájl a megfelelő helyen van‑e, vagy hogy a próbaidőszak még nem járt le.

## Gyakran feltett kérdések

**Q: Hogyan kezeljem a hiányzó metaadat‑tulajdonságokat?**  
A: Az API `null`‑t ad vissza a be nem állított mezőkre. Használj feltételes kifejezést, például `(author != null ? author : "N/A")`, hogy alapértelmezett értéket biztosíts.

**Q: Kinyerhet-e a GroupDocs.Metadata egyedi metaadat‑mezőket?**  
A: Igen, a beépített tulajdonságokon túl egyedi kulcs/érték párokat is olvashatsz és írhatod ugyanazzal az API‑val.

**Q: Támogatottak-e más prezentációs formátumok?**  
A: A GroupDocs.Metadata működik PowerPoint‑tal (`.ppt`, `.pptx`) valamint PDF‑vel, Word‑del és számos képformátummal.

**Q: Mik a rendszerkövetelmények a GroupDocs.Metadata Java‑hoz?**  
A: Kompatibilis JDK (8 vagy újabb) és elegendő heap‑memória a feldolgozott dokumentumok méretéhez.

**Q: Hol kaphatok segítséget, ha problémába ütközöm?**  
A: Látogasd meg a hivatalos támogatási fórumot: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## Források

- **Dokumentáció:** https://docs.groupdocs.com/metadata/java/
- **API‑referencia:** https://reference.groupdocs.com/metadata/java/
- **Letöltés:** https://releases.groupdocs.com/metadata/java/
- **GitHub:** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
- **Ingyenes támogatás:** https://forum.groupdocs.com/c/metadata/
- **Ideiglenes licenc:** https://purchase.groupdocs.com/temporary-license/

Ezzel az útmutatóval már tudod, hogyan **read created time java** és **java extract document properties** PowerPoint‑prezentációkból a GroupDocs.Metadata segítségével. Illeszd be ezeket a kódrészleteket a projektedbe, hogy növeld a dokumentumintelligenciát és egyszerűsítsd a megfelelőségi munkafolyamatokat.

---

**Legutóbb frissítve:** 2026-01-26  
**Tesztelve a következővel:** GroupDocs.Metadata 24.12 for Java  
**Szerző:** GroupDocs