---
date: '2026-08-05'
description: Leer hoe je PDF-versie Java kunt detecteren en PDF-metadata kunt bijwerken
  met GroupDocs.Metadata voor Java. Inclusief versiedetectie, eigenschappen lezen
  en metadata bewerken.
keywords:
- detect pdf version java
- update pdf metadata java
- groupdocs.metadata java
lastmod: '2026-08-05'
og_description: Detecteer PDF-versie Java en werk PDF-metadata bij met GroupDocs.Metadata.
  Stapsgewijze Java-gids toont versiedetectie, eigenschappen lezen en metadata bewerken.
og_image_alt: Guide showing Java code for detecting PDF version and updating metadata
  using GroupDocs.Metadata
og_title: Detecteer PDF-versie Java en werk PDF-metadata bij
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  headline: Detect PDF version java and update PDF metadata
  type: TechArticle
- description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  name: Detect PDF version java and update PDF metadata
  steps:
  - name: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
    text: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
  - name: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
    text: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
  - name: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
    text: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
  - name: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
    text: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
  - name: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
    text: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
  - name: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
    text: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
  - name: '**Report generation** – Insert version information into automatically generated
      reports.'
    text: '**Report generation** – Insert version information into automatically generated
      reports.'
  - name: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
    text: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
  type: HowTo
- questions:
  - answer: Yes, but you must supply the password when creating the `Metadata` object.
    question: Can I update metadata on password‑protected PDFs?
  - answer: Absolutely. You can read and write custom XMP fields through the same
      API.
    question: Does GroupDocs.Metadata support custom XMP properties?
  - answer: The library can report the version; changing it requires saving the document
      with a different version profile, which is supported via additional save options.
    question: Is it possible to change the PDF version itself?
  - answer: The getters will return `null`. You can safely call the setters to create
      new metadata entries.
    question: What happens if the PDF has no existing metadata?
  - answer: A commercial license is required for production deployments; the trial
      is limited to evaluation purposes.
    question: Are there any licensing restrictions for commercial use?
  type: FAQPage
tags:
- detect pdf version
- update pdf metadata
- groupdocs.metadata
- java pdf processing
title: Detecteer PDF-versie Java en werk PDF-metadata bij
type: docs
url: /nl/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# Detecteer PDF-versie java en werk PDF-metadata bij

Het programmatic beheren van PDF‑bestanden betekent vaak dat je **detecteer PDF-versie java** en **werk PDF-metadata bij** — auteur, titel, aanmaakdatum, of zelfs de PDF‑versie zelf. Inconsistente metadata kan renderingsfouten veroorzaken of het moeilijker maken om documenten in een grote repository te vinden. Deze tutorial leidt je door het detecteren van de PDF‑versie en het bijwerken van PDF‑metadata met behulp van **GroupDocs.Metadata** voor Java, en biedt een betrouwbare manier om je PDF’s netjes, doorzoekbaar en compatibel met elke viewer te houden.

## Snelle antwoorden
- **Wat betekent “update PDF metadata”?** Het toevoegen, wijzigen of verwijderen van informatie die in een PDF‑bestand is opgeslagen.  
- **Welke bibliotheek helpt hierbij in Java?** GroupDocs.Metadata.  
- **Kan ik ook de PDF‑versie detecteren?** Ja, dezelfde API biedt versie‑detectie.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor evaluatie; een betaalde licentie is vereist voor productie.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.  

## Wat is het bijwerken van PDF-metadata?

Het bijwerken van PDF‑metadata betekent het programmatisch lezen en schrijven van de beschrijvende informatie die in een PDF‑bestand is ingebed—zoals auteur, titel, onderwerp en aangepaste eigenschappen. Juiste metadata verbetert doorzoekbaarheid, naleving en versiebeheer in documentbeheersystemen. Nauwkeurige metadata maakt ook geautomatiseerde indexering, compliance‑rapportage en versie‑tracking mogelijk in documentbeheersystemen.

## Waarom PDF‑versie detecteren in Java?

Het detecteren van de PDF‑versie stelt je in staat te verifiëren dat een bestand correct wordt weergegeven in de doelviewer en dat het voldoet aan de vereisten voor verdere verwerking. Weten of een PDF versie 1.4, 1.7 of nieuwer is, helpt je compatibiliteitsregels af te dwingen vóór het archiveren, publiceren of converteren van het document.

## Vereisten

- **Java Development Kit (JDK)** 8 of hoger.  
- **Maven** voor afhankelijkheidsbeheer (of je kunt de JAR direct downloaden).  
- Basiskennis van Java bestands‑I/O.  

## GroupDocs.Metadata voor Java instellen

### Maven-configuratie
Voeg de repository en afhankelijkheid toe aan je `pom.xml`:

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
Download anders de nieuwste JAR van de officiële release‑pagina: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Stappen voor het verkrijgen van een licentie
- **Free trial** – begin met experimenteren zonder kosten.  
- **Temporary license** – verleng de proefperiode indien nodig.  
- **Purchase** – verkrijg een volledige licentie voor productiegebruik.  

## Basisinitialisatie en -configuratie

De `Metadata`‑klasse is het toegangspunt voor het werken met PDF‑bestanden in GroupDocs.Metadata. Het vertegenwoordigt een container die je lees‑/schrijftoegang geeft tot documenteigenschappen, versie‑informatie en aangepaste XMP‑gegevens.

Maak een `Metadata`‑instantie die naar je PDF‑bestand wijst:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

Nu ben je klaar om eigenschappen te lezen, de versie te detecteren en metadata bij te werken.

## Hoe PDF‑versie java detecteren

Laad je PDF met `new Metadata("sample.pdf")` en roep `getRootPackage().getVersion()` aan — de methode retourneert de exacte PDF‑versie (bijv. 1.4, 1.7) in één oproep. Dit directe antwoord stelt je in staat om snel de compatibiliteit te valideren vóór verdere verwerking. De versie‑string weerspiegelt het PDF‑specificatieniveau waaraan het bestand voldoet, wat cruciaal is voor compatibiliteitscontroles.  
`getVersion()` retourneert de PDF‑versie als een string, bijv. "1.4" of "1.7".

### Stapsgewijze handleiding

1. **Open the PDF** – instantieer het `Metadata`‑object (zie bovenstaande initialisatie).  
2. **Access the PDF‑specific root package** – roep `metadata.getRootPackage()` aan.  
3. **Retrieve the version** – roep `pdfRoot.getVersion()` aan; de geretourneerde string bevat het versienummer.

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Pro tip:** Gebruik de `version`‑waarde om compatibiliteitscontroles af te dwingen vóór het verwerken van een batch PDF‑bestanden.

#### Probleemoplossing
- Controleer het bestandspad; een onjuist pad veroorzaakt `FileNotFoundException`.  
- Zorg ervoor dat de GroupDocs.Metadata‑versie overeenkomt met je JDK (het voorbeeld gebruikt 24.12).

## Hoe PDF‑eigenschappen lezen in Java

`DocumentInfo` biedt toegang tot standaard PDF‑metadata‑velden zonder het volledige document te laden. De `DocumentInfo`‑klasse biedt toegang tot standaard PDF‑eigenschappen zoals auteur, titel en aanmaakdatum. Het is een lichtgewicht wrapper die metadata leest zonder het hele document in het geheugen te laden.

Maak een `DocumentInfo`‑instantie van het geopende `Metadata`‑object:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

Je kunt vervolgens getters aanroepen zoals `getAuthor()`, `getTitle()` en `getCreationDate()` om waarden op te halen.

## Hoe PDF‑metadata bijwerken in Java

Laad de PDF (zoals hierboven), verkrijg het `DocumentInfo`‑pakket, wijzig de gewenste velden en sla de wijzigingen op. De bewerking overschrijft het bestaande metadata‑blok terwijl de rest van het document behouden blijft. Na het wijzigen van de velden schrijft het aanroepen van `save()` de wijzigingen terug naar het bestand terwijl de content‑streams behouden blijven.

De `DocumentInfo`‑klasse is het object van GroupDocs.Metadata voor het bewerken van PDF‑niveau eigenschappen zoals auteur, titel, onderwerp en aangepaste XMP‑velden.

Werk de metadata‑velden bij:

```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Opmerking:** De setter‑aanroepen volgen hetzelfde patroon als de eerder getoonde getters, waardoor de API intuïtief en consistent is.

#### Veelvoorkomende valkuilen
- Proberen metadata te wijzigen op een PDF die de doel‑eigenschap niet heeft, geeft `null` terug — controleer altijd op `null` voordat je een nieuwe waarde instelt.  
- Grote PDF‑bestanden kunnen extra JVM‑heap vereisen; houd het geheugenverbruik in de gaten tijdens batch‑updates.

## Praktische toepassingsgevallen

1. **Compliance audits** – Verifieer dat alle PDF‑bestanden voldoen aan een minimale versie (bijv. 1.7) vóór juridische indiening.  
2. **Automated archiving** – Label PDF‑bestanden met auteur, afdeling en aanmaakdatum voor eenvoudigere terugvinden.  
3. **Document management integration** – Verrijk PDF‑bestanden met aangepaste eigenschappen die DMS‑platforms kunnen indexeren.  
4. **Report generation** – Voeg versie‑informatie toe aan automatisch gegenereerde rapporten.  
5. **Cross‑platform testing** – Detecteer versie‑verschillen die renderingsproblemen kunnen veroorzaken op oudere viewers.  

## Prestatie‑tips

- **Use try‑with‑resources** (zoals getoond) om `Metadata`‑objecten automatisch te sluiten.  
- **Batch process** meerdere bestanden in een lus om overhead te verminderen.  
- **Monitor heap** voor zeer grote PDF‑bestanden; overweeg ze in delen te verwerken als je geheugenlimieten bereikt.  
- **GroupDocs.Metadata supports 50+ input and output formats** en kan metadata lezen uit PDF‑bestanden van honderden pagina's zonder het volledige bestand in het geheugen te laden, waardoor snelle prestaties op standaard serverhardware worden geleverd.  

## Veelgestelde vragen

**V: Kan ik metadata bijwerken op met wachtwoord beveiligde PDF‑bestanden?**  
**A:** Ja, maar je moet het wachtwoord opgeven bij het aanmaken van het `Metadata`‑object.

**V: Ondersteunt GroupDocs.Metadata aangepaste XMP‑eigenschappen?**  
**A:** Absoluut. Je kunt aangepaste XMP‑velden lezen en schrijven via dezelfde API.

**V: Is het mogelijk om de PDF‑versie zelf te wijzigen?**  
**A:** De bibliotheek kan de versie rapporteren; om deze te wijzigen moet je het document opslaan met een ander versie‑profiel, wat wordt ondersteund via extra opslaan‑opties.

**V: Wat gebeurt er als de PDF geen bestaande metadata heeft?**  
**A:** De getters zullen `null` retourneren. Je kunt veilig de setters aanroepen om nieuwe metadata‑items aan te maken.

**V: Zijn er licentiebeperkingen voor commercieel gebruik?**  
**A:** Een commerciële licentie is vereist voor productie‑implementaties; de proefversie is beperkt tot evaluatiedoeleinden.

---

**Laatst bijgewerkt:** 2026-08-05  
**Getest met:** GroupDocs.Metadata 24.12 for Java  
**Auteur:** GroupDocs

## Gerelateerde tutorials

- [PDF-metadata efficiënt bijwerken met GroupDocs.Metadata in Java voor documentbeheer](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Beheer van metadata masteren: Documenteigenschappen & encryptiestatus detecteren met GroupDocs.Metadata voor Java](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)
- [Documentpreview maken Java – GroupDocs.Metadata tutorials](/metadata/java/document-formats/)