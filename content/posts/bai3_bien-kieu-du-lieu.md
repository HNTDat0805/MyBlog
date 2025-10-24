---
title: "BIẾN VÀ KIỂU DỮ LIỆU"
date: 2025-10-23
draft: false
description: "Khám phá các kiểu dữ liệu nguyên thủy (Primitive Types), cách khai báo và gán giá trị cho Biến trong Java."
tags: ["java", "biến", "kiểu dữ liệu", "primitive", "data types"]
---

### I. Biến (Variables) Là Gì?

**Biến** là một vùng nhớ được đặt tên trong bộ nhớ máy tính, dùng để lưu trữ dữ liệu.

#### Cú Pháp Khai Báo Biến

Cú pháp cơ bản bao gồm **Kiểu Dữ Liệu** và **Tên Biến**:

```java
// Cú pháp: [Kiểu Dữ Liệu] [Tên Biến];
int soLuong;

// Khai báo và gán giá trị ban đầu (Initialization)
String tenHocSinh = "Nguyễn Văn A";
```

### II. Kiểu Dữ Liệu Nguyên Thủy (Primitive Data Types)

Java có 8 kiểu dữ liệu nguyên thủy cơ bản, chúng được dùng để lưu trữ các giá trị đơn lẻ và có kích thước cố định trong bộ nhớ.

#### 1. Các Kiểu Số Nguyên (Integers)

Các kiểu này dùng để lưu trữ số nguyên (không có phần thập phân).

| Kiểu dữ liệu | Kích thước | Phạm vi giá trị             | Ứng dụng phổ biến                   |
| :----------- | :--------- | :-------------------------- | :---------------------------------- |
| **`byte`**   | 1 byte     | -128 đến 127                | Tiết kiệm bộ nhớ trong mảng lớn.    |
| **`short`**  | 2 bytes    | -32,768 đến 32,767          | Ít dùng hơn `int`.                  |
| **`int`**    | 4 bytes    | Khoảng +/- 2 tỷ             | Kiểu mặc định và phổ biến nhất.     |
| **`long`**   | 8 bytes    | Rất lớn (+/- 9 quintillion) | Lưu trữ số lớn (như ID, timestamp). |

Lưu ý: Khi gán giá trị cho long, nên thêm chữ L hoặc l ở cuối.

```java
int diemSo = 100;
long danSoTheGioi = 8000000000L;
```

#### 2. Các Kiểu Số Thực (Floating-Point Numbers)

Các kiểu này dùng để lưu trữ số có phần thập phân.

| Kiểu dữ liệu | Kích thước | Độ chính xác     | Ứng dụng phổ biến                |
| :----------- | :--------- | :--------------- | :------------------------------- |
| **`float`**  | 4 bytes    | Đơn (6-7 chữ số) | Tiết kiệm bộ nhớ.                |
| **`double`** | 8 bytes    | Kép (15 chữ số)  | Kiểu mặc định và chính xác nhất. |

Lưu ý: Khi gán giá trị cho float, phải thêm chữ F hoặc f ở cuối.

```java
double PI = 3.1415926535; // Mặc định là double
float tyGia = 24500.5f; // Bắt buộc phải có 'f'
```

#### 3. Kiểu Ký Tự (Character)

Kiểu char dùng để lưu trữ một ký tự đơn, được đặt trong dấu nháy đơn (' ').

```java
char diemA = 'A';
char kyTuDacBiet = '$';
```

#### 4. Kiểu Logic (Boolean)

Kiểu boolean chỉ có hai giá trị: true hoặc false, dùng cho logic điều kiện.

```java
boolean laSinhVien = true;
boolean coLoi = false;
```

### III. Kiểu Dữ Liệu Tham Chiếu (Reference Data Types)

Không giống như kiểu nguyên thủy, kiểu tham chiếu không lưu trữ trực tiếp giá trị mà lưu trữ địa chỉ (tham chiếu) đến đối tượng trong bộ nhớ.

Ví dụ: String, Array, Class, Interface.

#### 1. Kiểu Chuỗi (String)

String là kiểu tham chiếu phổ biến nhất, dùng để lưu trữ chuỗi ký tự, được đặt trong dấu nháy kép (" ").

```java
String tenBlog = "Blog Java";
String loiChao = "Chào mừng bạn!";

// String có thể được nối chuỗi (Concatenation)
String thongBao = loiChao + " Đến với " + tenBlog;
```

#### 2. Mảng (Array)

Mảng là một tập hợp các phần tử có cùng kiểu dữ liệu và có kích thước cố định.

```java
// Khai báo một mảng các số nguyên (int)
int[] diemThi = {90, 85, 95};

// Khai báo một mảng các chuỗi (String)
String[] danhSachTen = new String[5];
```

#### 3. Kiểu Lớp/Đối tượng Tự Định Nghĩa (Class/Object)

Bất kỳ Class nào bạn tạo ra đều là một kiểu dữ liệu tham chiếu (ví dụ: XeHoi từ Bài 2).

```java
// Giả sử có Class 'SinhVien' đã được định nghĩa
// Tạo một đối tượng (tham chiếu) SinhVien mới
SinhVien svMoi = new SinhVien("An", 20);

// So sánh đối tượng (so sánh địa chỉ bộ nhớ)
SinhVien svKhac = svMoi; // Hai tham chiếu trỏ về cùng một đối tượng
```

#### 4. Interface (Giao diện) và Wrapper Classes

**Interface (Giao diện)**: Dùng để tham chiếu đến các đối tượng triển khai giao diện đó. Ví dụ: List, Map.

**Wrapper Classes**: Các lớp bao bọc (Object) cho các kiểu nguyên thủy, dùng khi cần xử lý kiểu nguyên thủy như một đối tượng (ví dụ: trong các Collection).

### IV. Quy Tắc Gán Giá Trị (Assignment) và Ép Kiểu (Casting)

#### 1. Gán Giá Trị (Assignment)

Sử dụng toán tử = để gán giá trị cho biến.

```java
int x = 10;

x = 20; // Giá trị mới là 20
```

#### 2. Ép Kiểu (Type Casting)

- **Ép kiểu** là chuyển đổi giá trị từ kiểu dữ liệu này sang kiểu dữ liệu khác.
- **Ép kiểu Ngầm Định (Implicit Casting)**: Xảy ra tự động khi chuyển từ kiểu nhỏ hơn sang kiểu lớn hơn (không mất mát dữ liệu).

* Thứ tự: `byte` → `short` → `int` → `long` → `float` → `double`.

```java
int a = 100;
double b = a; // Implicit: b = 100.0 (tự động)
```

- **Ép kiểu Tường Minh (Explicit Casting)**: Phải khai báo kiểu dữ liệu đích (có thể gây mất mát dữ liệu).

```java
double c = 10.99;
int d = (int) c; // Explicit: d = 10 (mất phần thập phân .99)
```

### V. Tổng Kết: Lưu Trữ Hiệu Quả

Việc chọn kiểu dữ liệu phù hợp giúp tối ưu hóa bộ nhớ và độ chính xác của chương trình.
