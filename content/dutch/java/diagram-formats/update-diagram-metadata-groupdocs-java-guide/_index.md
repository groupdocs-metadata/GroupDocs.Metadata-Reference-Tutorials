---
date: '2026-01-19'
description: Leer hoe u de aanmaaktijd kunt wijzigen en de metadata‑updates voor diagrambestanden
  kunt automatiseren met GroupDocs.Metadata in Java.
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: Wijzig de aanmaaktijd in diagrammetadata met GroupDocs Java
type: docs
url: /nl/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Wijzig creatietijd in diagrammetadata met GroupDocs Java

Het handmatig bijwerken van metadatavelden zoals maker, **wijzig creatietijd**, en categorie kan tijdrovend zijn. Automatiseer dit proces met de GroupDocs.Metadata bibliotheek voor Java, en je kunt **creatietijd wijzigen** en andere ingebouwde eigenschappen in één enkele, herhaalbare stap. Deze gids leidt je door het instellen van de bibliotheek, het bijwerken van diagrammetadata, en het toepassen van best‑practice prestatie‑tips zodat je je documenten consistent en doorzoekbaar kunt houden.

## Snelle antwoorden
- **Wat is het primaire doel?** Wijzig creatietijd en andere metadata in diagrambestanden.  
- **Welke bibliotheek moet ik gebruiken?** GroupDocs.Metadata voor Java.  
- **Heb ik een licentie nodig?** Een gratis proefversie werkt voor testen; een volledige licentie is vereist voor productie.  
-?** Ja — gebruik dezelfde aanpak binnen een lus of parallelle stream.  
- **Welke Java‑versie is vereist?** JDK 8 of hoger.

## Wat is “wijzig creatietijd” in diagrammetadata?
Het wijzigen van de creatietijd betekent dat de oorspronkelijke tijdstempel die in een diagrambestand is opgeslagen (bijv.ingsregels Bij:** Helpt audit‑vereisten te voldoen door nauwkeurige tijdstempels te waarborgen.  

## Vereisten
- **Java Development Kit (JDK) 8+** geïnstalleerd.  
- **IDE** zoals IntelliJ IDEA of Eclipse.  
- **Maven** (of handmatige JAR‑afhandeling) voor afhankelijkheidsbeheer.  
- Basiskennis van Java‑klassen, methoden en foutafhandeling.

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
Als je liever direct downloadt, bezoek dan [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) om de nieuwste versie te verkrijgen.

### Omgevingsconfiguratie
- JDK 8 of nieuwer.  
- IntelliJ IDEA, Eclipse, of een andere Java‑compatibele IDE.  

### Kennis‑voorkennis
Begrip van Java‑syntaxis en basis‑bestand‑I/O maakt de tutorial soepeler, maar de stappen worden in gewone taal uitgelegd.

## GroupDocs.Metadata voor Java instellen
### Installatie‑instructies
**Maven‑gebruikers:** Het fragment hierboven voegt de repository en de vereiste JAR automatisch toe.  
**Direct‑download‑gebruikers:** Na het downloaden van de JAR van [GroupDocs](https://releases.groupdocs.com/metadata/java/), voeg je deze toe aan de classpath van je project.

### Licentie‑acquisitie
- **Gratis proefversie:** Verken de bibliotheek zonder kosten.  
- **Tijdelijke licentie:** Verkrijg een tijdelijke licentie voor uitgebreid testen [hier](https://purchase.groupdocs.com/temporary-license/).  
- **Aankoop:** Schaf een volledige licentie aan voor productieomgevingen.

### Basisinitialisatie
Om GroupDocs.Metadata te gebruiken, importeer je de klasse en open je een diagrambestand:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Met de bibliotheek geïnitialiseerd kun je nu elke ingebouwde eigenschap wijzigen, inclusief de creatietijd.

## Implementatie‑gids
### Hoe creatietijd wijzigen in diagrambestanden
In deze sectie lopen we stap voor stap door wat nodig is om **creatietijd te wijzigen** en andere veelvoorkomende eigenschappen zoals auteur, bedrijf en categorie bij te werken.

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
*Uitleg:* Het root‑pakket geeft directe toegang tot alle ingebouwde metadata‑velden voor het diagram.

#### Stap 3: Stel de maker‑eigenschap in
```java
root.getDocumentProperties().setCreator("test author");
```
*Uitleg:* Wijs een nieuwe auteursnaam toe. Vervang `"test author"` door de daadwerkelijke maker.

#### Stap 4: **Wijzig creatietijd**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*Uitleg:* Deze regel **wijzigt creatietijd** naar de huidige systeemdatum en -tijd. Je kunt ook een specifieke `Date`‑instantie leveren als je een aangepaste tijdstempel nodig hebt.

#### Stap 5: Definieer bedrijfsinformatie
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*Uitleg:* Slaat de bedrijfsnaam op die aan het diagram is gekoppeld — handig voor enterprise‑tracking.

#### Stap 6: Stel documentcategorie in
```java
root.getDocumentProperties().setCategory("test category");
```
*Uitleg:* Categoriseert het bestand, waardoor je **diagramcategorie bijwerkt** consistent door je repository heen.

#### Stap 7: Voeg trefwoorden toe
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*Uitleg:* Trefwoorden verbeteren de doorzoekbaarheid; je kunt elke term die relevant is voor de inhoud van het diagram vermelden.

#### Stap 8: Sla wijzigingen op
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*Uitleg:* Slaat alle aanpassingen op in een nieuw bestand, waardoor het origineel onaangeroerd blijft.

### Veelvoorkomende valkuilen & probleemoplossing
- **Bestand niet gevonden:** Controleer het invoerpad en zorg dat de bestandsextensie overeenkomt met het werkelijke formaat.  
- **Toegang geweigerd:** Controleer lees‑/schrijfrechten voor zowel invoer‑ als uitvoermappen.  
- **Ongeldig datumformaat:** Gebruik `java.util.Date` of `java.time`‑objecten die compatibel zijn met de API.  

## Praktische toepassingen
1. **Automatisering van documentarchivering** — Bij het verplaatsen van oude diagrammen naar een archief, wijzig automatisch **creatietijd** naar de archiveringsdatum en stel een uniforme categorie in.  
2. **Integratie met versiebeheer** — Houd tijdstempels synchroon met Git‑commits door creatietijd bij te werken bij elke release.  
3. **Enterprise DMS‑standaardisatie** — Handhaaf een bedrijfsbrede policy voor auteur, bedrijf en trefwoorden over alle diagram‑assets.

## Prestatie‑overwegingen
- **Batchverwerking:** Plaats de bovenstaande stappen in een lus om tientallen bestanden in één run te verwerken.  
- **Geheugenbeheer:** Maak elke `Metadata`‑instantie direct vrij (het try‑with‑resources‑blok doet dit automatisch).  
- **Asynchrone uitvoering:** Overweeg voor grote batches `CompletableFuture` om updates parallel uit te voeren zonder de hoofdthread te blokkeren.

## Conclusie
Je weet nu hoe je **creatietijd kunt wijzigen** en andere ingebouwde metadata‑eigenschappen voor diagramdocumenten kunt bijwerken met GroupDocs.Metadata in Java. Door deze stappen te automatiseren kun je consistente, doorzoekbare en conforme documentatie behouden binnen je organisatie.

**Volgende stappen**
- Experimenteer met andere bestandsformaten die door GroupDocs.Metadata worden ondersteund (PDF, DOCX, enz.).  
- Integreer de code in een CI/CD‑pipeline om metadata‑standaarden bij elke build af te dwingen.  

Klaar om het uit te proberen? Ga naar [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) en begin vandaag nog met het implementeren van je eigen metadata‑automatisering.

---

**Laatst bijgewerkt:** 2026-01-19  
**Getest met:** GroupDocs.Metadata 24.12  
**Auteur:** GroupDocs  

## Veelgestelde vragen

**Q: Kan ik deze aanpak gebruiken met andere diagramformaten zoals VSDX?**  
A: Ja, dezelfde API werkt voor alle diagramformaten die door GroupDocs.Metadata worden ondersteund.

**Q: Heb ik een licentie nodig voor ontwikkel‑builds?**  
A: Een gratis proefversie is voldoende voor ontwikkeling en testen; een volledige licentie is vereist voor productie‑implementaties.

**Q: Hoe kan ik meerdere eigenschappen in één oproep bijwerken?**  
A: Stel elke eigenschap in op het `DocumentProperties`‑object voordat je `metadata.save(...)` aanroept; de bibliotheek schrijft ze allemaal in één keer.

**Q: Is het veilig om het originele bestand te overschrijven?**  
A: Het wordt aanbevolen om naar een nieuw bestand op te slaan (zoals getoond) om gegevensverlies te voorkomen, en vervolgens het origineel te vervangen indien nodig.

**Q: Wat als ik een aangepaste creatiedatum moet instellen in plaats van de huidige tijd?**  
A: Maak een `java.util.Date` (of `java.time`‑instantie) met de gewenste tijdstempel en geef deze door aan `setTimeCreated`.