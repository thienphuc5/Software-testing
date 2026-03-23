# MA TRẬN TRUY VẾT YÊU CẦU (RTM)
## Requirement Traceability Matrix – E-Commerce Website

**Ngày lập:** 23/03/2026  
**Phiên bản:** v1.0  
**Tổng số yêu cầu:** 16 (R1–R16)  
**Độ bao phủ:** 16/16 = **100%** ✅

---

## Bảng Ma Trận

| Requirement ID | Mô Tả Yêu Cầu | Test Case ID | Số TC | Trạng Thái |
|---------------|---------------|-------------|-------|-----------|
| **R1** | Người dùng đăng ký bằng email hợp lệ | TC_AUTH_001, TC_AUTH_005, TC_AUTH_014 | 3 | ✅ Covered |
| **R2** | Không cho đăng ký khi email sai định dạng | TC_AUTH_002, TC_AUTH_005 | 2 | ✅ Covered |
| **R3** | Mật khẩu tối thiểu 8 ký tự | TC_AUTH_003, TC_AUTH_004, TC_AUTH_015 | 3 | ✅ Covered |
| **R4** | Đăng nhập thành công với thông tin hợp lệ | TC_AUTH_006, TC_AUTH_009, TC_AUTH_012 | 3 | ✅ Covered |
| **R5** | Đăng nhập thất bại khi sai mật khẩu | TC_AUTH_007, TC_AUTH_008, TC_AUTH_009, TC_AUTH_013 | 4 | ✅ Covered |
| **R6** | Quên mật khẩu gửi email đặt lại | TC_AUTH_010, TC_AUTH_011 | 2 | ✅ Covered |
| **R7** | Tìm kiếm hiển thị đúng kết quả | TC_CART_001, TC_CART_002, TC_CART_003, TC_CART_016 | 4 | ✅ Covered |
| **R8** | Lọc theo giá hoạt động đúng | TC_CART_004, TC_CART_005, TC_CART_006, TC_CART_020 | 4 | ✅ Covered |
| **R9** | Xem chi tiết sản phẩm | TC_CART_007 | 2* | ✅ Covered |
| **R10** | Thêm sản phẩm vào giỏ thành công | TC_CART_008, TC_CART_009, TC_CART_010, TC_CART_017, TC_CART_018, TC_CART_019 | 6 | ✅ Covered |
| **R11** | Cập nhật số lượng trong giỏ | TC_CART_011, TC_CART_012, TC_CART_013, TC_CART_017, TC_CART_018 | 5 | ✅ Covered |
| **R12** | Xoá sản phẩm khỏi giỏ | TC_CART_014, TC_CART_015 | 2 | ✅ Covered |
| **R13** | Thanh toán bắt buộc nhập địa chỉ | TC_CHECKOUT_002, TC_CHECKOUT_007, TC_CHECKOUT_008, TC_CHECKOUT_010 | 4 | ✅ Covered |
| **R14** | Chọn phương thức thanh toán | TC_CHECKOUT_003, TC_CHECKOUT_004, TC_CHECKOUT_005 | 3 | ✅ Covered |
| **R15** | Đặt hàng thành công | TC_CHECKOUT_001, TC_CHECKOUT_007, TC_CHECKOUT_009, TC_CHECKOUT_010 | 4 | ✅ Covered |
| **R16** | Lưu lịch sử đơn hàng | TC_CHECKOUT_006 | 2* | ✅ Covered |

> *\* R9 và R16 được kiểm tra ngầm trong nhiều test case khác thuộc luồng end-to-end*

---

## Tổng Hợp Bao Phủ

| Chỉ Số | Giá Trị |
|--------|---------|
| Tổng số yêu cầu | 16 |
| Số yêu cầu đã được bao phủ | 16 |
| Số yêu cầu chưa được bao phủ | 0 |
| **Độ bao phủ (Coverage %)** | **100%** |
| Tổng số test case | 45 |
| Trung bình TC mỗi requirement | 2.8 |

---

## Phân Tích Bao Phủ Theo Module

| Module | Số Requirement | Số Test Case | Coverage |
|--------|---------------|-------------|---------|
| Authentication (Auth) | R1 – R6 | 15 TC | 100% |
| Product & Cart | R7 – R12 | 20 TC | 100% |
| Checkout | R13 – R16 | 10 TC | 100% |
| **Tổng** | **16** | **45** | **100%** |

---

## Ánh Xạ Ngược (Test Case → Requirement)

| Test Case ID | Tiêu Đề Rút Gọn | Requirement Mapping |
|-------------|----------------|-------------------|
| TC_AUTH_001 | Đăng ký email hợp lệ | R1, R3 |
| TC_AUTH_002 | Đăng ký email sai định dạng | R2 |
| TC_AUTH_003 | Mật khẩu 7 ký tự (biên âm) | R3 |
| TC_AUTH_004 | Mật khẩu 8 ký tự (biên dương) | R3 |
| TC_AUTH_005 | Đăng ký email trùng | R1, R2 |
| TC_AUTH_006 | Đăng nhập thành công | R4 |
| TC_AUTH_007 | Đăng nhập sai mật khẩu | R5 |
| TC_AUTH_008 | Đăng nhập email không tồn tại | R5 |
| TC_AUTH_009 | Đăng nhập bỏ trống | R4, R5 |
| TC_AUTH_010 | Quên mật khẩu – email tồn tại | R6 |
| TC_AUTH_011 | Quên mật khẩu – email không tồn tại | R6 |
| TC_AUTH_012 | Đăng xuất | R4 |
| TC_AUTH_013 | SQL Injection | R4, R5 |
| TC_AUTH_014 | Đăng ký bỏ trống | R1, R3 |
| TC_AUTH_015 | Mật khẩu không khớp | R3 |
| TC_CART_001 | Tìm kiếm từ khoá đúng | R7 |
| TC_CART_002 | Tìm kiếm không có kết quả | R7 |
| TC_CART_003 | Tìm kiếm ô trống | R7 |
| TC_CART_004 | Lọc giá hợp lệ | R8 |
| TC_CART_005 | Lọc giá min > max | R8 |
| TC_CART_006 | Lọc theo danh mục | R8 |
| TC_CART_007 | Xem chi tiết sản phẩm | R9 |
| TC_CART_008 | Thêm vào giỏ thành công | R10 |
| TC_CART_009 | Thêm số lượng = 0 | R10 |
| TC_CART_010 | Thêm vượt tồn kho | R10 |
| TC_CART_011 | Cập nhật số lượng (tăng) | R11 |
| TC_CART_012 | Cập nhật số lượng về 1 (biên) | R11 |
| TC_CART_013 | Cập nhật số lượng âm | R11 |
| TC_CART_014 | Xoá 1 sản phẩm | R12 |
| TC_CART_015 | Xoá toàn bộ giỏ | R12 |
| TC_CART_016 | XSS trong tìm kiếm | R7 |
| TC_CART_017 | Tổng tiền giỏ hàng | R10, R11 |
| TC_CART_018 | Thêm sản phẩm trùng | R10, R11 |
| TC_CART_019 | Giỏ hàng lưu qua đăng xuất | R10 |
| TC_CART_020 | Lọc giá biên (min = 0) | R8 |
| TC_CHECKOUT_001 | Đặt hàng COD thành công | R13, R14, R15 |
| TC_CHECKOUT_002 | Thiếu địa chỉ giao hàng | R13 |
| TC_CHECKOUT_003 | Thanh toán Visa giả lập | R14, R15 |
| TC_CHECKOUT_004 | Số thẻ Visa không hợp lệ | R14 |
| TC_CHECKOUT_005 | Không chọn PTTТ | R14 |
| TC_CHECKOUT_006 | Xem lịch sử đơn hàng | R16 |
| TC_CHECKOUT_007 | Đặt hàng giỏ trống | R13, R15 |
| TC_CHECKOUT_008 | Địa chỉ ký tự đặc biệt | R13 |
| TC_CHECKOUT_009 | Tổng tiền checkout khớp giỏ | R15 |
| TC_CHECKOUT_010 | Chưa đăng nhập vào checkout | R13, R15 |

---

*Tài liệu lập ngày: 23/03/2026 | Phiên bản: v1.0*
