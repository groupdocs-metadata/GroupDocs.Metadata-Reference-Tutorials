---
title: Atualizar propriedades integradas em planilhas usando .NET
linktitle: Atualizar propriedades integradas em planilhas usando .NET
second_title: API GroupDocs.Metadata .NET
description: Saiba como atualizar propriedades de metadados integradas em arquivos Excel usando GroupDocs.Metadata for .NET. Modifique autor, horário de criação, empresa e muito mais com C#.
weight: 14
url: /pt/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
type: docs
---
# Atualizar propriedades integradas em planilhas usando .NET

## Introdução
Neste tutorial, exploraremos como utilizar GroupDocs.Metadata for .NET para atualizar propriedades integradas em arquivos de planilha usando C#. GroupDocs.Metadata é uma API poderosa que permite aos desenvolvedores ler, editar e remover propriedades de metadados de vários formatos de arquivo, incluindo planilhas. Vamos nos concentrar especificamente na modificação de propriedades como autor, hora de criação, empresa, categoria e palavras-chave em arquivos Excel.
## Pré-requisitos
Antes de começarmos, certifique-se de ter o seguinte:
- Visual Studio: instale a versão mais recente do Visual Studio.
-  GroupDocs.Metadata for .NET: Baixe e instale GroupDocs.Metadata for .NET a partir do[página de download](https://releases.groupdocs.com/metadata/net/).
- Conhecimento básico de C#: Compreensão da linguagem de programação C# e do framework .NET.

## Importar namespaces
Comece importando os namespaces necessários em seu projeto C#:
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## Etapa 1: carregar o arquivo da planilha
 Primeiro, inicialize um`Metadata` objeto carregando o arquivo da planilha de entrada:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // Acesse as propriedades do documento na raiz
}
```
## Etapa 2: atualizar as propriedades integradas
 Acesse as propriedades internas do documento através do`SpreadsheetRootPackage` e modifique-os conforme necessário:
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
Certifique-se de substituir os espaços reservados (`YourAuthorName`, `YourCompany`, `YourCategory`com valores reais que você deseja definir para as propriedades.
## Etapa 3: salvar alterações
Após atualizar as propriedades, salve as alterações novamente no arquivo de planilha:
```csharp
metadata.Save("YourInputFile.xlsx");
```

## Conclusão
Neste tutorial, demonstramos como usar GroupDocs.Metadata for .NET para atualizar propriedades integradas de arquivos de planilha programaticamente. Ao aproveitar esta API, os desenvolvedores podem gerenciar com eficiência metadados em documentos Excel, melhorando a organização e a acessibilidade dos dados.

## Perguntas frequentes
### Quais formatos de arquivo o GroupDocs.Metadata suporta?
GroupDocs.Metadata oferece suporte a uma ampla variedade de formatos de arquivo, incluindo documentos do Microsoft Office, PDFs, imagens, arquivos de áudio e muito mais.
### Posso recuperar propriedades de metadados existentes de arquivos?
Sim, você pode extrair e ler propriedades de metadados, como autor, data de criação, palavras-chave e propriedades personalizadas usando GroupDocs.Metadata.
### O GroupDocs.Metadata é compatível com o .NET Core?
Sim, GroupDocs.Metadata é compatível com .NET Framework e .NET Core.
### O GroupDocs.Metadata oferece uma avaliação gratuita?
 Sim, você pode baixar uma versão de avaliação gratuita do GroupDocs.Metadata em[aqui](https://releases.groupdocs.com/).
### Onde posso encontrar suporte para GroupDocs.Metadata?
 Para suporte e discussões, visite o[Fórum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14).