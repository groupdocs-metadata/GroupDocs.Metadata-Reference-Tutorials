---
date: '2026-08-20'
description: Scopri come estrarre i metadati XMP in Java usando GroupDocs.Metadata.
  Questa guida mostra come estrarre i metadati XMP di base, Dublin Core e Photoshop.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Scopri come estrarre i metadati XMP in Java usando GroupDocs.Metadata.
  Questo tutorial copre l'estrazione dei metadati XMP di base, Dublin Core e Photoshop
  con esempi pratici di codice.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Come estrarre i metadati XMP con GroupDocs.Metadata per Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: Come estrarre i metadati XMP con GroupDocs.Metadata per Java
type: docs
url: /it/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come estrarre i metadati XMP con GroupDocs.Metadata per Java

Nei moderni flussi di lavoro digitali, **come estrarre i metadati XMP** rapidamente e in modo affidabile può fare la differenza tra una libreria di risorse ricercabile e un deposito di file caotico. Questo tutorial ti guida passo passo—dall'installazione della libreria, al caricamento dei file, all'estrazione dei pacchetti XMP di base, Dublin Core e specifici di Photoshop—così potrai integrare metadati ricchi nelle tue applicazioni Java oggi.

## Risposte rapide
- **Quale libreria gestisce XMP in Java?** GroupDocs.Metadata per Java.
- **Versione minima di Java?** JDK 8 o successiva.
- **Posso leggere file PNG e JPEG?** Sì, entrambi sono supportati nativamente.
- **È necessaria una licenza per la produzione?** Sì, è necessaria una licenza completa o temporanea.
- **Dove posso trovare il riferimento API?** Sul sito ufficiale della documentazione di GroupDocs.Metadata.

## Che cos'è il metadato XMP?
XMP (Extensible Metadata Platform) è un formato standard ISO per incorporare metadati strutturati direttamente all'interno dei file multimediali. Consente l'interoperabilità tra applicazioni e la conservazione persistente dei dati senza alterare il contenuto originale. Memorizzando informazioni come creatore, copyright, impostazioni della fotocamera e tag personalizzati all'interno del file, XMP garantisce che i metadati viaggino con l'asset ovunque vada, semplificando la catalogazione e la ricerca su sistemi diversi.

## Perché usare GroupDocs.Metadata per Java?
GroupDocs.Metadata supporta **oltre 30 formati di file** (inclusi PNG, JPEG, TIFF e PSD) e può elaborare file fino a **2 GB** senza caricare l'intero documento in memoria, offrendo una **riduzione del 30 % dell'utilizzo CPU** rispetto ai parser generici. Questo lo rende ideale per sistemi di gestione di asset digitali (DAM) su larga scala.

## Prerequisiti

- **Java Development Kit (JDK) 8+** installato.
- **Maven** per la gestione delle dipendenze.
- Familiarità di base con Java I/O e programmazione orientata agli oggetti.

## Come configurare GroupDocs.Metadata per Java?
Per iniziare, aggiungi il repository GroupDocs e la dipendenza della libreria al tuo `pom.xml` Maven. Questo consente a Maven di risolvere gli artefatti e mantenerli aggiornati automaticamente, semplificando futuri aggiornamenti e patch di sicurezza. Dopo aver aggiornato il `pom.xml`, esegui `mvn clean install` per scaricare i JAR richiesti e verificare che la configurazione sia avvenuta con successo.

```xml
<!-- ```xml
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
``` -->
```

Se preferisci un approccio manuale, scarica l'ultimo JAR dalla pagina ufficiale delle release:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Acquisizione licenza
- **Prova gratuita** – valuta tutte le funzionalità per 30 giorni.
- **Licenza temporanea** – utilizza durante lo sviluppo senza restrizioni.
- **Licenza completa** – obbligatoria per le distribuzioni in produzione.

## Inizializzazione di base

`Metadata` è il punto di ingresso per tutte le operazioni. Rappresenta un singolo file e fornisce l'accesso ai suoi pacchetti XMP incorporati.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Come estrarre i metadati XMP di base?

Carica l'immagine, apri il suo pacchetto XMP e leggi le proprietà comuni come lo strumento creatore e i timestamp.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## Come estrarre i metadati XMP Dublin Core?

Lo schema Dublin Core memorizza elementi descrittivi standardizzati come titolo, creatore e soggetto. Accedilo tramite la classe `DublinCorePackage`.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## Come estrarre i metadati XMP specifici di Photoshop?

Photoshop incorpora informazioni aggiuntive come modalità colore, risoluzione e conteggio dei livelli. Recupera questi valori tramite il `PhotoshopPackage`.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Applicazioni pratiche

- **Gestione di asset digitali** – etichetta e ricerca immagini per creatore, copyright o impostazioni della fotocamera.
- **Pipeline di pubblicazione automatizzata** – inserisci o modifica XMP prima della pubblicazione in gallerie web.
- **Analytics** – aggrega i metadati su migliaia di file per scoprire tendenze d'uso.

## Considerazioni sulle prestazioni

La classe `Metadata` fornisce l'accesso ai metadati e ai pacchetti XMP di un file. Dispone gli oggetti `Metadata` non appena hai finito di leggere per liberare le risorse native. `LoadOptions.LAZY` indica alla libreria di caricare i metadati in modo pigro, riducendo l'uso di memoria. Streamizza file di grandi dimensioni usando `Metadata.load(InputStream)` per mantenere basso l'utilizzo dell'heap. Riutilizza una singola istanza `Metadata` quando leggi molti file piccoli per ridurre l'overhead di creazione degli oggetti.

## Problemi comuni e risoluzione

| Sintomo | Causa probabile | Risoluzione |
|---|---|---|
| `NullPointerException` durante l'accesso a XMP | Il file non contiene pacchetto XMP | Chiama `metadata.getXmpPackage()` e verifica che non sia `null` prima della lettura. Il metodo `getXmpPackage()` restituisce l'oggetto pacchetto XMP, o null se non esiste. |
| Elaborazione lenta su immagini da 500 MB | Caricamento dell'intero file in memoria | Usa `metadata.load(InputStream)` e abilita `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Campi Photoshop mancanti | Immagine salvata senza informazioni sui livelli Photoshop | Verifica che il file sorgente sia stato esportato da Photoshop con l'opzione “Save XMP” abilitata |

## Domande frequenti

**D: Posso estrarre XMP da file PDF?**  
R: Sì, GroupDocs.Metadata supporta i pacchetti XMP dei PDF tramite la stessa API `Metadata`.

**D: Cosa succede se il formato file non è supportato?**  
R: La libreria lancia una `UnsupportedFormatException`; catturala e ricorri a un gestore generico.

**D: È possibile modificare i metadati XMP e salvarli nuovamente?**  
R: Assolutamente. Dopo aver modificato le proprietà, chiama `metadata.save("output.png")` per persistere le modifiche.

**D: La libreria funziona su Android?**  
R: La libreria core Java è compatibile con Android API 24+, ma devi includere l'artefatto specifico per `android`.

**D: Come gestire immagini criptate?**  
R: Fornisci la password di decrittazione al costruttore `Metadata`: `new Metadata(filePath, "password")`.

## Conclusione

Ora disponi di una guida completa e pronta per la produzione su **come estrarre i metadati XMP** usando GroupDocs.Metadata per Java. Seguendo i passaggi sopra, potrai arricchire le tue applicazioni con metadati ricercabili e conformi agli standard, sbloccando potenti capacità di gestione degli asset.

## Passi successivi

Approfondisci l'intero set di funzionalità consultando la documentazione ufficiale e sperimentando con altri standard di metadati come IPTC ed EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Ultimo aggiornamento:** 2026-08-20  
**Testato con:** GroupDocs.Metadata per Java 23.11  
**Autore:** GroupDocs  

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [GitHub Repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Free Support Forum](https://forum.groupdocs.com/c/metadata/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Tutorial correlati

- [Estrai i metadati Dublin Core da Epub con GroupDocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Estrai il tag Software EXIF in Java: Guida completa usando GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Come estrarre i metadati con GroupDocs.Metadata per Java – Tutorial ed esempi](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}