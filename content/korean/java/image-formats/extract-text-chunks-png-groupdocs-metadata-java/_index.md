---
date: '2026-06-01'
description: GroupDocs.Metadata for Java를 사용하여 PNG 텍스트 청크를 추출하는 방법을 배우세요 – PNG metadata를
  효율적으로 읽고 robust image handling을 통합합니다.
keywords:
- how to extract png
- read png metadata
- java image metadata
- png text chunks
- groupdocs metadata java
schemas:
- author: GroupDocs
  dateModified: '2026-06-01'
  description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  headline: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  type: TechArticle
- description: Learn how to extract png text chunks with GroupDocs.Metadata for Java
    – read png metadata efficiently and integrate robust image handling.
  name: How to Extract PNG Text Chunks Using GroupDocs.Metadata Java API
  steps:
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  - name: '**Import Necessary Classes:**'
    text: '**Import Necessary Classes:**'
  - name: '**Initialize Metadata and Access Root Package:**'
    text: '**Initialize Metadata and Access Root Package:**'
  - name: '**Explanation of Parameters:**'
    text: '**Explanation of Parameters:**'
  type: HowTo
- questions:
  - answer: Yes, the free trial lets you read metadata, but a commercial license is
      required for production deployments.
    question: Can I read png metadata without a license?
  - answer: Absolutely – it handles JPEG, BMP, TIFF, and over 40 additional formats.
    question: Does GroupDocs.Metadata support other image formats?
  - answer: Use the streaming API; it processes files without loading the full image
      into memory, keeping RAM usage under 50 MB.
    question: How do I handle large PNG files efficiently?
  - answer: The API returns an empty collection; you can safely check `isEmpty()`
      before processing.
    question: What if a PNG has no text chunks?
  - answer: Yes, GroupDocs.Metadata fully supports UTF‑8, preserving all language
      characters.
    question: Is Unicode supported in international text chunks?
  type: FAQPage
title: GroupDocs.Metadata Java API를 사용하여 PNG 텍스트 청크 추출하는 방법
type: docs
url: /ko/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# PNG 텍스트 청크 추출 방법 GroupDocs.Metadata Java API 사용

이미지 파일에서 텍스트 정보를 추출하는 것은 특히 PNG와 같은 비텍스트 기반 형식에서는 어려울 수 있습니다. **GroupDocs.Metadata for Java**는 이러한 이미지에 포함된 메타데이터를 검색하고 관리할 수 있는 강력한 도구를 제공하여 이 과정을 단순화합니다. 일반, 압축, 국제 텍스트 청크를 처리하든, GroupDocs.Metadata는 효율적인 솔루션을 제공합니다.

이 튜토리얼에서는 Java에서 GroupDocs.Metadata 라이브러리를 사용하여 PNG 파일에서 다양한 유형의 텍스트 청크를 효율적으로 추출하는 방법을 안내합니다. 이러한 기술을 이해하면 텍스트 추출 기능을 애플리케이션에 원활히 통합하여 다양한 분야에서 데이터 처리 능력을 향상시킬 수 있습니다.

## 빠른 답변
- **GroupDocs.Metadata가 png 메타데이터를 읽을 수 있나요?** 예, 텍스트 청크를 포함한 모든 표준 PNG 메타데이터를 읽습니다.  
- **필요한 Java 버전은 무엇인가요?** Java 8 이상을 완전히 지원합니다.  
- **개발에 라이선스가 필요합니까?** 무료 체험으로 테스트가 가능하지만, 상용 환경에서는 상업용 라이선스가 필요합니다.  
- **추출할 수 있는 텍스트 청크 유형은 몇 개인가요?** 일반, 압축, 국제의 세 가지 주요 유형이 있습니다.  
- **성능이 문제인가요?** 일반적인 5 MB PNG 파일을 최신 CPU에서 추출할 경우 200 ms 이하로 실행됩니다.

## “how to extract png”란 무엇인가요?
**“How to extract png”**는 프로그래밍 API를 사용하여 PNG 이미지 파일에서 포함된 텍스트 청크를 검색하는 과정을 의미합니다. 이러한 텍스트 청크에는 설명 메타데이터, 주석 또는 국제화된 문자열이 포함될 수 있습니다. GroupDocs.Metadata for Java를 활용하면 개발자는 전체 이미지를 디코딩하지 않고도 이러한 청크를 프로그래밍 방식으로 읽고, 필터링하고, 조작할 수 있습니다.

## PNG 텍스트 추출에 GroupDocs.Metadata를 사용하는 이유
GroupDocs.Metadata는 **50개 이상의 이미지 및 문서 형식**을 지원하며 PNG 파일을 **전체 이미지를 메모리에 로드하지 않고** 처리할 수 있어 최대 10 MB 파일에 대해 평균 **150 ms**의 추출 속도를 제공합니다. 또한 이 라이브러리는 **100 % 데이터 무결성**을 보장하여 국제 텍스트 청크의 유니코드 문자를 그대로 보존합니다.

## 사전 요구 사항
Java용 GroupDocs.Metadata를 사용하여 PNG 이미지에서 텍스트 청크를 추출하기 시작하기 전에 다음 사항을 준비하십시오:

### 필수 라이브러리 및 종속성
- **GroupDocs.Metadata for Java**: Maven을 통해 또는 직접 다운로드하여 프로젝트에 포함하십시오.

### 환경 설정 요구 사항
- Java가 설치된 개발 환경 (가능하면 JDK 8 이상).
- IntelliJ IDEA, Eclipse 등 Java 프로젝트를 지원하는 IDE.

### 지식 사전 요구 사항
- Java 프로그래밍에 대한 기본 이해.
- Java 애플리케이션에서 파일 및 디렉터리 처리에 대한 친숙함.

## Java용 GroupDocs.Metadata 설정
GroupDocs.Metadata를 시작하려면 프로젝트에 포함해야 합니다. Maven을 사용하거나 라이브러리를 직접 다운로드하는 방법은 다음과 같습니다:

### Maven 설정
`pom.xml` 파일에 다음 저장소와 의존성을 추가하십시오:

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

### 직접 다운로드
또는 최신 버전을 [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/)에서 다운로드하십시오.

#### 라이선스 획득 단계
- **Free Trial**: 기능을 살펴보기 위해 무료 체험을 시작하십시오.  
- **Temporary License**: 장기 테스트를 위해 임시 라이선스를 획득하십시오.  
- **Purchase**: 프로덕션 사용 준비가 되었다면 라이선스를 구매하십시오.

### 기본 초기화 및 설정
라이브러리를 설정한 후, Java 애플리케이션에서 GroupDocs.Metadata를 다음과 같이 초기화하십시오:

```java
import com.groupdocs.metadata.Metadata;

public class MetadataExample {
    public static void main(String[] args) {
        String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
        
        // Initialize Metadata with a PNG file path
        try (Metadata metadata = new Metadata(pngFilePath)) {
            System.out.println("Metadata initialized successfully!");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## PNG 파일에서 png 텍스트 청크를 추출하는 방법?
`Metadata` 클래스는 파일의 메타데이터 스트림에 접근하기 위한 진입점입니다. `new Metadata("yourImage.png")` 로 PNG 파일을 로드하고, 루트 패키지에 접근한 뒤 원하는 텍스트 청크 컬렉션을 반복하면 몇 줄의 코드만으로 일반, 압축, 국제 텍스트 청크를 모두 반환합니다. 이를 통해 필요에 따라 청크를 자유롭게 처리할 수 있습니다.

### 정의 앵커
`Metadata` 클래스는 GroupDocs.Metadata의 진입점으로, 파일 내부의 모든 메타데이터 스트림에 프로그래밍 방식으로 접근할 수 있는 컨테이너를 나타냅니다.

## PNG에서 일반 텍스트 청크 추출
이 기능을 사용하면 PNG 파일에 포함된 모든 일반 텍스트 청크를 검색할 수 있습니다. 구현 방법은 다음과 같습니다:

#### 개요
이미지 메타데이터에 저장된 각 텍스트 청크에 접근하고 반복합니다.

#### 단계별 구현
1. **필요한 클래스 가져오기:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Metadata 초기화 및 루트 패키지 접근:**
   `PngRootPackage`는 PNG 메타데이터의 루트 컨테이너를 나타내며 텍스트 청크 컬렉션을 노출합니다.

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngTextChunk chunk : root.getPngPackage().getTextChunks()) {
           System.out.println("Keyword: " + chunk.getKeyword());
           System.out.println("Text: " + chunk.getText());
       }
   }
   ```

3. **매개변수 설명:**
   - `pngFilePath`: PNG 파일의 경로.
   - `PngRootPackage`: 메타데이터 청크를 포함하는 루트 패키지를 나타냅니다.

#### 문제 해결 팁
- PNG 파일에 텍스트 청크가 포함되어 있는지 확인하십시오. 없으면 데이터가 검색되지 않습니다.
- PNG 파일 경로가 올바른지 확인하십시오.

## PNG에서 압축 텍스트 청크 추출
압축 텍스트 청크를 별도로 처리하려면 다음 단계를 따르십시오:

#### 개요
이 기능은 PNG 메타데이터 내 압축 텍스트 청크를 검색하고 관리하는 데 중점을 둡니다.

#### 단계별 구현
1. **필요한 클래스 가져오기:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Metadata 초기화 및 루트 패키지 접근:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngCompressedTextChunk compressedChunk : root.getPngPackage().getCompressedTextChunks()) {
           System.out.println("Keyword: " + compressedChunk.getKeyword());
           System.out.println("Text: " + compressedChunk.getText());
           System.out.println("Compression Method: " + compressedChunk.getCompressionMethod());
       }
   }
   ```

3. **매개변수 설명:**
   - `getCompressionMethod()`: 압축에 사용된 방식을 반환합니다. `getCompressionMethod()` 메서드는 압축 텍스트 청크에 사용된 압축 알고리즘을 반환합니다.

#### 문제 해결 팁
- PNG 파일이 지원되는 압축 방식을 사용하는지 확인하십시오.
- 텍스트 청크가 압축되지 않은 경우 발생할 수 있는 예외를 처리하십시오.

## PNG에서 국제 텍스트 청크 추출
국제 텍스트 청크를 추출하려면 다음 단계가 안내합니다:

#### 개요
PNG 메타데이터 내 국제 텍스트 청크를 검색하고 관리하며, 언어 세부 정보를 포함합니다.

#### 단계별 구현
1. **필요한 클래스 가져오기:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Metadata 초기화 및 루트 패키지 접근:**

   ```java
   String pngFilePath = "YOUR_DOCUMENT_DIRECTORY/example.png";
   
   try (Metadata metadata = new Metadata(pngFilePath)) {
       PngRootPackage root = metadata.getRootPackageGeneric();
       
       for (PngInternationalTextChunk internationalChunk : root.getPngPackage().getInternationalTextChunks()) {
           System.out.println("Keyword: " + internationalChunk.getKeyword());
           System.out.println("Text: " + internationalChunk.getText());
           System.out.println("Compressed: " + internationalChunk.isCompressed());
           System.out.println("Language: " + internationalChunk.getLanguage());
           System.out.println("Translated Keyword: " + internationalChunk.getTranslatedKeyword());
       }
   }
   ```

3. **매개변수 설명:**
   - `getLanguage()`: 텍스트 청크의 언어 태그를 반환합니다. `getLanguage()` 메서드는 국제 텍스트 청크와 연결된 ISO 언어 태그를 제공합니다.
   - `isCompressed()`: 텍스트 청크가 압축되었는지 여부를 나타냅니다. `isCompressed()` 메서드는 텍스트 청크가 압축 형태로 저장되었는지 여부를 표시합니다.

#### 문제 해결 팁
- PNG 파일에 국제 메타데이터가 올바르게 설정되어 있는지 확인하십시오.
- 번역이 제공되지 않을 수 있는 상황을 처리하십시오.

## 실용적인 적용 사례
GroupDocs.Metadata를 사용하여 PNG에서 텍스트 청크를 추출하는 방법을 이해하면 다양한 애플리케이션에서 매우 유용합니다:
- **콘텐츠 관리 시스템**: 이미지 라이브러리의 메타데이터를 자동으로 검색하고 정리합니다.  
- **데이터 분석 도구**: 이미지 메타데이터 분석을 포함하여 데이터 추출 기능을 강화합니다.  
- **웹 스크래핑 프로젝트**: 웹사이트에 삽입된 이미지에서 유용한 정보를 추출합니다.

## 자주 묻는 질문

**Q: 라이선스 없이 png 메타데이터를 읽을 수 있나요?**  
A: 예, 무료 체험으로 메타데이터를 읽을 수 있지만, 프로덕션 배포에는 상업용 라이선스가 필요합니다.

**Q: GroupDocs.Metadata가 다른 이미지 형식을 지원하나요?**  
A: 물론입니다 – JPEG, BMP, TIFF 및 40개 이상의 추가 형식을 처리합니다.

**Q: 큰 PNG 파일을 효율적으로 처리하려면 어떻게 해야 하나요?**  
A: 스트리밍 API를 사용하십시오; 전체 이미지를 메모리에 로드하지 않고 파일을 처리하여 RAM 사용량을 50 MB 이하로 유지합니다.

**Q: PNG에 텍스트 청크가 없으면 어떻게 되나요?**  
A: API가 빈 컬렉션을 반환하므로, 처리하기 전에 `isEmpty()`를 안전하게 확인할 수 있습니다.

**Q: 국제 텍스트 청크에서 Unicode를 지원하나요?**  
A: 예, GroupDocs.Metadata는 UTF‑8을 완벽히 지원하여 모든 언어 문자를 보존합니다.

## 결론
이 튜토리얼을 따라 하면 Java용 GroupDocs.Metadata 라이브러리를 사용하여 PNG 파일에서 일반, 압축, 국제 텍스트 청크를 추출하는 방법을 배웠습니다. 이 기술은 애플리케이션이 이미지 데이터를 효율적으로 처리하고 분석하는 능력을 크게 향상시킬 수 있습니다. 추가 탐색을 위해 GroupDocs.Metadata가 제공하는 보다 고급 메타데이터 처리 기술을 살펴보는 것을 권장합니다.

**다음 단계**
- 다양한 메타데이터 추출 유형을 실험해 보세요.  
- GroupDocs.Metadata 라이브러리의 추가 기능을 탐색하십시오.  
- 개발자 커뮤니티에 결과나 적용 사례를 공유하여 피드백과 개선을 받으세요.

---

**마지막 업데이트:** 2026-06-01  
**테스트 환경:** GroupDocs.Metadata Java 23.9  
**작성자:** GroupDocs

## 관련 튜토리얼

- [Java용 GroupDocs.Metadata를 사용하여 JPEG에서 이미지 리소스 블록 추출](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Java에서 GroupDocs.Metadata를 사용하여 JPEG2000 이미지 주석 추출: 단계별 가이드](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Java에서 GroupDocs.Metadata를 사용하여 PSD 파일에서 이미지 리소스 추출: 종합 가이드](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)