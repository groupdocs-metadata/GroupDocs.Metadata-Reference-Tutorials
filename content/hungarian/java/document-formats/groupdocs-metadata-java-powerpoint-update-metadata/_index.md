---
date: '2026-05-27'
description: Ismerje meg, hogyan állíthatja be a pptx CreatedTime értékét Java-ban
  a GroupDocs Maven függőség használatával a PowerPoint metaadatok frissítéséhez,
  beleértve a PPTX létrehozási dátumának módosítását.
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
title: PPTX Létrehozási Idő beállítása Java-ban a GroupDocs Maven függőséggel
type: docs
url: /hu/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Állítsa be a PPTX Létrehozás Idejét Java-ban a GroupDocs.Metadata segítségével

A pontos metaadatok elengedhetetlenek a megfelelőség és a megtalálhatóság szempontjából a modern dokumentumáramlásokban. A **GroupDocs.Metadata** segítségével programozottan **állíthatja be a PPTX CreatedTime értékét Java-ban**, lehetővé téve a **PPTX létrehozási dátumának módosítását** egyéb beépített tulajdonságok, például szerző vagy cég mellett. Ez az útmutató végigvezet a Maven beállításon, az API inicializálásán, a metaadatok frissítésén és a módosított prezentáció mentésén – mindezt tiszta, termelésre kész kóddal.

## Gyors válaszok
- **Melyik könyvtár frissíti a PowerPoint metaadatait Java-ban?** GroupDocs.Metadata a GroupDocs Maven függőségén keresztül.  
- **Beállíthatom a PPTX CreatedTime tulajdonságot?** Igen – használja a `root.getDocumentProperties().setCreatedTime(yourDate)` metódust.  
- **Szükséges licenc a termeléshez?** A próbaverzió elegendő értékeléshez; a kereskedelmi licenc kötelező a termelési környezetben.  
- **Melyik build eszközt használja a példa?** Maven (a JAR-t manuálisan is letöltheti).  
- **Támogatja-e az API a Java 8 és újabb verziókat?** Teljes mértékben – a GroupDocs.Metadata a Java 8+ célplatformra épül.

## Mi az a GroupDocs Maven függőség?
A **GroupDocs Maven függőség** egy Maven‑kompatibilis tárolóbejegyzés, amely a legújabb GroupDocs.Metadata könyvtárat húzza be a Java projektjébe. Egyszerűsíti a függőségkezelést azáltal, hogy automatikusan feloldja a transzitív könyvtárakat, garantálja, hogy mindig a legfrissebb és legbiztonságosabb verziót használja, és megszünteti a kézi JAR‑letöltések vagy verziókövetés szükségességét.

## Miért használjuk a GroupDocs.Metadata‑t a PPTX létrehozási dátum módosításához?
A GroupDocs.Metadata lehetővé teszi az automatizált, kötegelt PPTX létrehozási időbélyegek frissítését, biztosítva, hogy minden prezentáció megfeleljen a vállalati szabályzatoknak vagy jogi követelményeknek. A CreatedTime tulajdonság programozott beállításával elkerülhető a kézi szerkesztés, csökken az emberi hiba, és a változtatás beépíthető CI/CD folyamatokba vagy migrációs szkriptekbe a zökkenőmentes dokumentumkezelés érdekében.

## Előfeltételek
- Java 8 vagy újabb telepítve.  
- IDE, például IntelliJ IDEA vagy Eclipse.  
- Maven a függőségkezeléshez.  
- Hozzáférés egy GroupDocs próbaverzióhoz vagy megvásárolt licenchez.

## Hogyan állítsa be a PPTX CreatedTime értékét Java-ban?

A `Metadata` osztály egy dokumentumot képvisel, és hozzáférést biztosít a metaadat‑tulajdonságaihoz.

Töltse be a PowerPoint fájlt a `new Metadata("presentation.pptx")` segítségével, szerezze meg a gyökércsomagot, hívja meg a `setCreatedTime`‑t a kívánt `java.util.Date` objektummal, majd végül a `save`‑t a változtatások írásához. Ez az átfogó folyamat módosítja a létrehozási dátumot, miközben megőrzi az összes diát és egyéb tulajdonságot.

### Maven beállítás
Adja hozzá a GroupDocs tárolót és a metaadat‑függőséget a `pom.xml`‑hez:

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

> **Pro tipp:** A verziószám naprakészen tartása biztosítja, hogy a legújabb hibajavítások és teljesítményjavítások elérhetők legyenek.

### Közvetlen letöltés (ha nem szeretne Maven‑t használni)

Alternatívaként töltse le a legújabb JAR‑t a [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) oldalról.

#### Licenc beszerzése

Kezdje egy ingyenes próbaverzióval, vagy kérjen ideiglenes licencet a GroupDocs.Metadata értékeléséhez. Termelési használathoz vásároljon licencet a [GroupDocs hivatalos weboldalán](https://purchase.groupdocs.com/temporary-license/).

## Alapvető inicializálás és beállítás

Miután a könyvtár a classpath‑on van, létrehozhat egy `Metadata` példányt, amely a PowerPoint fájlra mutat:

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

Ez a kód egy try‑with‑resources blokkban nyitja meg a prezentációt, garantálva, hogy a fájlkezelő automatikusan felszabaduljon.

## Lépésről‑lépésre útmutató a beépített metaadatok frissítéséhez

### 1. lépés: A prezentáció betöltése

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

A fájl betöltése kapcsolatot hoz létre, amely lehetővé teszi a metaadatok olvasását vagy írását.

### 2. lépés: A prezentáció gyökércsomagjának elérése

A `root` objektum hozzáférést biztosít a prezentáció alapcsomagjához és beépített tulajdonságaihoz.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

A `root` objektum minden beépített dokumentumtulajdonságot kiérhet.

### 3. lépés: Beépített dokumentumtulajdonságok frissítése (beleértve a létrehozási dátumot)

A `setCreatedTime` új létrehozási időbélyeget rendel a dokumentumhoz.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Itt bemutatjuk, hogyan **állítsa be a PPTX CreatedTime‑t** egy új `Date` objektum `CreatedTime`‑hez rendelésével. Cserélje a `new Date()`‑t a kívánt időbélyegre.

### 4. lépés: A frissített prezentáció mentése

A `save` visszaírja a módosított metaadatokat egy fájlba.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

A `save` hívás a módosított metaadatokat egy új PowerPoint fájlba írja, az eredetit érintetlenül hagyva.

## Hibaelhárítási tippek
- **File Not Found:** Ellenőrizze a bemeneti útvonalat és a fájl jogosultságait.  
- **Version Mismatch:** Győződjön meg róla, hogy a `groupdocs-metadata` verziója megegyezik a Java futtatókörnyezetével.  
- **Property Not Updating:** Ellenőrizze, hogy a `setCreatedTime` (vagy a megfelelő setter) meghívásra került‑e a `save` előtt.

## Gyakorlati alkalmazások

1. **Vállalati arculat:** Automatikusan injektálja a helyes cégnevet és kategóriát minden diakészletbe a terjesztés előtt.  
2. **Dokumentumkezelő rendszerek:** Gazdagítsa a PPTX fájlokat kereshető metaadatokkal a gyorsabb visszakeresés érdekében.  
3. **Oktatási anyagok:** Tartsa naprakészen a szerzői és tantervi információkat az előadási diákon.  
4. **Együttműködési nyomonkövetés:** Rögzítse a közreműködők neveit a felelősségvállalás fenntartása érdekében.  
5. **CMS integráció:** Szinkronizálja a metaadat‑változásokat tartalomkezelő platformjával valós időben.

## Teljesítménybeli megfontolások
- **Kötegelt feldolgozás:** Iteráljon egy fájllistán, és ahol lehetséges, használjon egyetlen `Metadata` példányt újra.  
- **Memóriakezelés:** Mindig alkalmazzon try‑with‑resources‑t (ahogy a példában látható) a natív erőforrások gyors felszabadítása érdekében.  
- **Hatékony adatstruktúrák:** Tárolja a metaadat‑frissítéseket egy map‑ben, mielőtt alkalmazná őket, így csökkentve az ismétlődő hívások számát.

## Gyakran Ismételt Kérdések

**Q: Mi a fő célja a GroupDocs Maven függőségnek?**  
A: Kényelmes módot biztosít a legújabb GroupDocs.Metadata könyvtár Maven‑alapú Java projektekbe való beillesztésére.

**Q: Hogyan állíthatom be a PPTX létrehozási dátumot anélkül, hogy más tulajdonságokat érinteném?**  
A: Hívja meg a `root.getDocumentProperties().setCreatedTime(yourDesiredDate)`‑t a `metadata.save()` előtt.

**Q: Szükséges licenc a kód fejlesztésben való futtatásához?**  
A: Ideiglenes próbaverzió elegendő fejlesztéshez és teszteléshez; a teljes licenc kötelező a termeléshez.

**Q: Frissíthetek egyéni metaadat‑mezőket is?**  
A: Igen – a GroupDocs.Metadata támogatja a beépített és egyéni tulajdonságok kezelését az API‑ján keresztül.

**Q: Van mód a változtatások visszavonására, ha hibát követek el?**  
A: Tartson meg egy másolatot az eredeti fájlról, vagy olvassa ki a meglévő tulajdonságértékeket a felülírás előtt, majd szükség esetén állítsa vissza őket.

## Források

- [Documentation](https://docs.groupdocs.com/metadata/java/)  
- [API Reference](https://apireference.groupdocs.com/metadata/java/)

---

**Utoljára frissítve:** 2026-05-27  
**Tesztelve:** GroupDocs.Metadata 24.12 for Java  
**Szerző:** GroupDocs  

---

## Kapcsolódó oktatóanyagok

- [Update Custom Metadata in PowerPoint Using GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)  
- [How to Update Word Document Metadata Using GroupDocs.Metadata Java: A Complete Guide](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)  
- [Efficiently Update PDF Metadata with GroupDocs.Metadata in Java for Document Management](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)