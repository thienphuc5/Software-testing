# BÁO CÁO KIỂM THỬ (TEST REPORT)
## E-Commerce Website – Manual Testing
**Ngày lập:** 23/03/2026 | **Phiên bản:** v1.0 | **Chu kỳ kiểm thử:** Sprint 1

---

## 1. Tổng Quan Thực Thi

| Chỉ Số | Giá Trị |
|--------|---------|
| Tổng số test case | 45 |
| Số TC đã thực thi | 45 |
| Số TC **Pass** | 31 |
| Số TC **Fail** | 13 |
| Số TC **Blocked** | 1 |
| Tỷ lệ thực thi (Execution Rate) | 100% |
| Tỷ lệ Pass | **68.9%** |
| Tỷ lệ Fail | 28.9% |

---

## 2. Kết Quả Theo Module

| Module | Tổng TC | Pass | Fail | Blocked | Pass Rate |
|--------|---------|------|------|---------|-----------|
| Authentication | 15 | 11 | 3 | 1 | 73.3% |
| Product & Cart | 20 | 14 | 6 | 0 | 70.0% |
| Checkout | 10 | 6 | 4 | 0 | 60.0% |
| **Tổng** | **45** | **31** | **13** | **1** | **68.9%** |

> *Blocked: TC_AUTH_010 – Không thể kiểm tra email reset do môi trường staging chưa cấu hình SMTP*

---

## 3. Phân Bố Kết Quả Test Case

```
PASS    ████████████████████████████████  31 TC (68.9%)
FAIL    ████████████░░                   13 TC (28.9%)
BLOCKED █░░░░░░░░░░░░░░                   1 TC (2.2%)
```

---

## 4. Top 5 Lỗi Nghiêm Trọng Nhất

| Thứ Tự | Bug ID | Mô Tả | Severity | Module |
|--------|--------|--------|----------|--------|
| 1 | BUG_CHECKOUT_001 | Người chưa đăng nhập có thể truy cập trang thanh toán | 🔴 Critical | Checkout |
| 2 | BUG_CHECKOUT_002 | Tổng tiền trang checkout không khớp giỏ hàng | 🔴 Critical | Checkout |
| 3 | BUG_CART_001 | Tổng tiền giỏ hàng không cập nhật sau khi thay đổi SL | 🔴 Critical | Cart |
| 4 | BUG_AUTH_001 | Cho đăng ký với email trống | 🔴 Critical | Auth |
| 5 | BUG_AUTH_002 | Mật khẩu 7 ký tự qua được validation | 🔴 Critical | Auth |

---

## 5. Thống Kê Bug Theo Severity

| Severity | Số Lượng | Tỷ Lệ |
|----------|---------|-------|
| 🔴 Critical | 5 | 38.5% |
| 🟠 Major | 6 | 46.1% |
| 🟡 Minor | 2 | 15.4% |
| **Tổng** | **13** | **100%** |

---

## 6. Nhận Xét Chất Lượng Hệ Thống

### 6.1 Vấn Đề Tìm Thấy

**Module Authentication:**
- Validation phía server cho email và mật khẩu chưa hoạt động đúng (BUG_AUTH_001, BUG_AUTH_002)
- Thông báo lỗi tiết lộ thông tin về tài khoản (BUG_AUTH_003) – rủi ro bảo mật
- UX kém: không có phản hồi sau khi gửi email reset mật khẩu (BUG_AUTH_004)

**Module Product & Cart:**
- Lỗi tính toán tổng tiền nghiêm trọng (BUG_CART_001) – ảnh hưởng trực tiếp đến doanh thu
- Có thể nhập số lượng âm (BUG_CART_002) – gây dữ liệu không nhất quán
- Logic hợp nhất sản phẩm trong giỏ sai (BUG_CART_004)

**Module Checkout:**
- **Lỗ hổng bảo mật nghiêm trọng**: trang checkout không yêu cầu xác thực (BUG_CHECKOUT_001)
- Tổng tiền sai ở trang thanh toán (BUG_CHECKOUT_002) – ảnh hưởng trực tiếp đến kinh doanh
- Giỏ hàng không được xoá sau đặt hàng → nguy cơ đặt đơn trùng (BUG_CHECKOUT_004)

### 6.2 Điểm Tích Cực
- Chức năng tìm kiếm cơ bản hoạt động đúng
- Lọc theo danh mục hoạt động ổn định
- Xem chi tiết sản phẩm hiển thị đầy đủ thông tin
- Xoá sản phẩm khỏi giỏ hoạt động đúng
- UI nhìn chung rõ ràng, dễ sử dụng

---

## 7. Quyết Định Phát Hành (Release Decision)

> ## ❌ NO-RELEASE – KHÔNG CHO PHÉP PHÁT HÀNH

**Lý do:**
1. Còn **5 bug Critical** chưa được khắc phục
2. **Lỗ hổng bảo mật nghiêm trọng** (BUG_CHECKOUT_001): trang thanh toán không yêu cầu đăng nhập
3. **Lỗi tính tiền** (BUG_CHECKOUT_002, BUG_CART_001): ảnh hưởng trực tiếp đến doanh thu
4. Tỷ lệ Pass chỉ đạt **68.9%** – dưới ngưỡng chấp nhận (≥80%)

**Điều kiện để xem xét phát hành:**
- Tất cả 5 bug Critical phải được sửa và kiểm tra lại (retest)
- Ít nhất 4/6 bug Major phải được sửa
- Tỷ lệ Pass ≥ 80% sau khi retest

---

## 8. Đề Xuất Hành Động Tiếp Theo

| Ưu Tiên | Hành Động | Phụ Trách |
|---------|-----------|-----------|
| 1 | Sửa BUG_CHECKOUT_001 (bảo mật – redirect về login) | Dev Backend |
| 2 | Sửa BUG_CHECKOUT_002 và BUG_CART_001 (tính tiền sai) | Dev Frontend/Backend |
| 3 | Sửa BUG_AUTH_001 và BUG_AUTH_002 (validation đăng ký) | Dev Frontend |
| 4 | Sửa các bug Major còn lại | Dev |
| 5 | Retest toàn bộ sau khi sửa lỗi | QA Team |
| 6 | Chạy Regression Test trên các module bị ảnh hưởng | QA Team |

---

*Báo cáo lập ngày: 23/03/2026 | Người lập: Nguyễn Thiện Phúc | Phiên bản: v1.0*
