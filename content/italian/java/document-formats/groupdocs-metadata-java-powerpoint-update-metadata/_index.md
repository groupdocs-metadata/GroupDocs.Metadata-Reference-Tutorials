---
date: '2026-05-27'
description: Scopri come impostare il CreatedTime di un pptx in Java usando la dipendenza
  GroupDocs Maven per aggiornare i metadati di PowerPoint, incluso come modificare
  la data di creazione del PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Imposta il CreatedTime di PPTX in Java con la dipendenza GroupDocs Maven
type: docs
url: /it/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Imposta CreatedTime PPTX in Java con GroupDocs.Metadata

I metadati accurati sono essenziali per la conformità e la reperibilità nei moderni flussi di lavoro dei documenti. Con **GroupDocs.Metadata** è possibile **impostare il CreatedTime del PPTX in Java**, consentendo di **cambiare la data di creazione del PPTX** insieme ad altre proprietà integrate come autore o azienda. Questo tutorial ti guida attraverso la configurazione di Maven, l’inizializzazione dell’API, l’aggiornamento dei metadati e il salvataggio della presentazione modificata—tutto con codice chiaro e pronto per la produzione.

## Risposte Rapide
- **Quale libreria aggiorna i metadati di PowerPoint in Java?** GroupDocs.Metadata tramite la dipendenza Maven di GroupDocs.  
- **Posso impostare la proprietà CreatedTime del PPTX?** Sì—usa `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **È necessaria una licenza per la produzione?** Una versione di prova è sufficiente per la valutazione; una licenza commerciale è obbligatoria per le distribuzioni in produzione.  
- **Quale strumento di build utilizza l'esempio?** Maven (è anche possibile scaricare il JAR manualmente).  
- **L'API supporta Java 8 e versioni successive?** Assolutamente—GroupDocs.Metadata è destinato a Java 8+.

## Cos'è la dipendenza Maven di GroupDocs?
La **dipendenza Maven di GroupDocs** è una voce di repository compatibile con Maven che importa l'ultima libreria GroupDocs.Metadata nel tuo progetto Java. Semplifica la gestione delle dipendenze risolvendo automaticamente le librerie transitive, garantendo l'uso della versione più recente e sicura, ed eliminando la necessità di scaricare manualmente i JAR o tenere traccia delle versioni.

## Perché usare GroupDocs.Metadata per modificare la data di creazione del PPTX?
GroupDocs.Metadata consente aggiornamenti automatizzati e pronti per il batch dei timestamp di creazione dei PPTX, assicurando che ogni presentazione rispetti le politiche aziendali o i requisiti legali. Impostando programmaticamente la proprietà CreatedTime eviti modifiche manuali, riduci gli errori umani e puoi integrare la modifica nei pipeline CI/CD o negli script di migrazione per una gestione documentale senza interruzioni.

## Prerequisiti
- Java 8 o superiore installato.  
- Un IDE come IntelliJ IDEA o Eclipse.  
- Maven per la gestione delle dipendenze.  
- Accesso a una prova di GroupDocs o a una licenza acquistata.

## Come impostare il CreatedTime del PPTX in Java?

La classe `Metadata` rappresenta un documento e fornisce l'accesso alle sue proprietà di metadati.

Carica il tuo file PowerPoint con `new Metadata("presentation.pptx")`, recupera il pacchetto radice, chiama `setCreatedTime` con il `java.util.Date` desiderato e infine invoca `save` per scrivere le modifiche. Questo flusso end‑to‑end modifica la data di creazione preservando tutti i contenuti delle diapositive e le altre proprietà.

### Configurazione Maven
Aggiungi il repository GroupDocs e la dipendenza metadata al tuo `pom.xml`:

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

> **Suggerimento:** Mantenere il numero di versione aggiornato garantisce di beneficiare delle ultime correzioni di bug e miglioramenti delle prestazioni.

### Download diretto (se preferisci non usare Maven)

In alternativa, scarica l'ultimo JAR da [Rilasci GroupDocs.Metadata per Java](https://releases.groupdocs.com/metadata/java/).

#### Acquisizione della licenza

Inizia con una prova gratuita o richiedi una licenza temporanea per valutare GroupDocs.Metadata. Per l'uso in produzione, acquista una licenza tramite il [sito ufficiale di GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Inizializzazione e Configurazione di Base

Una volta che la libreria è nel classpath, puoi creare un'istanza `Metadata` che punta al tuo file PowerPoint:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Questo codice apre la presentazione in un blocco try‑with‑resources, garantendo che la gestione del file venga rilasciata automaticamente.

## Guida passo‑passo per aggiornare i metadati integrati

### Passo 1: Carica il documento di presentazione

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Il caricamento del file stabilisce una connessione che ti consente di leggere o scrivere i metadati.

### Passo 2: Accedi al pacchetto radice della presentazione

L'oggetto `root` fornisce l'accesso al pacchetto principale della presentazione e alle sue proprietà integrate.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

L'oggetto `root` espone tutte le proprietà di documento integrate.

### Passo 3: Aggiorna le proprietà dei documenti integrati (inclusa la data di creazione)

`setCreatedTime` assegna un nuovo timestamp di creazione al documento.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Qui dimostriamo come **impostare il CreatedTime del PPTX** assegnando un nuovo oggetto `Date` a `CreatedTime`. Sostituisci `new Date()` con qualsiasi timestamp specifico di cui hai bisogno.

### Passo 4: Salva la presentazione aggiornata

`save` scrive i metadati modificati su un file.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

La chiamata `save` scrive i metadati modificati in un nuovo file PowerPoint, lasciando intatto l'originale.

## Suggerimenti per la risoluzione dei problemi
- **File non trovato:** Verifica il percorso di input e i permessi del file.  
- **Incompatibilità di versione:** Assicurati che la versione di `groupdocs-metadata` corrisponda al tuo runtime Java.  
- **Proprietà non aggiornata:** Controlla di aver chiamato `setCreatedTime` (o il setter pertinente) prima di invocare `save`.

## Applicazioni pratiche

1. **Branding aziendale:** Inserisci automaticamente il nome e la categoria dell'azienda in tutti i deck diapositive prima della distribuzione.  
2. **Sistemi di gestione documentale:** Arricchisci i file PPTX con metadati ricercabili per un recupero più rapido.  
3. **Risorse educative:** Mantieni aggiornate le informazioni su autore e curriculum nelle diapositive delle lezioni.  
4. **Tracciamento della collaborazione:** Registra i nomi dei contributori per mantenere la responsabilità.  
5. **Integrazione CMS:** Sincronizza le modifiche ai metadati con la tua piattaforma di gestione dei contenuti in tempo reale.

## Considerazioni sulle prestazioni
- **Elaborazione batch:** Cicla su un elenco di file e riutilizza una singola istanza `Metadata` quando possibile.  
- **Gestione della memoria:** Usa sempre try‑with‑resources (come mostrato) per liberare rapidamente le risorse native.  
- **Strutture dati efficienti:** Memorizza gli aggiornamenti dei metadati in una mappa prima di applicarli per ridurre le chiamate ripetitive.

## Domande frequenti

**Q: Qual è lo scopo principale della dipendenza Maven di GroupDocs?**  
A: Fornisce un modo conveniente per includere l'ultima libreria GroupDocs.Metadata nei progetti Java basati su Maven.

**Q: Come posso impostare la data di creazione del PPTX senza influire su altre proprietà?**  
A: Usa `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` prima di chiamare `metadata.save()`.

**Q: È necessaria una licenza per eseguire questo codice in sviluppo?**  
A: Una licenza di prova temporanea è sufficiente per sviluppo e test; è richiesta una licenza completa per la produzione.

**Q: Posso aggiornare anche i campi di metadati personalizzati?**  
A: Sì—GroupDocs.Metadata supporta sia le proprietà integrate sia quelle personalizzate tramite la sua API.

**Q: Esiste un modo per annullare le modifiche se commetto un errore?**  
A: Conserva una copia del file originale o leggi i valori delle proprietà esistenti prima di sovrascriverli, quindi ripristinali se necessario.

## Risorse

- [Documentazione](https://docs.groupdocs.com/metadata/java/)
- [Riferimento API](https://apireference.groupdocs.com/metadata/java/)

---

**Ultimo aggiornamento:** 2026-05-27  
**Testato con:** GroupDocs.Metadata 24.12 for Java  
**Autore:** GroupDocs  

---

## Tutorial correlati

- [Aggiorna metadati personalizzati in PowerPoint usando GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Come aggiornare i metadati di un documento Word usando GroupDocs.Metadata Java: Guida completa](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Aggiorna efficientemente i metadati PDF con GroupDocs.Metadata in Java per la gestione dei documenti](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)