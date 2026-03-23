# BÁO CÁO LỖI (BUG REPORTS)
## E-Commerce Website – Manual Testing
**Tổng số bug:** 12 | **Ngày lập:** 23/03/2026

---

## BUG_AUTH_001 – Đăng ký thành công dù email bỏ trống

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_AUTH_001 |
| **Tóm tắt** | Hệ thống cho phép đăng ký khi trường Email bị bỏ trống |
| **Module** | Authentication |
| **Test Case liên quan** | TC_AUTH_014 |
| **Các bước tái hiện** | 1. Mở trang `/register` <br>2. Nhập Mật khẩu: `Test@12345` và Xác nhận mật khẩu <br>3. Để trống trường Email <br>4. Nhấn **"Đăng ký"** |
| **Kết quả mong đợi** | Hiển thị thông báo lỗi: "Email không được để trống" |
| **Kết quả thực tế** | Form được submit thành công, hệ thống tạo tài khoản với email rỗng |
| **Mức độ nghiêm trọng** | 🔴 Critical |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_AUTH_002 – Mật khẩu 7 ký tự vượt qua validation

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_AUTH_002 |
| **Tóm tắt** | Hệ thống cho phép đăng ký với mật khẩu chỉ 7 ký tự (dưới giới hạn tối thiểu) |
| **Module** | Authentication |
| **Test Case liên quan** | TC_AUTH_003 |
| **Các bước tái hiện** | 1. Mở trang `/register` <br>2. Nhập email hợp lệ <br>3. Nhập mật khẩu: `Test@12` (7 ký tự) <br>4. Nhập xác nhận mật khẩu: `Test@12` <br>5. Nhấn **"Đăng ký"** |
| **Kết quả mong đợi** | Lỗi: "Mật khẩu phải có ít nhất 8 ký tự" |
| **Kết quả thực tế** | Đăng ký thành công dù mật khẩu chỉ có 7 ký tự |
| **Mức độ nghiêm trọng** | 🔴 Critical |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_AUTH_003 – Thông báo lỗi đăng nhập tiết lộ email có tồn tại

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_AUTH_003 |
| **Tóm tắt** | Hệ thống trả về thông báo khác nhau khi email không tồn tại vs sai mật khẩu, gây rủi ro bảo mật |
| **Module** | Authentication |
| **Test Case liên quan** | TC_AUTH_008 |
| **Các bước tái hiện** | 1. Mở trang `/login` <br>2. Nhập email không tồn tại + bất kỳ mật khẩu <br>3. Quan sát thông báo lỗi <br>4. Thử lại với email có thật nhưng sai mật khẩu <br>5. So sánh thông báo |
| **Kết quả mong đợi** | Cả 2 trường hợp đều hiển thị thông báo chung: "Email hoặc mật khẩu không đúng" |
| **Kết quả thực tế** | Trường hợp email không tồn tại hiển thị: "Email không tìm thấy" → lộ thông tin |
| **Mức độ nghiêm trọng** | 🟠 Major |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CART_001 – Tổng tiền giỏ hàng tính sai khi cập nhật số lượng

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CART_001 |
| **Tóm tắt** | Tổng tiền giỏ hàng không được cập nhật sau khi thay đổi số lượng sản phẩm |
| **Module** | Product & Cart |
| **Test Case liên quan** | TC_CART_011, TC_CART_017 |
| **Các bước tái hiện** | 1. Đăng nhập và thêm "Áo thun" (150.000đ) × 1 vào giỏ <br>2. Mở trang giỏ hàng <br>3. Tăng số lượng lên 3 <br>4. Quan sát tổng tiền |
| **Kết quả mong đợi** | Tổng = 150.000 × 3 = 450.000đ |
| **Kết quả thực tế** | Tổng vẫn hiển thị 150.000đ (không tự động cập nhật; cần F5 mới đúng) |
| **Mức độ nghiêm trọng** | 🔴 Critical |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CART_002 – Có thể thêm số lượng âm vào giỏ hàng

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CART_002 |
| **Tóm tắt** | Hệ thống chấp nhận số lượng âm khi cập nhật giỏ hàng, gây lỗi hiển thị tổng tiền |
| **Module** | Product & Cart |
| **Test Case liên quan** | TC_CART_013 |
| **Các bước tái hiện** | 1. Mở trang giỏ hàng có sản phẩm <br>2. Nhập số lượng: `-2` <br>3. Nhấn cập nhật |
| **Kết quả mong đợi** | Lỗi validation: "Số lượng phải lớn hơn 0" |
| **Kết quả thực tế** | Hệ thống chấp nhận, giỏ hàng hiển thị số lượng: -2; tổng tiền bị âm |
| **Mức độ nghiêm trọng** | 🟠 Major |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CART_003 – Lọc giá không hoạt động khi giá min > giá max

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CART_003 |
| **Tóm tắt** | Khi nhập giá min lớn hơn giá max, hệ thống vẫn thực hiện lọc thay vì báo lỗi |
| **Module** | Product & Cart |
| **Test Case liên quan** | TC_CART_005 |
| **Các bước tái hiện** | 1. Mở trang danh sách sản phẩm <br>2. Nhập giá min: `900000`, giá max: `100000` <br>3. Nhấn **Áp dụng** |
| **Kết quả mong đợi** | Lỗi: "Giá tối thiểu không được lớn hơn giá tối đa" |
| **Kết quả thực tế** | Hệ thống thực hiện lọc và hiển thị danh sách trống mà không có thông báo lỗi |
| **Mức độ nghiêm trọng** | 🟠 Major |
| **Độ ưu tiên** | Medium |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CART_004 – Thêm cùng sản phẩm tạo ra 2 dòng riêng biệt trong giỏ

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CART_004 |
| **Tóm tắt** | Thêm sản phẩm đã có trong giỏ tạo ra 2 dòng riêng thay vì cộng số lượng |
| **Module** | Product & Cart |
| **Test Case liên quan** | TC_CART_018 |
| **Các bước tái hiện** | 1. Thêm "Chuột" vào giỏ <br>2. Quay lại trang sản phẩm "Chuột" <br>3. Thêm "Chuột" lần 2 <br>4. Kiểm tra giỏ hàng |
| **Kết quả mong đợi** | Giỏ hàng: "Chuột" × 2 (1 dòng duy nhất) |
| **Kết quả thực tế** | Giỏ hàng: 2 dòng "Chuột" × 1 riêng biệt → tổng tiền bị tính đúng nhưng giao diện rối |
| **Mức độ nghiêm trọng** | 🟠 Major |
| **Độ ưu tiên** | Medium |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CHECKOUT_001 – Trang thanh toán có thể truy cập khi chưa đăng nhập

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CHECKOUT_001 |
| **Tóm tắt** | Người dùng chưa đăng nhập có thể truy cập trực tiếp URL `/checkout` |
| **Module** | Checkout |
| **Test Case liên quan** | TC_CHECKOUT_010 |
| **Các bước tái hiện** | 1. Mở trình duyệt không có session đăng nhập <br>2. Nhập trực tiếp URL: `https://shop.example.com/checkout` |
| **Kết quả mong đợi** | Chuyển hướng về `/login` |
| **Kết quả thực tế** | Trang checkout hiển thị đầy đủ; người dùng có thể nhập địa chỉ và nhấn đặt hàng |
| **Mức độ nghiêm trọng** | 🔴 Critical |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CHECKOUT_002 – Tổng tiền trang checkout không khớp với giỏ hàng

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CHECKOUT_002 |
| **Tóm tắt** | Tổng tiền hiển thị trong trang checkout nhỏ hơn tổng tiền trong giỏ hàng |
| **Module** | Checkout |
| **Test Case liên quan** | TC_CHECKOUT_009 |
| **Các bước tái hiện** | 1. Thêm 2 sản phẩm vào giỏ: Áo thun × 2 (300.000đ) + Bàn phím × 1 (350.000đ) = 650.000đ <br>2. Nhấn "Tiến hành thanh toán" <br>3. Xem tổng tiền ở trang checkout |
| **Kết quả mong đợi** | Tổng = 650.000đ |
| **Kết quả thực tế** | Tổng hiển thị = 500.000đ (sai – có vẻ bỏ qua 1 sản phẩm) |
| **Mức độ nghiêm trọng** | 🔴 Critical |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CHECKOUT_003 – Địa chỉ chứa ký tự đặc biệt được chấp nhận

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CHECKOUT_003 |
| **Tóm tắt** | Hệ thống chấp nhận địa chỉ giao hàng chỉ có ký tự đặc biệt, không có validation |
| **Module** | Checkout |
| **Test Case liên quan** | TC_CHECKOUT_008 |
| **Các bước tái hiện** | 1. Mở trang thanh toán <br>2. Nhập địa chỉ: `@#$%^&*()` <br>3. Chọn COD <br>4. Nhấn đặt hàng |
| **Kết quả mong đợi** | Lỗi: "Địa chỉ không hợp lệ" |
| **Kết quả thực tế** | Đơn hàng được tạo thành công với địa chỉ `@#$%^&*()` → dữ liệu rác trong hệ thống |
| **Mức độ nghiêm trọng** | 🟠 Major |
| **Độ ưu tiên** | Medium |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CHECKOUT_004 – Giỏ hàng không bị xoá sau khi đặt hàng thành công

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CHECKOUT_004 |
| **Tóm tắt** | Sau khi đặt hàng thành công, giỏ hàng vẫn còn hiển thị sản phẩm cũ |
| **Module** | Checkout |
| **Test Case liên quan** | TC_CHECKOUT_001 |
| **Các bước tái hiện** | 1. Thực hiện đặt hàng COD thành công <br>2. Xem trang xác nhận đơn hàng <br>3. Quay lại nhấn icon giỏ hàng |
| **Kết quả mong đợi** | Giỏ hàng trống sau khi đặt hàng thành công |
| **Kết quả thực tế** | Giỏ hàng vẫn hiển thị các sản phẩm đã đặt → có thể đặt lại đơn trùng |
| **Mức độ nghiêm trọng** | 🟠 Major |
| **Độ ưu tiên** | High |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_AUTH_004 – Không có thông báo sau khi nhấn "Quên mật khẩu"

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_AUTH_004 |
| **Tóm tắt** | Sau khi nhập email và nhấn gửi reset, trang không hiển thị bất kỳ thông báo nào |
| **Module** | Authentication |
| **Test Case liên quan** | TC_AUTH_010 |
| **Các bước tái hiện** | 1. Mở trang `/forgot-password` <br>2. Nhập email hợp lệ: `testuser@example.com` <br>3. Nhấn **"Gửi"** |
| **Kết quả mong đợi** | Thông báo: "Email đặt lại mật khẩu đã được gửi, vui lòng kiểm tra hộp thư" |
| **Kết quả thực tế** | Trang reload nhưng không hiển thị thông báo nào; người dùng không biết có thành công không |
| **Mức độ nghiêm trọng** | 🟡 Minor |
| **Độ ưu tiên** | Medium |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## BUG_CART_005 – Tìm kiếm phân biệt hoa/thường không nhất quán

| Trường | Nội Dung |
|--------|----------|
| **Bug ID** | BUG_CART_005 |
| **Tóm tắt** | Tìm kiếm "iphone" trả về kết quả nhưng "IPHONE" không trả về kết quả nào |
| **Module** | Product & Cart |
| **Test Case liên quan** | TC_CART_001 |
| **Các bước tái hiện** | 1. Tìm kiếm với từ khoá: `iphone 15` → có kết quả <br>2. Tìm kiếm với từ khoá: `IPHONE 15` → không có kết quả |
| **Kết quả mong đợi** | Cả 2 trường hợp đều trả về cùng kết quả (tìm kiếm case-insensitive) |
| **Kết quả thực tế** | Tìm kiếm phân biệt hoa thường → trải nghiệm người dùng kém |
| **Mức độ nghiêm trọng** | 🟡 Minor |
| **Độ ưu tiên** | Low |
| **Môi trường** | Chrome, Windows 10 |
| **Trạng thái** | Open |
| **Ngày phát hiện** | 23/03/2026 |

---

## Tổng Hợp Bug Report

| Bug ID | Module | Severity | Priority | Trạng Thái |
|--------|--------|----------|----------|-----------|
| BUG_AUTH_001 | Auth | 🔴 Critical | High | Open |
| BUG_AUTH_002 | Auth | 🔴 Critical | High | Open |
| BUG_AUTH_003 | Auth | 🟠 Major | High | Open |
| BUG_AUTH_004 | Auth | 🟡 Minor | Medium | Open |
| BUG_CART_001 | Cart | 🔴 Critical | High | Open |
| BUG_CART_002 | Cart | 🟠 Major | High | Open |
| BUG_CART_003 | Cart | 🟠 Major | Medium | Open |
| BUG_CART_004 | Cart | 🟠 Major | Medium | Open |
| BUG_CART_005 | Cart | 🟡 Minor | Low | Open |
| BUG_CHECKOUT_001 | Checkout | 🔴 Critical | High | Open |
| BUG_CHECKOUT_002 | Checkout | 🔴 Critical | High | Open |
| BUG_CHECKOUT_003 | Checkout | 🟠 Major | Medium | Open |
| BUG_CHECKOUT_004 | Checkout | 🟠 Major | High | Open |

**Tổng: 13 bugs | Critical: 5 | Major: 6 | Minor: 2**
