---
date: '2026-08-20'
description: Aprenda a extrair metadados XMP em Java usando o GroupDocs.Metadata.
  Este guia mostra como extrair metadados XMP básicos, Dublin Core e Photoshop.
keywords:
- extract XMP metadata
- GroupDocs.Metadata for Java
- Java metadata management
lastmod: '2026-08-20'
og_description: Aprenda a extrair metadados XMP em Java usando o GroupDocs.Metadata.
  Este tutorial cobre a extração básica, Dublin Core e Photoshop XMP com exemplos
  de código práticos.
og_image_alt: Guide showing Java code that extracts XMP metadata using GroupDocs.Metadata
og_title: Como extrair metadados XMP com GroupDocs.Metadata para Java
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
title: Como extrair metadados XMP com GroupDocs.Metadata para Java
type: docs
url: /pt/java/metadata-standards/extract-xmp-metadata-groupdocs-metadata-java/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Como extrair metadados XMP com GroupDocs.Metadata para Java

Em fluxos de trabalho digitais modernos, **como extrair XMP** metadados de forma rápida e confiável pode fazer a diferença entre uma biblioteca de ativos pesquisável e um depósito caótico de arquivos. Este tutorial orienta você em cada passo — configurando a biblioteca, carregando arquivos e extraindo pacotes XMP básicos, Dublin Core e específicos do Photoshop — para que você possa integrar metadados ricos em suas aplicações Java hoje.

## Respostas rápidas
- **Qual biblioteca lida com XMP em Java?** GroupDocs.Metadata for Java.
- **Versão mínima do Java?** JDK 8 ou posterior.
- **Posso ler arquivos PNG e JPEG?** Sim, ambos são suportados nativamente.
- **É necessária uma licença para produção?** Sim, é necessária uma licença completa ou temporária.
- **Onde posso encontrar a referência da API?** No site oficial da documentação do GroupDocs.Metadata.

## O que são metadados XMP?
XMP (Extensible Metadata Platform) é um formato padrão ISO para incorporar metadados estruturados diretamente dentro de arquivos de mídia. Ele permite interoperabilidade entre aplicações e armazenamento persistente de dados sem alterar o conteúdo original. Ao armazenar informações como criador, direitos autorais, configurações da câmera e tags personalizadas dentro do arquivo, o XMP garante que os metadados viajem com o ativo onde quer que ele vá, simplificando a catalogação e a pesquisa em sistemas diversos.

## Por que usar GroupDocs.Metadata para Java?
GroupDocs.Metadata suporta **mais de 30 formatos de arquivo** (incluindo PNG, JPEG, TIFF e PSD) e pode processar arquivos de até **2 GB** sem carregar todo o documento na memória, proporcionando uma **redução de 30 % no uso de CPU** em comparação com analisadores genéricos. Isso o torna ideal para sistemas de gerenciamento de ativos digitais (DAM) em grande escala.

## Pré-requisitos

- **Java Development Kit (JDK) 8+** instalado.
- **Maven** para gerenciamento de dependências.
- Familiaridade básica com Java I/O e programação orientada a objetos.

## Como configurar GroupDocs.Metadata para Java?
Para começar, adicione o repositório GroupDocs e a dependência da biblioteca ao seu `pom.xml` do Maven. Isso garante que o Maven possa resolver os artefatos e mantê‑los atualizados automaticamente, simplificando futuras atualizações e correções de segurança. Após atualizar o `pom.xml`, execute `mvn clean install` para baixar os JARs necessários e verificar se a configuração foi bem‑sucedida.

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

Se preferir uma abordagem manual, baixe o JAR mais recente da página oficial de lançamentos:

[GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)

### Aquisição de licença
- **Teste gratuito** – avalie todos os recursos por 30 dias.
- **Licença temporária** – use durante o desenvolvimento sem restrições.
- **Licença completa** – necessária para implantações em produção.

## Inicialização básica

`Metadata` é o ponto de entrada para todas as operações. Ele representa um único arquivo e fornece acesso aos seus pacotes XMP incorporados.

```java
// ```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PngWithXmp.png");
// Always ensure resources are freed up after usage
metadata.dispose();
```
```

## Como extrair metadados XMP básicos?

Carregue a imagem, abra seu pacote XMP e leia propriedades comuns como ferramenta de criação e timestamps.

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

## Como extrair metadados XMP Dublin Core?

O esquema Dublin Core armazena elementos descritivos padronizados como título, criador e assunto. Acesse‑o através da classe `DublinCorePackage`.

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

## Como extrair metadados XMP específicos do Photoshop?

O Photoshop incorpora informações adicionais como modo de cor, resolução e contagem de camadas. Recupere esses valores via `PhotoshopPackage`.

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

## Aplicações práticas

- **Gerenciamento de ativos digitais** – etiquetar e pesquisar imagens por criador, direitos autorais ou configurações da câmera.
- **Pipelines de publicação automatizada** – injetar ou modificar XMP antes de publicar em galerias web.
- **Analytics** – agregar metadados em milhares de arquivos para descobrir tendências de uso.

## Considerações de desempenho

A classe `Metadata` fornece acesso aos metadados e pacotes XMP de um arquivo. Libere os objetos `Metadata` assim que terminar a leitura para liberar recursos nativos. `LoadOptions.LAZY` indica à biblioteca que carregue os metadados de forma preguiçosa, reduzindo o uso de memória. Transmita arquivos grandes usando `Metadata.load(InputStream)` para manter o uso de heap baixo. Reutilize uma única instância de `Metadata` ao ler muitos arquivos pequenos para reduzir a sobrecarga de criação de objetos.

## Armadilhas comuns e solução de problemas

| Sintoma | Causa provável | Correção |
|---|---|---|
| `NullPointerException` ao acessar XMP | O arquivo não possui pacote XMP | Chame `metadata.getXmpPackage()` e verifique se é `null` antes de ler. O método `getXmpPackage()` retorna o objeto do pacote XMP, ou null se não existir. |
| Processamento lento em imagens de 500 MB | Carregando todo o arquivo na memória | Use `metadata.load(InputStream)` e habilite `metadata.setLoadOptions(LoadOptions.LAZY)`. |
| Campos do Photoshop ausentes | Imagem salva sem informações de camada do Photoshop | Verifique se o arquivo de origem foi exportado do Photoshop com “Save XMP” habilitado |

## Perguntas frequentes

**Q: Posso extrair XMP de arquivos PDF?**  
A: Sim, o GroupDocs.Metadata suporta pacotes XMP de PDF via a mesma API `Metadata`.

**Q: O que acontece se o formato de arquivo não for suportado?**  
A: A biblioteca lança uma `UnsupportedFormatException`; capture‑a e recorra a um manipulador genérico.

**Q: É possível modificar metadados XMP e salvá‑los novamente?**  
A: Absolutamente. Após alterar as propriedades, chame `metadata.save("output.png")` para persistir as atualizações.

**Q: A biblioteca funciona no Android?**  
A: A biblioteca Java core é compatível com Android API 24+, mas você deve incluir o artefato específico `android`.

**Q: Como lidar com imagens criptografadas?**  
A: Forneça a senha de descriptografia ao construtor `Metadata`: `new Metadata(filePath, "password")`.

## Conclusão

Agora você tem um guia completo e pronto para produção sobre **como extrair XMP** metadados usando GroupDocs.Metadata para Java. Seguindo os passos acima, você pode enriquecer suas aplicações com metadados pesquisáveis e compatíveis com padrões, e desbloquear poderosas capacidades de gerenciamento de ativos.

## Próximos passos

Aprofunde-se no conjunto completo de recursos revisando a documentação oficial e experimentando outros padrões de metadados como IPTC e EXIF.

[documentation](https://docs.groupdocs.com/metadata/java/)

---

**Última atualização:** 2026-08-20  
**Testado com:** GroupDocs.Metadata for Java 23.11  
**Autor:** GroupDocs  

- [Documentação](https://docs.groupdocs.com/metadata/java/)
- [Referência da API](https://reference.groupdocs.com/metadata/java/)
- [Download](https://releases.groupdocs.com/metadata/java/)
- [Repositório no GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java)
- [Fórum de Suporte Gratuito](https://forum.groupdocs.com/c/metadata/)
- [Licença Temporária](https://purchase.groupdocs.com/temporary-license/)

## Tutoriais Relacionados

- [Extrair Metadados Dublin Core Epub Groupdocs Java](/metadata/java/metadata-standards/extract-dublin-core-metadata-epub-groupdocs-java/)
- [Extrair Tag de Software EXIF em Java: Guia Completo Usando GroupDocs.Metadata](/metadata/java/metadata-standards/master-exif-data-java-groupdocs-metadata/)
- [Como Extrair Metadados com GroupDocs.Metadata para Java – Tutoriais e Exemplos](/metadata/java/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}