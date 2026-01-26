---
date: '2026-01-26'
description: Apprenez à lire la date de création et à extraire d’autres propriétés
  de documents à partir de présentations PowerPoint avec GroupDocs.Metadata pour Java.
  Idéal pour la gestion documentaire et la conformité.
keywords:
- read created time java
- java extract document properties
- presentation metadata
title: Comment lire l'heure de création Java des fichiers de présentation à l'aide
  de GroupDocs.Metadata – Guide étape par étape
type: docs
url: /fr/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# Comment lire la date de création java à partir de fichiers de présentation avec GroupDocs.Metadata

La gestion des métadonnées est une pierre angulaire des flux de travail modernes de documents. Dans ce tutoriel, vous apprendrez **comment lire la date de création java** et extraire d’autres propriétés utiles — telles que l’auteur, l’entreprise et les mots‑clés — d’une présentation PowerPoint en utilisant **GroupDocs.Metadata for Java**. À la fin, vous serez prêt à intégrer ces détails dans des systèmes de gestion de documents, des rapports de conformité ou toute application basée sur Java qui doit comprendre la provenance d’un fichier.

## Réponses rapides
- **Que signifie « read created time java » ?** C’est le processus de récupération du horodatage de création d’un fichier via du code Java.  
- **Quelle bibliothèque prend‑en charge cela ?** GroupDocs.Metadata for Java fournit une API claire pour toutes les propriétés intégrées des présentations.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour le développement ; une licence permanente est requise pour la production.  
- **Puis‑je extraire d’autres propriétés en même temps ?** Oui — l’auteur, l’entreprise, la catégorie et plus encore sont disponibles via la même API.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.

## Qu’est‑ce que « read created time java » ?
Lire la date de création d’un document en Java signifie accéder au champ de métadonnées qui indique quand le fichier a été généré à l’origine. Ce horodatage est essentiel pour le contrôle de version, les pistes d’audit et la vérification de conformité.

## Pourquoi utiliser GroupDocs.Metadata for Java pour extraire les propriétés d’un document ?
GroupDocs.Metadata abstrait les complexités des différents formats de fichiers, vous permettant de vous concentrer sur la logique métier plutôt que sur l’analyse de bas niveau. Il prend en charge PowerPoint, PDF, Word et de nombreux types d’images, ce qui en fait un polyvalent pour tout projet Java qui doit **java extract document properties** de manière fiable.

## Prérequis
- **GroupDocs.Metadata for Java** version 24.12 ou ultérieure.  
- Java Development Kit (JDK 8 ou plus récent).  
- Un IDE tel qu’IntelliJ IDEA ou Eclipse.  
- Connaissances de base en gestion de fichiers Java.

## Configuration de GroupDocs.Metadata pour Java

### Configuration Maven
Si vous gérez les dépendances avec Maven, ajoutez le dépôt et la dépendance à votre `pom.xml` :

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
Sinon, vous pouvez télécharger la bibliothèque depuis la page officielle des versions :

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

#### Étapes d’obtention de licence
- **Free Trial :** Commencez avec un essai gratuit pour explorer l’API.  
- **Temporary License :** Obtenez une clé temporaire pour des tests illimités.  
- **Purchase :** Acquérez une licence complète pour les déploiements en production.

### Initialisation et configuration de base
Une fois la dépendance en place, créez un objet `Metadata` et pointez‑le vers votre fichier de présentation :

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## Comment java extraire les propriétés d’un document à partir d’une présentation
Ci‑dessous, nous parcourons les propriétés intégrées les plus courantes, en montrant exactement comment les lire.

### Extraction des informations d’auteur
**Aperçu :** Récupérer le nom de la personne qui a créé la présentation.

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*La méthode `getAuthor()` renvoie la chaîne de l’auteur ou `null` si le champ est vide.*

### Extraction de la date de création (read created time java)
**Aperçu :** Obtenir le horodatage qui indique quand le fichier a été créé pour la première fois.

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*`getCreatedTime()` fournit un objet `java.util.Date` représentant le moment de création — exactement ce à quoi fait référence « read created time java ». *

### Extraction des informations d’entreprise
**Aperçu :** Extraire le nom de l’organisation associé à la présentation.

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*La méthode `getCompany()` renvoie les métadonnées de l’entreprise ou `null` si elles ne sont pas définies.*

### Métadonnées supplémentaires que vous pouvez extraire
Vous pouvez de la même manière récupérer d’autres champs intégrés tels que **Category**, **Keywords**, **Last Printed Date** et **Application Name** en utilisant des méthodes comme `getCategory()`, `getKeywords()`, etc.

## Applications pratiques
1. **Document Management Systems :** Indexer les présentations par auteur, entreprise ou date de création pour une récupération rapide.  
2. **Compliance Auditing :** Vérifier que les métadonnées requises (par ex., le horodatage de création) sont présentes avant l’archivage.  
3. **Automated Reporting :** Générer des rapports récapitulatifs listant qui a créé chaque jeu de diapositives et quand.  
4. **CRM Integration :** Lier les présentations aux dossiers clients en utilisant le champ de métadonnées de l’entreprise.

## Considérations de performance
- **Parallel Processing :** Lors du traitement de gros lots, traitez les fichiers dans des threads séparés pour améliorer le débit.  
- **Resource Management :** Utilisez try‑with‑resources (comme montré) pour fermer automatiquement les flux et éviter les fuites de mémoire.  
- **Batch Extraction :** GroupDocs.Metadata prend en charge les opérations en masse ; envisagez de lire plusieurs fichiers dans une boucle unique pour plus d’efficacité.

## Problèmes courants et solutions
- **Missing Metadata :** Si une propriété renvoie `null`, le fichier source ne contient simplement pas cette information. Protégez‑vous contre les valeurs `null` comme démontré.  
- **Unsupported Format :** Assurez‑vous que le fichier est un format PowerPoint pris en charge (`.pptx`, `.ppt`).  
- **License Errors :** Vérifiez que votre fichier de licence est correctement placé ou que la période d’essai n’est pas expirée.

## Questions fréquemment posées

**Q : Comment gérer les propriétés de métadonnées manquantes ?**  
R : L’API renvoie `null` pour les champs non définis. Utilisez une expression conditionnelle comme `(author != null ? author : "N/A")` pour fournir une valeur de secours.

**Q : GroupDocs.Metadata peut‑il extraire des champs de métadonnées personnalisés ?**  
R : Oui, au‑delà des propriétés intégrées, vous pouvez lire et écrire des paires clé/valeur personnalisées en utilisant la même API.

**Q : Existe‑t‑il une prise en charge d’autres formats de présentation ?**  
R : GroupDocs.Metadata fonctionne avec PowerPoint (`.ppt`, `.pptx`) ainsi qu’avec PDF, Word et de nombreux formats d’image.

**Q : Quelles sont les exigences système pour GroupDocs.Metadata Java ?**  
R : Un JDK compatible (8 ou supérieur) et une mémoire heap suffisante pour la taille des documents que vous traitez.

**Q : Où puis‑je obtenir de l’aide en cas de problème ?**  
R : Consultez le forum officiel de support pour obtenir de l’aide : [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## Ressources

- **Documentation :** https://docs.groupdocs.com/metadata/java/  
- **Référence API :** https://reference.groupdocs.com/metadata/java/  
- **Téléchargement :** https://releases.groupdocs.com/metadata/java/  
- **GitHub :** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java  
- **Support gratuit :** https://forum.groupdocs.com/c/metadata/  
- **Licence temporaire :** https://purchase.groupdocs.com/temporary-license/

En suivant ce guide, vous savez maintenant comment **read created time java** et **java extract document properties** à partir de présentations PowerPoint en utilisant GroupDocs.Metadata. Intégrez ces extraits dans vos projets pour améliorer l’intelligence documentaire et rationaliser les flux de travail de conformité.

---

**Dernière mise à jour :** 2026-01-26  
**Testé avec :** GroupDocs.Metadata 24.12 for Java  
**Auteur :** GroupDocs