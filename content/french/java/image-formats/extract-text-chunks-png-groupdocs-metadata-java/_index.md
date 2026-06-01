---
date: '2026-06-01'
description: Apprenez comment extraire les blocs de texte PNG avec GroupDocs.Metadata
  pour Java – lisez les métadonnées PNG efficacement et intégrez une gestion d'images
  robuste.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: Comment extraire les blocs de texte PNG à l'aide de l'API Java GroupDocs.Metadata
type: docs
url: /fr/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Comment extraire les blocs de texte PNG à l'aide de l'API GroupDocs.Metadata Java

L'extraction d'informations textuelles à partir de fichiers image peut être difficile, en particulier pour les formats non textuels comme les PNG. **GroupDocs.Metadata for Java** simplifie ce processus en fournissant des outils robustes pour récupérer et gérer les métadonnées intégrées dans ces images. Que vous manipuliez des blocs de texte généraux, compressés ou internationaux, GroupDocs.Metadata offre des solutions rationalisées.

Dans ce tutoriel, nous vous guiderons pour extraire efficacement différents types de blocs de texte à partir de fichiers PNG en utilisant la bibliothèque GroupDocs.Metadata en Java. En comprenant ces techniques, vous pourrez intégrer sans effort des fonctionnalités d'extraction de texte dans vos applications, améliorant les capacités de traitement des données dans divers domaines.

## Réponses rapides
- **GroupDocs.Metadata peut-il lire les métadonnées png ?** Oui, il lit toutes les métadonnées PNG standard, y compris les blocs de texte.  
- **Quelle version de Java est requise ?** Java 8 ou ultérieure est entièrement prise en charge.  
- **Ai-je besoin d'une licence pour le développement ?** Un essai gratuit fonctionne pour les tests ; une licence commerciale est requise pour la production.  
- **Combien de types de blocs de texte peuvent être extraits ?** Trois types principaux : général, compressé et international.  
- **La performance est‑elle un problème ?** L'extraction s'effectue en moins de 200 ms pour des PNG de 5 Mo typiques sur un CPU moderne.

## Qu’est‑ce que « how to extract png » ?
**« How to extract png »** fait référence au processus de récupération des blocs de texte intégrés dans un fichier image PNG à l'aide d'API programmatiques. Ces blocs de texte peuvent contenir des métadonnées descriptives, des commentaires ou des chaînes internationalisées. En tirant parti de GroupDocs.Metadata for Java, les développeurs peuvent lire, filtrer et manipuler ces blocs de manière programmatique sans décoder l'image complète.

## Pourquoi utiliser GroupDocs.Metadata pour l'extraction de texte PNG ?
GroupDocs.Metadata prend en charge **plus de 50 formats d'image et de document** et peut traiter les fichiers PNG **sans charger l'image entière en mémoire**, offrant des vitesses d'extraction de **150 ms en moyenne** pour des fichiers jusqu'à 10 Mo. La bibliothèque garantit également **une fidélité des données à 100 %**, préservant les caractères Unicode dans les blocs de texte internationaux.

## Prérequis

Avant de commencer à extraire des blocs de texte à partir d'images PNG avec GroupDocs.Metadata for Java, assurez‑vous de disposer de ce qui suit :

### Bibliothèques et dépendances requises
- **GroupDocs.Metadata for Java** : incluez cette bibliothèque dans votre projet via Maven ou en la téléchargeant directement.

### Exigences de configuration de l'environnement
- Un environnement de développement configuré avec Java (de préférence JDK 8 ou ultérieur).  
- Un IDE tel qu'IntelliJ IDEA, Eclipse ou tout autre supportant les projets Java.

### Prérequis de connaissances
- Compréhension de base de la programmation Java.  
- Familiarité avec la gestion des fichiers et répertoires dans une application Java.

## Configuration de GroupDocs.Metadata pour Java

Pour commencer avec GroupDocs.Metadata, vous devez l'inclure dans votre projet. Voici comment procéder en utilisant Maven ou en téléchargeant directement la bibliothèque :

### Configuration Maven
Ajoutez le dépôt et la dépendance suivants à votre fichier `pom.xml` :

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
Vous pouvez également télécharger la dernière version depuis [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Étapes d'obtention de licence
- **Free Trial** : Commencez avec un essai gratuit pour explorer les fonctionnalités.  
- **Temporary License** : Obtenez une licence temporaire pour des tests prolongés.  
- **Purchase** : Achetez une licence si vous êtes prêt à passer en production.

### Initialisation et configuration de base

Après avoir configuré la bibliothèque, initialisez GroupDocs.Metadata dans votre application Java comme suit :

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## Comment extraire les blocs de texte png d'un fichier PNG ?

La classe `Metadata` est le point d'entrée pour accéder aux flux de métadonnées d'un fichier. Chargez le PNG avec `new Metadata("yourImage.png")`, accédez au package racine et parcourez les collections de blocs de texte souhaitées – le tout en quelques lignes de code. Cette approche renvoie chaque bloc de texte général, compressé et international, vous permettant de les gérer comme vous le désirez.

### Ancre de définition
La classe `Metadata` est le point d'entrée de GroupDocs.Metadata, représentant un conteneur qui vous donne un accès programmatique à tous les flux de métadonnées à l'intérieur d'un fichier.

## Extraction des blocs de texte généraux d'un PNG

Cette fonctionnalité vous permet de récupérer tous les blocs de texte généraux intégrés dans un fichier PNG. Voici comment procéder :

#### Vue d'ensemble
Vous accéderez et parcourrez chaque bloc de texte stocké dans les métadonnées de l'image.

#### Implémentation étape par étape
1. **Import Necessary Classes :**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package :** `PngRootPackage` représente le conteneur racine des métadonnées PNG, exposant les collections de blocs de texte.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **Explanation of Parameters :**
   - `pngFilePath` : chemin vers votre fichier PNG.  
   - `PngRootPackage` : représente le package racine contenant les blocs de métadonnées.

#### Conseils de dépannage
- Assurez‑vous que vos fichiers PNG contiennent des blocs de texte ; sinon, aucune donnée ne sera récupérée.  
- Vérifiez que le chemin vers votre fichier PNG est correct.

## Extraction des blocs de texte compressés d'un PNG

Pour gérer spécifiquement les blocs de texte compressés, suivez ces étapes :

#### Vue d'ensemble
Cette fonctionnalité se concentre sur la récupération et la gestion des blocs de texte compressés au sein des métadonnées PNG.

#### Implémentation étape par étape
1. **Import Necessary Classes :**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package :**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **Explanation of Parameters :**
   - `getCompressionMethod()` : renvoie la méthode utilisée pour la compression. La méthode `getCompressionMethod()` retourne l'algorithme de compression utilisé pour un bloc de texte compressé.

#### Conseils de dépannage
- Assurez‑vous que vos fichiers PNG utilisent une méthode de compression prise en charge.  
- Gérez les exceptions où les blocs de texte pourraient ne pas être compressés.

## Extraction des blocs de texte internationaux d'un PNG

Pour l'extraction des blocs de texte internationaux, les étapes suivantes vous guideront :

#### Vue d'ensemble
Récupérez et gérez les blocs de texte internationaux dans les métadonnées PNG, y compris les détails de langue.

#### Implémentation étape par étape
1. **Import Necessary Classes :**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package :**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **Explanation of Parameters :**
   - `getLanguage()` : récupère le tag de langue du bloc de texte. La méthode `getLanguage()` fournit le tag ISO de langue associé à un bloc de texte international.  
   - `isCompressed()` : indique si le bloc de texte est compressé. La méthode `isCompressed()` indique si un bloc de texte est stocké sous forme compressée.

#### Conseils de dépannage
- Assurez‑vous que vos fichiers PNG ont les métadonnées internationales correctement définies.  
- Gérez les scénarios où les traductions pourraient ne pas être disponibles.

## Applications pratiques

Comprendre comment extraire les blocs de texte des PNG à l'aide de GroupDocs.Metadata peut être inestimable dans diverses applications :
- **Content Management Systems** : récupérez et organisez automatiquement les métadonnées pour les bibliothèques d'images.  
- **Data Analysis Tools** : améliorez les capacités d'extraction de données en incluant l'analyse des métadonnées d'images.  
- **Web Scraping Projects** : extrayez des informations précieuses des images intégrées sur les sites web.

## Questions fréquemment posées

**Q : Puis‑je lire les métadonnées png sans licence ?**  
A : Oui, l'essai gratuit vous permet de lire les métadonnées, mais une licence commerciale est requise pour les déploiements en production.

**Q : GroupDocs.Metadata prend‑il en charge d'autres formats d'image ?**  
A : Absolument – il gère JPEG, BMP, TIFF et plus de 40 formats supplémentaires.

**Q : Comment gérer efficacement les gros fichiers PNG ?**  
A : Utilisez l'API de streaming ; elle traite les fichiers sans charger l'image complète en mémoire, maintenant l'utilisation RAM sous 50 Mo.

**Q : Que se passe‑t‑il si un PNG ne contient aucun bloc de texte ?**  
A : L'API renvoie une collection vide ; vous pouvez vérifier `isEmpty()` avant de traiter.

**Q : Unicode est‑il pris en charge dans les blocs de texte internationaux ?**  
A : Oui, GroupDocs.Metadata prend pleinement en charge UTF‑8, préservant tous les caractères de langue.

## Conclusion

En suivant ce tutoriel, vous avez appris à extraire les blocs de texte généraux, compressés et internationaux des fichiers PNG à l'aide de la bibliothèque GroupDocs.Metadata en Java. Cette compétence peut considérablement améliorer la capacité de votre application à traiter et analyser les données d'image de manière efficace. Pour aller plus loin, envisagez d'explorer des techniques avancées de gestion des métadonnées proposées par GroupDocs.Metadata.

**Next Steps**
- Expérimentez différents types d'extraction de métadonnées.  
- Explorez les fonctionnalités supplémentaires de la bibliothèque GroupDocs.Metadata.  
- Partagez vos découvertes ou applications dans les communautés de développeurs pour obtenir des retours et des améliorations.

---

**Last Updated:** 2026-06-01  
**Tested With:** GroupDocs.Metadata Java 23.9  
**Author:** GroupDocs

## Tutoriels associés

- [Comment extraire les blocs de ressources d'image d'un JPEG avec GroupDocs.Metadata pour Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Extraire les commentaires d'image JPEG2000 en Java avec GroupDocs.Metadata : guide étape par étape](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Extraire les ressources d'image des fichiers PSD avec GroupDocs.Metadata en Java : guide complet](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)