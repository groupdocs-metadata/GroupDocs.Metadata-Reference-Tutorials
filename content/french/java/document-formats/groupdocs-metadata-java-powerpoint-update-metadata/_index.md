---
date: '2026-05-27'
description: Apprenez comment définir le CreatedTime du PPTX en Java en utilisant
  la dépendance GroupDocs Maven pour mettre à jour les metadata PowerPoint, y compris
  comment modifier la date de création du PPTX.
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
title: Définir le CreatedTime du PPTX en Java avec la dépendance GroupDocs Maven
type: docs
url: /fr/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Définir le CreatedTime PPTX en Java avec GroupDocs.Metadata

Les métadonnées précises sont essentielles pour la conformité et la découvrabilité dans les flux de travail de documents modernes. Avec **GroupDocs.Metadata**, vous pouvez programmer **définir le CreatedTime PPTX en Java**, vous permettant de **modifier la date de création du PPTX** ainsi que d’autres propriétés intégrées telles que l’auteur ou l’entreprise. Ce tutoriel vous guide à travers la configuration Maven, l’initialisation de l’API, la mise à jour des métadonnées et l’enregistrement de la présentation modifiée — le tout avec du code clair, prêt pour la production.

## Réponses rapides
- **Quelle bibliothèque met à jour les métadonnées PowerPoint en Java ?** GroupDocs.Metadata via la dépendance Maven GroupDocs.  
- **Puis-je définir la propriété CreatedTime du PPTX ?** Oui — utilisez `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Une licence est‑elle requise pour la production ?** Un essai fonctionne pour l’évaluation ; une licence commerciale est obligatoire pour les déploiements en production.  
- **Quel outil de construction l’exemple utilise‑t‑il ?** Maven (vous pouvez également télécharger le JAR manuellement).  
- **L’API prend‑elle en charge Java 8 et versions ultérieures ?** Absolument — GroupDocs.Metadata cible Java 8+.

## Qu’est‑ce que la dépendance Maven GroupDocs ?
La **dépendance Maven GroupDocs** est une entrée de référentiel compatible Maven qui récupère la dernière bibliothèque GroupDocs.Metadata dans votre projet Java. Elle simplifie la gestion des dépendances en résolvant automatiquement les bibliothèques transitoires, garantit que vous utilisez toujours la version la plus récente et sécurisée, et élimine le besoin de téléchargements manuels de JAR ou de suivi de versions.

## Pourquoi utiliser GroupDocs.Metadata pour modifier la date de création PPTX ?
GroupDocs.Metadata permet des mises à jour automatisées et prêtes pour le traitement par lots des horodatages de création PPTX, garantissant que chaque présentation respecte les politiques d’entreprise ou les exigences légales. En définissant programmétiquement la propriété CreatedTime, vous évitez les modifications manuelles, réduisez les erreurs humaines et pouvez intégrer le changement dans les pipelines CI/CD ou les scripts de migration pour une gestion fluide des documents.

## Prérequis
- Java 8 ou version supérieure installé.  
- Un IDE tel qu’IntelliJ IDEA ou Eclipse.  
- Maven pour la gestion des dépendances.  
- Accès à un essai GroupDocs ou à une licence achetée.

## Comment définir le CreatedTime PPTX en Java ?
La classe `Metadata` représente un document et fournit l’accès à ses propriétés de métadonnées.

Chargez votre fichier PowerPoint avec `new Metadata("presentation.pptx")`, récupérez le package racine, appelez `setCreatedTime` avec le `java.util.Date` souhaité, puis invoquez `save` pour enregistrer les modifications. Ce flux de bout en bout modifie la date de création tout en préservant le contenu de toutes les diapositives et les autres propriétés.

### Configuration Maven
Ajoutez le référentiel GroupDocs et la dépendance metadata à votre `pom.xml` :

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

> **Astuce :** Garder le numéro de version à jour vous assure de bénéficier des dernières corrections de bugs et améliorations de performances.

### Téléchargement direct (si vous préférez ne pas utiliser Maven)
Sinon, téléchargez le JAR le plus récent depuis [GroupDocs.Metadata pour les versions Java](https://releases.groupdocs.com/metadata/java/).

#### Obtention de licence
Commencez avec un essai gratuit ou demandez une licence temporaire pour évaluer GroupDocs.Metadata. Pour une utilisation en production, achetez une licence via le [site officiel de GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Initialisation et configuration de base
Une fois la bibliothèque sur le classpath, vous pouvez créer une instance `Metadata` qui pointe vers votre fichier PowerPoint :

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

## Guide étape par étape pour mettre à jour les métadonnées intégrées

### Étape 1 : Charger le document de présentation
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```
Le chargement du fichier établit une connexion qui vous permet de lire ou d’écrire les métadonnées.

### Étape 2 : Accéder au package racine de la présentation
L’objet `root` donne accès au package principal de la présentation et à ses propriétés intégrées.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```
L’objet `root` expose toutes les propriétés intégrées du document.

### Étape 3 : Mettre à jour les propriétés intégrées du document (y compris la date de création)
`setCreatedTime` attribue un nouvel horodatage de création au document.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
Voici comment **définir le CreatedTime PPTX** en assignant un nouvel objet `Date` à `CreatedTime`. Remplacez `new Date()` par le timestamp spécifique dont vous avez besoin.

### Étape 4 : Enregistrer la présentation mise à jour
`save` écrit les métadonnées modifiées dans un fichier.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```
L’appel `save` écrit les métadonnées modifiées dans un nouveau fichier PowerPoint, laissant l’original intact.

## Conseils de dépannage
- **Fichier non trouvé :** Vérifiez à nouveau le chemin d’entrée et les permissions du fichier.  
- **Incompatibilité de version :** Assurez‑vous que la version `groupdocs-metadata` correspond à votre runtime Java.  
- **Propriété non mise à jour :** Vérifiez que vous appelez `setCreatedTime` (ou le setter correspondant) avant d’appeler `save`.

## Applications pratiques
1. **Image de marque d’entreprise :** Injectez automatiquement le nom et la catégorie de l’entreprise dans toutes les présentations avant la distribution.  
2. **Systèmes de gestion de documents :** Enrichissez les fichiers PPTX avec des métadonnées recherchables pour une récupération plus rapide.  
3. **Ressources éducatives :** Maintenez à jour les informations d’auteur et de programme dans les diapositives de cours.  
4. **Suivi de collaboration :** Enregistrez les noms des contributeurs pour maintenir la responsabilité.  
5. **Intégration CMS :** Synchronisez les changements de métadonnées avec votre plateforme de gestion de contenu en temps réel.

## Considérations de performance
- **Traitement par lots :** Parcourez une liste de fichiers et réutilisez une seule instance `Metadata` lorsque c’est possible.  
- **Gestion de la mémoire :** Utilisez toujours le try‑with‑resources (comme montré) pour libérer rapidement les ressources natives.  
- **Structures de données efficaces :** Stockez les mises à jour de métadonnées dans une map avant de les appliquer afin de réduire les appels répétitifs.

## Questions fréquentes

**Q : Quel est le but principal de la dépendance Maven GroupDocs ?**  
R : Elle offre un moyen pratique d’inclure la dernière bibliothèque GroupDocs.Metadata dans les projets Java basés sur Maven.

**Q : Comment puis‑je définir la date de création du PPTX sans affecter les autres propriétés ?**  
R : Utilisez `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` avant d’appeler `metadata.save()`.

**Q : Ai‑je besoin d’une licence pour exécuter ce code en développement ?**  
R : Une licence d’essai temporaire suffit pour le développement et les tests ; une licence complète est requise pour la production.

**Q : Puis‑je également mettre à jour des champs de métadonnées personnalisés ?**  
R : Oui — GroupDocs.Metadata prend en charge les propriétés intégrées et personnalisées via son API.

**Q : Existe‑t‑il un moyen d’annuler les modifications en cas d’erreur ?**  
R : Conservez une copie du fichier original ou lisez les valeurs de propriétés existantes avant de les écraser, puis restaurez-les si nécessaire.

## Ressources
- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [Référence API](https://apireference.groupdocs.com/metadata/java/)

---

**Dernière mise à jour :** 2026-05-27  
**Testé avec :** GroupDocs.Metadata 24.12 pour Java  
**Auteur :** GroupDocs  

## Tutoriels associés
- [Mettre à jour les métadonnées personnalisées dans PowerPoint avec l’API Java GroupDocs.Metadata](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Comment mettre à jour les métadonnées d’un document Word avec GroupDocs.Metadata Java : guide complet](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Mettre à jour efficacement les métadonnées PDF avec GroupDocs.Metadata en Java pour la gestion de documents](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)