---
date: 2026-06-17
description: GroupDocs.Metadata for Java를 사용하여 PDF, Word, Excel, PowerPoint 등에서 문서를
  이미지로 변환하고 PDF 메타데이터를 추출, 읽기 또는 제거하는 방법을 배웁니다.
keywords:
- convert document to image
- read pdf metadata java
- extract pdf metadata java
- remove pdf metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-17'
  description: Learn how to convert document to image and extract, read, or remove
    PDF metadata using GroupDocs.Metadata for Java across PDF, Word, Excel, PowerPoint
    and more.
  headline: Convert Document to Image – GroupDocs.Metadata Java Tutorial
  type: TechArticle
- description: Learn how to convert document to image and extract, read, or remove
    PDF metadata using GroupDocs.Metadata for Java across PDF, Word, Excel, PowerPoint
    and more.
  name: Convert Document to Image – GroupDocs.Metadata Java Tutorial
  steps:
  - name: Set Up the Maven Dependency
    text: Add the GroupDocs.Metadata dependency to your `pom.xml`. This single line
      pulls in all required binaries.
  - name: Load the Source Document
    text: Create a `Document` object by passing the file path. This object represents
      the entire source file in memory.
  - name: (Optional) Read or Remove PDF Metadata
    text: If the source is a PDF, you can call `document.getMetadata().readAll()`
      to retrieve a map of metadata entries, or `document.getMetadata().clearAll()`
      to strip them before rendering.
  - name: Configure Image Options
    text: Set the output format (`ImageOptions.setImageFormat(ImageFormat.PNG)`) and
      optionally define DPI, page range, or background color.
  - name: Save Images to Disk
    text: Call `document.save("output_folder", imageOptions)`. The library creates
      one image per page, naming them sequentially (e.g., `page_1.png`, `page_2.png`).
  type: HowTo
- questions:
  - answer: No. The conversion creates separate image files; the source document remains
      unchanged unless you explicitly overwrite it.
    question: Does converting to image affect the original file size?
  - answer: Yes. Use `ImageOptions.setPageRange("1-5")` to render pages 1 through
      5 only.
    question: Can I convert only a subset of pages?
  - answer: The SDK renders raster images; for vector‑preserving output you would
      need a PDF‑to‑SVG converter, which is outside the scope of GroupDocs.Metadata.
    question: Is it possible to retain vector quality for PDFs?
  - answer: The library can handle documents with thousands of pages, limited only
      by available disk space and memory. It streams pages one‑by‑one to keep memory
      usage low.
    question: Are there limits on the number of pages I can convert?
  - answer: Purchase a commercial license from GroupDocs; a temporary license is available
      for evaluation and is automatically applied when you set the license file path
      in your code.
    question: How do I license the library for production?
  type: FAQPage
title: 문서를 이미지로 변환 – GroupDocs.Metadata Java 튜토리얼
type: docs
url: /ko/java/document-formats/
weight: 6
---

# 문서를 이미지로 변환 – GroupDocs.Metadata Java 튜토리얼

이 포괄적인 가이드에서는 Java용 GroupDocs.Metadata를 사용하여 **문서를 이미지로 변환하는 방법**을 배우고, 필요에 따라 PDF 메타데이터를 읽고, 추출하고, 제거하는 방법도 학습합니다. 왜, 무엇을, 단계별 방법을 안내하여 미리보기 기반 워크플로, 규정 준수 검사 및 검색 가능한 문서 라이브러리를 구축할 수 있는 탄탄한 기반을 제공합니다.

## 빠른 답변
- **문서를 이미지로 변환한다는 것은 무엇을 의미합니까?** 소스 파일(PDF, DOCX, XLSX, PPTX 등)의 각 페이지를 PNG 또는 JPEG와 같은 래스터 이미지로 렌더링하는 것을 의미합니다.  
- **프리뷰에 GroupDocs.Metadata를 사용하는 이유는?** Microsoft Office를 설치할 필요 없이 이미지를 렌더링하며, 동일한 파이프라인에서 메타데이터를 제거하거나 편집할 수 있습니다.  
- **같은 호출에서 PDF 메타데이터를 읽을 수 있나요?** 예—렌더링 전후에 메타데이터를 추가 I/O 없이 읽을 수 있습니다.  
- **PDF 메타데이터 제거가 지원되나요?** 물론입니다; API는 모든 기본 및 사용자 정의 속성을 지우는 메서드를 제공합니다.  
- **이미지 변환에 지원되는 포맷은 무엇인가요?** PDF, DOCX, XLSX, PPTX 등 50가지 이상의 입력 포맷과 다양한 이미지 타입을 지원합니다.

## “문서를 이미지로 변환”이란?
*Convert document to image*는 디지털 파일의 각 페이지를 비트맵 이미지(PNG, JPEG, BMP 등)로 변환하는 과정입니다. 이를 통해 썸네일 갤러리, 브라우저에서의 빠른 프리뷰 렌더링, 검색 엔진을 위한 콘텐츠 무관 인덱싱이 가능해지며, 시각적 품질을 유지하고 단일 워크플로에서 후속 메타데이터 처리를 할 수 있습니다.

## GroupDocs.Metadata로 문서를 이미지로 변환하는 이유는?
GroupDocs.Metadata는 **50개 이상의 입력 및 출력 포맷**을 지원하며 전체 문서를 메모리에 로드하지 않고 수백 페이지 파일을 렌더링할 수 있어 일반적인 2 GHz 서버에서 **초당 최대 30페이지**의 속도로 프리뷰를 생성합니다. 이 라이브러리는 메타데이터에 대한 세밀한 제어도 제공하여 동일한 워크플로에서 읽기, 추출 또는 제거가 가능해 I/O를 줄이고 보안을 향상시킵니다.

## 사전 요구 사항
- 개발 머신에 Java 17 이상이 설치되어 있어야 합니다.  
- 유효한 GroupDocs.Metadata for Java 라이선스(테스트용 임시 라이선스도 가능).  
- 의존성 관리를 위한 Maven 또는 Gradle.  
- Java IDE(IntelliJ IDEA, Eclipse, VS Code)에 대한 기본적인 친숙함.

## GroupDocs.Metadata for Java를 사용하여 문서를 이미지로 변환하는 방법
`Document` 클래스는 로드된 파일을 나타내며 해당 콘텐츠와 메타데이터에 접근할 수 있습니다. `ImageOptions` 클래스는 포맷, DPI, 페이지 범위와 같은 렌더링 매개변수를 설정합니다. `Document` 클래스로 소스 파일을 로드하고, `ImageOptions`를 구성한 뒤 `save`를 호출하여 이미지 파일을 생성합니다. 변환은 두 줄의 코드로 이루어지며, 저장하기 전에 메타데이터를 선택적으로 삭제할 수 있습니다.

### 단계 1: Maven 의존성 설정
`pom.xml`에 GroupDocs.Metadata 의존성을 추가합니다. 이 한 줄로 모든 필요한 바이너리를 가져옵니다.

### 단계 2: 소스 문서 로드
파일 경로를 전달하여 `Document` 객체를 생성합니다. 이 객체는 메모리 내 전체 소스 파일을 나타냅니다.

### 단계 3: (선택) PDF 메타데이터 읽기 또는 제거
소스가 PDF인 경우 `document.getMetadata().readAll()`을 호출하여 메타데이터 항목 맵을 가져오거나, 렌더링 전에 `document.getMetadata().clearAll()`을 호출하여 메타데이터를 제거할 수 있습니다.

### 단계 4: 이미지 옵션 구성
출력 포맷을 설정합니다(`ImageOptions.setImageFormat(ImageFormat.PNG)`) 그리고 필요에 따라 DPI, 페이지 범위 또는 배경 색을 정의할 수 있습니다.

### 단계 5: 이미지 디스크에 저장
`document.save("output_folder", imageOptions)`를 호출합니다. 라이브러리는 페이지당 하나의 이미지를 생성하고 순차적으로 이름을 지정합니다(예: `page_1.png`, `page_2.png`).

## Java에서 PDF 메타데이터 읽는 방법
`Document` 클래스는 로드된 파일을 나타내며 메타데이터 작업을 위한 `getMetadata()` 접근자를 제공합니다. PDF에 대해 `Document` 인스턴스를 생성하고 `document.getMetadata().readAll()`을 호출한 뒤 반환된 `Map<String, Object>`를 반복하여 각 메타데이터 키‑값 쌍에 접근합니다. 이 메서드는 기본 및 사용자 정의 속성을 한 번에 반환하므로 별도의 파서가 필요하지 않습니다.

## Java에서 PDF 메타데이터 추출하는 방법
`readAll()`은 모든 기본 및 사용자 정의 메타데이터 속성의 맵을 반환합니다. `document.getMetadata().readAll()`을 호출한 후, 결과 맵을 Jackson(`ObjectMapper.writeValueAsString(map)`)과 같은 직렬화 도구에 전달하여 JSON 문자열을 만들거나, SDK에서 제공하는 `MetadataExporter`를 사용해 CSV 또는 XML 파일로 직접 기록할 수 있습니다.

## Java에서 PDF 메타데이터 제거하는 방법
`clearAll()`은 문서의 모든 메타데이터 항목을 제거합니다. `document.getMetadata().clearAll()`을 호출하여 모든 메타데이터를 삭제한 뒤 `document.save("cleaned.pdf")`로 PDF를 저장합니다. 이 작업은 원본 메타데이터 없이 파일을 다시 쓰므로 프라이버시 준수를 보장합니다.

## 일반 사용 사례
- **문서 관리 시스템(DMS):** 업로드된 모든 파일에 대한 썸네일 프리뷰를 생성하고 추출된 메타데이터를 검색 가능한 인덱스에 저장합니다.  
- **규정 준수 감사:** 보관 전 PDF 메타데이터를 자동으로 읽고 기록하여 필수 필드가 존재하는지 확인합니다.  
- **보안 공유:** PDF의 모든 메타데이터를 제거한 뒤 이미지 프리뷰를 렌더링하여 내부 정보를 노출하지 않고 외부 파트너와 공유합니다.  
- **대량 마이그레이션:** 레거시 Office 문서를 이미지로 변환하면서 메타데이터를 추출해 새로운 콘텐츠 저장소에 가져옵니다.

## 문제 해결 팁
- **빈 이미지:** 소스 파일이 비밀번호로 보호되지 않았는지 확인하고, `Document.load(path, password)`를 통해 비밀번호를 제공하세요.  
- **메타데이터 누락:** 일부 PDF는 XMP 스트림을 사용할 수 있습니다; 표준 속성이 비어 있으면 `document.getMetadata().readAllXmp()`를 사용하세요.  
- **성능 병목:** 대량 배치에서는 스레드당 단일 `Document` 인스턴스를 재사용하고 `ImageOptions.setDpi(150)`을 설정하여 품질과 속도의 균형을 맞추세요.  
- **지원되지 않는 포맷:** 파일 확장자가 SDK 지원 포맷 표(50개 이상)에 나열되어 있는지 확인하세요.

## 자주 묻는 질문

**Q: 이미지를 변환하면 원본 파일 크기에 영향을 줍니까?**  
A: 아니요. 변환은 별도의 이미지 파일을 생성하므로 원본 문서는 명시적으로 덮어쓰지 않는 한 변경되지 않습니다.

**Q: 페이지의 일부만 변환할 수 있나요?**  
A: 예. `ImageOptions.setPageRange("1-5")`를 사용하여 1~5 페이지만 렌더링합니다.

**Q: PDF의 벡터 품질을 유지할 수 있나요?**  
A: SDK는 래스터 이미지를 렌더링합니다; 벡터를 보존하는 출력이 필요하면 PDF‑to‑SVG 변환기가 필요하며 이는 GroupDocs.Metadata 범위 밖입니다.

**Q: 변환할 수 있는 페이지 수에 제한이 있나요?**  
A: 라이브러리는 수천 페이지 문서를 처리할 수 있으며, 제한은 사용 가능한 디스크 공간과 메모리뿐입니다. 페이지를 하나씩 스트리밍하여 메모리 사용량을 낮게 유지합니다.

**Q: 프로덕션에서 라이브러리를 라이선스하려면 어떻게 해야 하나요?**  
A: GroupDocs에서 상용 라이선스를 구매하십시오; 평가용 임시 라이선스가 제공되며 코드에서 라이선스 파일 경로를 설정하면 자동으로 적용됩니다.

## 추가 리소스

- [GroupDocs.Metadata for Java 문서](https://docs.groupdocs.com/metadata/java/)
- [GroupDocs.Metadata for Java API 레퍼런스](https://reference.groupdocs.com/metadata/java/)
- [GroupDocs.Metadata for Java 다운로드](https://releases.groupdocs.com/metadata/java/)
- [GroupDocs.Metadata 포럼](https://forum.groupdocs.com/c/metadata)
- [무료 지원](https://forum.groupdocs.com/)
- [임시 라이선스](https://purchase.groupdocs.com/temporary-license/)

### 사용 가능한 튜토리얼

#### [Java에서 GroupDocs를 사용한 Word 문서 메타데이터 액세스&#58; 포괄적인 가이드](./access-word-metadata-groupdocs-java/)
Java에서 GroupDocs를 사용한 Word 문서 메타데이터 액세스&#58; 포괄적인 가이드

#### [Java에서 GroupDocs.Metadata를 사용한 문서 이미지 프리뷰 생성&#58; 포괄적인 가이드](./java-groupdocs-metadata-document-image-previews/)
Java에서 GroupDocs.Metadata를 사용한 문서 이미지 프리뷰 생성&#58; 포괄적인 가이드

#### [Java용 GroupDocs.Metadata를 사용한 스프레드시트 유형 감지 및 식별](./detect-spreadsheet-types-groupdocs-metadata-java/)
Java용 GroupDocs.Metadata를 사용한 스프레드시트 유형 감지 및 식별

#### [문서 관리를 위한 Java에서 GroupDocs.Metadata로 PDF 메타데이터 효율적으로 업데이트](./update-pdf-metadata-groupdocs-metadata-java/)
문서 관리를 위한 Java에서 GroupDocs.Metadata로 PDF 메타데이터 효율적으로 업데이트

#### [Java에서 GroupDocs.Metadata를 사용한 문서 메타데이터 내보내기&#58; 단계별 가이드](./export-document-metadata-groupdocs-metadata-java/)
Java에서 GroupDocs.Metadata를 사용한 문서 메타데이터 내보내기&#58; 단계별 가이드

#### [Java에서 OpenType 폰트의 디지털 서명 추출&#58; GroupDocs.Metadata를 활용한 완전 가이드](./extract-digital-signatures-opentype-fonts-java/)
Java에서 OpenType 폰트의 디지털 서명 추출&#58; GroupDocs.Metadata를 활용한 완전 가이드

#### [Java용 GroupDocs.Metadata를 사용한 프레젠테이션 메타데이터 추출&#58; 단계별 가이드](./extract-metadata-presentation-groupdocs-metadata-java/)
Java용 GroupDocs.Metadata를 사용한 프레젠테이션 메타데이터 추출&#58; 단계별 가이드

#### [Java를 사용한 Word 문서 메타데이터 추출&#58; GroupDocs.Metadata for Java와 함께하는 포괄적인 가이드](./extract-word-metadata-groupdocs-java/)
Java를 사용한 Word 문서 메타데이터 추출&#58; GroupDocs.Metadata for Java와 함께하는 포괄적인 가이드

#### [Java에서 GroupDocs.Metadata를 사용한 Word 문서 속성 추출](./groupdocs-metadata-java-word-properties-extraction/)
Java에서 GroupDocs.Metadata를 사용한 Word 문서 속성 추출

#### [GroupDocs.Metadata Java를 사용한 Word 문서 통계 추출&#58; 단계별 가이드](./extract-word-statistics-groupdocs-metadata-java/)
GroupDocs.Metadata Java를 사용한 Word 문서 통계 추출&#58; 단계별 가이드

#### [Java에서 GroupDocs.Metadata를 사용한 스프레드시트 메타데이터 추출 및 관리](./extract-manage-spreadsheet-metadata-groupdocs-java/)
Java에서 GroupDocs.Metadata를 사용한 스프레드시트 메타데이터 추출 및 관리

#### [Java에서 GroupDocs.Metadata를 사용해 PDF에서 사용자 정의 메타데이터 추출&#58; 포괄적인 가이드](./extract-custom-metadata-groupdocs-metadata-java/)
Java에서 GroupDocs.Metadata를 사용해 PDF에서 사용자 정의 메타데이터 추출&#58; 포괄적인 가이드

#### [Java에서 GroupDocs.Metadata 라이브러리를 사용해 PDF 메타데이터 추출하는 방법](./extract-pdf-metadata-java-groupdocs/)
Java에서 GroupDocs.Metadata 라이브러리를 사용해 PDF 메타데이터 추출하는 방법

#### [Java용 GroupDocs.Metadata를 사용한 프레젠테이션 통계 추출 방법](./groupdocs-metadata-java-extract-presentation-statistics/)
Java용 GroupDocs.Metadata를 사용한 프레젠테이션 통계 추출 방법

#### [Java에서 GroupDocs.Metadata를 사용한 스프레드시트 주석 검사 및 관리 방법](./inspect-spreadsheet-comments-groupdocs-metadata-java/)
Java에서 GroupDocs.Metadata를 사용한 스프레드시트 주석 검사 및 관리 방법

#### [Java에서 GroupDocs.Metadata를 사용해 PDF 주석 제거하는 방법](./remove-annotations-pdf-groupdocs-metadata-java/)
Java에서 GroupDocs.Metadata를 사용해 PDF 주석 제거하는 방법

#### [Java용 GroupDocs.Metadata를 사용해 Word 문서의 검사 속성 업데이트 방법](./update-word-document-inspection-properties-groupdocs-metadata-java/)
Java용 GroupDocs.Metadata를 사용해 Word 문서의 검사 속성 업데이트 방법

#### [Java에서 GroupDocs.Metadata를 사용해 스프레드시트 메타데이터 업데이트 방법](./update-spreadsheet-metadata-groupdocs-java/)
Java에서 GroupDocs.Metadata를 사용해 스프레드시트 메타데이터 업데이트 방법

#### [GroupDocs.Metadata Java API를 사용해 Word 문서 메타데이터 업데이트 방법](./update-word-metadata-groupdocs-java-api/)
GroupDocs.Metadata Java API를 사용해 Word 문서 메타데이터 업데이트 방법

#### [GroupDocs.Metadata Java&#58; 완전 가이드로 Word 문서 메타데이터 업데이트 방법](./update-word-metadata-groupdocs-java/)
GroupDocs.Metadata Java&#58; 완전 가이드로 Word 문서 메타데이터 업데이트 방법

#### [GroupDocs.Metadata Java API를 사용해 프레젠테이션 주석 및 숨겨진 슬라이드 검사 방법](./groupdocs-metadata-java-inspect-comments-hidden-slides/)
GroupDocs.Metadata Java API를 사용해 프레젠테이션 주석 및 숨겨진 슬라이드 검사 방법

#### [GroupDocs&#58; PowerPoint 프레젠테이션에서 주석 및 숨겨진 슬라이드 삭제와 함께하는 Java 메타데이터 관리](./java-metadata-management-groupdocs-clear-comments-slides/)
GroupDocs&#58; PowerPoint 프레젠테이션에서 주석 및 숨겨진 슬라이드 삭제와 함께하는 Java 메타데이터 관리

#### [GroupDocs.Metadata를 사용한 Java PDF 통계 추출 가이드](./java-pdf-stats-groupdocs-metadata-developer-guide/)
GroupDocs.Metadata를 사용한 Java PDF 통계 추출 가이드

#### [Java에서 GroupDocs.Metadata를 사용해 PDF 메타데이터 관리 및 버전 감지](./manage-pdf-metadata-groupdocs-java/)
Java에서 GroupDocs.Metadata를 사용해 PDF 메타데이터 관리 및 버전 감지

#### [GroupDocs.Metadata를 사용한 Java 문서 메타데이터 관리 마스터](./master-document-metadata-java-groupdocs/)
GroupDocs.Metadata를 사용한 Java 문서 메타데이터 관리 마스터

#### [GroupDocs.Metadata&#58; 주석, 첨부 파일 등과 함께 Java에서 PDF 검사 마스터](./groupdocs-metadata-java-pdf-inspection/)
GroupDocs.Metadata&#58; 주석, 첨부 파일 등과 함께 Java에서 PDF 검사 마스터

#### [GroupDocs.Metadata for Java&#58; 개발자 가이드와 함께하는 PDF 메타데이터 관리 마스터](./master-pdf-metadata-groupdocs-java/)
GroupDocs.Metadata for Java&#58; 개발자 가이드와 함께하는 PDF 메타데이터 관리 마스터

#### [Java&#58; GroupDocs와 함께 스프레드시트 메타데이터 관리 마스터&#58; 주석 및 디지털 서명 제거](./master-spreadsheet-metadata-groupdocs-remove-comments-signatures/)
Java&#58; GroupDocs와 함께 스프레드시트 메타데이터 관리 마스터&#58; 주석 및 디지털 서명 제거

#### [GroupDocs.Metadata Java API를 사용해 PowerPoint에서 사용자 정의 메타데이터 업데이트](./update-custom-metadata-ppt-groupdocs-java/)
GroupDocs.Metadata Java API를 사용해 PowerPoint에서 사용자 정의 메타데이터 업데이트

#### [GroupDocs&#58; 포괄적인 가이드와 함께 Java에서 PDF 메타데이터 업데이트](./java-pdf-metadata-update-groupdocs-guide/)
GroupDocs&#58; 포괄적인 가이드와 함께 Java에서 PDF 메타데이터 업데이트

#### [GroupDocs.Metadata Java 라이브러리를 사용해 PowerPoint 메타데이터 업데이트](./groupdocs-metadata-java-powerpoint-update-metadata/)
GroupDocs.Metadata Java 라이브러리를 사용해 PowerPoint 메타데이터 업데이트

#### [GroupDocs.Metadata for Java&#58; 포괄적인 가이드와 함께 Word 문서 통계 업데이트](./update-word-document-statistics-groupdocs-metadata-java/)
GroupDocs.Metadata for Java&#58; 포괄적인 가이드와 함께 Word 문서 통계 업데이트

**마지막 업데이트:** 2026-06-17  
**테스트 환경:** GroupDocs.Metadata 23.12 for Java  
**작성자:** GroupDocs

## 관련 튜토리얼

- [GroupDocs.Metadata 라이브러리를 사용한 pdf 메타데이터 java 추출 방법](/metadata/java/document-formats/extract-pdf-metadata-java-groupdocs/)
- [문서 관리를 위한 Java에서 GroupDocs.Metadata로 PDF 메타데이터 효율적으로 업데이트](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)
- [Java용 GroupDocs.Metadata를 사용해 JPEG에서 이미지 리소스 블록 추출 방법](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)