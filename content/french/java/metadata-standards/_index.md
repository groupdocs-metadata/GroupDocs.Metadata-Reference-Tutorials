---
date: 2026-07-26
description: Guide étape par étape pour lire les métadonnées IPTC avec GroupDocs.Metadata
  pour Java, ainsi que comment ajouter du XMP, extraire les EXIF et écrire des métadonnées
  XMP.
keywords:
- read iptc metadata
- how to add xmp
- how to extract exif
- write xmp metadata
- read xmp properties
lastmod: 2026-07-26
og_description: Apprenez à lire les métadonnées IPTC avec GroupDocs.Metadata pour
  Java. Ce tutoriel couvre également comment ajouter du XMP, extraire les EXIF et
  écrire des métadonnées XMP en Java.
og_image_alt: 'Guide: read IPTC metadata using GroupDocs.Metadata Java library'
og_title: Lire les métadonnées IPTC avec GroupDocs.Metadata pour Java – Guide complet
schemas:
- author: GroupDocs
  dateModified: '2026-07-26'
  description: Step‑by‑step guide to read IPTC metadata using GroupDocs.Metadata for
    Java, plus how to add XMP, extract EXIF, and write XMP metadata.
  headline: Read IPTC Metadata with GroupDocs.Metadata for Java
  type: TechArticle
- description: Step‑by‑step guide to read IPTC metadata using GroupDocs.Metadata for
    Java, plus how to add XMP, extract EXIF, and write XMP metadata.
  name: Read IPTC Metadata with GroupDocs.Metadata for Java
  steps:
  - name: Initialise the Metadata object
    text: The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata.
      Provide the file path and optional load options.
  - name: Access IPTC tags
    text: Call `metadata.getIptc()` to obtain the IPTC handler, then `getAllTags()`
      returns a `Map<String, String>` containing every available IPTC field.
  - name: Process the tags
    text: Iterate over the map, log the values, or store them in your database. You
      can also filter for specific keys such as “Keywords” or “Creator”.
  - name: (Optional) Read EXIF or XMP in the same session
    text: Use `metadata.getExif()` or `metadata.getXmp()` to pull additional metadata
      without reopening the file. This is useful when you need to combine IPTC keywords
      with camera settings.
  type: HowTo
- questions:
  - answer: Yes, GroupDocs.Metadata extracts IPTC embedded in PDF/X‑4 files, returning
      the same tag map as with images.
    question: Can I read IPTC metadata from PDF files?
  - answer: “How to add XMP” focuses on embedding a new XMP package, while “write
      XMP metadata” refers to updating existing XMP properties; both use the same
      API methods.
    question: How does “how to add xmp” differ from “write xmp metadata”?
  - answer: The library extracts EXIF from RAW, JPEG, TIFF, and PSD files; for proprietary
      RAW types, ensure the latest version is installed.
    question: Is “how to extract exif” supported for RAW formats?
  - answer: Yes, `metadata.getXmp().getProperties()` returns a dictionary of all XMP
      key‑value pairs, satisfying the “read xmp properties” requirement.
    question: Does the library support reading XMP properties directly?
  - answer: Version 22.11 or newer includes full EXIF support for Java; earlier releases
      lack some newer camera tags.
    question: What version of GroupDocs.Metadata is required for “extract exif java”?
  type: FAQPage
tags:
- iptc metadata
- groupdocs metadata
- java document processing
- exif extraction
- xmp handling
title: Lire les métadonnées IPTC avec GroupDocs.Metadata pour Java
type: docs
url: /fr/java/metadata-standards/
weight: 4
---

# Lire les métadonnées IPTC avec GroupDocs.Metadata pour Java

Si vous devez **lire les métadonnées IPTC** à partir d'images, de PDF ou d'autres médias dans une application Java, vous êtes au bon endroit. Ce tutoriel vous guide dans l'utilisation de la bibliothèque GroupDocs.Metadata pour extraire les balises IPTC, montre où ajouter des paquets XMP personnalisés, et démontre même comment récupérer les informations EXIF lorsque cela est nécessaire. À la fin, vous disposerez d'une approche claire, prête pour la production, qui fonctionne sur plus de 50 formats de fichiers et s'adapte aux documents de plusieurs centaines de pages sans charger le fichier complet en mémoire.

## Réponses rapides
- **Qu'est‑ce que les métadonnées IPTC ?** C’est un ensemble standardisé de balises décrivant le contenu d’une image, comme les mots‑clés, le créateur et le droit d’auteur.
- **Quelle bibliothèque lit les IPTC en Java ?** GroupDocs.Metadata for Java fournit une API simple pour lire et écrire les IPTC.
- **Puis‑je également lire les EXIF et XMP ?** Oui – la même bibliothèque prend en charge l’extraction des EXIF et XMP en un seul appel.
- **Ai‑je besoin d’une licence ?** Une licence temporaire fonctionne pour l’évaluation ; une licence complète est requise pour la production.
- **Quelles versions de Java sont prises en charge ?** Java 8 à 17 sont entièrement compatibles.

## Qu’est‑ce que la lecture des métadonnées IPTC ?
*Lire les métadonnées IPTC* signifie récupérer les balises descriptives standardisées intégrées dans un fichier image. Ces balises permettent une gestion d’actifs searchable, une catégorisation automatisée et la conformité aux flux de travail de publication, permettant aux applications d’indexer, filtrer et afficher les médias en fonction du créateur, des mots‑clés, du droit d’auteur et d’autres propriétés essentielles.

## Pourquoi utiliser GroupDocs.Metadata pour Java ?
GroupDocs.Metadata prend en charge **plus de 50 formats d’entrée et de sortie** — y compris JPEG, TIFF, PSD, PDF et EPUB — et peut traiter **des documents jusqu’à 1 Go** sans charger le fichier complet en RAM. La bibliothèque offre également des opérations **thread‑safe**, un streaming haute performance et une validation intégrée des normes de métadonnées, ce qui la rend idéale pour les pipelines d’actifs numériques à l’échelle de l’entreprise qui exigent fiabilité et rapidité.

## Prérequis
- Java 8 ou version ultérieure installé.
- Système de build Maven ou Gradle.
- Bibliothèque GroupDocs.Metadata pour Java (ajoutez la dépendance Maven indiquée dans la documentation officielle).
- Un fichier de licence temporaire ou complet (placez‑le dans les ressources de votre projet).

## Comment lire les métadonnées IPTC étape par étape
Chargez votre fichier, obtenez le gestionnaire IPTC et récupérez la carte des balises — le tout dans un flux de travail concis en trois étapes qui peut être encapsulé dans une méthode utilitaire pour être réutilisé dans votre code.

**Réponse directe (45 mots) :**  
Créez un objet `Metadata` pour le fichier cible, appelez `metadata.getIptc().getAllTags()` pour obtenir une carte des noms et valeurs des balises, puis parcourez la carte pour consigner, stocker ou traiter davantage les informations IPTC selon les besoins.

La classe `Metadata` est le point d’entrée principal qui charge un fichier et fournit l’accès à ses sections de métadonnées.

### Étape 1 : Initialise l’objet Metadata
La classe `Metadata` est le point d’entrée pour toutes les opérations de métadonnées dans GroupDocs.Metadata. Fournissez le chemin du fichier et les options de chargement facultatives.

### Étape 2 : Accéder aux balises IPTC
Appelez `metadata.getIptc()` pour obtenir le gestionnaire IPTC, puis `getAllTags()` renvoie un `Map<String, String>` contenant chaque champ IPTC disponible.

### Étape 3 : Traiter les balises
Parcourez la carte, consignez les valeurs ou stockez‑les dans votre base de données. Vous pouvez également filtrer des clés spécifiques comme « Keywords » ou « Creator ».

### Étape 4 : (Facultatif) Lire EXIF ou XMP dans la même session
Utilisez `metadata.getExif()` ou `metadata.getXmp()` pour extraire des métadonnées supplémentaires sans rouvrir le fichier. Cela est utile lorsque vous devez combiner les mots‑clés IPTC avec les réglages de l’appareil photo.

## Comment ajouter des métadonnées XMP à un fichier ?
Intégrer des paquets XMP personnalisés aux côtés des données IPTC existantes est simple : créez un paquet XMP, attachez‑le à l’objet metadata, puis enregistrez le fichier. Cette opération préserve les métadonnées existantes tout en étendant le fichier avec de nouvelles propriétés conformes aux normes.

**Réponse directe (48 mots) :**  
Instanciez un `XmpPackage`, remplissez‑le avec vos propriétés XMP personnalisées, ajoutez le paquet au fichier via `metadata.getXmp().addPackage(xmpPackage)`, puis appelez finalement `metadata.save()` pour écrire les modifications sur le disque, garantissant que le nouveau bloc XMP est entièrement intégré.

La classe `XmpPackage` représente un conteneur pour des propriétés XMP personnalisées pouvant être intégrées dans un fichier.

## Pièges courants et dépannage
- **Section IPTC manquante :** Certains fichiers PNG n’ont pas d’IPTC ; vérifiez toujours `metadata.getIptc().isPresent()` avant d’accéder aux balises.
- **Images volumineuses :** Pour les fichiers de plus de 200 Mo, activez le mode streaming via `LoadOptions.setUseMemoryCache(true)` pour éviter `OutOfMemoryError`. La classe `LoadOptions` vous permet de configurer la façon dont les fichiers sont chargés, comme activer le streaming en cache mémoire.
- **Erreurs de licence :** Assurez‑vous que le chemin du fichier de licence est correct ; sinon, la bibliothèque fonctionne en mode d’essai et peut limiter le nombre de fichiers traités.

## Questions fréquemment posées
**Q : Puis‑je lire les métadonnées IPTC à partir de fichiers PDF ?**  
R : Oui, GroupDocs.Metadata extrait les IPTC intégrés dans les fichiers PDF/X‑4, renvoyant la même carte de balises qu’avec les images.

**Q : En quoi « how to add xmp » diffère‑t‑il de « write xmp metadata » ?**  
R : « How to add XMP » se concentre sur l’intégration d’un nouveau paquet XMP, tandis que « write XMP metadata » fait référence à la mise à jour des propriétés XMP existantes ; les deux utilisent les mêmes méthodes d’API.

**Q : « how to extract exif » est‑il pris en charge pour les formats RAW ?**  
R : La bibliothèque extrait les EXIF des fichiers RAW, JPEG, TIFF et PSD ; pour les types RAW propriétaires, assurez‑vous que la dernière version est installée.

**Q : La bibliothèque prend‑elle en charge la lecture directe des propriétés XMP ?**  
R : Oui, `metadata.getXmp().getProperties()` renvoie un dictionnaire de toutes les paires clé‑valeur XMP, répondant à l’exigence « read xmp properties ».

**Q : Quelle version de GroupDocs.Metadata est requise pour « extract exif java » ?**  
R : La version 22.11 ou supérieure inclut la prise en charge complète des EXIF pour Java ; les versions antérieures manquent de certaines nouvelles balises d’appareil photo.

---

**Dernière mise à jour :** 2026-07-26  
**Testé avec :** GroupDocs.Metadata for Java 23.5  
**Auteur :** GroupDocs  

---  

## Tutoriels disponibles

### [Ajouter des métadonnées XMP personnalisées aux fichiers avec GroupDocs.Metadata Java&#58; Guide complet](./add-custom-xmp-metadata-groupdocs-java/)
Apprenez à ajouter des paquets de métadonnées XMP personnalisés aux fichiers en utilisant GroupDocs.Metadata pour Java. Améliorez la gestion des données de fichiers avec ce tutoriel étape par étape.

### [Gestion des métadonnées EXIF en Java&#58; Guide complet utilisant GroupDocs.Metadata](./exif-metadata-management-java-groupdocs-metadata/)
Apprenez à gérer efficacement les métadonnées EXIF dans les applications Java en utilisant GroupDocs.Metadata, couvrant l’installation, les mises à jour et l’enregistrement des modifications.

### [Extraire les métadonnées Dublin Core des fichiers EPUB avec GroupDocs.Metadata en Java](./extract-dublin-core-metadata-epub-groupdocs-java/)
Apprenez à extraire efficacement les métadonnées Dublin Core des fichiers EPUB en utilisant la bibliothèque GroupDocs.Metadata pour Java. Ce guide couvre l’installation, la mise en œuvre et les applications pratiques.

### [Extraire les métadonnées Dublin Core des documents Word avec Java et GroupDocs.Metadata](./extract-dublin-core-metadata-word-docs-java/)
Apprenez à extraire efficacement les métadonnées Dublin Core des documents Word en utilisant la bibliothèque GroupDocs.Metadata en Java. Suivez ce guide étape par étape pour améliorer vos processus de gestion de documents.

### [Extraire les métadonnées EXIF des fichiers PSD avec GroupDocs.Metadata pour Java | Guide complet](./extract-exif-metadata-psd-groupdocs-java/)
Apprenez à extraire les métadonnées EXIF des fichiers PSD en utilisant GroupDocs.Metadata pour Java. Ce guide couvre les techniques d’extraction de métadonnées de base et avancées.

### [Extraire la balise Software EXIF en Java&#58; Guide complet utilisant GroupDocs.Metadata](./master-exif-data-java-groupdocs-metadata/)
Apprenez à extraire la balise software des données EXIF d’image en utilisant GroupDocs.Metadata pour Java. Améliorez la gestion des actifs numériques et l’expérience utilisateur.

### [Extraire les métadonnées XMP avec GroupDocs.Metadata pour Java&#58; Guide complet](./extract-xmp-metadata-groupdocs-metadata-java/)
Apprenez à extraire et gérer les métadonnées XMP en Java avec GroupDocs.Metadata. Ce guide couvre les extractions de métadonnées de base, Dublin Core et spécifiques à Photoshop.

### [Comment extraire les métadonnées Dublin Core avec GroupDocs.Metadata pour Java&#58; Guide complet](./extract-dublin-core-metadata-groupdocs-java/)
Apprenez à extraire et gérer les métadonnées Dublin Core en Java en utilisant GroupDocs.Metadata. Ce guide couvre l’installation, la mise en œuvre et les applications pratiques.

### [Comment extraire les métadonnées EXIF des images TIFF avec GroupDocs.Metadata en Java](./extract-exif-metadata-groupdocs-java-tiff/)
Apprenez à extraire et gérer les métadonnées EXIF des fichiers TIFF en utilisant GroupDocs.Metadata pour Java. Améliorez vos applications de gestion d’actifs numériques avec des informations d’image détaillées.

### [Comment extraire les métadonnées IPTC des images TIFF avec GroupDocs.Metadata pour Java](./extract-iptc-metadata-tiff-groupdocs-java/)
Apprenez à extraire efficacement les métadonnées IPTC des images TIFF en utilisant GroupDocs.Metadata pour Java. Rationalisez la gestion de vos données d’image avec ce guide étape par étape.

### [Comment lire et gérer les métadonnées DICOM en Java avec GroupDocs.Metadata](./master-dicom-metadata-groupdocs-metadata-java/)
Apprenez à extraire et gérer efficacement les métadonnées DICOM dans vos applications Java en utilisant la puissante bibliothèque GroupDocs.Metadata.

### [Comment lire et gérer les métadonnées EXIF en Java avec GroupDocs.Metadata](./read-exif-metadata-groupdocs-java/)
Apprenez à extraire et exploiter efficacement les métadonnées EXIF d’images en utilisant GroupDocs.Metadata pour Java. Ce guide couvre l’installation, la lecture des balises et les applications pratiques.

### [Comment supprimer les métadonnées EXIF des JPEG avec GroupDocs.Metadata pour Java&#58; Guide complet](./remove-exif-metadata-jpeg-groupdocs-java/)
Apprenez à supprimer facilement les métadonnées EXIF sensibles des fichiers JPEG en utilisant GroupDocs.Metadata pour Java. Améliorez la confidentialité et optimisez vos images avec ce guide étape par étape.

### [Comment définir les métadonnées IPTC avec GroupDocs.Metadata en Java&#58; Guide complet](./set-iptc-metadata-groupdocs-java-guide/)
Apprenez à gérer et définir efficacement les métadonnées IPTC manquantes en utilisant GroupDocs.Metadata pour Java. Améliorez dès aujourd’hui vos applications de gestion d’images.

### [Gestion des métadonnées Java avec GroupDocs&#58; Ajouter & récupérer les mots‑clés IPTC pour la gestion d’actifs numériques](./java-metadata-groupdocs-add-retrieve-iptc-keywords/)
Apprenez à ajouter et récupérer efficacement les mots‑clés IPTC en utilisant GroupDocs.Metadata en Java, améliorant la gestion des actifs numériques.

### [Maîtriser GroupDocs.Metadata Java&#58; Extraire les métadonnées IPTC des JPEG sans effort](./reading-iptc-metadata-jpeg-groupdocs-metadata-java/)
Apprenez à extraire les métadonnées IPTC des fichiers JPEG en utilisant GroupDocs.Metadata pour Java. Un guide étape par étape pour gérer efficacement les actifs numériques.

### [Maîtriser la gestion des métadonnées IPTC Java avec GroupDocs.Metadata pour Java](./java-iptc-metadata-groupdocs-metadata/)
Apprenez à gérer et personnaliser les métadonnées IPTC dans les applications Java en utilisant GroupDocs.Metadata. Améliorez l’organisation des documents, la recherche et la gestion des actifs.

### [Lire les métadonnées IPTC en Java avec la bibliothèque GroupDocs.Metadata](./groupdocs-metadata-java-read-iptc-datasets/)
Apprenez à lire et gérer efficacement les métadonnées IPTC dans les images en utilisant la bibliothèque GroupDocs.Metadata en Java. Découvrez des instructions étape par étape, les meilleures pratiques et des applications pratiques.

## Ressources supplémentaires
- [Documentation GroupDocs.Metadata pour Java](https://docs.groupdocs.com/metadata/java/)
- [Référence API GroupDocs.Metadata pour Java](https://reference.groupdocs.com/metadata/java/)
- [Télécharger GroupDocs.Metadata pour Java](https://releases.groupdocs.com/metadata/java/)
- [Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata)
- [Support gratuit](https://forum.groupdocs.com/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)

## Tutoriels associés
- [Gestion des métadonnées Java avec GroupDocs&#58; Ajouter & récupérer les mots‑clés IPTC pour la gestion d’actifs numériques](/metadata/java/metadata-standards/java-metadata-groupdocs-add-retrieve-iptc-keywords/)
- [Extraire les métadonnées XMP avec GroupDocs.Metadata pour Java&#58; Guide complet](/metadata/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/)
- [Extraire les métadonnées EXIF des fichiers PSD avec GroupDocs.Metadata pour Java | Guide complet](/metadata/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/)