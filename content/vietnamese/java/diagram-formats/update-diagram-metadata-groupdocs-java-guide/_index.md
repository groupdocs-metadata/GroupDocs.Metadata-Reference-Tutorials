---
date: '2026-01-19'
description: Tìm hiểu cách thay đổi thời gian tạo và tự động cập nhật siêu dữ liệu
  cho các tệp sơ đồ bằng GroupDocs.Metadata trong Java.
keywords:
- update diagram metadata
- groupdocs java
- automate metadata update
title: Thay đổi thời gian tạo trong metadata của sơ đồ bằng GroupDocs Java
type: docs
url: /vi/java/diagram-formats/update-diagram-metadata-groupdocs-java-guide/
weight: 1
---

 Tạo trong tạo, **thay đổi thời gian tạo**,, và áp dụng các mẹo hiệu suất tốt nhất để giữ cho tài liệu của bạn nhất quán và dễ tìm kiếm.

## Câu trả lời nhanh
- **Mục tiêu chính là gì?** dùng cho Java.  
- **Có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; cần giấy phép đầy đủ cho môi trường sản xuất.  
- **Có thể xử lý hàng loạt nhiều sơ đồ không?** Có — sử dụng cùng một cách tiếp cận trong vòng lặp hoặc stream song song.  
- **Yêu cầu phiên bản Java nào?** JDK 8 hoặc cao hơn.

## “Thay đổi thời gian tạo” trong siêu dữ liệu sơ đồ là gì?
Thay đổi thời gian tạo có nghĩa là ghi đè dấu thời gian gốc được lưu trong tệp sơ đồ (ví dụ: VDX, VSDX) bằng một ngày mới. Điều này hữu ích khi bạn muốn siêu dữ liệu của tệp phản ánh ngày xử lý thực tế thay vì ngày tạo ban đầu.

## Tại sao nên tự động hoá việc cập nhật siêu dữ liệu cho sơ đồ?
- **Nhất quán:** Đảm bảo mọi tệp đều tuân theo cùng một quy tắc đặt tên và phân loại.  
- **Tìm kiếm dễ dàng:** Các từ khóa và danh mục được cập nhật giúp cải thiện khả năng khám phá tài liệu trong các giải pháp DMS.  
- **Tuân thủ:** Hỗ trợ đáp ứng yêu cầu kiểm toán bằng cách đảm bảo các dấu thời gian chính xác.  

## Điều kiện tiên quyết
- **Java Development Kit (JDK) 8+** đã được cài đặt.  
- **IDE** như IntelliJ IDEA hoặc Eclipse.  
- **Maven** (hoặc quản lý JAR thủ công) để xử lý phụ thuộc.  
- Kiến thức cơ bản về các lớp, phương thức Java và xử lý ngoại lệ.

### Thư viện và phụ thuộc cần thiết
Thêm kho và phụ thuộc sau vào tệp `pom.xml` nếu bạn dùng Maven:

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
Nếu bạn muốn tải trực tiếp, truy cập [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) để lấy phiên bản mới nhất.

### Cài đặt môi trường
- JDK 8 hoặc mới hơn.  
- IntelliJ IDEA, Eclipse, hoặc bất kỳ IDE nào hỗ trợ Java.  

### Kiến thức nền tảng
Hiểu cú pháp Java và thao tác I/O cơ bản sẽ giúp quá trình học nhanh hơn, nhưng các bước đều được giải thích bằng ngôn ngữ đơn giản.

## Thiết lập GroupDocs.Metadata cho Java
### Hướng dẫn cài đặt
**Người dùng Maven:** Đoạn mã trên sẽ tự động thêm kho và JAR cần thiết.  
**Người dùng tải trực tiếp:** Sau khi tải JAR từ [GroupDocs](https://releases.groupdocs.com/metadata/java/), thêm nó vào classpath của dự án.

### Cách lấy giấy phép
- **Bản dùng thử:** Khám phá thư viện mà không tốn phí.  
- **Giấy phép tạm thời:** Nhận giấy phép tạm thời để thử nghiệm kéo dài hơn [tại đây](https://purchase.groupdocs.com/temporary-license/).  
- **Mua bản đầy đủ:** Mua giấy phép đầy đủ cho môi trường sản xuất.

### Khởi tạo cơ bản
Để bắt đầu sử dụng GroupDocs.Metadata, nhập lớp và mở tệp sơ đồ:

```java
import com.groupdocs.metadata.Metadata;

// Load a diagram document and access its metadata
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Your code here
}
```

Sau khi thư viện được khởi tạo, bạn có thể sửa đổi bất kỳ thuộc tính tích hợp nào, bao gồm thời gian tạo.

## Hướng dẫn thực hiện
### Cách thay đổi thời gian tạo trong tệp sơ đồ
Trong phần này chúng ta sẽ đi qua từng bước cần thiết để **thay đổi thời gian tạo** và cập nhật các thuộc tính phổ biến khác như tác giả, công ty và danh mục.

#### Bước 1: Tải tài liệu sơ đồ
```java
try (Metadata metadata = new Metadata("YOUR_DOCUMENT_DIRECTORY/InputVdx")) {
    // Access and update document properties here
}
```
*Giải thích:* Hàm khởi tạo `Metadata` nhận đường dẫn tới tệp sơ đồ của bạn. Khối `try‑with‑resources` đảm bảo tệp được đóng đúng cách sau khi thực hiện.

#### Bước 2: Truy cập gói gốc
```java
DiagramRootPackage root = metadata.getRootPackageGeneric();
```
*Giải thích:* Gói gốc cung cấp quyền truy cập trực tiếp vào tất cả các trường siêu dữ liệu tích hợp cho sơ đồ.

#### Bước 3: Đặt thuộc tính Người tạo
```java
root.getDocumentProperties().setCreator("test author");
```
*Giải thích:* Gán tên tác giả mới. Thay `"test author"` bằng tên người tạo thực tế.

#### Bước 4: **Thay đổi thời gian tạo**
```java
root.getDocumentProperties().setTimeCreated(new Date());
```
*Giải thích:* Dòng này **thay đổi thời gian tạo** thành ngày và giờ hệ thống hiện tại. Bạn cũng có thể cung cấp một đối tượng `Date` cụ thể nếu cần dấu thời gian tùy chỉnh.

#### Bước 5: Định nghĩa thông tin công ty
```java
root.getDocumentProperties().setCompany("GroupDocs");
```
*Giải thích:* Lưu tên công ty liên quan đến sơ đồ — hữu ích cho việc theo dõi doanh nghiệp.

#### Bước 6: Đặt danh mục tài liệu
```java
root.getDocumentProperties().setCategory("test category");
```
*Giải thích:* Phân loại tệp, giúp bạn **cập nhật danh mục sơ đồ** một cách nhất quán trên toàn bộ kho lưu trữ.

#### Bước 7: Thêm từ khóa
```java
root.getDocumentProperties().setKeywords("metadata, built-in, update");
```
*Giải thích:* Từ khóa cải thiện khả năng tìm kiếm; bạn có thể liệt kê bất kỳ thuật ngữ nào liên quan đến nội dung sơ đồ.

#### Bước 8: Lưu thay đổi
```java
metadata.save("YOUR_OUTPUT_DIRECTORY/OutputVdx");
```
*Giải thích:* Ghi lại tất cả các sửa đổi vào một tệp mới, để nguyên tệp gốc không bị thay đổi.

### Các lỗi- **File không tồn tại:** Kiểm tra lại đường dẫn đầu vào và đảm bảo phần mở rộng tệp khớp với định dạng thực tế.  
- **Không có quyền truy cập:** Kiểm tra quyền đọc/ghi cho cả thư mục đầu vào và đầu ra.  
- **Định dạng ngày không hợp lệ:** Sử dụng đối tượng `java.util nhất. kiểm soát phiên bản** – Đồng bộ dấu thời gian với các commit Git bằng cách – Thực thi chính sách toàn công ty về tác giả, công ty và từ khóa cho tất cả tài sản sơ đồ.

## Cân nhắc về hiệu suất
- **Xử lý hàng loạt:** Đặt các bước trên trong một vòng lặp để xử lý hàng chục tệp trong một lần chạy.  
- **Quản lý bộ nhớ:** Giải phóng mỗi đối tượng `Metadata` kịp thời (khối `try‑with‑resources` tự động làm việc này).  
- **Thực thi bất đồng bộ:** Đối với các batch lớn, cân nhắc sử bạn có thể duy trì tài liệu nhất quán, dễ tìm kiếm và tuân thủ quy định trong toàn tổ chức.

**Bước tiếp theo**
- Thử nghiệm với các định dạng tệp khác được hỗ trợ áp dụng tiêu chuẩn siêu dữẵn sàng thử chưa? Truy cập [GroupDocs.Metadata for Java releases](https://releases.groupdocs.com/metadata/java/) và bắt đầu triển khai tự động hoá siêu dữ liệu của bạn ngay hôm nay.

---

**Cập nhật lần cuối:** 2026-01-19  
**Đã kiểm tra với:** GroupDocs.Metadata 24.12  
**Tác giả:** GroupDocs  

## Câu hỏi thường gặp

**H: Tôi có thể dùng cách này với các định dạng sơ đồ khác như VSDX không?**  
Đ: Có, cùng một API hoạt động cho tất cả các định dạng sơ đồ được GroupDocs.Metadata hỗ trợ.

**H: Tôi có cần giấy phép cho các bản dựng phát triển không?**  
Đ: Bản dùng thử đủ cho phát triển và thử nghiệm; giấy phép đầy đủ cần cho triển khai sản xuất.

**H: Làm sao tôi có thể cập nhật nhiều thuộc tính trong một lần gọi?**  
Đ: Đặt từng thuộc tính trên đối tượng `DocumentProperties` trước khi gọi `metadata.save(...)`; thư viện sẽ ghi chúng đồng thời.

**H: Có an toàn khi ghi đè lên tệp gốc không?**  
Đ: Nên lưu vào tệp mới (như trong ví dụ) để tránh mất dữ liệu, sau đó thay thế tệp gốc nếu cần.

**H: Nếu tôi muốn đặt ngày tạo tùy chỉnh thay vì thời gian hiện tại thì làm sao?**  
Đ: Tạo một đối tượng `java.util.Date` (hoặc instance `java.time`) với dấu thời gian mong muốn và truyền nó vào `setTimeCreated`.