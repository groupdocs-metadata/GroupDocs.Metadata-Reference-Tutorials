---
title: Aggiorna le proprietà integrate nei PDF utilizzando .NET
linktitle: Aggiorna le proprietà integrate nei PDF utilizzando .NET
second_title: API GroupDocs.Metadata .NET
description: Scopri come aggiornare le proprietà del documento PDF utilizzando C# e GroupDocs.Metadata per .NET. Modifica autore, titolo, parole chiave e altro in modo programmatico.
weight: 15
url: /it/net/pdf-metadata/update-built-in-properties-pdfs/
type: docs
---
# Aggiorna le proprietà integrate nei PDF utilizzando .NET

## introduzione
In questo tutorial impareremo come utilizzare GroupDocs.Metadata per .NET per aggiornare le proprietà integrate dei documenti PDF. Questa libreria fornisce un potente set di strumenti per manipolare i metadati all'interno di vari formati di documenti. Esamineremo i passaggi necessari per modificare proprietà come autore, titolo, data di creazione, parole chiave, creatore e produttore in un file PDF utilizzando C#.
## Prerequisiti
Prima di iniziare, assicurati di avere a disposizione quanto segue:
-  GroupDocs.Metadata per .NET Library: scarica la libreria da[Qui](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: installa Visual Studio per scrivere ed eseguire il codice C#.
- Conoscenza di base di C#: si consiglia la familiarità con il linguaggio di programmazione C#.

## Importa spazi dei nomi
Inizia includendo gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Passaggio 1: inizializza l'oggetto metadati
 Inizia inizializzando a`Metadata`oggetto con il percorso del file PDF:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Il tuo codice andrà qui
}
```
## Passaggio 2: accedi al pacchetto root PDF
 Successivamente, recupera il pacchetto root specifico per l'utilizzo di PDF`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Passaggio 3: aggiorna le proprietà del documento
 Ora aggiorna le proprietà desiderate del documento PDF all'interno del file`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Passaggio 4: salva le modifiche
Dopo aver modificato le proprietà, salva nuovamente le modifiche nel file PDF:
```csharp
metadata.Save("Your Output File Path");
```
## Passaggio 5: recuperare le proprietà aggiornate
Per verificare le modifiche, ricaricare i metadati e recuperare le proprietà aggiornate:
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

## Conclusione
In questo tutorial, abbiamo esplorato come sfruttare GroupDocs.Metadata per .NET per aggiornare a livello di codice le proprietà integrate dei documenti PDF. Seguendo i passaggi descritti, puoi gestire e modificare in modo efficiente i metadati all'interno dei file PDF utilizzando C#. Sentiti libero di esplorare ulteriori funzionalità e capacità offerte da GroupDocs.Metadata per una manipolazione completa dei metadati.

## Domande frequenti
### D: Cos'è GroupDocs.Metadata per .NET?
R: GroupDocs.Metadata per .NET è una libreria che consente agli sviluppatori di leggere, modificare, rimuovere e manipolare i metadati in vari formati di documenti a livello di codice.
### D: Dove posso trovare la documentazione per GroupDocs.Metadata per .NET?
 R: Puoi accedere alla documentazione[Qui](https://tutorials.groupdocs.com/metadata/net/).
### D: Come posso scaricare GroupDocs.Metadata per .NET?
 R: Puoi scaricare GroupDocs.Metadata per .NET da[questo link](https://releases.groupdocs.com/metadata/net/).
### D: È disponibile una prova gratuita?
 R: Sì, puoi ottenere una versione di prova gratuita[Qui](https://releases.groupdocs.com/).
### D: Dove posso ottenere supporto per GroupDocs.Metadata per .NET?
 R: Per assistenza, visita il forum GroupDocs.Metadata[Qui](https://forum.groupdocs.com/c/metadata/14).