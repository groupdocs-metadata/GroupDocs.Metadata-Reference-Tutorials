---
date: '2026-06-22'
description: Apprenez à lire les métadonnées sevenzip java en utilisant GroupDocs.Metadata
  pour Java, y compris comment obtenir la taille compressée java et d'autres propriétés
  d'archive.
keywords:
- read sevenzip metadata java
- get compressed size java
- GroupDocs.Metadata Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-22'
  description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  headline: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to read sevenzip metadata java using GroupDocs.Metadata for
    Java, including how to get compressed size java and other archive properties.
  name: How to Read SevenZip Metadata Java with GroupDocs.Metadata
  steps:
  - name: Initialize Metadata Object
    text: The `Metadata` class represents the entry point for loading and interacting
      with archive files.
  - name: Obtain the Root Package
    text: The `getRootPackageGeneric()` method returns a generic view of the archive's
      root package, allowing you to work with entries without needing format‑specific
      code. - **Why Use `getRootPackageGeneric()`?** It provides a generalized view
      of the archive's contents, making it easier to iterate over its e
  - name: Iterate Over Archive Entries
    text: The `SevenZipPackage` class represents the SevenZip container, and each
      entry is exposed as a `SevenZipFileInfo` object. The `SevenZipFileInfo` class
      provides direct access to properties like name, compressed size, and modification
      date. - **Why Extract These Properties?** Knowing file sizes helps m
  - name: Clean Up Resources
    text: Calling `close()` on the `Metadata` instance releases native resources and
      avoids memory leaks in long‑running services. - **Why Dispose?** Properly disposing
      of objects helps prevent memory leaks in long‑running applications.
  type: HowTo
- questions:
  - answer: GroupDocs.Metadata for Java – a single‑API solution for over 70 archive
      and document formats.
    question: What library should I use?
  - answer: Yes – call `getSevenZipPackage().getFiles()` after initializing the `Metadata`
      object.
    question: Can I list files inside a SevenZip archive?
  - answer: A free trial works for evaluation; a full license is required for production.
    question: Do I need a license?
  - answer: JDK 8 or higher (compatible with Java 17 LTS).
    question: Which Java version is supported?
  - answer: Not mandatory, but Maven handles transitive dependencies automatically.
    question: Is Maven required?
  type: FAQPage
title: Comment lire les métadonnées SevenZip Java avec GroupDocs.Metadata
type: docs
url: /fr/java/archive-formats/read-sevenzip-metadata-groupdocs-java/
weight: 1
---

# Comment lire les métadonnées SevenZip Java avec GroupDocs.Metadata

Si vous devez **read sevenzip metadata java** depuis une application Java, vous êtes au bon endroit. Dans ce tutoriel, nous parcourrons l’utilisation de **GroupDocs.Metadata** pour extraire les noms de fichiers, les tailles compressées, les tailles non compressées, les dates de modification, et plus encore — exactement les données dont vous avez besoin pour la validation des sauvegardes, la synchronisation ou les tâches d’optimisation du stockage.

## Introduction

Vous avez du mal à accéder et à lire les propriétés de métadonnées des fichiers d’archive SevenZip avec Java ? Ce tutoriel vous guidera à travers le processus d’utilisation de **GroupDocs.Metadata**. Une bibliothèque puissante, elle simplifie l’extraction d’informations essentielles telles que les noms de fichiers, les tailles et les dates de modification directement depuis vos archives.

## Réponses rapides

- **Quelle bibliothèque devrais-je utiliser ?** GroupDocs.Metadata for Java – une solution à API unique pour plus de 70 formats d’archive et de document.  
- **Puis-je lister les fichiers à l’intérieur d’une archive SevenZip ?** Oui – appelez `getSevenZipPackage().getFiles()` après avoir initialisé l’objet `Metadata`.  
- **Ai-je besoin d’une licence ?** Un essai gratuit suffit pour l’évaluation ; une licence complète est requise pour la production.  
- **Quelle version de Java est prise en charge ?** JDK 8 ou supérieur (compatible avec Java 17 LTS).  
- **Maven est‑il obligatoire ?** Ce n’est pas obligatoire, mais Maven gère automatiquement les dépendances transitives.  

## Qu’est‑ce que « how to read sevenzip » en Java ?

Lire les métadonnées SevenZip signifie ouvrir le conteneur `.7z`, énumérer chaque entrée et extraire des propriétés telles que **compressed size**, **uncompressed size**, **file name** et **modification date** sans extraire les fichiers réels. Ce processus vous donne un aperçu de la composition de l’archive, permet de vérifier l’intégrité des sauvegardes et vous aide à prendre des décisions de capacité de stockage sans le coût d’une extraction complète.

## read sevenzip metadata java

Utiliser le mot‑clé principal dans un titre dédié aide à la fois les lecteurs et les moteurs de recherche à comprendre le sujet de ce guide. Ci-dessous, nous détaillerons les étapes exactes dont vous avez besoin pour **read sevenzip metadata java** efficacement.

## Pourquoi utiliser GroupDocs.Metadata Java pour l’extraction de métadonnées ?

GroupDocs.Metadata ne lit que les informations d’en‑tête nécessaires à l’extraction des métadonnées, de sorte que l’opération se termine en millisecondes même pour des archives multi‑gigaoctets. Il prend en charge **70+** formats d’archive et de document, traite les archives jusqu’à **2 GB** sans charger le fichier complet en mémoire, et fournit une API cohérente pour tous les types pris en charge.

## Prérequis

Avant de plonger dans **GroupDocs.Metadata for Java**, assurez‑vous que votre environnement de développement est correctement configuré. Voici ce dont vous avez besoin :

- **Java Development Kit (JDK) :** Version 8 ou supérieure.  
- **Maven :** Recommandé pour la gestion des dépendances, bien que vous puissiez ajouter le JAR manuellement.  
- **Connaissances de base en Java :** Familiarité avec les classes, les méthodes et la gestion des exceptions.  

## Configuration de GroupDocs.Metadata pour Java

Pour utiliser GroupDocs.Metadata, incluez‑le dans votre projet via Maven ou en téléchargeant directement la bibliothèque.

### Utilisation de Maven

Ajoutez la configuration suivante à votre fichier `pom.xml` :

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

### Téléchargement direct

Alternativement, téléchargez la dernière version depuis [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Acquisition de licence

1. **Essai gratuit :** Commencez avec un essai gratuit pour tester les capacités de GroupDocs.Metadata.  
2. **Licence temporaire :** Demandez une licence temporaire si vous avez besoin d’un accès prolongé à des fins d’évaluation.  
3. **Achat :** Pour une utilisation à long terme, envisagez d’acheter une licence complète.  

Une fois la configuration terminée, passons à la mise en œuvre de la fonctionnalité de lecture des métadonnées.

## Guide d’implémentation

### Accès aux métadonnées des archives SevenZip

Dans cette section, nous extrairons et afficherons les propriétés de métadonnées telles que les noms de fichiers et les tailles d’une archive SevenZip.

#### Étape 1 : Initialiser l’objet Metadata

La classe `Metadata` représente le point d’entrée pour charger et interagir avec les fichiers d’archive.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SevenZipFile;
import com.groupdocs.metadata.core.SevenZipRootPackage;

public class ReadSevenZipMetadata {
    public static void main(String[] args) {
        Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.7z");
```

#### Étape 2 : Obtenir le package racine

La méthode `getRootPackageGeneric()` renvoie une vue générique du package racine de l’archive, vous permettant de travailler avec les entrées sans nécessiter de code spécifique au format.

```java
try (
    SevenZipRootPackage root = metadata.getRootPackageGeneric()) {
```

- **Pourquoi utiliser `getRootPackageGeneric()` ?** Elle fournit une vue généralisée du contenu de l’archive, facilitant l’itération sur ses entrées sans se soucier des formats de fichiers spécifiques.

#### Étape 3 : Parcourir les entrées de l’archive

La classe `SevenZipPackage` représente le conteneur SevenZip, et chaque entrée est exposée sous forme d’un objet `SevenZipFileInfo`. La classe `SevenZipFileInfo` offre un accès direct aux propriétés telles que le nom, la taille compressée et la date de modification.

```java
int totalEntries = root.getSevenZipPackage().getTotalEntries();

for (SevenZipFile file : root.getSevenZipPackage().getFiles()) {
    String name = file.getName();
    long compressedSize = file.getCompressedSize();
    java.util.Date modificationDateTime = file.getModificationDateTime();
    long uncompressedSize = file.getUncompressedSize();

    // Output metadata properties for each file in the archive
    System.out.println("File Name: " + name);
    System.out.println("Compressed Size: " + compressedSize);
    System.out.println("Modification Date and Time: " + modificationDateTime);
    System.out.println("Uncompressed Size: " + uncompressedSize);
}
```

- **Pourquoi extraire ces propriétés ?** Connaître les tailles des fichiers aide à gérer le stockage, tandis que la date de modification peut être cruciale pour les tâches de synchronisation. L’appel `getCompressedSize()` est la façon Java d’**get compressed size java** pour chaque entrée.

#### Étape 4 : Nettoyer les ressources

Appeler `close()` sur l’instance `Metadata` libère les ressources natives et évite les fuites de mémoire dans les services de longue durée.

```java
} finally {
    metadata.dispose();
}
```

- **Pourquoi libérer ?** Libérer correctement les objets aide à prévenir les fuites de mémoire dans les applications de longue durée.

## Comment extraire les métadonnées efficacement ?

Chargez l’archive SevenZip avec une seule instance `Metadata`, appelez `getRootPackageGeneric()` une fois, puis parcourez les entrées avec une boucle `for‑each`. Ce modèle évite les I/O répétés, réduit la pression sur le GC et se termine en temps O(n) où *n* est le nombre d’entrées.

## Applications pratiques

Comprendre comment **read sevenzip metadata java** offre de nombreux avantages concrets :

1. **Gestion des sauvegardes de données :** Vérifiez rapidement l’intégrité et la complétude des archives de sauvegarde.  
2. **Outils de synchronisation de fichiers :** Utilisez les dates de modification pour décider quels fichiers doivent être mis à jour.  
3. **Optimisation du stockage :** Comparez les tailles compressées et non compressées pour planifier la capacité.  

L’intégration avec d’autres systèmes est possible, permettant une extraction automatisée des métadonnées dans le cadre de flux de travail de gestion de données plus larges.

## Considérations de performance

Lorsque vous travaillez avec GroupDocs.Metadata et de grandes archives, gardez ces conseils à l’esprit :

- **Traitement par lots :** Traitez les fichiers par lots pour gérer efficacement l’utilisation de la mémoire.  
- **Gestion efficace des exceptions :** Utilisez try‑with‑resources pour une gestion automatique des ressources.  
- **Traitement asynchrone :** Mettez en œuvre des techniques asynchrones pour les charges de travail lourdes.

## Problèmes courants et solutions

| Problème | Solution |
|----------|----------|
| **`NullPointerException` when accessing a file** | Vérifiez que le chemin de l’archive est correct et que le fichier n’est pas corrompu. |
| **Memory spikes on huge archives** | Activez le traitement par lots ou augmentez la taille du tas JVM (`-Xmx`). |
| **License not recognized** | Assurez‑vous que le fichier de licence est placé dans le répertoire de travail de l’application ou défini via `License.setLicense(path)`. |

## Questions fréquentes

**Q :** Qu’est‑ce que GroupDocs.Metadata ?  
**A :** C’est une bibliothèque Java pour gérer les métadonnées à travers différents formats de fichiers, y compris les archives SevenZip.

**Q :** Puis‑je utiliser GroupDocs.Metadata sans Maven ?  
**A :** Oui, vous pouvez télécharger le JAR depuis le site officiel et l’ajouter au classpath de votre projet.

**Q :** Comment gérer efficacement les grandes archives ?  
**A :** Mettez en œuvre le traitement par lots ou utilisez des flux asynchrones pour limiter la consommation de mémoire.

**Q :** Où puis‑je trouver des instructions plus détaillées ?  
**A :** Consultez la [official documentation](https://docs.groupdocs.com/metadata/java/) pour des références API complètes.

**Q :** Que faire si je rencontre des problèmes avec la bibliothèque ?  
**A :** Posez votre question à la communauté sur le [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/).

## Ressources

- **Documentation :** Explorez davantage sur [GroupDocs.Metadata Documentation](https://docs.groupdocs.com/metadata/java/)  
- **Documentation officielle :** [official documentation](https://docs.groupdocs.com/metadata/java/)  
- **Référence API :** Consultez les informations détaillées de l’API sur [GroupDocs.API Reference](https://reference.groupdocs.com/metadata/java/)  
- **Téléchargement :** Obtenez la dernière version depuis [GroupDocs Downloads](https://releases.groupdocs.com/metadata/java/)  
- **Dépôt GitHub :** Accédez aux exemples de code sur [GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)  
- **Forum de support gratuit :** Rejoignez les discussions ou posez des questions sur [GroupDocs Free Support](https://forum.groupdocs.com/c/metadata/)

---

**Dernière mise à jour :** 2026-06-22  
**Testé avec :** GroupDocs.Metadata 24.12 pour Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment lire les fichiers TAR et extraire les métadonnées avec GroupDocs.Metadata pour Java](/metadata/java/archive-formats/extract-tar-metadata-groupdocs-java-guide/)  
- [Mettre à jour le commentaire ZIP Java – Comment mettre à jour les commentaires d’archive ZIP avec GroupDocs.Metadata](/metadata/java/archive-formats/update-zip-archive-comments-groupdocs-metadata-java/)  
- [Extraire les métadonnées vidéo Java : comment lire les fichiers AVI avec GroupDocs.Metadata](/metadata/java/audio-video-formats/extract-avi-metadata-groupdocs-metadata-java/)