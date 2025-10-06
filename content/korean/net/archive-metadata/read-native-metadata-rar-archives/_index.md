---
title: .NET의 RAR 아카이브에서 기본 메타데이터 속성 읽기
linktitle: .NET의 RAR 아카이브에서 기본 메타데이터 속성 읽기
second_title: GroupDocs.메타데이터 .NET API
description: C#에서 .NET용 GroupDocs.Metadata를 사용하여 RAR 아카이브에서 메타데이터 속성을 추출하는 방법을 알아보세요. 손쉽게 파일 세부정보를 탐색해 보세요.
weight: 10
url: /ko/net/archive-metadata/read-native-metadata-rar-archives/
type: docs
---
# .NET의 RAR 아카이브에서 기본 메타데이터 속성 읽기

## 소개
RAR(Roshal Archive)은 데이터 압축 및 보관에 사용되는 널리 사용되는 파일 형식입니다. .NET 애플리케이션에서 RAR 파일로 작업할 때 이러한 아카이브에 포함된 메타데이터 속성을 읽고 추출해야 하는 경우가 많습니다. 이 자습서에서는 .NET용 GroupDocs.Metadata를 활용하여 RAR 아카이브에서 기본 메타데이터 속성에 액세스하고 추출하는 과정을 안내합니다.
## 전제 조건

시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
- C# 프로그래밍 언어에 대한 기본 이해.
- 개발 컴퓨터에 Visual Studio가 설치되어 있습니다.
-  .NET 라이브러리용 GroupDocs.Metadata가 설치되었습니다(참조:[다운로드 링크](https://releases.groupdocs.com/metadata/net/)).
- 테스트 목적으로 RAR 아카이브 파일에 액세스합니다.

## 네임스페이스 가져오기
시작하려면 필요한 네임스페이스를 C# 프로젝트로 가져옵니다.
```csharp
using GroupDocs.Formats.Archive;
using System;
using GroupDocs.Metadata;
using System.Text;
```

## 1단계: RAR 아카이브 로드
 먼저,`Metadata` RAR 아카이브 파일을 로드하여 개체:
```csharp
using (Metadata metadata = new Metadata("YourZipFile.rar"))
{
    var root = metadata.GetRootPackage<RarRootPackage>();
```
## 2단계: RAR 아카이브의 전체 항목에 액세스
RAR 아카이브 내의 총 항목(파일/폴더) 수를 검색합니다.
```csharp
Console.WriteLine(root.RarPackage.TotalEntries);
```
## 3단계: 아카이브의 파일을 통해 반복
RAR 아카이브 내의 각 파일을 반복하여 특정 메타데이터 속성에 액세스합니다.
```csharp
foreach (var file in root.RarPackage.Files)
{
    Console.WriteLine(file.Name);
    Console.WriteLine(file.CompressedSize);
    Console.WriteLine(file.ModificationDateTime);
    Console.WriteLine(file.UncompressedSize);
}
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Metadata를 사용하여 RAR 아카이브에서 메타데이터 속성을 추출하는 방법을 배웠습니다. 이 라이브러리는 다양한 파일 형식에 포함된 메타데이터에 액세스하고 활용하는 프로세스를 단순화하여 .NET 애플리케이션의 기능을 향상시킵니다.

## FAQ
### .NET용 GroupDocs.Metadata란 무엇입니까?
.NET용 GroupDocs.Metadata는 개발자가 RAR과 같은 아카이브를 포함하여 다양한 파일 형식의 메타데이터로 작업할 수 있는 강력한 라이브러리입니다.
### .NET용 GroupDocs.Metadata의 임시 라이센스를 얻으려면 어떻게 해야 합니까?
 임시면허를 취득하실 수 있습니다.[여기](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Metadata는 RAR 외에 다른 아카이브 형식을 지원합니까?
예, GroupDocs.Metadata는 ZIP, TAR, 7z를 포함한 광범위한 아카이브 형식을 지원합니다.
### 이 라이브러리를 사용하여 메타데이터 속성을 수정하고 RAR 아카이브 내에서 업데이트할 수 있습니까?
예, GroupDocs.Metadata를 사용하면 지원되는 파일 형식에 메타데이터 속성을 업데이트, 제거 및 추가할 수 있습니다.
### GroupDocs.Metadata에 대한 추가 도움말이나 지원은 어디서 찾을 수 있나요?
 방문하다[GroupDocs.메타데이터 포럼](https://forum.groupdocs.com/c/metadata/14) 커뮤니티 지원 및 토론을 위해.