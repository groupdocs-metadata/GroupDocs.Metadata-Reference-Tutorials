---
date: '2026-01-19'
description: Aprende cómo cambiar la hora de creación y automatizar la actualización
  de metadatos para archivos de diagramas usando GroupDocs.Metadata en Java.
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: Cambiar la hora de creación en los metadatos del diagrama con GroupDocs Java
type: docs
url: /es/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

# Cambiar la hora de creación en los metadatos del diagrama usando GroupDocs Java

## Respuestas rápidas
- **¿Cuál es el objetivo principal?** Cambiar la hora de creación y otros metadatos en archivos de diagramas.  
- **¿Qué biblioteca debo usar?** GroupDocs.Metadata para Java.  
- **¿Necesito una licencia?** Una prueba gratuita funciona para pruebas; se requiere una licencia completa para producción.  
- **¿Puedo procesar por lotes muchos diagramas?** Sí—utilice el mismo enfoque dentro de un bucle o flujo paralelo.  
- **¿Qué versión de Java se requiere?** JDK 8 o superior.

## ¿Qué es “cambiar la hora de creación” en los metadatos del diagrama?
Cambiar la hora de creación significa sobrescribir la marca de tiempo original almacenada dentro de un archivo de diagrama (p. ej., VDX, VSDX) con una nueva fecha. Esto es útil cuando necesita que los metadatos del archivo reflejen la fecha real de procesamiento en lugar de la fecha de creación original.

## ¿Por qué automatizar la actualización de metadatos para diagramas?
- **Consistencia:** Garantiza que cada archivo siga las mismas reglas de nomenclatura y categorización.  
- **Facilidad de búsqueda:** Las palabras clave y categorías actualizadas mejoran el descubrimiento de documentos en soluciones DMS.  
- **Cumplimiento:** Ayuda a cumplir con los requisitos de auditoría al asegurar marcas de tiempo precisas.  

## Requisitos previos
- **Java Development Kit (JDK) 8+** instalado.  
- **IDE** como IntelliJ IDEA o Eclipse.  
- **Maven** (o manejo manual de JAR) para la gestión de dependencias.  
- Conocimientos básicos de clases, métodos y manejo de excepciones en Java.

### Bibliotecas y dependencias requeridas
Agregue el siguiente repositorio y dependencia a su archivo `pom.xml` si usa Maven:

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

Si prefiere descargar directamente, visite [Lanzamientos de GroupDocs.Metadata para Java](https://releases.groupdocs.com/metadata/java/) para obtener la última versión.

### Configuración del entorno
- JDK 8 o más reciente.  
- IntelliJ IDEA, Eclipse o cualquier IDE compatible con Java.  

### Prerequisitos de conocimiento
Comprender la sintaxis de Java y la E/S de archivos básica hará el tutorial más fluido, pero los pasos se explican en lenguaje sencillo.

## Configuración de GroupDocs.Metadata para Java
### Instrucciones de instalación
**Usuarios de Maven:** El fragmento anterior agrega el repositorio y el JAR requerido automáticamente.  
**Usuarios de descarga directa:** Después de descargar el JAR desde [GroupDocs](https://releases.groupdocs.com/metadata/java/), agréguelo al classpath de su proyecto.

### Obtención de licencia
- **Prueba gratuita:** Explore la biblioteca sin costo.  
- **Licencia temporal:** Obtenga una licencia temporal para pruebas extendidas [aquí](https://purchase.groupdocs.com/temporary-license/).  
- **Compra:** Adquiera una licencia completa para entornos de producción.

### Inicialización básica
Para comenzar a usar GroupDocs.Metadata, importe la clase y abra un archivo de diagrama:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Con la biblioteca inicializada, ahora puede modificar cualquier propiedad incorporada, incluida la hora de creación.

## Guía de implementación
### Cómo cambiar la hora de creación en archivos de diagramas
En esta sección recorreremos cada paso necesario para **cambiar la hora de creación** y actualizar otras propiedades comunes como autor, empresa y categoría.

#### Paso 1: Cargar el documento del diagrama
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```
*Explicación:* El constructor `Metadata` recibe la ruta a su archivo de diagrama. El bloque try‑with‑resources garantiza que el archivo se cierre correctamente después de la operación.

#### Paso 2: Acceder al paquete raíz
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```
*Explicación:* El paquete raíz le brinda acceso directo a todos los campos de metadatos incorporados para el diagrama.

#### Paso 3: Establecer la propiedad Creador
```java
root.getDocumentProperties().setCreator("test author");
```
*Explicación:* Asigna un nuevo nombre de autor. Reemplace `"test author"` con el creador real.

#### Paso 4: **Cambiar la hora de creación**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*Explicación:* Esta línea **cambia la hora de creación** a la fecha y hora actuales del sistema. También puede proporcionar una instancia `Date` específica si necesita una marca de tiempo personalizada.

#### Paso 5: Definir la información de la empresa
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*Explicación:* Almacena el nombre de la empresa asociado al diagrama—útil para el seguimiento empresarial.

#### Paso 6: Establecer la categoría del documento
```java
root.getDocumentProperties().setCategory("test category");
```
*Explicación:* Categoriza el archivo, ayudándole a **actualizar la categoría del diagrama** de manera consistente en todo su repositorio.

#### Paso 7: Añadir palabras clave
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*Explicación:* Las palabras clave mejoran la capacidad de búsqueda; puede enumerar cualquier término relevante al contenido del diagrama.

#### Paso 8: Guardar cambios
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*Explicación:* Persiste Verifique para los directorios de entrada y salida.  
- **Formato de fecha inválido:** Use objetos `java.util.Date` o `java.time` compatibles con la API.  

## Aplicaciones prácticas
1. **Automatización del archivado de documentos** – Al mover diagramas antiguos a un archivo, cambie automáticamente la **hora de creación** a la fecha de archivado y establezca una categoría uniforme.  
2. **Integración con control de versiones** – Mantenga las marcas de tiempo sincronizadas con los commits de Git actualizando la hora de creación durante cada lanzamiento.  
3. **Estandarización DMS empresarial** – Implemente una política a nivel de empresa para autor, empresa y palabras clave en todos los recursos de diagramas.

## Consideraciones de rendimiento
- **Procesamiento por lotes:** Encierre los pasos anteriores dentro de un bucle para manejar decenas de archivos en una sola ejecución.  
- **Gestión de memoria:** Libere cada instancia `Metadata` rápidamente (el bloque try‑with‑resources lo hace automáticamente).  
- **Ejecución asíncrona:** Para lotes grandes, considere `CompletableFuture` para ejecutar actualizaciones en paralelo sin bloquear el hilo principal.

## Conclusión
Ahora sabe cómo **cambiar la hora de creación** y actualizar otras propiedades de metadatos incorporadas para documentos de diagramas usando GroupDocs.Metadata en Java. Al automatizar estos pasos, puede mantener documentación consistente, fácil de buscar y conforme en toda su organización.

**Próximos pasos**
- Experimente con otros formatos de archivo compatibles con GroupDocs.Metadata (PDF, DOCX, etc.).  
- Integre el código en una canalización CI/CD para aplicar estándares de metadatos en cada compilación.

¿Listo para probarlo? Diríjase a [Lanzamientos de GroupDocs.Metadata para Java](https://releases.groupdocs.com/metadata/java/) y comience a implementar su propia automatización de metadatos hoy.

---

**Última actualización:** 2026-01-19  
**Probado con:** GroupDocs.Metadata 24.12  
**Autor:** GroupDocs  

## Preguntas frecuentes

**P: ¿Puedo usar este enfoque con otros formatos de diagrama como VSDX?**  
R: Sí, la misma API funciona para todos los formatos de diagrama compatibles con GroupDocs.Metadata.

**P: ¿Necesito una licencia para compilaciones de desarrollo?**  
R: Una prueba gratuita es suficiente para desarrollo y pruebas; se requiere una licencia completa para despliegues en producción.

**P: ¿Cómo puedo actualizar múltiples propiedades en una sola llamada?**  
R: Establezca cada propiedad en el objeto `DocumentProperties` antes de llamar a `metadata.save(...)`; la biblioteca las escribe todas a la vez.

**P: ¿Es seguro sobrescribir el archivo original?**  
R: Se recomienda el originalP: ¿Qué pasa si necesito establecer una fecha de creación personalizada en lugar de la hora actual?**  
R: Cree una `java.util.Date` (o instancia `java.time`) con la marca de tiempo deseada y pásela a `setTimeCreated`.