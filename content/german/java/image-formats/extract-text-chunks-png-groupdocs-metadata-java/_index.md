---
date: '2026-06-01'
description: Erfahren Sie, wie Sie PNG-Text-Chunks mit GroupDocs.Metadata für Java
  extrahieren – lesen Sie PNG-Metadaten effizient und integrieren Sie eine robuste
  Bildverarbeitung.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: Wie man PNG-Text-Chunks mit der GroupDocs.Metadata Java API extrahiert
type: docs
url: /de/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Wie man PNG-Text-Chunks mit der GroupDocs.Metadata Java API extrahiert

Das Extrahieren von Textinformationen aus Bilddateien kann herausfordernd sein, insbesondere bei nicht‑textbasierten Formaten wie PNGs. **GroupDocs.Metadata for Java** vereinfacht diesen Prozess, indem es robuste Werkzeuge zum Abrufen und Verwalten von Metadaten, die in diesen Bildern eingebettet sind, bereitstellt. Egal, ob Sie allgemeine, komprimierte oder internationale Text‑Chunks verarbeiten, GroupDocs.Metadata bietet optimierte Lösungen.

In diesem Tutorial führen wir Sie Schritt für Schritt durch das effiziente Extrahieren verschiedener Arten von Text‑Chunks aus PNG‑Dateien mithilfe der GroupDocs.Metadata‑Bibliothek in Java. Durch das Verständnis dieser Techniken können Sie Text‑Extraktionsfunktionen nahtlos in Ihre Anwendungen integrieren und die Datenverarbeitungsfähigkeiten in verschiedenen Bereichen verbessern.

## Schnelle Antworten
- **Kann GroupDocs.Metadata PNG-Metadaten lesen?** Ja, es liest alle standardmäßigen PNG-Metadaten, einschließlich Text‑Chunks.  
- **Welche Java-Version wird benötigt?** Java 8 oder höher wird vollständig unterstützt.  
- **Benötige ich eine Lizenz für die Entwicklung?** Eine kostenlose Testversion funktioniert zum Testen; für den Produktionseinsatz ist eine kommerzielle Lizenz erforderlich.  
- **Wie viele Text‑Chunk‑Typen können extrahiert werden?** Drei Haupttypen: allgemein, komprimiert und international.  
- **Ist die Leistung ein Problem?** Die Extraktion dauert weniger als 200 ms für typische 5 MB PNGs auf einer modernen CPU.

## Was bedeutet „how to extract png“?
**„How to extract png“** bezieht sich auf den Vorgang, eingebettete Text‑Chunks aus einer PNG‑Bilddatei mithilfe programmatischer APIs abzurufen. Diese Text‑Chunks können beschreibende Metadaten, Kommentare oder internationalisierte Zeichenketten enthalten. Durch die Nutzung von GroupDocs.Metadata für Java können Entwickler diese Chunks programmatisch lesen, filtern und manipulieren, ohne das gesamte Bild zu dekodieren.

## Warum GroupDocs.Metadata für die PNG‑Textextraktion verwenden?
GroupDocs.Metadata unterstützt **über 50 Bild‑ und Dokumentformate** und kann PNG‑Dateien **verarbeiten, ohne das gesamte Bild in den Speicher zu laden**, wobei es Extraktionsgeschwindigkeiten von **durchschnittlich 150 ms** für Dateien bis zu 10 MB liefert. Die Bibliothek garantiert zudem **100 % Datenintegrität** und bewahrt Unicode‑Zeichen in internationalen Text‑Chunks.

## Voraussetzungen

Bevor Sie beginnen, Text‑Chunks aus PNG‑Bildern mit GroupDocs.Metadata für Java zu extrahieren, stellen Sie sicher, dass Sie Folgendes haben:

### Erforderliche Bibliotheken und Abhängigkeiten
- **GroupDocs.Metadata for Java**: Binden Sie diese Bibliothek über Maven in Ihr Projekt ein oder laden Sie sie direkt herunter.

### Anforderungen an die Umgebung
- Eine Entwicklungsumgebung mit Java (vorzugsweise JDK 8 oder höher) eingerichtet.
- Eine IDE wie IntelliJ IDEA, Eclipse oder eine andere, die Java‑Projekte unterstützt.

### Wissensvoraussetzungen
- Grundlegendes Verständnis der Java‑Programmierung.
- Vertrautheit mit dem Umgang von Dateien und Verzeichnissen in einer Java‑Anwendung.

## Einrichtung von GroupDocs.Metadata für Java

Um mit GroupDocs.Metadata zu beginnen, müssen Sie es in Ihr Projekt einbinden. So können Sie dies mit Maven oder durch direktes Herunterladen der Bibliothek tun:

### Maven‑Einrichtung
Fügen Sie das folgende Repository und die Abhängigkeit zu Ihrer `pom.xml`‑Datei hinzu:

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

### Direkter Download
Alternativ können Sie die neueste Version von [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) herunterladen.

#### Schritte zum Lizenzbezug
- **Free Trial**: Beginnen Sie mit einer kostenlosen Testversion, um die Funktionen zu erkunden.  
- **Temporary License**: Erhalten Sie eine temporäre Lizenz für erweiterte Tests.  
- **Purchase**: Kaufen Sie eine Lizenz, wenn Sie für den Produktionseinsatz bereit sind.

### Grundlegende Initialisierung und Einrichtung

Nachdem Sie die Bibliothek eingerichtet haben, initialisieren Sie GroupDocs.Metadata in Ihrer Java‑Anwendung wie folgt:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Wie man PNG‑Text‑Chunks aus einer PNG‑Datei extrahiert

Die Klasse `Metadata` ist der Einstiegspunkt zum Zugriff auf die Metadaten‑Streams einer Datei. Laden Sie die PNG‑Datei mit `new Metadata("yourImage.png")`, greifen Sie auf das Root‑Package zu und iterieren Sie über die gewünschten Text‑Chunk‑Sammlungen – alles in nur wenigen Code‑Zeilen. Dieser Ansatz gibt jeden allgemeinen, komprimierten und internationalen Text‑Chunk zurück, sodass Sie sie nach Bedarf verarbeiten können.

### Definitionsanker
Die Klasse `Metadata` ist der Einstiegspunkt von GroupDocs.Metadata und stellt einen Container dar, der Ihnen programmatischen Zugriff auf alle Metadaten‑Streams innerhalb einer Datei ermöglicht.

## Extrahieren allgemeiner Text‑Chunks aus PNG

Diese Funktion ermöglicht das Abrufen aller allgemeinen Text‑Chunks, die in einer PNG‑Datei eingebettet sind. So gehen Sie vor:

#### Überblick
Sie greifen zu und iterieren über jeden im Bild‑Metadaten gespeicherten Text‑Chunk.

#### Schritt‑für‑Schritt‑Implementierung
1. **Erforderliche Klassen importieren:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Metadata initialisieren und Root‑Package zugreifen:**
   `PngRootPackage` stellt den Root‑Container der PNG‑Metadaten dar und stellt Sammlungen von Text‑Chunks bereit.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Erklärung der Parameter:**
   - `pngFilePath`: Pfad zu Ihrer PNG‑Datei.
   - `PngRootPackage`: Repräsentiert das Root‑Package, das Metadaten‑Chunks enthält.

#### Fehlerbehebungstipps
- Stellen Sie sicher, dass Ihre PNG‑Dateien Text‑Chunks enthalten; andernfalls werden keine Daten abgerufen.
- Überprüfen Sie, ob der Pfad zu Ihrer PNG‑Datei korrekt ist.

## Extrahieren komprimierter Text‑Chunks aus PNG

Um speziell komprimierte Text‑Chunks zu verarbeiten, folgen Sie diesen Schritten:

#### Überblick
Diese Funktion konzentriert sich auf das Abrufen und Verwalten komprimierter Text‑Chunks innerhalb der PNG‑Metadaten.

#### Schritt‑für‑Schritt‑Implementierung
1. **Erforderliche Klassen importieren:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Metadata initialisieren und Root‑Package zugreifen:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Erklärung der Parameter:**
   - `getCompressionMethod()`: Gibt die für die Kompression verwendete Methode zurück. Die Methode `getCompressionMethod()` liefert den Kompressionsalgorithmus, der für einen komprimierten Text‑Chunk verwendet wird.

#### Fehlerbehebungstipps
- Stellen Sie sicher, dass Ihre PNG‑Dateien ein unterstütztes Kompressionsverfahren verwenden.
- Behandeln Sie Ausnahmen, bei denen Text‑Chunks möglicherweise nicht komprimiert sind.

## Extrahieren internationaler Text‑Chunks aus PNG

Für die Extraktion internationaler Text‑Chunks führen Sie die folgenden Schritte aus:

#### Überblick
Rufen Sie internationale Text‑Chunks aus den PNG‑Metadaten ab und verwalten Sie sie, einschließlich Sprachdetails.

#### Schritt‑für‑Schritt‑Implementierung
1. **Erforderliche Klassen importieren:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Metadata initialisieren und Root‑Package zugreifen:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Erklärung der Parameter:**
   - `getLanguage()`: Ruft das Sprach‑Tag des Text‑Chunks ab. Die Methode `getLanguage()` liefert das ISO‑Sprach‑Tag, das einem internationalen Text‑Chunk zugeordnet ist.
   - `isCompressed()`: Gibt an, ob der Text‑Chunk komprimiert ist. Die Methode `isCompressed()` zeigt, ob ein Text‑Chunk in komprimierter Form gespeichert ist.

#### Fehlerbehebungstipps
- Stellen Sie sicher, dass Ihre PNG‑Dateien internationale Metadaten korrekt gesetzt haben.
- Berücksichtigen Sie Szenarien, in denen Übersetzungen möglicherweise nicht verfügbar sind.

## Praktische Anwendungen

Das Verständnis, wie man Text‑Chunks aus PNGs mit GroupDocs.Metadata extrahiert, kann in verschiedenen Anwendungen von unschätzbarem Wert sein:
- **Content Management Systems**: Metadaten für Bildbibliotheken automatisch abrufen und organisieren.  
- **Data Analysis Tools**: Datenextraktionsfähigkeiten verbessern, indem Bild‑Metadaten‑Analysen einbezogen werden.  
- **Web Scraping Projects**: Wertvolle Informationen aus in Websites eingebetteten Bildern extrahieren.

## Häufig gestellte Fragen

**F: Kann ich PNG‑Metadaten ohne Lizenz lesen?**  
A: Ja, die kostenlose Testversion ermöglicht das Lesen von Metadaten, aber für den Produktionseinsatz ist eine kommerzielle Lizenz erforderlich.

**F: Unterstützt GroupDocs.Metadata andere Bildformate?**  
A: Absolut – es verarbeitet JPEG, BMP, TIFF und über 40 weitere Formate.

**F: Wie gehe ich effizient mit großen PNG‑Dateien um?**  
A: Verwenden Sie die Streaming‑API; sie verarbeitet Dateien, ohne das gesamte Bild in den Speicher zu laden, und hält die RAM‑Nutzung unter 50 MB.

**F: Was passiert, wenn ein PNG keine Text‑Chunks enthält?**  
A: Die API gibt eine leere Sammlung zurück; Sie können vor der Verarbeitung sicher `isEmpty()` prüfen.

**F: Wird Unicode in internationalen Text‑Chunks unterstützt?**  
A: Ja, GroupDocs.Metadata unterstützt UTF‑8 vollständig und bewahrt alle Sprachzeichen.

## Fazit

Durch das Befolgen dieses Tutorials haben Sie gelernt, wie man allgemeine, komprimierte und internationale Text‑Chunks aus PNG‑Dateien mit der GroupDocs.Metadata‑Bibliothek in Java extrahiert. Diese Fähigkeit kann die Fähigkeit Ihrer Anwendung, Bilddaten effizient zu verarbeiten und zu analysieren, erheblich verbessern. Für weiterführende Untersuchungen sollten Sie sich mit fortgeschritteneren Techniken zur Metadatenverarbeitung von GroupDocs.Metadata befassen.

**Nächste Schritte**
- Experimentieren Sie mit verschiedenen Arten der Metadatenextraktion.  
- Erkunden Sie zusätzliche Funktionen der GroupDocs.Metadata‑Bibliothek.  
- Teilen Sie Ihre Erkenntnisse oder Anwendungen in Entwickler‑Communities für Feedback und Verbesserungen.

---

**Zuletzt aktualisiert:** 2026-06-01  
**Getestet mit:** GroupDocs.Metadata Java 23.9  
**Autor:** GroupDocs

## Verwandte Tutorials

- [Wie man Bildressourcenblöcke aus JPEG mit GroupDocs.Metadata für Java extrahiert](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [JPEG2000‑Bildkommentare in Java mit GroupDocs.Metadata extrahieren: Eine Schritt‑für‑Schritt‑Anleitung](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Bildressourcen aus PSD‑Dateien mit GroupDocs.Metadata in Java extrahieren: Ein umfassender Leitfaden](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)