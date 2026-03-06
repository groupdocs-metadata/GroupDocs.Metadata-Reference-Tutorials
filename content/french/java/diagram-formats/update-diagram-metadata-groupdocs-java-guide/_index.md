---
date: '2026-01-19'
description: Apprenez comment modifier la date de création et automatiser la mise
  à jour des métadonnées des fichiers de diagramme à l'aide de GroupDocs.Metadata
  en Java.
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: Modifier l'heure de création dans les métadonnées du diagramme à l'aide de
  GroupDocs Java
type: docs
url: /fr/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Modifier l'heure de création dans les métadonnées de diagramme avec GroupDocs Java

Mettre à jour les propriétés de métadonnées telles que le créateur, **modifier l'heure de création**, et la catégorie manuellement peut être fastidieux. Automatisez ce processus avec la bibliothèque GroupDocs.Metadata pour Java, et vous pourrez **modifier l'heure de création** ainsi que d'autres propriétés intégrées en une seule étape répétable. Ce guide vous accompagne dans la configuration de la bibliothèque, la mise à jour des métadonnées de diagramme, et l'application de bonnes pratiques de performance afin de garder vos documents cohérents et recherchables.

## Réponses rapides
- **Quel est l'objectif principal ?** Modifier l'heure de création et d'autres métadonnées dans les fichiers de diagramme.  
- **Quelle bibliothèque dois‑je utiliser ?** GroupDocs.Metadata pour Java.  
- **Ai‑je besoin d'une licence ?** Un essai gratuit suffit pour les tests ; une licence complète est requise pour la production.  
- **Puis‑je traiter en lot de nombreux diagrammes ?** Oui — utilisez la même approche dans une boucle ou un flux parallèle.  
- **Quelle version de Java est requise ?** JDK 8 ou supérieur.

## Qu’est‑ce que « modifier l'heure de création » dans les métadonnées de diagramme ?
Modifier l'heure de création signifie écraser l'horodatage original stocké à l'intérieur d'un fichier de diagramme (par ex., VDX, VSDX) avec une nouvelle date. Cela est utile lorsque vous avez besoin que les métadonnées du fichier reflètent la date réelle de traitement plutôt que la date d'auteur originale.

## Pourquoi automatiser la mise à jour des métadonnées pour les diagrammes ?
- **Cohérence :** Garantit que chaque fichier suit les mêmes règles de nommage et de catégorisation.  
- **Facilité de recherche :** Les mots‑clés et catégories mis à jour améliorent la découverte des documents dans les solutions DMS.  
- **Conformité :** Aide à répondre aux exigences d’audit en assurant des horodatages précis.  

## Prérequis
- **Java Development Kit (JDK) 8+** installé.  
- **IDE** tel qu’IntelliJ IDEA ou Eclipse.  
- **Maven** (ou gestion manuelle des JAR) pour la gestion des dépendances.  
- Connaissances de base des classes Java, des méthodes et de la gestion des exceptions.

### Bibliothèques et dépendances requises
Ajoutez le dépôt et la dépendance suivants à votre fichier `pom.xml` si vous utilisez Maven :

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
Si vous préférez télécharger directement, visitez [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) pour obtenir la dernière version.

### Configuration de l'environnement
- JDK 8 ou plus récent.  
- IntelliJ IDEA, Eclipse ou tout IDE compatible Java.  

### Prérequis de connaissances
Comprendre la syntaxe Java et les bases des entrées‑sorties de fichiers facilitera le tutoriel, mais les étapes sont expliquées en langage clair.

## Configuration de GroupDocs.Metadata pour Java
### Instructions d'installation
**Utilisateurs Maven :** Le fragment ci‑dessus ajoute le dépôt et le JAR requis automatiquement.  
**Utilisateurs téléchargement direct :** Après avoir téléchargé le JAR depuis [GroupDocs](https://releases.groupdocs.com/metadata/java/), ajoutez‑le au classpath de votre projet.

### Acquisition de licence
- **Essai gratuit :** Explorez la bibliothèque sans frais.  
- **Licence temporaire :** Obtenez une licence temporaire pour des tests prolongés [ici](https://purchase.groupdocs.com/temporary-license/).  
- **Achat :** Acquérez une licence complète pour les environnements de production.

### Initialisation de base
Pour commencer à utiliser GroupDocs.Metadata, importez la classe et ouvrez un fichier de diagramme :

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Avec la bibliothèque initialisée, vous pouvez maintenant modifier n'importe quelle propriété intégrée, y compris l'heure de création.

## Guide de mise en œuvre
### Comment modifier l'heure de création dans les fichiers de diagramme
Dans cette section nous passerons en revue chaque étape nécessaire pour **modifier l'heure de création** et mettre à jour d'autres propriétés courantes telles que l'auteur, l'entreprise et la catégorie.

#### Étape 1 : Charger le document de diagramme
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```
*Explication :* Le constructeur `Metadata` reçoit le chemin vers votre fichier de diagramme. Le bloc try‑with‑resources garantit que le fichier est correctement fermé après l'opération.

#### Étape 2 : Accéder au package racine
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```
*Explication :* Le package racine vous donne un accès direct à tous les champs de métadonnées intégrés du diagramme.

#### Étape 3 : Définir la propriété Créateur
```java
root.getDocumentProperties().setCreator("test author");
```
*Explication :* Attribue un nouveau nom d'auteur. Remplacez `"test author"` par le créateur réel.

#### Étape 4 : **Modifier l'heure de création**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*Explication :* Cette ligne **modifie l'heure de création** à la date et l'heure système actuelles. Vous pouvez également fournir une instance `Date` spécifique si vous avez besoin d'un horodatage personnalisé.

#### Étape 5 : Définir les informations de l'entreprise
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*Explication :* Enregistre le nom de l'entreprise associé au diagramme — utile pour le suivi en entreprise.

#### Étape 6 : Définir la catégorie du document
```java
root.getDocumentProperties().setCategory("test category");
```
*Explication :* Catégorise le fichier, vous aidant à **mettre à jour la catégorie du diagramme** de façon cohérente dans tout votre référentiel.

#### Étape 7 : Ajouter des mots‑clés
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*Explication :* Les mots‑clés améliorent la recherchabilité ; vous pouvez lister tous les termes pertinents au contenu du diagramme.

#### Étape 8 : Enregistrer les modifications
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*Explication :* Persiste toutes les modifications dans un nouveau fichier, laissant l'original intact.

### Pièges courants & dépannage
- **Fichier non trouvé :** Vérifiez le chemin d’entrée et assurez‑vous que l’extension du fichier correspond au format réel.  
- **Accès refusé :** Vérifiez les permissions de lecture/écriture pour les répertoires d’entrée et de sortie.  
- **Format de date invalide :** Utilisez des objets `java.util.Date` ou `java.time` compatibles avec l’API.  

## Applications pratiques
1. **Automatisation de l'archivage de documents** – Lors du déplacement d'anciens diagrammes vers une archive, modifiez automatiquement **l'heure de création** à la date d'archivage et définissez une catégorie uniforme.  
2. **Intégration du contrôle de version** – Gardez les horodatages synchronisés avec les commits Git en mettant à jour l'heure de création à chaque version.  
3. **Normalisation DMS d'entreprise** – Appliquez une politique d’entreprise pour l’auteur, l’entreprise et les mots‑clés sur tous les actifs de diagrammes.  

## Considérations de performance
- **Traitement par lots :** Enveloppez les étapes ci‑dessus dans une boucle pour gérer des dizaines de fichiers en une exécution.  
- **Gestion de la mémoire :** Libérez chaque instance `Metadata` rapidement (le bloc try‑with‑resources le fait automatiquement).  
- **Exécution asynchrone :** Pour de gros lots, envisagez `CompletableFuture` pour exécuter les mises à jour en parallèle sans bloquer le thread principal.  

## Conclusion
Vous savez maintenant comment **modifier l'heure de création** et mettre à jour d'autres propriétés de métadonnées intégrées pour les documents de diagramme en utilisant GroupDocs.Metadata en Java. En automatisant ces étapes, vous pouvez maintenir une documentation cohérente, recherchable et conforme dans toute votre organisation.

**Prochaines étapes**
- Expérimentez d’autres formats de fichiers pris en charge par GroupDocs.Metadata (PDF, DOCX, etc.).  
- Intégrez le code dans un pipeline CI/CD pour appliquer les normes de métadonnées à chaque build.  

Prêt à essayer ? Rendez‑vous sur [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) et commencez dès aujourd'hui à implémenter votre propre automatisation des métadonnées.

---

**Dernière mise à jour :** 2026-01-19  
**Testé avec :** GroupDocs.Metadata 24.12  
**Auteur :** GroupDocs  

## Foire aux questions

**Q : Puis‑je utiliser cette approche avec d'autres formats de diagramme comme VSDX ?**  
R : Oui, la même API fonctionne pour tous les formats de diagramme pris en charge par GroupDocs.Metadata.

**Q : Ai‑je besoin d'une licence pour les builds de développement ?**  
R : Un essai gratuit suffit pour le développement et les tests ; une licence complète est requise pour les déploiements en production.

**Q : Comment puis‑je mettreR : un nouveau fichier (comme montré) pour éviter toute perte de données, puis de remplacer l'original si nécessaire.

**Q : Et si je dois définir une date de création personnalisée au lieu de l'heure actuelle ?**  
R : Créez une instance `java.util.Date` (ou `java.time`) avec le timestamp souhaité et transmettez‑la à `setTimeCreated`.