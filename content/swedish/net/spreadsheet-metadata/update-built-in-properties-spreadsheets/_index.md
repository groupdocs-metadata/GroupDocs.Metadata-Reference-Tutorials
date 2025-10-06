---
title: Uppdatera inbyggda egenskaper i kalkylblad med .NET
linktitle: Uppdatera inbyggda egenskaper i kalkylblad med .NET
second_title: GroupDocs.Metadata .NET API
description: Lär dig hur du uppdaterar inbyggda metadataegenskaper i Excel-filer med GroupDocs.Metadata för .NET. Ändra författare, skapelsetid, företag och mer med C#.
weight: 14
url: /sv/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
type: docs
---
# Uppdatera inbyggda egenskaper i kalkylblad med .NET

## Introduktion
I den här handledningen kommer vi att utforska hur man använder GroupDocs.Metadata för .NET för att uppdatera inbyggda egenskaper i kalkylarksfiler med C#. GroupDocs.Metadata är ett kraftfullt API som låter utvecklare läsa, redigera och ta bort metadataegenskaper från olika filformat, inklusive kalkylblad. Vi kommer att fokusera specifikt på att ändra egenskaper som författare, skapelsetid, företag, kategori och nyckelord i Excel-filer.
## Förutsättningar
Innan vi börjar, se till att du har följande:
- Visual Studio: Installera den senaste versionen av Visual Studio.
-  GroupDocs.Metadata for .NET: Ladda ner och installera GroupDocs.Metadata for .NET från[nedladdningssida](https://releases.groupdocs.com/metadata/net/).
- Grundläggande C#-kunskaper: Förståelse av C#-programmeringsspråk och .NET-ramverk.

## Importera namnområden
Börja med att importera de nödvändiga namnrymden i ditt C#-projekt:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Steg 1: Ladda kalkylarksfilen
 Initiera först a`Metadata` objekt genom att ladda indatakalkylarksfilen:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Få åtkomst till dokumentegenskaper inom root
}
```
## Steg 2: Uppdatera inbyggda egenskaper
 Få åtkomst till de inbyggda dokumentegenskaperna via`SpreadsheetRootPackage` och ändra dem efter behov:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Se till att ersätta platshållare (`YourAuthorName`, `YourCompany`, `YourCategory`med faktiska värden du vill ställa in för egenskaperna.
## Steg 3: Spara ändringar
När du har uppdaterat egenskaperna sparar du ändringarna tillbaka till kalkylarksfilen:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Slutsats
I den här handledningen har vi visat hur man använder GroupDocs.Metadata för .NET för att uppdatera inbyggda egenskaper för kalkylarksfiler programmatiskt. Genom att utnyttja detta API kan utvecklare effektivt hantera metadata i Excel-dokument, vilket förbättrar dataorganisation och tillgänglighet.

## FAQ's
### Vilka filformat stöder GroupDocs.Metadata?
GroupDocs.Metadata stöder ett brett utbud av filformat, inklusive Microsoft Office-dokument, PDF-filer, bilder, ljudfiler och mer.
### Kan jag hämta befintliga metadataegenskaper från filer?
Ja, du kan extrahera och läsa metadataegenskaper som författare, skapelsedatum, nyckelord och anpassade egenskaper med GroupDocs.Metadata.
### Är GroupDocs.Metadata kompatibel med .NET Core?
Ja, GroupDocs.Metadata är kompatibel med både .NET Framework och .NET Core.
### Ger GroupDocs.Metadata en gratis provperiod?
 Ja, du kan ladda ner en gratis testversion av GroupDocs.Metadata från[här](https://releases.groupdocs.com/).
### Var kan jag hitta support för GroupDocs.Metadata?
 För support och diskussioner, besök[GroupDocs.Metadata-forum](https://forum.groupdocs.com/c/metadata/14).