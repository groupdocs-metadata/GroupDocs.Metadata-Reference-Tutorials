---
title: Aktualisieren integrierter Eigenschaften in Tabellenkalkulationen mithilfe von .NET
linktitle: Aktualisieren integrierter Eigenschaften in Tabellenkalkulationen mithilfe von .NET
second_title: GroupDocs.Metadata .NET-API
description: Erfahren Sie, wie Sie integrierte Metadateneigenschaften in Excel-Dateien mit GroupDocs.Metadata für .NET aktualisieren. Ändern Sie Autor, Erstellungszeit, Unternehmen und mehr mit C#.
type: docs
weight: 14
url: /de/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## Einführung
In diesem Tutorial erfahren Sie, wie Sie GroupDocs.Metadata für .NET nutzen können, um integrierte Eigenschaften in Tabellenkalkulationsdateien mit C# zu aktualisieren. GroupDocs.Metadata ist eine leistungsstarke API, mit der Entwickler Metadateneigenschaften aus verschiedenen Dateiformaten, einschließlich Tabellenkalkulationen, lesen, bearbeiten und entfernen können. Wir konzentrieren uns insbesondere auf das Ändern von Eigenschaften wie Autor, Erstellungszeit, Unternehmen, Kategorie und Schlüsselwörtern in Excel-Dateien.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Visual Studio: Installieren Sie die neueste Version von Visual Studio.
-  GroupDocs.Metadata für .NET: Laden Sie GroupDocs.Metadata für .NET herunter und installieren Sie es von der[Download-Seite](https://releases.groupdocs.com/metadata/net/).
- Grundlegende C#-Kenntnisse: Verständnis der Programmiersprache C# und des .NET-Frameworks.

## Namespaces importieren
Beginnen Sie mit dem Importieren der erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Schritt 1: Laden Sie die Tabellenkalkulationsdatei
 Initialisieren Sie zunächst a`Metadata` Objekt durch Laden der Eingabetabellendatei:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Zugriff auf Dokumenteigenschaften im Stammverzeichnis
}
```
## Schritt 2: Integrierte Eigenschaften aktualisieren
 Greifen Sie auf die integrierten Dokumenteigenschaften zu über`SpreadsheetRootPackage` und ändern Sie sie nach Bedarf:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Stellen Sie sicher, dass Sie Platzhalter ersetzen (`YourAuthorName`, `YourCompany`, `YourCategory`mit tatsächlichen Werten, die Sie für die Eigenschaften festlegen möchten.
## Schritt 3: Änderungen speichern
Speichern Sie die Änderungen nach dem Aktualisieren der Eigenschaften wieder in der Tabellendatei:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Abschluss
In diesem Tutorial haben wir gezeigt, wie Sie GroupDocs.Metadata für .NET verwenden, um integrierte Eigenschaften von Tabellenkalkulationsdateien programmgesteuert zu aktualisieren. Durch die Nutzung dieser API können Entwickler Metadaten in Excel-Dokumenten effizient verwalten und so die Datenorganisation und -zugänglichkeit verbessern.

## Häufig gestellte Fragen
### Welche Dateiformate unterstützt GroupDocs.Metadata?
GroupDocs.Metadata unterstützt eine Vielzahl von Dateiformaten, darunter Microsoft Office-Dokumente, PDFs, Bilder, Audiodateien und mehr.
### Kann ich vorhandene Metadateneigenschaften aus Dateien abrufen?
Ja, Sie können Metadateneigenschaften wie Autor, Erstellungsdatum, Schlüsselwörter und benutzerdefinierte Eigenschaften mit GroupDocs.Metadata extrahieren und lesen.
### Ist GroupDocs.Metadata mit .NET Core kompatibel?
Ja, GroupDocs.Metadata ist sowohl mit .NET Framework als auch .NET Core kompatibel.
### Bietet GroupDocs.Metadata eine kostenlose Testversion?
 Ja, Sie können eine kostenlose Testversion von GroupDocs.Metadata herunterladen unter[Hier](https://releases.groupdocs.com/).
### Wo finde ich Unterstützung für GroupDocs.Metadata?
 Für Unterstützung und Diskussionen besuchen Sie die[GroupDocs.Metadata-Forum](https://forum.groupdocs.com/c/metadata/14).