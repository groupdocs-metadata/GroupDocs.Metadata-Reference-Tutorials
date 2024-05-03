---
title: Aggiorna le proprietà integrate nei fogli di calcolo utilizzando .NET
linktitle: Aggiorna le proprietà integrate nei fogli di calcolo utilizzando .NET
second_title: API GroupDocs.Metadata .NET
description: Scopri come aggiornare le proprietà dei metadati integrate nei file Excel utilizzando GroupDocs.Metadata per .NET. Modifica autore, ora di creazione, azienda e altro ancora con C#.
type: docs
weight: 14
url: /it/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## introduzione
In questo tutorial esploreremo come utilizzare GroupDocs.Metadata per .NET per aggiornare le proprietà integrate nei file di fogli di calcolo utilizzando C#. GroupDocs.Metadata è una potente API che consente agli sviluppatori di leggere, modificare e rimuovere le proprietà dei metadati da vari formati di file, inclusi i fogli di calcolo. Ci concentreremo in particolare sulla modifica di proprietà come autore, ora di creazione, azienda, categoria e parole chiave all'interno dei file Excel.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Visual Studio: installa la versione più recente di Visual Studio.
-  GroupDocs.Metadata per .NET: scaricare e installare GroupDocs.Metadata per .NET dal[pagina di download](https://releases.groupdocs.com/metadata/net/).
- Conoscenza di base di C#: comprensione del linguaggio di programmazione C# e del framework .NET.

## Importa spazi dei nomi
Inizia importando gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Passaggio 1: caricare il file del foglio di calcolo
 Innanzitutto, inizializza a`Metadata` oggetto caricando il file del foglio di calcolo di input:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Accedi alle proprietà del documento all'interno di root
}
```
## Passaggio 2: aggiorna le proprietà integrate
 Accedi alle proprietà del documento integrate tramite`SpreadsheetRootPackage` e modificarli secondo necessità:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Assicurarsi di sostituire i segnaposto (`YourAuthorName`, `YourCompany`, `YourCategory`con i valori effettivi che desideri impostare per le proprietà.
## Passaggio 3: salva le modifiche
Dopo aver aggiornato le proprietà, salva nuovamente le modifiche nel file del foglio di calcolo:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Conclusione
In questa esercitazione è stato dimostrato come utilizzare GroupDocs.Metadata per .NET per aggiornare a livello di codice le proprietà integrate dei file di fogli di calcolo. Sfruttando questa API, gli sviluppatori possono gestire in modo efficiente i metadati all'interno dei documenti Excel, migliorando l'organizzazione e l'accessibilità dei dati.

## Domande frequenti
### Quali formati di file supporta GroupDocs.Metadata?
GroupDocs.Metadata supporta un'ampia gamma di formati di file, inclusi documenti di Microsoft Office, PDF, immagini, file audio e altro ancora.
### Posso recuperare le proprietà dei metadati esistenti dai file?
Sì, puoi estrarre e leggere proprietà dei metadati come autore, data di creazione, parole chiave e proprietà personalizzate utilizzando GroupDocs.Metadata.
### GroupDocs.Metadata è compatibile con .NET Core?
Sì, GroupDocs.Metadata è compatibile sia con .NET Framework che con .NET Core.
### GroupDocs.Metadata fornisce una prova gratuita?
 Sì, puoi scaricare una prova gratuita di GroupDocs.Metadata da[Qui](https://releases.groupdocs.com/).
### Dove posso trovare supporto per GroupDocs.Metadata?
 Per supporto e discussioni, visitare il[Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).