---
title: Atualizar propriedades integradas em PDFs usando .NET
linktitle: Atualizar propriedades integradas em PDFs usando .NET
second_title: API GroupDocs.Metadata .NET
description: Saiba como atualizar propriedades de documentos PDF usando C# e GroupDocs.Metadata for .NET. Modifique autor, título, palavras-chave e muito mais de forma programática.
weight: 15
url: /pt/net/pdf-metadata/update-built-in-properties-pdfs/
---

# Atualizar propriedades integradas em PDFs usando .NET

## Introdução
Neste tutorial, aprenderemos como usar GroupDocs.Metadata for .NET para atualizar propriedades integradas de documentos PDF. Esta biblioteca fornece um poderoso conjunto de ferramentas para manipular metadados em vários formatos de documentos. Percorreremos as etapas necessárias para modificar propriedades como autor, título, data de criação, palavras-chave, criador e produtor em um arquivo PDF usando C#.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte em vigor:
-  Biblioteca GroupDocs.Metadata for .NET: Baixe a biblioteca em[aqui](https://releases.groupdocs.com/metadata/net/).
- Visual Studio: instale o Visual Studio para escrever e executar o código C#.
- Compreensão básica de C#: Recomenda-se familiaridade com a linguagem de programação C#.

## Importar namespaces
Comece incluindo os namespaces necessários em seu projeto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Etapa 1: inicializar objeto de metadados
 Comece inicializando um`Metadata`objeto com o caminho para o seu arquivo PDF:
```csharp
using (Metadata metadata = new Metadata("Your Input File Path"))
{
    // Seu código irá aqui
}
```
## Passo 2: Acesse o pacote raiz do PDF
 A seguir, recupere o pacote raiz especificamente para PDF usando`GetRootPackage<PdfRootPackage>()`:
```csharp
var root = metadata.GetRootPackage<PdfRootPackage>();
```
## Etapa 3: atualizar as propriedades do documento
 Agora, atualize as propriedades desejadas do documento PDF dentro do`PdfRootPackage`:
```csharp
root.DocumentProperties.Author = "New Author Name";
root.DocumentProperties.CreatedDate = DateTime.Now;
root.DocumentProperties.Title = "New Document Title";
root.DocumentProperties.Keywords = "keyword1, keyword2";
root.DocumentProperties.Creator = "Document Creator";
root.DocumentProperties.Producer = "Document Producer";
```
## Etapa 4: salvar alterações
Após modificar as propriedades, salve as alterações novamente no arquivo PDF:
```csharp
metadata.Save("Your Output File Path");
```
## Etapa 5: recuperar propriedades atualizadas
Para verificar as alterações, recarregue os metadados e recupere as propriedades atualizadas:
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

## Conclusão
Neste tutorial, exploramos como aproveitar o GroupDocs.Metadata for .NET para atualizar propriedades integradas de documentos PDF de forma programática. Seguindo as etapas descritas, você pode gerenciar e modificar com eficiência metadados em arquivos PDF usando C#. Sinta-se à vontade para explorar mais recursos e capacidades oferecidos pelo GroupDocs.Metadata para manipulação abrangente de metadados.

## Perguntas frequentes
### P: O que é GroupDocs.Metadata para .NET?
R: GroupDocs.Metadata for .NET é uma biblioteca que permite aos desenvolvedores ler, editar, remover e manipular metadados em vários formatos de documentos de forma programática.
### P: Onde posso encontrar a documentação do GroupDocs.Metadata for .NET?
 R: Você pode acessar a documentação[aqui](https://tutorials.groupdocs.com/metadata/net/).
### P: Como posso baixar GroupDocs.Metadata para .NET?
 R: Você pode baixar GroupDocs.Metadata para .NET em[esse link](https://releases.groupdocs.com/metadata/net/).
### P: Existe uma avaliação gratuita disponível?
 R: Sim, você pode obter uma versão de avaliação gratuita[aqui](https://releases.groupdocs.com/).
### P: Onde posso obter suporte para GroupDocs.Metadata for .NET?
 R: Para suporte, visite o fórum GroupDocs.Metadata[aqui](https://forum.groupdocs.com/c/metadata/14).