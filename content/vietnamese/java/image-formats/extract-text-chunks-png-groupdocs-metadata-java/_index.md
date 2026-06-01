---
date: '2026-06-01'
description: Tìm hiểu cách trích xuất các khối văn bản png với GroupDocs.Metadata
  cho Java – đọc siêu dữ liệu png một cách hiệu quả và tích hợp xử lý hình ảnh mạnh
  mẽ.
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
title: Cách trích xuất các khối văn bản PNG bằng GroupDocs.Metadata Java API
type: docs
url: /vi/java/image-formats/extract-text-chunks-png-groupdocs-metadata-java/
weight: 1
---

# Cách Trích Xuất Các Đoạn Văn Bản PNG Sử Dụng GroupDocs.Metadata Java API

Việc trích xuất thông tin văn bản từ các tệp hình ảnh có thể gặp khó khăn, đặc biệt đối với các định dạng không dựa trên văn bản như PNG. **GroupDocs.Metadata for Java** đơn giản hoá quá trình này bằng cách cung cấp các công cụ mạnh mẽ để lấy và quản lý siêu dữ liệu nhúng trong các hình ảnh này. Cho dù bạn đang xử lý các đoạn văn bản chung, nén hoặc quốc tế, GroupDocs.Metadata cung cấp các giải pháp tối ưu.

Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách trích xuất hiệu quả các loại đoạn văn bản khác nhau từ tệp PNG bằng thư viện GroupDocs.Metadata trong Java. Bằng cách hiểu các kỹ thuật này, bạn có thể tích hợp liền mạch tính năng trích xuất văn bản vào ứng dụng của mình, nâng cao khả năng xử lý dữ liệu trong nhiều lĩnh vực.

## Câu trả lời nhanh
- **GroupDocs.Metadata có thể đọc siêu dữ liệu png không?** Có, nó đọc tất cả siêu dữ liệu PNG tiêu chuẩn, bao gồm các đoạn văn bản.  
- **Phiên bản Java nào được yêu cầu?** Java 8 hoặc mới hơn được hỗ trợ đầy đủ.  
- **Tôi có cần giấy phép cho việc phát triển không?** Bản dùng thử miễn phí hoạt động cho việc thử nghiệm; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Có bao nhiêu loại đoạn văn bản có thể được trích xuất?** Ba loại chính: chung, nén và quốc tế.  
- **Hiệu suất có phải là mối quan tâm không?** Việc trích xuất diễn ra dưới 200 ms cho các PNG 5 MB điển hình trên CPU hiện đại.

## “how to extract png” là gì?
**“How to extract png”** đề cập đến quá trình lấy các đoạn văn bản nhúng từ tệp ảnh PNG bằng các API lập trình. Các đoạn văn bản này có thể chứa siêu dữ liệu mô tả, bình luận hoặc chuỗi quốc tế hoá. Bằng cách tận dụng GroupDocs.Metadata for Java, các nhà phát triển có thể đọc, lọc và thao tác các đoạn này một cách lập trình mà không cần giải mã toàn bộ hình ảnh.

## Tại sao nên sử dụng GroupDocs.Metadata để trích xuất văn bản PNG?
GroupDocs.Metadata hỗ trợ **hơn 50 định dạng hình ảnh và tài liệu** và có thể xử lý các tệp PNG **không cần tải toàn bộ hình ảnh vào bộ nhớ**, mang lại tốc độ trích xuất trung bình **150 ms** cho các tệp lên tới 10 MB. Thư viện cũng đảm bảo **độ chính xác dữ liệu 100 %**, bảo tồn các ký tự Unicode trong các đoạn văn bản quốc tế.

## Yêu cầu trước

Trước khi bắt đầu trích xuất các đoạn văn bản từ hình ảnh PNG bằng GroupDocs.Metadata cho Java, hãy đảm bảo bạn có những thứ sau:

### Thư viện và phụ thuộc cần thiết
- **GroupDocs.Metadata for Java**: Bao gồm thư viện này trong dự án của bạn qua Maven hoặc tải trực tiếp.

### Yêu cầu thiết lập môi trường
- Môi trường phát triển đã cài đặt Java (tốt nhất là JDK 8 hoặc mới hơn).
- Một IDE như IntelliJ IDEA, Eclipse, hoặc bất kỳ công cụ nào hỗ trợ dự án Java.

### Kiến thức tiên quyết
- Hiểu biết cơ bản về lập trình Java.
- Quen thuộc với việc xử lý tệp và thư mục trong ứng dụng Java.

## Cài đặt GroupDocs.Metadata cho Java

Để bắt đầu với GroupDocs.Metadata, bạn cần đưa nó vào dự án. Dưới đây là cách thực hiện bằng Maven hoặc tải thư viện trực tiếp:

### Cấu hình Maven
Thêm repository và dependency sau vào tệp `pom.xml` của bạn:

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

### Tải trực tiếp
Ngoài ra, tải phiên bản mới nhất từ [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Các bước lấy giấy phép
- **Free Trial**: Bắt đầu với bản dùng thử miễn phí để khám phá các tính năng.  
- **Temporary License**: Nhận giấy phép tạm thời để thử nghiệm kéo dài hơn.  
- **Purchase**: Mua giấy phép nếu bạn đã sẵn sàng cho việc sử dụng trong môi trường sản xuất.

### Khởi tạo và cấu hình cơ bản

Sau khi thiết lập thư viện, khởi tạo GroupDocs.Metadata trong ứng dụng Java của bạn như sau:

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

## Cách trích xuất các đoạn văn bản png từ tệp PNG?

Lớp `Metadata` là điểm vào để truy cập các luồng siêu dữ liệu của tệp. Tải tệp PNG bằng `new Metadata("yourImage.png")`, truy cập gói gốc và lặp qua các bộ sưu tập đoạn văn bản mong muốn – chỉ trong vài dòng mã. Cách tiếp cận này trả về mọi đoạn văn bản chung, nén và quốc tế, cho phép bạn xử lý chúng theo nhu cầu.

### Định nghĩa
Lớp `Metadata` là điểm vào của GroupDocs.Metadata, đại diện cho một container cung cấp cho bạn quyền truy cập lập trình vào tất cả các luồng siêu dữ liệu bên trong một tệp.

## Trích xuất các đoạn văn bản chung từ PNG

Tính năng này cho phép bạn lấy tất cả các đoạn văn bản chung được nhúng trong tệp PNG. Dưới đây là cách thực hiện:

#### Tổng quan
Bạn sẽ truy cập và lặp qua mỗi đoạn văn bản được lưu trong siêu dữ liệu hình ảnh.

#### Hướng dẫn từng bước
1. **Import Necessary Classes:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:** `PngRootPackage` đại diện cho container gốc của siêu dữ liệu PNG, mở ra các bộ sưu tập đoạn văn bản.

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

3. **Explanation of Parameters:**
   - `pngFilePath`: Đường dẫn tới tệp PNG của bạn.
   - `PngRootPackage`: Đại diện cho gói gốc chứa các đoạn siêu dữ liệu.

#### Mẹo khắc phục sự cố
- Đảm bảo các tệp PNG của bạn chứa các đoạn văn bản; nếu không, sẽ không có dữ liệu nào được lấy.
- Kiểm tra lại đường dẫn tới tệp PNG là đúng.

## Trích xuất các đoạn văn bản nén từ PNG

Để xử lý các đoạn văn bản nén một cách cụ thể, hãy làm theo các bước sau:

#### Tổng quan
Tính năng này tập trung vào việc lấy và quản lý các đoạn văn bản nén trong siêu dữ liệu PNG.

#### Hướng dẫn từng bước
1. **Import Necessary Classes:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngCompressedTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**

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

3. **Explanation of Parameters:**
   - `getCompressionMethod()`: Trả về phương pháp được sử dụng để nén. Phương thức `getCompressionMethod()` trả về thuật toán nén được dùng cho một đoạn văn bản nén.

#### Mẹo khắc phục sự cố
- Đảm bảo các tệp PNG của bạn sử dụng phương pháp nén được hỗ trợ.
- Xử lý các ngoại lệ khi các đoạn văn bản có thể không được nén.

## Trích xuất các đoạn văn bản quốc tế từ PNG

Đối với việc trích xuất các đoạn văn bản quốc tế, các bước sau sẽ hướng dẫn bạn:

#### Tổng quan
Lấy và quản lý các đoạn văn bản quốc tế trong siêu dữ liệu PNG, bao gồm chi tiết ngôn ngữ.

#### Hướng dẫn từng bước
1. **Import Necessary Classes:**

   ```java
   import com.groupdocs.metadata.Metadata;
   import com.groupdocs.metadata.core.PngInternationalTextChunk;
   import com.groupdocs.metadata.core.PngRootPackage;
   ```

2. **Initialize Metadata and Access Root Package:**

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

3. **Explanation of Parameters:**
   - `getLanguage()`: Lấy thẻ ngôn ngữ cho đoạn văn bản. Phương thức `getLanguage()` cung cấp thẻ ngôn ngữ ISO liên quan đến một đoạn văn bản quốc tế.
   - `isCompressed()`: Chỉ ra liệu đoạn văn bản có được nén hay không. Phương thức `isCompressed()` cho biết một đoạn văn bản có được lưu dưới dạng nén hay không.

#### Mẹo khắc phục sự cố
- Đảm bảo các tệp PNG của bạn đã thiết lập siêu dữ liệu quốc tế một cách chính xác.
- Xử lý các trường hợp mà bản dịch có thể không có sẵn.

## Ứng dụng thực tiễn

Hiểu cách trích xuất các đoạn văn bản từ PNG bằng GroupDocs.Metadata có thể mang lại giá trị trong nhiều ứng dụng:
- **Content Management Systems**: Tự động lấy và tổ chức siêu dữ liệu cho thư viện hình ảnh.  
- **Data Analysis Tools**: Nâng cao khả năng trích xuất dữ liệu bằng cách bao gồm phân tích siêu dữ liệu hình ảnh.  
- **Web Scraping Projects**: Lấy thông tin có giá trị từ các hình ảnh được nhúng trên website.

## Câu hỏi thường gặp

**Q: Tôi có thể đọc siêu dữ liệu png mà không có giấy phép không?**  
A: Có, bản dùng thử miễn phí cho phép bạn đọc siêu dữ liệu, nhưng giấy phép thương mại cần thiết cho triển khai sản xuất.

**Q: GroupDocs.Metadata có hỗ trợ các định dạng hình ảnh khác không?**  
A: Chắc chắn – nó xử lý JPEG, BMP, TIFF và hơn 40 định dạng bổ sung.

**Q: Làm thế nào để xử lý các tệp PNG lớn một cách hiệu quả?**  
A: Sử dụng API streaming; nó xử lý tệp mà không cần tải toàn bộ hình ảnh vào bộ nhớ, giữ mức sử dụng RAM dưới 50 MB.

**Q: Nếu một PNG không có đoạn văn bản thì sao?**  
A: API trả về một bộ sưu tập rỗng; bạn có thể an toàn kiểm tra `isEmpty()` trước khi xử lý.

**Q: Unicode có được hỗ trợ trong các đoạn văn bản quốc tế không?**  
A: Có, GroupDocs.Metadata hoàn toàn hỗ trợ UTF‑8, bảo tồn tất cả các ký tự ngôn ngữ.

## Kết luận

Bằng cách làm theo hướng dẫn này, bạn đã học cách trích xuất các đoạn văn bản chung, nén và quốc tế từ tệp PNG bằng thư viện GroupDocs.Metadata trong Java. Kỹ năng này có thể nâng cao đáng kể khả năng xử lý và phân tích dữ liệu hình ảnh của ứng dụng. Để khám phá thêm, hãy xem xét các kỹ thuật xử lý siêu dữ liệu nâng cao hơn do GroupDocs.Metadata cung cấp.

**Các bước tiếp theo**
- Thử nghiệm với các loại trích xuất siêu dữ liệu khác nhau.  
- Khám phá các tính năng bổ sung của thư viện GroupDocs.Metadata.  
- Chia sẻ kết quả hoặc ứng dụng của bạn trong cộng đồng nhà phát triển để nhận phản hồi và cải tiến.

---

**Cập nhật lần cuối:** 2026-06-01  
**Kiểm tra với:** GroupDocs.Metadata Java 23.9  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Cách trích xuất các khối tài nguyên hình ảnh từ JPEG bằng GroupDocs.Metadata cho Java](/metadata/java/image-formats/extract-jpeg-image-resource-blocks-groupdocs-metadata-java/)
- [Trích xuất nhận xét hình ảnh JPEG2000 trong Java bằng GroupDocs.Metadata: Hướng dẫn từng bước](/metadata/java/image-formats/extract-jpeg2000-image-comments-java-groupdocs-metadata/)
- [Trích xuất tài nguyên hình ảnh từ tệp PSD bằng GroupDocs.Metadata trong Java: Hướng dẫn toàn diện](/metadata/java/image-formats/extract-image-resources-psd-groupdocs-metadata-java/)