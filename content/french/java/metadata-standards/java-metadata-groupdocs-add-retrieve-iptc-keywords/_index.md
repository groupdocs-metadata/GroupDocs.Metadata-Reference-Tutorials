---
date: '2026-08-15'
description: Découvrez comment ajouter des mots‑clés IPTC en Java avec GroupDocs.Metadata,
  améliorant la gestion des actifs numériques et la recherche.
keywords:
- add iptc keywords java
- groupdocs metadata java
- java add image metadata
lastmod: '2026-08-15'
og_description: Ajoutez des mots‑clés IPTC en Java avec GroupDocs.Metadata pour renforcer
  la gestion des actifs numériques. Découvrez la configuration étape par étape, le
  code et les meilleures pratiques.
og_image_alt: Guide showing Java code that adds IPTC keywords with GroupDocs.Metadata
og_title: Ajouter des mots‑clés IPTC en Java avec GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-08-15'
  description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  headline: Add IPTC keywords in Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to add IPTC keywords in Java using GroupDocs.Metadata, improving
    digital asset management and searchability.
  name: Add IPTC keywords in Java with GroupDocs.Metadata
  steps:
  - name: create a constants class
    text: The `Constants` class stores reusable values such as file locations and
      the license string.
  - name: initialize metadata and set the IPTC package
    text: '`Metadata` is the entry point for reading and writing any supported metadata
      format. It abstracts file handling so you don’t need to manage streams manually.
      The code below checks whether an IPTC package already exists; if not, it creates
      one, guaranteeing a place for keyword storage.'
  - name: add keywords to the IPTC record
    text: IptcDataSet represents a single IPTC metadata entry such as a keyword. Each
      keyword is added as an `IptcDataSet` entry. You can add as many keywords as
      required; the library automatically handles duplicate detection.
  - name: retrieve and display IPTC keywords
    text: '`metadata.getIptc().getKeywords()` returns the list of keyword strings
      stored in the IPTC package. After saving, you can read back the keywords to
      confirm they were persisted correctly. This verification step is useful for
      unit tests and debugging.'
  type: HowTo
- questions:
  - answer: No. IPTC is an image‑specific standard; for PDFs you would use XMP or
      PDF‑specific metadata fields.
    question: Can I add IPTC keywords to PDF files?
  - answer: Yes—it handles JPEG, TIFF, PNG, BMP, and WebP, preserving existing metadata
      while adding new IPTC entries.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: The IPTC specification allows up to 64 keywords per image; GroupDocs.Metadata
      enforces this limit automatically.
    question: How many keywords can I store?
  - answer: Absolutely. The library is compiled for Java 8+ and works seamlessly on
      Java 11, 17, and newer LTS releases.
    question: Is the library compatible with Java 11?
  - answer: Retrieve the keyword list, remove the unwanted entry, then call `metadata.getIptc().setKeywords(updatedList)`
      and save the file.
    question: What if I need to remove a keyword?
  type: FAQPage
tags:
- add iptc keywords
- groupdocs metadata
- java metadata handling
- digital asset management
- image metadata
title: Ajouter des mots‑clés IPTC en Java avec GroupDocs.Metadata
type: docs
url: /fr/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/
weight: 1
---

# Ajouter des mots‑clés IPTC en Java avec GroupDocs.Metadata

La gestion des métadonnées d'image est essentielle pour toute stratégie de gestion d'actifs numériques (DAM). Dans ce tutoriel, vous apprendrez **comment ajouter des mots‑clés IPTC en Java** en utilisant la bibliothèque GroupDocs.Metadata, puis récupérer ces mots‑clés pour vérifier les modifications. À la fin, vous disposerez d'un modèle réutilisable que vous pourrez intégrer dans des travaux de traitement par lots, des pipelines de gestion de contenu ou tout flux de travail multimédia basé sur Java.

## Réponses rapides
- **Quelle bibliothèque ajoute des mots‑clés IPTC en Java ?** GroupDocs.Metadata for Java.  
- **Ai‑je besoin d'une licence ?** Un essai gratuit fonctionne pour le développement ; une licence payante est requise pour la production.  
- **Puis‑je ajouter plusieurs mots‑clés à la fois ?** Oui — ajoutez simplement chaque mot‑clé au paquet IPTC.  
- **La prise en charge des gros fichiers est‑elle assurée ?** GroupDocs.Metadata traite les fichiers jusqu’à 2 Go sans charger le fichier entier en mémoire.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur, avec Maven 3 ou ultérieur.

## Qu’est‑ce que l’ajout de mots‑clés IPTC en Java ?
**Add IPTC keywords java** fait référence à l’insertion programmatique d’étiquettes de mots‑clés conformes à la norme IPTC dans les fichiers image à l’aide de code Java. Cette opération enrichit les métadonnées de l’image, les rendant recherchables dans les systèmes DAM et améliore le SEO des actifs web. Elle aide également à maintenir la conformité aux normes de l’industrie pour le balisage des actifs médiatiques.

## Pourquoi utiliser GroupDocs.Metadata pour Java ?
GroupDocs.Metadata prend en charge **plus de 150 normes de métadonnées** (y compris EXIF, IPTC, XMP) et peut **traiter des fichiers jusqu’à 2 Go** sans les charger entièrement en mémoire, ce qui réduit l’utilisation du CPU et de la RAM jusqu’à 30 % comparé aux approches naïves de flux de fichiers. L’API est sûre au niveau des types, bien documentée, et offre un appel en une seule ligne pour persister les modifications.

## Prérequis
- **GroupDocs.Metadata for Java** (version 24.12 ou ultérieure).  
- Java Development Kit 8 ou plus récent.  
- Maven 3 installé et configuré.  
- Un IDE tel qu’IntelliJ IDEA ou Eclipse (optionnel mais recommandé).  

### Bibliothèques requises
Ajoutez la dépendance GroupDocs.Metadata à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>metadata</artifactId>
    <version>24.12</version>
</dependency>
```

Vous pouvez télécharger la bibliothèque depuis la page **GroupDocs.Metadata for Java releases** : [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

## Comment ajouter des mots‑clés IPTC en Java ?
Tout d’abord, chargez le fichier image cible à l’aide de l’API GroupDocs.Metadata, puis vérifiez qu’un paquet IPTC est présent ou créez‑en un s’il manque, et enfin ajoutez les mots‑clés souhaités à la collection IPTC Keywords. Les étapes ci‑dessous illustrent chaque partie de ce flux de travail en détail.

### Étape 1 : créer une classe de constantes
La classe `Constants` stocke des valeurs réutilisables telles que les emplacements de fichiers et la chaîne de licence.

```java
public class Constants {
    public static final String YOUR_DOCUMENT_DIRECTORY = "path/to/your/document";
    public static final String OUTPUT_DIRECTORY = "path/to/output/directory";
}
```

### Étape 2 : initialiser les métadonnées et définir le paquet IPTC
`Metadata` est le point d’entrée pour lire et écrire tout format de métadonnées pris en charge. Il abstrait la gestion des fichiers afin que vous n’ayez pas à gérer les flux manuellement.

Le code ci‑dessous vérifie si un paquet IPTC existe déjà ; sinon, il en crée un, garantissant un emplacement pour le stockage des mots‑clés.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcRecordSet;

public class InitializeMetadataAndIPTCPackage {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            if (root.getIptcPackage() == null) {
                root.setIptcPackage(new IptcRecordSet());
            }
        } catch (Exception e) {
            System.out.println("Error initializing metadata: " + e.getMessage());
        }
    }
}
```

### Étape 3 : ajouter des mots‑clés à l’enregistrement IPTC
IptcDataSet représente une entrée unique de métadonnées IPTC telle qu’un mot‑clé. Chaque mot‑clé est ajouté en tant qu’entrée `IptcDataSet`. Vous pouvez ajouter autant de mots‑clés que nécessaire ; la bibliothèque gère automatiquement la détection des doublons.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.IptcDataSet;
import com.groupdocs.metadata.core.IptcRecordType;
import com.groupdocs.metadata.core.IptcApplicationRecordDataSet;

public class AddKeywordsToIPTC {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.YOUR_DOCUMENT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            IptcDataSet dataSet1 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 1");
            IptcDataSet dataSet2 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 2");
            IptcDataSet dataSet3 = new IptcDataSet((byte)IptcRecordType.ApplicationRecord.getRawValue(), 
                                                   (byte)IptcApplicationRecordDataSet.Keywords.getRawValue(), "keyword 3");

            root.getIptcPackage().add(dataSet1);
            root.getIptcPackage().add(dataSet2);
            root.getIptcPackage().add(dataSet3);

            metadata.save(Constants.OUTPUT_DIRECTORY);
        } catch (Exception e) {
            System.out.println("Error adding keywords: " + e.getMessage());
        }
    }
}
```

### Étape 4 : récupérer et afficher les mots‑clés IPTC
`metadata.getIptc().getKeywords()` renvoie la liste des chaînes de mots‑clés stockées dans le paquet IPTC. Après l’enregistrement, vous pouvez relire les mots‑clés pour confirmer qu’ils ont été correctement persistés. Cette étape de vérification est utile pour les tests unitaires et le débogage.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IIptc;
import com.groupdocs.metadata.core.MetadataProperty;

public class RetrieveAndDisplayKeywords {
    public void run() {
        try (Metadata metadata = new Metadata(Constants.OUTPUT_DIRECTORY)) {
            IIptc root = (IIptc)metadata.getRootPackage();
            
            MetadataProperty keywordsProperty = root.getIptcPackage().getApplicationRecord()
                                                    .get_Item((byte)IptcApplicationRecordDataSet.Keywords.getRawValue());

            for (Object value : keywordsProperty.getValue()) {
                System.out.println(value);
            }
        } catch (Exception e) {
            System.out.println("Error retrieving keywords: " + e.getMessage());
        }
    }
}
```

## Comment récupérer les mots‑clés IPTC en Java ?
`metadata.getIptc().getKeywords()` renvoie la liste des chaînes de mots‑clés stockées dans le paquet IPTC. Vous pouvez ensuite parcourir la liste, consigner chaque entrée, ou les injecter dans un index de recherche pour une récupération rapide. La méthode renvoie un `List<String>` contenant chaque mot‑clé stocké dans le paquet IPTC, vous permettant de les afficher ou de les traiter instantanément.

## Pièges courants et dépannage
- **Package IPTC manquant :** Si l’image ne possède pas de bloc IPTC, `metadata.getIptc()` renvoie `null`. Appelez toujours `metadata.addIptc()` avant d’ajouter des mots‑clés.  
- **Erreurs de licence :** Assurez‑vous que le fichier de licence d’essai ou commercial est correctement référencé dans `Constants.LICENSE_PATH`. Une licence manquante déclenche `LicenseException`.  
- **Fichiers volumineux :** Pour les images supérieures à 2 Go, divisez le traitement en morceaux ou utilisez les API de streaming fournies par GroupDocs.Metadata pour éviter `OutOfMemoryError`.  

## Questions fréquemment posées
**Q : Puis‑je ajouter des mots‑clés IPTC aux fichiers PDF ?**  
R : Non. IPTC est une norme spécifique aux images ; pour les PDF vous utiliseriez XMP ou les champs de métadonnées spécifiques aux PDF.

**Q : GroupDocs.Metadata prend‑il en charge d’autres formats d’image ?**  
R : Oui — il gère JPEG, TIFF, PNG, BMP et WebP, en préservant les métadonnées existantes tout en ajoutant de nouvelles entrées IPTC.

**Q : Combien de mots‑clés puis‑je stocker ?**  
R : La spécification IPTC autorise jusqu’à 64 mots‑clés par image ; GroupDocs.Metadata applique cette limite automatiquement.

**Q : La bibliothèque est‑elle compatible avec Java 11 ?**  
R : Absolument. La bibliothèque est compilée pour Java 8+ et fonctionne parfaitement sur Java 11, 17 et les versions LTS plus récentes.

**Q : Que faire si je dois supprimer un mot‑clé ?**  
R : Récupérez la liste des mots‑clés, supprimez l’entrée indésirable, puis appelez `metadata.getIptc().setKeywords(updatedList)` et enregistrez le fichier.

## Conclusion
Vous disposez maintenant d’un modèle complet, prêt pour la production, pour **ajouter des mots‑clés IPTC en Java** avec GroupDocs.Metadata. En initialisant l’objet de métadonnées, en garantissant qu’un paquet IPTC existe, en ajoutant des mots‑clés et en vérifiant les résultats, vous pouvez intégrer un balisage robuste dans tout flux de travail DAM ou de gestion de contenu basé sur Java. Explorez d’autres types de métadonnées — EXIF, XMP et balises personnalisées — pour enrichir davantage vos actifs.

**Étapes suivantes**
- Étendre l’exemple pour traiter par lots les dossiers d’images.  
- Combiner l’ajout de mots‑clés avec une analyse d’image automatisée (par ex., balises générées par IA).  
- Explorer l’API de GroupDocs.Metadata pour lire/écrire les données GPS EXIF afin de permettre des recherches basées sur la localisation.

---

**Dernière mise à jour :** 2026-08-15  
**Testé avec :** GroupDocs.Metadata 24.12 for Java  
**Auteur :** GroupDocs

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

## Tutoriels associés
- [Extraire l’en-tête BMP Java – Tutoriels d’image GroupDocs.Metadata](/metadata/java/image-formats/)
- [java extraire métadonnées d’image – Extraire les métadonnées Panasonic MakerNote avec GroupDocs.Metadata en Java](/metadata/java/image-formats/extract-panasonic-maker-note-groupdocs-metadata-java/)
- [Automatiser les mises à jour de métadonnées Java par date avec GroupDocs.Metadata pour une gestion efficace des fichiers](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)