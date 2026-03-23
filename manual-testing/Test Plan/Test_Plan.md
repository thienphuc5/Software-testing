# KẾ HOẠCH KIỂM THỬ (TEST PLAN)
## Hệ thống: Website Bán Hàng Online (E-Commerce)

---

## 1. Giới Thiệu (Introduction)

### 1.1 Mục Đích
Tài liệu này mô tả kế hoạch kiểm thử thủ công (manual testing) cho hệ thống website bán hàng online. Mục đích nhằm đảm bảo các chức năng cốt lõi hoạt động đúng theo yêu cầu đặc tả trước khi phát hành sản phẩm.

### 1.2 Tài Liệu Tham Chiếu
- Danh sách yêu cầu hệ thống (R1–R16)
- Ca kiểm thử (Test Cases): TC_AUTH_001 → TC_AUTH_015, TC_CART_001 → TC_CART_020, TC_CHECKOUT_001 → TC_CHECKOUT_010
- Báo cáo lỗi (Bug Reports): BUG_AUTH_*, BUG_CART_*, BUG_CHECKOUT_*

### 1.3 Người Thực Hiện
- Nhóm: Kiểm thử thủ công (Manual QA Team)
- Sinh viên: Nguyễn Thiện Phúc
- Giảng viên hướng dẫn: [Tên giảng viên]

---

## 2. Phạm Vi Kiểm Thử (Scope)

### 2.1 Trong Phạm Vi (In-Scope)

| Module | Chức Năng |
|--------|-----------|
| **Module 1 – Xác Thực (Authentication)** | Đăng ký tài khoản, Đăng nhập, Quên mật khẩu, Đăng xuất |
| **Module 2 – Sản Phẩm & Giỏ Hàng (Product & Cart)** | Tìm kiếm sản phẩm, Lọc theo giá/danh mục, Xem chi tiết, Thêm/Cập nhật/Xoá khỏi giỏ |
| **Module 3 – Thanh Toán (Checkout)** | Nhập địa chỉ giao hàng, Chọn phương thức thanh toán, Đặt hàng, Xem lịch sử |

### 2.2 Ngoài Phạm Vi (Out-of-Scope)
- Kiểm thử hiệu năng (Performance Testing)
- Kiểm thử tự động (Automation Testing)
- Kiểm thử bảo mật nâng cao (Penetration Testing)
- Kiểm thử tương thích trình duyệt đa nền tảng (Cross-browser Testing ngoài Chrome)
- API Testing / Backend Testing

---

## 3. Phương Pháp Kiểm Thử (Test Approach)

### 3.1 Kiểm Thử Chức Năng (Functional Testing)
- Xác minh từng chức năng hoạt động đúng theo yêu cầu
- Bao gồm cả test case dương (positive), âm (negative) và biên (boundary)
- Kiểm tra các trường hợp validation đầu vào

### 3.2 Kiểm Thử Giao Diện Cơ Bản (UI Testing – Basic)
- Kiểm tra hiển thị đúng nội dung, thông báo lỗi
- Xác minh điều hướng (navigation) giữa các trang
- Kiểm tra nút bấm, biểu mẫu (form) hoạt động đúng

### 3.3 Kiểm Thử Hồi Quy Khói (Regression – Smoke Testing)
- Sau mỗi sửa lỗi, chạy lại các test case cốt lõi (smoke suite)
- Đảm bảo chức năng không bị ảnh hưởng ngoài ý muốn

### 3.4 Kỹ Thuật Thiết Kế Test Case
- **Equivalence Partitioning**: Phân chia dữ liệu đầu vào thành các nhóm tương đương
- **Boundary Value Analysis**: Kiểm tra giá trị biên (min, max, min±1, max±1)
- **Error Guessing**: Dựa vào kinh nghiệm để đoán các lỗi tiềm ẩn

---

## 4. Môi Trường Kiểm Thử (Test Environment)

| Thành Phần | Thông Tin |
|------------|-----------|
| **Trình Duyệt** | Google Chrome (phiên bản mới nhất) |
| **Hệ Điều Hành** | Windows 10/11 |
| **Độ Phân Giải** | 1920×1080 |
| **Dữ Liệu Test** | Tài khoản giả lập (test@example.com / Test@12345) |
| **Môi Trường** | Staging / UAT (không phải production) |
| **Kết Nối Mạng** | Có kết nối Internet ổn định |

### Dữ Liệu Kiểm Thử Mẫu
| Loại | Giá Trị |
|------|---------|
| Email hợp lệ | `testuser@example.com` |
| Email không hợp lệ | `testuser@`, `abc`, `@domain.com` |
| Mật khẩu đúng | `Test@12345` |
| Mật khẩu sai | `wrongpass`, `12345` |
| Mật khẩu biên | 7 ký tự, 8 ký tự, 9 ký tự |

---

## 5. Điều Kiện Vào / Ra (Entry / Exit Criteria)

### 5.1 Điều Kiện Vào (Entry Criteria)
- Môi trường test đã được thiết lập và hoạt động
- Tài liệu yêu cầu (requirements) đã được duyệt
- Test case đã được thiết kế và review
- Dữ liệu test đã sẵn sàng
- Bản dựng (build) ứng dụng đã được triển khai lên môi trường Staging

### 5.2 Điều Kiện Ra (Exit Criteria)
- Tối thiểu 90% test case đã được thực thi
- Tỷ lệ pass ≥ 80%
- Tất cả bug mức Critical đã được sửa và kiểm tra lại
- Tất cả bug mức Major đã có phương án xử lý hoặc được đánh giá chấp nhận rủi ro
- Báo cáo kiểm thử đã được lập và ký duyệt

---

## 6. Rủi Ro & Biện Pháp Giảm Thiểu (Risks & Mitigation)

| STT | Rủi Ro | Mức Độ | Biện Pháp Giảm Thiểu |
|-----|--------|--------|----------------------|
| 1 | Môi trường test không ổn định | Cao | Thiết lập môi trường dự phòng; kiểm tra trước khi chạy |
| 2 | Yêu cầu thay đổi giữa chu kỳ test | Trung bình | Đóng băng yêu cầu (requirement freeze) trước khi test |
| 3 | Thiếu dữ liệu test phù hợp | Trung bình | Chuẩn bị sẵn bộ dữ liệu test đầy đủ trước khi bắt đầu |
| 4 | Thời gian kiểm thử bị rút ngắn | Cao | Ưu tiên test case theo mức độ nghiêm trọng (Critical first) |
| 5 | Lỗi phát sinh muộn gần ngày release | Cao | Chạy smoke test hàng ngày; báo cáo tức thì |
| 6 | Năng lực kiểm thử viên hạn chế | Thấp | Hướng dẫn và review test case trước khi thực thi |

---

## 7. Vai Trò & Trách Nhiệm (Roles & Responsibilities)

| Vai Trò | Trách Nhiệm | Người Thực Hiện |
|---------|------------|-----------------|
| Test Lead | Lập kế hoạch, phân công công việc, tổng hợp báo cáo | Nhóm trưởng |
| QA Engineer | Thiết kế và thực thi test case | Thành viên nhóm |
| Bug Reporter | Ghi nhận và theo dõi lỗi | Thành viên nhóm |
| Developer | Sửa lỗi được báo cáo | [Developer Team] |
| Stakeholder | Duyệt kết quả và quyết định release | Giảng viên / PO |

---

## 8. Lịch Trình Kiểm Thử (Test Schedule – Giả Lập)

| Giai Đoạn | Hoạt Động | Bắt Đầu | Kết Thúc | Người Phụ Trách |
|-----------|-----------|---------|---------|-----------------|
| Chuẩn bị | Thiết kế test case, chuẩn bị dữ liệu | 17/03/2026 | 19/03/2026 | Test Lead |
| Thực thi – Module Auth | Chạy TC_AUTH_001 → 015 | 20/03/2026 | 21/03/2026 | QA Engineer |
| Thực thi – Module Cart | Chạy TC_CART_001 → 020 | 21/03/2026 | 22/03/2026 | QA Engineer |
| Thực thi – Module Checkout | Chạy TC_CHECKOUT_001 → 010 | 22/03/2026 | 23/03/2026 | QA Engineer |
| Báo cáo lỗi | Ghi nhận và phân loại bug | 20/03/2026 | 23/03/2026 | Bug Reporter |
| Kiểm tra lại (Retest) | Verify bug đã sửa | 23/03/2026 | 24/03/2026 | QA Engineer |
| Tổng hợp báo cáo | Lập Test Report & Metrics | 24/03/2026 | 25/03/2026 | Test Lead |

---

## 9. Công Cụ Kiểm Thử (Test Tools)

| Công Cụ | Mục Đích |
|---------|----------|
| Google Chrome DevTools | Kiểm tra console, network requests |
| Microsoft Excel / Google Sheets | Quản lý test case, RTM, bug report |
| Google Docs / Markdown | Viết tài liệu kế hoạch và báo cáo |
| Snipping Tool / Lightshot | Chụp màn hình bằng chứng |
| Jira (giả lập) | Theo dõi bug và tiến độ |

---

## 10. Tiêu Chí Đánh Giá Chất Lượng (Quality Acceptance Criteria)

- Tất cả yêu cầu (R1–R16) đều có ít nhất 2 test case mapping
- Độ bao phủ yêu cầu ≥ 95%
- Không còn bug Critical chưa được xử lý
- Tỷ lệ test case Pass ≥ 80% tổng số đã thực thi

---

*Tài liệu này được lập ngày: 23/03/2026*
*Phiên bản: v1.0*
