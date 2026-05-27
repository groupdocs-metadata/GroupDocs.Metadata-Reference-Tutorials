---
date: '2026-05-27'
description: Aprenda como definir o CreatedTime de pptx em Java usando a dependência
  Maven do GroupDocs para atualizar os metadados do PowerPoint, incluindo como alterar
  a data de criação do PPTX.
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
title: Definir CreatedTime de PPTX em Java com a dependência Maven do GroupDocs
type: docs
url: /pt/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Definir CreatedTime do PPTX em Java com GroupDocs.Metadata

Metadados precisos são essenciais para conformidade e descoberta em fluxos de trabalho modernos de documentos. Com **GroupDocs.Metadata** você pode programaticamente **definir CreatedTime do PPTX em Java**, permitindo que você **altere a data de criação do PPTX** juntamente com outras propriedades incorporadas, como autor ou empresa. Este tutorial orienta você na configuração do Maven, inicialização da API, atualização de metadados e salvamento da apresentação modificada — tudo com código claro e pronto para produção.

## Respostas Rápidas
- **Qual biblioteca atualiza metadados do PowerPoint em Java?** GroupDocs.Metadata via a dependência Maven do GroupDocs.  
- **Posso definir a propriedade CreatedTime do PPTX?** Sim—use `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **É necessária uma licença para produção?** Uma avaliação funciona para testes; uma licença comercial é obrigatória para implantações em produção.  
- **Qual ferramenta de build o exemplo usa?** Maven (você também pode baixar o JAR manualmente).  
- **A API suporta Java 8 e versões mais recentes?** Absolutamente—GroupDocs.Metadata tem como alvo Java 8+.

## O que é a Dependência Maven do GroupDocs?
A **dependência Maven do GroupDocs** é uma entrada de repositório compatível com Maven que traz a biblioteca mais recente do GroupDocs.Metadata para o seu projeto Java. Ela simplifica o gerenciamento de dependências ao resolver automaticamente bibliotecas transitivas, garante que você sempre use a versão mais recente e segura, e elimina a necessidade de downloads manuais de JARs ou rastreamento de versões.

## Por que usar GroupDocs.Metadata para alterar a data de criação do PPTX?
GroupDocs.Metadata permite atualizações automatizadas e prontas para lote de carimbos de data/hora de criação do PPTX, garantindo que cada apresentação esteja em conformidade com políticas corporativas ou requisitos legais. Ao definir programaticamente a propriedade CreatedTime, você evita edições manuais, reduz erros humanos e pode integrar a mudança em pipelines CI/CD ou scripts de migração para gerenciamento de documentos sem atritos.

## Pré-requisitos
- Java 8 ou superior instalado.  
- Uma IDE como IntelliJ IDEA ou Eclipse.  
- Maven para gerenciamento de dependências.  
- Acesso a uma avaliação do GroupDocs ou licença adquirida.

## Como definir CreatedTime do PPTX em Java?

A classe `Metadata` representa um documento e fornece acesso às suas propriedades de metadados.

Carregue seu arquivo PowerPoint com `new Metadata("presentation.pptx")`, recupere o pacote raiz, chame `setCreatedTime` com o `java.util.Date` desejado e, finalmente, invoque `save` para gravar as alterações. Esse fluxo de ponta a ponta modifica a data de criação enquanto preserva todo o conteúdo dos slides e outras propriedades.

### Configuração do Maven
Adicione o repositório GroupDocs e a dependência de metadata ao seu `pom.xml`:

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

> **Dica:** Manter o número da versão atualizado garante que você se beneficie das correções de bugs e melhorias de desempenho mais recentes.

### Download Direto (se preferir não usar Maven)

Alternativamente, baixe o JAR mais recente em [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Aquisição de Licença

Comece com uma avaliação gratuita ou solicite uma licença temporária para avaliar o GroupDocs.Metadata. Para uso em produção, adquira uma licença através do [site oficial da GroupDocs](https://purchase.groupdocs.com/temporary-license/).

## Inicialização e Configuração Básicas

Uma vez que a biblioteca esteja no classpath, você pode criar uma instância `Metadata` que aponta para seu arquivo PowerPoint:

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

Este código abre a apresentação em um bloco try‑with‑resources, garantindo que o manipulador de arquivo seja liberado automaticamente.

## Guia passo a passo para atualizar metadados incorporados

### Etapa 1: Carregar o documento de apresentação

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Carregar o arquivo estabelece uma conexão que permite ler ou escrever metadados.

### Etapa 2: Acessar o pacote raiz da apresentação

O objeto `root` fornece acesso ao pacote central da apresentação e às suas propriedades incorporadas.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

O objeto `root` expõe todas as propriedades de documento incorporadas.

### Etapa 3: Atualizar propriedades de documento incorporadas (incluindo data de criação)

`setCreatedTime` atribui um novo carimbo de data/hora de criação ao documento.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Aqui demonstramos como **definir CreatedTime do PPTX** atribuindo um novo objeto `Date` a `CreatedTime`. Substitua `new Date()` por qualquer carimbo de data/hora específico que precisar.

### Etapa 4: Salvar a apresentação atualizada

`save` grava os metadados modificados de volta em um arquivo.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

A chamada `save` grava os metadados modificados em um novo arquivo PowerPoint, deixando o original intacto.

## Dicas de solução de problemas
- **Arquivo não encontrado:** Verifique novamente o caminho de entrada e as permissões do arquivo.  
- **Incompatibilidade de versão:** Certifique‑se de que a versão `groupdocs-metadata` corresponde ao seu runtime Java.  
- **Propriedade não está sendo atualizada:** Verifique se está chamando `setCreatedTime` (ou o setter relevante) antes de invocar `save`.

## Aplicações práticas

1. **Branding corporativo:** Injete automaticamente o nome e a categoria corretos da empresa em todos os decks de slides antes da distribuição.  
2. **Sistemas de gerenciamento de documentos:** Enriquecer arquivos PPTX com metadados pesquisáveis para recuperação mais rápida.  
3. **Recursos educacionais:** Mantenha as informações de autor e currículo atualizadas em todos os slides de aula.  
4. **Rastreamento de colaboração:** Registre os nomes dos colaboradores para manter a responsabilidade.  
5. **Integração CMS:** Sincronize alterações de metadados com sua plataforma de gerenciamento de conteúdo em tempo real.

## Considerações de desempenho
- **Processamento em lote:** Percorra uma lista de arquivos e reutilize uma única instância `Metadata` sempre que possível.  
- **Gerenciamento de memória:** Sempre use try‑with‑resources (como mostrado) para liberar recursos nativos prontamente.  
- **Estruturas de dados eficientes:** Armazene atualizações de metadados em um mapa antes de aplicá‑las para reduzir chamadas repetitivas.

## Perguntas Frequentes

**Q: Qual é o objetivo principal da dependência Maven do GroupDocs?**  
A: Ela fornece uma maneira conveniente de incluir a biblioteca mais recente do GroupDocs.Metadata em projetos Java baseados em Maven.

**Q: Como posso definir a data de criação do PPTX sem afetar outras propriedades?**  
A: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` antes de chamar `metadata.save()`.

**Q: Preciso de uma licença para executar este código em desenvolvimento?**  
A: Uma licença de avaliação temporária é suficiente para desenvolvimento e testes; uma licença completa é necessária para produção.

**Q: Posso atualizar campos de metadados personalizados também?**  
A: Sim—GroupDocs.Metadata suporta tanto propriedades incorporadas quanto personalizadas através de sua API.

**Q: Existe uma maneira de reverter as alterações se eu cometer um erro?**  
A: Mantenha uma cópia do arquivo original ou leia os valores de propriedade existentes antes de sobrescrevê‑los, então restaure se necessário.

## Recursos

- [Documentation](https://docs.groupdocs.com/metadata/java/)
- [API Reference](https://apireference.groupdocs.com/metadata/java/)

---

**Last Updated:** 2026-05-27  
**Tested With:** GroupDocs.Metadata 24.12 for Java  
**Author:** GroupDocs  

## Tutoriais Relacionados

- [Update Custom Metadata in PowerPoint Using GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [How to Update Word Document Metadata Using GroupDocs.Metadata Java: A Complete Guide](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Efficiently Update PDF Metadata with GroupDocs.Metadata in Java for Document Management](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)