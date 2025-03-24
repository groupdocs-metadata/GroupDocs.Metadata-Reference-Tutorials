---
title: Integrierte Eigenschaften in PDFs mit .NET aktualisieren
linktitle: Integrierte Eigenschaften in PDFs mit .NET aktualisieren
second_title: GroupDocs.Metadata .NET-API
description: Erfahren Sie, wie Sie PDF-Dokumenteigenschaften mit C# und GroupDocs.Metadata für .NET aktualisieren. Ändern Sie Autor, Titel, Schlüsselwörter und mehr programmgesteuert.
weight: 15
url: /de/net/pdf-metadata/update-built-in-properties-pdfs/
---
## Einführung
In diesem Tutorial lernen wir, wie man GroupDocs.Metadata für .NET verwendet, um integrierte Eigenschaften von PDF-Dokumenten zu aktualisieren. Diese Bibliothek bietet einen leistungsstarken Satz von Tools zum Bearbeiten von Metadaten in verschiedenen Dokumentformaten. Wir gehen die notwendigen Schritte durch, um Eigenschaften wie Autor, Titel, Erstellungsdatum, Schlüsselwörter, Ersteller und Produzent in einer PDF-Datei mit C# zu ändern.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:
-  GroupDocs.Metadata für .NET-Bibliothek: Laden Sie die Bibliothek herunter von[Hier](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: Installieren Sie Visual Studio, um den C#-Code zu schreiben und auszuführen.
- Grundlegende Kenntnisse in C#: Vertrautheit mit der Programmiersprache C# wird empfohlen.

## Namespaces importieren
Fügen Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt ein:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Schritt 1: Metadatenobjekt initialisieren
 Beginnen Sie mit der Initialisierung von a`Metadata`Objekt mit dem Pfad zu Ihrer PDF-Datei:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Ihr Code wird hier angezeigt
}
```
## Schritt 2: Greifen Sie auf das PDF-Root-Paket zu
 Rufen Sie als Nächstes das Root-Paket speziell für die PDF-Verwendung ab`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Schritt 3: Dokumenteigenschaften aktualisieren
 Aktualisieren Sie nun die gewünschten Eigenschaften des PDF-Dokuments innerhalb`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Schritt 4: Änderungen speichern
Speichern Sie die Änderungen nach dem Ändern der Eigenschaften wieder in der PDF-Datei:
```csharp
metadata.Save("Your Output File Path");
```
## Schritt 5: Aktualisierte Eigenschaften abrufen
Um die Änderungen zu überprüfen, laden Sie die Metadaten neu und rufen Sie die aktualisierten Eigenschaften ab:
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## Abschluss
In diesem Tutorial haben wir untersucht, wie Sie GroupDocs.Metadata für .NET nutzen können, um integrierte Eigenschaften von PDF-Dokumenten programmgesteuert zu aktualisieren. Wenn Sie die beschriebenen Schritte befolgen, können Sie Metadaten in PDF-Dateien mit C# effizient verwalten und ändern. Entdecken Sie gerne weitere Funktionen und Möglichkeiten von GroupDocs.Metadata für eine umfassende Metadatenbearbeitung.

## Häufig gestellte Fragen
### F: Was ist GroupDocs.Metadata für .NET?
A: GroupDocs.Metadata für .NET ist eine Bibliothek, die es Entwicklern ermöglicht, Metadaten in verschiedenen Dokumentformaten programmgesteuert zu lesen, zu bearbeiten, zu entfernen und zu manipulieren.
### F: Wo finde ich die Dokumentation für GroupDocs.Metadata für .NET?
 A: Sie können auf die Dokumentation zugreifen[Hier](https://tutorials.groupdocs.com/metadata/net/).
### F: Wie kann ich GroupDocs.Metadata für .NET herunterladen?
 A: Sie können GroupDocs.Metadata für .NET herunterladen von[dieser Link](https://releases.groupdocs.com/metadata/net/).
### F: Gibt es eine kostenlose Testversion?
 A: Ja, Sie können eine kostenlose Testversion erhalten[Hier](https://releases.groupdocs.com/).
### F: Wo erhalte ich Support für GroupDocs.Metadata für .NET?
 A: Für Support besuchen Sie das GroupDocs.Metadata-Forum[Hier](https://forum.groupdocs.com/c/metadata/14).