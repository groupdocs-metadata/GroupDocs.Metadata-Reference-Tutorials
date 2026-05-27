---
date: '2026-05-27'
description: Tìm hiểu cách đặt CreatedTime cho pptx trong Java bằng cách sử dụng phụ
  thuộc GroupDocs Maven để cập nhật siêu dữ liệu PowerPoint, bao gồm cách thay đổi
  ngày tạo PPTX.
keywords:
- set pptx createdtime java
- change pptx creation date
- groupdocs metadata java
- powerpoint metadata update
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  headline: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  type: TechArticle
- description: Learn how to set pptx CreatedTime in Java using the GroupDocs Maven
    dependency to update PowerPoint metadata, including how to change PPTX creation
    date.
  name: Set PPTX CreatedTime in Java with GroupDocs Maven Dependency
  steps:
  - name: Load the Presentation Document
    text: Loading the file establishes a connection that lets you read or write metadata.
  - name: Access the Root Package of the Presentation
    text: The `root` object gives access to the presentation's core package and its
      built‑in properties. The `root` object exposes all the built‑in document properties.
  - name: Update Built‑In Document Properties (including creation date)
    text: '`setCreatedTime` assigns a new creation timestamp to the document. Here
      we demonstrate how to **set PPTX CreatedTime** by assigning a new `Date` object
      to `CreatedTime`. Replace `new Date()` with any specific timestamp you need.'
  - name: Save the Updated Presentation
    text: '`save` writes the modified metadata back to a file. The `save` call writes
      the modified metadata back to a new PowerPoint file, leaving the original untouched.'
  type: HowTo
- questions:
  - answer: It provides a convenient way to include the latest GroupDocs.Metadata
      library in Maven‑based Java projects.
    question: What is the primary purpose of the GroupDocs Maven dependency?
  - answer: Use `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` before
      calling `metadata.save()`.
    question: How can I set the PPTX creation date without affecting other properties?
  - answer: A temporary trial license is sufficient for development and testing; a
      full license is required for production.
    question: Do I need a license to run this code in development?
  - answer: Yes—GroupDocs.Metadata supports both built‑in and custom properties through
      its API.
    question: Can I update custom metadata fields as well?
  - answer: Keep a copy of the original file or read the existing property values
      before overwriting them, then restore if needed.
    question: Is there a way to revert changes if I make a mistake?
  type: FAQPage
title: Đặt CreatedTime cho PPTX trong Java với phụ thuộc GroupDocs Maven
type: docs
url: /vi/java/document-formats/groupdocs-metadata-java-powerpoint-update-metadata/
weight: 1
---

# Đặt Thời Gian Tạo PPTX trong Java với GroupDocs.Metadata

Siêu dữ liệu chính xác là cần thiết cho việc tuân thủ và khả năng khám phá trong quy trình tài liệu hiện đại. Với **GroupDocs.Metadata** bạn có thể lập trình **đặt PPTX CreatedTime trong Java**, cho phép bạn **thay đổi ngày tạo PPTX** cùng với các thuộc tính tích hợp khác như tác giả hoặc công ty. Hướng dẫn này sẽ đưa bạn qua việc thiết lập Maven, khởi tạo API, cập nhật siêu dữ liệu và lưu bản trình chiếu đã chỉnh sửa — tất cả với mã rõ ràng, sẵn sàng cho môi trường sản xuất.

## Câu trả lời nhanh
- **Thư viện nào cập nhật siêu dữ liệu PowerPoint trong Java?** GroupDocs.Metadata qua phụ thuộc Maven của GroupDocs.  
- **Tôi có thể đặt thuộc tính PPTX CreatedTime không?** Có — sử dụng `root.getDocumentProperties().setCreatedTime(yourDate)`.  
- **Có cần giấy phép cho môi trường sản xuất không?** Bản dùng thử hoạt động cho việc đánh giá; giấy phép thương mại là bắt buộc cho triển khai trong môi trường sản xuất.  
- **Công cụ xây dựng nào được ví dụ sử dụng?** Maven (bạn cũng có thể tải JAR thủ công).  
- **API có hỗ trợ Java 8 và các phiên bản mới hơn không?** Chắc chắn — GroupDocs.Metadata hỗ trợ Java 8+.

## GroupDocs Maven Dependency là gì?
**GroupDocs Maven dependency** là mục nhập kho tương thích Maven, kéo thư viện GroupDocs.Metadata mới nhất vào dự án Java của bạn. Nó đơn giản hoá việc quản lý phụ thuộc bằng cách tự động giải quyết các thư viện truyền tải, đảm bảo bạn luôn sử dụng phiên bản mới nhất và an toàn, và loại bỏ nhu cầu tải JAR thủ công hoặc theo dõi phiên bản.

## Tại sao nên sử dụng GroupDocs.Metadata để thay đổi ngày tạo PPTX?
GroupDocs.Metadata cho phép cập nhật tự động, sẵn sàng cho hàng loạt các dấu thời gian tạo PPTX, đảm bảo mỗi bản trình chiếu tuân thủ chính sách công ty hoặc yêu cầu pháp lý. Bằng cách lập trình đặt thuộc tính CreatedTime, bạn tránh việc chỉnh sửa thủ công, giảm lỗi con người, và có thể tích hợp thay đổi này vào các pipeline CI/CD hoặc script di chuyển để quản lý tài liệu một cách liền mạch.

## Yêu cầu trước
- Java 8 hoặc cao hơn đã được cài đặt.  
- Một IDE như IntelliJ IDEA hoặc Eclipse.  
- Maven để quản lý phụ thuộc.  
- Truy cập bản dùng thử hoặc giấy phép đã mua của GroupDocs.  

## Cách đặt PPTX CreatedTime trong Java?

Lớp `Metadata` đại diện cho một tài liệu và cung cấp quyền truy cập vào các thuộc tính siêu dữ liệu của nó.

Tải tệp PowerPoint của bạn bằng `new Metadata("presentation.pptx")`, lấy gói gốc, gọi `setCreatedTime` với `java.util.Date` mong muốn, và cuối cùng gọi `save` để ghi các thay đổi. Quy trình từ đầu đến cuối này sửa đổi ngày tạo trong khi giữ nguyên toàn bộ nội dung slide và các thuộc tính khác.

### Cài đặt Maven
Thêm kho GroupDocs và phụ thuộc metadata vào `pom.xml` của bạn:

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

> **Pro tip:** Giữ số phiên bản luôn cập nhật sẽ giúp bạn hưởng lợi từ các bản sửa lỗi và cải thiện hiệu năng mới nhất.

### Tải trực tiếp (nếu bạn không muốn sử dụng Maven)

Hoặc, tải JAR mới nhất từ [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

#### Mua giấy phép

Bắt đầu với bản dùng thử miễn phí hoặc yêu cầu giấy phép tạm thời để đánh giá GroupDocs.Metadata. Đối với sử dụng trong môi trường sản xuất, mua giấy phép qua [GroupDocs' official website](https://purchase.groupdocs.com/temporary-license/).

## Khởi tạo và Cấu hình Cơ bản

Khi thư viện đã có trong classpath, bạn có thể tạo một thể hiện `Metadata` trỏ tới tệp PowerPoint của bạn:

```java
import com.groupdocs.metadata.*;

public class MetadataInitializer {
    public static void main(String[] args) {
        try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
            // Your code for manipulating metadata will go here.
        }
    }
}
```

Đoạn mã này mở bản trình chiếu trong khối try‑with‑resources, đảm bảo rằng tay cầm tệp được giải phóng tự động.

## Hướng dẫn từng bước để cập nhật siêu dữ liệu tích hợp

### Bước 1: Tải tài liệu trình chiếu

```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/input.pptx")) {
    // Proceed to access and modify the document properties.
}
```

Việc tải tệp thiết lập một kết nối cho phép bạn đọc hoặc ghi siêu dữ liệu.

### Bước 2: Truy cập gói gốc của bản trình chiếu

Đối tượng `root` cung cấp quyền truy cập vào gói lõi của bản trình chiếu và các thuộc tính tích hợp của nó.

```java
PresentationRootPackage root = metadata.getRootPackageGeneric();
```

Đối tượng `root` hiển thị tất cả các thuộc tính tài liệu tích hợp.

### Bước 3: Cập nhật các thuộc tính tài liệu tích hợp (bao gồm ngày tạo)

`setCreatedTime` gán một dấu thời gian tạo mới cho tài liệu.

```java
root.getDocumentProperties().setAuthor("test author");
root.getDocumentProperties().setCreatedTime(new Date());   // This changes the PPTX creation date
root.getDocumentProperties().setCompany("GroupDocs");
root.getDocumentProperties().setCategory("test category");
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```

Ở đây chúng tôi trình bày cách **đặt PPTX CreatedTime** bằng cách gán một đối tượng `Date` mới cho `CreatedTime`. Thay thế `new Date()` bằng bất kỳ dấu thời gian cụ thể nào bạn cần.

### Bước 4: Lưu bản trình chiếu đã cập nhật

`save` ghi siêu dữ liệu đã sửa đổi trở lại tệp.

```java
metadata.save("YOUR_OUTPUT_DIRECTORY/output.pptx");
```

Lệnh `save` ghi siêu dữ liệu đã sửa đổi vào một tệp PowerPoint mới, để nguyên tệp gốc không bị thay đổi.

## Mẹo khắc phục sự cố
- **Không tìm thấy tệp:** Kiểm tra lại đường dẫn đầu vào và quyền truy cập tệp.  
- **Phiên bản không khớp:** Đảm bảo phiên bản `groupdocs-metadata` phù hợp với môi trường Java của bạn.  
- **Thuộc tính không được cập nhật:** Xác nhận rằng bạn đã gọi `setCreatedTime` (hoặc setter tương ứng) trước khi gọi `save`.

## Ứng dụng thực tiễn
1. **Corporate Branding:** Tự động chèn tên công ty và danh mục đúng vào tất cả các bộ slide trước khi phân phối.  
2. **Document Management Systems:** Làm phong phú các tệp PPTX bằng siêu dữ liệu có thể tìm kiếm để truy xuất nhanh hơn.  
3. **Educational Resources:** Giữ thông tin tác giả và chương trình học luôn cập nhật trên các slide bài giảng.  
4. **Collaboration Tracking:** Ghi lại tên người đóng góp để duy trì trách nhiệm.  
5. **CMS Integration:** Đồng bộ các thay đổi siêu dữ liệu với nền tảng quản lý nội dung của bạn trong thời gian thực.

## Xem xét hiệu năng
- **Batch Processing:** Lặp qua danh sách tệp và tái sử dụng một thể hiện `Metadata` duy nhất khi có thể.  
- **Memory Management:** Luôn sử dụng try‑with‑resources (như đã minh họa) để giải phóng tài nguyên gốc kịp thời.  
- **Efficient Data Structures:** Lưu các cập nhật siêu dữ liệu vào một map trước khi áp dụng chúng để giảm các lần gọi lặp lại.

## Câu hỏi thường gặp

**Q: Mục đích chính của GroupDocs Maven dependency là gì?**  
A: Nó cung cấp cách tiện lợi để đưa thư viện GroupDocs.Metadata mới nhất vào các dự án Java dựa trên Maven.

**Q: Làm sao tôi có thể đặt ngày tạo PPTX mà không ảnh hưởng đến các thuộc tính khác?**  
A: Sử dụng `root.getDocumentProperties().setCreatedTime(yourDesiredDate)` trước khi gọi `metadata.save()`.

**Q: Tôi có cần giấy phép để chạy đoạn mã này trong môi trường phát triển không?**  
A: Giấy phép dùng thử tạm thời là đủ cho phát triển và kiểm thử; giấy phép đầy đủ cần thiết cho môi trường sản xuất.

**Q: Tôi có thể cập nhật các trường siêu dữ liệu tùy chỉnh không?**  
A: Có — GroupDocs.Metadata hỗ trợ cả thuộc tính tích hợp và tùy chỉnh thông qua API của nó.

**Q: Có cách nào để hoàn tác các thay đổi nếu tôi mắc lỗi không?**  
A: Giữ một bản sao của tệp gốc hoặc đọc các giá trị thuộc tính hiện có trước khi ghi đè, sau đó khôi phục nếu cần.

## Tài nguyên
- [Tài liệu](https://docs.groupdocs.com/metadata/java/)
- [Tham chiếu API](https://apireference.groupdocs.com/metadata/java/)

---

**Cập nhật lần cuối:** 2026-05-27  
**Kiểm tra với:** GroupDocs.Metadata 24.12 for Java  
**Tác giả:** GroupDocs  

## Các hướng dẫn liên quan
- [Cập nhật Siêu dữ liệu Tùy chỉnh trong PowerPoint bằng GroupDocs.Metadata Java API](/metadata/java/document-formats/update-custom-metadata-ppt-groupdocs-java/)
- [Cách Cập nhật Siêu dữ liệu Tài liệu Word bằng GroupDocs.Metadata Java: Hướng dẫn đầy đủ](/metadata/java/document-formats/update-word-metadata-groupdocs-java/)
- [Cập nhật Siêu dữ liệu PDF hiệu quả với GroupDocs.Metadata trong Java cho Quản lý Tài liệu](/metadata/java/document-formats/update-pdf-metadata-groupdocs-metadata-java/)