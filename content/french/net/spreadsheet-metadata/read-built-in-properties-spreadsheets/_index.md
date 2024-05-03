---
title: Lire les propriétés intégrées à partir de feuilles de calcul dans .NET
linktitle: Lire les propriétés intégrées à partir de feuilles de calcul dans .NET
second_title: API GroupDocs.Metadata .NET
description: Découvrez comment extraire des métadonnées de feuilles de calcul dans .NET à l'aide de GroupDocs.Metadata, améliorant ainsi la gestion et l'organisation des documents dans vos applications.
type: docs
weight: 10
url: /fr/net/spreadsheet-metadata/read-built-in-properties-spreadsheets/
---
## Introduction
Dans ce didacticiel, nous verrons comment utiliser GroupDocs.Metadata pour .NET pour gérer et extraire efficacement les métadonnées des feuilles de calcul. GroupDocs.Metadata for .NET est une API puissante qui permet aux développeurs de travailler avec des métadonnées intégrées dans divers formats de fichiers, notamment des feuilles de calcul, des présentations, des documents, des images, etc. Ce guide se concentre spécifiquement sur l'extraction de propriétés intégrées à partir de feuilles de calcul à l'aide de C#.
## Conditions préalables
Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
- Environnement de développement : Visual Studio ou tout IDE compatible C#.
-  GroupDocs.Metadata for .NET Library : téléchargez et installez la bibliothèque à partir du[site web](https://releases.groupdocs.com/metadata/net/).
- Fichier d'entrée : préparez un exemple de fichier de feuille de calcul (par exemple, Excel) à partir duquel vous souhaitez extraire les métadonnées.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires pour accéder aux fonctionnalités GroupDocs.Metadata au sein de votre projet C#.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Étape 1 : initialiser les métadonnées et récupérer le package racine de la feuille de calcul
 Commencez par initialiser le`Metadata` object avec le chemin de votre fichier d’entrée. Ensuite, récupérez le package racine spécifique aux feuilles de calcul.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    
    //Accéder et récupérer les propriétés intégrées
}
```
## Étape 2 : accéder aux propriétés intégrées
 Une fois que vous disposez du package racine, vous pouvez accéder à diverses propriétés intégrées du fichier de feuille de calcul en utilisant`DocumentProperties`.
### Étape 2.1 : Accéder à la propriété de l'auteur
Récupérez l'auteur (créateur) de la feuille de calcul.
```csharp
Console.WriteLine(root.DocumentProperties.Author);
```
### Étape 2.2 : Accéder à la propriété d'heure créée
Obtenez l'horodatage de création de la feuille de calcul.
```csharp
Console.WriteLine(root.DocumentProperties.CreatedTime);
```
### Étape 2.3 : Accéder à la propriété de l'entreprise
Récupérez le nom de l’entreprise associé à la feuille de calcul.
```csharp
Console.WriteLine(root.DocumentProperties.Company);
```
### Étape 2.4 : Accéder à la propriété de catégorie
Obtenez les informations de catégorie de la feuille de calcul.
```csharp
Console.WriteLine(root.DocumentProperties.Category);
```
### Étape 2.5 : Accéder à la propriété des mots-clés
Récupérez les mots-clés associés à la feuille de calcul.
```csharp
Console.WriteLine(root.DocumentProperties.Keywords);
```
### Étape 2.6 : Accéder à la propriété de langue
Récupérez la langue utilisée dans la feuille de calcul.
```csharp
Console.WriteLine(root.DocumentProperties.Language);
```
### Étape 2.7 : Accéder à la propriété de type de contenu
Obtenez le type de contenu ou le type MIME de la feuille de calcul.
```csharp
Console.WriteLine(root.DocumentProperties.ContentType);
```

## Conclusion
Dans ce didacticiel, nous avons exploré comment utiliser GroupDocs.Metadata pour .NET pour extraire les propriétés intégrées des fichiers de feuille de calcul à l'aide de C#. En suivant ces étapes, vous pouvez intégrer de manière transparente la gestion des métadonnées dans vos applications .NET, améliorant ainsi l'organisation des fichiers et les capacités de récupération.

## FAQ
### GroupDocs.Metadata pour .NET est-il compatible avec différents formats de fichiers ?
Oui, GroupDocs.Metadata prend en charge un large éventail de formats de fichiers, notamment des feuilles de calcul, des documents, des présentations, des images, etc.
### Puis-je modifier les métadonnées à l’aide de GroupDocs.Metadata pour .NET ?
Oui, vous pouvez non seulement lire mais également modifier, mettre à jour et supprimer des métadonnées à l'aide de cette API.
### Où puis-je trouver une documentation détaillée pour GroupDocs.Metadata pour .NET ?
 Une documentation détaillée est disponible sur[Documentation GroupDocs.Metadata pour .NET](https://reference.groupdocs.com/metadata/net/).
### Comment puis-je obtenir une licence temporaire à des fins de test ?
 Vous pouvez demander une licence temporaire auprès de[ici](https://purchase.groupdocs.com/temporary-license/).
### Existe-t-il un forum communautaire pour la prise en charge de GroupDocs.Metadata ?
 Oui, vous pouvez visiter le[Forum GroupDocs.Metadonnées](https://forum.groupdocs.com/c/metadata/14) pour le soutien et les discussions de la communauté.