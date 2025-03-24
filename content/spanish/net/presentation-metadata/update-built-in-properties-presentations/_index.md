---
title: Actualizar propiedades integradas en presentaciones usando .NET
linktitle: Actualizar propiedades integradas en presentaciones usando .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda a actualizar propiedades integradas en presentaciones usando .NET con GroupDocs.Metadata, una biblioteca versátil de manipulación de metadatos.
weight: 15
url: /es/net/presentation-metadata/update-built-in-properties-presentations/
---

# Actualizar propiedades integradas en presentaciones usando .NET

## Introducción
En este tutorial, profundizaremos en las poderosas capacidades de GroupDocs.Metadata para .NET, una biblioteca integral diseñada para manipular metadatos dentro de documentos utilizando el marco .NET. Específicamente, nos centraremos en actualizar las propiedades integradas en presentaciones (archivos .PPT y .PPTX) mediante programación usando C#.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Visual Studio: instalado en su sistema.
-  GroupDocs.Metadata para .NET: descargado e instalado desde[aquí](https://releases.groupdocs.com/metadata/net/).
- Conocimientos básicos de C#: Familiaridad con el lenguaje de programación C#.

## Importar espacios de nombres
Comience importando los espacios de nombres necesarios a su proyecto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Paso 1: cargue el archivo de presentación
 Primero, cree una nueva instancia de`Metadata` cargando su archivo de presentación:
```csharp
using (Metadata metadata = new Metadata("YourPresentationFile.pptx"))
{
    var root = metadata.GetRootPackage<PresentationRootPackage>();
```
## Paso 2: actualizar las propiedades integradas
Ahora, actualice las propiedades integradas deseadas de la presentación. Por ejemplo, puedes modificar el autor, fecha de creación, empresa, categoría, palabras clave, etc. Así es como puedes hacerlo:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, presentation, update";
```
## Paso 3: guardar cambios
Después de actualizar las propiedades, guarde los cambios en el archivo de presentación:
```csharp
metadata.Save("YourPresentationFile.pptx");
```

## Conclusión
En este tutorial, exploramos cómo usar GroupDocs.Metadata para .NET para actualizar propiedades integradas en archivos de presentación mediante programación. Si sigue estos pasos, podrá administrar y modificar metadatos de manera eficiente dentro de sus aplicaciones .NET.

## Preguntas frecuentes
### P: ¿Qué es GroupDocs.Metadata para .NET?
R: GroupDocs.Metadata para .NET es una poderosa biblioteca de manipulación de metadatos para .NET framework, que permite a los desarrolladores leer, escribir y editar metadatos en varios formatos de documentos.
### P: ¿Dónde puedo encontrar documentación para GroupDocs.Metadata?
 R: Puedes acceder a la documentación detallada[aquí](https://tutorials.groupdocs.com/metadata/net/).
### P: ¿Cómo puedo obtener una licencia temporal para GroupDocs.Metadata?
 R: Puedes adquirir una licencia temporal[aquí](https://purchase.groupdocs.com/temporary-license/).
### P: ¿GroupDocs.Metadata admite otros formatos de archivo además de las presentaciones?
R: Sí, GroupDocs.Metadata admite una amplia gama de formatos, incluidos documentos, hojas de cálculo, imágenes, videos y más.
### P: ¿Dónde puedo obtener soporte o hacer preguntas sobre GroupDocs.Metadata?
 R: Para soporte y discusiones, visite el[Foro GroupDocs.Metadatos](https://forum.groupdocs.com/c/metadata/14).