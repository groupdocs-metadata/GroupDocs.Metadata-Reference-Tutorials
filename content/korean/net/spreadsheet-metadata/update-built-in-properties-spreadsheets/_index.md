---
title: .NET을 사용하여 스프레드시트의 내장 속성 업데이트
linktitle: .NET을 사용하여 스프레드시트의 내장 속성 업데이트
second_title: GroupDocs.메타데이터 .NET API
description: .NET용 GroupDocs.Metadata를 사용하여 Excel 파일에 내장된 메타데이터 속성을 업데이트하는 방법을 알아보세요. C#을 사용하여 작성자, 생성 시간, 회사 등을 수정하세요.
type: docs
weight: 14
url: /ko/net/spreadsheet-metadata/update-built-in-properties-spreadsheets/
---
## 소개
이 자습서에서는 .NET용 GroupDocs.Metadata를 활용하여 C#을 사용하여 스프레드시트 파일의 기본 제공 속성을 업데이트하는 방법을 살펴보겠습니다. GroupDocs.Metadata는 개발자가 스프레드시트를 포함한 다양한 파일 형식에서 메타데이터 속성을 읽고, 편집하고, 제거할 수 있는 강력한 API입니다. 특히 Excel 파일 내의 작성자, 생성 시간, 회사, 범주 및 키워드와 같은 속성을 수정하는 데 중점을 둘 것입니다.
## 전제 조건
시작하기 전에 다음 사항이 있는지 확인하세요.
- Visual Studio: 최신 버전의 Visual Studio를 설치합니다.
-  .NET용 GroupDocs.Metadata: 다음에서 .NET용 GroupDocs.Metadata를 다운로드하고 설치합니다.[다운로드 페이지](https://releases.groupdocs.com/metadata/net/).
- 기본 C# 지식: C# 프로그래밍 언어 및 .NET 프레임워크에 대한 이해.

## 네임스페이스 가져오기
C# 프로젝트에서 필요한 네임스페이스를 가져오는 것부터 시작하세요.
```csharp
using System;
using GroupDocs.Metadata;
using GroupDocs.Metadata.Formats.Document;
```
## 1단계: 스프레드시트 파일 로드
 먼저,`Metadata` 입력 스프레드시트 파일을 로드하여 객체:
```csharp
using (Metadata metadata = new Metadata("YourInputFile.xlsx"))
{
    var root = metadata.GetRootPackage<SpreadsheetRootPackage>();
    // 루트 내의 문서 속성에 액세스
}
```
## 2단계: 내장 속성 업데이트
 다음을 통해 내장된 문서 속성에 액세스합니다.`SpreadsheetRootPackage` 필요에 따라 수정합니다.
```csharp
root.DocumentProperties.Author = "YourAuthorName";
root.DocumentProperties.CreatedTime = DateTime.Now;
root.DocumentProperties.Company = "YourCompany";
root.DocumentProperties.Category = "YourCategory";
root.DocumentProperties.Keywords = "metadata, built-in, update";
```
자리 표시자를 교체해야 합니다(`YourAuthorName`, `YourCompany`, `YourCategory`속성에 설정하려는 실제 값을 사용합니다.
## 3단계: 변경 사항 저장
속성을 업데이트한 후 변경 사항을 스프레드시트 파일에 다시 저장합니다.
```csharp
metadata.Save("YourInputFile.xlsx");
```

## 결론
이 자습서에서는 .NET용 GroupDocs.Metadata를 사용하여 스프레드시트 파일의 기본 제공 속성을 프로그래밍 방식으로 업데이트하는 방법을 보여주었습니다. 개발자는 이 API를 활용하여 Excel 문서 내의 메타데이터를 효율적으로 관리하고 데이터 구성 및 접근성을 향상시킬 수 있습니다.

## FAQ
### GroupDocs.Metadata는 어떤 파일 형식을 지원합니까?
GroupDocs.Metadata는 Microsoft Office 문서, PDF, 이미지, 오디오 파일 등을 포함한 광범위한 파일 형식을 지원합니다.
### 파일에서 기존 메타데이터 속성을 검색할 수 있나요?
예, GroupDocs.Metadata를 사용하면 작성자, 생성 날짜, 키워드 및 사용자 정의 속성과 같은 메타데이터 속성을 추출하고 읽을 수 있습니다.
### GroupDocs.Metadata는 .NET Core와 호환되나요?
예, GroupDocs.Metadata는 .NET Framework 및 .NET Core 모두와 호환됩니다.
### GroupDocs.Metadata는 무료 평가판을 제공합니까?
 예, 다음에서 GroupDocs.Metadata 무료 평가판을 다운로드할 수 있습니다.[여기](https://releases.groupdocs.com/).
### GroupDocs.Metadata에 대한 지원은 어디서 찾을 수 있나요?
 지원 및 토론을 원하시면 다음 사이트를 방문하세요.[GroupDocs.메타데이터 포럼](https://forum.groupdocs.com/c/metadata/14).