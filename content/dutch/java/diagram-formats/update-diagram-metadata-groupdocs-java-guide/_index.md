---
date: '2026-06-17'
description: Leer hoe u de creatietijd van een diagram kunt wijzigen en de metadata-update
  voor diagrambestanden kunt automatiseren met GroupDocs.Metadata in Java.
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
title: Diagram creatietijd wijzigen in metadata met GroupDocs Java
type: docs
url: /nl/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Diagram creatietijd wijzigen in metadata met GroupDocs Java

In deze stapsgewijze tutorial ontdek je hoe je **diagram creatietijd** kunt wijzigen en andere ingebouwde eigenschappen van diagrambestanden kunt bijwerken met behulp van de GroupDocs.Metadata bibliotheek voor Java. Het automatiseren van deze wijzigingen bespaart uren handmatig bewerken, garandeert consistente tijdstempels in je repository, en maakt je diagrammen direct doorzoekbaar in elk document‑managementsysteem.

## Snelle antwoorden
- **Wat is het primaire doel?** Diagram creatietijd wijzigen en andere metadata in diagrambestanden bijwerken.  
- **Welke bibliotheek moet ik gebruiken?** GroupDocs.Metadata for Java.  
- **Heb ik een licentie nodig?** Een gratis proefversie is voldoende voor testen; een volledige licentie is vereist voor productie.  
- **Kan ik veel diagrammen batch‑verwerken?** Ja—pak dezelfde logica in een lus of een parallelle stream.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.

## Wat betekent “diagram creatietijd wijzigen” in diagrammetadata?
Het wijzigen van de creatietijd overschrijft de oorspronkelijke tijdstempel die in een diagrambestand (zoals VDX of VSDX) is opgeslagen met een nieuwe datum‑tijdwaarde. Hierdoor kun je de metadata van het bestand afstemmen op de werkelijke verwerkings‑ of archiveringsdatum in plaats van de oorspronkelijke tijdstempel van de auteur, wat essentieel is voor audit‑trails en nauwkeurige zoekresultaten.

## Waarom metadata‑updates voor diagrammen automatiseren?
Het automatiseren van metadata zorgt ervoor dat elk diagram dezelfde naamgevings‑, categorisatie‑ en tijdstempelstandaarden volgt zonder menselijke fouten. Het versnelt ook bulk‑migraties, vermindert compliance‑risico's en verbetert de vindbaarheid in enterprise DMS‑platforms—en bespaart tot 70 % van de handmatige inspanning in grootschalige projecten.

## Voorvereisten
- **Java Development Kit (JDK) 8+** geïnstalleerd op je machine.  
- **IDE** zoals IntelliJ IDEA of Eclipse.  
- **Maven** (of handmatige JAR‑afhandeling) voor afhankelijkheidsbeheer.  
- Basiskennis van Java‑klassen, methoden en exception‑handling.

### Vereiste bibliotheken en afhankelijkheden
Voeg de volgende repository en afhankelijkheid toe aan je `pom.xml`‑bestand als je Maven gebruikt:

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
Als je liever direct downloadt, bezoek dan [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) om de nieuwste versie te krijgen.

### Omgevingsconfiguratie
- JDK 8 of nieuwer.  
- IntelliJ IDEA, Eclipse, of een andere Java‑compatibele IDE.  

### Kennisvoorvereisten
Begrip van Java‑syntaxis en basis bestands‑I/O maakt de tutorial soepeler, maar de stappen worden in eenvoudige taal uitgelegd.

## GroupDocs.Metadata voor Java instellen
### Installatie‑instructies
**Maven‑gebruikers:** Het bovenstaande fragment voegt de repository en de vereiste JAR automatisch toe.  
**Direct‑download‑gebruikers:** Na het downloaden van de JAR van [GroupDocs](https://releases.groupdocs.com/metadata/java/), voeg je deze toe aan de classpath van je project.

### Licentie‑verwerving
- **Gratis proefversie:** Verken de bibliotheek zonder kosten.  
- **Tijdelijke licentie:** Verkrijg een tijdelijke licentie voor uitgebreid testen [hier](https://purchase.groupdocs.com/temporary-license/).  
- **Aankoop:** Verkrijg een volledige licentie voor productieomgevingen.

### Basisinitialisatie
`Metadata` is de kernklasse die een metadata‑container van een document vertegenwoordigt en lees‑/schrijftoegang biedt tot alle ingebouwde eigenschappen. Om GroupDocs.Metadata te gebruiken, importeer je de klasse en open je een diagrambestand:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Met de bibliotheek geïnitieerd kun je nu elke ingebouwde eigenschap wijzigen, inclusief de creatietijd.

## Implementatie‑gids
### Hoe de creatietijd in diagrambestanden te wijzigen
In deze sectie lopen we stap voor stap door wat nodig is om **diagram creatietijd** te wijzigen en andere veelvoorkomende eigenschappen zoals auteur, bedrijf en categorie bij te werken. Het proces omvat het laden van het diagram met de Metadata‑API, toegang tot het root‑pakket, het instellen van de gewenste velden, en tenslotte het opslaan van de wijzigingen naar een nieuw bestand, zodat het origineel onaangeroerd blijft.

#### Stap 1: Laad het diagramdocument
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```  
*Uitleg:* De `Metadata`‑constructor ontvangt het pad naar je diagrambestand. Het try‑with‑resources‑blok zorgt ervoor dat het bestand correct wordt gesloten na de bewerking.

#### Stap 2: Toegang tot het root‑pakket
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```  
*Uitleg:* Het root‑pakket geeft je directe toegang tot alle ingebouwde metadata‑velden voor het diagram.

#### Stap 3: Stel de maker‑eigenschap in
```java
root.getDocumentProperties().setCreator("test author");
```  
*Uitleg:* Wijs een nieuwe auteursnaam toe. Vervang `"test author"` door de daadwerkelijke maker.

#### Stap 4: Wijzig de creatietijd
```java
root.getDocumentProperties().setTimeCreated(new Date());
```  
*Uitleg:* Deze regel **wijzigt de creatietijd** naar de huidige systeemdatum en -tijd. Je kunt ook een specifieke `Date`‑instantie opgeven als je een aangepast tijdstempel nodig hebt.

#### Stap 5: Definieer bedrijfsinformatie
```java
root.getDocumentProperties().setCompany("GroupDocs");
```  
*Uitleg:* Slaat de bedrijfsnaam op die aan het diagram is gekoppeld—handig voor enterprise‑tracking.

#### Stap 6: Stel documentcategorie in
```java
root.getDocumentProperties().setCategory("test category");
```  
*Uitleg:* Categoriseert het bestand, waardoor je **diagramcategorie** consistent kunt bijwerken in je repository.

#### Stap 7: Voeg trefwoorden toe
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```  
*Uitleg:* Trefwoorden verbeteren de doorzoekbaarheid; je kunt alle termen die relevant zijn voor de inhoud van het diagram opsommen.

#### Stap 8: Sla wijzigingen op
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```  
*Uitleg:* Slaat alle wijzigingen op in een nieuw bestand, waardoor het origineel onaangeroerd blijft.

### Veelvoorkomende valkuilen & probleemoplossing
- **Bestand niet gevonden:** Controleer het invoerpad en zorg dat de bestandsextensie overeenkomt met het daadwerkelijke formaat.  
- **Toegang geweigerd:** Controleer lees‑/schrijfrechten voor zowel invoer‑ als uitvoermappen.  
- **Ongeldig datumformaat:** Gebruik `java.util.Date` of `java.time`‑objecten die compatibel zijn met de API.  

## Praktische toepassingen
1. **Automatiseren van documentarchivering** – Bij het verplaatsen van oude diagrammen naar een archief, automatisch **diagram creatietijd** wijzigen naar de archiveringsdatum en een uniforme categorie instellen.  
2. **Integratie met versiebeheer** – Houd tijdstempels synchroon met Git‑commits door de creatietijd bij elke release bij te werken.  
3. **Enterprise DMS‑standaardisatie** – Handhaaf een bedrijfsbrede beleidsregel voor auteur, bedrijf en trefwoorden voor alle diagram‑assets.

## Prestatie‑overwegingen
- **Batch‑verwerking:** Plaats de bovenstaande stappen in een lus om tientallen bestanden in één run te verwerken.  
- **Geheugenbeheer:** Maak elke `Metadata`‑instantie direct vrij (het try‑with‑resources‑blok doet dit automatisch).  
- **Asynchrone uitvoering:** Overweeg voor grote batches `CompletableFuture` om updates parallel uit te voeren zonder de hoofdthread te blokkeren.  
- **Gekwantificeerde capaciteit:** GroupDocs.Metadata ondersteunt meer dan 30 diagramformaten en kan bestanden tot 500 MB verwerken zonder het volledige document in het geheugen te laden, met updates in minder dan 200 ms per bestand op typische serverhardware.

## Conclusie
Je weet nu hoe je **diagram creatietijd** kunt wijzigen en andere ingebouwde metadata‑eigenschappen voor diagramdocumenten kunt bijwerken met GroupDocs.Metadata in Java. Door deze stappen te automatiseren kun je consistente, doorzoekbare en conforme documentatie behouden binnen je organisatie.

**Volgende stappen**
- Experimenteer met andere bestandsformaten die door GroupDocs.Metadata worden ondersteund (PDF, DOCX, enz.).
- Integreer de code in een CI/CD‑pipeline om metadata‑standaarden bij elke build af te dwingen.

Klaar om het uit te proberen? Ga naar [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) en begin vandaag nog met het implementeren van je eigen metadata‑automatisering.

---

**Last Updated:** 2026-06-17  
**Tested With:** GroupDocs.Metadata 24.12  
**Author:** GroupDocs  

## Veelgestelde vragen

**Q: Kan ik deze aanpak gebruiken met andere diagramformaten zoals VSDX?**  
A: Ja, dezelfde API werkt voor alle diagramformaten die door GroupDocs.Metadata worden ondersteund.

**Q: Heb ik een licentie nodig voor ontwikkel‑builds?**  
A: Een gratis proefversie is voldoende voor ontwikkeling en testen; een volledige licentie is vereist voor productie‑implementaties.

**Q: Hoe kan ik meerdere eigenschappen in één oproep bijwerken?**  
A: Stel elke eigenschap in op het `DocumentProperties`‑object voordat je `metadata.save(...)` aanroept; de bibliotheek schrijft ze allemaal in één keer.

**Q: Is het veilig om het originele bestand te overschrijven?**  
A: Het wordt aanbevolen om naar een nieuw bestand op te slaan (zoals getoond) en het origineel pas te vervangen nadat de update geslaagd is.

**Q: Wat als ik een aangepaste creatiedatum moet instellen in plaats van de huidige tijd?**  
A: Maak een `java.util.Date` (of `java.time`‑instantie) met het gewenste tijdstempel en geef deze door aan `setTimeCreated`.

## Gerelateerde tutorials

- [Hoe diagrammetadata bijwerken in Java met GroupDocs.Metadata](/metadata/java/diagram-formats/update-diagram-metadata-groupdocs-java/)
- [Hoe DXF‑auteurmetadata bijwerken met GroupDocs.Metadata voor Java – Een volledige gids](/metadata/java/cad-formats/update-dxf-author-metadata-groupdocs-java/)
- [Java‑metadata‑updates automatiseren op datum met GroupDocs.Metadata voor efficiënt bestandsbeheer](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)