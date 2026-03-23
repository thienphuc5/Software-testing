# CA KIỂM THỬ – MODULE THANH TOÁN (CHECKOUT)
## Tổng số: 10 Test Case

---

### TC_CHECKOUT_001 – Thanh toán thành công với COD và địa chỉ hợp lệ

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_001 |
| **Tiêu đề** | Đặt hàng thành công với phương thức COD và địa chỉ đầy đủ |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có sản phẩm "Áo thun" × 1 (150.000đ) |
| **Các bước** | 1. Mở trang giỏ hàng <br>2. Nhấn **"Tiến hành thanh toán"** <br>3. Nhập địa chỉ: "123 Lê Lợi, Q.1, TP.HCM" <br>4. Nhập số điện thoại: "0901234567" <br>5. Chọn phương thức: **COD** <br>6. Nhấn **"Đặt hàng"** |
| **Kết quả mong đợi** | Đơn hàng được tạo thành công; hiển thị mã đơn hàng; email xác nhận được gửi; giỏ hàng trống |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R13, R14, R15 |

---

### TC_CHECKOUT_002 – Thanh toán thất bại khi không nhập địa chỉ giao hàng

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_002 |
| **Tiêu đề** | Đặt hàng khi để trống trường địa chỉ giao hàng |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có sản phẩm |
| **Các bước** | 1. Mở trang thanh toán `/checkout` <br>2. Để trống trường **Địa chỉ giao hàng** <br>3. Chọn phương thức: COD <br>4. Nhấn **"Đặt hàng"** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo lỗi: "Vui lòng nhập địa chỉ giao hàng"; không tạo đơn hàng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative / Validation |
| **Requirement** | R13 |

---

### TC_CHECKOUT_003 – Thanh toán với Visa giả lập thành công

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_003 |
| **Tiêu đề** | Đặt hàng thành công với phương thức thanh toán Visa giả lập |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có sản phẩm |
| **Các bước** | 1. Mở trang thanh toán <br>2. Nhập địa chỉ: "456 Nguyễn Trãi, Q.5, TP.HCM" <br>3. Chọn phương thức: **Visa** <br>4. Nhập số thẻ: `4111 1111 1111 1111` <br>5. Nhập Ngày hết hạn: `12/28`, CVV: `123` <br>6. Nhấn **"Đặt hàng"** |
| **Kết quả mong đợi** | Đơn hàng được tạo; hiển thị xác nhận thanh toán thành công; mã đơn hàng được hiển thị |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R14, R15 |

---

### TC_CHECKOUT_004 – Thanh toán Visa với số thẻ không hợp lệ

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_004 |
| **Tiêu đề** | Đặt hàng với số thẻ Visa sai định dạng |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có sản phẩm |
| **Các bước** | 1. Mở trang thanh toán <br>2. Nhập địa chỉ hợp lệ <br>3. Chọn phương thức: **Visa** <br>4. Nhập số thẻ: `1234 abcd` (không hợp lệ) <br>5. Nhấn **"Đặt hàng"** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi: "Số thẻ không hợp lệ"; không tạo đơn hàng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative / Validation |
| **Requirement** | R14 |

---

### TC_CHECKOUT_005 – Không chọn phương thức thanh toán

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_005 |
| **Tiêu đề** | Đặt hàng khi chưa chọn phương thức thanh toán |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có sản phẩm |
| **Các bước** | 1. Mở trang thanh toán <br>2. Nhập địa chỉ hợp lệ <br>3. Bỏ qua phần chọn phương thức thanh toán <br>4. Nhấn **"Đặt hàng"** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi: "Vui lòng chọn phương thức thanh toán"; không tạo đơn hàng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative / Validation |
| **Requirement** | R14 |

---

### TC_CHECKOUT_006 – Xem lịch sử đơn hàng sau khi đặt hàng

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_006 |
| **Tiêu đề** | Lịch sử đơn hàng hiển thị đúng sau khi đặt hàng thành công |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đặt hàng thành công ít nhất 1 đơn |
| **Các bước** | 1. Đăng nhập vào hệ thống <br>2. Vào menu **"Tài khoản"** → **"Lịch sử đơn hàng"** <br>3. Xem danh sách đơn hàng |
| **Kết quả mong đợi** | Hiển thị danh sách đơn hàng với: mã đơn, ngày đặt, tổng tiền, trạng thái; đơn hàng vừa đặt xuất hiện đầu danh sách |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R16 |

---

### TC_CHECKOUT_007 – Đặt hàng khi giỏ hàng trống

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_007 |
| **Tiêu đề** | Truy cập trang thanh toán khi giỏ hàng đang trống |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng trống (0 sản phẩm) |
| **Các bước** | 1. Truy cập trực tiếp URL `/checkout` khi giỏ hàng trống |
| **Kết quả mong đợi** | Hệ thống chuyển hướng về trang giỏ hàng HOẶC hiển thị thông báo "Giỏ hàng trống, không thể thanh toán" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Negative / Boundary |
| **Requirement** | R13, R15 |

---

### TC_CHECKOUT_008 – Địa chỉ giao hàng chỉ có ký tự đặc biệt

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_008 |
| **Tiêu đề** | Nhập địa chỉ giao hàng chỉ gồm ký tự đặc biệt |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có sản phẩm |
| **Các bước** | 1. Mở trang thanh toán <br>2. Nhập địa chỉ: `@#$%^&*()` <br>3. Chọn COD <br>4. Nhấn **"Đặt hàng"** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi validation: "Địa chỉ không hợp lệ"; không tạo đơn hàng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Negative / Validation |
| **Requirement** | R13 |

---

### TC_CHECKOUT_009 – Kiểm tra tổng tiền đơn hàng trước khi xác nhận

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_009 |
| **Tiêu đề** | Tổng tiền trong trang thanh toán khớp với giỏ hàng |
| **Module** | Checkout |
| **Điều kiện trước** | Giỏ hàng có: "Áo thun" × 2 (150.000đ) + "Bàn phím" × 1 (350.000đ) |
| **Các bước** | 1. Mở trang giỏ hàng – ghi nhớ tổng tiền (650.000đ) <br>2. Nhấn **"Tiến hành thanh toán"** <br>3. Kiểm tra tổng tiền trên trang thanh toán |
| **Kết quả mong đợi** | Tổng tiền hiển thị trên trang checkout = 650.000đ, khớp với giỏ hàng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R15 |

---

### TC_CHECKOUT_010 – Người dùng chưa đăng nhập cố truy cập trang thanh toán

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CHECKOUT_010 |
| **Tiêu đề** | Bảo mật – Chưa đăng nhập cố truy cập trang checkout |
| **Module** | Checkout |
| **Điều kiện trước** | Người dùng chưa đăng nhập |
| **Các bước** | 1. Mở trình duyệt <br>2. Truy cập trực tiếp URL `/checkout` |
| **Kết quả mong đợi** | Hệ thống chuyển hướng về trang đăng nhập; không cho phép truy cập trang thanh toán khi chưa xác thực |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Security / Negative |
| **Requirement** | R13, R15 |
