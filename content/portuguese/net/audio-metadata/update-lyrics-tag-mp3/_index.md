---
title: Atualizar a tag de letras em arquivos MP3 usando .NET
linktitle: Atualizar a tag de letras em arquivos MP3 usando .NET
second_title: API GroupDocs.Metadata .NET
description: Aprenda como atualizar metadados de arquivos MP3, incluindo letras, artistas e detalhes do álbum de forma programática usando GroupDocs.Metadata for .NET.
weight: 21
url: /pt/net/audio-metadata/update-lyrics-tag-mp3/
---

# Atualizar a tag de letras em arquivos MP3 usando .NET

## Introdução
Neste tutorial, demonstraremos como usar a biblioteca GroupDocs.Metadata for .NET para atualizar a tag de letras em arquivos MP3 programaticamente. Este processo envolve acessar e modificar os metadados dos arquivos MP3, visando especificamente as informações das letras.
## Pré-requisitos
Antes de começar, certifique-se de ter o seguinte:
- Conhecimento básico de programação C#.
- Visual Studio instalado em sua máquina.
-  Biblioteca GroupDocs.Metadata for .NET instalada (consulte[Link para Download](https://releases.groupdocs.com/metadata/net/)).
- Um arquivo MP3 para fins de teste.

## Importar namespaces
Comece importando os namespaces necessários para o seu projeto C#:
```csharp
using GroupDocs.Formats.Audio;
using System;
using GroupDocs.Metadata;
```
## Passo 1: Carregue o arquivo MP3
 Primeiro, carregue o arquivo MP3 em um`Metadata` objeto usando GroupDocs.Metadata:
```csharp
using (Metadata metadata = new Metadata("path_to_your_mp3_file.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // Acesse a tag Lyrics3V2
    if (root.Lyrics3V2 == null)
    {
        root.Lyrics3V2 = new LyricsTag();
    }
```
## Etapa 2: atualizar as informações das letras
Em seguida, atualize as informações das letras junto com outros detalhes relevantes, como artista, álbum e faixa:
```csharp
    root.Lyrics3V2.Lyrics = "[00:01]Test lyrics";
    root.Lyrics3V2.Artist = "test artist";
    root.Lyrics3V2.Album = "test album";
    root.Lyrics3V2.Track = "test track";
```
## Etapa 3: adicionar campos personalizados (opcional)
Opcionalmente, você pode adicionar campos personalizados à tag:
```csharp
    root.Lyrics3V2.Set(new LyricsField("ABC", "custom value"));
```
## Etapa 4: salve as alterações
Por fim, salve os metadados modificados de volta no arquivo MP3:
```csharp
    metadata.Save("path_to_your_output_file.mp3");
}
```

## Conclusão
Neste tutorial, exploramos como atualizar a tag de letras em arquivos MP3 usando GroupDocs.Metadata for .NET. Seguindo as etapas descritas, você pode gerenciar e modificar com eficiência metadados em arquivos MP3 de forma programática.

## Perguntas frequentes
### Posso atualizar outros metadados além das letras usando GroupDocs.Metadata for .NET?
Sim, GroupDocs.Metadata for .NET permite trabalhar com vários tipos de metadados em diferentes formatos de arquivo.
### O GroupDocs.Metadata for .NET é compatível com o .NET Core?
Sim, a biblioteca oferece suporte a .NET Framework e .NET Core.
### O GroupDocs.Metadata for .NET requer uma licença para uso comercial?
 Sim, você pode obter uma licença de[Documentos de grupo](https://purchase.groupdocs.com/buy) para uso comercial.
### Como posso obter suporte ou fazer perguntas relacionadas ao GroupDocs.Metadata for .NET?
 Você pode visitar o[Fórum GroupDocs.Metadata](https://forum.groupdocs.com/c/metadata/14) para apoio e discussões.
### Posso experimentar o GroupDocs.Metadata for .NET gratuitamente?
 Sim, você pode obter um[teste grátis](https://releases.groupdocs.com/) para explorar suas características.