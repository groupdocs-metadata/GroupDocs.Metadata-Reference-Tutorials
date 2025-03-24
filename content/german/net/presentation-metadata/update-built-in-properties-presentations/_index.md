---
title: Aktualisieren Sie integrierte Eigenschaften in Präsentationen mit .NET
linktitle: Aktualisieren Sie integrierte Eigenschaften in Präsentationen mit .NET
second_title: GroupDocs.Metadata .NET-API
description: Erfahren Sie, wie Sie integrierte Eigenschaften in Präsentationen mithilfe von .NET mit GroupDocs.Metadata, einer vielseitigen Bibliothek zur Metadatenbearbeitung, aktualisieren.
weight: 15
url: /de/net/presentation-metadata/update-built-in-properties-presentations/
---
## Einführung
In diesem Tutorial befassen wir uns mit den leistungsstarken Funktionen von GroupDocs.Metadata für .NET, einer umfassenden Bibliothek zur Bearbeitung von Metadaten in Dokumenten mithilfe des .NET-Frameworks. Insbesondere konzentrieren wir uns auf die programmgesteuerte Aktualisierung integrierter Eigenschaften in Präsentationen (.PPT- und .PPTX-Dateien) mithilfe von C#.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:
- Visual Studio: Auf Ihrem System installiert.
-  GroupDocs.Metadata für .NET: Heruntergeladen und installiert von[Hier](https://releases.groupdocs.com/metadata/net/).
- Grundlegende C#-Kenntnisse: Vertrautheit mit der Programmiersprache C#.

## Namespaces importieren
Beginnen Sie mit dem Importieren der erforderlichen Namespaces in Ihr C#-Projekt:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Schritt 1: Laden Sie die Präsentationsdatei
 Erstellen Sie zunächst eine neue Instanz von`Metadata` indem Sie Ihre Präsentationsdatei laden:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Schritt 2: Integrierte Eigenschaften aktualisieren
Aktualisieren Sie nun die gewünschten integrierten Eigenschaften der Präsentation. Sie können beispielsweise den Autor, das Erstellungsdatum, das Unternehmen, die Kategorie, Schlüsselwörter usw. ändern. So können Sie das tun:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## Schritt 3: Änderungen speichern
Speichern Sie die Änderungen nach dem Aktualisieren der Eigenschaften wieder in der Präsentationsdatei:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Abschluss
In diesem Tutorial haben wir untersucht, wie Sie mit GroupDocs.Metadata für .NET integrierte Eigenschaften in Präsentationsdateien programmgesteuert aktualisieren können. Indem Sie diese Schritte befolgen, können Sie Metadaten in Ihren .NET-Anwendungen effizient verwalten und ändern.

## Häufig gestellte Fragen
### F: Was ist GroupDocs.Metadata für .NET?
A: GroupDocs.Metadata für .NET ist eine leistungsstarke Bibliothek zur Metadatenbearbeitung für das .NET-Framework, die es Entwicklern ermöglicht, Metadaten in verschiedenen Dokumentformaten zu lesen, zu schreiben und zu bearbeiten.
### F: Wo finde ich Dokumentation für GroupDocs.Metadata?
 A: Sie können auf die ausführliche Dokumentation zugreifen[Hier](https://tutorials.groupdocs.com/metadata/net/).
### F: Wie kann ich eine temporäre Lizenz für GroupDocs.Metadata erhalten?
 A: Sie können eine temporäre Lizenz erwerben[Hier](https://purchase.groupdocs.com/temporary-license/).
### F: Unterstützt GroupDocs.Metadata neben Präsentationen auch andere Dateiformate?
A: Ja, GroupDocs.Metadata unterstützt eine breite Palette von Formaten, darunter Dokumente, Tabellen, Bilder, Videos und mehr.
### F: Wo kann ich Support erhalten oder Fragen zu GroupDocs.Metadata stellen?
 A: Für Unterstützung und Diskussionen besuchen Sie die[GroupDocs.Metadata-Forum](https://forum.groupdocs.com/c/metadata/14).