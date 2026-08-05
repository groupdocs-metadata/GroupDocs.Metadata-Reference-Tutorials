---
date: '2026-08-05'
description: Scopri come rilevare la versione PDF in Java e aggiornare i metadati
  PDF usando GroupDocs.Metadata per Java. Include version detection, reading properties,
  and metadata editing.
keywords:
- detect pdf version java
- update pdf metadata java
- groupdocs.metadata java
lastmod: '2026-08-05'
og_description: Rileva la versione PDF in Java e aggiorna i metadati PDF con GroupDocs.Metadata.
  Guida passo‑passo Java mostra version detection, reading properties e editing metadata.
og_image_alt: Guide showing Java code for detecting PDF version and updating metadata
  using GroupDocs.Metadata
og_title: Rileva la versione PDF in Java e aggiorna i metadati PDF
schemas:
- author: GroupDocs
  dateModified: '2026-08-05'
  description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  headline: Detect PDF version java and update PDF metadata
  type: TechArticle
- description: Learn how to detect PDF version java and update PDF metadata using
    GroupDocs.Metadata for Java. Includes version detection, reading properties, and
    metadata editing.
  name: Detect PDF version java and update PDF metadata
  steps:
  - name: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
    text: '**Open the PDF** – instantiate the `Metadata` object (see initialization
      above).'
  - name: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
    text: '**Access the PDF‑specific root package** – call `metadata.getRootPackage()`.'
  - name: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
    text: '**Retrieve the version** – invoke `pdfRoot.getVersion()`; the returned
      string contains the version number.'
  - name: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
    text: '**Compliance audits** – Verify that all PDFs meet a minimum version (e.g., 1.7)
      before legal filing.'
  - name: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
    text: '**Automated archiving** – Tag PDFs with author, department, and creation
      date for easier retrieval.'
  - name: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
    text: '**Document management integration** – Enrich PDFs with custom properties
      that DMS platforms can index.'
  - name: '**Report generation** – Insert version information into automatically generated
      reports.'
    text: '**Report generation** – Insert version information into automatically generated
      reports.'
  - name: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
    text: '**Cross‑platform testing** – Detect version mismatches that could cause
      rendering issues on older viewers.'
  type: HowTo
- questions:
  - answer: Yes, but you must supply the password when creating the `Metadata` object.
    question: Can I update metadata on password‑protected PDFs?
  - answer: Absolutely. You can read and write custom XMP fields through the same
      API.
    question: Does GroupDocs.Metadata support custom XMP properties?
  - answer: The library can report the version; changing it requires saving the document
      with a different version profile, which is supported via additional save options.
    question: Is it possible to change the PDF version itself?
  - answer: The getters will return `null`. You can safely call the setters to create
      new metadata entries.
    question: What happens if the PDF has no existing metadata?
  - answer: A commercial license is required for production deployments; the trial
      is limited to evaluation purposes.
    question: Are there any licensing restrictions for commercial use?
  type: FAQPage
tags:
- detect pdf version
- update pdf metadata
- groupdocs.metadata
- java pdf processing
title: Rileva la versione PDF in Java e aggiorna i metadati PDF
type: docs
url: /it/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# Rilevare la versione PDF java e aggiornare i metadati PDF

Gestire i file PDF in modo programmatico spesso richiede di **rilevare la versione PDF java** e **aggiornare i metadati PDF** — autore, titolo, data di creazione o persino la versione PDF stessa. Metadati incoerenti possono causare problemi di rendering o rendere più difficile individuare i documenti in un ampio archivio. Questo tutorial ti guida nella rilevazione della versione PDF e nell'aggiornamento dei metadati PDF usando **GroupDocs.Metadata** per Java, offrendoti un modo affidabile per mantenere i tuoi PDF ordinati, ricercabili e compatibili con qualsiasi visualizzatore.

## Risposte rapide
- **Che cosa significa “aggiornare i metadati PDF”?** Aggiungere, modificare o rimuovere le informazioni memorizzate all'interno di un file PDF.  
- **Quale libreria aiuta a fare questo in Java?** GroupDocs.Metadata.  
- **Posso anche rilevare la versione PDF?** Sì, la stessa API fornisce la rilevazione della versione.  
- **Ho bisogno di una licenza?** Una prova gratuita è sufficiente per la valutazione; è necessaria una licenza a pagamento per la produzione.  
- **Quale versione di Java è richiesta?** JDK 8 o superiore.

## Cos'è l'aggiornamento dei metadati PDF?

Aggiornare i metadati PDF significa leggere e scrivere programmaticamente le informazioni descrittive incorporate in un file PDF — come autore, titolo, soggetto e proprietà personalizzate. Metadati corretti migliorano la ricercabilità, la conformità e il controllo delle versioni nei sistemi di gestione dei documenti. Metadati accurati consentono inoltre l'indicizzazione automatizzata, la generazione di report di conformità e il tracciamento delle versioni nei sistemi di gestione dei documenti.

## Perché rilevare la versione PDF in Java?

Rilevare la versione PDF ti consente di verificare che un file venga visualizzato correttamente nel visualizzatore di destinazione e che soddisfi i requisiti di elaborazione a valle. Sapere se un PDF è versione 1.4, 1.7 o più recente ti aiuta a imporre regole di compatibilità prima di archiviare, pubblicare o convertire il documento.

## Prerequisiti

- **Java Development Kit (JDK)** 8 o superiore.  
- **Maven** per la gestione delle dipendenze (oppure puoi scaricare direttamente il JAR).  
- Familiarità di base con Java file I/O.  

## Configurazione di GroupDocs.Metadata per Java

### Configurazione Maven
Aggiungi il repository e la dipendenza al tuo `pom.xml`:

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

### Download diretto
In alternativa, scarica l'ultimo JAR dalla pagina di rilascio ufficiale: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Passaggi per l'acquisizione della licenza
- **Prova gratuita** – inizia a sperimentare senza costi.  
- **Licenza temporanea** – estendi la prova se necessario.  
- **Acquisto** – ottieni una licenza completa per l'uso in produzione.  

## Inizializzazione e configurazione di base

La classe `Metadata` è il punto di ingresso per lavorare con i file PDF in GroupDocs.Metadata. Rappresenta un contenitore che ti fornisce accesso in lettura/scrittura alle proprietà del documento, alle informazioni sulla versione e ai dati XMP personalizzati.

Crea un'istanza `Metadata` che punti al tuo file PDF:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

Ora sei pronto per leggere le proprietà, rilevare la versione e aggiornare i metadati.

## Come rilevare la versione PDF java

Carica il tuo PDF con `new Metadata("sample.pdf")` e chiama `getRootPackage().getVersion()` — il metodo restituisce la versione PDF esatta (ad es., 1.4, 1.7) in una singola chiamata. Questa risposta diretta ti consente di convalidare rapidamente la compatibilità prima di qualsiasi ulteriore elaborazione. La stringa della versione riflette il livello di specifica PDF a cui il file aderisce, fondamentale per i controlli di compatibilità.  
`getVersion()` restituisce la versione PDF come stringa, ad es., "1.4" o "1.7".

### Guida passo‑passo

1. **Apri il PDF** – istanzia l'oggetto `Metadata` (vedi l'inizializzazione sopra).  
2. **Accedi al pacchetto radice specifico del PDF** – chiama `metadata.getRootPackage()`.  
3. **Recupera la versione** – invoca `pdfRoot.getVersion()`; la stringa restituita contiene il numero di versione.  

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Suggerimento:** Usa il valore `version` per imporre controlli di compatibilità prima di elaborare un batch di PDF.

#### Risoluzione dei problemi
- Verifica il percorso del file; un percorso errato genera `FileNotFoundException`.  
- Assicurati che la versione di GroupDocs.Metadata corrisponda al tuo JDK (l'esempio utilizza 24.12).

## Come leggere le proprietà PDF in Java

`DocumentInfo` fornisce l'accesso ai campi standard dei metadati PDF senza caricare l'intero documento. La classe `DocumentInfo` consente l'accesso alle proprietà PDF standard come autore, titolo e data di creazione. È un wrapper leggero che legge i metadati senza caricare l'intero documento in memoria.

Crea un'istanza `DocumentInfo` dall'oggetto `Metadata` aperto:

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

Puoi quindi chiamare i getter come `getAuthor()`, `getTitle()` e `getCreationDate()` per recuperare i valori.

## Come aggiornare i metadati PDF in Java

Carica il PDF (come sopra), ottieni il pacchetto `DocumentInfo`, modifica i campi desiderati e salva le modifiche. L'operazione sovrascrive il blocco dei metadati esistente preservando il resto del documento. Dopo aver modificato i campi, chiamare `save()` scrive le modifiche nel file mantenendo intatti i flussi di contenuto.

La classe `DocumentInfo` è l'oggetto di GroupDocs.Metadata per modificare le proprietà a livello PDF come autore, titolo, soggetto e campi XMP personalizzati.

Aggiorna i campi dei metadati:

```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Nota:** Le chiamate ai setter seguono lo stesso schema dei getter mostrati in precedenza, rendendo l'API intuitiva e coerente.

#### Trappole comuni
- Tentare di modificare i metadati su un PDF che non contiene la proprietà target restituisce `null` — controlla sempre `null` prima di impostare un nuovo valore.  
- I PDF di grandi dimensioni possono richiedere un aumento dell'heap JVM; monitora l'uso della memoria durante gli aggiornamenti batch.

## Casi d'uso pratici

1. **Audit di conformità** – Verifica che tutti i PDF soddisfino una versione minima (ad es., 1.7) prima della presentazione legale.  
2. **Archiviazione automatica** – Etichetta i PDF con autore, dipartimento e data di creazione per una più facile reperibilità.  
3. **Integrazione con la gestione documentale** – Arricchisci i PDF con proprietà personalizzate che le piattaforme DMS possono indicizzare.  
4. **Generazione di report** – Inserisci le informazioni di versione nei report generati automaticamente.  
5. **Test cross‑platform** – Rileva discrepanze di versione che potrebbero causare problemi di rendering su visualizzatori più vecchi.  

## Suggerimenti sulle prestazioni

- **Usa try‑with‑resources** (come mostrato) per chiudere automaticamente gli oggetti `Metadata`.  
- **Elabora in batch** più file in un ciclo per ridurre l'overhead.  
- **Monitora l'heap** per PDF molto grandi; considera di elaborarli a blocchi se raggiungi i limiti di memoria.  
- **GroupDocs.Metadata supporta più di 50 formati di input e output** e può leggere i metadati da PDF di centinaia di pagine senza caricare l'intero file in memoria, offrendo prestazioni rapide su hardware server standard.  

## Domande frequenti

**Q: Posso aggiornare i metadati su PDF protetti da password?**  
A: Sì, ma devi fornire la password quando crei l'oggetto `Metadata`.

**Q: GroupDocs.Metadata supporta proprietà XMP personalizzate?**  
A: Assolutamente. Puoi leggere e scrivere campi XMP personalizzati tramite la stessa API.

**Q: È possibile modificare la versione PDF stessa?**  
A: La libreria può segnalare la versione; modificarla richiede di salvare il documento con un profilo di versione diverso, supportato tramite opzioni di salvataggio aggiuntive.

**Q: Cosa succede se il PDF non ha metadati esistenti?**  
A: I getter restituiranno `null`. Puoi chiamare in sicurezza i setter per creare nuove voci di metadati.

**Q: Ci sono restrizioni di licenza per l'uso commerciale?**  
A: È necessaria una licenza commerciale per le distribuzioni in produzione; la versione di prova è limitata a scopi di valutazione.

---

**Ultimo aggiornamento:** 2026-08-05  
**Testato con:** GroupDocs.Metadata 24.12 for Java  
**Autore:** GroupDocs

## Tutorial correlati

- [Aggiornare efficientemente i metadati PDF con GroupDocs.Metadata in Java per la gestione dei documenti](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Gestione avanzata dei metadati: rilevare le proprietà del documento e lo stato di crittografia con GroupDocs.Metadata per Java](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)
- [Creare anteprima documento Java – Tutorial GroupDocs.Metadata](/metadata/java/document-formats/)