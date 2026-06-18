---
date: '2026-06-12'
description: Aprenda como criar pacotes XMP personalizados, gerenciar metadados de
  arquivos e adicionar metadados personalizados a PDFs usando GroupDocs.Metadata para
  Java.
keywords:
- create custom xmp package
- manage file metadata
- add custom metadata pdf
schemas:
- author: GroupDocs
  dateModified: '2026-06-12'
  description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  headline: Create Custom XMP Package with GroupDocs.Metadata for Java
  type: TechArticle
- description: Learn how to create custom XMP packages, manage file metadata and add
    custom metadata to PDFs using GroupDocs.Metadata for Java.
  name: Create Custom XMP Package with GroupDocs.Metadata for Java
  steps:
  - name: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
    text: '**Digital Asset Management** – Embed licensing and usage rights directly
      into images and PDFs.'
  - name: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
    text: '**Content Personalization** – Attach user‑specific identifiers to documents
      for targeted delivery.'
  - name: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
    text: '**Regulatory Compliance** – Store audit trails and retention policies inside
      the file itself, simplifying governance audits.'
  type: HowTo
- questions:
  - answer: Over 50 formats—including JPEG, PNG, PDF, DOCX, and TIFF—support XMP packet
      injection. See the full list in the [GroupDocs.Metadata documentation](https://docs.groupdocs.com/metadata/java/).
    question: What file formats support custom XMP packages?
  - answer: Yes, the library lets you read, modify, and delete any XMP property using
      the `IXmp` interface.
    question: Can I edit existing XMP metadata with GroupDocs.Metadata?
  - answer: For unsupported formats, consider wrapping the file in a container that
      does support XMP (e.g., converting to PDF) or using an alternative metadata
      store.
    question: How do I handle files that don’t natively support XMP?
  - answer: Absolutely—GroupDocs.Metadata is tested against Java 8 through Java 21,
      including all LTS releases.
    question: Is the library compatible with Java 17 LTS?
  - answer: Common pitfalls include using an incorrect namespace URI, exceeding the
      maximum packet size (≈ 2 MB), or attempting to write to a read‑only file. Ensure
      proper permissions and validate your XML schema before saving.
    question: What are typical errors when adding XMP packages?
  type: FAQPage
title: Criar Pacote XMP Personalizado com GroupDocs.Metadata para Java
type: docs
url: /pt/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/
weight: 1
---

# Criar Pacote XMP Personalizado com GroupDocs.Metadata para Java

Em fluxos de trabalho digitais modernos, **criar pacotes XMP personalizados** é essencial para incorporar metadados ricos e pesquisáveis diretamente dentro dos arquivos. Seja manipulando imagens, PDFs ou ativos multimídia, o GroupDocs.Metadata para Java oferece uma maneira confiável de **gerenciar metadados de arquivos** e **adicionar metadados personalizados a PDFs** sem bancos de dados externos. Neste tutorial, percorreremos todo o processo — desde a configuração da biblioteca até a incorporação de um pacote XMP totalmente funcional — para que você possa começar a enriquecer seus documentos hoje.

## Respostas Rápidas
- **Qual é o primeiro passo?** Add GroupDocs.Metadata as a Maven dependency or download the JAR.  
- **Quantas linhas de código?** Only three concise statements are needed to create and attach a custom XMP package.  
- **Quais formatos de arquivo são suportados?** Over 50 formats, including JPEG, PNG, PDF, DOCX, and TIFF.  
- **Preciso de uma licença?** A free trial works for development; a permanent license is required for production.  
- **Posso usar isso com Java 11+?** Yes, the library is compatible with Java 8 through Java 21.

## O que é “criar pacote xmp personalizado”?
*Criar um pacote XMP personalizado* significa construir um pacote XMP que contém campos de metadados definidos pelo usuário e incorporá‑lo em um arquivo suportado. Este pacote é armazenado dentro da seção XMP do arquivo, tornando os metadados portáteis e pesquisáveis por qualquer aplicação compatível com XMP.

## Por que usar GroupDocs.Metadata para Java para gerenciar metadados de arquivos?
GroupDocs.Metadata suporta **mais de 50 formatos de entrada e saída** e pode processar arquivos de até **2 GB** sem carregar o documento inteiro na memória, o que reduz o consumo de RAM em até **80 %** em ativos grandes. A API também fornece operações thread‑safe, permitindo processamento em lote de alta vazão em ambientes corporativos.

## Pré‑requisitos
- **Java Development Kit** 8 ou mais recente (Java 11+ recomendado).  
- Uma IDE como **IntelliJ IDEA** ou **Eclipse**.  
- Maven instalado para gerenciamento de dependências.  
- Compreensão básica de classes Java e conceitos de metadados.

## Configurando GroupDocs.Metadata para Java
### Configuração Maven
Adicione a seguinte dependência ao seu arquivo `pom.xml` para incluir o GroupDocs.Metadata:

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

Consulte a [Documentação da API](https://reference.groupdocs.com/metadata/java/) para obter as assinaturas completas dos métodos.  
Para referência detalhada da API, veja a [Documentação Java do GroupDocs.Metadata](https://docs.groupdocs.com/metadata/java/).

**Download Direto** – Se preferir configuração manual, obtenha o JAR mais recente em [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/). Você também pode visualizar a página de [Últimas Versões](https://releases.groupdocs.com/metadata/java/) para detalhes do changelog.

### Aquisição de Licença
- **Teste Gratuito** – Avalie todos os recursos sem custo.  
- **Licença Temporária** – Obtenha uma chave de tempo limitado para testes de desenvolvimento. ([Obter uma Licença Temporária](https://purchase.groupdocs.com/temporary-license/))  
- **Compra** – Adquira uma licença perpétua para uso em produção.

O código‑fonte e exemplos estão disponíveis no [GroupDocs Metadata no GitHub](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java).

## Guia de Implementação
A seguir, um passo a passo que mostra exatamente como **criar um pacote XMP personalizado** e incorporá‑lo em um arquivo.

### Como criar um pacote XMP personalizado e anexá‑lo a um arquivo?
Carregue seu arquivo alvo com a classe `Metadata`, construa um `XmpPacketWrapper`, defina seus campos XMP personalizados e, finalmente, salve as alterações. Esse fluxo de ponta a ponta requer apenas três chamadas de método após a inicialização. O processo garante que o pacote XMP seja incorporado corretamente e que o arquivo permaneça totalmente funcional em todas as aplicações suportadas.

### Inicializar o Objeto Metadata
`Metadata` é a classe principal que representa um arquivo e fornece métodos para ler e escrever seus metadados.  
```java
Metadata metadata = new Metadata("sample.pdf");
```

### Criar um Novo XmpPacketWrapper
`XmpPacketWrapper` funciona como um contêiner para um ou mais pacotes XMP, permitindo atualizações em lote antes de salvar.  
```java
XmpPacketWrapper xmpWrapper = new XmpPacketWrapper();
```

### Definir e Configurar o Pacote XMP Personalizado
A interface `IXmp` permite definir esquemas XMP personalizados e definir valores de propriedades dentro do pacote.  
```java
IXmp customXmp = xmpWrapper.createPackage("http://mycompany.com/custom");
customXmp.setProperty("Creator", "John Doe");
customXmp.setProperty("Project", "Metadata Migration");
customXmp.setProperty("Version", "1.0");
```

### Salvar os Metadados Atualizados
`Metadata.save()` grava os metadados modificados de volta ao arquivo original, persistindo quaisquer pacotes XMP adicionados.  
```java
metadata.getXmp().addPacket(xmpWrapper);
metadata.save();
```

#### Explicação dos Componentes Principais
- **Objeto Metadata** – Centro central para acessar os metadados de um arquivo.  
- **Interface IXmp** – Fornece métodos para ler/gravar campos específicos de XMP.  
- **XmpPacketWrapper** – Contém um ou mais pacotes XMP, permitindo atualizações em lote.  
- **Pacote XMP Personalizado** – Seu esquema definido pelo usuário que armazena informações adicionais.

## Problemas Comuns e Soluções
- **Formato de Arquivo Não Suportado** – Verifique se o tipo de arquivo alvo aparece na lista oficial de formatos (mais de 50 formatos suportados).  
- **Licença Não Encontrada** – Certifique‑se de que o arquivo de licença está colocado no diretório raiz da aplicação ou definido via `License.setLicense("license_path")`.  
- **Exaustão de Memória em Arquivos Grandes** – Use `metadata.setLoadOptions(LoadOptions.lazyLoad())` para processar metadados de forma preguiçosa e manter o uso de memória baixo.

Para ajuda adicional, visite o fórum [Suporte GroupDocs](https://forum.groupdocs.com/c/metadata/).

## Aplicações Práticas
1. **Gerenciamento de Ativos Digitais** – Incorporar licenças e direitos de uso diretamente em imagens e PDFs.  
2. **Personalização de Conteúdo** – Anexar identificadores específicos de usuário a documentos para entrega direcionada.  
3. **Conformidade Regulatória** – Armazenar trilhas de auditoria e políticas de retenção dentro do próprio arquivo, simplificando auditorias de governança.

## Considerações de Desempenho
- **Otimização de Recursos** – Processar metadados em modo streaming para manter o uso de RAM abaixo de **100 MB** para arquivos maiores que **1 GB**.  
- **Atualizações de Versão** – Mantenha a biblioteca atualizada; cada lançamento principal adiciona suporte a novos formatos e melhora a velocidade de processamento em até **30 %**.

## Conclusão
Seguindo este guia, você agora sabe como **criar pacotes XMP personalizados** com o GroupDocs.Metadata para Java, permitindo que você **gerencie metadados de arquivos** de forma eficiente e **adicione metadados personalizados a PDFs** e muitos outros formatos. Experimente esquemas XMP adicionais, integre o fluxo de trabalho ao seu pipeline de CI ou combine‑o com o GroupDocs.Viewer para processamento de documentos de ponta a ponta.

## Perguntas Frequentes

**Q: Quais formatos de arquivo suportam pacotes XMP personalizados?**  
A: Mais de 50 formatos — incluindo JPEG, PNG, PDF, DOCX e TIFF — suportam injeção de pacotes XMP. Veja a lista completa na [documentação do GroupDocs.Metadata](https://docs.groupdocs.com/metadata/java/).

**Q: Posso editar metadados XMP existentes com o GroupDocs.Metadata?**  
A: Sim, a biblioteca permite ler, modificar e excluir qualquer propriedade XMP usando a interface `IXmp`.

**Q: Como lidar com arquivos que não suportam XMP nativamente?**  
A: Para formatos não suportados, considere envolver o arquivo em um contêiner que suporte XMP (por exemplo, convertendo para PDF) ou usar um armazenamento de metadados alternativo.

**Q: A biblioteca é compatível com Java 17 LTS?**  
A: Absolutamente — o GroupDocs.Metadata é testado com Java 8 até Java 21, incluindo todas as versões LTS.

**Q: Quais são os erros típicos ao adicionar pacotes XMP?**  
A: Armadilhas comuns incluem usar um URI de namespace incorreto, exceder o tamanho máximo do pacote (≈ 2 MB) ou tentar gravar em um arquivo somente‑leitura. Garanta permissões adequadas e valide seu esquema XML antes de salvar.

---

**Última Atualização:** 2026-06-12  
**Testado com:** GroupDocs.Metadata 23.12 for Java  
**Autor:** GroupDocs  

---

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

```java
import com.groupdocs.metadata.Metadata;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Proceed with operations on metadata
}
```

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.IXmp;

try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY")) {
    // Get the root XMP package from the metadata
    IXmp root = (IXmp) metadata.getRootPackage();
```

```java
import com.groupdocs.metadata.core.XmpPacketWrapper;

// Create a new XmpPacketWrapper to hold custom packages
XmpPacketWrapper packet = new XmpPacketWrapper();
```

```java
import com.groupdocs.metadata.core.XmpPackage;
import com.groupdocs.metadata.core.XmpArray;
import com.groupdocs.metadata.core.XmpArrayType;

// Define and configure the custom XMP package
custom = new XmpPackage("gd", "GroupDocs Custom Package");
custom.set("CustomProperty", "CustomValue");

// Add it to the packet
packet.addPackage(custom);
```

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```

## Tutoriais Relacionados

- [Adicionar Metadados XMP Personalizados a Arquivos com GroupDocs.Metadata Java: Um Guia Abrangente](/metadata/java/metadata-standards/add-custom-xmp-metadata-groupdocs-java/)
- [Como Adicionar Metadados a PDF com GroupDocs.Metadata para Java – Guia do Desenvolvedor](/metadata/java/document-formats/master-pdf-metadata-groupdocs-java/)
- [Como Extrair Metadados Personalizados de PDFs Usando GroupDocs.Metadata em Java: Um Guia Abrangente](/metadata/java/document-formats/extract-custom-metadata-groupdocs-metadata-java/)