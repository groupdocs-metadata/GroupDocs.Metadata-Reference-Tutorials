---
date: '2026-05-27'
description: Aprenda cómo establecer el CreatedTime de pptx en Java usando la dependencia
  Maven de GroupDocs para actualizar los metadatos de PowerPoint, incluido cómo cambiar
  la fecha de creación del PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Establecer CreatedTime de PPTX en Java con la dependencia Maven de GroupDocs
type: docs
url: /es/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Establecer CreatedTime de PPTX en Java con GroupDocs.Metadata

Los metadatos precisos son esenciales para el cumplimiento y la capacidad de descubrimiento en los flujos de trabajo modernos de documentos. Con **GroupDocs.Metadata** puedes programáticamente **establecer CreatedTime de PPTX en Java**, lo que te permite **cambiar la fecha de creación del PPTX** junto con otras propiedades incorporadas como autor o empresa. Este tutorial te guía a través de la configuración de Maven, la inicialización de la API, la actualización de metadatos y el guardado de la presentación modificada, todo con código claro y listo para producción.

## Respuestas rápidas
- **¿Qué biblioteca actualiza los metadatos de PowerPoint en Java?** GroupDocs.Metadata a través de la dependencia Maven de GroupDocs.  
- **¿Puedo establecer la propiedad CreatedTime del PPTX?** Sí—utiliza `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **¿Se requiere una licencia para producción?** Una prueba funciona para evaluación; una licencia comercial es obligatoria para implementaciones en producción.  
- **¿Qué herramienta de compilación usa el ejemplo?** Maven (también puedes descargar el JAR manualmente).  
- **¿La API es compatible con Java 8 y versiones posteriores?** Absolutamente—GroupDocs.Metadata está dirigido a Java 8+.

## ¿Qué es la dependencia Maven de GroupDocs?
La **dependencia Maven de GroupDocs** es una entrada de repositorio compatible con Maven que incorpora la última biblioteca GroupDocs.Metadata a tu proyecto Java. Simplifica la gestión de dependencias al resolver automáticamente las bibliotecas transitivas, garantiza que siempre uses la versión más reciente y segura, y elimina la necesidad de descargar JAR manualmente o rastrear versiones.

## ¿Por qué usar GroupDocs.Metadata para cambiar la fecha de creación del PPTX?
GroupDocs.Metadata permite actualizaciones automatizadas y listas para procesamiento por lotes de las marcas de tiempo de creación del PPTX, asegurando que cada presentación cumpla con las políticas corporativas o requisitos legales. Al establecer programáticamente la propiedad CreatedTime evitas la edición manual, reduces errores humanos y puedes integrar el cambio en pipelines CI/CD o scripts de migración para una gestión de documentos sin interrupciones.

## Requisitos previos
- Java 8 o superior instalado.  
- Un IDE como IntelliJ IDEA o Eclipse.  
- Maven para la gestión de dependencias.  
- Acceso a una prueba de GroupDocs o una licencia comprada.

## ¿Cómo establecer CreatedTime de PPTX en Java?
La clase `Metadata` representa un documento y brinda acceso a sus propiedades de metadatos.

Carga tu archivo PowerPoint con `new Metadata("presentation.pptx")`, recupera el paquete raíz, llama a `setCreatedTime` con el `java.util.Date` deseado y, finalmente, invoca `save` para escribir los cambios. Este flujo de extremo a extremo modifica la fecha de creación mientras preserva todo el contenido de las diapositivas y otras propiedades.

### Configuración de Maven
Añade el repositorio de GroupDocs y la dependencia de metadata a tu `pom.xml`:

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

> **Consejo profesional:** Mantener el número de versión actualizado garantiza que te beneficies de las últimas correcciones de errores y mejoras de rendimiento.

### Descarga directa (si prefieres no usar Maven)
Alternativamente, descarga el último JAR desde [GroupDocs.Metadata para lanzamientos Java](https://releases.groupdocs.com/metadata/java/).

#### Obtención de licencia
Comienza con una prueba gratuita o solicita una licencia temporal para evaluar GroupDocs.Metadata. Para uso en producción, compra una licencia a través del [sitio web oficial de GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Inicialización y configuración básicas
Una vez que la biblioteca está en el classpath, puedes crear una instancia de `Metadata` que apunte a tu archivo PowerPoint:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Este código abre la presentación en un bloque try‑with‑resources, garantizando que el manejador del archivo se libere automáticamente.

## Guía paso a paso para actualizar metadatos incorporados

### Paso 1: Cargar el documento de presentación
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Cargar el archivo establece una conexión que te permite leer o escribir metadatos.

### Paso 2: Acceder al paquete raíz de la presentación
El `root` object gives access to the presentation's core package and its built‑in properties.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

El objeto `root` expone todas las propiedades de documento incorporadas.

### Paso 3: Actualizar propiedades de documento incorporadas (incluida la fecha de creación)
`setCreatedTime` assigns a new creation timestamp to the document.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Aquí demostramos cómo **establecer CreatedTime de PPTX** asignando un nuevo objeto `Date` a `CreatedTime`. Reemplaza `new Date()` con cualquier marca de tiempo específica que necesites.

### Paso 4: Guardar la presentación actualizada
`save` writes the modified metadata back to a file.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

La llamada `save` escribe los metadatos modificados de vuelta a un nuevo archivo PowerPoint, dejando el original intacto.

## Consejos de solución de problemas
- **Archivo no encontrado:** Verifica nuevamente la ruta de entrada y los permisos del archivo.  
- **Incompatibilidad de versión:** Asegúrate de que la versión de `groupdocs-metadata` coincida con tu entorno Java.  
- **Propiedad no se actualiza:** Verifica que estés llamando a `setCreatedTime` (o al setter correspondiente) antes de invocar `save`.

## Aplicaciones prácticas
1. **Marca corporativa:** Inyecta automáticamente el nombre y la categoría correctos de la empresa en todas las presentaciones antes de la distribución.  
2. **Sistemas de gestión documental:** Enriquece los archivos PPTX con metadatos buscables para una recuperación más rápida.  
3. **Recursos educativos:** Mantén la información del autor y del currículo actualizada en todas las diapositivas de las clases.  
4. **Seguimiento de colaboración:** Registra los nombres de los colaboradores para mantener la responsabilidad.  
5. **Integración CMS:** Sincroniza los cambios de metadatos con tu plataforma de gestión de contenidos en tiempo real.

## Consideraciones de rendimiento
- **Procesamiento por lotes:** Recorre una lista de archivos y reutiliza una única instancia de `Metadata` cuando sea posible.  
- **Gestión de memoria:** Siempre usa try‑with‑resources (como se muestra) para liberar los recursos nativos rápidamente.  
- **Estructuras de datos eficientes:** Almacena las actualizaciones de metadatos en un mapa antes de aplicarlas para reducir llamadas repetitivas.

## Preguntas frecuentes

**P: ¿Cuál es el propósito principal de la dependencia Maven de GroupDocs?**  
R: Proporciona una forma conveniente de incluir la última biblioteca GroupDocs.Metadata en proyectos Java basados en Maven.

**P: ¿Cómo puedo establecer la fecha de creación del PPTX sin afectar otras propiedades?**  
R: Usa `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` antes de llamar a `metadata.save()`.

**P: ¿Necesito una licencia para ejecutar este código en desarrollo?**  
R: Una licencia de prueba temporal es suficiente para desarrollo y pruebas; se requiere una licencia completa para producción.

**P: ¿Puedo actualizar también campos de metadatos personalizados?**  
R: Sí—GroupDocs.Metadata admite tanto propiedades incorporadas como personalizadas a través de su API.

**P: ¿Hay una forma de revertir los cambios si cometo un error?**  
R: Mantén una copia del archivo original o lee los valores de propiedad existentes antes de sobrescribirlos, y luego restaura si es necesario.

## Recursos
- [Documentación](https://docs.groupdocs.com/metadata/java/)
- [Referencia de API](https://apireference.groupdocs.com/metadata/java/)

---

**Última actualización:** 2026-05-27  
**Probado con:** GroupDocs.Metadata 24.12 para Java  
**Autor:** GroupDocs  

## Tutoriales relacionados
- [Actualizar metadatos personalizados en PowerPoint usando la API Java de GroupDocs.Metadata](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Cómo actualizar los metadatos de documentos Word usando GroupDocs.Metadata Java: Guía completa](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Actualizar eficientemente metadatos PDF con GroupDocs.Metadata en Java para la gestión documental](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)