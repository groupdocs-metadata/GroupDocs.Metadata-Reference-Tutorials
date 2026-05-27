---
date: '2026-05-27'
description: Leer hoe je pptx CreatedTime in Java kunt instellen met de GroupDocs
  Maven dependency om PowerPoint-metadata bij te werken, inclusief hoe je de creatiedatum
  van PPTX kunt wijzigen.
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
title: Stel PPTX CreatedTime in Java in met GroupDocs Maven Dependency
type: docs
url: /nl/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Stel PPTX CreatedTime in Java in met GroupDocs.Metadata

Nauwkeurige metadata is essentieel voor naleving en vindbaarheid in moderne documentworkflows. Met **GroupDocs.Metadata** kun je programmatisch **PPTX CreatedTime in Java instellen**, waardoor je **de creatiedatum van PPTX kunt wijzigen** naast andere ingebouwde eigenschappen zoals auteur of bedrijf. Deze tutorial leidt je door Maven‑configuratie, het initialiseren van de API, het bijwerken van metadata en het opslaan van de gewijzigde presentatie — allemaal met duidelijke, productie‑klare code.

## Snelle Antwoorden
- **Welke bibliotheek werkt PowerPoint-metadata bij in Java?** GroupDocs.Metadata via de GroupDocs Maven‑dependency.  
- **Kan ik de PPTX CreatedTime‑eigenschap instellen?** Ja — gebruik `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Is een licentie vereist voor productie?** Een proefversie werkt voor evaluatie; een commerciële licentie is verplicht voor productie‑implementaties.  
- **Welke build‑tool gebruikt het voorbeeld?** Maven (je kunt de JAR ook handmatig downloaden).  
- **Ondersteunt de API Java 8 en nieuwer?** Absoluut — GroupDocs.Metadata richt zich op Java 8+.

## Wat is de GroupDocs Maven‑dependency?
De **GroupDocs Maven‑dependency** is een Maven‑compatibel repository‑item dat de nieuwste GroupDocs.Metadata‑bibliotheek in je Java‑project haalt. Het vereenvoudigt het beheer van afhankelijkheden door automatisch transitieve bibliotheken op te lossen, garandeert dat je altijd de meest recente en veilige versie gebruikt, en elimineert de noodzaak van handmatige JAR‑downloads of versie‑tracking.

## Waarom GroupDocs.Metadata gebruiken om de PPTX‑creatiedatum te wijzigen?
GroupDocs.Metadata maakt geautomatiseerde, batch‑klare updates van PPTX‑creatietijdstempels mogelijk, waardoor elke presentatie voldoet aan bedrijfsbeleid of wettelijke vereisten. Door programmatisch de CreatedTime‑eigenschap in te stellen, vermijd je handmatige bewerking, verminder je menselijke fouten, en kun je de wijziging integreren in CI/CD‑pipelines of migratiescripts voor naadloos documentbeheer.

## Voorvereisten
- Java 8 of hoger geïnstalleerd.  
- Een IDE zoals IntelliJ IDEA of Eclipse.  
- Maven voor afhankelijkheidsbeheer.  
- Toegang tot een GroupDocs‑proefversie of aangeschafte licentie.

## Hoe PPTX CreatedTime in Java in te stellen?
De `Metadata`‑klasse vertegenwoordigt een document en biedt toegang tot de metadata‑eigenschappen.

Laad je PowerPoint‑bestand met `new Metadata("presentation.pptx")`, haal het root‑pakket op, roep `setCreatedTime` aan met de gewenste `java.util.Date`, en roep tenslotte `save` aan om de wijzigingen weg te schrijven. Deze end‑to‑end‑stroom wijzigt de creatiedatum terwijl alle dia‑inhoud en andere eigenschappen behouden blijven.

### Maven‑configuratie
Add the GroupDocs repository and the metadata dependency to your `pom.xml`:

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

> **Pro tip:** Het up‑to‑date houden van het versienummer zorgt ervoor dat je profiteert van de nieuwste bugfixes en prestatieverbeteringen.

### Directe download (als je liever geen Maven gebruikt)
Alternatively, download the latest JAR from [GroupDocs.Metadata voor Java releases](https://releases.groupdocs.com/metadata/java/).

#### Licentie‑acquisitie
Begin met een gratis proefversie of vraag een tijdelijke licentie aan om GroupDocs.Metadata te evalueren. Voor productie‑gebruik koop je een licentie via [de officiële website van GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Basisinitialisatie en configuratie
Once the library is on the classpath, you can create a `Metadata` instance that points to your PowerPoint file:

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

## Stapsgewijze handleiding om ingebouwde metadata bij te werken
### Stap 1: Laad het presentatiedocument
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Het laden van het bestand legt een verbinding tot stand die je in staat stelt metadata te lezen of te schrijven.

### Stap 2: Toegang tot het root‑pakket van de presentatie
Het `root`‑object geeft toegang tot het kernpakket van de presentatie en de ingebouwde eigenschappen.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

Het `root`‑object maakt alle ingebouwde documenteigenschappen zichtbaar.

### Stap 3: Werk ingebouwde documenteigenschappen bij (inclusief datum van creatie)
`setCreatedTime` kent een nieuwe creatietijdstempel toe aan het document.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Hier laten we zien hoe je **PPTX CreatedTime** instelt door een nieuw `Date`‑object toe te wijzen aan `CreatedTime`. Vervang `new Date()` door een specifieke tijdstempel die je nodig hebt.

### Stap 4: Sla de bijgewerkte presentatie op
`save` schrijft de gewijzigde metadata terug naar een bestand.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

De `save`‑aanroep schrijft de gewijzigde metadata terug naar een nieuw PowerPoint‑bestand, waarbij het origineel onaangeroerd blijft.

## Probleemoplossingstips
- **Bestand niet gevonden:** Controleer het invoerpad en de bestandsrechten.  
- **Versie‑mismatch:** Zorg ervoor dat de `groupdocs-metadata`‑versie overeenkomt met je Java‑runtime.  
- **Eigenschap wordt niet bijgewerkt:** Controleer of je `setCreatedTime` (of de relevante setter) aanroept vóór het uitvoeren van `save`.

## Praktische toepassingen
1. **Corporate branding:** Automatisch de juiste bedrijfsnaam en categorie in alle presentaties injecteren vóór distributie.  
2. **Documentbeheersystemen:** PPTX‑bestanden verrijken met doorzoekbare metadata voor snellere terugwinning.  
3. **Educatieve bronnen:** Auteur‑ en curriculum‑informatie up‑to‑date houden in college‑dia's.  
4. **Samenwerkings‑tracking:** Namen van bijdragers vastleggen om verantwoordelijkheid te behouden.  
5. **CMS‑integratie:** Metadata‑wijzigingen in realtime synchroniseren met je content‑managementplatform.

## Prestatie‑overwegingen
- **Batchverwerking:** Loop over een lijst met bestanden en hergebruik waar mogelijk een enkele `Metadata`‑instantie.  
- **Geheugenbeheer:** Gebruik altijd try‑with‑resources (zoals getoond) om native resources snel vrij te geven.  
- **Efficiënte datastructuren:** Sla metadata‑updates op in een map voordat je ze toepast om herhaalde aanroepen te verminderen.

## Veelgestelde vragen
**Q: Wat is het primaire doel van de GroupDocs Maven‑dependency?**  
A: Het biedt een handige manier om de nieuwste GroupDocs.Metadata‑bibliotheek op te nemen in Maven‑gebaseerde Java‑projecten.

**Q: Hoe kan ik de PPTX‑creatiedatum instellen zonder andere eigenschappen te beïnvloeden?**  
A: Gebruik `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` vóór het aanroepen van `metadata.save()`.

**Q: Heb ik een licentie nodig om deze code in ontwikkeling uit te voeren?**  
A: Een tijdelijke proeflicentie is voldoende voor ontwikkeling en testen; een volledige licentie is vereist voor productie.

**Q: Kan ik ook aangepaste metadata‑velden bijwerken?**  
A: Ja — GroupDocs.Metadata ondersteunt zowel ingebouwde als aangepaste eigenschappen via de API.

**Q: Is er een manier om wijzigingen ongedaan te maken als ik een fout maak?**  
A: Bewaar een kopie van het originele bestand of lees de bestaande eigenschapswaarden voordat je ze overschrijft, en herstel ze indien nodig.

## Bronnen
- [Documentatie](https://docs.groupdocs.com/metadata/java/)
- [API‑referentie](https://apireference.groupdocs.com/metadata/java/)

---

**Laatst bijgewerkt:** 2026-05-27  
**Getest met:** GroupDocs.Metadata 24.12 for Java  
**Auteur:** GroupDocs  

## Gerelateerde tutorials
- [Aangepaste metadata bijwerken in PowerPoint met GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Hoe Word-documentmetadata bij te werken met GroupDocs.Metadata Java: Een volledige gids](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [PDF-metadata efficiënt bijwerken met GroupDocs.Metadata in Java voor documentbeheer](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)