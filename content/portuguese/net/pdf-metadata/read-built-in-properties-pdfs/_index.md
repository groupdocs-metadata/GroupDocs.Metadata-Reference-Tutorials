---
title: Leia propriedades integradas de PDFs em .NET
linktitle: Leia propriedades integradas de PDFs em .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda como ler metadados PDF em .NET usando GroupDocs.Metadata. Acesse nomes de autores, datas de criação, assuntos e muito mais com código C#.
weight: 10
url: /pt/net/pdf-metadata/read-built-in-properties-pdfs/
type: docs
---
# Leia propriedades integradas de PDFs em .NET

## Introdução
Neste tutorial, exploraremos como aproveitar GroupDocs.Metadata for .NET para ler propriedades integradas de arquivos PDF. GroupDocs.Metadata é uma biblioteca poderosa que permite aos desenvolvedores trabalhar com metadados associados a vários formatos de documentos, incluindo PDFs, documentos do Microsoft Office, imagens e muito mais. Ao usar esta biblioteca, você pode acessar e manipular facilmente atributos de metadados incorporados em arquivos PDF, como nomes de autores, datas de criação, assuntos e muito mais.
## Pré-requisitos
Antes de mergulhar neste tutorial, certifique-se de ter os seguintes pré-requisitos:
- Visual Studio: certifique-se de ter o Visual Studio instalado em sua máquina.
-  GroupDocs.Metadata for .NET: Baixe e instale GroupDocs.Metadata for .NET em[aqui](https://releases.groupdocs.com/metadata/net/).
- Conhecimento básico de C#: Familiaridade com a linguagem de programação C# e o framework .NET.

## Importar namespaces
Comece adicionando os namespaces necessários ao seu projeto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Passo 1: Carregar Metadados PDF
Primeiro, carregue o arquivo PDF e extraia seus metadados usando GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.pdf"))
{
    // Acesse o pacote raiz do arquivo PDF
    var root = metadata.GetRootPackage<PdfRootPackage>();
    // Recuperar e exibir propriedades integradas
    Console.WriteLine("Author: " + root.DocumentProperties.Author);
    Console.WriteLine("Created Date: " + root.DocumentProperties.CreatedDate);
    Console.WriteLine("Subject: " + root.DocumentProperties.Subject);
    Console.WriteLine("Producer: " + root.DocumentProperties.Producer);
    Console.WriteLine("Keywords: " + root.DocumentProperties.Keywords);
    // Propriedades adicionais podem ser acessadas de forma semelhante
    // ...
}
```
Além da leitura de metadados, GroupDocs.Metadata permite operações avançadas como edição, remoção ou adição de novas propriedades de metadados a arquivos PDF de forma programática. Essa flexibilidade permite o gerenciamento abrangente de metadados de documentos em seus aplicativos .NET.
## Conclusão
Neste tutorial, abordamos como utilizar GroupDocs.Metadata for .NET para extrair propriedades integradas de arquivos PDF usando C#. Ao integrar esta biblioteca em seus projetos, você pode lidar perfeitamente com operações de metadados de documentos, fornecendo recursos aprimorados de gerenciamento de documentos.

## Perguntas frequentes
### O GroupDocs.Metadata pode funcionar com outros formatos de documentos?
Sim, GroupDocs.Metadata oferece suporte a vários formatos de documento, como DOCX, XLSX, PPTX, PDF, JPG, PNG e muito mais.
### Existe uma avaliação gratuita disponível para GroupDocs.Metadata?
Sim, você pode acessar uma avaliação gratuita do GroupDocs.Metadata em[aqui](https://releases.groupdocs.com/).
### Como posso modificar propriedades de metadados usando GroupDocs.Metadata?
Você pode modificar propriedades de metadados programaticamente acessando o pacote de documentos correspondente e definindo novos valores.
### O GroupDocs.Metadata oferece suporte ao .NET Core?
Sim, GroupDocs.Metadata é compatível com .NET Framework e .NET Core.
### Onde posso encontrar suporte ou fazer perguntas relacionadas ao GroupDocs.Metadata?
 Para suporte e discussões, visite o[Fórum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).