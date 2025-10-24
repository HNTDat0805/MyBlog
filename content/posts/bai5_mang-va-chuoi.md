---
title: "MẢNG VÀ CHUỖI"
date: 2025-10-23
draft: false
description: "Tìm hiểu về mảng một chiều, mảng đa chiều và các phương thức cơ bản của đối tượng String."
tags: ["java", "mảng", "array", "chuỗi", "string", "collection"]
---

### I. Mảng (Arrays)

**Mảng** là một tập hợp các biến có cùng kiểu dữ liệu, được lưu trữ liên tiếp nhau trong bộ nhớ. Mảng có **kích thước cố định** và các phần tử được truy cập thông qua **chỉ số (index)**, bắt đầu từ 0.

#### 1. Khai Báo và Khởi Tạo Mảng

Có hai cách chính để tạo mảng:

```java
// Cách 1: Khởi tạo với kích thước cố định (Kích thước: 5)
// Các phần tử sẽ được gán giá trị mặc định (0 cho int, null cho String,...)
int[] soNguyen = new int[5];

// Cách 2: Khởi tạo trực tiếp với các giá trị (Kích thước: 3)
String[] tenTraiCay = {"Táo", "Cam", "Xoài"};
```

#### 2. Truy Cập và Gán Giá Trị

Phần tử trong mảng được truy cập thông qua chỉ số (index).

```java
int[] diemSo = {8, 9, 7};

// Lấy giá trị phần tử thứ nhất (index 0)
int diemDauTien = diemSo[0]; // diemDauTien = 8

// Gán giá trị mới cho phần tử cuối cùng (index 2)
diemSo[2] = 10;

// Lấy kích thước của mảng
int kichThuoc = diemSo.length; // kichThuoc = 3
```

#### 3. Vòng Lặp Với Mảng

Sử dụng vòng lặp for truyền thống hoặc for-each để duyệt qua các phần tử.

```java
String[] mauSac = {"Đỏ", "Xanh", "Vàng"};

// Duyệt bằng for-each (Dễ đọc hơn)
for (String mau : mauSac) {
    System.out.println(mau);
}

// Duyệt bằng for truyền thống (Dùng khi cần dùng index)
for (int i = 0; i < mauSac.length; i++) {
    System.out.println("Màu thứ " + i + ": " + mauSac[i]);
}
```

#### 4. Mảng Đa Chiều (Multidimensional Arrays)

Thường dùng là mảng hai chiều, giống như một bảng (table) hoặc ma trận (Matrix).

```java
// Mảng 2x3 (2 hàng, 3 cột)
int[][] maTran = {
    {1, 2, 3}, // Hàng 0
    {4, 5, 6}  // Hàng 1
};

// Truy cập phần tử ở Hàng 1, Cột 0 (Giá trị 4)
int phanTu = maTran[1][0];
```

### II. Chuỗi (String)

String là một lớp (Class) và là một kiểu dữ liệu tham chiếu trong Java, được dùng để lưu trữ một chuỗi các ký tự. Chuỗi trong Java là bất biến (Immutable), nghĩa là không thể thay đổi sau khi đã được tạo.

#### 1. Khai Báo Chuỗi

```java
// Cách 1: Dùng String Literal (phổ biến)
String ten = "John Doe";

// Cách 2: Dùng từ khóa new (tạo đối tượng mới trong bộ nhớ)
String thongDiep = new String("Xin chào");
```

#### 2. Các Phương Thức (Methods) Thường Dùng

Lớp String cung cấp nhiều phương thức mạnh mẽ để thao tác và kiểm tra chuỗi.

| Phương thức                    | Công dụng                                           | Ví dụ                                |
| :----------------------------- | :-------------------------------------------------- | :----------------------------------- |
| **`.length()`**                | Trả về độ dài của chuỗi.                            | `"Hello".length()` → `5`             |
| **`.charAt(index)`**           | Lấy ký tự tại chỉ số cụ thể.                        | `"Java".charAt(1)` → `'a'`           |
| **`.substring(start)`**        | Trích xuất chuỗi con từ chỉ số `start`.             | `"Code".substring(2)` → `"de"`       |
| **`.equals(other)`**           | So sánh giá trị chuỗi (phân biệt hoa thường).       | `"A".equals("a")` → `false`          |
| **`.equalsIgnoreCase(other)`** | So sánh giá trị chuỗi (không phân biệt hoa thường). | `"A".equalsIgnoreCase("a")` → `true` |
| **`.toUpperCase()`**           | Chuyển chuỗi sang chữ hoa.                          | `"hi".toUpperCase()` → `"HI"`        |
| **`.trim()`**                  | Loại bỏ khoảng trắng ở đầu và cuối chuỗi.           | `" hello ".trim()` → `"hello"`       |

#### 3. So Sánh Chuỗi (Quan trọng)

Luôn dùng phương thức .equals() để so sánh nội dung của hai chuỗi, không dùng toán tử ==. Toán tử == chỉ so sánh địa chỉ bộ nhớ (tham chiếu), không phải giá trị.

```java
String s1 = "Java";
String s2 = new String("Java");
String s3 = "Java";

System.out.println(s1 == s2);      // false (Địa chỉ khác nhau)
System.out.println(s1.equals(s2)); // true (Giá trị giống nhau)
System.out.println(s1 == s3);      // true (Do Java tối ưu hóa String Literal, cùng địa chỉ)
```

### III. Kết Luận

Mảng cung cấp cách lưu trữ có cấu trúc, còn String là công cụ không thể thiếu để xử lý văn bản.
