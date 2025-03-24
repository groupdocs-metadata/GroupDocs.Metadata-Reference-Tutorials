---
title: Mettre à jour les propriétés intégrées dans les présentations à l'aide de .NET
linktitle: Mettre à jour les propriétés intégrées dans les présentations à l'aide de .NET
second_title: API GroupDocs.Metadata .NET
description: Découvrez comment mettre à jour les propriétés intégrées dans les présentations à l'aide de .NET avec GroupDocs.Metadata, une bibliothèque polyvalente de manipulation de métadonnées.
weight: 15
url: /fr/net/presentation-metadata/update-built-in-properties-presentations/
---
## Introduction
Dans ce didacticiel, nous approfondirons les puissantes fonctionnalités de GroupDocs.Metadata pour .NET, une bibliothèque complète conçue pour manipuler les métadonnées dans les documents à l'aide du framework .NET. Plus précisément, nous nous concentrerons sur la mise à jour des propriétés intégrées dans les présentations (fichiers .PPT et .PPTX) par programmation à l'aide de C#.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio : installé sur votre système.
-  GroupDocs.Metadata pour .NET : téléchargé et installé à partir de[ici](https://releases.groupdocs.com/metadata/net/).
- Connaissances de base en C# : Familiarité avec le langage de programmation C#.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires dans votre projet C# :
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Étape 1 : Charger le fichier de présentation
 Tout d'abord, créez une nouvelle instance de`Metadata` en chargeant votre fichier de présentation :
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Étape 2 : mettre à jour les propriétés intégrées
Maintenant, mettez à jour les propriétés intégrées souhaitées de la présentation. Vous pouvez par exemple modifier l'auteur, la date de création, la société, la catégorie, les mots-clés, etc. Voici comment procéder :
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## Étape 3 : Enregistrer les modifications
Après avoir mis à jour les propriétés, enregistrez les modifications dans le fichier de présentation :
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Conclusion
Dans ce didacticiel, nous avons expliqué comment utiliser GroupDocs.Metadata pour .NET pour mettre à jour par programme les propriétés intégrées dans les fichiers de présentation. En suivant ces étapes, vous pouvez gérer et modifier efficacement les métadonnées au sein de vos applications .NET.

## FAQ
### Q : Qu'est-ce que GroupDocs.Metadata pour .NET ?
R : GroupDocs.Metadata for .NET est une puissante bibliothèque de manipulation de métadonnées pour le framework .NET, permettant aux développeurs de lire, d'écrire et de modifier des métadonnées dans différents formats de documents.
### Q : Où puis-je trouver de la documentation pour GroupDocs.Metadata ?
 R : Vous pouvez accéder à la documentation détaillée[ici](https://tutorials.groupdocs.com/metadata/net/).
### Q : Comment puis-je obtenir une licence temporaire pour GroupDocs.Metadata ?
 R : Vous pouvez acquérir une licence temporaire[ici](https://purchase.groupdocs.com/temporary-license/).
### Q : GroupDocs.Metadata prend-il en charge d'autres formats de fichiers que les présentations ?
R : Oui, GroupDocs.Metadata prend en charge un large éventail de formats, notamment des documents, des feuilles de calcul, des images, des vidéos, etc.
### Q : Où puis-je obtenir de l'aide ou poser des questions sur GroupDocs.Metadata ?
 R : Pour obtenir de l'aide et des discussions, visitez le[Forum GroupDocs.Metadonnées](https://forum.groupdocs.com/c/metadata/14).