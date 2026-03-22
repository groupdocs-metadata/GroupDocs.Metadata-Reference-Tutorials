---
date: '2026-02-03'
description: Leer hoe u de GroupDocs Maven‑dependency kunt gebruiken om PowerPoint‑metadata
  bij te werken, inclusief hoe u de aanmaakdatum van een PPTX kunt wijzigen, met Java.
keywords:
- update PowerPoint metadata Java
- GroupDocs.Metadata Java library
- presentation metadata management
title: PowerPoint-metadata bijwerken met GroupDocs Maven-afhankelijkheid
type: docs
url: /nl/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Hoe presentatiemetadata bijwerken met GroupDocs.Metadata Java

In moderne documentwerkstromen is het nauwkeurig houden van metadata een must‑have. Door gebruik te maken van de **groupdocs Maven dependency**, kun je programmatisch ingebouwde eigenschappen van een PowerPoint‑bestand bijwerken—zoals auteur, bedrijf, en zelfs de **wijziging van de PPTX‑creatiedatum**—direct vanuit Java. Deze tutorial leidt je door het volledige proces, van Maven‑configuratie tot het opslaan van de bijgewerkte presentatie.

## Snelle antwoorden
- **Welke bibliotheek laat me PowerPoint‑metadata bewerken in Java?** GroupDocs.Metadata Java via de groupdocs Maven dependency.  
- **Kan ik de PPTX‑creatiedatum wijzigen?** Ja—stel simpelweg de `CreatedTime`‑eigenschap in.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor evaluatie; een commerciële licentie is vereist voor productie.  
- **Welke build‑tool wordt ondersteund?** Maven (hieronder getoond) of handmatige JAR‑download.  
- **Is de code compatibel met Java 8+?** Absoluut—GroupDocs.Metadata richt zich op Java 8 en nieuwer.

## Wat is de GroupDocs Maven Dependency?
De **groupdocs Maven dependency** is een Maven‑compatibel repository‑item dat de nieuwste GroupDocs.Metadata‑bibliotheek in je Java‑project haalt. Het vereenvoudigt afhankelijkheidsbeheer en zorgt ervoor dat je altijd de meest recente, veilige versie hebt.

## Waarom GroupDocs.Metadata gebruiken om de PPTX‑creatiedatum te wijzigen?
- **Gecentraliseerde controle:** Werk veel presentaties bij in een batch‑taak.  
- **Naleving:** Houd creatietijdstempels in overeenstemming met je document‑beheerbeleid.  
- **Geen UI vereist:** Automatiseer metadata‑wijzigingen tijdens CI/CD‑pijplijnen of content‑migraties.

## Vereisten
- Java 8 of hoger geïnstalleerd.  
- Een IDE zoals IntelliJ IDEA of Eclipse.  
- Maven voor afhankelijkheidsbeheer.  
- Toegang tot een GroupDocs‑proefversie of aangeschafte licentie.

## De GroupDocs Maven Dependency gebruiken in je Java‑project

### Maven‑configuratie
Voeg de GroupDocs‑repository en de metadata‑afhankelijkheid toe aan je `pom.xml`:

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

> **Pro tip:** Het up‑to‑date houden van het versienummer zorgt ervoor dat je profiteert van de nieuwste bug‑fixes en prestatie‑verbeteringen.

### Directe download (als je liever geen Maven gebruikt)
Download anders de nieuwste JAR van [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Licentie‑acquisitie
Begin met een gratis proefversie of vraag een tijdelijke licentie aan om GroupDocs.Metadata te evalueren. Voor productie‑gebruik koop je een licentie via [GroupDocs' officiële website](https://purchase.groupdocs.com/temporary-license/).

## Basisinitialisatie en configuratie
Zodra de bibliotheek op het classpath staat, kun je een `Metadata`‑instantie maken die naar je PowerPoint‑bestand wijst:

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

Deze code opent de presentatie in een try‑with‑resources‑blok, waardoor de bestands‑handle automatisch wordt vrijgegeven.

## Stapsgewijze gids om ingebouwde metadata bij te werken

### Stap 1: Laad het presentatiedocument
Het laden van het bestand legt een verbinding tot stand waarmee je metadata kunt lezen of schrijven.

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

### Stap 2: Toegang tot het root‑pakket van de presentatie
Het `root`‑object geeft toegang tot alle ingebouwde documenteigenschappen.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

### Stap 3: Werk ingebouwde documenteigenschappen bij (inclusief creatiedatum)
Hier demonstreren we hoe je de **PPTX‑creatiedatum wijzigt** door een nieuw `Date`‑object toe te wijzen aan `CreatedTime`. Je kunt `new Date()` vervangen door een specifieke tijdstempel die je nodig hebt.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

### Stap 4: Sla de bijgewerkte presentatie op
De `save`‑aanroep schrijft de gewijzigde metadata terug naar een nieuw PowerPoint‑bestand, waarbij het origineel onaangeroerd blijft.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

## Probleemoplossingstips
- **Bestand niet gevonden:** Controleer het invoerpad en de bestandsrechten.  
- **Versie‑mismatch:** Zorg ervoor dat de `groupdocs-metadata`‑versie overeenkomt met je Java‑runtime.  
- **Eigenschap wordt niet bijgewerkt:** Controleer of je `setCreatedTime` (of de relevante setter) aanroept vóór `save`.

## Praktische toepassingen
1. **Corporate branding:** Automatisch de juiste bedrijfsnaam en categorie in alle slide‑decks injecteren vóór distributie.  
2. **Documentbeheersystemen:** Verrijk PPTX‑bestanden met doorzoekbare metadata voor snellere terugwinning.  
3. **Educatieve bronnen:** Houd auteur‑ en curriculum‑informatie up‑to‑date in alle lezing‑slides.  
4. **Samenwerkings‑tracking:** Registreer namen van bijdragers om verantwoordelijkheid te behouden.  
5. **CMS‑integratie:** Synchroniseer metadata‑wijzigingen met je content‑managementplatform in realtime.

## Prestatie‑overwegingen
- **Batch‑verwerking:** Loop over een lijst met bestanden en hergebruik waar mogelijk een enkele `Metadata`‑instantie.  
- **- **Efficiënte datastructuren:** Sla metadata‑updates op in een map voordat je ze toepast om herhaalde aanroepen te?** nieuwsteprojecten.

**Q: Hoe kan ik de PPTX‑creatiedatum wijzigen zonder andere eigenschappen te beïnvloeden?**  
A: Gebruik `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` vóór Een tijdelijke proeflicentie is voldoende voor ontwikkeling en testen; een volledige licentie is vereist voor productie.

**Q: Kan ik ook aangepaste metadata‑velden bijwerken?**  
A: Ja—GroupDocs.Metadata ondersteunt zowel ingebouwde als aangepaste eigenschappen via de API.

**Q: Is er een manier om wijzigingen ongedaan te maken als ik een fout maak?** bestand bij of lees de bestaande eigenschapswaarden voordat je ze overschrijft, en herstel ze indien nodig.

## Resources
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://apireference.groupdocs.com/metadata/java/)

---

**Laatst bijgewerkt:** 2026-02-03  
**Getest met:** GroupDocs.Metadata 24.12 voor Java  
**Auteur:** GroupDocs  

---