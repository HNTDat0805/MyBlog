---
title: "CẤU TRÚC ĐIỀU KHIỂN"
date: 2025-10-23
draft: false
description: "Hướng dẫn sử dụng if-else, switch-case, vòng lặp for, while và do-while."
tags: ["java", "điều khiển", "if", "switch", "loop", "vòng lặp"]
---

### I. Mở Đầu: Đưa Ra Quyết Định

**Cấu trúc Điều khiển** giúp kiểm soát luồng thực thi của chương trình, cho phép ra quyết định (chọn nhánh thực thi) và lặp lại (thực hiện một khối lệnh nhiều lần) tùy theo điều kiện cụ thể.

### II. Câu Lệnh Điều Kiện (Conditional Statements)

#### 1. `if`, `else if`, và `else`

Dùng để thực thi một khối code nếu một điều kiện cụ thể là `true`.

```java
int diemSo = 75;

if (diemSo >= 90) {
    System.out.println("Hạng A");
} else if (diemSo >= 70) {
    System.out.println("Hạng B");
} else {
    System.out.println("Hạng C");
}
```

#### 2. switch

Dùng khi bạn có nhiều trường hợp (case) so sánh với cùng một biến. Lệnh break là bắt buộc để thoát khỏi khối switch sau khi thực thi xong một case.

```java
int ngay = 3;
String tenNgay;

switch (ngay) {
    case 1:
        tenNgay = "Chủ Nhật";
        break;
    case 3:
        tenNgay = "Thứ Ba";
        break;
    default:
        tenNgay = "Ngày Không Hợp Lệ";
}
System.out.println("Hôm nay là: " + tenNgay);
```

### III. Vòng Lặp (Loops) - Lặp Lại Hành Động

#### 1. Vòng Lặp for

Thích hợp khi bạn biết chính xác số lần lặp.

Cấu trúc gồm 3 phần: Khởi tạo; Điều kiện lặp; Bước tăng/giảm.

```java
// Lặp 5 lần, từ i=0 đến i=4
for (int i = 0; i < 5; i++) {
    System.out.println("Lặp lần thứ: " + i);
}
```

#### 2. Vòng Lặp while

Lặp liên tục miễn là điều kiện còn đúng (true). Rất quan trọng là phải có một bước thoát bên trong khối lệnh.

```java
int dem = 0;
while (dem < 3) {
    System.out.println("Giá trị đếm: " + dem);
    dem++; // Bước thoát: đảm bảo vòng lặp dừng lại
}
```

#### 3. Vòng Lặp do-while

Khối lệnh được thực thi ít nhất một lần, sau đó mới kiểm tra điều kiện lặp.

```java
int i = 10;
do {
    System.out.println("Chạy ít nhất một lần (vì i = 10)");
    i++;
} while (i < 5); // Điều kiện này sai ngay lần đầu, nhưng khối lệnh vẫn chạy 1 lần
```

### IV. Lệnh Điều Khiển Vòng Lặp

Đây là các lệnh dùng để thay đổi luồng hoạt động của vòng lặp:

| Lệnh           | Ý nghĩa                                                       |
| :------------- | :------------------------------------------------------------ |
| **`break`**    | Thoát **hoàn toàn** khỏi vòng lặp hiện tại.                   |
| **`continue`** | Bỏ qua **lần lặp hiện tại** và chuyển sang lần lặp tiếp theo. |

```java
for (int j = 1; j <= 5; j++) {
    if (j == 3) {
        continue; // Khi j=3, bỏ qua lệnh in và nhảy sang j=4
    }
    if (j == 5) {
        break; // Khi j=5, thoát hoàn toàn khỏi vòng lặp
    }
    System.out.println("Giá trị: " + j); // Chỉ in ra 1, 2, 4
}
```

### V. Kết Luận

Cấu trúc điều khiển là nền tảng của mọi logic phức tạp. Nắm vững các cấu trúc này giúp bạn tạo ra các chương trình thông minh hơn.
