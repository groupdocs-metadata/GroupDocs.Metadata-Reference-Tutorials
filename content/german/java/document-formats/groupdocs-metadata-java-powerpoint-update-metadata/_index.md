---
date: '2026-05-27'
description: Erfahren Sie, wie Sie pptx CreatedTime in Java mit der GroupDocs Maven-Abhängigkeit
  setzen, um PowerPoint-Metadaten zu aktualisieren, einschließlich wie Sie das Erstellungsdatum
  von PPTX ändern.
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
title: Setzen Sie PPTX CreatedTime in Java mit der GroupDocs Maven-Abhängigkeit
type: docs
url: /de/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# PPTX-Erstellungszeit in Java mit GroupDocs.Metadata festlegen

Genaues Metadaten sind für Compliance und Auffindbarkeit in modernen Dokumenten‑Workflows unerlässlich. Mit **GroupDocs.Metadata** können Sie programmgesteuert **die PPTX‑Erstellungszeit in Java festlegen**, sodass Sie das **Erstellungsdatum der PPTX** zusammen mit anderen integrierten Eigenschaften wie Autor oder Unternehmen ändern können. Dieses Tutorial führt Sie durch die Maven‑Einrichtung, die Initialisierung der API, das Aktualisieren von Metadaten und das Speichern der modifizierten Präsentation – alles mit klarem, produktionsreifem Code.

## Schnelle Antworten
- **Welche Bibliothek aktualisiert PowerPoint‑Metadaten in Java?** GroupDocs.Metadata über die GroupDocs Maven‑Abhängigkeit.  
- **Kann ich die PPTX‑Erstellungszeit‑Eigenschaft festlegen?** Ja – verwenden Sie `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Ist für die Produktion eine Lizenz erforderlich?** Eine Testversion funktioniert für die Evaluierung; eine kommerzielle Lizenz ist für den Produktionseinsatz obligatorisch.  
- **Welches Build‑Tool verwendet das Beispiel?** Maven (Sie können das JAR auch manuell herunterladen).  
- **Unterstützt die API Java 8 und neuer?** Absolut – GroupDocs.Metadata zielt auf Java 8+ ab.

## Was ist die GroupDocs Maven‑Abhängigkeit?
Die **GroupDocs Maven‑Abhängigkeit** ist ein Maven‑kompatibler Repository‑Eintrag, der die neueste GroupDocs.Metadata‑Bibliothek in Ihr Java‑Projekt einbindet. Sie vereinfacht das Abhängigkeitsmanagement, indem sie transitive Bibliotheken automatisch auflöst, garantiert, dass Sie stets die neueste und sicherste Version verwenden, und eliminiert die Notwendigkeit manueller JAR‑Downloads oder Versionsverfolgung.

## Warum GroupDocs.Metadata verwenden, um das PPTX‑Erstellungsdatum zu ändern?
GroupDocs.Metadata ermöglicht automatisierte, stapelverarbeitbare Aktualisierungen von PPTX‑Erstellungszeitstempeln und stellt sicher, dass jede Präsentation den Unternehmensrichtlinien oder gesetzlichen Anforderungen entspricht. Durch das programmgesteuerte Festlegen der CreatedTime‑Eigenschaft vermeiden Sie manuelle Bearbeitung, reduzieren menschliche Fehler und können die Änderung in CI/CD‑Pipelines oder Migrationsskripte integrieren für ein nahtloses Dokumentenmanagement.

## Voraussetzungen
- Java 8 oder höher installiert.  
- Eine IDE wie IntelliJ IDEA oder Eclipse.  
- Maven für die Abhängigkeitsverwaltung.  
- Zugriff auf eine GroupDocs‑Testversion oder gekaufte Lizenz.

## Wie man PPTX-Erstellungszeit in Java festlegt?
Die Klasse `Metadata` repräsentiert ein Dokument und bietet Zugriff auf dessen Metadaten‑Eigenschaften.

Laden Sie Ihre PowerPoint‑Datei mit `new Metadata("presentation.pptx")`, holen Sie das Root‑Package, rufen Sie `setCreatedTime` mit dem gewünschten `java.util.Date` auf und schließlich `save`, um die Änderungen zu schreiben. Dieser End‑zu‑End‑Ablauf ändert das Erstellungsdatum, während er den gesamten Folieninhalt und andere Eigenschaften beibehält.

### Maven‑Einrichtung
Fügen Sie das GroupDocs‑Repository und die Metadaten‑Abhängigkeit zu Ihrer `pom.xml` hinzu:

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

> **Pro‑Tipp:** Die Versionsnummer aktuell zu halten, stellt sicher, dass Sie von den neuesten Fehlerbehebungen und Leistungsverbesserungen profitieren.

### Direkter Download (falls Sie Maven nicht verwenden möchten)
Alternativ können Sie das neueste JAR von [GroupDocs.Metadata für Java‑Releases](https://releases.groupdocs.com/metadata/java/) herunterladen.

#### Lizenzbeschaffung
Beginnen Sie mit einer kostenlosen Testversion oder fordern Sie eine temporäre Lizenz an, um GroupDocs.Metadata zu evaluieren. Für den Produktionseinsatz erwerben Sie eine Lizenz über die [offizielle Website von GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Grundlegende Initialisierung und Einrichtung
Sobald die Bibliothek im Klassenpfad ist, können Sie eine `Metadata`‑Instanz erstellen, die auf Ihre PowerPoint‑Datei verweist:

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

Dieser Code öffnet die Präsentation in einem try‑with‑resources‑Block und garantiert, dass der Dateihandle automatisch freigegeben wird.

## Schritt‑für‑Schritt‑Anleitung zum Aktualisieren integrierter Metadaten

### Schritt 1: Präsentationsdokument laden
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Das Laden der Datei stellt eine Verbindung her, die es Ihnen ermöglicht, Metadaten zu lesen oder zu schreiben.

### Schritt 2: Zugriff auf das Root‑Package der Präsentation
Das Objekt `root` bietet Zugriff auf das Kern‑Package der Präsentation und dessen integrierten Eigenschaften.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

Das Objekt `root` stellt alle integrierten Dokumenteneigenschaften bereit.

### Schritt 3: Integrierte Dokumenteneigenschaften aktualisieren (einschließlich Erstellungsdatum)
`setCreatedTime` weist dem Dokument einen neuen Erstellungszeitstempel zu.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Hier zeigen wir, wie man **die PPTX‑Erstellungszeit festlegt**, indem man ein neues `Date`‑Objekt `CreatedTime` zuweist. Ersetzen Sie `new Date()` durch einen beliebigen gewünschten Zeitstempel.

### Schritt 4: Aktualisierte Präsentation speichern
`save` schreibt die modifizierten Metadaten zurück in eine Datei.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

Der Aufruf `save` schreibt die modifizierten Metadaten in eine neue PowerPoint‑Datei, wobei das Original unverändert bleibt.

## Fehlerbehebungstipps
- **Datei nicht gefunden:** Überprüfen Sie den Eingabepfad und die Dateiberechtigungen.  
- **Versionskonflikt:** Stellen Sie sicher, dass die `groupdocs-metadata`‑Version zu Ihrer Java‑Laufzeit passt.  
- **Eigenschaft wird nicht aktualisiert:** Vergewissern Sie sich, dass Sie `setCreatedTime` (oder den entsprechenden Setter) vor dem Aufruf von `save` aufrufen.

## Praktische Anwendungsfälle
1. **Corporate Branding:** Automatisch den korrekten Firmennamen und die Kategorie in alle Folienpräsentationen vor der Verteilung einfügen.  
2. **Document Management Systems:** PPTX‑Dateien mit durchsuchbaren Metadaten anreichern für schnellere Wiederauffindung.  
3. **Educational Resources:** Autor‑ und Lehrplaninformationen über alle Vorlesungsfolien hinweg aktuell halten.  
4. **Collaboration Tracking:** Namen der Mitwirkenden erfassen, um Verantwortlichkeit zu gewährleisten.  
5. **CMS Integration:** Metadatenänderungen in Echtzeit mit Ihrer Content‑Management‑Plattform synchronisieren.

## Leistungsüberlegungen
- **Batch‑Verarbeitung:** Durchlaufen Sie eine Dateiliste und verwenden Sie nach Möglichkeit eine einzelne `Metadata`‑Instanz erneut.  
- **Speichermanagement:** Verwenden Sie stets try‑with‑resources (wie gezeigt), um native Ressourcen zeitnah freizugeben.  
- **Effiziente Datenstrukturen:** Speichern Sie Metadaten‑Updates in einer Map, bevor Sie sie anwenden, um wiederholte Aufrufe zu reduzieren.

## Häufig gestellte Fragen
**Q: Was ist der Hauptzweck der GroupDocs Maven‑Abhängigkeit?**  
A: Sie bietet eine bequeme Möglichkeit, die neueste GroupDocs.Metadata‑Bibliothek in Maven‑basierten Java‑Projekten einzubinden.

**Q: Wie kann ich das PPTX‑Erstellungsdatum festlegen, ohne andere Eigenschaften zu beeinflussen?**  
A: Verwenden Sie `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` bevor Sie `metadata.save()` aufrufen.

**Q: Benötige ich eine Lizenz, um diesen Code in der Entwicklung auszuführen?**  
A: Eine temporäre Testlizenz reicht für Entwicklung und Tests aus; für die Produktion ist eine Voll‑Lizenz erforderlich.

**Q: Kann ich auch benutzerdefinierte Metadatenfelder aktualisieren?**  
A: Ja – GroupDocs.Metadata unterstützt sowohl integrierte als auch benutzerdefinierte Eigenschaften über seine API.

**Q: Gibt es eine Möglichkeit, Änderungen rückgängig zu machen, wenn ich einen Fehler mache?**  
A: Bewahren Sie eine Kopie der Originaldatei auf oder lesen Sie die bestehenden Eigenschaftswerte aus, bevor Sie sie überschreiben, und stellen Sie sie bei Bedarf wieder her.

## Ressourcen
- [Dokumentation](https://docs.groupdocs.com/metadata/java/)
- [API‑Referenz](https://apireference.groupdocs.com/metadata/java/)

---

**Zuletzt aktualisiert:** 2026-05-27  
**Getestet mit:** GroupDocs.Metadata 24.12 für Java  
**Autor:** GroupDocs  

---

## Verwandte Tutorials
- [Benutzerdefinierte Metadaten in PowerPoint mit der GroupDocs.Metadata Java‑API aktualisieren](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Wie man Word‑Dokumentmetadaten mit GroupDocs.Metadata Java aktualisiert: Ein vollständiger Leitfaden](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [PDF‑Metadaten effizient mit GroupDocs.Metadata in Java für das Dokumentenmanagement aktualisieren](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)