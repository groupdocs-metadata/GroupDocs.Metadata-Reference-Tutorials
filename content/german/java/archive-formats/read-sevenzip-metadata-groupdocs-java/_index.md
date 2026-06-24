---
date: '2026-06-22'
description: Erfahren Sie, wie Sie SevenZip-Metadaten in Java mit GroupDocs.Metadata
  für Java lesen, einschließlich wie Sie die komprimierte Größe in Java und weitere
  Archiv‑Eigenschaften abrufen.
keywords:
- read sevenzip metadata java
- get compressed size java
- GroupDocs.Metadata Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  headline: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  name: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  steps:
  - name: Initialize Metadata Object
    text: The `Metadata` class represents the entry point for loading and interacting
      with archive files.
  - name: Obtain the Root Package
    text: The `getRootPackageGeneric()` method returns a generic view of the archive's
      root package, allowing you to work with entries without needing format‑specific
      code. - **Why Use `getRootPackageGeneric()`?** It provides a generalized view
      of the archive's contents, making it easier to iterate over its e
  - name: Iterate Over Archive Entries
    text: The `SevenZipPackage` class represents the SevenZip container, and each
      entry is exposed as a `SevenZipFileInfo` object. The `SevenZipFileInfo` class
      provides direct access to properties like name, compressed size, and modification
      date. - **Why Extract These Properties?** Knowing file sizes helps m
  - name: Clean Up Resources
    text: Calling `close()` on the `Metadata` instance releases native resources and
      avoids memory leaks in long‑running services. - **Why Dispose?** Properly disposing
      of objects helps prevent memory leaks in long‑running applications.
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java – a single‑API solution for over 70 archive
      and document formats.
    question: What library should I use?
  - answer: Yes – call `getSevenZipPackage().getFiles()` after initializing the `Metadata`
      object.
    question: Can I list files inside a SevenZip archive?
  - answer: A free trial works for evaluation; a full license is required for production.
    question: Do I need a license?
  - answer: JDK 8 or higher (compatible with Java 17 LTS).
    question: Which Java version is supported?
  - answer: Not mandatory, but Maven handles transitive dependencies automatically.
    question: Is Maven required?
  type: FAQPage
title: Wie man SevenZip-Metadaten in Java mit GroupDocs.Metadata liest
type: docs
url: /de/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# Wie man SevenZip-Metadaten in Java mit GroupDocs.Metadata liest

Wenn Sie **read sevenzip metadata java** aus einer Java-Anwendung lesen müssen, sind Sie hier genau richtig. In diesem Tutorial führen wir Sie durch die Verwendung von **GroupDocs.Metadata**, um Dateinamen, komprimierte Größen, unkomprimierte Größen, Änderungsdaten und mehr zu extrahieren – genau die Daten, die Sie für Backup‑Validierung, Synchronisation oder Speicheroptimierungs‑Aufgaben benötigen.

## Einführung

Haben Sie Schwierigkeiten, Metadaten‑Eigenschaften aus SevenZip‑Archivdateien mit Java zuzugreifen und zu lesen? Dieses Tutorial führt Sie durch den Prozess der Verwendung von **GroupDocs.Metadata**. Eine leistungsstarke Bibliothek, die das Extrahieren wichtiger Informationen wie Dateinamen, Größen und Änderungsdaten direkt aus Ihren Archiven vereinfacht.

## Schnelle Antworten
- **Welche Bibliothek sollte ich verwenden?** GroupDocs.Metadata for Java – eine Single‑API‑Lösung für über 70 Archiv‑ und Dokumentformate.  
- **Kann ich Dateien innerhalb eines SevenZip‑Archivs auflisten?** Ja – call `getSevenZipPackage().getFiles()` after initializing the `Metadata` object.  
- **Brauche ich eine Lizenz?** Eine kostenlose Testversion funktioniert für die Evaluierung; eine Voll‑Lizenz ist für die Produktion erforderlich.  
- **Welche Java‑Version wird unterstützt?** JDK 8 oder höher (kompatibel mit Java 17 LTS).  
- **Ist Maven erforderlich?** Nicht zwingend, aber Maven verwaltet transitive Abhängigkeiten automatisch.  

## Was bedeutet „how to read sevenzip“ in Java?

Das Lesen von SevenZip‑Metadaten bedeutet, den `.7z`‑Container zu öffnen, jeden Eintrag zu enumerieren und Eigenschaften wie **compressed size**, **uncompressed size**, **file name** und **modification date** abzurufen, ohne die eigentlichen Dateien zu extrahieren. Dieser Vorgang gibt Ihnen Einblick in die Zusammensetzung des Archivs, ermöglicht die Überprüfung der Backup‑Integrität und erlaubt Entscheidungen zur Speicherkapazität, ohne das komplette Extrahieren.

## read sevenzip metadata java

Die Verwendung des primären Schlüsselworts in einer eigenen Überschrift hilft sowohl Lesern als auch Suchmaschinen, den Fokus dieses Leitfadens zu verstehen. Im Folgenden gehen wir die genauen Schritte durch, die Sie benötigen, um **read sevenzip metadata java** effizient zu **read sevenzip metadata java**.

## Warum GroupDocs.Metadata Java für die Metadatenextraktion verwenden?

GroupDocs.Metadata liest nur die Header‑Informationen, die für die Metadatenextraktion erforderlich sind, sodass der Vorgang selbst bei Multi‑Gigabyte‑Archiven in Millisekunden abgeschlossen ist. Es unterstützt **70+** Archiv‑ und Dokumentformate, verarbeitet Archive bis zu **2 GB**, ohne die gesamte Datei in den Speicher zu laden, und bietet eine konsistente API über alle unterstützten Typen hinweg.

## Voraussetzungen

Bevor Sie in **GroupDocs.Metadata for Java** einsteigen, stellen Sie sicher, dass Ihre Entwicklungsumgebung korrekt eingerichtet ist. Folgendes benötigen Sie:

- **Java Development Kit (JDK):** Version 8 oder höher.  
- **Maven:** Empfohlen für das Management von Abhängigkeiten, obwohl Sie das JAR auch manuell hinzufügen können.  
- **Grundlegende Java‑Kenntnisse:** Vertrautheit mit Klassen, Methoden und Ausnahmebehandlung.  

## Einrichtung von GroupDocs.Metadata für Java

Um GroupDocs.Metadata zu verwenden, binden Sie es über Maven in Ihr Projekt ein oder laden die Bibliothek direkt herunter.

### Maven verwenden

Fügen Sie die folgende Konfiguration zu Ihrer `pom.xml`‑Datei hinzu:

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

#### Lizenzbeschaffung

1. **Free Trial:** Starten Sie mit einer kostenlosen Testversion, um die Fähigkeiten von GroupDocs.Metadata zu testen.  
2. **Temporary License:** Beantragen Sie eine temporäre Lizenz, wenn Sie für Evaluierungszwecke erweiterten Zugriff benötigen.  
3. **Purchase:** Für den langfristigen Einsatz sollten Sie den Kauf einer Voll‑Lizenz in Betracht ziehen.  

Mit der abgeschlossenen Einrichtung gehen wir nun zur Implementierung der Metadaten‑Lese‑Funktionalität über.

## Implementierungs‑Leitfaden

### Zugriff auf Metadaten aus SevenZip‑Archiven

In diesem Abschnitt extrahieren und geben wir Metadaten‑Eigenschaften wie Dateinamen und Größen aus einem SevenZip‑Archiv aus.

#### Schritt 1: Metadaten‑Objekt initialisieren

Die Klasse `Metadata` stellt den Einstiegspunkt zum Laden und Interagieren mit Archivdateien dar.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### Schritt 2: Root‑Package erhalten

Die Methode `getRootPackageGeneric()` liefert eine generische Ansicht des Root‑Packages des Archivs, sodass Sie Einträge bearbeiten können, ohne format‑spezifischen Code zu benötigen.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Warum `getRootPackageGeneric()` verwenden?** Es bietet eine verallgemeinerte Sicht auf den Inhalt des Archivs, wodurch das Durchlaufen der Einträge ohne Sorge um spezifische Dateiformate erleichtert wird.

#### Schritt 3: Durch Archiv‑Einträge iterieren

Die Klasse `SevenZipPackage` repräsentiert den SevenZip‑Container, und jeder Eintrag wird als `SevenZipFileInfo`‑Objekt bereitgestellt. Die Klasse `SevenZipFileInfo` ermöglicht den direkten Zugriff auf Eigenschaften wie Name, komprimierte Größe und Änderungsdatum.

```java
int totalEntries = root.getSevenZipPackage().getTotalEntries();

for (SevenZipFile file : root.getSevenZipPackage().getFiles()) {
    String name = file.getName();
    long compressedSize = file.getCompressedSize();
    java.util.Date modificationDateTime = file.getModificationDateTime();
    long uncompressedSize = file.getUncompressedSize();

    // Output metadata properties for each file in the archive
    System.out.println("File Name: " + name);
    System.out.println("Compressed Size: " + compressedSize);
    System.out.println("Modification Date and Time: " + modificationDateTime);
    System.out.println("Uncompressed Size: " + uncompressedSize);
}
```

- **Warum diese Eigenschaften extrahieren?** Das Wissen um Dateigrößen hilft bei der Speicherverwaltung, während das Änderungsdatum für Synchronisationsaufgaben entscheidend sein kann. Der Aufruf `getCompressedSize()` ist der Java‑Weg, um **get compressed size java** für jeden Eintrag zu erhalten.

#### Schritt 4: Ressourcen bereinigen

Durch Aufrufen von `close()` auf der `Metadata`‑Instanz werden native Ressourcen freigegeben und Speicherlecks in langlaufenden Diensten vermieden.

```java
} finally {
    metadata.dispose();
}
```

- **Warum entsorgen?** Das ordnungsgemäße Freigeben von Objekten verhindert Speicherlecks in langlaufenden Anwendungen.

## Wie man Metadaten effizient extrahiert?

Laden Sie das SevenZip‑Archiv mit einer einzigen `Metadata`‑Instanz, rufen Sie `getRootPackageGeneric()` einmal auf und streamen Sie dann die Einträge mittels einer `for‑each`‑Schleife. Dieses Muster vermeidet wiederholte I/O‑Operationen, reduziert den GC‑Druck und läuft in O(n)‑Zeit, wobei *n* die Anzahl der Einträge ist.

## Praktische Anwendungen

Das Verständnis, wie man **read sevenzip metadata java** ausführt, bietet zahlreiche reale Vorteile:

1. **Backup‑Management:** Schnell die Integrität und Vollständigkeit von Backup‑Archiven überprüfen.  
2. **Dateisynchronisations‑Tools:** Änderungsdaten nutzen, um zu entscheiden, welche Dateien aktualisiert werden müssen.  
3. **Speicheroptimierung:** Komprimierte vs. unkomprimierte Größen vergleichen, um Kapazitätsplanungen zu erstellen.  

Eine Integration mit anderen Systemen ist möglich, sodass automatisierte Metadaten‑Extraktion als Teil größerer Daten‑Management‑Workflows eingesetzt werden kann.

## Leistungs‑Überlegungen

Beim Arbeiten mit GroupDocs.Metadata und großen Archiven sollten Sie folgende Tipps beachten:

- **Batch‑Verarbeitung:** Dateien in Batches verarbeiten, um den Speicherverbrauch effektiv zu steuern.  
- **Effiziente Ausnahmebehandlung:** Verwenden Sie try‑with‑resources für automatisches Ressourcen‑Management.  
- **Asynchrone Verarbeitung:** Implementieren Sie asynchrone Techniken für schwere Workloads.  

## Häufige Probleme und Lösungen

| Problem | Lösung |
|---------|--------|
| **`NullPointerException` beim Zugriff auf eine Datei** | Stellen Sie sicher, dass der Archivpfad korrekt ist und die Datei nicht beschädigt ist. |
| **Speicherspitzen bei riesigen Archiven** | Aktivieren Sie die Batch‑Verarbeitung oder erhöhen Sie die JVM‑Heap‑Größe (`-Xmx`). |
| **Lizenz wird nicht erkannt** | Vergewissern Sie sich, dass die Lizenzdatei im Arbeitsverzeichnis der Anwendung liegt oder über `License.setLicense(path)` gesetzt wird. |

## Häufig gestellte Fragen

**Q:** Was ist GroupDocs.Metadata?  
**A:** Es ist eine Java‑Bibliothek zur Handhabung von Metadaten über verschiedene Dateiformate hinweg, einschließlich SevenZip‑Archiven.

**Q:** Kann ich GroupDocs.Metadata ohne Maven verwenden?  
**A:** Ja, Sie können das JAR von der offiziellen Seite herunterladen und zu Ihrem Projekt‑Classpath hinzufügen.

**Q:** Wie gehe ich effizient mit großen Archiven um?  
**A:** Implementieren Sie Batch‑Verarbeitung oder nutzen Sie asynchrone Streams, um den Speicherverbrauch zu begrenzen.

**Q:** Wo finde ich detailliertere Anleitungen?  
**A:** Siehe die [official documentation](https://docs.groupdocs.com/metadata/java/) für umfassende API‑Referenzen.

**Q:** Was tun, wenn ich Probleme mit der Bibliothek habe?  
**A:** Fragen Sie die Community im [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/).

## Ressourcen

- **Documentation:** Erkunden Sie mehr unter [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **Official documentation:** [official documentation](https://docs.groupdocs.com/metadata/java/)  
- **API Reference:** Detaillierte API‑Informationen finden Sie unter [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Download:** Laden Sie die neueste Version von [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/) herunter  
- **GitHub Repository:** Zugriff auf Code‑Beispiele auf [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Free Support Forum:** Nehmen Sie an Diskussionen teil oder stellen Sie Fragen im [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**Zuletzt aktualisiert:** 2026-06-22  
**Getestet mit:** GroupDocs.Metadata 24.12 for Java  
**Autor:** GroupDocs

## Verwandte Tutorials

- [How to Read TAR Files and Extract Metadata with GroupDocs.Metadata for Java](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)  
- [Update ZIP Comment Java – How to Update ZIP Archive Comments Using GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)  
- [Extract Video Metadata Java: How to Read AVI Files with GroupDocs.Metadata](/metadata/java/audio-video-formats/extract-avi-metadata-groupdocs-metadata-java/)