---
date: '2026-08-10'
description: Leer hoe u EXIF-metadata uit PSD‑bestanden kunt extraheren met GroupDocs.Metadata
  voor Java. Deze gids behandelt basis‑extractie, IFD‑pakketten, GPS‑gegevens en praktijkvoorbeelden.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Leer hoe u EXIF-metadata uit PSD‑bestanden kunt extraheren met GroupDocs.Metadata
  voor Java. Stapsgewijze gids, code‑fragmenten en probleemoplossingstips voor ontwikkelaars.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: Hoe EXIF-metadata uit PSD‑bestanden te extraheren met GroupDocs.Metadata
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
title: Hoe EXIF-metadata uit PSD‑bestanden te extraheren met GroupDocs.Metadata
type: docs
url: /nl/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# Hoe EXIF-metadata uit PSD-bestanden te extraheren met GroupDocs.Metadata

Het extraheren van **EXIF-metadata** uit PSD-bestanden is een routineuze maar krachtige stap wanneer u de herkomst van afbeeldingen moet controleren, asset‑tagging moet automatiseren of doorzoekbare mediabibliotheken moet opbouwen. In deze tutorial ontdekt u **hoe u EXIF snel kunt extraheren** met GroupDocs.Metadata voor Java, ziet u de exacte API‑aanroepen en leert u hoe u geavanceerde IFD‑pakketten en GPS‑coördinaten kunt verwerken. Aan het einde bent u klaar om metadata‑extractie te integreren in elke Java‑gebaseerde workflow.

## Snelle antwoorden
De `Metadata`‑klasse vertegenwoordigt een bestand en biedt toegang tot de metadata ervan.

- **Wat is de eerste regel code?** `Metadata metadata = new Metadata("sample.psd");`
- **Welke methode retourneert de artiestennaam?** `metadata.getExif().getArtist();`
- **Kan ik GPS-gegevens lezen?** Ja – gebruik `metadata.getExif().getGpsInfo();`
- **Heb ik een licentie nodig voor productie?** Een geldige GroupDocs.Metadata‑licentie is vereist na de proefperiode.
- **Ondersteunde Java‑versie?** Java 8 of later (tot Java 21).

## Wat is EXIF-metadata?
EXIF (Exchangeable Image File Format) metadata slaat camera‑instellingen, aanmaak‑tijdstempels en locatiegegevens op binnen afbeeldingsbestanden. GroupDocs.Metadata leest deze informatie direct uit de binaire structuur van PSD‑bestanden en maakt deze beschikbaar via een nette Java‑API. Het stelt ontwikkelaars in staat om programmatisch details op te halen zoals cameramodel, belichtingstijd en GPS‑coördinaten zonder handmatige inspectie.

## Waarom GroupDocs.Metadata voor Java gebruiken?
GroupDocs.Metadata ondersteunt **meer dan 30 bestandsformaten** (inclusief PSD, JPEG, PNG, TIFF) en kan bestanden verwerken tot **2 GB** zonder het volledige document in het geheugen te laden. De bibliotheek extraheert **meer dan 150 verschillende EXIF‑tags**, waardoor u de volledige set camera‑ en GPS‑attributen heeft die nodig zijn voor analyses of naleving.

## Voorvereisten
- **Java Development Kit (JDK) 8** of nieuwer geïnstalleerd op uw machine.  
- **Maven** voor afhankelijkheidsbeheer.  
- **GroupDocs.Metadata voor Java versie 24.12** (of nieuwer).  
- Basiskennis van Java‑klassen, objecten en foutafhandeling.

### Vereiste bibliotheken en afhankelijkheden
| Afhankelijkheid | Maven‑coördinaten |
|-----------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### Omgevingsconfiguratie
U dient een Maven‑compatibele IDE te hebben, zoals IntelliJ IDEA of Eclipse. Maak een nieuw Maven‑project aan of voeg de afhankelijkheid toe aan een bestaand project.

## Hoe GroupDocs.Metadata voor Java in te stellen
GroupDocs.Metadata kan aan een Maven‑project worden toegevoegd met enkele regels configuratie. De volgende stappen laten zien hoe u de repository en afhankelijkheid opneemt zodat de bibliotheek beschikbaar is op het classpath.

### Maven‑configuratie
Add the following snippet to your `pom.xml` inside the `<dependencies>` section:

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

### Directe download
Download anders de nieuwste JAR van de officiële releases‑pagina: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Licentie‑acquisitie
Om de bibliotheek te gebruiken na de 30‑daagse proefperiode, verkrijg een tijdelijke of volledige licentie:

1. Bezoek de [License Purchase Page](https://purchase.groupdocs.com/temporary-license).  
2. Kies **temporary** voor testen of **full** voor productie.  
3. Volg de instructies op het scherm om het licentiebestand (`metadata.lic`) in uw Java‑classpath te plaatsen.

### Basisinitialisatie en configuratie
After the library is on the classpath, initialize it as shown below:

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

## Hoe basis‑EXIF‑metadata‑eigenschappen uit een PSD‑afbeelding te extraheren
Deze sectie legt uit hoe u een PSD‑bestand laadt, de EXIF‑container benadert en de meest voorkomende tags leest, zoals **artist**, **copyright** en **software**. Het proces omvat het maken van een `Metadata`‑instantie, het aanroepen van `getExif()`, en vervolgens het ophalen van individuele eigenschappen met eenvoudige getter‑methoden.

### Stapsgewijze implementatie
1. **Maak een `Metadata`‑instantie** die naar uw PSD‑bestand wijst.  
2. **Roep `getExif()` aan** om de EXIF‑container te verkrijgen.  
3. **Lees individuele eigenschappen** zoals `getArtist()`, `getCopyright()` en `getSoftware()`.  
4. **Print of sla** de waarden op volgens uw toepassingslogica.

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

> **Pro tip:** Het `Metadata`‑object detecteert automatisch het bestandsformaat, zodat u dezelfde code kunt hergebruiken voor JPEG‑ of TIFF‑bestanden zonder aanpassing.

## Hoe EXIF‑IFD‑pakket‑eigenschappen uit een PSD‑afbeelding te extraheren
De IFD (Image File Directory)‑sectie bevat diepere technische details zoals **camera‑serienummer**, **lensmodel** en **gebruikerscommentaren**. `Ifd0` vertegenwoordigt de primaire Image File Directory met basis‑camera‑informatie. Het extraheren van deze velden is nuttig voor forensische analyse of nauwkeurige catalogisering.

### Implementatiestappen
1. **Herbruik de `Metadata`‑instantie** uit de vorige sectie.  
2. **Navigeer naar de IFD‑container** via `metadata.getExif().getIfd0()`.  
3. **Lees eigenschappen** zoals `getBodySerialNumber()` en `getUserComment()`.  
4. **Geef de gegevens weer** of map ze naar uw domeinmodel.

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

## Hoe GPS‑gegevens (breedtegraad, lengtegraad) uit een PSD‑bestand op te halen
Veel moderne camera's embedden GPS‑coördinaten in het EXIF‑blok. `GpsInfo` bevat geografische coördinaten die uit EXIF‑gegevens zijn gehaald. Roep `metadata.getExif().getGpsInfo()` aan en gebruik vervolgens `getLatitude()`, `getLongitude()` en `getAltitude()` om precieze locatiegegevens te verkrijgen — geen extra parsing vereist.

### Gedetailleerde stappen
1. **Verkrijg het GPS‑info‑object**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **Lees breedte‑ en lengtegraad**: `gps.getLatitude()` retourneert een `double` in decimale graden.  
3. **Afhandelen van ontbrekende gegevens**: De API retourneert `null` als de tag afwezig is, dus bescherm tegen `NullPointerException`.  

> **Veelvoorkomend probleem:** Sommige PSD‑bestanden slaan GPS‑coördinaten op als rationale getallen; de bibliotheek normaliseert ze automatisch, maar oudere bestanden kunnen handmatige conversie vereisen.

## Veelvoorkomende problemen en foutopsporing
| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|----------|--------------------------|-----------|
| `Unsupported format` exception | Gebruik van een oudere GroupDocs.Metadata‑versie die PSD niet herkent | Upgrade naar versie 24.12 of later |
| `NullPointerException` when calling `getArtist()` | EXIF‑tag niet aanwezig in het bronbestand | Controleer `metadata.getExif().hasArtist()` vóór het lezen |
| License error after 30 days | Licentiebestand niet gevonden op het classpath | Plaats `metadata.lic` in `src/main/resources` of stel `Metadata.setLicense("path/to/license")` in |

## Veelgestelde vragen

**Q: Kan ik EXIF‑metadata extraheren uit een met wachtwoord beveiligd PSD‑bestand?**  
A: Ja. Laad het bestand met `new Metadata("file.psd", "password")` en benader vervolgens de EXIF‑gegevens zoals gewoonlijk.

**Q: Ondersteunt GroupDocs.Metadata batchverwerking van veel PSD‑bestanden?**  
A: Absoluut. Instantieer een `Metadata`‑object binnen een lus, of gebruik de `MetadataCollection`‑helper om mappen efficiënt te verwerken.

**Q: Welke Java‑versies worden officieel ondersteund?**  
A: Java 8 tot en met Java 21 zijn volledig getest. De bibliotheek gebruikt alleen standaard‑API's, dus hij werkt op elke conforme JVM.

**Q: Is het mogelijk om EXIF‑gegevens terug te schrijven naar een PSD‑bestand?**  
A: Ja. Na het wijzigen van eigenschappen via het `Exif`‑object, roep `metadata.save("output.psd")` aan om de wijzigingen op te slaan.

**Q: Hoe groot een PSD‑bestand kan de bibliotheek verwerken zonder geheugenproblemen?**  
A: GroupDocs.Metadata streamt data en kan bestanden tot **2 GB** verwerken op een typische machine met 8 GB RAM, dankzij de low‑memory‑architectuur.

## Conclusie
U weet nu **hoe u EXIF**‑metadata uit PSD‑bestanden kunt extraheren met GroupDocs.Metadata voor Java, van basis‑tags tot geavanceerde IFD‑ en GPS‑informatie. Integreer deze fragmenten in uw afbeelding‑verwerkingspipeline om catalogisering, nalevingscontroles of locatie‑gebaseerde services te automatiseren. Voor een diepere verkenning, probeer metadata uit andere ondersteunde formaten (JPEG, TIFF, PNG) te extraheren of experimenteer met de terugschrijf‑mogelijkheden om aangepaste tags in te sluiten.

---

**Laatste update:** 2026-08-10  
**Getest met:** GroupDocs.Metadata 24.12 for Java  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [Afbeeldingsbronnen extraheren uit PSD‑bestanden met GroupDocs.Metadata in Java: Een uitgebreide gids](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [PSD‑header- en laag‑informatie extraheren met GroupDocs.Metadata voor Java: Een uitgebreide gids](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [MakerNote‑eigenschappen extraheren als TIFF/EXIF‑tags met GroupDocs.Metadata in Java](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)