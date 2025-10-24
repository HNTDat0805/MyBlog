---
title: "CẤU TRÚC CƠ BẢN"
date: 2025-10-23
draft: false
description: "Tìm hiểu Class, Object, Main Method, Package và các quy tắc cú pháp cơ bản của Java."
tags: ["java", "cấu trúc", "class", "main", "package"]
---

### I. Khái Niệm Cốt Lõi: Lớp (Class) và Đối Tượng (Object)

Trong Java, mọi thứ đều được tổ chức bên trong một **Lớp (Class)**.

- **Lớp (Class):** Giống như một **bản thiết kế** (Blueprint). Nó định nghĩa các **thuộc tính** (dữ liệu) và **phương thức** (hành vi) mà các đối tượng sẽ có.
- **Đối Tượng (Object):** Là một **thể hiện thực tế** được tạo ra từ lớp.

#### Cú Pháp Khai Báo Lớp:

```java
// Khai báo lớp XeHoi
public class XeHoi {
    // Thuộc tính (dữ liệu)
    String mauSac = "Đỏ";
    int tocDo = 0;

    // Phương thức (hành vi)
    public void tangToc() {
        tocDo = tocDo + 10;
        System.out.println("Tốc độ hiện tại: " + tocDo + " km/h");
    }
}
```

### II. Phương Thức Chính (The Main Method)

Phương thức main là điểm khởi đầu, là nơi JVM bắt đầu thực thi code. Nó phải luôn tuân thủ cú pháp sau:

```java
public static void main(String[] args) {
// Code của chương trình bắt đầu từ đây

// Tạo một Đối tượng từ lớp XeHoi
    XeHoi xeA = new XeHoi(); // Sử dụng từ khóa 'new' để tạo đối tượng

System.out.println("Xe A ban đầu có màu: " + xeA.mauSac);

// Gọi phương thức của đối tượng
    xeA.tangToc();
}
```

#### Giải Thích Chi Tiết Phương Thức `main`

Phương thức `public static void main(String[] args)` bao gồm các từ khóa quan trọng sau:

| Từ khóa      | Ý nghĩa                                                                       |
| :----------- | :---------------------------------------------------------------------------- |
| **`public`** | Có thể truy cập công khai từ bất cứ đâu.                                      |
| **`static`** | Thuộc về Lớp (Class), không cần tạo Đối tượng (Object) để gọi.                |
| **`void`**   | Phương thức không trả về giá trị nào sau khi thực thi xong.                   |
| **`main`**   | Tên hàm tiêu chuẩn mà **JVM (Máy ảo Java)** tìm kiếm để bắt đầu chương trình. |

### III. Quy Tắc Cú Pháp Cơ Bản

Tuân thủ các quy tắc này là bắt buộc để code Java chạy được:

- **Phân Biệt Chữ Hoa/Thường (Case Sensitive):** Tên biến, tên lớp phân biệt rõ ràng (ví dụ: `Ten` và `ten` là hai thứ khác nhau).
- **Dấu Chấm Phẩy (`;`):** Mọi câu lệnh kết thúc bằng dấu chấm phẩy.
- **Khối Lệnh (`{}`):** Dùng để nhóm các câu lệnh lại với nhau, định nghĩa thân của Class, Phương thức hoặc cấu trúc điều khiển.

#### Quy Tắc Đặt Tên (Conventions)

| Thành phần              | Quy ước                       | Ví dụ                         |
| :---------------------- | :---------------------------- | :---------------------------- |
| **Lớp (Class)**         | **PascalCase**                | `TenLopMoi`                   |
| **Biến và Phương thức** | **camelCase**                 | `tenBienCuaToi`, `tinhTong()` |
| **Hằng số (Constant)**  | **VIẾT_HOA_CÓ_DẤU_GẠCH_DƯỚI** | `MAX_VALUE`                   |

### IV. Tổ Chức Code: Gói (Package) và Import

Khi dự án lớn dần, ta cần cơ chế tổ chức code.

#### 1. Gói (Package)

Package là cơ chế nhóm các lớp có liên quan với nhau vào một thư mục logic, giúp quản lý và tránh xung đột tên lớp.

```java
// Dòng đầu tiên trong file phải là khai báo package
package com.tencongty.tenproject.models;

public class NguoiDung {
// Nội dung lớp NguoiDung
}
```

#### 2. Lệnh Import

Sử dụng import để cho phép bạn sử dụng một lớp từ một Package khác.

```java
// Import lớp Scanner từ package java.util
import java.util.Scanner;

public class ViDuImport {
public static void main(String[] args) {
// Có thể sử dụng Scanner sau khi import
Scanner scanner = new Scanner(System.in);
System.out.println("Nhập tên của bạn:");
String ten = scanner.nextLine();
}
}
```

### V. Chú Thích (Comments) - Code Dễ Đọc

Chú thích là những dòng code mà JVM bỏ qua, nhưng chúng lại cực kỳ quan trọng đối với khả năng đọc hiểu của code.

| Kiểu Chú Thích | Cú Pháp      | Ứng dụng                              |
| :------------- | :----------- | :------------------------------------ |
| **Dòng đơn**   | `//`         | Giải thích nhanh một dòng code.       |
| **Khối**       | `/* ... */`  | Chú thích trên nhiều dòng.            |
| **Javadoc**    | `/** ... */` | Tạo tài liệu tự động (Documentation). |
