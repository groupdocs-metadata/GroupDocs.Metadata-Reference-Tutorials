---
date: '2026-02-19'
description: Tanulja meg, hogyan olvassa be a SevenZip metaadatait Java-ban a GroupDocs.Metadata
  for Java segítségével, beleértve a tömörített méret és egyéb archívum tulajdonságok
  lekérését.
keywords:
- SevenZip metadata Java
- extract SevenZip archive information
- read SevenZip file properties
title: Hogyan olvassuk a SevenZip metaadatokat a GroupDocs.Metadata segítségével Java-ban
type: docs
url: /hu/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# Hogyan olvassuk a SevenZip metaadatokat a GroupDocs.Metadata segítségével Java-ban

Ha Java alkalmazásból kell **read sevenzip metadata java** olvasni, jó helyen jár. Ebben az útmutatóban bemutatjuk, hogyan használhatja a **GroupDocs.Metadata**-t fájlnevek, tömörített méretek, kitömörített méretek, módosítási dátumok és egyéb adatok kinyerésére – pontosan azokra az információkra, amelyekre a biztonsági mentés ellenőrzéséhez, szinkronizáláshoz vagy tárolás‑optimalizálási feladatokhoz szükség van.

## Bevezetés

Küzd a SevenZip archívumfájlok metaadat‑tulajdonságainak elérésével és olvasásával Java-ban? Ez az útmutató végigvezeti a **GroupDocs.Metadata** használatának folyamatán. Ez a hatékony könyvtár leegyszerűsíti a fontos információk, például fájlnevek, méretek és módosítási dátumok közvetlen kinyerését az archívumokból.

## Gyors válaszok
- **Milyen könyvtárat használjak?** GroupDocs.Metadata for Java  
- **Listázhatok fájlokat egy SevenZip archívumban?** Igen – használja a `getSevenZipPackage().getFiles()`  
- **Szükségem van licencre?** Egy ingyenes próba a kiértékeléshez megfelelő; a teljes licenc a termeléshez szükséges  
- **Melyik Java verzió támogatott?** JDK 8 vagy újabb  
- **Kell a Maven?** Nem kötelező, de a Maven egyszerűsíti a függőségek kezelését  

## Mi az a „how to read sevenzip” Java-ban?

A SevenZip metaadatok olvasása azt jelenti, hogy megnyitja a `.7z` konténert, felsorolja az egyes bejegyzéseket, és kinyeri a **compressed size**, **uncompressed size**, **file name**, és **modification date** tulajdonságokat anélkül, hogy a tényleges fájlokat kicsomagolná.

## read sevenzip metadata java

Az elsődleges kulcsszó dedikált címsorban való használata segíti az olvasókat és a keresőmotorokat a guide fókuszának megértésében. Az alábbiakban részletesen bemutatjuk a lépéseket, amelyekkel hatékonyan **read sevenzip metadata java** tudja elvégezni.

## Miért használja a GroupDocs.Metadata Java-t metaadatok kinyeréséhez?

- **Unified API** – több tucat archívum- és dokumentumformátumon működik  
- **No external tools** – minden a Java folyamaton belül történik  
- **Performance‑focused** – csak a metaadat extraction java feladatokhoz szükséges fejlécinformációkat olvassa  
- **Robust licensing** – próba elérhető, teljes licenc kereskedelmi használathoz  

## Előkövetelmények

Mielőtt elkezdené a **GroupDocs.Metadata for Java** használatát, győződjön meg arról, hogy a fejlesztői környezet megfelelően be van állítva. Íme, amire szüksége lesz:

- **Java Development Kit (JDK):** 8-as vagy újabb verzió.  
- **Maven:** Ajánlott a függőségek kezeléséhez, bár a JAR-t manuálisan is hozzáadhatja.  
- **Alap Java ismeretek:** Osztályok, metódusok és kivételkezelés ismerete.  

## A GroupDocs.Metadata beállítása Java-hoz

A GroupDocs.Metadata használatához adja hozzá a projektjéhez Maven-en keresztül vagy a könyvtár közvetlen letöltésével.

### Maven használata

Adja hozzá a következő konfigurációt a `pom.xml` fájlhoz:

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

Alternatívaként töltse le a legújabb verziót a [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) oldalról.

#### Licenc beszerzése

1. **Free Trial:** Kezdje egy ingyenes próbaidőszakkal a GroupDocs.Metadata képességeinek teszteléséhez.  
2. **Temporary License:** Kérjen ideiglenes licencet, ha hosszabb kiértékelési hozzáférésre van szüksége.  
3. **Purchase:** Hosszú távú használathoz fontolja meg egy teljes licenc megvásárlását.

A beállítás befejezése után lépjünk tovább a metaadat‑olvasási funkció megvalósítására.

## Implementációs útmutató

### Metaadatok elérése SevenZip archívumokból

Ebben a szakaszban kinyerjük és kiírjuk a metaadat-tulajdonságokat, például a fájlneveket és méreteket egy SevenZip archívumból.

#### 1. lépés: Metadata objektum inicializálása

Kezdje a `Metadata` objektum inicializálásával a SevenZip fájl elérési útjával. Ez megmondja a GroupDocs-nak, melyik fájlon kell dolgoznia.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### 2. lépés: Gyökércsomag lekérése

Ezután érje el az archívum gyökércsomagját, amely belépési pontot biztosít az összes fájlhoz és azok tulajdonságaihoz.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Miért használja a `getRootPackageGeneric()`‑t?** Általános nézetet biztosít az archívum tartalmáról, megkönnyítve a bejegyzések iterálását anélkül, hogy konkrét fájlformátumok miatt aggódna.

#### 3. lépés: Archívumbejegyzések iterálása

Miután hozzáfér a archívum gyökércsomagjához, iteráljon minden bejegyzésen a metaadat-tulajdonságok kinyeréséhez. Ez magában foglalja a név, a tömörített méret és a módosítási dátum lekérését.

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

- **Miért kell ezeket a tulajdonságokat kinyerni?** A fájlméretek ismerete segít a tárolás kezelésében, míg a módosítási dátum kulcsfontosságú lehet a szinkronizálási feladatoknál. A `getCompressedSize()` hívás a Java módja a **get compressed size java** lekérésének minden bejegyzéshez.

#### 4. lépés: Erőforrások felszabadítása

Végül győződjön meg róla, hogy eldobja a metadata objektumot, hogy felszabadítsa a GroupDocs.Metadata által lefoglalt erőforrásokat.

```java
} finally {
    metadata.dispose();
}
```

- **Miért kell eldobni?** Az objektumok megfelelő eldobása segít megelőzni a memória szivárgásokat a hosszú távú alkalmazásokban.

## Gyakorlati alkalmazások

A **read sevenzip metadata java** megértése számos valós előnnyel jár:

1. **Adatbiztonsági mentés kezelése:** Gyorsan ellenőrizze a biztonsági mentés archívumok integritását és teljességét.  
2. **Fájl szinkronizációs eszközök:** Használja a módosítási dátumokat annak eldöntésére, mely fájlokat kell frissíteni.  
3. **Tárolás optimalizálása:** Hasonlítsa össze a tömörített és kitömörített méreteket a kapacitástervezéshez.

Az integráció más rendszerekkel lehetséges, lehetővé téve az automatikus metaadat-kinyerést a nagyobb adatkezelési munkafolyamatok részeként.

## Teljesítmény szempontok

GroupDocs.Metadata és nagy archívumok használata során vegye figyelembe ezeket a tippeket:

- **Batch Processing:** Fájlok feldolgozása kötegekben a memóriahasználat hatékony kezelése érdekében.  
- **Efficient Exception Handling:** Használjon try‑with‑resources-t az automatikus erőforrás-kezeléshez.  
- **Asynchronous Processing:** Aszinkron technikák alkalmazása nagy terhelés esetén.

## Gyakori problémák és megoldások

| Issue | Solution |
|-------|----------|
| **`NullPointerException` fájl elérésekor** | Ellenőrizze, hogy az archívum útvonala helyes-e, és a fájl nem sérült. |
| **Memória csúcsok hatalmas archívumoknál** | Engedélyezze a kötegelt feldolgozást vagy növelje a JVM heap méretét (`-Xmx`). |
| **A licenc nem ismerhető fel** | Győződjön meg róla, hogy a licencfájl az alkalmazás munkakönyvtárában van, vagy állítsa be a `License.setLicense(path)` segítségével. |

## Gyakran Ismételt Kérdések

**Q:** Mi az a GroupDocs.Metadata?  
**A:** Egy Java könyvtár, amely különböző fájlformátumok metaadatainak kezelésére szolgál, beleértve a SevenZip archívumokat.

**Q:** Használhatom a GroupDocs.Metadata‑t Maven nélkül?  
**A:** Igen, letöltheti a JAR-t a hivatalos oldalról, és hozzáadhatja a projekt osztályútvonalához.

**Q:** Hogyan kezeljem hatékonyan a nagy archívumokat?  
**A:** Alkalmazzon kötegelt feldolgozást vagy aszinkron stream-eket a memóriahasználat korlátozásához.

**Q:** Hol találok részletesebb útmutatót?  
**A:** Tekintse meg a [hivatalos dokumentációt](https://docs.groupdocs.com/metadata/java/) a teljes API referenciáért.

**Q:** Mit tegyek, ha problémáim vannak a könyvtárral?  
**A:** Kérdezze a közösséget a [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) oldalon.

## Erőforrások

- **Documentation:** További információk a [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/) oldalon  
- **API Reference:** Részletes API információk a [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/) oldalon  
- **Download:** A legújabb verzió letölthető a [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/) oldalról  
- **GitHub Repository:** Kódminták a [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java) oldalon  
- **Free Support Forum:** Csatlakozzon a beszélgetésekhez vagy tegyen fel kérdéseket a [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/) fórumon

---

**Legutóbb frissítve:** 2026-02-19  
**Tesztelve a következővel:** GroupDocs.Metadata 24.12 for Java  
**Szerző:** GroupDocs