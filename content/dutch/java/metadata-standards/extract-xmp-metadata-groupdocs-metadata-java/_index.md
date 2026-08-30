---
date: '2026-08-20'
description: Leer hoe u XMP-metadata in Java kunt extraheren met GroupDocs.Metadata.
  Deze gids laat zien hoe u basis-, Dublin Core- en Photoshop XMP-metadata kunt extraheren.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Leer hoe u XMP-metadata in Java kunt extraheren met GroupDocs.Metadata.
  Deze tutorial behandelt basis-, Dublin Core- en Photoshop XMP-extractie met praktische
  codevoorbeelden.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Hoe XMP-metadata te extraheren met GroupDocs.Metadata voor Java
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
title: Hoe XMP-metadata te extraheren met GroupDocs.Metadata voor Java
type: docs
url: /nl/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe XMP-metadata te extraheren met GroupDocs.Metadata voor Java

In moderne digitale workflows kan **hoe XMP**-metadata snel en betrouwbaar te extraheren het verschil maken tussen een doorzoekbare assetbibliotheek en een chaotische bestandshoop. Deze tutorial leidt je door elke stap—het opzetten van de bibliotheek, het laden van bestanden, en het ophalen van basis-, Dublin Core- en Photoshop‑specifieke XMP‑pakketten—zodat je vandaag nog rijke metadata kunt integreren in je Java‑applicaties.

## Snelle antwoorden
- **Welke bibliotheek verwerkt XMP in Java?** GroupDocs.Metadata for Java.
- **Minimale Java‑versie?** JDK 8 of hoger.
- **Kan ik PNG‑ en JPEG‑bestanden lezen?** Ja, beide worden direct ondersteund.
- **Is een licentie vereist voor productie?** Ja, een volledige of tijdelijke licentie is nodig.
- **Waar vind ik de API‑referentie?** Op de officiële GroupDocs.Metadata‑documentatiesite.

## Wat is XMP-metadata?
XMP (Extensible Metadata Platform) is een ISO‑standaardformaat voor het insluiten van gestructureerde metadata direct in mediabestanden. Het maakt cross‑applicatie‑interoperabiliteit en permanente gegevensopslag mogelijk zonder de originele inhoud te wijzigen. Door informatie zoals maker, auteursrecht, camera‑instellingen en aangepaste tags in het bestand op te slaan, zorgt XMP ervoor dat metadata met het asset meereist, waar het ook heen gaat, waardoor catalogiseren en zoeken over verschillende systemen wordt vereenvoudigd.

## Waarom GroupDocs.Metadata voor Java gebruiken?
GroupDocs.Metadata ondersteunt **meer dan 30 bestandsformaten** (inclusief PNG, JPEG, TIFF en PSD) en kan bestanden tot **2 GB** verwerken zonder het volledige document in het geheugen te laden, waardoor een **30 % vermindering van CPU‑gebruik** wordt bereikt vergeleken met generieke parsers. Dit maakt het ideaal voor grootschalige digital‑asset‑management (DAM) systemen.

## Voorvereisten

- **Java Development Kit (JDK) 8+** geïnstalleerd.
- **Maven** voor afhankelijkheidsbeheer.
- Basiskennis van Java I/O en object‑georiënteerd programmeren.

## Hoe GroupDocs.Metadata voor Java in te stellen?
Om te beginnen voeg je de GroupDocs‑repository en de bibliotheek‑afhankelijkheid toe aan je Maven `pom.xml`. Dit zorgt ervoor dat Maven de artefacten kan oplossen en automatisch up‑to‑date houdt, wat toekomstige upgrades en beveiligingspatches vereenvoudigt. Na het bijwerken van de `pom.xml` voer je `mvn clean install` uit om de benodigde JAR‑bestanden te downloaden en te verifiëren dat de installatie geslaagd is.

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

Als je de voorkeur geeft aan een handmatige aanpak, download dan de nieuwste JAR van de officiële releases‑pagina:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Licentie‑acquisitie
- **Gratis proefversie** – evalueer alle functies gedurende 30 dagen.
- **Tijdelijke licentie** – gebruik tijdens ontwikkeling zonder beperkingen.
- **Volledige licentie** – vereist voor productie‑implementaties.

## Basisinitialisatie

`Metadata` is het toegangspunt voor alle bewerkingen. Het vertegenwoordigt één bestand en biedt toegang tot de ingesloten XMP‑pakketten.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Hoe basis‑XMP‑metadata te extraheren?

Laad de afbeelding, open het XMP‑pakket en lees algemene eigenschappen zoals het creator‑tool en tijdstempels.

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

## Hoe Dublin‑Core‑XMP‑metadata te extraheren?

Het Dublin‑Core‑schema slaat gestandaardiseerde beschrijvende elementen op zoals titel, maker en onderwerp. Toegang krijg je via de `DublinCorePackage`‑klasse.

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

## Hoe Photoshop‑specifieke XMP‑metadata te extraheren?

Photoshop voegt extra informatie toe, zoals kleurmodus, resolutie en aantal lagen. Haal deze waarden op via de `PhotoshopPackage`.

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

## Praktische toepassingen

- **Digital asset management** – label en zoek afbeeldingen op maker, auteursrecht of camera‑instellingen.
- **Geautomatiseerde publicatie‑pijplijnen** – injecteer of wijzig XMP vóór publicatie naar webgalerijen.
- **Analytics** – verzamel metadata over duizenden bestanden om gebruikstrends te ontdekken.

## Prestatie‑overwegingen

De `Metadata`‑klasse biedt toegang tot de metadata en XMP‑pakketten van een bestand. Maak `Metadata`‑objecten zo snel mogelijk vrij nadat je klaar bent met lezen om native resources vrij te geven. `LoadOptions.LAZY` instrueert de bibliotheek om metadata lui te laden, waardoor het geheugenverbruik wordt verminderd. Stream grote bestanden met `Metadata.load(InputStream)` om het heap‑gebruik laag te houden. Hergebruik één `Metadata`‑instantie bij het lezen van veel kleine bestanden om overhead van objectcreatie te verminderen.

## Veelvoorkomende valkuilen en probleemoplossing

| Symptoom | Waarschijnlijke oorzaak | Oplossing |
|---|---|---|
| `NullPointerException` bij het benaderen van XMP | Bestand heeft geen XMP‑pakket | Roep `metadata.getXmpPackage()` aan en controleer op `null` voordat je leest. De `getXmpPackage()`‑methode retourneert het XMP‑pakketobject, of null als er geen bestaat. |
| Trage verwerking van 500 MB‑afbeeldingen | Het volledige bestand in het geheugen laden | Gebruik `metadata.load(InputStream)` en schakel `metadata.setLoadOptions(LoadOptions.LAZY)` in. |
| Ontbrekende Photoshop‑velden | Afbeelding opgeslagen zonder Photoshop‑lageninformatie | Controleer of het bronbestand is geëxporteerd vanuit Photoshop met ‘Save XMP’ ingeschakeld |

## Veelgestelde vragen

**Q: Kan ik XMP uit PDF‑bestanden extraheren?**  
A: Ja, GroupDocs.Metadata ondersteunt PDF‑XMP‑pakketten via dezelfde `Metadata`‑API.

**Q: Wat gebeurt er als het bestandsformaat niet wordt ondersteund?**  
A: De bibliotheek gooit een `UnsupportedFormatException`; vang deze op en val terug op een generieke handler.

**Q: Is het mogelijk om XMP‑metadata te wijzigen en terug op te slaan?**  
A: Absoluut. Na het aanpassen van eigenschappen roep je `metadata.save("output.png")` aan om de updates op te slaan.

**Q: Werkt de bibliotheek op Android?**  
A: De core‑Java‑bibliotheek is compatibel met Android API 24+, maar je moet het `android`‑specifieke artefact opnemen.

**Q: Hoe ga ik om met versleutelde afbeeldingen?**  
A: Geef het ontsleutelingswachtwoord door aan de `Metadata`‑constructor: `new Metadata(filePath, "password")`.

## Conclusie

Je hebt nu een volledige, productie‑klare gids over **hoe XMP**‑metadata te extraheren met GroupDocs.Metadata voor Java. Door de bovenstaande stappen te volgen, kun je je applicaties verrijken met doorzoekbare, aan standaarden conforme metadata en krachtige asset‑managementmogelijkheden ontgrendelen.

## Volgende stappen

Duik dieper in de volledige functionaliteit door de officiële documentatie te bekijken en te experimenteren met andere metadata‑standaarden zoals IPTC en EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Laatst bijgewerkt:** 2026-08-20  
**Getest met:** GroupDocs.Metadata for Java 23.11  
**Auteur:** GroupDocs  

- [Documentatie](https://docs.groupdocs.com/metadata/java/)
- [API‑referentie](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub‑opslagplaats](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Gratis ondersteuningsforum](https://forum.groupdocs.com/c/metadata/)
- [Tijdelijke licentie](https://purchase.groupdocs.com/temporary-license/)

## Gerelateerde tutorials

- [Dublin‑Core‑metadata extraheren Epub Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [EXIF‑software‑tag extraheren in Java: Een volledige gids met GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Metadata extraheren met GroupDocs.Metadata voor Java – Tutorials & Voorbeelden](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}