---
date: '2026-08-20'
description: Apprenez à extraire les métadonnées XMP en Java avec GroupDocs.Metadata.
  Ce guide montre comment extraire les métadonnées XMP de base, Dublin Core et Photoshop.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Apprenez à extraire les métadonnées XMP en Java avec GroupDocs.Metadata.
  Ce tutoriel couvre l'extraction des métadonnées XMP de base, Dublin Core et Photoshop,
  avec des exemples de code pratiques.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Comment extraire les métadonnées XMP avec GroupDocs.Metadata pour Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to extract XMP metadata in Java using GroupDocs.Metadata.
    This guide shows how to extract basic, Dublin Core, and Photoshop XMP metadata.
  headline: How to extract XMP metadata with GroupDocs.Metadata for Java
  type: TechArticle
- questions:
  - answer: Yes, GroupDocs.Metadata supports PDF XMP packets via the same `Metadata`
      API.
    question: Can I extract XMP from PDF files?
  - answer: The library throws a `UnsupportedFormatException`; catch it and fallback
      to a generic handler.
    question: What happens if the file format isn’t supported?
  - answer: Absolutely. After changing properties, call `metadata.save("output.png")`
      to persist the updates.
    question: Is it possible to modify XMP metadata and save it back?
  - answer: The core Java library is compatible with Android API 24+, but you must
      include the `android`‑specific artifact.
    question: Does the library work on Android?
  - answer: 'Provide the decryption password to the `Metadata` constructor: `new Metadata(filePath,
      "password")`.'
    question: How do I handle encrypted images?
  type: FAQPage
tags:
- extract XMP
- GroupDocs.Metadata
- Java metadata
- digital asset management
- XMP standards
title: Comment extraire les métadonnées XMP avec GroupDocs.Metadata pour Java
type: docs
url: /fr/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment extraire les métadonnées XMP avec GroupDocs.Metadata pour Java

Dans les flux de travail numériques modernes, **comment extraire les métadonnées XMP** rapidement et de manière fiable peut faire la différence entre une bibliothèque d'actifs recherchable et un dépôt de fichiers chaotique. Ce tutoriel vous guide à travers chaque étape — configuration de la bibliothèque, chargement des fichiers et extraction des paquets XMP de base, Dublin Core et spécifiques à Photoshop — afin que vous puissiez intégrer des métadonnées riches dans vos applications Java dès aujourd'hui.

## Réponses rapides
- **Quelle bibliothèque gère XMP en Java ?** GroupDocs.Metadata for Java.
- **Version minimale de Java ?** JDK 8 ou ultérieure.
- **Puis-je lire les fichiers PNG et JPEG ?** Oui, les deux sont pris en charge immédiatement.
- **Une licence est‑elle requise pour la production ?** Oui, une licence complète ou temporaire est nécessaire.
- **Où puis‑je trouver la référence API ?** Sur le site officiel de la documentation GroupDocs.Metadata.

## Qu'est-ce que les métadonnées XMP ?
XMP (Extensible Metadata Platform) est un format standard ISO permettant d’intégrer des métadonnées structurées directement à l’intérieur des fichiers multimédia. Il favorise l’interopérabilité entre applications et le stockage persistant des données sans modifier le contenu original. En stockant des informations telles que le créateur, le droit d’auteur, les réglages de l’appareil photo et des balises personnalisées dans le fichier, XMP garantit que les métadonnées accompagnent l’actif où qu’il aille, simplifiant le catalogage et la recherche à travers des systèmes divers.

## Pourquoi utiliser GroupDocs.Metadata pour Java ?
GroupDocs.Metadata prend en charge **plus de 30 formats de fichiers** (y compris PNG, JPEG, TIFF et PSD) et peut traiter des fichiers jusqu’à **2 Go** sans charger le document complet en mémoire, offrant une **réduction de 30 % de l’utilisation du CPU** par rapport aux analyseurs génériques. Cela le rend idéal pour les systèmes de gestion d’actifs numériques (DAM) à grande échelle.

## Prérequis

- **Java Development Kit (JDK) 8+** installé.
- **Maven** pour la gestion des dépendances.
- Familiarité de base avec Java I/O et la programmation orientée objet.

## Comment configurer GroupDocs.Metadata pour Java ?
Pour commencer, ajoutez le dépôt GroupDocs et la dépendance de la bibliothèque à votre `pom.xml` Maven. Cela garantit que Maven peut résoudre les artefacts et les maintenir à jour automatiquement, ce qui simplifie les futures mises à jour et correctifs de sécurité. Après avoir mis à jour le `pom.xml`, exécutez `mvn clean install` pour télécharger les JAR requis et vérifier que la configuration a réussi.

```xml
<!-- ```xml
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
``` -->
```

Si vous préférez une approche manuelle, téléchargez le dernier JAR depuis la page officielle des releases :

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Acquisition de licence
- **Essai gratuit** – évaluer toutes les fonctionnalités pendant 30 jours.
- **Licence temporaire** – utilisation pendant le développement sans restrictions.
- **Licence complète** – requise pour les déploiements en production.

## Initialisation de base

`Metadata` est le point d’entrée pour toutes les opérations. Il représente un fichier unique et fournit l’accès à ses paquets XMP intégrés.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Comment extraire les métadonnées XMP de base ?

Chargez l’image, ouvrez son paquet XMP et lisez les propriétés courantes telles que l’outil de création et les horodatages.

```java
// ```java
   Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
   ```
```

```java
// ```java
   IXmp root = (IXmp) metadata.getRootPackage();
   if (root.getXmpPackage() != null) {
       var xmpBasic = root.getXmpPackage().getSchemes().getXmpBasic();
   }
   ```
```

```java
// ```java
   if (xmpBasic != null) {
       String creatorTool = xmpBasic.getCreatorTool();
       String createDate = xmpBasic.getCreateDate();
       String modifyDate = xmpBasic.getModifyDate();
       // Use the extracted properties as needed
   }
   ```
```

## Comment extraire les métadonnées XMP Dublin Core ?

Le schéma Dublin Core stocke des éléments descriptifs standardisés tels que le titre, le créateur et le sujet. Accédez‑y via la classe `DublinCorePackage`.

```java
// ```java
   var dublinCore = root.getXmpPackage().getSchemes().getDublinCore();
   ```
```

```java
// ```java
   if (dublinCore != null) {
       String format = dublinCore.getFormat();
       String coverage = dublinCore.getCoverage();
       // Use the extracted properties as needed
   }
   ```
```

## Comment extraire les métadonnées XMP spécifiques à Photoshop ?

Photoshop intègre des informations supplémentaires telles que le mode couleur, la résolution et le nombre de calques. Récupérez ces valeurs via le `PhotoshopPackage`.

```java
// ```java
   var photoshop = root.getXmpPackage().getSchemes().getPhotoshop();
   ```
```

```java
// ```java
   if (photoshop != null) {
       String colorMode = photoshop.getColorMode();
       // Use the extracted properties as needed
   }
   ```
```

## Applications pratiques

- **Gestion d’actifs numériques** – étiqueter et rechercher les images par créateur, droit d’auteur ou réglages de l’appareil photo.
- **Flux de publication automatisés** – injecter ou modifier XMP avant la publication dans des galeries web.
- **Analytique** – agréger les métadonnées de milliers de fichiers pour découvrir les tendances d’utilisation.

## Considérations de performance

La classe `Metadata` fournit l’accès aux métadonnées et aux paquets XMP d’un fichier. Libérez les objets `Metadata` dès que vous avez fini la lecture afin de libérer les ressources natives. `LoadOptions.LAZY` indique à la bibliothèque de charger les métadonnées de façon paresseuse, réduisant ainsi l’utilisation de la mémoire. Diffusez les gros fichiers en utilisant `Metadata.load(InputStream)` pour maintenir une faible consommation de heap. Réutilisez une même instance `Metadata` lors de la lecture de nombreux petits fichiers afin de réduire la surcharge de création d’objets.

## Pièges courants et dépannage

| Symptôme | Cause probable | Solution |
|---|---|---|
| `NullPointerException` lors de l'accès à XMP | Le fichier ne contient aucun paquet XMP | Appelez `metadata.getXmpPackage()` et vérifiez que le résultat n’est pas `null` avant de lire. La méthode `getXmpPackage()` renvoie l’objet paquet XMP, ou `null` s’il n’existe pas. |
| Traitement lent sur des images de 500 Mo | Chargement du fichier complet en mémoire | Utilisez `metadata.load(InputStream)` et activez `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Champs Photoshop manquants | Image enregistrée sans les informations de calque Photoshop | Vérifiez que le fichier source a été exporté depuis Photoshop avec l’option « Save XMP » activée |

## Questions fréquemment posées

**Q : Puis‑je extraire XMP à partir de fichiers PDF ?**  
R : Oui, GroupDocs.Metadata prend en charge les paquets XMP PDF via la même API `Metadata`.

**Q : Que se passe‑t‑il si le format de fichier n’est pas pris en charge ?**  
R : La bibliothèque lève une `UnsupportedFormatException` ; attrapez‑la et basculez vers un gestionnaire générique.

**Q : Est‑il possible de modifier les métadonnées XMP et de les enregistrer ?**  
R : Absolument. Après avoir modifié les propriétés, appelez `metadata.save("output.png")` pour persister les mises à jour.

**Q : La bibliothèque fonctionne‑t‑elle sur Android ?**  
R : La bibliothèque Java core est compatible avec Android API 24+, mais vous devez inclure l’artifact spécifique `android`.

**Q : Comment gérer les images chiffrées ?**  
R : Fournissez le mot de passe de déchiffrement au constructeur `Metadata` : `new Metadata(filePath, "password")`.

## Conclusion

Vous disposez maintenant d’un guide complet et prêt pour la production sur **comment extraire les métadonnées XMP** à l’aide de GroupDocs.Metadata pour Java. En suivant les étapes ci‑dessus, vous pouvez enrichir vos applications avec des métadonnées recherchables et conformes aux normes, et débloquer des capacités puissantes de gestion d’actifs.

## Prochaines étapes

Explorez plus en profondeur l’ensemble complet des fonctionnalités en consultant la documentation officielle et en expérimentant d’autres normes de métadonnées telles que IPTC et EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Last Updated:** 2026-08-20  
**Tested With:** GroupDocs.Metadata for Java 23.11  
**Author:** GroupDocs  

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [Référence API](https://reference.groupdocs.com/metadata/java/)
- [Téléchargement](https://releases.groupdocs.com/metadata/java/)
- [Dépôt GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Forum d’assistance gratuit](https://forum.groupdocs.com/c/metadata/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)

## Tutoriels associés

- [Extraire les métadonnées Dublin Core d’un EPUB avec GroupDocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Extraire la balise logicielle EXIF en Java : guide complet avec GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Comment extraire les métadonnées avec GroupDocs.Metadata pour Java – Tutoriels & exemples](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}