---
date: '2026-06-22'
description: Erfahren Sie, wie Sie die komprimierte Größe in Java ermitteln, während
  Sie RAR-Metadaten mit GroupDocs.Metadata für Java extrahieren. Schritt‑für‑Schritt‑Anleitung,
  Code‑Beispiele und bewährte Methoden.
keywords:
- get compressed size java
- groupdocs metadata java
- extract rar metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  headline: Get Compressed Size Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to get compressed size java while extracting RAR metadata
    using GroupDocs.Metadata for Java. Step‑by‑step guide, code samples, and best
    practices.
  name: Get Compressed Size Java with GroupDocs.Metadata
  steps:
  - name: Initialize the Metadata object
    text: Create a `Metadata` instance by providing the path to the RAR file. This
      object represents the archive in memory and gives you access to its internal
      structure.
  - name: Obtain the root package of the RAR archive
    text: Call `metadata.getRootPackage()` to retrieve the top‑level package that
      contains all entries. The returned `ArchivePackage` lets you enumerate files
      and folders inside the archive.
  - name: Retrieve total entry count
    text: Use `archivePackage.getEntries().size()` to know how many items are stored.
      Knowing the count helps you allocate progress‑tracking structures for batch
      jobs.
  - name: Iterate over each file and read its properties
    text: Loop through `archivePackage.getEntries()`. For every entry that represents
      a file (not a folder), call `entry.getCompressedSize()` to obtain its compressed
      size in bytes. You can also read `entry.getOriginalSize()` if you need the uncompressed
      size for ratio calculations. **Troubleshooting Tips** -
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java is a library that enables reading, updating,
      and managing metadata across more than 50 file formats, including RAR, ZIP,
      and 7z, without requiring file extraction.
    question: What is GroupDocs.Metadata for Java?
  - answer: Visit the [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/)
      to acquire a temporary or permanent license; a free trial is available for development.
    question: How do I obtain a license for full access?
  - answer: Yes, the same API supports ZIP, 7z, and several other archive formats,
      allowing a unified codebase for all archive metadata tasks.
    question: Can I use GroupDocs.Metadata with other archive types besides RAR?
  - answer: The main issues are memory consumption and file‑handle limits; mitigate
      them by processing entries one‑by‑one and closing the `Metadata` object promptly.
    question: What are common pitfalls when handling large RAR files?
  - answer: The [GroupDocs free support forum](https://forum.groupdocs.com/c/metadata/)
      provides assistance from both the vendor’s engineers and the community.
    question: Where can I get support if I encounter problems?
  type: FAQPage
title: Komprimierte Größe in Java mit GroupDocs.Metadata abrufen
type: docs
url: /de/java/archive-formats/extract-rar-metadata-groupdocs-java/
weight: 1
---

# Komprimierte Größe in Java mit GroupDocs.Metadata

In modernen daten‑zentrierten Anwendungen ist **get compressed size java** ein häufiges Bedürfnis, wenn Sie die Größe von Dateien, die in RAR‑Archiven gespeichert sind, ohne sie zu entpacken prüfen müssen. Egal, ob Sie ein Backup‑Verifizierungs‑Tool, ein Digital‑Asset‑Management‑System oder ein Datei‑Sharing‑Portal erstellen, das Auslesen dieser Metadaten spart sowohl Zeit als auch Systemressourcen. Dieser Leitfaden führt Sie durch die Verwendung von GroupDocs.Metadata für Java, um die komprimierte Größe jedes Eintrags schnell, sicher und mit minimalem Code abzurufen.

## Schnelle Antworten
- **Welche Bibliothek wird benötigt?** GroupDocs.Metadata for Java  
- **Kann ich komprimierte Größen abrufen?** Yes – call `rarFile.getCompressedSize()` on each entry  
- **Benötige ich eine Lizenz?** Ein kostenloser Test funktioniert für die Entwicklung; eine Voll‑Lizenz ist für die Produktion erforderlich  
- **Welche Java‑Version wird unterstützt?** Java 8+ (jede Maven‑kompatible Umgebung)  
- **Ist Batch‑Verarbeitung möglich?** Absolut – durchlaufen Sie einen Ordner mit RAR‑Dateien und verwenden Sie denselben Code erneut  
- **Wie gehe ich mit großen Archiven um?** Verarbeiten Sie Einträge einzeln und schließen Sie das Metadata‑Objekt, wenn Sie fertig sind  

## Was ist “get compressed size java” und warum ist es wichtig?
**Get compressed size java** liest die Größe einer Datei, wie sie in einem RAR‑Container gespeichert ist. Dieser Wert gibt an, wie viel Platz die Datei nach der Kompression belegt, sodass Sie Kompressionsraten überprüfen, Übertragungszeiten schätzen und sowohl Original‑ als auch komprimierte Größen in Inventarberichten darstellen können.

## Wie man get compressed size java aus RAR‑Archiven erhält
Laden Sie das RAR‑Archiv mit GroupDocs.Metadata, iterieren Sie über seine Einträge und rufen Sie die Methode `getCompressedSize()` für jeden Dateieintrag auf. Dieser Ansatz liest nur den Archiv‑Header, sodass keine Extraktion oder vollständiges Laden der Datei erfolgt, und hält die Speichernutzung unter 5 MB, selbst bei Archiven von mehreren hundert Megabyte.

### Schritt 1: Metadaten‑Objekt initialisieren
Erstellen Sie eine `Metadata`‑Instanz, indem Sie den Pfad zur RAR‑Datei angeben. Dieses Objekt repräsentiert das Archiv im Speicher und gibt Ihnen Zugriff auf seine interne Struktur.

### Schritt 2: Das Root‑Package des RAR‑Archivs erhalten
Rufen Sie `metadata.getRootPackage()` auf, um das oberste Package zu erhalten, das alle Einträge enthält. Das zurückgegebene `ArchivePackage` ermöglicht Ihnen, Dateien und Ordner im Archiv aufzulisten.

### Schritt 3: Gesamte Eintragsanzahl abrufen
Verwenden Sie `archivePackage.getEntries().size()`, um zu erfahren, wie viele Elemente gespeichert sind. Das Wissen um die Anzahl hilft Ihnen, Fortschritts‑Tracking‑Strukturen für Batch‑Jobs zuzuweisen.

### Schritt 4: Über jede Datei iterieren und ihre Eigenschaften auslesen
Durchlaufen Sie `archivePackage.getEntries()`. Für jeden Eintrag, der eine Datei (nicht einen Ordner) darstellt, rufen Sie `entry.getCompressedSize()` auf, um die komprimierte Größe in Bytes zu erhalten. Sie können auch `entry.getOriginalSize()` lesen, wenn Sie die unkomprimierte Größe für Verhältnis‑Berechnungen benötigen.

**Fehlerbehebungstipps**  
- Stellen Sie sicher, dass `rarFilePath` auf eine vorhandene RAR‑Datei zeigt.  
- Stellen Sie sicher, dass die Anwendung Leseberechtigungen für das Archiv hat.  
- Falls Sie Fehler wie „unsupported format“ erhalten, prüfen Sie, ob die RAR‑Version mit GroupDocs.Metadata kompatibel ist (es unterstützt RAR 4 und RAR 5).  

## Warum GroupDocs.Metadata für RAR‑Dateien verwenden?
GroupDocs.Metadata bietet eine High‑Level‑API, die Archiv‑Header liest, ohne Dateien zu extrahieren, und schnellen Zugriff auf Eigenschaften wie komprimierte Größe, Originalgröße und Zeitstempel ermöglicht. Sie funktioniert mit den Formaten RAR 4 und RAR 5, verarbeitet große Archive effizient und abstrahiert format‑spezifische Details, sodass Entwickler einheitlichen Code für verschiedene Archivtypen schreiben können.

## Häufige Anwendungsfälle
1. **Data Management Systems** – archivieren Sie Inhalte automatisch für durchsuchbare Inventare.  
2. **Digital Asset Management** – bereichern Sie Mediatheken mit archivbezogenen Details wie der komprimierten Größe.  
3. **Backup Verification** – vergleichen Sie gespeicherte komprimierte Größen mit erwarteten Werten, um Beschädigungen zu erkennen.  
4. **File‑Sharing Platforms** – zeigen Sie Archiv‑Zusammenfassungen an, ohne Dateien vollständig zu extrahieren, und verbessern Sie die Benutzererfahrung.  

## Leistungsüberlegungen
- **Nur benötigte Eigenschaften zugreifen** – vermeiden Sie das Aufrufen schwerer Methoden, wenn Sie nur Dateinamen und Größen benötigen.  
- **Metadaten‑Objekte freigeben** – rufen Sie nach der Verarbeitung `metadata.close()` auf, um native Ressourcen freizugeben.  
- **Batch‑Verarbeitung** – verarbeiten Sie mehrere RAR‑Dateien in einer Schleife und verwenden Sie dieselbe JVM erneut, um Start‑Overhead zu reduzieren.  

## Häufig gestellte Fragen

**Q: Was ist GroupDocs.Metadata für Java?**  
A: GroupDocs.Metadata for Java ist eine Bibliothek, die das Lesen, Aktualisieren und Verwalten von Metadaten für mehr als 50 Dateiformate ermöglicht, einschließlich RAR, ZIP und 7z, ohne dass eine Dateiextraktion erforderlich ist.

**Q: Wie erhalte ich eine Lizenz für vollen Zugriff?**  
A: Besuchen Sie die [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/), um eine temporäre oder permanente Lizenz zu erhalten; ein kostenloser Test ist für die Entwicklung verfügbar.

**Q: Kann ich GroupDocs.Metadata mit anderen Archivtypen außer RAR verwenden?**  
A: Ja, dieselbe API unterstützt ZIP, 7z und mehrere andere Archivformate, sodass ein einheitlicher Code für alle Archiv‑Metadaten‑Aufgaben verwendet werden kann.

**Q: Was sind häufige Fallstricke beim Umgang mit großen RAR‑Dateien?**  
A: Die Hauptprobleme sind Speicherverbrauch und Dateihandhabungs‑Grenzen; mildern Sie diese, indem Sie Einträge einzeln verarbeiten und das `Metadata`‑Objekt umgehend schließen.

**Q: Wo kann ich Unterstützung erhalten, wenn ich Probleme habe?**  
A: Das [GroupDocs free support forum](https://forum.groupdocs.com/c/metadata/) bietet Hilfe sowohl von den Ingenieuren des Anbieters als auch von der Community.

## Ressourcen
- **Dokumentation**: [GroupDocs Metadata Java Documentation](https://docs.groupdocs.com/metadata/java/)  
- **API‑Referenz**: [GroupDocs API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Download**: [Latest Version Downloads](https://releases.groupdocs.com/metadata/java/)  
- **GitHub**: [Source Code on GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Kostenloser Support**: [GroupDocs Forum](https://forum.groupdocs.com/c/metadata/)  
- **Veröffentlichungen**: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)  
- **Umfassende Dokumentation**: [comprehensive documentation](https://docs.groupdocs.com/metadata/java/)

## Fazit
Sie wissen jetzt, **wie man GroupDocs.Metadata** verwendet, um umfassende Metadaten aus RAR‑Archiven zu extrahieren, einschließlich **wie man get compressed size java** für jeden Eintrag ermittelt. Integrieren Sie dieses Muster in Ihre Projekte, um Daten‑Management‑Fähigkeiten zu steigern, die Backup‑Verifizierung zu verbessern und Dateisuche‑Erlebnisse zu bereichern, ohne den Aufwand einer vollständigen Extraktion.

### Nächste Schritte
Erkunden Sie zusätzliche Funktionen wie das Aktualisieren von Eintragskommentaren oder das Extrahieren von Prüfsummeninformationen in der offiziellen Dokumentation und überlegen Sie, diese Metadaten‑Extraktion mit Ihrer bestehenden Indexierungs‑Pipeline zu kombinieren, um ein vollständig durchsuchbares Archiv‑Repository zu erhalten.

---

**Zuletzt aktualisiert:** 2026-06-22  
**Getestet mit:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs  

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

```java
import com.groupdocs.metadata.Metadata;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata object
        Metadata metadata = new Metadata("path/to/your/document");
        System.out.println("Metadata initialized successfully.");
    }
}
```

```java
// Specify the path to your input RAR file
String rarFilePath = "YOUR_DOCUMENT_DIRECTORY/input.rar";

// Initialize Metadata object with the specified RAR file path\ nMetadata metadata = new Metadata(rarFilePath);
```

```java
// Obtain the root package of the RAR archive
RarRootPackage root = metadata.getRootPackageGeneric();
```

```java
// Retrieve and print the total number of entries in the RAR package
int totalEntries = root.getRarPackage().getTotalEntries();
system.out.println("Total Entries: " + totalEntries);
```

```java
// Iterate over each file within the RAR archive
for (RarFile rarFile : root.getRarPackage().getFiles()) {
    // Print file name, compressed size, modification date time, and uncompressed size
    System.out.println("File Name: " + rarFile.getName());
    System.out.println("Compressed Size: " + rarFile.getCompressedSize());
    System.out.println("Modification Date Time: " + rarFile.getModificationDateTime());
    System.out.println("Uncompressed Size: " + rarFile.getUncompressedSize());
}
```

## Verwandte Tutorials

- [ZIP-Kommentare in Java mit GroupDocs.Metadata extrahieren – Anleitung](/metadata/java/archive-formats/extract-zip-metadata-groupdocs-java-guide/)
- [ZIP-Kommentar in Java aktualisieren – Wie man ZIP-Archivkommentare mit GroupDocs.Metadata aktualisiert](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)
- [Wie man TAR-Dateien liest und Metadaten mit GroupDocs.Metadata für Java extrahiert](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)