---
date: '2026-08-20'
description: Aprenda a extraer metadatos XMP en Java usando GroupDocs.Metadata. Esta
  guía muestra cómo extraer metadatos XMP básicos, Dublin Core y Photoshop.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Aprenda a extraer metadatos XMP en Java usando GroupDocs.Metadata.
  Este tutorial cubre la extracción básica, Dublin Core y Photoshop XMP con ejemplos
  de código prácticos.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Cómo extraer metadatos XMP con GroupDocs.Metadata para Java
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
title: Cómo extraer metadatos XMP con GroupDocs.Metadata para Java
type: docs
url: /es/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo extraer metadatos XMP con GroupDocs.Metadata para Java

En los flujos de trabajo digitales modernos, **cómo extraer XMP** rápidamente y de forma fiable puede marcar la diferencia entre una biblioteca de recursos buscable y un volcado caótico de archivos. Este tutorial le guía paso a paso—configurar la biblioteca, cargar archivos y extraer paquetes XMP básicos, Dublin Core y específicos de Photoshop—para que pueda integrar metadatos enriquecidos en sus aplicaciones Java hoy.

## Respuestas rápidas
- **¿Qué biblioteca maneja XMP en Java?** GroupDocs.Metadata for Java.
- **¿Versión mínima de Java?** JDK 8 o posterior.
- **¿Puedo leer archivos PNG y JPEG?** Sí, ambos son compatibles de forma nativa.
- **¿Se requiere una licencia para producción?** Sí, se necesita una licencia completa o temporal.
- **¿Dónde puedo encontrar la referencia de la API?** En el sitio oficial de documentación de GroupDocs.Metadata.

## Qué son los metadatos XMP?
XMP (Extensible Metadata Platform) es un formato estándar ISO para incrustar metadatos estructurados directamente dentro de archivos multimedia. Permite la interoperabilidad entre aplicaciones y el almacenamiento persistente de datos sin alterar el contenido original. Al almacenar información como creador, derechos de autor, ajustes de cámara y etiquetas personalizadas dentro del archivo, XMP garantiza que los metadatos viajen con el recurso dondequiera que vaya, simplificando la catalogación y búsqueda en sistemas diversos.

## ¿Por qué usar GroupDocs.Metadata para Java?
GroupDocs.Metadata soporta **más de 30 formatos de archivo** (incluidos PNG, JPEG, TIFF y PSD) y puede procesar archivos de hasta **2 GB** sin cargar todo el documento en memoria, ofreciendo una **reducción del 30 % en el uso de CPU** en comparación con analizadores genéricos. Esto lo hace ideal para sistemas de gestión de activos digitales (DAM) a gran escala.

## Requisitos previos

- **Java Development Kit (JDK) 8+** instalado.
- **Maven** para la gestión de dependencias.
- Familiaridad básica con Java I/O y programación orientada a objetos.

## ¿Cómo configurar GroupDocs.Metadata para Java?
Para comenzar, añada el repositorio de GroupDocs y la dependencia de la biblioteca a su `pom.xml` de Maven. Esto garantiza que Maven pueda resolver los artefactos y mantenerlos actualizados automáticamente, lo que simplifica futuras actualizaciones y parches de seguridad. Después de actualizar el `pom.xml`, ejecute `mvn clean install` para descargar los JAR necesarios y verificar que la configuración se haya completado con éxito.

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

Si prefiere un enfoque manual, descargue el JAR más reciente desde la página oficial de lanzamientos:

[​Lanzamientos de GroupDocs.Metadata para Java](https://releases.groupdocs.com/metadata/java/)

### Obtención de licencia
- **Prueba gratuita** – evalúe todas las funciones durante 30 días.
- **Licencia temporal** – úsela durante el desarrollo sin restricciones.
- **Licencia completa** – requerida para implementaciones en producción.

## Inicialización básica

`Metadata` es el punto de entrada para todas las operaciones. Representa un archivo único y proporciona acceso a sus paquetes XMP incrustados.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## ¿Cómo extraer metadatos XMP básicos?

Cargue la imagen, abra su paquete XMP y lea propiedades comunes como la herramienta creadora y las marcas de tiempo.

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

## ¿Cómo extraer metadatos XMP Dublin Core?

El esquema Dublin Core almacena elementos descriptivos estandarizados como título, creador y asunto. Acceda a él mediante la clase `DublinCorePackage`.

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

## ¿Cómo extraer metadatos XMP específicos de Photoshop?

Photoshop incrusta información adicional como modo de color, resolución y número de capas. Recupere estos valores a través del `PhotoshopPackage`.

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

## Aplicaciones prácticas

- **Gestión de activos digitales** – etiquetar y buscar imágenes por creador, derechos de autor o configuraciones de cámara.
- **Flujos de publicación automatizados** – inyectar o modificar XMP antes de publicar en galerías web.
- **Analítica** – agregar metadatos de miles de archivos para descubrir tendencias de uso.

## Consideraciones de rendimiento

La clase `Metadata` brinda acceso a los metadatos y paquetes XMP de un archivo. Libere los objetos `Metadata` tan pronto como termine de leer para liberar recursos nativos. `LoadOptions.LAZY` indica a la biblioteca que cargue los metadatos de forma perezosa, reduciendo el uso de memoria. Transmita archivos grandes usando `Metadata.load(InputStream)` para mantener bajo el uso del heap. Reutilice una única instancia de `Metadata` al leer muchos archivos pequeños para reducir la sobrecarga de creación de objetos.

## Problemas comunes y solución de errores

| Síntoma | Causa probable | Solución |
|---|---|---|
| `NullPointerException` al acceder a XMP | El archivo no tiene paquete XMP | Llame a `metadata.getXmpPackage()` y verifique que no sea `null` antes de leer. El método `getXmpPackage()` devuelve el objeto del paquete XMP, o null si no existe. |
| Procesamiento lento en imágenes de 500 MB | Cargando todo el archivo en memoria | Use `metadata.load(InputStream)` y habilite `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Faltan campos de Photoshop | Imagen guardada sin información de capas de Photoshop | Verifique que el archivo fuente se haya exportado desde Photoshop con la opción “Save XMP” habilitada |

## Preguntas frecuentes

**Q: ¿Puedo extraer XMP de archivos PDF?**  
A: Sí, GroupDocs.Metadata soporta paquetes XMP de PDF a través de la misma API `Metadata`.

**Q: ¿Qué ocurre si el formato de archivo no está soportado?**  
A: La biblioteca lanza una `UnsupportedFormatException`; captúrela y recurra a un manejador genérico.

**Q: ¿Es posible modificar los metadatos XMP y guardarlos nuevamente?**  
A: Absolutamente. Después de cambiar las propiedades, llame a `metadata.save("output.png")` para persistir las actualizaciones.

**Q: ¿Funciona la biblioteca en Android?**  
A: La biblioteca central de Java es compatible con Android API 24+, pero debe incluir el artefacto específico `android`.

**Q: ¿Cómo manejo imágenes encriptadas?**  
A: Proporcione la contraseña de descifrado al constructor `Metadata`: `new Metadata(filePath, "password")`.

## Conclusión

Ahora dispone de una guía completa y lista para producción sobre **cómo extraer XMP** usando GroupDocs.Metadata para Java. Siguiendo los pasos anteriores, podrá enriquecer sus aplicaciones con metadatos buscables y compatibles con estándares, y desbloquear potentes capacidades de gestión de activos.

## Próximos pasos

Profundice en el conjunto completo de funciones revisando la documentación oficial y experimentando con otros estándares de metadatos como IPTC y EXIF.

[documentación](https://docs.groupdocs.com/metadata/java/)

---

**Última actualización:** 2026-08-20  
**Probado con:** GroupDocs.Metadata for Java 23.11  
**Autor:** GroupDocs  

- [Documentación](https://docs.groupdocs.com/metadata/java/)
- [Referencia de API](https://reference.groupdocs.com/metadata/java/)
- [Descarga](https://releases.groupdocs.com/metadata/java/)
- [Repositorio GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Foro de soporte gratuito](https://forum.groupdocs.com/c/metadata/)
- [Licencia temporal](https://purchase.groupdocs.com/temporary-license/)

## Tutoriales relacionados

- [Extraer metadatos Dublin Core de Epub con Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Extraer etiqueta de software EXIF en Java: Guía completa usando GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Cómo extraer metadatos con GroupDocs.Metadata para Java – Tutoriales y ejemplos](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}