# Chương 1: Can't Unsee (tên trò chơi luyện lỗi UI/UX)

## Mô tả bài tập
Can't Unsee (trò chơi luyện nhận diện lỗi) là một trò chơi nhỏ giúp rèn luyện khả năng phát hiện các lỗi trong thiết kế UI/UX (giao diện người dùng/trải nghiệm người dùng).
Bài tập yêu cầu quan sát và nhận diện các vấn đề liên quan đến:
- Căn chỉnh giao diện
- Khoảng cách giữa các thành phần
- Tính nhất quán
- Khả năng đọc và trải nghiệm người dùng

🔗 Liên kết bài tập: [https://cantunsee.space](https://cantunsee.space) (trang web của trò chơi)

## Kết quả đạt được
Điểm số: 

Kết quả cho thấy khả năng quan sát và nhận diện lỗi giao diện ở mức tốt so với đa số người tham gia.

### Ảnh chụp màn hình kết quả sau khi hoàn thành bài tập:
![Kết quả Can't Unsee](Screenshot%202026-01-05%20222127.png)


# Chương 2: Bài tập thực hành JUnit – Phân tích điểm số học sinh

## Mô tả
Chương trình phân tích danh sách điểm học sinh:
- Đếm số học sinh đạt loại Giỏi (>= 8.0)
- Tính điểm trung bình hợp lệ (0–10)

Các điểm không hợp lệ (<0 hoặc >10) sẽ bị bỏ qua.

## Công nghệ sử dụng
- Java
- JUnit 5

## Cấu trúc thư mục
unit-test/  
├── src/  
├── test/  
└── README.md

## Cách chạy kiểm thử
###  IntelliJ
- Chuột trái vào `StudentAnalyzerTest`,
- Chọn dấu tam giác để chạy từng test


# Chương 3: Bài tập thực hành kiểm thử tự động End-to-End với Cypress

## Mô tả
Thực hành các kịch bản kiểm thử tự động end-to-end phổ biến trên trang web mẫu https://www.saucedemo.com.

## Các kịch bản kiểm thử
1. Đăng nhập (Thành công & Thất bại)
2. Quản lý giỏ hàng (Thêm & Xóa sản phẩm)
3. Sắp xếp sản phẩm
4. Quy trình thanh toán (Checkout)

## Công nghệ sử dụng
- Node.js
- Cypress

## Cấu trúc thư mục
cypress-exercise/
├── cypress/
│   ├── e2e/
│   │   ├── login_spec.cy.js
│   │   ├── cart_spec.cy.js
│   │   └── checkout_spec.cy.js
│   └── videos/
├── cypress.config.js
└── package.json

## Cách chạy kiểm thử
1. Mở terminal tại thư mục `cypress-exercise`
2. Chạy lệnh: `npx cypress run` (chạy ngầm) hoặc `npx cypress open` (giao diện)

Sinh viên: Nguyễn Thiện Phúc
