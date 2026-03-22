---
date: '2026-03-22'
description: Apprenez à modifier la date de création d’Excel et à mettre à jour les
  métadonnées d’Excel en utilisant GroupDocs.Metadata pour Java. Suivez ce guide étape
  par étape pour ajouter des mots‑clés à Excel et modifier les propriétés du document.
keywords:
- GroupDocs Metadata Java
- update spreadsheet metadata
- Java document formats
title: Modifier la date de création d’Excel avec GroupDocs.Metadata en Java
type: docs
url: /fr/java/document-formats/update-spreadsheet-metadata-groupdocs-java/
weight: 1
---

# Modifier la date de création d'Excel avec GroupDocs.Metadata en Java

Dans les environnements modernes axés sur les données, **modifier la date de création d'Excel** et maintenir les autres métadonnées à jour peut améliorer considérablement l'organisation des documents, leur recherche et la conformité. Que vous manipuliez des rapports financiers, des suivis de projets ou des données d'archives, des métadonnées précises garantissent que les bonnes personnes trouvent les bons fichiers au bon moment. Ce tutoriel vous guide à travers l'utilisation de la bibliothèque GroupDocs.Metadata pour **modifier la date de création d'Excel**, **ajouter des mots‑clés à Excel** et **modifier les propriétés du document Excel** dans une application Java.

## Réponses rapides
- **Puis-je modifier la date de création d'un fichier Excel ?** Oui, en utilisant `setCreatedTime` de GroupDocs.Metadata.  
- **Quelle bibliothèque prend en charge la mise à jour des métadonnées Excel en Java ?** GroupDocs.Metadata for Java.  
- **Ai‑je besoin d'une licence ?** Un essai gratuit suffit pour l'évaluation ; une licence permanente est requise pour la production.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.  
- **Puis‑je ajouter des mots‑clés personnalisés à un classeur Excel ?** Absolument — utilisez `setKeywords` sur les propriétés du document.

## Qu’est‑ce que « modifier la date de création d’Excel » ?
Modifier la date de création d'Excel signifie mettre à jour la propriété intégrée *Created* stockée à l'intérieur du fichier classeur. Cette propriété fait partie des métadonnées standard Office Open XML et peut être éditée programmatiquement sans altérer le contenu réel des feuilles de calcul.

## Pourquoi utiliser GroupDocs.Metadata pour les métadonnées Excel ?
GroupDocs.Metadata offre une API de haut niveau, typée, qui abstrait la manipulation XML de bas niveau requise par le format Office Open XML. Elle vous permet de :

- **Mettre à jour les propriétés principales** telles que l’auteur, l’entreprise et la date de création en un seul appel.  
- **Ajouter des mots‑clés à Excel** pour améliorer les résultats de recherche dans SharePoint, OneDrive ou les systèmes de fichiers locaux.  
- **Modifier les propriétés du document Excel** sans ouvrir le classeur dans Excel, ce qui fait gagner du temps et des ressources.  

## Prérequis
- Java Development Kit (JDK) 8 ou plus récent.  
- Un IDE comme IntelliJ IDEA ou Eclipse.  
- Familiarité de base avec les I/O de fichiers Java.  

## Configuration de GroupDocs.Metadata pour Java

### Installation

Ajoutez le dépôt Maven de GroupDocs.Metadata et la dépendance à votre `pom.xml` :

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

Alternativement, vous pouvez [télécharger la dernière version directement](https://releases.groupdocs.com/metadata/java/) si vous préférez une configuration manuelle.

### Acquisition de licence

GroupDocs propose un essai gratuit pour l'évaluation. Pour une utilisation en production, obtenez une licence temporaire ou permanente auprès du fournisseur. Consultez la [page d'achat de GroupDocs](https://purchase.groupdocs.com/temporary-license/) pour plus de détails.

#### Initialisation de base

Importez les classes nécessaires dans votre fichier source Java :

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.SpreadsheetRootPackage;
```

## Implémentation étape par étape

### Étape 1 : Ouvrir le classeur Excel

Fournissez le chemin du classeur source et créez une instance `Metadata`. Le bloc `try‑with‑resources` garantit que le handle du fichier est fermé automatiquement.

```java
String inputFilePath = "YOUR_DOCUMENT_DIRECTORY/input.xlsx";

try (Metadata metadata = new Metadata(inputFilePath)) {
    // Access the root package for further operations
    SpreadsheetRootPackage root = metadata.getRootPackageGeneric();
}
```

### Étape 2 : Mettre à jour les propriétés de métadonnées intégrées

Vous pouvez maintenant **modifier la date de création d'Excel**, définir l'auteur, la société, la catégorie, et **ajouter des mots‑clés à Excel**. L'appel `new Date()` capture l'horodatage actuel, mais vous pouvez fournir n'importe quel `java.util.Date` dont vous avez besoin.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

> **Astuce :** Utilisez une convention de nommage cohérente pour les mots‑clés (par ex., `project:Q2, finance, confidential`) afin de rendre les recherches futures plus efficaces.

### Étape 3 : Enregistrer le classeur mis à jour

Spécifiez un chemin de sortie et persistez les modifications. Le fichier original reste intact, ce qui est utile pour les pistes d’audit.

```java
String outputFilePath = "YOUR_OUTPUT_DIRECTORY/output.xlsx";
metadata.save(outputFilePath);
```

## Problèmes courants et solutions

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Erreurs de chemin de fichier** | Chemins relatifs/absolus incorrects | Vérifiez à nouveau `inputFilePath` et `outputFilePath`. Utilisez `Paths.get(...)` pour des chemins indépendants de la plateforme. |
| **Version de bibliothèque incompatible** | Utilisation d’une version plus ancienne de GroupDocs.Metadata qui ne supporte pas la méthode `setCreatedTime` | Mettez à jour vers la dernière version (comme indiqué dans le snippet Maven). |
| **Licence manquante** | Période d'essai expirée | Appliquez une licence temporaire ou achetez une licence complète via la page d'achat. |
| **Utilisation mémoire élevée pour un grand classeur** | Le chargement de fichiers Excel massifs consomme de la mémoire du tas | Traitez les fichiers par lots et augmentez le tas JVM (`-Xmx`) si nécessaire. |

## Questions fréquentes

**Q : Quelles versions de Java sont prises en charge par GroupDocs.Metadata ?**  
R : Java 8 et les versions ultérieures sont entièrement prises en charge.

**Q : Comment gérer les exceptions lors de la mise à jour des métadonnées ?**  
R : Enveloppez le code dans un bloc `try‑catch` et consignez `MetadataException` pour capturer les erreurs d'E/S ou de format.

**Q : Puis‑je mettre à jour plusieurs fichiers Excel en une seule exécution ?**  
R : Oui, parcourez une collection de chemins de fichiers, mais surveillez l'utilisation de la mémoire pour les gros lots.

**Q : Est‑il possible d'annuler les modifications apportées aux métadonnées ?**  
R : Conservez une sauvegarde du classeur original avant d'appliquer les mises à jour, puis restaurez‑le si nécessaire.

**Q : Où puis‑je trouver une documentation plus détaillée ?**  
R : Voir le guide officiel à [GroupDocs Metadata Documentation](https://docs.groupdocs.com/metadata/java/).

## Applications pratiques

1. **Audits financiers** – Enregistrez qui a modifié un classeur et quand, fournissant une piste d’audit.  
2. **Gestion de projet** – Étiquetez les feuilles de calcul avec des mots‑clés spécifiques au projet pour une récupération rapide.  
3. **Archivage des données** – Conservez les dates de création originales et les informations de l’entreprise pour la conformité.

## Conseils de performance

- Limitez les opérations de métadonnées par exécution pour éviter une consommation excessive de mémoire.  
- Fermez rapidement l'objet `Metadata` (le modèle `try‑with‑resources` le fait automatiquement).  
- Pour des classeurs très volumineux, envisagez de les traiter dans un thread en arrière‑plan afin de garder l'interface réactive.

## Conclusion

Vous savez maintenant comment **modifier la date de création d'Excel**, **ajouter des mots‑clés à Excel** et **modifier les propriétés du document Excel** en utilisant GroupDocs.Metadata en Java. Cette capacité vous permet de garder vos feuilles de calcul bien organisées, recherchables et conformes aux politiques de gouvernance interne. Comme prochaine étape, explorez d’autres fonctionnalités de métadonnées telles que les propriétés personnalisées ou le traitement par lots pour optimiser davantage votre flux de gestion de documents.

---

**Last Updated:** 2026-03-22  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs  

**Ressources**
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [Référence API](https://reference.groupdocs.com/metadata/java/)
- [Télécharger GroupDocs.Metadata](https://releases.groupdocs.com/metadata/java/)
- [Dépôt GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Forum d'assistance gratuit](https://forum.groupdocs.com/c/metadata/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)