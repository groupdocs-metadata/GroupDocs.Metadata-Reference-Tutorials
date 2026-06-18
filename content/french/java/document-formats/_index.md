---
date: 2026-06-17
description: Apprenez comment convertir un document en image et extraire, lire ou
  supprimer les metadata PDF à l'aide de GroupDocs.Metadata pour Java, pour les formats
  PDF, Word, Excel, PowerPoint et plus encore.
keywords:
- convert document to image
- read pdf metadata java
- extract pdf metadata java
- remove pdf metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to convert document to image and extract, read, or remove
    PDF metadata using GroupDocs.Metadata for Java across PDF, Word, Excel, PowerPoint
    and more.
  headline: Convert Document to Image – GroupDocs.Metadata Java Tutorial
  type: TechArticle
- description: Learn how to convert document to image and extract, read, or remove
    PDF metadata using GroupDocs.Metadata for Java across PDF, Word, Excel, PowerPoint
    and more.
  name: Convert Document to Image – GroupDocs.Metadata Java Tutorial
  steps:
  - name: Set Up the Maven Dependency
    text: Add the GroupDocs.Metadata dependency to your `pom.xml`. This single line
      pulls in all required binaries.
  - name: Load the Source Document
    text: Create a `Document` object by passing the file path. This object represents
      the entire source file in memory.
  - name: (Optional) Read or Remove PDF Metadata
    text: If the source is a PDF, you can call `document.getMetadata().readAll()`
      to retrieve a map of metadata entries, or `document.getMetadata().clearAll()`
      to strip them before rendering.
  - name: Configure Image Options
    text: Set the output format (`ImageOptions.setImageFormat(ImageFormat.PNG)`) and
      optionally define DPI, page range, or background color.
  - name: Save Images to Disk
    text: Call `document.save("output_folder", imageOptions)`. The library creates
      one image per page, naming them sequentially (e.g., `page_1.png`, `page_2.png`).
  type: HowTo
- questions:
  - answer: No. The conversion creates separate image files; the source document remains
      unchanged unless you explicitly overwrite it.
    question: Does converting to image affect the original file size?
  - answer: Yes. Use `ImageOptions.setPageRange("1-5")` to render pages 1 through
      5 only.
    question: Can I convert only a subset of pages?
  - answer: The SDK renders raster images; for vector‑preserving output you would
      need a PDF‑to‑SVG converter, which is outside the scope of GroupDocs.Metadata.
    question: Is it possible to retain vector quality for PDFs?
  - answer: The library can handle documents with thousands of pages, limited only
      by available disk space and memory. It streams pages one‑by‑one to keep memory
      usage low.
    question: Are there limits on the number of pages I can convert?
  - answer: Purchase a commercial license from GroupDocs; a temporary license is available
      for evaluation and is automatically applied when you set the license file path
      in your code.
    question: How do I license the library for production?
  type: FAQPage
title: Convertir un document en image – Tutoriel Java GroupDocs.Metadata
type: docs
url: /fr/java/document-formats/
weight: 6
---

# Convertir un document en image – Tutoriel GroupDocs.Metadata Java

Dans ce guide complet, vous découvrirez **comment convertir un document en image** avec GroupDocs.Metadata pour Java tout en apprenant à lire les métadonnées PDF, extraire les métadonnées PDF et supprimer les métadonnées PDF lorsque cela est nécessaire. Nous parcourons le pourquoi, le quoi et le comment étape par étape, vous offrant une base solide pour créer des flux de travail basés sur les aperçus, des contrôles de conformité et des bibliothèques de documents consultables.

## Réponses rapides
- **Que signifie « convertir un document en image » ?** Cela signifie rendre chaque page d’un fichier source (PDF, DOCX, XLSX, PPTX, etc.) sous forme d’image raster telle que PNG ou JPEG.  
- **Pourquoi utiliser GroupDocs.Metadata pour les aperçus ?** Il rend les images sans nécessiter l’installation de Microsoft Office et vous permet de supprimer ou modifier les métadonnées dans le même pipeline.  
- **Puis‑je lire les métadonnées PDF dans le même appel ?** Oui — les métadonnées peuvent être lues avant ou après le rendu sans I/O supplémentaire.  
- **La suppression des métadonnées PDF est‑elle prise en charge ?** Absolument ; l’API fournit des méthodes pour effacer toutes les propriétés intégrées et personnalisées.  
- **Quels formats sont pris en charge pour la conversion d’image ?** Plus de 50 formats d’entrée, y compris PDF, DOCX, XLSX, PPTX et de nombreux types d’image.

## Qu’est‑ce que « convertir un document en image » ?
*Convert document to image* est le processus qui consiste à transformer chaque page d’un fichier numérique en une image bitmap (PNG, JPEG, BMP, etc.). Cela permet des galeries de vignettes, un rendu d’aperçu rapide dans les navigateurs et un indexage indépendant du contenu pour les moteurs de recherche, tout en préservant la fidélité visuelle et en autorisant la gestion des métadonnées en aval dans un seul flux de travail.

## Pourquoi convertir des documents en images avec GroupDocs.Metadata ?
GroupDocs.Metadata prend en charge **plus de 50 formats d’entrée et de sortie** et peut rendre des fichiers de plusieurs centaines de pages sans charger le document entier en mémoire, générant des aperçus à un taux de **jusqu’à 30 pages par seconde** sur un serveur typique de 2 GHz. La bibliothèque vous offre également un contrôle granulaire sur les métadonnées — vous permettant de les lire, extraire ou supprimer dans le même flux de travail, ce qui réduit les I/O et améliore la sécurité.

## Prérequis
- Java 17 ou version ultérieure installé sur votre machine de développement.  
- Une licence valide GroupDocs.Metadata pour Java (une licence temporaire suffit pour les tests).  
- Maven ou Gradle pour la gestion des dépendances.  
- Familiarité de base avec les IDE Java (IntelliJ IDEA, Eclipse, VS Code).

## Comment convertir un document en image avec GroupDocs.Metadata pour Java ?
La classe `Document` représente un fichier chargé et fournit l’accès à son contenu et à ses métadonnées. La classe `ImageOptions` configure les paramètres de rendu tels que le format, le DPI et la plage de pages. Chargez votre fichier source avec la classe `Document`, configurez les `ImageOptions`, puis appelez `save` pour générer les fichiers image. La conversion s’effectue en deux lignes de code, et vous pouvez éventuellement effacer les métadonnées avant l’enregistrement.

### Étape 1 : Configurer la dépendance Maven
Ajoutez la dépendance GroupDocs.Metadata à votre `pom.xml`. Cette ligne unique récupère tous les binaires requis.

### Étape 2 : Charger le document source
Créez un objet `Document` en passant le chemin du fichier. Cet objet représente le fichier source complet en mémoire.

### Étape 3 : (Facultatif) Lire ou supprimer les métadonnées PDF
Si la source est un PDF, vous pouvez appeler `document.getMetadata().readAll()` pour récupérer une carte des entrées de métadonnées, ou `document.getMetadata().clearAll()` pour les supprimer avant le rendu.

### Étape 4 : Configurer les options d’image
Définissez le format de sortie (`ImageOptions.setImageFormat(ImageFormat.PNG)`) et, éventuellement, le DPI, la plage de pages ou la couleur de fond.

### Étape 5 : Enregistrer les images sur le disque
Appelez `document.save("output_folder", imageOptions)`. La bibliothèque crée une image par page, les nommant séquentiellement (par ex., `page_1.png`, `page_2.png`).

## Comment lire les métadonnées PDF en Java ?
La classe `Document` représente un fichier chargé et fournit un accesseur `getMetadata()` pour les opérations sur les métadonnées. Créez une instance `Document` pour le PDF, appelez `document.getMetadata().readAll()`, puis parcourez la `Map<String, Object>` retournée pour accéder à chaque paire clé‑valeur de métadonnées. La méthode renvoie les propriétés intégrées et personnalisées en un seul appel, éliminant le besoin de parseurs séparés.

## Comment extraire les métadonnées PDF en Java ?
`readAll()` renvoie une carte de toutes les propriétés de métadonnées intégrées et personnalisées. Après avoir invoqué `document.getMetadata().readAll()`, transmettez la carte résultante à un sérialiseur tel que Jackson (`ObjectMapper.writeValueAsString(map)`) pour produire une chaîne JSON, ou utilisez `MetadataExporter` fourni par le SDK pour écrire directement en CSV ou XML.

## Comment supprimer les métadonnées PDF en Java ?
`clearAll()` supprime chaque entrée de métadonnées du document. Appelez `document.getMetadata().clearAll()` pour effacer toutes les métadonnées, puis enregistrez le PDF avec `document.save("cleaned.pdf")`. Cette opération réécrit le fichier sans aucune des métadonnées d’origine, garantissant la conformité en matière de confidentialité.

## Cas d’utilisation courants
- **Document Management Systems (DMS) :** Générer des aperçus de vignettes pour chaque fichier téléchargé et stocker les métadonnées extraites dans un index consultable.  
- **Compliance Audits :** Lire et consigner automatiquement les métadonnées PDF avant l’archivage afin de vérifier que les champs requis sont présents.  
- **Secure Sharing :** Supprimer toutes les métadonnées des PDF, puis rendre des aperçus image pour les partager avec des partenaires externes sans exposer d’informations internes.  
- **Bulk Migration :** Convertir les documents Office hérités en images tout en extrayant les métadonnées pour les importer dans un nouveau référentiel de contenu.

## Conseils de dépannage
- **Blank Images :** Assurez‑vous que le fichier source n’est pas protégé par mot de passe ; fournissez le mot de passe via `Document.load(path, password)`.  
- **Missing Metadata :** Certains PDF peuvent utiliser des flux XMP ; utilisez `document.getMetadata().readAllXmp()` si les propriétés standard sont vides.  
- **Performance Bottlenecks :** Pour de gros lots, réutilisez une seule instance `Document` par thread et définissez `ImageOptions.setDpi(150)` pour équilibrer qualité et vitesse.  
- **Unsupported Formats :** Vérifiez que l’extension du fichier figure dans le tableau des formats pris en charge par le SDK (plus de 50 formats).  

## Foire aux questions

**Q : La conversion en image affecte‑t‑elle la taille du fichier original ?**  
R : Non. La conversion crée des fichiers image séparés ; le document source reste inchangé sauf si vous le remplacez explicitement.

**Q : Puis‑je convertir uniquement un sous‑ensemble de pages ?**  
R : Oui. Utilisez `ImageOptions.setPageRange("1-5")` pour rendre uniquement les pages 1 à 5.

**Q : Est‑il possible de conserver la qualité vectorielle pour les PDF ?**  
R : Le SDK rend des images raster ; pour une sortie vectorielle vous auriez besoin d’un convertisseur PDF‑to‑SVG, ce qui dépasse le cadre de GroupDocs.Metadata.

**Q : Existe‑t‑il des limites au nombre de pages que je peux convertir ?**  
R : La bibliothèque peut gérer des documents contenant des milliers de pages, limitée uniquement par l’espace disque et la mémoire disponibles. Elle diffuse les pages une par une pour maintenir une faible consommation de mémoire.

**Q : Comment licencier la bibliothèque pour la production ?**  
R : Achetez une licence commerciale auprès de GroupDocs ; une licence temporaire est disponible pour l’évaluation et est appliquée automatiquement lorsque vous indiquez le chemin du fichier de licence dans votre code.

## Ressources supplémentaires

- [Documentation GroupDocs.Metadata pour Java](https://docs.groupdocs.com/metadata/java/)
- [Référence API GroupDocs.Metadata pour Java](https://reference.groupdocs.com/metadata/java/)
- [Télécharger GroupDocs.Metadata pour Java](https://releases.groupdocs.com/metadata/java/)
- [Forum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata)
- [Support gratuit](https://forum.groupdocs.com/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)

### Tutoriels disponibles

#### [Accéder aux métadonnées d’un document Word avec GroupDocs en Java : Guide complet](./access-word-metadata-groupdocs-java/)
#### [Créer des aperçus d’images de documents en Java avec GroupDocs.Metadata : Guide complet](./java-groupdocs-metadata-document-image-previews/)
#### [Détecter et identifier les types de feuilles de calcul avec GroupDocs.Metadata pour Java](./detect-spreadsheet-types-groupdocs-metadata-java/)
#### [Mettre à jour efficacement les métadonnées PDF avec GroupDocs.Metadata en Java pour la gestion de documents](./update-pdf-metadata-groupdocs-metadata-java/)
#### [Exporter les métadonnées de documents avec GroupDocs.Metadata en Java : Guide étape par étape](./export-document-metadata-groupdocs-metadata-java/)
#### [Extraire les signatures numériques des polices OpenType en Java : Guide complet avec GroupDocs.Metadata](./extract-digital-signatures-opentype-fonts-java/)
#### [Extraire les métadonnées de présentations avec GroupDocs.Metadata pour Java : Guide étape par étape](./extract-metadata-presentation-groupdocs-metadata-java/)
#### [Extraire les métadonnées d’un document Word avec Java : Guide complet avec GroupDocs.Metadata pour Java](./extract-word-metadata-groupdocs-java/)
#### [Extraire les propriétés d’un document Word avec GroupDocs.Metadata en Java](./groupdocs-metadata-java-word-properties-extraction/)
#### [Extraire les statistiques d’un document Word avec GroupDocs.Metadata Java : Guide étape par étape](./extract-word-statistics-groupdocs-metadata-java/)
#### [Extraire et gérer les métadonnées de feuilles de calcul en Java avec GroupDocs.Metadata](./extract-manage-spreadsheet-metadata-groupdocs-java/)
#### [Comment extraire les métadonnées personnalisées des PDF avec GroupDocs.Metadata en Java : Guide complet](./extract-custom-metadata-groupdocs-metadata-java/)
#### [Comment extraire les métadonnées PDF en Java avec la bibliothèque GroupDocs.Metadata](./extract-pdf-metadata-java-groupdocs/)
#### [Comment extraire les statistiques de présentations avec GroupDocs.Metadata pour Java](./groupdocs-metadata-java-extract-presentation-statistics/)
#### [Comment inspecter et gérer les commentaires de feuilles de calcul avec GroupDocs.Metadata en Java](./inspect-spreadsheet-comments-groupdocs-metadata-java/)
#### [Comment supprimer les annotations des PDF avec GroupDocs.Metadata en Java](./remove-annotations-pdf-groupdocs-metadata-java/)
#### [Comment mettre à jour les propriétés d’inspection dans les documents Word avec GroupDocs.Metadata pour Java](./update-word-document-inspection-properties-groupdocs-metadata-java/)
#### [Comment mettre à jour les métadonnées des feuilles de calcul avec GroupDocs.Metadata en Java](./update-spreadsheet-metadata-groupdocs-java/)
#### [Comment mettre à jour les métadonnées d’un document Word avec l’API Java de GroupDocs.Metadata](./update-word-metadata-groupdocs-java-api/)
#### [Comment mettre à jour les métadonnées d’un document Word avec GroupDocs.Metadata Java : Guide complet](./update-word-metadata-groupdocs-java/)
#### [Inspecter les commentaires de présentation et les diapositives cachées avec l’API Java de GroupDocs.Metadata](./groupdocs-metadata-java-inspect-comments-hidden-slides/)
#### [Gestion des métadonnées Java avec GroupDocs : Suppression des commentaires et diapositives cachées des présentations PowerPoint](./java-metadata-management-groupdocs-clear-comments-slides/)
#### [Guide d’extraction des statistiques PDF en Java avec GroupDocs.Metadata](./java-pdf-stats-groupdocs-metadata-developer-guide/)
#### [Gérer les métadonnées PDF et détecter la version avec GroupDocs.Metadata en Java](./manage-pdf-metadata-groupdocs-java/)
#### [Maîtriser la gestion des métadonnées de documents en Java avec GroupDocs.Metadata](./master-document-metadata-java-groupdocs/)
#### [Maîtriser l’inspection PDF en Java avec GroupDocs.Metadata : Annotations, pièces jointes, et plus](./groupdocs-metadata-java-pdf-inspection/)
#### [Maîtriser la gestion des métadonnées PDF avec GroupDocs.Metadata pour Java : Guide du développeur](./master-pdf-metadata-groupdocs-java/)
#### [Maîtriser la gestion des métadonnées de feuilles de calcul en Java : Suppression des commentaires et signatures numériques avec GroupDocs](./master-spreadsheet-metadata-groupdocs-remove-comments-signatures/)
#### [Mettre à jour les métadonnées personnalisées dans PowerPoint avec l’API Java de GroupDocs.Metadata](./update-custom-metadata-ppt-groupdocs-java/)
#### [Mettre à jour les métadonnées PDF en Java avec GroupDocs : Guide complet](./java-pdf-metadata-update-groupdocs-guide/)
#### [Mettre à jour les métadonnées PowerPoint avec la bibliothèque Java GroupDocs.Metadata](./groupdocs-metadata-java-powerpoint-update-metadata/)
#### [Mettre à jour les statistiques des documents Word avec GroupDocs.Metadata pour Java : Guide complet](./update-word-document-statistics-groupdocs-metadata-java/)

**Dernière mise à jour :** 2026-06-17  
**Testé avec :** GroupDocs.Metadata 23.12 pour Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment extraire les métadonnées PDF en Java avec la bibliothèque GroupDocs.Metadata](/metadata/java/document-formats/extract-pdf-metadata-java-groupdocs/)
- [Mettre à jour efficacement les métadonnées PDF avec GroupDocs.Metadata en Java pour la gestion de documents](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Comment extraire les blocs de ressources d’image d’un JPEG avec GroupDocs.Metadata pour Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)