---
date: '2026-03-25'
description: Leer hoe u de aanmaakdatum in Java kunt ophalen en documentmetadata kunt
  extraheren met GroupDocs.Metadata voor Java. Deze gids behandelt de installatie,
  het lezen van eigenschappen en praktische toepassingen.
keywords:
- access word document metadata
- groupdocs.metadata java
- read word metadata properties
title: ophalen van aanmaaktijd Java uit Word‑documenten met GroupDocs
type: docs
url: /nl/java/document-formats/access-word-metadata-groupdocs-java/
weight: 1
---

# retrieve created time java van Word-documenten met GroupDocs

## Hoe metadata‑eigenschappen van een Word‑document te extraheren en te manipuleren met GroupDocs.Metadata Java

### Introductie

Zoek je naar **retrieve created time java** of wil je **java extract document metadata** uit je Word‑bestanden halen? Het kennen van de metadata die in een document is ingebed is essentieel voor audit, compliance en intelligente content‑beheer. In deze tutorial lopen we stap voor stap door het opzetten van GroupDocs.Metadata, het lezen van ingebouwde eigenschappen (inclusief de Created Time) en het toepassen van die informatie in real‑world scenario’s.

Hieronder vind je alles wat je nodig hebt om aan de slag te gaan — voorkeuren, Maven‑configuratie, code‑fragmenten en foutoplossingstips — alles geschreven in een vriendelijke, stap‑voor‑stap stijl.

## Snelle antwoorden
- **Wat betekent “retrieve created time java”?** Het is het proces van het uitlezen van de aanmaak‑tijdstempel van een document met Java‑code.  
- **Welke bibliotheek regelt dit?** GroupDocs.Metadata voor Java biedt een eenvoudige API voor het benaderen van Word‑metadata.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor evaluatie; een volledige licentie is vereist voor productie.  
- **Kan ik tegelijk andere eigenschappen lezen?** Ja — author, company, keywords en meer zijn beschikbaar via dezelfde API.  
- **Is deze aanpak performant?** Ja, vooral wanneer je try‑with‑resources gebruikt om geheugen efficiënt te beheren.

## Voorvereisten

Voordat we de implementatie induiken, zorg dat je het volgende hebt:

- **JDK** (Java Development Kit) geïnstalleerd op je machine.  
- **Maven** (of een ander build‑tool) om afhankelijkheden te beheren.  
- Basiskennis van Java en een IDE zoals IntelliJ IDEA of Eclipse.  

### Vereiste bibliotheken en afhankelijkheden

Om met GroupDocs.Metadata te werken, voeg je de repository en afhankelijkheid toe in je `pom.xml`‑bestand:

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

Of download je de nieuwste versie direct vanaf [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Omgevings‑setup vereisten

- **JDK** (Java 8 of hoger)  
- **Maven** (als je liever handmatig JAR‑bestanden beheert, zie de sectie Direct Download hieronder)  

### Kennis‑voorvereisten

- Basis Java‑syntaxis en object‑georiënteerde concepten.  
- Begrip van hoe je afhankelijkheden toevoegt aan een Maven‑project.  

## GroupDocs.Metadata voor Java instellen

### Maven‑setup

Als je Maven gebruikt, haalt het bovenstaande fragment de bibliotheek automatisch op.

### Directe download

Voor niet‑Maven projecten, bezoek [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) om de JAR te verkrijgen en voeg deze toe aan je project‑build‑path.

### Licentie‑acquisitie

1. **Free Trial** – Download een proefversie van de officiële site.  
2. **Temporary License** – Vraag een tijdelijke sleutel aan voor uitgebreide evaluatie.  
3. **Full License** – Schaf een commerciële licentie aan voor productie‑implementaties.

### Basisinitialisatie

Zodra de bibliotheek beschikbaar is, kun je de `Metadata`‑klasse instantieren:

```java
import com.groupdocs.metadata.*;

// Initialize the Metadata class with the path to your document
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your-document.docx")) {
    // Your code here to work with metadata
}
```

## Implementatie‑gids

### Documenteigenschappen benaderen

#### Stap 1: Laad het Word‑document

```java
// Load the Word document from a specified path
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/your-document.docx")) {
    // Proceed with accessing properties
}
```

#### Stap 2: Benader het root‑package

```java
// Get the root package for Word Processing documents
WordProcessingRootPackage root = metadata.getRootPackageGeneric();
```

#### Stap 3: Lees en bewerk ingebouwde documenteigenschappen

```java
// Retrieve built-in properties
String author = root.getDocumentProperties().getAuthor();
java.util.Date createdTime = root.getDocumentProperties().getCreatedTime();
String company = root.getDocumentProperties().getCompany();
String category = root.getDocumentProperties().getCategory();
String keywords = root.getDocumentProperties().getKeywords();

// Print the retrieved properties
System.out.println("Author: " + author);
System.out.println("Created Time: " + createdTime);
System.out.println("Company: " + company);
System.out.println("Category: " + category);
System.out.println("Keywords: " + keywords);
```

De aanroep `getCreatedTime()` is precies wat je nodig hebt om **retrieve created time java** uit te voeren. Je kunt deze tijdstempel nu opslaan, weergeven of verwerken zoals je applicatie vereist.

### Foutoplossingstips

- **Documentpad** – Controleer het bestandspad; relatieve paden worden opgelost vanaf de project‑root.  
- **Bibliotheekversie** – Zorg dat de GroupDocs.Metadata‑versie overeenkomt met je JDK‑niveau.  
- **Exception‑handling** – Plaats aanroepen in try‑catch‑blokken om `FileNotFoundException`, `MetadataException`, enz. netjes af te handelen.  

## Praktische toepassingen

Het begrijpen en benaderen van metadata opent de deur naar vele scenario’s:

1. **Document‑audit** – Verifieer wie een bestand heeft aangemaakt en wanneer, ter voldoening van compliance‑controles.  
2. **Organisatorische tagging** – Gebruik categorieën en keywords om zoeken en classificatie in een DMS te stimuleren.  
3. **Integratie** – Stroom metadata in workflow‑engines of content‑management‑API’s voor rijkere automatisering.  

## Prestatie‑overwegingen

- Gebruik **try‑with‑resources** (zoals getoond) om `Metadata`‑objecten automatisch te sluiten en native resources vrij te geven.  
- Verwerk documenten in batches alleen indien nodig, om het geheugenverbruik voorspelbaar te houden.  

## Conclusie

Je beschikt nu over een solide, productie‑klare methode om **retrieve created time java** en andere metadata uit Word‑documenten te halen met GroupDocs.Metadata. Deze mogelijkheid stelt je in staat audit‑trails te bouwen, zoeken te verbeteren en document‑eigenschappen te integreren in bredere bedrijfsprocessen.

### Volgende stappen

- Experimenteer met het bijwerken van metadata (bijv. `setAuthor`, `setKeywords`).  
- Verken de volledige API voor aangepaste eigenschappen en geavanceerde manipulatie.  
- Raadpleeg de officiële documentatie voor diepgaandere voorbeelden.

### FAQ‑sectie

1. **Wat is GroupDocs.Metadata?**  
   - Een Java‑bibliotheek die manipulatie en uitlezing van document‑metadata mogelijk maakt voor diverse formaten.  
2. **Hoe begin ik met GroupDocs.Metadata in mijn project?**  
   - Stel Maven in of download de JAR, en voeg de afhankelijkheid toe zoals hierboven getoond.  
3. **Kan ik GroupDocs.Metadata gratis gebruiken?**  
   - Ja, er is een proefversie beschikbaar; een tijdelijke licentie ontgrendelt geavanceerde functies.  
4. **Wat zijn veelvoorkomende fouten bij het gebruik van deze bibliotheek?**  
   - Onjuiste documentpaden en niet‑overeenkomende bibliotheekversies komen het vaakst voor.  
5. **Hoe kan ik de prestaties optimaliseren bij het werken met metadata in Java?**  
   - Volg best practices voor geheugenbeheer, gebruik try‑with‑resources, en vermijd onnodig grote documenten te laden.  

## Veelgestelde vragen

**Q: Ondersteunt GroupDocs.Metadata andere bestandsformaten naast Word?**  
A: Ja, het werkt met PDF, Excel, PowerPoint en vele andere formaten.

**Q: Kan ik metadata bewerken nadat ik het heb opgehaald?**  
A: Absoluut. De API biedt setter‑methoden zoals `setAuthor` en `setCreatedTime`.

**Q: Is er een manier om metadata volledig te verwijderen?**  
A: Je kunt individuele eigenschappen wissen of de methode `removeAllProperties` gebruiken om alle metadata te wissen.

**Q: Hoe ga ik om met wachtwoord‑beveiligde documenten?**  
A: Geef het wachtwoord door aan de `Metadata`‑constructor‑overload die een `LoadOptions`‑object accepteert.

**Q: Waar vind ik meer code‑voorbeelden?**  
A: De officiële documentatie en de GitHub‑repository bevatten uitgebreide voorbeelden.

### Resources
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download GroupDocs.Metadata for Java](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata)

---

**Last Updated:** 2026-03-25  
**Tested With:** GroupDocs.Metadata 24.12  
**Author:** GroupDocs