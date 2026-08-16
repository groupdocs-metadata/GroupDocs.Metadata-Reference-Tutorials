---
date: '2026-08-10'
description: Lär dig hur du extraherar EXIF‑metadata från PSD‑filer med GroupDocs.Metadata
  för Java. Denna guide täcker grundläggande extraktion, IFD‑paket, GPS‑data och verkliga
  användningsfall.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Lär dig hur du extraherar EXIF‑metadata från PSD‑filer med GroupDocs.Metadata
  för Java. Steg‑för‑steg‑guide, kodexempel och felsökningstips för utvecklare.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Hur man extraherar EXIF‑metadata från PSD‑filer med GroupDocs.Metadata
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
title: Hur man extraherar EXIF‑metadata från PSD‑filer med GroupDocs.Metadata
type: docs
url: /sv/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Hur man extraherar EXIF-metadata från PSD-filer med GroupDocs.Metadata

Att extrahera **EXIF metadata** från PSD-filer är ett rutinmässigt men kraftfullt steg när du behöver granska bildursprung, automatisera märkning av tillgångar eller bygga sökbara mediabibliotek. I den här handledningen kommer du att upptäcka **hur man extraherar EXIF** snabbt med GroupDocs.Metadata för Java, se de exakta API-anropen och lära dig hur man hanterar avancerade IFD-paket och GPS-koordinater. I slutet är du redo att integrera metadataextraktion i vilket Java‑baserat arbetsflöde som helst.

## Snabba svar

Klassen `Metadata` representerar en fil och ger åtkomst till dess metadata.

- **Vad är den första kodraden?** `Metadata metadata = new Metadata("sample.psd");`
- **Vilken metod returnerar artistnamnet?** `metadata.getExif().getArtist();`
- **Kan jag läsa GPS-data?** Ja – use `metadata.getExif().getGpsInfo();`
- **Behöver jag en licens för produktion?** A valid GroupDocs.Metadata license is required beyond the trial period.
- **Stödd Java-version?** Java 8 eller senare (upp till Java 21).

## Vad är EXIF-metadata?

EXIF (Exchangeable Image File Format) metadata lagrar kamerainställningar, skapelsestämplar och platsdata i bildfiler. GroupDocs.Metadata läser denna information direkt från den binära strukturen i PSD-filer och exponerar den via ett rent Java‑API. Det gör det möjligt för utvecklare att programatiskt hämta detaljer såsom kameramodell, exponeringstid och GPS‑koordinater utan manuell inspektion.

## Varför använda GroupDocs.Metadata för Java?

GroupDocs.Metadata stöder **30+ filformat** (inklusive PSD, JPEG, PNG, TIFF) och kan bearbeta filer upp till **2 GB** utan att ladda hela dokumentet i minnet. Biblioteket extraherar **över 150 olika EXIF‑taggar**, vilket garanterar att du har hela uppsättningen av kamera‑ och GPS‑attribut som behövs för analys eller efterlevnad.

## Förutsättningar

- **Java Development Kit (JDK) 8** eller nyare installerat på din maskin.  
- **Maven** för beroendehantering.  
- **GroupDocs.Metadata för Java version 24.12** (eller nyare).  
- Grundläggande kunskap om Java‑klasser, objekt och undantagshantering.

### Nödvändiga bibliotek och beroenden

| Beroende | Maven‑koordinater |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Miljöinställning

Du bör ha en Maven‑kompatibel IDE som IntelliJ IDEA eller Eclipse. Skapa ett nytt Maven‑projekt eller lägg till beroendet i ett befintligt.

## Så ställer du in GroupDocs.Metadata för Java

GroupDocs.Metadata kan läggas till i ett Maven‑projekt med några rader konfiguration. Följande steg visar hur du inkluderar repositoryt och beroendet så att biblioteket är tillgängligt på classpath.

### Maven‑inställning

Lägg till följande kodsnutt i din `pom.xml` inom `<dependencies>`‑sektionen:

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

### Direkt nedladdning

Alternativt, ladda ner den senaste JAR‑filen från den officiella releases‑sidan: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Licensförvärv

För att köra biblioteket efter 30‑dagars provperioden, skaffa en tillfällig eller fullständig licens:

1. Besök [Licensköpssidan](https://purchase.groupdocs.com/temporary-license).  
2. Välj **temporary** för testning eller **full** för produktion.  
3. Följ instruktionerna på skärmen för att bädda in licensfilen (`metadata.lic`) i din Java‑classpath.

### Grundläggande initiering och konfiguration

När biblioteket är på classpath, initiera det som visas nedan:

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

## Hur man extraherar grundläggande EXIF-metadataegenskaper från en PSD‑bild

Detta avsnitt förklarar hur man laddar en PSD‑fil, får åtkomst till EXIF‑behållaren och läser de vanligaste taggarna såsom **artist**, **copyright** och **software**. Processen innebär att skapa en `Metadata`‑instans, anropa `getExif()` och sedan hämta enskilda egenskaper med enkla getter‑metoder.

### Steg‑för‑steg‑implementering

1. **Skapa en `Metadata`‑instans** som pekar på din PSD‑fil.  
2. **Anropa `getExif()`** för att få EXIF‑behållaren.  
3. **Läs enskilda egenskaper** som `getArtist()`, `getCopyright()` och `getSoftware()`.  
4. **Skriv ut eller lagra** värdena enligt din applikationslogik.

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

> **Proffstips:** `Metadata`‑objektet upptäcker automatiskt filformatet, så du kan återanvända samma kod för JPEG‑ eller TIFF‑filer utan ändring.

## Hur man extraherar EXIF IFD‑paketegenskaper från en PSD‑bild

IFD‑sektionen (Image File Directory) innehåller djupare tekniska detaljer såsom **kamera‑serienummer**, **linsmodell** och **användarkommentarer**. `Ifd0` representerar den primära Image File Directory som innehåller grundläggande kamerainformation. Att extrahera dessa fält är användbart för forensisk analys eller högprecisionskatalogisering.

### Implementeringssteg

1. **Återanvänd `Metadata`‑instansen** från föregående avsnitt.  
2. **Navigera till IFD‑behållaren** via `metadata.getExif().getIfd0()`.  
3. **Läs egenskaper** som `getBodySerialNumber()` och `getUserComment()`.  
4. **Skriv ut data** eller mappa den till din domänmodell.

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

## Hur man hämtar GPS‑data (latitud, longitud) från en PSD‑fil

Många moderna kameror inbäddar GPS‑koordinater i EXIF‑blocket. `GpsInfo` innehåller geografiska koordinater som extraheras från EXIF‑data. Anropa `metadata.getExif().getGpsInfo()` och använd sedan `getLatitude()`, `getLongitude()` och `getAltitude()` för att få exakt positionsdata—ingen ytterligare parsning krävs.

### Detaljerade steg

1. **Hämta GPS‑informationsobjektet**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Läs latitud och longitud**: `gps.getLatitude()` returnerar en `double` i decimalgrader.  
3. **Hantera saknad data**: API‑et returnerar `null` om taggen saknas, så skydda mot `NullPointerException`.  

> **Vanligt fallgropp:** Vissa PSD‑filer lagrar GPS‑koordinater som rationella tal; biblioteket normaliserar dem automatiskt, men äldre filer kan kräva manuell konvertering.

## Vanliga problem och felsökning

| Symtom | Trolig orsak | Lösning |
|---------|--------------|-----|
| `Unsupported format` exception | Using an older GroupDocs.Metadata version that doesn’t recognise PSD | Upgrade to version 24.12 or later |
| `NullPointerException` when calling `getArtist()` | EXIF tag not present in the source file | Check `metadata.getExif().hasArtist()` before reading |
| License error after 30 days | License file not found on the classpath | Place `metadata.lic` in `src/main/resources` or set `Metadata.setLicense("path/to/license")` |

## Vanliga frågor

**Q: Kan jag extrahera EXIF‑metadata från en lösenordsskyddad PSD‑fil?**  
A: Ja. Ladda filen med `new Metadata("file.psd", "password")` och få sedan åtkomst till EXIF‑data som vanligt.

**Q: Stöder GroupDocs.Metadata batch‑bearbetning av många PSD‑filer?**  
A: Absolut. Instansiera ett `Metadata`‑objekt i en loop, eller använd `MetadataCollection`‑hjälpen för att effektivt bearbeta kataloger.

**Q: Vilka Java‑versioner stöds officiellt?**  
A: Java 8 till Java 21 är fullt testade. Biblioteket använder endast standard‑API:er, så det fungerar på alla kompatibla JVM:er.

**Q: Är det möjligt att skriva EXIF‑data tillbaka till en PSD‑fil?**  
A: Ja. Efter att ha ändrat egenskaper via `Exif`‑objektet, anropa `metadata.save("output.psd")` för att spara ändringarna.

**Q: Hur stor PSD‑fil kan biblioteket hantera utan att minnet tar slut?**  
A: GroupDocs.Metadata strömmar data och kan bearbeta filer upp till **2 GB** på en vanlig maskin med 8 GB RAM, tack vare dess låg‑minnesarkitektur.

## Slutsats

Du vet nu **hur man extraherar EXIF**‑metadata från PSD‑filer med GroupDocs.Metadata för Java, från grundläggande taggar till avancerad IFD‑ och GPS‑information. Integrera dessa kodsnuttar i din bildbehandlingspipeline för att automatisera katalogisering, efterlevnadskontroller eller platsbaserade tjänster. För djupare utforskning, prova att extrahera metadata från andra stödda format (JPEG, TIFF, PNG) eller experimentera med skriv‑tillbaka‑funktionerna för att bädda in anpassade taggar.

---

**Senast uppdaterad:** 2026-08-10  
**Testad med:** GroupDocs.Metadata 24.12 for Java  
**Författare:** GroupDocs

## Relaterade handledningar

- [Extrahera bildresurser från PSD‑filer med GroupDocs.Metadata i Java: En omfattande guide](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Extrahera PSD‑header och lagerinformation med GroupDocs.Metadata för Java: En omfattande guide](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Extrahera MakerNote‑egenskaper som TIFF/EXIF‑taggar med GroupDocs.Metadata i Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)