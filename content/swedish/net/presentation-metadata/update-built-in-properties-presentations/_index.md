---
title: Uppdatera inbyggda egenskaper i presentationer med .NET
linktitle: Uppdatera inbyggda egenskaper i presentationer med .NET
second_title: GroupDocs.Metadata .NET API
description: Lär dig hur du uppdaterar inbyggda egenskaper i presentationer med .NET med GroupDocs.Metadata, ett mångsidigt bibliotek för metadatamanipulation.
weight: 15
url: /sv/net/presentation-metadata/update-built-in-properties-presentations/
type: docs
---
# Uppdatera inbyggda egenskaper i presentationer med .NET

## Introduktion
den här handledningen kommer vi att fördjupa oss i de kraftfulla funktionerna i GroupDocs.Metadata for .NET, ett omfattande bibliotek som är utformat för att manipulera metadata i dokument med .NET-ramverket. Specifikt kommer vi att fokusera på att uppdatera inbyggda egenskaper i presentationer (.PPT- och .PPTX-filer) programmatiskt med C#.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Visual Studio: Installerad på ditt system.
-  GroupDocs.Metadata for .NET: Laddas ner och installeras från[här](https://releases.groupdocs.com/metadata/net/).
- Grundläggande C#-kunskaper: Bekantskap med programmeringsspråket C#.

## Importera namnområden
Börja med att importera de nödvändiga namnrymden till ditt C#-projekt:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Steg 1: Ladda presentationsfilen
 Skapa först en ny instans av`Metadata` genom att ladda din presentationsfil:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Steg 2: Uppdatera inbyggda egenskaper
Uppdatera nu de önskade inbyggda egenskaperna för presentationen. Du kan till exempel ändra författare, skapandedatum, företag, kategori, nyckelord, etc. Så här gör du:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## Steg 3: Spara ändringar
När du har uppdaterat egenskaperna, spara ändringarna tillbaka till presentationsfilen:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Slutsats
den här handledningen undersökte vi hur man använder GroupDocs.Metadata för .NET för att uppdatera inbyggda egenskaper i presentationsfiler programmatiskt. Genom att följa dessa steg kan du effektivt hantera och ändra metadata i dina .NET-applikationer.

## FAQ's
### F: Vad är GroupDocs.Metadata för .NET?
S: GroupDocs.Metadata för .NET är ett kraftfullt bibliotek för metadatamanipulation för .NET-ramverket, som gör det möjligt för utvecklare att läsa, skriva och redigera metadata i olika dokumentformat.
### F: Var kan jag hitta dokumentation för GroupDocs.Metadata?
 S: Du kan komma åt den detaljerade dokumentationen[här](https://tutorials.groupdocs.com/metadata/net/).
### F: Hur kan jag få en tillfällig licens för GroupDocs.Metadata?
 S: Du kan skaffa en tillfällig licens[här](https://purchase.groupdocs.com/temporary-license/).
### F: Stöder GroupDocs.Metadata andra filformat än presentationer?
S: Ja, GroupDocs.Metadata stöder ett brett utbud av format inklusive dokument, kalkylblad, bilder, videor och mer.
### F: Var kan jag få support eller ställa frågor om GroupDocs.Metadata?
 S: För support och diskussioner, besök[GroupDocs.Metadata-forum](https://forum.groupdocs.com/c/metadata/14).