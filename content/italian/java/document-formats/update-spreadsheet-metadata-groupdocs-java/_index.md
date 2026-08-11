---
date: '2026-03-22'
description: Scopri come modificare la data di creazione di Excel e aggiornare i metadati
  di Excel utilizzando GroupDocs.Metadata per Java. Segui questa guida passo passo
  per aggiungere parole chiave a Excel e modificare le proprietà del documento.
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: Modifica la data di creazione di Excel usando GroupDocs.Metadata in Java
type: docs
url: /it/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# Cambia la data di creazione di Excel usando GroupDocs.Metadata in Java

In ambienti moderni guidati dai dati, **modificare la data di creazione di Excel** e mantenere aggiornati gli altri metadati può migliorare drasticamente l'organizzazione dei documenti, la ricercabilità e la conformità. Che tu stia gestendo report finanziari, tracker di progetto o dati d'archivio, metadati accurati garantiscono che le persone giuste trovino i file giusti al momento giusto. Questo tutorial ti guida nell'uso della libreria GroupDocs.Metadata per **cambiare la data di creazione di Excel**, **aggiungere parole chiave a Excel** e **modificare le proprietà del documento Excel** in un'applicazione Java.

## Risposte rapide
- **Posso cambiare la data di creazione di un file Excel?** Sì, usando `setCreatedTime` di GroupDocs.Metadata.  
- **Quale libreria supporta l'aggiornamento dei metadati di Excel in Java?** GroupDocs.Metadata per Java.  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per la valutazione; è richiesta una licenza permanente per la produzione.  
- **Quale versione di Java è richiesta?** JDK 8 o superiore.  
- **Posso aggiungere parole chiave personalizzate a una cartella di lavoro Excel?** Assolutamente sì—usa `setKeywords` sulle proprietà del documento.

## Cos'è “cambiare la data di creazione di Excel”?
Cambiare la data di creazione di Excel significa aggiornare la proprietà *Created* integrata memorizzata all'interno del file della cartella di lavoro. Questa proprietà fa parte dei metadati standard Office Open XML e può essere modificata programmaticamente senza alterare il contenuto reale dei fogli di lavoro.

## Perché usare GroupDocs.Metadata per i metadati di Excel?
GroupDocs.Metadata offre un'API di alto livello, type‑safe, che astrae la gestione XML a basso livello richiesta dal formato Office Open XML. Ti consente di:

- **Aggiornare le proprietà principali** come autore, azienda e data di creazione con una singola chiamata.  
- **Aggiungere parole chiave a Excel** per migliorare i risultati di ricerca in SharePoint, OneDrive o nei file system locali.  
- **Modificare le proprietà del documento Excel** senza aprire la cartella di lavoro in Excel, risparmiando tempo e risorse.  

## Prerequisiti
- Java Development Kit (JDK) 8 o più recente.  
- Un IDE come IntelliJ IDEA o Eclipse.  
- Familiarità di base con Java I/O.  

## Configurare GroupDocs.Metadata per Java

### Installazione

Aggiungi il repository Maven di GroupDocs.Metadata e la dipendenza al tuo `pom.xml`:

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

In alternativa, puoi [scaricare l'ultima versione direttamente](https://releases.groupdocs.com/metadata/java/) se preferisci una configurazione manuale.

### Acquisizione della licenza

GroupDocs offre una prova gratuita per la valutazione. Per l'uso in produzione, ottieni una licenza temporanea o permanente dal fornitore. Visita la [pagina di acquisto di GroupDocs](https://purchase.groupdocs.com/temporary-license/) per i dettagli.

#### Inizializzazione di base

Importa le classi necessarie nel tuo file sorgente Java:

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Implementazione passo‑passo

### Passo 1: Apri la cartella di lavoro Excel

Fornisci il percorso al file di origine e crea un'istanza `Metadata`. Il blocco `try‑with‑resources` garantisce che la gestione del file venga chiusa automaticamente.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Passo 2: Aggiorna le proprietà dei metadati integrati

Ora puoi **cambiare la data di creazione di Excel**, impostare autore, azienda, categoria e **aggiungere parole chiave a Excel**. La chiamata `new Date()` cattura il timestamp corrente, ma puoi fornire qualsiasi `java.util.Date` necessario.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **Suggerimento professionale:** Usa una convenzione di denominazione coerente per le parole chiave (ad es., `project:Q2, finance, confidential`) per rendere le ricerche future più efficaci.

### Passo 3: Salva la cartella di lavoro aggiornata

Specifica un percorso di output e persisti le modifiche. Il file originale rimane intatto, il che è utile per le tracce di audit.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Problemi comuni e soluzioni

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Errori di percorso file** | Percorsi relativi/assoluti errati | Controlla attentamente `inputFilePath` e `outputFilePath`. Usa `Paths.get(...)` per percorsi indipendenti dalla piattaforma. |
| **Versione della libreria incompatibile** | Stai usando una versione più vecchia di GroupDocs.Metadata che non supporta il metodo `setCreatedTime` | Aggiorna all'ultima versione (come mostrato nello snippet Maven). |
| **Licenza mancante** | Periodo di prova scaduto | Applica una licenza temporanea o acquista una licenza completa tramite la pagina di acquisto. |
| **Elevato consumo di memoria per cartelle di lavoro grandi** | Il caricamento di file Excel massivi consuma heap | Elabora i file in batch e aumenta l'heap JVM (`-Xmx`) se necessario. |

## Domande frequenti

**D: Quali versioni di Java sono supportate da GroupDocs.Metadata?**  
R: Java 8 e versioni successive sono pienamente supportate.

**D: Come devo gestire le eccezioni durante l'aggiornamento dei metadati?**  
R: Avvolgi il codice in un blocco `try‑catch` e registra `MetadataException` per catturare eventuali errori I/O o di formato.

**D: Posso aggiornare più file Excel in un'unica esecuzione?**  
R: Sì, itera su una collezione di percorsi file, ma monitora l'uso di memoria per batch di grandi dimensioni.

**D: È possibile ripristinare le modifiche apportate ai metadati?**  
R: Conserva un backup della cartella di lavoro originale prima di applicare gli aggiornamenti, quindi ripristinala se necessario.

**D: Dove posso trovare una documentazione più dettagliata?**  
R: Consulta la guida ufficiale su [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## Applicazioni pratiche

1. **Audit finanziari** – Registra chi ha modificato una cartella di lavoro e quando, fornendo una traccia di audit.  
2. **Gestione progetti** – Tagga i fogli di calcolo con parole chiave specifiche del progetto per un recupero rapido.  
3. **Archiviazione dati** – Conserva le date di creazione originali e le informazioni aziendali per la conformità.

## Consigli sulle prestazioni

- Limita le operazioni sui metadati per esecuzione per evitare un consumo eccessivo di memoria.  
- Chiudi prontamente l'oggetto `Metadata` (il pattern `try‑with‑resources` lo fa automaticamente).  
- Per cartelle di lavoro molto grandi, considera l'elaborazione in un thread di background per mantenere reattiva l'interfaccia utente.

## Conclusione

Ora sai come **cambiare la data di creazione di Excel**, **aggiungere parole chiave a Excel** e **modificare le proprietà del documento Excel** usando GroupDocs.Metadata in Java. Questa capacità ti permette di mantenere i tuoi fogli di calcolo ben organizzati, ricercabili e conformi alle politiche interne di governance. Come passo successivo, esplora altre funzionalità dei metadati come proprietà personalizzate o elaborazione batch per ottimizzare ulteriormente il tuo flusso di lavoro di gestione dei documenti.

---

**Ultimo aggiornamento:** 2026-03-22  
**Testato con:** GroupDocs.Metadata 24.12 per Java  
**Autore:** GroupDocs  

**Risorse**
- [Documentazione](https://docs.groupdocs.com/metadata/java/)
- [Riferimento API](https://reference.groupdocs.com/metadata/java/)
- [Scarica GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [Repository GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Forum di supporto gratuito](https://forum.groupdocs.com/c/metadata/)
- [Licenza temporanea](https://purchase.groupdocs.com/temporary-license/)