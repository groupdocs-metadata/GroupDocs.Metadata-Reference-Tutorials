---
title: Actualizar propiedades integradas en archivos PDF usando .NET
linktitle: Actualizar propiedades integradas en archivos PDF usando .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda a actualizar las propiedades de documentos PDF usando C# y GroupDocs.Metadata para .NET. Modifique el autor, el título, las palabras clave y más mediante programación.
type: docs
weight: 15
url: /es/net/pdf-metadata/update-built-in-properties-pdfs/
---
## Introducción
En este tutorial, aprenderemos cómo usar GroupDocs.Metadata para .NET para actualizar las propiedades integradas de los documentos PDF. Esta biblioteca proporciona un poderoso conjunto de herramientas para manipular metadatos dentro de varios formatos de documentos. Revisaremos los pasos necesarios para modificar propiedades como autor, título, fecha de creación, palabras clave, creador y productor en un archivo PDF usando C#.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente en su lugar:
-  Biblioteca GroupDocs.Metadata para .NET: descargue la biblioteca desde[aquí](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: instale Visual Studio para escribir y ejecutar el código C#.
- Conocimientos básicos de C#: se recomienda estar familiarizado con el lenguaje de programación C#.

## Importar espacios de nombres
Comience por incluir los espacios de nombres necesarios en su proyecto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Paso 1: inicializar el objeto de metadatos
 Comience por inicializar un`Metadata`objeto con la ruta a su archivo PDF:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Tu código irá aquí
}
```
## Paso 2: acceda al paquete raíz de PDF
 A continuación, recupere el paquete raíz específicamente para PDF usando`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Paso 3: actualizar las propiedades del documento
 Ahora, actualice las propiedades deseadas del documento PDF dentro del`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Paso 4: guardar cambios
Después de modificar las propiedades, guarde los cambios nuevamente en el archivo PDF:
```csharp
metadata.Save("Your Output File Path");
```
## Paso 5: recuperar propiedades actualizadas
Para verificar los cambios, vuelva a cargar los metadatos y recupere las propiedades actualizadas:
```csharp
using (Metadata metadata = new Metadata("Your Output File Path"))
{
    var root = metadata.GetRootPackage<PdfRootPackage>();
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Title: " + root.DocumentProperties.Title);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    Console.WriteLine("Creator: " + root.DocumentProperties.Creator);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
}
```

## Conclusión
En este tutorial, exploramos cómo aprovechar GroupDocs.Metadata para .NET para actualizar las propiedades integradas de los documentos PDF mediante programación. Si sigue los pasos descritos, puede administrar y modificar de manera eficiente los metadatos dentro de archivos PDF usando C#. No dude en explorar más funciones y capacidades que ofrece GroupDocs.Metadata para una manipulación integral de metadatos.

## Preguntas frecuentes
### P: ¿Qué es GroupDocs.Metadata para .NET?
R: GroupDocs.Metadata para .NET es una biblioteca que permite a los desarrolladores leer, editar, eliminar y manipular metadatos en varios formatos de documentos mediante programación.
### P: ¿Dónde puedo encontrar la documentación de GroupDocs.Metadata para .NET?
 R: Puedes acceder a la documentación[aquí](https://reference.groupdocs.com/metadata/net/).
### P: ¿Cómo puedo descargar GroupDocs.Metadata para .NET?
 R: Puede descargar GroupDocs.Metadata para .NET desde[este enlace](https://releases.groupdocs.com/metadata/net/).
### P: ¿Hay una prueba gratuita disponible?
 R: Sí, puedes obtener una versión de prueba gratuita.[aquí](https://releases.groupdocs.com/).
### P: ¿Dónde puedo obtener soporte para GroupDocs.Metadata para .NET?
 R: Para obtener ayuda, visite el foro GroupDocs.Metadata[aquí](https://forum.groupdocs.com/c/metadata/14).