---
date: '2026-06-17'
description: Ismerje meg, hogyan módosíthatja a diagram létrehozási időt, és automatizálhatja
  a metaadatok frissítését diagramfájlok esetén a GroupDocs.Metadata Java használatával.
keywords:
- change diagram creation time
- groupdocs metadata java
- update diagram metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  headline: Change Diagram Creation Time in Metadata with GroupDocs Java
  type: TechArticle
- description: Learn how to change diagram creation time and automate metadata update
    for diagram files using GroupDocs.Metadata in Java.
  name: Change Diagram Creation Time in Metadata with GroupDocs Java
  steps:
  - name: Load the Diagram Document
    text: '*Explanation:* The `Metadata` constructor receives the path to your diagram
      file. The try‑with‑resources block ensures the file is closed properly after
      the operation.'
  - name: Access the Root Package
    text: '*Explanation:* The root package gives you direct access to all built‑in
      metadata fields for the diagram.'
  - name: Set the Creator Property
    text: '*Explanation:* Assigns a new author name. Replace `"test author"` with
      the actual creator.'
  - name: Change Creation Time
    text: '*Explanation:* This line **changes creation time** to the current system
      date and time. You can also supply a specific `Date` instance if you need a
      custom timestamp.'
  - name: Define Company Information
    text: '*Explanation:* Stores the company name associated with the diagram—useful
      for enterprise tracking.'
  - name: Set Document Category
    text: '*Explanation:* Categorizes the file, helping you **update diagram category**
      consistently across your repository.'
  - name: Add Keywords
    text: '*Explanation:* Keywords improve searchability; you can list any terms relevant
      to the diagram’s content.'
  - name: Save Changes
    text: '*Explanation:* Persists all modifications to a new file, leaving the original
      untouched.'
  type: HowTo
- questions:
  - answer: Yes, the same API works for all diagram formats supported by GroupDocs.Metadata.
    question: Can I use this approach with other diagram formats like VSDX?
  - answer: A free trial is sufficient for development and testing; a full license
      is required for production deployments.
    question: Do I need a license for development builds?
  - answer: Set each property on the `DocumentProperties` object before invoking `metadata.save(...)`;
      the library writes them all at once.
    question: How can I update multiple properties in one call?
  - answer: It’s recommended to save to a new file (as shown) and replace the original
      only after confirming the update succeeded.
    question: Is it safe to overwrite the original file?
  - answer: Create a `java.util.Date` (or `java.time` instance) with the desired timestamp
      and pass it to `setTimeCreated`.
    question: What if I need to set a custom creation date instead of the current
      time?
  type: FAQPage
title: Diagram létrehozási idő módosítása a metaadatokban a GroupDocs Java segítségével
type: docs
url: /hu/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Diagram létrehozási idő módosítása a metaadatokban a GroupDocs Java-val

Ebben a lépésről‑lépésre útmutatóban megtudja, hogyan **módosíthatja a diagram létrehozási időt**, és frissítheti a diagramfájlok egyéb beépített tulajdonságait a GroupDocs.Metadata Java könyvtár segítségével. Ezeknek a változtatásoknak az automatizálása órákat takarít meg a kézi szerkesztésből, biztosítja a konzisztens időbélyegeket a tárolójában, és azonnal kereshetővé teszi a diagramokat bármely dokumentumkezelő rendszerben.

## Gyors válaszok
- **Mi a fő cél?** Diagram létrehozási idő és egyéb metaadatok módosítása a diagramfájlokban.  
- **Melyik könyvtárat kell használni?** GroupDocs.Metadata for Java.  
- **Szükségem van licencre?** Egy ingyenes próba elegendő a teszteléshez; a teljes licenc a termeléshez szükséges.  
- **Feldolgozhatok tömegesen sok diagramot?** Igen – a logikát egy ciklusba vagy párhuzamos streambe lehet csomagolni.  
- **Milyen Java verzió szükséges?** JDK 8 vagy újabb.

## Mi a “diagram létrehozási idő módosítása” a diagram metaadatokban?
A létrehozási idő módosítása felülírja a diagramfájlban (például VDX vagy VSDX) tárolt eredeti időbélyeget egy új dátum‑idő értékkel. Ez lehetővé teszi, hogy a fájl metaadatait a tényleges feldolgozási vagy archiválási dátummal egyeztesse, a szerző eredeti időbélyege helyett, ami elengedhetetlen az audit nyomvonalakhoz és a pontos keresési eredményekhez.

## Miért automatizáljuk a metaadatok frissítését diagramokhoz?
A metaadatok automatizálása biztosítja, hogy minden diagram ugyanazokat a névadási, kategorizálási és időbélyeg szabványokat kövesse emberi hiba nélkül. Emellett felgyorsítja a tömeges migrációkat, csökkenti a megfelelőségi kockázatot, és javítja a megtalálhatóságot vállalati DMS platformokon – akár 70 %-kal csökkentve a manuális erőfeszítést nagy léptékű projektekben.

## Előfeltételek
- **Java Development Kit (JDK) 8+** telepítve van a gépén.  
- **IDE** például IntelliJ IDEA vagy Eclipse.  
- **Maven** (vagy kézi JAR kezelés) a függőségkezeléshez.  
- Alapvető ismeretek a Java osztályok, metódusok és kivételkezelés terén.

### Szükséges könyvtárak és függőségek
Add the following repository and dependency to your `pom.xml` file if using Maven:

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
If you prefer downloading directly, visit [GroupDocs.Metadata Java kiadások](https://releases.groupdocs.com/metadata/java/) to get the latest version.

### Környezet beállítása
- JDK 8 vagy újabb.  
- IntelliJ IDEA, Eclipse vagy bármely Java‑kompatibilis IDE.  

### Tudás előfeltételek
A Java szintaxis és az alapvető fájl‑I/O megértése gördülékenyebbé teszi az útmutatót, de a lépések egyszerű nyelven vannak leírva.

## A GroupDocs.Metadata beállítása Java-hoz
### Telepítési útmutató
**Maven felhasználók:** A fenti kódrészlet automatikusan hozzáadja a tárolót és a szükséges JAR‑t.  
**Közvetlen letöltés felhasználók:** A JAR letöltése után a [GroupDocs](https://releases.groupdocs.com/metadata/java/) oldalról, adja hozzá a projekt osztályútvonalához.

### Licenc beszerzése
- **Ingyenes próba:** A könyvtár költség nélkül történő felfedezése.  
- **Ideiglenes licenc:** Szerezzen ideiglenes licencet a kiterjesztett teszteléshez [itt](https://purchase.groupdocs.com/temporary-license/).  
- **Vásárlás:** Teljes licenc beszerzése a termelési környezetekhez.

### Alap inicializálás
`Metadata` a központi osztály, amely egy dokumentum metaadat tárolóját képviseli, és olvasási/írási hozzáférést biztosít az összes beépített tulajdonsághoz. A GroupDocs.Metadata használatának megkezdéséhez importálja az osztályt, és nyisson meg egy diagramfájlt:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

## Implementációs útmutató
### Hogyan módosítsuk a létrehozási időt diagramfájlokban
Ebben a szakaszban végigvezetjük a **diagram létrehozási idő módosításához** szükséges minden lépést, valamint más gyakori tulajdonságok, például szerző, cég és kategória frissítését. A folyamat magában foglalja a diagram betöltését a Metadata API‑val, a gyökércsomag elérését, a kívánt mezők beállítását, majd végül a módosítások egy új fájlba mentését, biztosítva, hogy az eredeti érintetlen maradjon.

#### 1. lépés: Diagram dokumentum betöltése
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Magyarázat:* A `Metadata` konstruktor megkapja a diagramfájl elérési útját. A try‑with‑resources blokk biztosítja, hogy a fájl a művelet után megfelelően legyen lezárva.

#### 2. lépés: Gyökércsomag elérése
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Magyarázat:* A gyökércsomag közvetlen hozzáférést biztosít a diagram összes beépített metaadat mezőjéhez.

#### 3. lépés: Létrehozó tulajdonság beállítása
```java
root.getDocumentProperties().setCreator("test author");
```  
*Magyarázat:* Új szerzőnevet állít be. Cserélje a `"test author"` értéket a tényleges létrehozóra.

#### 4. lépés: Létrehozási idő módosítása
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Magyarázat:* Ez a sor **módosítja a létrehozási időt** a rendszer aktuális dátumára és időére. Ha egyedi időbélyeget szeretne, megadhat egy konkrét `Date` példányt is.

#### 5. lépés: Céginformáció meghatározása
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Magyarázat:* A diagramhoz kapcsolódó cégnevet tárolja – hasznos vállalati nyomon követéshez.

#### 6. lépés: Dokumentum kategória beállítása
```java
root.getDocumentProperties().setCategory("test category");
```  
*Magyarázat:* Kategorizálja a fájlt, segítve a **diagram kategória frissítését** következetesen a tárolóban.

#### 7. lépés: Kulcsszavak hozzáadása
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Magyarázat:* A kulcsszavak javítják a kereshetőséget; felsorolhat bármilyen a diagram tartalmához kapcsolódó kifejezést.

#### 8. lépés: Változások mentése
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Magyarázat:* Az összes módosítást egy új fájlba menti, az eredetit érintetlenül hagyva.

### Gyakori hibák és hibaelhárítás
- **Fájl nem található:** Ellenőrizze a bemeneti útvonalat, és győződjön meg róla, hogy a fájlkiterjesztés megfelel a tényleges formátumnak.  
- **Hozzáférés megtagadva:** Ellenőrizze az olvasási/írási jogosultságokat a bemeneti és kimeneti könyvtárakban.  
- **Érvénytelen dátumformátum:** Használjon `java.util.Date` vagy `java.time` objektumokat, amelyek kompatibilisek az API‑val.

## Gyakorlati alkalmazások
1. **Dokumentum archiválás automatizálása** – Régi diagramok archivba helyezésekor automatikusan **módosítsa a diagram létrehozási időt** az archiválási dátumra, és állítson be egységes kategóriát.  
2. **Verziókezelő integráció** – Tartsa szinkronban az időbélyegeket a Git commitokkal, a létrehozási idő frissítésével minden kiadás során.  
3. **Vállalati DMS szabványosítás** – Kényszerítse a szerző, cég és kulcsszavak vállalati szintű szabályzatát minden diagrameszközön.

## Teljesítmény szempontok
- **Kötegelt feldolgozás:** A fenti lépéseket egy ciklusba csomagolva egyszerre több tucat fájlt is kezelhet.  
- **Memória kezelés:** Minden `Metadata` példányt gyorsan szabadítson fel (a try‑with‑resources blokk ezt automatikusan megteszi).  
- **Aszinkron végrehajtás:** Nagy kötegek esetén fontolja meg a `CompletableFuture` használatát a frissítések párhuzamos futtatásához, a fő szál blokkolása nélkül.  
- **Mennyiségi képesség:** A GroupDocs.Metadata több mint 30 diagramformátumot támogat, és akár 500 MB méretű fájlokat is feldolgozhat a teljes dokumentum memóriába betöltése nélkül, frissítéseket 200 ms alatti idő alatt biztosítva egy tipikus szerver hardveren.

## Következtetés
Most már tudja, hogyan **módosíthatja a diagram létrehozási időt** és frissítheti a diagramdokumentumok egyéb beépített metaadat tulajdonságait a GroupDocs.Metadata Java‑ban. Ezeknek a lépéseknek az automatizálásával konzisztens, kereshető és megfelelőségi dokumentációt tarthat fenn szervezete számára.

**Következő lépések**
- Kísérletezzen a GroupDocs.Metadata által támogatott egyéb fájlformátumokkal (PDF, DOCX, stb.).  
- Integrálja a kódot egy CI/CD csővezetékbe, hogy minden buildnél érvényesítse a metaadat szabványokat.  

Készen áll a kipróbálásra? Látogasson el a [GroupDocs.Metadata Java kiadások](https://releases.groupdocs.com/metadata/java/) oldalra, és kezdje el ma a saját metaadat automatizálásának megvalósítását.

---

**Legutóbb frissítve:** 2026-06-17  
**Tesztelve ezzel:** GroupDocs.Metadata 24.12  
**Szerző:** GroupDocs  

## Gyakran Ismételt Kérdések

**K: Használhatom ezt a megközelítést más diagramformátumokkal, például VSDX‑szel?**  
V: Igen, ugyanaz az API működik minden, a GroupDocs.Metadata által támogatott diagramformátummal.

**K: Szükségem van licencre a fejlesztői buildekhez?**  
V: Az ingyenes próba elegendő fejlesztéshez és teszteléshez; a teljes licenc a termelési környezethez szükséges.

**K: Hogyan frissíthetek több tulajdonságot egy hívásban?**  
V: Állítsa be minden tulajdonságot a `DocumentProperties` objektumban, mielőtt meghívná a `metadata.save(...)`‑t; a könyvtár egyszerre írja őket.

**K: Biztonságos-e felülírni az eredeti fájlt?**  
V: Ajánlott egy új fájlba menteni (ahogy a példában), és csak a frissítés sikerességének megerősítése után cserélni le az eredetit.

**K: Mi van, ha egyedi létrehozási dátumot kell beállítanom a jelenlegi idő helyett?**  
V: Hozzon létre egy `java.util.Date` (vagy `java.time` példányt) a kívánt időbélyeggel, és adja át a `setTimeCreated`‑nek.

## Kapcsolódó útmutatók

- [Hogyan frissítsük a diagram metaadatait Java-val a GroupDocs.Metadata segítségével](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)  
- [Hogyan frissítsük a DXF szerző metaadatait a GroupDocs.Metadata for Java‑val – Teljes útmutató](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)  
- [Java metaadat frissítések automatizálása dátum szerint a GroupDocs.Metadata segítségével a hatékony fájlkezeléshez](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)