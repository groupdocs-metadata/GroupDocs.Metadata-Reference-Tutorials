---
date: '2026-08-10'
description: Java용 GroupDocs.Metadata를 사용하여 PSD 파일에서 EXIF 메타데이터를 추출하는 방법을 배웁니다. 이
  가이드는 기본 추출, IFD 패키지, GPS 데이터 및 실제 사용 사례를 다룹니다.
keywords:
- how to extract exif
- how to read exif
- java extract image exif
lastmod: '2026-08-10'
og_description: Java용 GroupDocs.Metadata를 사용하여 PSD 파일에서 EXIF 메타데이터를 추출하는 방법을 배웁니다.
  단계별 가이드, 코드 스니펫 및 개발자를 위한 문제 해결 팁을 제공합니다.
og_image_alt: Guide showing Java code extracting EXIF data from a PSD file with GroupDocs.Metadata
og_title: GroupDocs.Metadata를 사용하여 PSD 파일에서 EXIF 메타데이터 추출하는 방법
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  headline: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  type: TechArticle
- description: Learn how to extract EXIF metadata from PSD files using GroupDocs.Metadata
    for Java. This guide covers basic extraction, IFD packages, GPS data, and real‑world
    use cases.
  name: How to extract EXIF metadata from PSD files with GroupDocs.Metadata
  steps:
  - name: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
    text: Visit the [License Purchase Page](https://purchase.groupdocs.com/temporary-license).
  - name: Choose **temporary** for testing or **full** for production.
    text: Choose **temporary** for testing or **full** for production.
  - name: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
    text: Follow the on‑screen instructions to embed the license file (`metadata.lic`)
      in your Java classpath.
  - name: '**Create a `Metadata` instance** pointing at your PSD file.'
    text: '**Create a `Metadata` instance** pointing at your PSD file.'
  - name: '**Call `getExif()`** to obtain the EXIF container.'
    text: '**Call `getExif()`** to obtain the EXIF container.'
  - name: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
    text: '**Read individual properties** like `getArtist()`, `getCopyright()`, and
      `getSoftware()`.'
  - name: '**Print or store** the values according to your application logic.'
    text: '**Print or store** the values according to your application logic.'
  - name: '**Reuse the `Metadata` instance** from the previous section.'
    text: '**Reuse the `Metadata` instance** from the previous section.'
  - name: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
    text: '**Navigate to the IFD container** via `metadata.getExif().getIfd0()`.'
  - name: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
    text: '**Read properties** like `getBodySerialNumber()` and `getUserComment()`.'
  type: HowTo
- questions:
  - answer: Yes. Load the file with `new Metadata("file.psd", "password")` and then
      access the EXIF data as usual.
    question: Can I extract EXIF metadata from a password‑protected PSD file?
  - answer: Absolutely. Instantiate a `Metadata` object inside a loop, or use the
      `MetadataCollection` helper to process directories efficiently.
    question: Does GroupDocs.Metadata support batch processing of many PSD files?
  - answer: Java 8 through Java 21 are fully tested. The library uses only standard
      APIs, so it works on any compliant JVM.
    question: What Java versions are officially supported?
  - answer: Yes. After modifying properties via the `Exif` object, call `metadata.save("output.psd")`
      to persist changes.
    question: Is it possible to write EXIF data back into a PSD file?
  - answer: GroupDocs.Metadata streams data and can process files up to **2 GB** on
      a typical 8 GB RAM machine, thanks to its low‑memory architecture.
    question: How large a PSD file can the library handle without running out of memory?
  type: FAQPage
tags:
- exif metadata
- groupdocs.metadata
- java image processing
- psd file handling
title: GroupDocs.Metadata를 사용하여 PSD 파일에서 EXIF 메타데이터 추출하는 방법
type: docs
url: /ko/java/metadata-standards/extract-exif-metadata-psd-groupdocs-java/
weight: 1
---

# GroupDocs.Metadata를 사용하여 PSD 파일에서 EXIF 메타데이터 추출하는 방법

PSD 파일에서 **EXIF 메타데이터**를 추출하는 것은 이미지 출처를 감사하거나, 자산 태깅을 자동화하거나, 검색 가능한 미디어 라이브러리를 구축해야 할 때 일상적이면서도 강력한 단계입니다. 이 튜토리얼에서는 GroupDocs.Metadata for Java를 사용하여 **EXIF를 빠르게 추출**하는 방법을 알아보고, 정확한 API 호출을 확인하며, 고급 IFD 패키지와 GPS 좌표를 처리하는 방법을 배웁니다. 끝까지 읽으면 메타데이터 추출을 모든 Java 기반 워크플로에 통합할 준비가 됩니다.

## 빠른 답변
`Metadata` 클래스는 파일을 나타내며 해당 메타데이터에 접근할 수 있게 합니다.

- **첫 번째 코드 라인은 무엇인가요?** `Metadata metadata = new Metadata("sample.psd");`
- **아티스트 이름을 반환하는 메서드는 무엇인가요?** `metadata.getExif().getArtist();`
- **GPS 데이터를 읽을 수 있나요?** 예 – `metadata.getExif().getGpsInfo();` 사용
- **프로덕션에 라이선스가 필요합니까?** 유효한 GroupDocs.Metadata 라이선스가 체험 기간 이후에 필요합니다.
- **지원되는 Java 버전은?** Java 8 이상 (Java 21까지).

## EXIF 메타데이터란?
EXIF(Exchangeable Image File Format) 메타데이터는 이미지 파일 내부에 카메라 설정, 생성 타임스탬프, 위치 데이터를 저장합니다. GroupDocs.Metadata는 PSD 파일의 바이너리 구조에서 이 정보를 직접 읽어들여 깔끔한 Java API를 통해 제공합니다. 이를 통해 개발자는 카메라 모델, 노출 시간, GPS 좌표와 같은 세부 정보를 수동 검사 없이 프로그래밍 방식으로 가져올 수 있습니다.

## Java용 GroupDocs.Metadata를 사용하는 이유
GroupDocs.Metadata는 **30개 이상의 파일 형식**(PSD, JPEG, PNG, TIFF 포함)을 지원하며 전체 문서를 메모리에 로드하지 않고 **2 GB**까지의 파일을 처리할 수 있습니다. 이 라이브러리는 **150개가 넘는 고유 EXIF 태그**를 추출하여 분석이나 규정 준수에 필요한 카메라 및 GPS 속성 전체를 제공한다는 것을 보장합니다.

## 사전 요구 사항
- **Java Development Kit (JDK) 8** 이상이 머신에 설치되어 있어야 합니다.  
- 의존성 관리를 위한 **Maven**.  
- **GroupDocs.Metadata for Java 버전 24.12** (또는 최신 버전).  
- Java 클래스, 객체 및 예외 처리에 대한 기본적인 이해.

### 필요한 라이브러리 및 의존성
| 의존성 | Maven 좌표 |
|------------|-------------------|
| GroupDocs.Metadata | `com.groupdocs:groupdocs-metadata:24.12` |

### 환경 설정
IntelliJ IDEA 또는 Eclipse와 같은 Maven 호환 IDE가 필요합니다. 새 Maven 프로젝트를 만들거나 기존 프로젝트에 의존성을 추가하십시오.

## Java용 GroupDocs.Metadata 설정 방법
GroupDocs.Metadata는 몇 줄의 설정만으로 Maven 프로젝트에 추가할 수 있습니다. 다음 단계에서는 저장소와 의존성을 포함시켜 라이브러리를 클래스패스에 사용할 수 있게 하는 방법을 보여줍니다.

### Maven 설정
Add the following snippet to your `pom.xml` inside the `<dependencies>` section:

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
또는 공식 릴리스 페이지에서 최신 JAR를 다운로드하십시오: [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### 라이선스 획득
To run the library beyond the 30‑day trial, obtain a temporary or full license:

1. 라이선스 구매 페이지([License Purchase Page](https://purchase.groupdocs.com/temporary-license))를 방문하십시오.  
2. 테스트용 **temporary** 또는 프로덕션용 **full**을 선택하십시오.  
3. 화면 지침에 따라 라이선스 파일(`metadata.lic`)을 Java 클래스패스에 포함시키십시오.

### 기본 초기화 및 설정
After the library is on the classpath, initialize it as shown below:

```java
import com.groupdocs.metadata.*;

public class MetadataSetup {
    public static void main(String[] args) {
        // Initialize metadata handling
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd")) {
            System.out.println("Metadata initialized successfully.");
        }
    }
}
```

## PSD 이미지에서 기본 EXIF 메타데이터 속성 추출 방법
이 섹션에서는 PSD 파일을 로드하고 EXIF 컨테이너에 접근하여 **artist**, **copyright**, **software**와 같은 가장 일반적인 태그를 읽는 방법을 설명합니다. 이 과정은 `Metadata` 인스턴스를 생성하고 `getExif()`를 호출한 뒤 간단한 getter 메서드로 개별 속성을 가져오는 것을 포함합니다.

### 단계별 구현
1. **PSD 파일을 가리키는 `Metadata` 인스턴스를 생성**합니다.  
2. **`getExif()`를 호출**하여 EXIF 컨테이너를 얻습니다.  
3. `getArtist()`, `getCopyright()`, `getSoftware()`와 같은 **개별 속성을 읽습니다**.  
4. **값을 출력하거나 저장**합니다(응용 프로그램 로직에 따라).

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractBasicExifProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null) {
                // Access and print basic EXIF properties
                String artist = root.getExifPackage().getArtist();
                System.out.println("Artist: " + artist);
                
                String copyright = root.getExifPackage().getCopyright();
                System.out.println("Copyright: " + copyright);
                
                String imageDescription = root.getExifPackage().getImageDescription();
                System.out.println("Image Description: " + imageDescription);
                
                String make = root.getExifPackage().getMake();
                System.out.println("Make: " + make);
                
                String model = root.getExifPackage().getModel();
                System.out.println("Model: " + model);
                
                String software = root.getExifPackage().getSoftware();
                System.out.println("Software: " + software);
                
                int imageWidth = root.getExifPackage().getImageWidth();
                System.out.println("Image Width: " + imageWidth);
                
                int imageLength = root.getExifPackage().getImageLength();
                System.out.println("Image Length: " + imageLength);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

> **팁:** `Metadata` 객체는 파일 형식을 자동으로 감지하므로 JPEG 또는 TIFF 파일에 대해 코드를 수정 없이 재사용할 수 있습니다.

## PSD 이미지에서 EXIF IFD 패키지 속성 추출 방법
IFD(Image File Directory) 섹션에는 **카메라 시리얼 번호**, **렌즈 모델**, **사용자 코멘트**와 같은 보다 깊은 기술 세부 정보가 포함됩니다. `Ifd0`는 기본 카메라 정보를 포함하는 주요 Image File Directory를 나타냅니다. 이러한 필드를 추출하면 포렌식 분석이나 고정밀 카탈로그 작성에 유용합니다.

### 구현 단계
1. **이전 섹션에서 만든 `Metadata` 인스턴스를 재사용**합니다.  
2. `metadata.getExif().getIfd0()`를 통해 **IFD 컨테이너로 이동**합니다.  
3. `getBodySerialNumber()` 및 `getUserComment()`와 같은 **속성을 읽습니다**.  
4. **데이터를 출력**하거나 도메인 모델에 매핑합니다.

```java
import com.groupdocs.metadata.Metadata;
import com.groupdocs.metadata.core.PsdRootPackage;

public class ExtractExifIfdProperties {
    public static void main(String[] args) {
        String documentPath = "YOUR_DOCUMENT_DIRECTORY/PsdWithExif.psd";
        
        try (Metadata metadata = new Metadata(documentPath)) {
            PsdRootPackage root = metadata.getRootPackageGeneric();
            if (root.getExifPackage() != null && root.getExifPackage().getExifIfdPackage() != null) {
                // Access and print EXIF IFD package properties
                String bodySerialNumber = root.getExifPackage().getExifIfdPackage().getBodySerialNumber();
                System.out.println("Body Serial Number: " + bodySerialNumber);
                
                String cameraOwnerName = root.getExifPackage().getExifIfdPackage().getCameraOwnerName();
                System.out.println("Camera Owner Name: " + cameraOwnerName);
                
                String userComment = root.getExifPackage().getExifIfdPackage().getUserComment();
                System.out.println("User Comment: " + userComment);
            }
        } catch (Exception e) {
            System.err.println("Error occurred while extracting metadata: " + e.getMessage());
        }
    }
}
```

## PSD 파일에서 GPS 데이터(위도, 경도) 가져오기
많은 최신 카메라가 EXIF 블록에 GPS 좌표를 삽입합니다. `GpsInfo`는 EXIF 데이터에서 추출한 지리 좌표를 보관합니다. `metadata.getExif().getGpsInfo()`를 호출한 뒤 `getLatitude()`, `getLongitude()`, `getAltitude()`를 사용하면 추가 파싱 없이 정확한 위치 데이터를 얻을 수 있습니다.

### 상세 단계
1. **GPS 정보 객체를 얻습니다**: `GpsInfo gps = metadata.getExif().getGpsInfo();`  
2. **위도와 경도를 읽습니다**: `gps.getLatitude()`는 십진수 도 형태의 `double`을 반환합니다.  
3. **누락된 데이터를 처리합니다**: 태그가 없을 경우 API가 `null`을 반환하므로 `NullPointerException`을 방지해야 합니다.  

> **일반적인 함정:** 일부 PSD 파일은 GPS 좌표를 유리수 형태로 저장합니다; 라이브러리가 자동으로 정규화하지만, 오래된 파일은 수동 변환이 필요할 수 있습니다.

## 일반적인 문제 및 해결 방법
| 증상 | 가능한 원인 | 해결 방법 |
|---------|--------------|-----|
| `Unsupported format` exception | PSD를 인식하지 못하는 오래된 GroupDocs.Metadata 버전을 사용하고 있음 | 버전을 24.12 이상으로 업그레이드하십시오. |
| `NullPointerException` when calling `getArtist()` | 소스 파일에 EXIF 태그가 존재하지 않음 | `metadata.getExif().hasArtist()`를 확인한 후 읽으십시오. |
| License error after 30 days | 클래스패스에 라이선스 파일을 찾을 수 없음 | `metadata.lic`를 `src/main/resources`에 두거나 `Metadata.setLicense("path/to/license")`를 설정하십시오. |

## 자주 묻는 질문

**Q: 비밀번호로 보호된 PSD 파일에서 EXIF 메타데이터를 추출할 수 있나요?**  
A: 예. `new Metadata("file.psd", "password")`로 파일을 로드한 뒤 일반적으로 EXIF 데이터를 접근하면 됩니다.

**Q: GroupDocs.Metadata가 많은 PSD 파일의 배치 처리를 지원하나요?**  
A: 물론입니다. 루프 안에서 `Metadata` 객체를 인스턴스화하거나 `MetadataCollection` 헬퍼를 사용해 디렉터리를 효율적으로 처리하십시오.

**Q: 공식적으로 지원되는 Java 버전은 무엇인가요?**  
A: Java 8부터 Java 21까지 완전히 테스트되었습니다. 라이브러리는 표준 API만 사용하므로 호환되는 모든 JVM에서 동작합니다.

**Q: EXIF 데이터를 PSD 파일에 다시 쓸 수 있나요?**  
A: 예. `Exif` 객체를 통해 속성을 수정한 후 `metadata.save("output.psd")`를 호출하면 변경 사항이 저장됩니다.

**Q: 메모리 부족 없이 라이브러리가 처리할 수 있는 PSD 파일 최대 크기는 얼마인가요?**  
A: GroupDocs.Metadata는 데이터를 스트리밍하며 일반적인 8 GB RAM 머신에서 **2 GB**까지 파일을 처리할 수 있습니다. 이는 저메모리 아키텍처 덕분입니다.

## 결론
이제 GroupDocs.Metadata for Java를 사용하여 PSD 파일에서 **EXIF 메타데이터를 추출**하는 방법을 기본 태그부터 고급 IFD 및 GPS 정보까지 알게 되었습니다. 이러한 코드를 이미지 처리 파이프라인에 통합하면 카탈로그 자동화, 규정 준수 검사 또는 위치 기반 서비스를 자동화할 수 있습니다. 더 깊이 탐구하려면 다른 지원 형식(JPEG, TIFF, PNG)에서 메타데이터를 추출하거나 쓰기 기능을 실험하여 사용자 정의 태그를 삽입해 보십시오.

---

**마지막 업데이트:** 2026-08-10  
**테스트 환경:** GroupDocs.Metadata 24.12 for Java  
**작성자:** GroupDocs

## 관련 튜토리얼

- [Java에서 GroupDocs.Metadata를 사용하여 PSD 파일에서 이미지 리소스 추출: 종합 가이드](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)
- [Java용 GroupDocs.Metadata를 사용하여 PSD 헤더 및 레이어 정보 추출: 종합 가이드](/metadata/java/image-formats/extract-psd-header-layer-info-groupdocs-metadata/)
- [Java에서 GroupDocs.Metadata를 사용하여 MakerNote 속성을 TIFF/EXIF 태그로 추출](/metadata/java/image-formats/groupdocs-metadata-java-makernote-extraction/)