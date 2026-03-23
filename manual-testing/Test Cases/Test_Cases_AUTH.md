# CA KIỂM THỬ – MODULE XÁC THỰC (AUTHENTICATION)
## Tổng số: 15 Test Case

---

### TC_AUTH_001 – Đăng ký tài khoản với email và mật khẩu hợp lệ

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_001 |
| **Tiêu đề** | Đăng ký tài khoản với email và mật khẩu hợp lệ |
| **Module** | Authentication |
| **Điều kiện trước** | Người dùng chưa có tài khoản; trình duyệt Chrome đang mở trang đăng ký |
| **Các bước** | 1. Mở trang `/register` <br>2. Nhập Email: `newuser@example.com` <br>3. Nhập Mật khẩu: `Test@12345` <br>4. Nhập Xác nhận mật khẩu: `Test@12345` <br>5. Nhấn nút **Đăng ký** |
| **Kết quả mong đợi** | Tài khoản được tạo thành công; hệ thống hiển thị thông báo "Đăng ký thành công" và chuyển hướng về trang đăng nhập hoặc trang chủ |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R1, R3 |

---

### TC_AUTH_002 – Đăng ký với email sai định dạng (thiếu @)

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_002 |
| **Tiêu đề** | Đăng ký với email sai định dạng – thiếu ký tự @ |
| **Module** | Authentication |
| **Điều kiện trước** | Trình duyệt Chrome đang mở trang đăng ký |
| **Các bước** | 1. Mở trang `/register` <br>2. Nhập Email: `newuserexample.com` <br>3. Nhập Mật khẩu: `Test@12345` <br>4. Nhập Xác nhận mật khẩu: `Test@12345` <br>5. Nhấn nút **Đăng ký** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo lỗi: "Email không đúng định dạng"; không tạo tài khoản |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative |
| **Requirement** | R2 |

---

### TC_AUTH_003 – Đăng ký với email hợp lệ nhưng mật khẩu ít hơn 8 ký tự

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_003 |
| **Tiêu đề** | Đăng ký với mật khẩu 7 ký tự (giá trị biên – dưới min) |
| **Module** | Authentication |
| **Điều kiện trước** | Trình duyệt Chrome đang mở trang đăng ký |
| **Các bước** | 1. Mở trang `/register` <br>2. Nhập Email: `user2@example.com` <br>3. Nhập Mật khẩu: `Test@12` (7 ký tự) <br>4. Nhập Xác nhận mật khẩu: `Test@12` <br>5. Nhấn nút **Đăng ký** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi: "Mật khẩu phải có ít nhất 8 ký tự"; không tạo tài khoản |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Boundary / Negative |
| **Requirement** | R3 |

---

### TC_AUTH_004 – Đăng ký với mật khẩu đúng 8 ký tự (giá trị biên – đúng min)

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_004 |
| **Tiêu đề** | Đăng ký với mật khẩu đúng 8 ký tự |
| **Module** | Authentication |
| **Điều kiện trước** | Trình duyệt Chrome đang mở trang đăng ký |
| **Các bước** | 1. Mở trang `/register` <br>2. Nhập Email: `user3@example.com` <br>3. Nhập Mật khẩu: `Test@123` (8 ký tự) <br>4. Nhập Xác nhận mật khẩu: `Test@123` <br>5. Nhấn nút **Đăng ký** |
| **Kết quả mong đợi** | Tài khoản được tạo thành công; hiển thị thông báo "Đăng ký thành công" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Boundary / Positive |
| **Requirement** | R3 |

---

### TC_AUTH_005 – Đăng ký với email đã tồn tại trong hệ thống

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_005 |
| **Tiêu đề** | Đăng ký với email đã được đăng ký trước đó |
| **Module** | Authentication |
| **Điều kiện trước** | Tài khoản `existing@example.com` đã tồn tại trong hệ thống |
| **Các bước** | 1. Mở trang `/register` <br>2. Nhập Email: `existing@example.com` <br>3. Nhập Mật khẩu: `Test@12345` <br>4. Nhập Xác nhận mật khẩu: `Test@12345` <br>5. Nhấn nút **Đăng ký** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi: "Email này đã được sử dụng"; không tạo tài khoản trùng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative |
| **Requirement** | R1, R2 |

---

### TC_AUTH_006 – Đăng nhập thành công với thông tin hợp lệ

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_006 |
| **Tiêu đề** | Đăng nhập thành công với email và mật khẩu hợp lệ |
| **Module** | Authentication |
| **Điều kiện trước** | Tài khoản `testuser@example.com` / `Test@12345` đã tồn tại |
| **Các bước** | 1. Mở trang `/login` <br>2. Nhập Email: `testuser@example.com` <br>3. Nhập Mật khẩu: `Test@12345` <br>4. Nhấn nút **Đăng nhập** |
| **Kết quả mong đợi** | Đăng nhập thành công; chuyển hướng về trang chủ; hiển thị tên người dùng trên thanh điều hướng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R4 |

---

### TC_AUTH_007 – Đăng nhập thất bại khi sai mật khẩu

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_007 |
| **Tiêu đề** | Đăng nhập thất bại khi nhập sai mật khẩu |
| **Module** | Authentication |
| **Điều kiện trước** | Tài khoản `testuser@example.com` đã tồn tại |
| **Các bước** | 1. Mở trang `/login` <br>2. Nhập Email: `testuser@example.com` <br>3. Nhập Mật khẩu: `WrongPass99` <br>4. Nhấn nút **Đăng nhập** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo lỗi: "Email hoặc mật khẩu không đúng"; không cho phép đăng nhập |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative |
| **Requirement** | R5 |

---

### TC_AUTH_008 – Đăng nhập với email không tồn tại

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_008 |
| **Tiêu đề** | Đăng nhập với email chưa được đăng ký |
| **Module** | Authentication |
| **Điều kiện trước** | Email `notexist@example.com` chưa có trong hệ thống |
| **Các bước** | 1. Mở trang `/login` <br>2. Nhập Email: `notexist@example.com` <br>3. Nhập Mật khẩu: `Test@12345` <br>4. Nhấn nút **Đăng nhập** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi: "Email hoặc mật khẩu không đúng"; không tiết lộ email có tồn tại hay không |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Negative / Security |
| **Requirement** | R5 |

---

### TC_AUTH_009 – Đăng nhập với hai trường bỏ trống

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_009 |
| **Tiêu đề** | Đăng nhập khi để trống cả email và mật khẩu |
| **Module** | Authentication |
| **Điều kiện trước** | Trình duyệt đang mở trang `/login` |
| **Các bước** | 1. Mở trang `/login` <br>2. Để trống trường Email <br>3. Để trống trường Mật khẩu <br>4. Nhấn nút **Đăng nhập** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo validation: "Vui lòng nhập email" và "Vui lòng nhập mật khẩu" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative / Validation |
| **Requirement** | R4, R5 |

---

### TC_AUTH_010 – Chức năng "Quên mật khẩu" gửi email đặt lại

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_010 |
| **Tiêu đề** | Quên mật khẩu – Gửi email đặt lại cho email đã đăng ký |
| **Module** | Authentication |
| **Điều kiện trước** | Tài khoản `testuser@example.com` đã tồn tại |
| **Các bước** | 1. Mở trang `/login` <br>2. Nhấn liên kết **"Quên mật khẩu?"** <br>3. Nhập email: `testuser@example.com` <br>4. Nhấn **"Gửi email đặt lại"** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo: "Email đặt lại mật khẩu đã được gửi"; email reset được gửi đến hộp thư |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R6 |

---

### TC_AUTH_011 – Quên mật khẩu với email không tồn tại

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_011 |
| **Tiêu đề** | Quên mật khẩu – Nhập email chưa đăng ký |
| **Module** | Authentication |
| **Điều kiện trước** | `nouser@example.com` không có trong hệ thống |
| **Các bước** | 1. Mở trang `/forgot-password` <br>2. Nhập email: `nouser@example.com` <br>3. Nhấn **"Gửi email đặt lại"** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo tương tự như khi email tồn tại (bảo mật – không tiết lộ thông tin) HOẶC hiển thị lỗi "Email không tìm thấy" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Negative / Security |
| **Requirement** | R6 |

---

### TC_AUTH_012 – Đăng xuất thành công

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_012 |
| **Tiêu đề** | Đăng xuất khỏi hệ thống thành công |
| **Module** | Authentication |
| **Điều kiện trước** | Người dùng đã đăng nhập với `testuser@example.com` |
| **Các bước** | 1. Nhấn vào tên người dùng góc trên phải <br>2. Chọn **"Đăng xuất"** từ menu dropdown <br>3. Xác nhận đăng xuất (nếu có popup) |
| **Kết quả mong đợi** | Phiên đăng nhập kết thúc; chuyển hướng về trang đăng nhập; không thể truy cập trang cần xác thực |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R4 |

---

### TC_AUTH_013 – Kiểm tra SQL Injection trong form đăng nhập

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_013 |
| **Tiêu đề** | Bảo mật – Thử SQL Injection vào trường email |
| **Module** | Authentication |
| **Điều kiện trước** | Trình duyệt đang mở trang `/login` |
| **Các bước** | 1. Mở trang `/login` <br>2. Nhập Email: `' OR '1'='1` <br>3. Nhập Mật khẩu: `anypassword` <br>4. Nhấn **Đăng nhập** |
| **Kết quả mong đợi** | Hệ thống từ chối xử lý; hiển thị thông báo lỗi đăng nhập thông thường; không bị bypass xác thực |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Security / Negative |
| **Requirement** | R4, R5 |

---

### TC_AUTH_014 – Đăng ký bỏ trống toàn bộ các trường

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_014 |
| **Tiêu đề** | Đăng ký khi để trống tất cả các trường bắt buộc |
| **Module** | Authentication |
| **Điều kiện trước** | Trình duyệt đang mở trang `/register` |
| **Các bước** | 1. Mở trang `/register` <br>2. Không nhập gì vào bất kỳ trường nào <br>3. Nhấn nút **Đăng ký** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo validation cho tất cả các trường còn trống; không tạo tài khoản |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative / Validation |
| **Requirement** | R1, R3 |

---

### TC_AUTH_015 – Đăng ký mật khẩu không khớp với xác nhận mật khẩu

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_AUTH_015 |
| **Tiêu đề** | Đăng ký khi mật khẩu và xác nhận mật khẩu không khớp |
| **Module** | Authentication |
| **Điều kiện trước** | Trình duyệt đang mở trang `/register` |
| **Các bước** | 1. Mở trang `/register` <br>2. Nhập Email: `user5@example.com` <br>3. Nhập Mật khẩu: `Test@12345` <br>4. Nhập Xác nhận mật khẩu: `Test@99999` <br>5. Nhấn nút **Đăng ký** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi: "Mật khẩu không khớp"; không tạo tài khoản |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Negative / Validation |
| **Requirement** | R3 |
