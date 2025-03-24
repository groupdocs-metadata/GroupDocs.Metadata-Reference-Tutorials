---
title: Leer propiedades integradas de archivos PDF en .NET
linktitle: Leer propiedades integradas de archivos PDF en .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda a leer metadatos PDF en .NET usando GroupDocs.Metadata. Acceda a nombres de autores, fechas de creación, temas y más con código C#.
weight: 10
url: /es/net/pdf-metadata/read-built-in-properties-pdfs/
---
## Introducción
En este tutorial, exploraremos cómo aprovechar GroupDocs.Metadata para .NET para leer propiedades integradas de archivos PDF. GroupDocs.Metadata es una poderosa biblioteca que permite a los desarrolladores trabajar con metadatos asociados con varios formatos de documentos, incluidos PDF, documentos de Microsoft Office, imágenes y más. Al utilizar esta biblioteca, puede acceder y manipular fácilmente los atributos de metadatos integrados en los archivos PDF, como nombres de autores, fechas de creación, temas y más.
## Requisitos previos
Antes de sumergirse en este tutorial, asegúrese de tener los siguientes requisitos previos:
- Visual Studio: asegúrese de tener Visual Studio instalado en su máquina.
-  GroupDocs.Metadata para .NET: descargue e instale GroupDocs.Metadata para .NET desde[aquí](https://releases.groupdocs.com/metadata/net/).
- Conocimientos básicos de C#: familiaridad con el lenguaje de programación C# y el marco .NET.

## Importar espacios de nombres
Comience agregando los espacios de nombres necesarios a su proyecto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Paso 1: cargar metadatos PDF
Primero, cargue el archivo PDF y extraiga sus metadatos usando GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // Acceda al paquete raíz del archivo PDF
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Recuperar y mostrar propiedades integradas
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // Se puede acceder a propiedades adicionales de manera similar
    // ...
}
```
Más allá de leer metadatos, GroupDocs.Metadata permite operaciones avanzadas como editar, eliminar o agregar nuevas propiedades de metadatos a archivos PDF mediante programación. Esta flexibilidad permite una gestión integral de los metadatos de los documentos dentro de sus aplicaciones .NET.
## Conclusión
En este tutorial, cubrimos cómo utilizar GroupDocs.Metadata para .NET para extraer propiedades integradas de archivos PDF usando C#. Al integrar esta biblioteca en sus proyectos, puede manejar sin problemas las operaciones de metadatos de documentos, proporcionando capacidades mejoradas de gestión de documentos.

## Preguntas frecuentes
### ¿GrupoDocs.Metadata puede funcionar con otros formatos de documentos?
Sí, GroupDocs.Metadata admite varios formatos de documentos como DOCX, XLSX, PPTX, PDF, JPG, PNG y más.
### ¿Existe una prueba gratuita disponible para GroupDocs.Metadata?
Sí, puede acceder a una prueba gratuita de GroupDocs.Metadata desde[aquí](https://releases.groupdocs.com/).
### ¿Cómo puedo modificar las propiedades de los metadatos usando GroupDocs.Metadata?
Puede modificar las propiedades de los metadatos mediante programación accediendo al paquete de documentos correspondiente y estableciendo nuevos valores.
### ¿GroupDocs.Metadata es compatible con .NET Core?
Sí, GroupDocs.Metadata es compatible tanto con .NET Framework como con .NET Core.
### ¿Dónde puedo encontrar soporte o hacer preguntas relacionadas con GroupDocs.Metadata?
 Para soporte y debates, visite el[Foro GroupDocs.Metadatos](https://forum.groupdocs.com/c/metadata/14).