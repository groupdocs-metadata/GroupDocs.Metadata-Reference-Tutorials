---
date: '2026-06-27'
description: Apprenez comment obtenir le timestamp de création de fichier et extraire
  d'autres propriétés de document à partir de présentations PowerPoint avec GroupDocs.Metadata
  pour Java. Idéal pour la gestion de documents et la conformité.
keywords:
- java get file creation timestamp
- java extract document properties
- GroupDocs.Metadata
schemas:
- author: GroupDocs
  dateModified: '2026-06-27'
  description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  headline: How to java get file creation timestamp from Presentation Files Using
    GroupDocs.Metadata
  type: TechArticle
- description: Learn how to java get file creation timestamp and extract other document
    properties from PowerPoint presentations with GroupDocs.Metadata for Java. Ideal
    for document management and compliance.
  name: How to java get file creation timestamp from Presentation Files Using GroupDocs.Metadata
  steps:
  - name: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
    text: '**Document Management Systems:** Index presentations by author, company,
      or creation date for rapid search and retrieval.'
  - name: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
    text: '**Compliance Auditing:** Ensure every archived slide deck includes a creation
      timestamp before it is stored for legal retention.'
  - name: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
    text: '**Automated Reporting:** Generate daily summaries that list who created
      each deck and when, feeding the data into BI dashboards.'
  - name: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
    text: '**CRM Integration:** Match the `Company` metadata to existing client records,
      enabling seamless attachment of presentations to customer profiles.'
  type: HowTo
- questions:
  - answer: 'The API returns `null` for unset fields. Use a conditional expression
      like `(author != null ? author : "N/A")` to provide a fallback value.'
    question: How do I handle missing metadata properties?
  - answer: Yes, beyond the built‑in properties you can read and write custom key/value
      pairs using the same API.
    question: Can GroupDocs.Metadata extract custom metadata fields?
  - answer: GroupDocs.Metadata works with PowerPoint (`.ppt`, `.pptx`) and also supports
      PDF, Word, Excel, and many image formats.
    question: Is there support for other presentation formats?
  - answer: A compatible JDK (8 or higher) and sufficient heap memory for the size
      of the documents you process (e.g., 1 GB heap for 500‑page presentations).
    question: What are the system requirements for GroupDocs.Metadata Java?
  - answer: 'Visit the official support forum for assistance: [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)'
    question: Where can I get help if I run into problems?
  type: FAQPage
title: Comment obtenir le timestamp de création de fichier à partir de fichiers de
  présentation avec GroupDocs.Metadata en Java
type: docs
url: /fr/java/document-formats/extract-metadata-presentation-groupdocs-metadata-java/
weight: 1
---

# Comment obtenir le timestamp de création de fichier Java à partir de fichiers de présentation avec GroupDocs.Metadata

Gestion des métadonnées est une pierre angulaire des flux de travail de documents modernes, et **java get file creation timestamp** est souvent la première information dont vous avez besoin pour vérifier la provenance d’un fichier. Dans ce guide étape par étape, vous découvrirez comment lire le timestamp de création d’une présentation PowerPoint, extraire des propriétés supplémentaires telles que l’auteur, l’entreprise et les mots‑clés, et intégrer les résultats dans n’importe quelle solution basée sur Java — qu’il s’agisse d’un système de gestion de documents, d’un générateur de piste d’audit ou d’un tableau de bord de conformité.

## Réponses rapides
- **What does “java get file creation timestamp” mean?** Cela signifie récupérer la date de création originale d’un fichier en utilisant du code Java via les API de métadonnées.  
- **Which library handles this?** GroupDocs.Metadata for Java fournit une API propre et indépendante du format pour lire les timestamps et d’autres propriétés intégrées.  
- **Do I need a license for production?** Oui — une licence permanente est requise pour la production ; un essai gratuit suffit pour le développement et les tests.  
- **Can I extract other metadata at once?** Absolument — l’auteur, l’entreprise, la catégorie, les mots‑clés et les champs personnalisés sont tous accessibles via la même API.  
- **What Java version is supported?** JDK 8 ou supérieur (compatible avec Java 11, 17 et versions ultérieures).

## Qu’est‑ce que “java get file creation timestamp” ?
`java get file creation timestamp` désigne l’opération d’accès au champ de métadonnées **Created** stocké dans un document, qui enregistre le moment exact où le fichier a été créé pour la première fois. Ce timestamp est crucial pour le contrôle de version, les pistes d’audit et la conformité réglementaire car il fournit un enregistrement immuable du moment où le contenu a été généré.

## Pourquoi utiliser GroupDocs.Metadata pour Java afin d’extraire les propriétés du document ?
GroupDocs.Metadata abstrait l’analyse de bas niveau de dizaines de formats de fichiers, vous permettant de vous concentrer sur la logique métier. Il prend en charge **plus de 50 formats d’entrée et de sortie** — y compris .pptx, .ppt, .pdf, .docx, .xlsx, et de nombreux types d’images — et peut traiter des présentations de plusieurs centaines de pages sans charger le fichier complet en mémoire, offrant une solution efficace en mémoire pour les environnements à grande échelle.

## Prérequis
- **GroupDocs.Metadata for Java** version 24.12 ou ultérieure.  
- Java Development Kit (JDK 8 ou plus récent).  
- Un IDE tel qu’IntelliJ IDEA ou Eclipse.  
- Une connaissance de base de l’I/O de fichiers Java et de la gestion des exceptions.

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
- **Free Trial:** Commencez avec un essai gratuit pour explorer l’API.  
- **Temporary License:** Obtenez une clé temporaire pour des tests sans restriction.  
- **Purchase:** Procurez-vous une licence complète pour les déploiements en production.

### Initialisation et configuration de base
`Metadata` est la classe principale d’entrée dans GroupDocs.Metadata pour Java qui fournit l’accès aux métadonnées d’un document. Une fois la dépendance en place, créez un objet `Metadata` et pointez‑le vers votre fichier de présentation :

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PresentationRootPackage;

String INPUT_DOCUMENT_PATH = "YOUR_DOCUMENT_DIRECTORY"; // Set your path here

try (Metadata metadata = new Metadata(INPUT_DOCUMENT_PATH)) {
    PresentationRootPackage root = metadata.getRootPackageGeneric();
    // Your code to extract metadata goes here
}
```

## Comment obtenir le timestamp de création de fichier Java et extraire d’autres propriétés d’une présentation ?
Chargez la présentation avec `new Metadata("sample.pptx")`, puis appelez les méthodes getter appropriées — `getCreatedTime()`, `getAuthor()`, `getCompany()`, etc. — pour récupérer chaque information. Cette approche à objet unique vous permet d’extraire toutes les propriétés intégrées en quelques lignes de code, éliminant ainsi le besoin de parseurs spécifiques à chaque format.

### Extraction des informations d’auteur
`getAuthor()` renvoie le nom de l’auteur stocké dans les métadonnées du document, ou `null` si le champ est vide.

```java
String author = root.getDocumentProperties().getAuthor();
System.out.println("Author: " + (author != null ? author : "N/A"));
```

*La méthode renvoie une `String` simple que vous pouvez consigner, afficher ou stocker dans une base de données.*

### Extraction du temps de création (java get file creation timestamp)
`getCreatedTime()` fournit un objet `java.util.Date` représentant le moment exact où le fichier a été créé pour la première fois — exactement ce que décrit “java get file creation timestamp”.

```java
Date createdTime = root.getDocumentProperties().getCreatedTime();
System.out.println("Created Time: " + (createdTime != null ? createdTime.toString() : "N/A"));
```

*Vous pouvez formater cette `Date` avec `SimpleDateFormat` ou la nouvelle API `java.time` pour l’affichage ou la comparaison.*

### Extraction des informations d’entreprise
`getCompany()` renvoie le nom de l’organisation associée à la présentation, ou `null` si le champ n’est pas défini.

```java
String company = root.getDocumentProperties().getCompany();
System.out.println("Company: " + (company != null ? company : "N/A"));
```

*Cette valeur est utile pour lier les documents aux dossiers d’entreprise ou aux entités CRM.*

### Métadonnées supplémentaires que vous pouvez extraire
Vous pouvez de la même façon récupérer d’autres champs intégrés tels que **Category**, **Keywords**, **Last Printed Date** et **Application Name** en utilisant des méthodes comme `getCategory()`, `getKeywords()`, etc. Chaque getter suit le même modèle : une valeur de retour concise et sûre contre les null, prête à l’emploi immédiat.

## Applications pratiques
1. **Document Management Systems:** Indexez les présentations par auteur, entreprise ou date de création pour une recherche et une récupération rapides.  
2. **Compliance Auditing:** Assurez‑vous que chaque diaporama archivé inclut un timestamp de création avant d’être stocké pour la conservation légale.  
3. **Automated Reporting:** Générez des résumés quotidiens listant qui a créé chaque diaporama et quand, en alimentant les données dans des tableaux de bord BI.  
4. **CRM Integration:** Faites correspondre les métadonnées `Company` aux enregistrements clients existants, permettant une attache fluide des présentations aux profils clients.

## Considérations de performance
- **Parallel Processing:** Lors de l’extraction de métadonnées de milliers de fichiers, exécutez chaque extraction dans son propre thread ou utilisez un pool de threads pour maximiser l’utilisation du CPU.  
- **Resource Management:** Utilisez try‑with‑resources (comme montré) pour fermer automatiquement l’objet `Metadata` et libérer les ressources natives.  
- **Batch Extraction:** GroupDocs.Metadata prend en charge les opérations en lot ; itérez sur une collection de chemins de fichiers et réutilisez une seule instance `Metadata` lorsque cela est possible afin de réduire la surcharge.

## Problèmes courants et solutions
- **Missing Metadata:** Si un getter renvoie `null`, le fichier source ne possède tout simplement pas cette propriété. Protégez‑vous contre les valeurs `null` avec des vérifications conditionnelles ou des valeurs par défaut.  
- **Unsupported Format:** Vérifiez que le fichier est un format PowerPoint pris en charge (`.pptx` ou `.ppt`). Tenter de charger un type non pris en charge génère une `UnsupportedFormatException`.  
- **License Errors:** Assurez‑vous que votre fichier de licence est correctement placé sur le classpath ou que la période d’essai n’est pas expirée ; sinon l’API lèvera une `LicenseException`.

## Questions fréquentes

**Q: Comment gérer les propriétés de métadonnées manquantes ?**  
A: L’API renvoie `null` pour les champs non définis. Utilisez une expression conditionnelle comme `(author != null ? author : "N/A")` pour fournir une valeur de secours.

**Q: GroupDocs.Metadata peut‑il extraire des champs de métadonnées personnalisés ?**  
A: Oui, au-delà des propriétés intégrées, vous pouvez lire et écrire des paires clé/valeur personnalisées en utilisant la même API.

**Q: Existe‑t‑il une prise en charge d’autres formats de présentation ?**  
A: GroupDocs.Metadata fonctionne avec PowerPoint (`.ppt`, `.pptx`) et prend également en charge PDF, Word, Excel et de nombreux formats d’image.

**Q: Quelles sont les exigences système pour GroupDocs.Metadata Java ?**  
A: Un JDK compatible (8 ou supérieur) et une mémoire heap suffisante pour la taille des documents que vous traitez (par exemple, 1 Go de heap pour des présentations de 500 pages).

**Q: Où puis‑je obtenir de l’aide en cas de problème ?**  
A: Visitez le forum de support officiel pour obtenir de l’aide : [GroupDocs Support Forum](https://forum.groupdocs.com/c/metadata/)

## Ressources

- **Documentation:** https://docs.groupdocs.com/metadata/java/
- **Référence API:** https://reference.groupdocs.com/metadata/java/
- **Téléchargement:** https://releases.groupdocs.com/metadata/java/
- **GitHub:** https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
- **Support gratuit:** https://forum.groupdocs.com/c/metadata/
- **Licence temporaire:** https://purchase.groupdocs.com/temporary-license/

En suivant ce guide, vous savez maintenant comment **java get file creation timestamp** et **java extract document properties** à partir de présentations PowerPoint en utilisant GroupDocs.Metadata. Intégrez ces extraits dans vos projets pour améliorer l’intelligence documentaire, rationaliser les flux de travail de conformité et renforcer les analyses en aval.

---

**Dernière mise à jour :** 2026-06-27  
**Testé avec :** GroupDocs.Metadata 24.12 for Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment extraire les métadonnées des présentations PowerPoint en utilisant GroupDocs.Metadata en Java](/metadata/java/working-with-metadata/extract-presentation-metadata-groupdocs-java/)
- [Automatiser les mises à jour de métadonnées Java par date en utilisant GroupDocs.Metadata pour une gestion efficace des fichiers](/metadata/java/working-with-metadata/java-metadata-update-by-date-groupdocs/)
- [Maîtriser la gestion des métadonnées : détecter les propriétés du document et le statut de chiffrement avec GroupDocs.Metadata pour Java](/metadata/java/working-with-metadata/master-metadata-management-groupdocs-java/)