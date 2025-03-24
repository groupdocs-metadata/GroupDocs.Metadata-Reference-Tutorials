---
title: .NET의 MP3 파일에서 가사 태그 읽기
linktitle: .NET의 MP3 파일에서 가사 태그 읽기
second_title: GroupDocs.메타데이터 .NET API
description: .NET용 GroupDocs.Metadata를 사용하여 MP3 파일에서 가사 태그를 추출하는 방법을 알아보세요. 단계별 튜토리얼을 따라해보세요.
weight: 13
url: /ko/net/audio-metadata/read-lyrics-tag-mp3/
---

# .NET의 MP3 파일에서 가사 태그 읽기

## 소개
이 튜토리얼에서는 .NET의 GroupDocs.Metadata API를 사용하여 MP3 파일에서 가사 태그를 추출하고 읽는 방법을 알아봅니다. GroupDocs.Metadata는 개발자가 MP3 파일을 비롯한 다양한 파일 형식과 관련된 메타데이터로 작업할 수 있는 강력한 라이브러리입니다. 다음 단계를 따르면 MP3 파일에 포함된 가사 관련 정보를 효율적으로 검색할 수 있습니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 설정되어 있는지 확인하세요.
- 컴퓨터에 Visual Studio가 설치되어 있습니다.
- C# 프로그래밍 언어에 대한 기본 지식.
-  .NET용 GroupDocs.Metadata 라이브러리. 당신은 그것을 다운로드 할 수 있습니다[여기](https://releases.groupdocs.com/metadata/net/).
- 테스트용 가사 태그가 포함된 MP3 파일에 액세스합니다.

## 네임스페이스 가져오기
먼저 C# 프로젝트에 필요한 네임스페이스를 포함합니다.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Formats.Audio;
```
## 1단계: MP3 파일 로드
 초기화부터 시작하세요.`Metadata` 입력 MP3 파일 경로를 사용하여 개체를 만듭니다.
```csharp
using (Metadata metadata = new Metadata("YourInputFile.mp3"))
{
    // MP3 형식의 루트 패키지 검색
    var root = metadata.GetRootPackage<MP3RootPackage>();
```
## 2단계: 가사 태그에 액세스
MP3 파일에 Lyrics3V2 태그가 포함되어 있는지 확인하고 관련 정보를 검색하십시오.
```csharp
    if (root.Lyrics3V2 != null)
    {
        //출력 특정 태그 필드
        Console.WriteLine("Lyrics: " + root.Lyrics3V2.Lyrics);
        Console.WriteLine("Album: " + root.Lyrics3V2.Album);
        Console.WriteLine("Artist: " + root.Lyrics3V2.Artist);
        Console.WriteLine("Track: " + root.Lyrics3V2.Track);
```
## 3단계: 모든 태그 필드를 반복합니다.
또는 Lyrics3V2 내에서 사용 가능한 모든 태그 필드를 반복할 수 있습니다.
```csharp
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Metadata를 사용하여 MP3 파일에서 가사 태그를 추출하고 읽는 방법을 살펴보았습니다. 다음 단계를 수행하면 추가 처리를 위해 MP3 파일에 포함된 가사 관련 메타데이터를 효과적으로 검색하거나 애플리케이션에 표시할 수 있습니다.

## FAQ
### GroupDocs.Metadata를 사용하여 가사 태그를 수정하거나 업데이트할 수 있나요?
예, GroupDocs.Metadata를 사용하면 가사 태그를 포함하여 MP3 파일 내의 메타데이터를 업데이트하고 수정할 수 있습니다.
### GroupDocs.Metadata는 MP3 외에 다른 오디오 형식을 지원합니까?
예, GroupDocs.Metadata는 메타데이터 추출 및 조작을 위한 광범위한 오디오 및 비디오 형식을 지원합니다.
### GroupDocs.Metadata에 대한 자세한 문서는 어디서 찾을 수 있나요?
 전체 문서에 액세스할 수 있습니다.[여기](https://tutorials.groupdocs.com/metadata/net/).
### GroupDocs.Metadata에 대한 무료 평가판이 있습니까?
 예, 무료 평가판을 받을 수 있습니다[여기](https://releases.groupdocs.com/).
### GroupDocs.Metadata에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
 기술 지원이 필요하면 GroupDocs.Metadata 지원 포럼을 방문하세요.[여기](https://forum.groupdocs.com/c/metadata/14).