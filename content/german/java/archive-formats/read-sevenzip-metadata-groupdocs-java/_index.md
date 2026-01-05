---
date: '2025-12-20'
description: Erfahren Sie, wie Sie Metadaten von SevenZip‑Archiven mit GroupDocs.Metadata
  für Java lesen, ein wichtiger Schritt in Java‑Projekten zur Metadatenextraktion.
keywords:
- SevenZip metadata Java
- extract SevenZip archive information
- read SevenZip file properties
title: Wie man SevenZip‑Metadaten mit GroupDocs.Metadata in Java ausliest
type: docs
url: /de/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# Wie man SevenZip-Metadaten mit GroupDocs.Metadata in Java liest

Wenn Sie **how to read sevenzip** Archivinformationen aus einer Java-Anwendung benötigen, sind Sie hier genau richtig. In diesem Tutorial führen wir Sie durch die Verwendung von **GroupDocs.Metadata**, um Dateinamen, Größen, Daten und mehr zu extrahieren – genau die Daten, die Sie für Backup-Validierung, Synchronisation oder Speicheroptimierungs-Aufgaben benötigen.

## Einführung

Haben Sie Schwierigkeiten, Metadaten-Eigenschaften aus SevenZip-Archivdateien mit Java zu lesen? Dieses Tutorial führt Sie durch den Prozess der Verwendung von **GroupDocs.Metadata**. Eine leistungsstarke Bibliothek, die das Extrahieren wichtiger Informationen wie Dateinamen, Größen und Änderungsdaten direkt aus Ihren Archiven vereinfacht.

In diesem Artikel zeigen wir, wie Sie **GroupDocs.Metadata for Java** nutzen können, um effizient auf Metadaten-Eigenschaften in SevenZip-Dateien zuzugreifen.

### Was Sie lernen werden
- Einrichten von GroupDocs.Metadata in einem Java‑Projekt
- Lesen von Metadaten aus SevenZip-Archiven mithilfe spezifischer Methoden und Klassen
- Praktische Beispiele zum Extrahieren wichtiger Dateiattribute wie Name, komprimierte Größe und Änderungsdatum

## Schnelle Antworten
- **Welche Bibliothek sollte ich verwenden?** GroupDocs.Metadata für Java
- **Kann ich Dateien innerhalb eines SevenZip-Archivs auflisten?** Ja – verwenden Sie `getSevenZipPackage().getFiles()`
- **Benötige ich eine Lizenz?** Eine kostenlose Testversion reicht für die Evaluierung; Für den Produktionseinsatz ist eine Voll‑Lizenz erforderlich
- **Welche Java‑Version wird unterstützt?** JDK8 oder höher
- **Ist Maven erforderlich?** Nicht unbedingt, aber Maven vereinfacht das Verwalten von Abhängigkeiten

## Was bedeutet „How to read sevenzip“ in Java?

Das Lesen von SevenZip-Metadaten bedeutet, den`.7z`-Container zu öffnen, jeden Eintrag zu enumerieren und Eigenschaften wie **komprimierte Größe**, **unkomprimierte Größe**, **Dateiname** und **Änderungsdatum** abzurufen, ohne die eigentlichen Dateien zu extrahieren.

## Warum GroupDocs.Metadata Java für die Metadatenextraktion verwenden?

- **Unified API** – funktioniert über Dutzende von Archiv- und Dokumentformaten hinweg
- **Keine externen Tools** – alles geschieht innerhalb Ihres Java-Prozesses
- **Performance-focused** – liest nur die Header-Informationen, die für Metadaten-Extraktions-Java-Aufgaben benötigt werden
- **Robuste Lizenzierung** – Testversion verfügbar, Voll‑Lizenz für den kommerziellen Einsatz

## Voraussetzungen

Bevor Sie in **GroupDocs.Metadata for Java** einsteigen, stellen Sie sicher, dass Ihre Entwicklungsumgebung korrekt eingerichtet ist. Folgendes benötigen Sie:

- **Java Development Kit (JDK):** Version8 oder höher.
- **Maven:** Empfohlen für das Verwalten von Abhängigkeiten, obwohl Sie das JAR auch manuell hinzufügen können.
- **Grundkenntnisse in Java:** Vertrautheit mit Klassen, Methoden und Ausnahmebehandlung.

## Einrichten von GroupDocs.Metadata für Java

Um GroupDocs.Metadata zu verwenden, binden Sie es über Maven in Ihr Projekt ein oder laden Sie die Bibliothek direkt herunter.

### Mit Maven

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

#### Lizenzerwerb

1. **Kostenlose Testversion:** Beginnen Sie mit einer kostenlosen Testversion, um die Fähigkeiten von GroupDocs.Metadata zu testen.
2. **Temporäre Lizenz:** Beantragen Sie eine temporäre Lizenz, wenn Sie für Evaluierungszwecke erweiterten Zugriff benötigen.
3. **Kauf:** Für den langfristigen Einsatz sollten Sie den Kauf einer Voll‑Lizenz in Betracht ziehen.

Nachdem die Einrichtung abgeschlossen ist, gehen wir zur Implementierung der Metadaten-Lese-Funktionalität über.

## Implementierungshandbuch

### Zugriff auf Metadaten aus SevenZip-Archiven

In diesem Abschnitt extrahieren und geben wir Metadaten-Eigenschaften wie Dateinamen und Größen aus einem SevenZip-Archiv aus.

#### Schritt 1: Metadatenobjekt initialisieren

Beginnen Sie damit, das `Metadata`‑Objekt mit dem Pfad zu Ihrer SevenZip‑Datei zu initialisieren. Dadurch weiß GroupDocs, welche Datei verarbeitet werden soll.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### Schritt 2: Stammpaket abrufen

Als nächstes greifen Sie auf das Root‑Package Ihres Archivs zu, um einen Einstiegspunkt zu allen Dateien und deren Eigenschaften zu erhalten.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Warum `getRootPackageGeneric()` verwenden?** Es bietet eine verallgemeinerte Ansicht des Inhalts des Archivs, wodurch das Durchlaufen seiner Einträge erleichtert wird, ohne sich um spezifische Dateiformate kümmern zu müssen.

#### Schritt 3: Archiv-Einträge durchlaufen

Mit Zugriff auf das Root‑Package Ihres Archivs iterieren Sie über jeden Eintrag, um Metadaten‑Eigenschaften zu extrahieren. Dabei werden Details wie Name, komprimierte Größe und Änderungsdatum abgerufen.

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

- **Warum diese Eigenschaften extrahieren?** Das Wissen über Dateigrößen hilft bei der Speicherverwaltung, während das Änderungsdatum für Synchronisationsaufgaben entscheidend sein kann.

#### Schritt 4: Ressourcen aufräumen

Stellen Sie schließlich sicher, dass Sie das Metadaten‑Objekt freigeben, um alle von GroupDocs.Metadata belegten Ressourcen zu release.

```java
} finally {
    metadata.dispose();
}
```

- **Warum freigeben?** Das korrekte Freigeben von Objekten hilft, Speicherlecks in langfristig laufenden Anwendungen zu verhindern.

## Praktische Anwendungen

Das Verständnis, wie man SevenZip‑Metadaten liest, bietet zahlreiche praktische Vorteile:

1. **Datensicherungsverwaltung:** Überprüfen Sie schnell die Integrität und Vollständigkeit von Backup-Archiven.
2. **File Synchronization Tools:** Änderungsdaten verwenden, um zu entscheiden, welche Dateien aktualisiert werden müssen.
3. **Speicheroptimierung:** Komprimierte und unkomprimierte Größen vergleichen, um die Kapazität zu planen.

Eine Integration mit anderen Systemen ist möglich, sodass die automatisierte Metadatenextraktion als Teil größerer Daten‑Management‑Workflows erfolgen kann.

## Leistungsüberlegungen

Beim Arbeiten mit GroupDocs.Metadata und großen Archiven sollten Sie diese Tipps beachten:

- **Stapelverarbeitung:** Dateien stapelweise verarbeiten, um den Speicherverbrauch effektiv zu steuern.
- **Effiziente Ausnahmebehandlung:** Verwenden Sie try-with-resources für die automatische Ressourcenverwaltung.
- **Asynchrone Verarbeitung:** Asynchrone Techniken für schwere Arbeitslasten Implementierung.

## Häufige Probleme und Lösungen

| Problem | Lösung |
|-------|----------|
| **`NullPointerException` beim Zugriff auf eine Datei** | Stellen Sie sicher, dass der Pfad zum Archiv korrekt ist und die Datei nicht beschädigt ist. |
| **Speicherspitzen bei riesigen Archiven** | Aktivieren Sie die Stapelverarbeitung oder erhöhen Sie die JVM-Heap-Größe (`-Xmx`). |
| **Lizenz nicht erkannt** | Stellen Sie sicher, dass die Lizenzdatei im Arbeitsverzeichnis der Anwendung liegt oder über `License.setLicense(path)` gesetzt wird. |

## Häufig gestellte Fragen

**F:** Was ist GroupDocs.Metadata?
**A:** Es ist eine Java-Bibliothek zum Umgang mit Metadaten über verschiedene Dateiformate hinweg, einschließlich SevenZip-Archiven.

**F:** Kann ich GroupDocs.Metadata ohne Maven verwenden?
**A:** Ja, Sie können das JAR von der offiziellen Website herunterladen und zu Ihrem Projekt‑Klassenpfad hinzufügen.

**F:** Wie gehe ich effizient mit großen Archiven um?
**A:** Implementieren Sie Stapelverarbeitung oder verwenden Sie asynchrone Streams, um den Speicherverbrauch zu begrenzen.

**F:** Wo finde ich detaillierte Anleitungen?
**A:** Siehe die [offizielle Dokumentation](https://docs.groupdocs.com/metadata/java/) für umfassende API-Referenzen.

**F:** Was tun, wenn ich Probleme mit der Bibliothek habe?
**A:** Fragen Sie die Community im [GroupDocs Support‑Forum](https://forum.groupdocs.com/c/metadata/).

## Ressourcen

- **Dokumentation:** Weitere Informationen finden Sie unter [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)
- **API-Referenz:** Detaillierte API-Informationen finden Sie unter [GroupDocs.API-Referenz](https://reference.groupdocs.com/metadata/java/)
- **Download:** Die neueste Version erhalten Sie von [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/)
- **GitHub Repository:** Code-Beispiele finden Sie auf [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- **Kostenloses Support-Forum:** Nehmen Sie an Diskussionen teil oder stellen Sie Fragen im [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**Zuletzt aktualisiert:** 2025-12-20  
**Getestet mit:** GroupDocs.Metadata 24.12 für Java  
**Autor:** GroupDocs