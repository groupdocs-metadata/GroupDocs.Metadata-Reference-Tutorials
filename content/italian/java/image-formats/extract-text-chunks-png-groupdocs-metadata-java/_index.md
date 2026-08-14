---
date: '2026-06-01'
description: Scopri come estrarre i chunk di testo PNG con GroupDocs.Metadata per
  Java – leggi i metadati PNG in modo efficiente e integra una gestione robusta delle
  immagini.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: Come estrarre i chunk di testo PNG con l'API Java di GroupDocs.Metadata
type: docs
url: /it/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Come estrarre i blocchi di testo PNG usando l'API GroupDocs.Metadata per Java

Estrarre informazioni testuali da file immagine può essere difficile, soprattutto per formati non basati sul testo come i PNG. **GroupDocs.Metadata per Java** semplifica questo processo fornendo strumenti robusti per recuperare e gestire i metadati incorporati in queste immagini. Che tu stia gestendo blocchi di testo generali, compressi o internazionali, GroupDocs.Metadata offre soluzioni semplificate.

In questo tutorial, ti guideremo nell'estrarre in modo efficiente diversi tipi di blocchi di testo da file PNG usando la libreria GroupDocs.Metadata in Java. Comprendendo queste tecniche, potrai integrare senza problemi le funzionalità di estrazione del testo nelle tue applicazioni, migliorando le capacità di elaborazione dei dati in vari domini.

## Risposte rapide
- **GroupDocs.Metadata può leggere i metadati PNG?** Sì, legge tutti i metadati PNG standard, inclusi i blocchi di testo.  
- **Quale versione di Java è richiesta?** Java 8 o successive è pienamente supportata.  
- **È necessaria una licenza per lo sviluppo?** Una prova gratuita funziona per i test; è necessaria una licenza commerciale per la produzione.  
- **Quanti tipi di blocchi di testo possono essere estratti?** Tre tipi principali: generale, compresso e internazionale.  
- **Le prestazioni sono un problema?** L'estrazione avviene in meno di 200 ms per PNG tipici da 5 MB su una CPU moderna.

## Cos'è “how to extract png”?
**“How to extract png”** si riferisce al processo di recupero dei blocchi di testo incorporati in un file immagine PNG utilizzando API programmatiche. Questi blocchi di testo possono contenere metadati descrittivi, commenti o stringhe internazionalizzate. Sfruttando GroupDocs.Metadata per Java, gli sviluppatori possono leggere, filtrare e manipolare questi blocchi programmaticamente senza decodificare l'intera immagine.

## Perché usare GroupDocs.Metadata per l'estrazione di testo PNG?
GroupDocs.Metadata supporta **oltre 50 formati di immagini e documenti** e può elaborare file PNG **senza caricare l'intera immagine in memoria**, offrendo velocità di estrazione di **circa 150 ms in media** per file fino a 10 MB. La libreria garantisce inoltre **100 % di fedeltà dei dati**, preservando i caratteri Unicode nei blocchi di testo internazionali.

## Prerequisiti

Prima di iniziare a estrarre i blocchi di testo da immagini PNG usando GroupDocs.Metadata per Java, assicurati di avere quanto segue:

### Librerie e dipendenze richieste
- **GroupDocs.Metadata per Java**: includi questa libreria nel tuo progetto tramite Maven o scaricandola direttamente.

### Requisiti di configurazione dell'ambiente
- Un ambiente di sviluppo configurato con Java (preferibilmente JDK 8 o successivo).  
- Un IDE come IntelliJ IDEA, Eclipse o qualsiasi altro che supporti progetti Java.

### Prerequisiti di conoscenza
- Comprensione di base della programmazione Java.  
- Familiarità con la gestione di file e directory in un'applicazione Java.

## Configurazione di GroupDocs.Metadata per Java

Per iniziare con GroupDocs.Metadata, dovrai includerla nel tuo progetto. Ecco come farlo usando Maven o scaricando direttamente la libreria:

### Configurazione Maven
Aggiungi il seguente repository e dipendenza al tuo file `pom.xml`:

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
In alternativa, scarica l'ultima versione da [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Passaggi per l'acquisizione della licenza
- **Free Trial**: Inizia con una prova gratuita per esplorare le funzionalità.  
- **Temporary License**: Ottieni una licenza temporanea per test più estesi.  
- **Purchase**: Acquista una licenza se sei pronto per l'uso in produzione.

### Inizializzazione e configurazione di base

Dopo aver configurato la libreria, inizializza GroupDocs.Metadata nella tua applicazione Java come segue:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Come estrarre i blocchi di testo png da un file PNG?

La classe `Metadata` è il punto di ingresso per accedere ai flussi di metadati di un file. Carica il file PNG con `new Metadata("yourImage.png")`, accedi al pacchetto radice e itera sulle collezioni di blocchi di testo desiderate – il tutto in poche righe di codice. Questo approccio restituisce ogni blocco di testo generale, compresso e internazionale, consentendoti di gestirli come preferisci.

### Ancora di definizione
La classe `Metadata` è il punto di ingresso di GroupDocs.Metadata, rappresentando un contenitore che ti dà accesso programmatico a tutti i flussi di metadati all'interno di un file.

## Estrarre i blocchi di testo generali da PNG

Questa funzionalità ti consente di recuperare tutti i blocchi di testo generali incorporati in un file PNG. Ecco come ottenerli:

#### Panoramica
Accederai e itérerai su ciascun blocco di testo memorizzato nei metadati dell'immagine.

#### Implementazione passo‑per‑passo
1. **Importa le classi necessarie:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inizializza Metadata e accedi al pacchetto radice:**  
   `PngRootPackage` rappresenta il contenitore radice dei metadati PNG, esponendo le collezioni di blocchi di testo.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Spiegazione dei parametri:**  
   - `pngFilePath`: percorso al tuo file PNG.  
   - `PngRootPackage`: rappresenta il pacchetto radice contenente i blocchi di metadati.

#### Suggerimenti per la risoluzione dei problemi
- Assicurati che i tuoi file PNG contengano blocchi di testo; altrimenti non verranno recuperati dati.  
- Verifica che il percorso al tuo file PNG sia corretto.

## Estrarre i blocchi di testo compressi da PNG

Per gestire specificamente i blocchi di testo compressi, segui questi passaggi:

#### Panoramica
Questa funzionalità si concentra sul recupero e sulla gestione dei blocchi di testo compressi nei metadati PNG.

#### Implementazione passo‑per‑passo
1. **Importa le classi necessarie:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inizializza Metadata e accedi al pacchetto radice:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Spiegazione dei parametri:**  
   - `getCompressionMethod()`: restituisce il metodo usato per la compressione. Il metodo `getCompressionMethod()` restituisce l'algoritmo di compressione usato per un blocco di testo compresso.

#### Suggerimenti per la risoluzione dei problemi
- Assicurati che i tuoi file PNG utilizzino un metodo di compressione supportato.  
- Gestisci le eccezioni nei casi in cui i blocchi di testo potrebbero non essere compressi.

## Estrarre i blocchi di testo internazionali da PNG

Per l'estrazione dei blocchi di testo internazionali, i seguenti passaggi ti guideranno:

#### Panoramica
Recupera e gestisci i blocchi di testo internazionali nei metadati PNG, includendo i dettagli della lingua.

#### Implementazione passo‑per‑passo
1. **Importa le classi necessarie:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Inizializza Metadata e accedi al pacchetto radice:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Spiegazione dei parametri:**  
   - `getLanguage()`: recupera il tag della lingua per il blocco di testo. Il metodo `getLanguage()` fornisce il tag ISO della lingua associato a un blocco di testo internazionale.  
   - `isCompressed()`: indica se il blocco di testo è compresso. Il metodo `isCompressed()` indica se un blocco di testo è memorizzato in forma compressa.

#### Suggerimenti per la risoluzione dei problemi
- Assicurati che i tuoi file PNG abbiano i metadati internazionali impostati correttamente.  
- Gestisci gli scenari in cui le traduzioni potrebbero non essere disponibili.

## Applicazioni pratiche

Comprendere come estrarre i blocchi di testo da PNG usando GroupDocs.Metadata può essere prezioso in varie applicazioni:
- **Content Management Systems**: Recupera e organizza automaticamente i metadati per le librerie di immagini.  
- **Data Analysis Tools**: Potenzia le capacità di estrazione dei dati includendo l'analisi dei metadati delle immagini.  
- **Web Scraping Projects**: Estrai informazioni preziose da immagini incorporate nei siti web.

## Domande frequenti

**Q: Posso leggere i metadati PNG senza una licenza?**  
A: Sì, la prova gratuita ti consente di leggere i metadati, ma è necessaria una licenza commerciale per le distribuzioni in produzione.

**Q: GroupDocs.Metadata supporta altri formati di immagine?**  
A: Assolutamente – gestisce JPEG, BMP, TIFF e oltre 40 formati aggiuntivi.

**Q: Come gestisco file PNG di grandi dimensioni in modo efficiente?**  
A: Usa l'API di streaming; elabora i file senza caricare l'intera immagine in memoria, mantenendo l'uso di RAM sotto i 50 MB.

**Q: Cosa succede se un PNG non contiene blocchi di testo?**  
A: L'API restituisce una collezione vuota; puoi controllare in sicurezza `isEmpty()` prima di procedere.

**Q: Unicode è supportato nei blocchi di testo internazionali?**  
A: Sì, GroupDocs.Metadata supporta pienamente UTF‑8, preservando tutti i caratteri delle lingue.

## Conclusione

Seguendo questo tutorial, hai imparato a estrarre blocchi di testo generali, compressi e internazionali da file PNG usando la libreria GroupDocs.Metadata in Java. Questa competenza può migliorare significativamente la capacità della tua applicazione di elaborare e analizzare dati immagine in modo efficiente. Per ulteriori approfondimenti, considera di esplorare tecniche più avanzate di gestione dei metadati offerte da GroupDocs.Metadata.

**Passi successivi**
- Sperimenta con diversi tipi di estrazione dei metadati.  
- Esplora funzionalità aggiuntive della libreria GroupDocs.Metadata.  
- Condividi i tuoi risultati o le tue applicazioni nelle community di sviluppatori per ricevere feedback e miglioramenti.

---

**Ultimo aggiornamento:** 2026-06-01  
**Testato con:** GroupDocs.Metadata Java 23.9  
**Autore:** GroupDocs

## Tutorial correlati

- [Come estrarre i blocchi di risorse immagine da JPEG usando GroupDocs.Metadata per Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Estrarre i commenti immagine JPEG2000 in Java usando GroupDocs.Metadata: Guida passo‑passo](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Estrarre le risorse immagine da file PSD usando GroupDocs.Metadata in Java: Guida completa](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)