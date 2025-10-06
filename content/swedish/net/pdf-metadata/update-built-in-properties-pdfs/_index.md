---
title: Uppdatera inbyggda egenskaper i PDF-filer med .NET
linktitle: Uppdatera inbyggda egenskaper i PDF-filer med .NET
second_title: GroupDocs.Metadata .NET API
description: Lär dig hur du uppdaterar PDF-dokumentegenskaper med C# och GroupDocs.Metadata för .NET. Ändra författare, titel, sökord och mer programmatiskt.
weight: 15
url: /sv/net/pdf-metadata/update-built-in-properties-pdfs/
type: docs
---
# Uppdatera inbyggda egenskaper i PDF-filer med .NET

## Introduktion
I den här handledningen kommer vi att lära oss hur du använder GroupDocs.Metadata för .NET för att uppdatera inbyggda egenskaper för PDF-dokument. Detta bibliotek tillhandahåller en kraftfull uppsättning verktyg för att manipulera metadata inom olika dokumentformat. Vi går igenom de nödvändiga stegen för att ändra egenskaper som författare, titel, skapelsedatum, nyckelord, skapare och producent i en PDF-fil med C#.
## Förutsättningar
Innan vi börjar, se till att du har följande på plats:
-  GroupDocs.Metadata for .NET Library: Ladda ner biblioteket från[här](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: Installera Visual Studio för att skriva och köra C#-koden.
- Grundläggande förståelse för C#: Bekantskap med programmeringsspråket C# rekommenderas.

## Importera namnområden
Börja med att inkludera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Steg 1: Initiera metadataobjekt
 Börja med att initiera a`Metadata`objekt med sökvägen till din PDF-fil:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Din kod kommer hit
}
```
## Steg 2: Få åtkomst till PDF Root Package
 Hämta sedan rotpaketet specifikt för PDF-användning`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Steg 3: Uppdatera dokumentegenskaper
 Uppdatera nu de önskade egenskaperna för PDF-dokumentet i`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Steg 4: Spara ändringar
När du har ändrat egenskaperna, spara ändringarna tillbaka till PDF-filen:
```csharp
metadata.Save("Your Output File Path");
```
## Steg 5: Hämta uppdaterade egenskaper
För att verifiera ändringarna, ladda om metadata och hämta de uppdaterade egenskaperna:
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

## Slutsats
I den här handledningen undersökte vi hur man kan utnyttja GroupDocs.Metadata för .NET för att uppdatera inbyggda egenskaper för PDF-dokument programmatiskt. Genom att följa de skisserade stegen kan du effektivt hantera och ändra metadata i PDF-filer med C#. Utforska gärna fler funktioner och möjligheter som erbjuds av GroupDocs.Metadata för omfattande metadatamanipulation.

## FAQ's
### F: Vad är GroupDocs.Metadata för .NET?
S: GroupDocs.Metadata för .NET är ett bibliotek som låter utvecklare läsa, redigera, ta bort och manipulera metadata i olika dokumentformat programmatiskt.
### F: Var kan jag hitta dokumentationen för GroupDocs.Metadata for .NET?
 S: Du kan komma åt dokumentationen[här](https://tutorials.groupdocs.com/metadata/net/).
### F: Hur kan jag ladda ner GroupDocs.Metadata för .NET?
 S: Du kan ladda ner GroupDocs.Metadata för .NET från[den här länken](https://releases.groupdocs.com/metadata/net/).
### F: Finns det en gratis provperiod?
 S: Ja, du kan få en gratis testversion[här](https://releases.groupdocs.com/).
### F: Var kan jag få support för GroupDocs.Metadata for .NET?
 S: För support besök forumet GroupDocs.Metadata[här](https://forum.groupdocs.com/c/metadata/14).