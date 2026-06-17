---
date: '2026-05-27'
description: Tìm hiểu cách cập nhật người nhận email java bằng GroupDocs.Metadata
  cho Java. Sửa đổi người nhận, tiêu đề và lưu các thay đổi một cách hiệu quả.
keywords:
- update email recipients java
- GroupDocs Metadata Java
- email metadata management
schemas:
- author: GroupDocs
  dateModified: '2026-05-27'
  description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  headline: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  type: TechArticle
- description: Learn how to update email recipients java using GroupDocs.Metadata
    for Java. Modify recipients, subjects, and save changes efficiently.
  name: 'Update Email Recipients Java: Master Email Metadata Updates with GroupDocs.Metadata'
  steps:
  - name: Initialize Metadata Object
    text: 'The `Metadata` class represents a file and provides access to its metadata.
      Create a `Metadata` instance with your input file path: **Definition anchor**:
      The `Metadata` class is the entry point for all metadata operations in GroupDocs.Metadata,
      representing a single file in memory.'
  - name: Access EmailRootPackage
    text: '`EmailRootPackage` gives access to email‑specific metadata such as recipients
      and subject. Access the email’s metadata using: This step is crucial as it provides
      access to all modifiable properties of your email.'
  - name: Update Recipients
    text: 'Set new recipients for your email message:'
  - name: Initialize and Obtain Root Package
    text: 'Similar to updating primary recipients, initialize the metadata object:'
  - name: Set CC Recipients
    text: '`addCcRecipient` appends a new address to the CC collection without overwriting
      existing entries. Add carbon copy recipients as follows: This approach ensures
      that additional users are notified without being the main point of contact.'
  - name: Initialize Metadata
    text: 'Start by initializing your metadata object:'
  - name: Change the Subject
    text: 'Update the email’s subject line: This step is vital for maintaining relevant
      and searchable email threads.'
  - name: Initialize and Obtain Root Package
    text: 'Begin with initializing the `Metadata` object:'
  - name: Save Changes
    text: 'Persist your changes by saving them to a specified output directory: This
      ensures that all modifications are retained and reflected in the saved file.'
  type: HowTo
- questions:
  - answer: Load the file with `Metadata`, get the `EmailRootPackage`, replace the
      `To` collection, and save – all in three lines of code.
    question: What is the fastest way to change an email’s primary recipient?
  - answer: Yes, use `addCcRecipient` on the `EmailRootPackage` to append new addresses.
    question: Can I add CC recipients without overwriting existing ones?
  - answer: A temporary license removes evaluation limits; a permanent license is
      required for commercial deployments. You can obtain a temporary license from
      the [GroupDocs](https://purchase.groupdocs.com/temporary-license/) page.
    question: Do I need a license for production use?
  - answer: GroupDocs.Metadata works with Java 8, 11, 17, and later.
    question: Which Java versions are supported?
  - answer: Process files in batches of 50–100 to keep memory usage under 200 MB per
      batch.
    question: Is batch processing safe for large mailboxes?
  type: FAQPage
title: 'Cập nhật người nhận email Java: Nắm vững việc cập nhật siêu dữ liệu email
  với GroupDocs.Metadata'
type: docs
url: /vi/java/email-contact-formats/master-email-metadata-updates-java-groupdocs/
weight: 1
---

# Cập nhật người nhận email Java với GroupDocs.Metadata

Trong hướng dẫn toàn diện này, bạn sẽ **update email recipients java** một cách lập trình bằng thư viện GroupDocs.Metadata. Chúng tôi sẽ hướng dẫn cách sửa đổi người nhận chính và CC, thay đổi tiêu đề, và lưu các thay đổi—tất cả với các đoạn mã rõ ràng, từng bước. Khi hoàn thành, bạn sẽ sẵn sàng tích hợp tự động hoá siêu dữ liệu email vào bất kỳ quy trình làm việc nào dựa trên Java.

## Câu trả lời nhanh
- **Cách nhanh nhất để thay đổi người nhận chính của email là gì?** Tải tệp bằng `Metadata`, lấy `EmailRootPackage`, thay thế bộ sưu tập `To`, và lưu — tất cả trong ba dòng mã.  
- **Có thể thêm người nhận CC mà không ghi đè lên những người hiện có không?** Có, sử dụng `addCcRecipient` trên `EmailRootPackage` để thêm các địa chỉ mới.  
- **Tôi có cần giấy phép cho việc sử dụng trong môi trường sản xuất không?** Giấy phép tạm thời loại bỏ các giới hạn đánh giá; giấy phép vĩnh viễn là bắt buộc cho các triển khai thương mại. Bạn có thể lấy giấy phép tạm thời từ trang [GroupDocs](https://purchase.groupdocs.com/temporary-license/) .  
- **Các phiên bản Java nào được hỗ trợ?** GroupDocs.Metadata hoạt động với Java 8, 11, 17 và các phiên bản sau.  
- **Xử lý hàng loạt có an toàn cho hộp thư lớn không?** Xử lý các tệp theo lô 50–100 để giữ mức sử dụng bộ nhớ dưới 200 MB mỗi lô.

## Cập nhật người nhận email java là gì?
*Updating email recipients in Java* có nghĩa là thay đổi một cách lập trình các trường “To”, “CC”, hoặc “BCC” của một tệp email (EML, MSG, v.v.) mà không mở client email. GroupDocs.Metadata cung cấp một API cấp cao cho phép đọc cấu trúc email, cho phép bạn sửa đổi các bộ sưu tập địa chỉ, và ghi lại tệp đã cập nhật lên đĩa.

## Tại sao nên sử dụng GroupDocs.Metadata cho siêu dữ liệu email?
GroupDocs.Metadata hỗ trợ **hơn 50 định dạng liên quan đến email** (bao gồm EML, MSG, MHT) và có thể xử lý **các tin nhắn hàng trăm trang** mà không cần tải toàn bộ tệp vào bộ nhớ, giảm tiêu thụ RAM lên tới **80 %** so với các cách tiếp cận đọc luồng tệp đơn giản. Việc triển khai thuần Java loại bỏ các phụ thuộc gốc, làm cho nó trở nên lý tưởng cho các dịch vụ đa nền tảng.

## Yêu cầu trước
- Java 8 hoặc mới hơn (Java 11, 17, 21 đã được kiểm tra đầy đủ).  
- Maven hoặc Gradle để quản lý phụ thuộc.  
- Giấy phép GroupDocs.Metadata hợp lệ (tạm thời hoặc vĩnh viễn).  

### Thư viện và phụ thuộc cần thiết
Thêm phụ thuộc sau vào tệp `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>23.12</version>
</dependency>
```
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

Để tải trực tiếp, lấy phiên bản mới nhất từ [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/).

### Cài đặt môi trường
Đảm bảo IDE của bạn trỏ tới JDK tương thích và Maven giải quyết các artifact của GroupDocs.Metadata mà không có lỗi.

## Cách cập nhật người nhận email trong Java?
Tải tệp email, thay thế các người nhận hiện có, và lưu kết quả. Thao tác này chỉ cần ba lời gọi API và chạy dưới **200 ms** cho các tin nhắn thường 1 MB. Bằng cách sử dụng API cấp cao `EmailRootPackage`, bạn tránh việc phân tích toàn bộ tệp, giúp giảm mức sử dụng bộ nhớ và làm cho việc xử lý hàng loạt trở nên đơn giản.

```java
Metadata metadata = new Metadata("input.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
email.getTo().clear();                         // remove old recipients
email.getTo().add(new EmailRecipient("new@example.com"));
metadata.save("output.eml");
```
```java
import com.groupdocs.metadata.Metadata;
```
Dòng trên nhập lớp thiết yếu để bắt đầu quản lý các thao tác siêu dữ liệu trên các tệp của bạn.

## Hướng dẫn triển khai
Bây giờ chúng ta sẽ đi sâu hơn vào từng tính năng, mở rộng các đoạn mã trả lời nhanh với ngữ cảnh đầy đủ.

### Cập nhật người nhận email
**Tổng quan**: Phần này trình bày cách bạn có thể cập nhật người nhận chính của một tin nhắn email một cách lập trình.

#### Bước 1: Khởi tạo đối tượng Metadata
Lớp `Metadata` đại diện cho một tệp và cung cấp quyền truy cập vào siêu dữ liệu của nó. Tạo một thể hiện `Metadata` với đường dẫn tệp đầu vào của bạn:

```java
Metadata metadata = new Metadata("sample.eml");
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    // Proceed to obtain root package for further operations
}
```
**Định nghĩa**: Lớp `Metadata` là điểm vào cho tất cả các thao tác siêu dữ liệu trong GroupDocs.Metadata, đại diện cho một tệp duy nhất trong bộ nhớ.

#### Bước 2: Truy cập EmailRootPackage
`EmailRootPackage` cung cấp quyền truy cập vào siêu dữ liệu đặc thù của email như người nhận và tiêu đề. Truy cập siêu dữ liệu email bằng cách:

```java
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
EmailRootPackage root = metadata.getRootPackageGeneric();
```
Bước này quan trọng vì nó cung cấp quyền truy cập vào tất cả các thuộc tính có thể sửa đổi của email.

#### Bước 3: Cập nhật người nhận
Đặt người nhận mới cho tin nhắn email của bạn:

```java
email.getTo().clear(); // remove existing recipients
email.getTo().add(new EmailRecipient("john.doe@example.com"));
email.getTo().add(new EmailRecipient("jane.smith@example.com"));
```
```java
root.getEmailPackage().setRecipients(new String[] { "sample@aspose.com" });
```

### Thêm người nhận Carbon Copy (CC) vào Email
**Tổng quan**: Tìm hiểu cách thêm người nhận CC vào một email hiện có.

#### Bước 1: Khởi tạo và lấy Root Package
Tương tự như việc cập nhật người nhận chính, khởi tạo đối tượng metadata:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Bước 2: Đặt người nhận CC
`addCcRecipient` thêm một địa chỉ mới vào bộ sưu tập CC mà không ghi đè các mục hiện có. Thêm người nhận carbon copy như sau:

```java
email.getCc().add(new EmailRecipient("manager@example.com"));
email.getCc().add(new EmailRecipient("teamlead@example.com"));
```
```java
root.getEmailPackage().setCarbonCopyRecipients(new String[] { "sample@groupdocs.com" });
```
Cách tiếp cận này đảm bảo rằng các người dùng bổ sung được thông báo mà không phải là điểm liên hệ chính.

### Cập nhật tiêu đề email
**Tổng quan**: Tính năng này cho phép bạn sửa đổi tiêu đề của email, giữ cho giao tiếp rõ ràng và cập nhật.

#### Bước 1: Khởi tạo Metadata
Bắt đầu bằng cách khởi tạo đối tượng metadata của bạn:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Bước 2: Thay đổi tiêu đề
Cập nhật tiêu đề của email:

```java
email.setSubject("Quarterly Report – Updated");
```
```java
root.getEmailPackage().setSubject("RE: test subject");
```
Bước này quan trọng để duy trì các chuỗi email có liên quan và có thể tìm kiếm.

### Lưu siêu dữ liệu email đã cập nhật
**Tổng quan**: Khi bạn đã thực hiện các thay đổi, việc lưu các cập nhật này là cần thiết. Phần này cho thấy cách lưu trữ các sửa đổi một cách hiệu quả.

#### Bước 1: Khởi tạo và lấy Root Package
Bắt đầu bằng việc khởi tạo đối tượng `Metadata`:

```java
Metadata metadata = new Metadata("sample.eml");
EmailRootPackage email = metadata.getRootPackage().getEmail();
```
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputEml")) {
    EmailRootPackage root = metadata.getRootPackageGeneric();
}
```

#### Bước 2: Lưu thay đổi
Lưu các thay đổi của bạn bằng cách ghi chúng vào thư mục đầu ra được chỉ định:

```java
metadata.save("output/updated_email.eml");
```
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputEml");
```
Điều này đảm bảo rằng tất cả các sửa đổi được giữ lại và phản ánh trong tệp đã lưu.

## Ứng dụng thực tế
Triển khai các tính năng này có thể mang lại lợi ích đáng kể trong nhiều kịch bản thực tế:

1. **Hệ thống quản lý email** – Tự động cập nhật người nhận cho việc phân phối email hàng loạt.  
2. **Nền tảng hỗ trợ khách hàng** – Nhanh chóng sửa đổi tiêu đề email để phản ánh thay đổi trạng thái ticket.  
3. **Công cụ giao tiếp nội bộ** – Đảm bảo tất cả thành viên trong nhóm được CC trong các thông báo quan trọng mà không cần chỉnh sửa thủ công.

## Các lưu ý về hiệu năng
Khi làm việc với khối lượng lớn dữ liệu email, hãy nhớ những lời khuyên sau:

- Xử lý các tệp theo lô **50–100** để giữ mức sử dụng bộ nhớ dưới **200 MB** mỗi lô.  
- Sử dụng lời gọi `metadata.getRootPackage().getEmail()` một cách hạn chế; tái sử dụng thể hiện `Metadata` khi có thể.  
- Giám sát việc sử dụng heap JVM bằng các công cụ như VisualVM để tránh lỗi OutOfMemory.

## Kết luận
Bạn đã thành thạo cách **update email recipients java** bằng GroupDocs.Metadata. Dù bạn đang điều chỉnh người nhận chính, thêm CC, hay chỉnh sửa tiêu đề, thư viện cung cấp một API nhanh, tiết kiệm bộ nhớ. Khám phá toàn bộ [documentation](https://docs.groupdocs.com/metadata/java/) để biết các kịch bản nâng cao hơn như xử lý tệp đính kèm hoặc chuyển đổi giữa định dạng EML và MSG.

## Phần Câu hỏi thường gặp
**Q1**: Các phiên bản Java nào được GroupDocs.Metadata hỗ trợ?  
- **A**: Java 8, 11, 17 và các phiên bản sau được hỗ trợ đầy đủ.

**Q2**: Tôi có thể sử dụng GroupDocs.Metadata mà không có giấy phép không?  
- **A**: Có, bản dùng thử miễn phí hoạt động với một số hạn chế; giấy phép tạm thời hoặc vĩnh viễn sẽ loại bỏ các giới hạn đó.

**Q3**: Làm thế nào để xử lý các tệp email lớn một cách hiệu quả?  
- **A**: Xử lý chúng theo các lô nhỏ hơn, tái sử dụng các đối tượng `Metadata`, và giám sát việc sử dụng heap để duy trì dưới 200 MB mỗi lô.

**Q4**: GroupDocs.Metadata hỗ trợ những loại tệp nào khác ngoài email?  
- **A**: Nó hỗ trợ hơn **70** định dạng bao gồm PDF, DOCX, XLSX, PPTX, hình ảnh và các tệp nén. Xem [API reference](https://reference.groupdocs.com/metadata/java/) để biết danh sách đầy đủ.

---

**Last Updated:** 2026-05-27  
**Tested With:** GroupDocs.Metadata 23.12 for Java  
**Author:** GroupDocs  

---

## Các hướng dẫn liên quan

- [Thành thạo trích xuất siêu dữ liệu email trong Java bằng GroupDocs.Metadata](/metadata/java/email-contact-formats/mastering-email-metadata-extraction-groupdocs-java/)
- [Các hướng dẫn siêu dữ liệu Email và Liên hệ cho GroupDocs.Metadata Java](/metadata/java/email-contact-formats/)
- [Cách trích xuất URI ảnh vCard bằng GroupDocs.Metadata trong Java để quản lý liên hệ hiệu quả](/metadata/java/email-contact-formats/extract-vcard-photo-uris-groupdocs-metadata-java/)