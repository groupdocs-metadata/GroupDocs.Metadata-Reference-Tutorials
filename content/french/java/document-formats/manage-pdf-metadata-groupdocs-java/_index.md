---
date: '2026-02-14'
description: Apprenez à mettre à jour les métadonnées PDF et à détecter la version
  PDF en Java en utilisant GroupDocs.Metadata. Ce guide montre également comment lire
  les propriétés PDF avec Java.
keywords:
- manage PDF metadata
- GroupDocs.Metadata Java
- detect PDF version
title: Mettre à jour les métadonnées PDF en Java avec GroupDocs.Metadata
type: docs
url: /fr/java/document-formats/manage-pdf-metadata-groupdocs-java/
weight: 1
---

# Mettre à jour les métadonnées PDF en Java avec GroupDocs.Metadata

Gestionner les fichiers PDF de façon programmatique signifie souvent que vous devez **mettre à jour les métadonnées PDF** — auteur, titre, date de création, voire même la version du PDF elle‑même. Des métadonnées incohérentes peuvent entraîner des problèmes d’affichage ou rendre plus difficile la localisation des documents dans un grand référentiel. Ce tutoriel vous guide dans la détection de la version du PDF et la mise à jour des métadonnées PDF à l’aide de **GroupDocs.Metadata** pour Java, vous offrant une méthode fiable pour garder vos PDF propres et compatibles.

## Réponses rapides
- **Que signifie « mettre à jour les métadonnées PDF » ?** Ajouter, modifier ou supprimer les informations stockées à l’intérieur d’un fichier PDF.  
- **Quelle bibliothèque permet cela en Java ?** GroupDocs.Metadata.  
- **Puis‑je également détecter la version du PDF ?** Oui, la même API fournit la détection de version.  
- **Ai‑je besoin d’une licence ?** Un essai gratuit suffit pour l’évaluation ; une licence payante est requise pour la production.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.

## Qu’est‑ce que la mise à jour des métadonnées PDF ?

Mettre à jour les métadonnées PDF désigne la lecture et l’écriture programmatiques des informations descriptives intégrées dans un fichier PDF — telles que l’auteur, le titre, le sujet et les propriétés personnalisées. Des métadonnées appropriées améliorent la recherchabilité, la conformité et le contrôle de version dans les systèmes de gestion de documents.

## Pourquoi détecter la version du PDF en Java ?

Savoir la version du PDF (par ex., 1.4, 1.7) vous aide à garantir que le fichier s’affichera correctement dans le visualiseur cible ou qu’il répond aux exigences des pipelines de traitement en aval. Détecter la version est particulièrement utile lorsque vous devez appliquer des règles de compatibilité avant d’archiver ou de publier des documents.

## Prérequis

- **Java Development Kit (JDK)** 8 ou supérieur.  
- **Maven** pour la gestion des dépendances (ou vous pouvez télécharger le JAR directement).  
- Familiarité de base avec les I/O de fichiers Java.  

## Configuration de GroupDocs.Metadata pour Java

### Configuration Maven
Ajoutez le dépôt et la dépendance à votre `pom.xml` :

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
Sinon, téléchargez le JAR le plus récent depuis la page officielle de publication : [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Étapes d’obtention de licence
- **Essai gratuit** – commencez à expérimenter sans frais.  
- **Licence temporaire** – prolongez l’essai si nécessaire.  
- **Achat** – obtenez une licence complète pour une utilisation en production.

## Initialisation et configuration de base

Créez une instance `Metadata` qui pointe vers votre fichier PDF :

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PdfRootPackage;

public class PdfMetadataExample {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
            // Further operations will go here
        }
    }
}
```

Vous êtes maintenant prêt à lire les propriétés, détecter la version et mettre à jour les métadonnées.

## Détecter la version du PDF et lire les propriétés PDF en Java

### Étape 1 : Ouvrir le PDF avec un objet `Metadata`
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Access PDF‑specific properties here
}
```

### Étape 2 : Obtenir le package racine pour les détails spécifiques au PDF
```java
PdfRootPackage root = metadata.getRootPackageGeneric();
```

### Étape 3 : Extraire les informations de version et de format
```java
String fileFormat = root.getPdfType().getFileFormat();
String version = root.getPdfType().getVersion();
String mimeType = root.getPdfType().getMimeType();
String extension = root.getPdfType().getExtension();

System.out.println("File Format: " + fileFormat);
System.out.println("PDF Version: " + version);
System.out.println("MIME Type: " + mimeType);
System.out.println("Extension: " + extension);
```

**Astuce :** Utilisez la valeur `version` pour appliquer des vérifications de compatibilité avant de traiter un lot de PDF.

#### Dépannage
- Vérifiez le chemin du fichier ; un chemin incorrect déclenche `FileNotFoundException`.  
- Assurez‑vous que la version de GroupDocs.Metadata correspond à votre JDK (l’exemple utilise la version 24.12).

## Mettre à jour les métadonnées PDF en Java

### Étape 1 : Ouvrir le PDF (identique à ci‑dessus)
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pdf")) {
    // Modify or read metadata here
}
```

### Étape 2 : Accéder au package document‑info et modifier les champs
```java
PdfRootPackage root = metadata.getRootPackageGeneric();

// Example: read the current author
String author = root.getPdfDocumentInfo().getAuthor();
System.out.println("Author: " + author);

// To update a property, call the setter (omitted for brevity)
// e.g., root.getPdfDocumentInfo().setAuthor("New Author");
```

**Remarque :** Les appels aux setters sont simples ; ils suivent le même modèle que les getters présentés.

#### Pièges courants
- Tenter de modifier les métadonnées d’un PDF qui ne possède pas la propriété cible renvoie une valeur `null` — vérifiez toujours la présence de `null` avant d’affecter.  
- Les PDF volumineux peuvent nécessiter une augmentation du tas JVM ; surveillez l’utilisation de la mémoire lors des mises à jour par lots.

## Cas d’utilisation pratiques

1. **Audits de conformité** – Vérifiez que tous les PDF respectent une version minimale (par ex., 1.7) avant le dépôt légal.  
2. **Archivage automatisé** – Étiquetez les PDF avec l’auteur, le service et la date de création pour faciliter la récupération.  
3. **Intégration de gestion documentaire** – Enrichissez les PDF avec des propriétés personnalisées que les plateformes DMS peuvent indexer.  
4. **Génération de rapports** – Insérez les informations de version dans les rapports générés automatiquement.  
5. **Tests multiplateformes** – Détectez les incompatibilités de version pouvant entraîner des problèmes d’affichage sur des visionneuses plus anciennes.  

## Conseils de performance

- **Utilisez try‑with‑resources** (comme indiqué) pour fermer automatiquement les objets `Metadata`.  
- **Traitement par lots** de plusieurs fichiers dans une boucle pour réduire la surcharge.  
- **Surveillez le tas** pour les PDF très volumineux ; envisagez de les traiter par morceaux si vous atteignez les limites de mémoire.

## Questions fréquemment posées

**Q : Puis‑je mettre à jour les métadonnées sur des PDF protégés par mot de passe ?**  
R : Oui, mais vous devez fournir le mot de passe lors de la création de l’objet `Metadata`.

**Q : GroupDocs.Metadata prend‑il en charge les propriétés XMP personnalisées ?**  
R : Absolument. Vous pouvez lire et écrire des champs XMP personnalisés via la même API.

**Q : Est‑il possible de modifier la version du PDF elle‑même ?**  
R : La bibliothèque peut signaler la version ; la modifier nécessite d’enregistrer le document avec un profil de version différent, ce qui est pris en charge via des options d’enregistrement supplémentaires.

**Q : Que se passe‑t‑il si le PDF ne possède aucune métadonnée existante ?**  
R : Les getters renverront `null`. Vous pouvez appeler les setters en toute sécurité pour créer de nouvelles entrées de métadonnées.

**Q : Existe‑t‑il des restrictions de licence pour une utilisation commerciale ?**  
R : Une licence commerciale est requise pour les déploiements en production ; l’essai est limité à des fins d’évaluation.

---

**Dernière mise à jour :** 2026-02-14  
**Testé avec :** GroupDocs.Metadata 24.12 pour Java  
**Auteur :** GroupDocs