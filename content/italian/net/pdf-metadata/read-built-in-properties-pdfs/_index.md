---
title: Leggi le proprietà integrate dai PDF in .NET
linktitle: Leggi le proprietà integrate dai PDF in .NET
second_title: API GroupDocs.Metadata .NET
description: Scopri come leggere i metadati PDF in .NET utilizzando GroupDocs.Metadata. Accedi a nomi di autori, date di creazione, argomenti e altro ancora con il codice C#.
weight: 10
url: /it/net/pdf-metadata/read-built-in-properties-pdfs/
---
## introduzione
In questo tutorial esploreremo come sfruttare GroupDocs.Metadata per .NET per leggere le proprietà integrate dai file PDF. GroupDocs.Metadata è una potente libreria che consente agli sviluppatori di lavorare con metadati associati a vari formati di documenti, inclusi PDF, documenti di Microsoft Office, immagini e altro. Utilizzando questa libreria, puoi accedere e manipolare facilmente gli attributi dei metadati incorporati nei file PDF, come nomi degli autori, date di creazione, argomenti e altro.
## Prerequisiti
Prima di immergerti in questo tutorial, assicurati di possedere i seguenti prerequisiti:
- Visual Studio: assicurati di avere Visual Studio installato sul tuo computer.
-  GroupDocs.Metadata per .NET: scarica e installa GroupDocs.Metadata per .NET da[Qui](https://releases.groupdocs.com/metadata/net/).
- Conoscenza di base di C#: familiarità con il linguaggio di programmazione C# e il framework .NET.

## Importa spazi dei nomi
Inizia aggiungendo gli spazi dei nomi necessari al tuo progetto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Passaggio 1: carica i metadati del PDF
Innanzitutto, carica il file PDF ed estrai i suoi metadati utilizzando GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // Accedi al pacchetto root del file PDF
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Recupera e visualizza le proprietà integrate
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // È possibile accedere ad altre proprietà in modo simile
    // ...
}
```
Oltre a leggere i metadati, GroupDocs.Metadata consente operazioni avanzate come la modifica, la rimozione o l'aggiunta di nuove proprietà dei metadati ai file PDF a livello di codice. Questa flessibilità consente la gestione completa dei metadati dei documenti all'interno delle applicazioni .NET.
## Conclusione
In questo tutorial abbiamo spiegato come utilizzare GroupDocs.Metadata per .NET per estrarre le proprietà integrate dai file PDF utilizzando C#. Integrando questa libreria nei tuoi progetti, puoi gestire senza problemi le operazioni sui metadati dei documenti, fornendo funzionalità avanzate di gestione dei documenti.

## Domande frequenti
### GroupDocs.Metadata può funzionare con altri formati di documenti?
Sì, GroupDocs.Metadata supporta vari formati di documenti come DOCX, XLSX, PPTX, PDF, JPG, PNG e altri.
### È disponibile una prova gratuita per GroupDocs.Metadata?
Sì, puoi accedere a una prova gratuita di GroupDocs.Metadata da[Qui](https://releases.groupdocs.com/).
### Come posso modificare le proprietà dei metadati utilizzando GroupDocs.Metadata?
È possibile modificare le proprietà dei metadati a livello di codice accedendo al pacchetto di documenti corrispondente e impostando nuovi valori.
### GroupDocs.Metadata supporta .NET Core?
Sì, GroupDocs.Metadata è compatibile sia con .NET Framework che con .NET Core.
### Dove posso trovare supporto o porre domande relative a GroupDocs.Metadata?
 Per supporto e discussioni, visitare il[Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).