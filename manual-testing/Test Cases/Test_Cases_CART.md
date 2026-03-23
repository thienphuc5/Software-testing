# CA KIỂM THỬ – MODULE SẢN PHẨM & GIỎ HÀNG (PRODUCT & CART)
## Tổng số: 20 Test Case

---

### TC_CART_001 – Tìm kiếm sản phẩm theo từ khoá đúng

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_001 |
| **Tiêu đề** | Tìm kiếm sản phẩm với từ khoá hợp lệ |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đã đăng nhập; hệ thống có sản phẩm "iPhone 15" |
| **Các bước** | 1. Mở trang chủ <br>2. Nhập từ khoá `iPhone 15` vào ô tìm kiếm <br>3. Nhấn **Enter** hoặc nút **Tìm kiếm** |
| **Kết quả mong đợi** | Danh sách kết quả hiển thị sản phẩm có tên chứa "iPhone 15"; số lượng kết quả hiển thị đúng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R7 |

---

### TC_CART_002 – Tìm kiếm sản phẩm không tồn tại

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_002 |
| **Tiêu đề** | Tìm kiếm với từ khoá không khớp bất kỳ sản phẩm nào |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đã đăng nhập |
| **Các bước** | 1. Mở trang chủ <br>2. Nhập từ khoá `xyzabc12345xyz` vào ô tìm kiếm <br>3. Nhấn **Enter** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo: "Không tìm thấy sản phẩm phù hợp" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Negative |
| **Requirement** | R7 |

---

### TC_CART_003 – Tìm kiếm với ô trống (không nhập từ khoá)

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_003 |
| **Tiêu đề** | Tìm kiếm khi để trống ô tìm kiếm |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đang ở trang chủ |
| **Các bước** | 1. Mở trang chủ <br>2. Để trống ô tìm kiếm <br>3. Nhấn **Enter** hoặc nút **Tìm kiếm** |
| **Kết quả mong đợi** | Hệ thống hiển thị tất cả sản phẩm HOẶC thông báo "Vui lòng nhập từ khoá"; không bị lỗi |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Low |
| **Loại test** | Boundary / Negative |
| **Requirement** | R7 |

---

### TC_CART_004 – Lọc sản phẩm theo khoảng giá hợp lệ

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_004 |
| **Tiêu đề** | Lọc sản phẩm theo khoảng giá từ 100.000đ đến 500.000đ |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đang ở trang danh sách sản phẩm |
| **Các bước** | 1. Mở trang danh sách sản phẩm <br>2. Chọn bộ lọc giá <br>3. Nhập giá thấp: `100000` <br>4. Nhập giá cao: `500000` <br>5. Nhấn **Áp dụng lọc** |
| **Kết quả mong đợi** | Chỉ hiển thị sản phẩm có giá từ 100.000đ đến 500.000đ; sản phẩm ngoài khoảng không hiển thị |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R8 |

---

### TC_CART_005 – Lọc sản phẩm với giá min lớn hơn giá max

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_005 |
| **Tiêu đề** | Lọc theo giá khi min > max (dữ liệu không hợp lệ) |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đang ở trang danh sách sản phẩm |
| **Các bước** | 1. Mở trang danh sách sản phẩm <br>2. Nhập giá thấp: `900000` <br>3. Nhập giá cao: `100000` <br>4. Nhấn **Áp dụng lọc** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo lỗi: "Giá tối thiểu không được lớn hơn giá tối đa" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Negative / Validation |
| **Requirement** | R8 |

---

### TC_CART_006 – Lọc theo danh mục sản phẩm

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_006 |
| **Tiêu đề** | Lọc sản phẩm theo danh mục "Điện tử" |
| **Module** | Product & Cart |
| **Điều kiện trước** | Hệ thống có danh mục "Điện tử" với ít nhất 1 sản phẩm |
| **Các bước** | 1. Mở trang danh sách sản phẩm <br>2. Chọn danh mục **"Điện tử"** từ menu lọc <br>3. Xem kết quả |
| **Kết quả mong đợi** | Chỉ hiển thị sản phẩm thuộc danh mục "Điện tử" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Positive |
| **Requirement** | R8 |

---

### TC_CART_007 – Xem chi tiết sản phẩm

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_007 |
| **Tiêu đề** | Xem trang chi tiết sản phẩm |
| **Module** | Product & Cart |
| **Điều kiện trước** | Tồn tại sản phẩm "iPhone 15" trong hệ thống |
| **Các bước** | 1. Mở trang danh sách sản phẩm <br>2. Nhấn vào sản phẩm "iPhone 15" |
| **Kết quả mong đợi** | Trang chi tiết hiển thị: tên SP, hình ảnh, giá, mô tả, số lượng tồn kho, nút "Thêm vào giỏ" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R9 |

---

### TC_CART_008 – Thêm sản phẩm vào giỏ hàng

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_008 |
| **Tiêu đề** | Thêm sản phẩm vào giỏ hàng thành công |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đã đăng nhập; đang xem trang chi tiết sản phẩm "Áo thun" giá 150.000đ |
| **Các bước** | 1. Mở trang chi tiết sản phẩm "Áo thun" <br>2. Chọn số lượng: 1 <br>3. Nhấn nút **"Thêm vào giỏ hàng"** |
| **Kết quả mong đợi** | Sản phẩm được thêm vào giỏ; biểu tượng giỏ hàng cập nhật số lượng; thông báo "Thêm vào giỏ thành công" |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R10 |

---

### TC_CART_009 – Thêm sản phẩm với số lượng = 0

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_009 |
| **Tiêu đề** | Thêm vào giỏ khi số lượng chọn bằng 0 |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đã đăng nhập; đang xem trang chi tiết sản phẩm |
| **Các bước** | 1. Mở trang chi tiết một sản phẩm <br>2. Chỉnh số lượng về 0 <br>3. Nhấn nút **"Thêm vào giỏ hàng"** |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi: "Số lượng phải lớn hơn 0"; không thêm vào giỏ |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Boundary / Negative |
| **Requirement** | R10 |

---

### TC_CART_010 – Thêm sản phẩm với số lượng vượt tồn kho

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_010 |
| **Tiêu đề** | Thêm vào giỏ số lượng vượt quá số lượng tồn kho |
| **Module** | Product & Cart |
| **Điều kiện trước** | Sản phẩm "Bàn phím" có tồn kho = 5 |
| **Các bước** | 1. Mở trang chi tiết sản phẩm "Bàn phím" <br>2. Nhập số lượng: 10 <br>3. Nhấn **"Thêm vào giỏ hàng"** |
| **Kết quả mong đợi** | Hệ thống hiển thị thông báo: "Số lượng vượt quá tồn kho (còn 5)"; không thêm quá giới hạn |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Boundary / Negative |
| **Requirement** | R10 |

---

### TC_CART_011 – Cập nhật số lượng sản phẩm trong giỏ hàng (tăng)

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_011 |
| **Tiêu đề** | Tăng số lượng sản phẩm trong giỏ hàng |
| **Module** | Product & Cart |
| **Điều kiện trước** | Giỏ hàng có sản phẩm "Áo thun" với số lượng = 1 |
| **Các bước** | 1. Mở trang giỏ hàng `/cart` <br>2. Tìm dòng sản phẩm "Áo thun" <br>3. Tăng số lượng lên 3 (nhấn nút + hoặc nhập số) <br>4. Xác nhận cập nhật |
| **Kết quả mong đợi** | Số lượng cập nhật thành 3; tổng tiền được tính lại đúng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R11 |

---

### TC_CART_012 – Cập nhật số lượng về 1 (giá trị biên tối thiểu)

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_012 |
| **Tiêu đề** | Cập nhật số lượng về đúng 1 (giá trị biên min) |
| **Module** | Product & Cart |
| **Điều kiện trước** | Giỏ hàng có sản phẩm với số lượng = 3 |
| **Các bước** | 1. Mở trang giỏ hàng <br>2. Giảm số lượng sản phẩm xuống 1 <br>3. Xác nhận cập nhật |
| **Kết quả mong đợi** | Số lượng cập nhật thành 1; tổng tiền được tính lại đúng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Boundary |
| **Requirement** | R11 |

---

### TC_CART_013 – Cập nhật số lượng về giá trị âm

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_013 |
| **Tiêu đề** | Cập nhật số lượng thành giá trị âm trong giỏ hàng |
| **Module** | Product & Cart |
| **Điều kiện trước** | Giỏ hàng có ít nhất 1 sản phẩm |
| **Các bước** | 1. Mở trang giỏ hàng <br>2. Nhập số lượng: `-1` trực tiếp vào ô số lượng <br>3. Nhấn cập nhật |
| **Kết quả mong đợi** | Hệ thống hiển thị lỗi validation; không cho phép nhập giá trị âm |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Boundary / Negative / Validation |
| **Requirement** | R11 |

---

### TC_CART_014 – Xoá một sản phẩm khỏi giỏ hàng

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_014 |
| **Tiêu đề** | Xoá một sản phẩm cụ thể khỏi giỏ hàng |
| **Module** | Product & Cart |
| **Điều kiện trước** | Giỏ hàng có 2 sản phẩm: "Áo thun" và "Bàn phím" |
| **Các bước** | 1. Mở trang giỏ hàng <br>2. Nhấn nút **Xoá** (icon thùng rác) tại dòng sản phẩm "Áo thun" <br>3. Xác nhận xoá |
| **Kết quả mong đợi** | "Áo thun" bị xoá khỏi giỏ; "Bàn phím" vẫn còn; tổng tiền được cập nhật đúng |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R12 |

---

### TC_CART_015 – Xoá toàn bộ sản phẩm khỏi giỏ hàng

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_015 |
| **Tiêu đề** | Xoá tất cả sản phẩm trong giỏ hàng |
| **Module** | Product & Cart |
| **Điều kiện trước** | Giỏ hàng có ít nhất 1 sản phẩm |
| **Các bước** | 1. Mở trang giỏ hàng <br>2. Xoá từng sản phẩm hoặc nhấn **"Xoá tất cả"** <br>3. Xác nhận |
| **Kết quả mong đợi** | Giỏ hàng trống; hiển thị thông báo "Giỏ hàng của bạn đang trống"; tổng tiền = 0 |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Positive |
| **Requirement** | R12 |

---

### TC_CART_016 – Tìm kiếm với ký tự đặc biệt (XSS cơ bản)

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_016 |
| **Tiêu đề** | Bảo mật – Nhập script tag vào ô tìm kiếm |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đang ở trang danh sách sản phẩm |
| **Các bước** | 1. Nhập vào ô tìm kiếm: `<script>alert('XSS')</script>` <br>2. Nhấn **Enter** |
| **Kết quả mong đợi** | Hệ thống không thực thi script; không hiển thị alert; chỉ tìm kiếm bình thường hoặc hiển thị không có kết quả |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Security / Negative |
| **Requirement** | R7 |

---

### TC_CART_017 – Kiểm tra tổng tiền giỏ hàng khi có nhiều sản phẩm

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_017 |
| **Tiêu đề** | Tổng tiền giỏ hàng tính đúng khi có nhiều loại sản phẩm |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đã đăng nhập |
| **Các bước** | 1. Thêm "Áo thun" (150.000đ × 2) vào giỏ <br>2. Thêm "Bàn phím" (350.000đ × 1) vào giỏ <br>3. Mở trang giỏ hàng <br>4. Kiểm tra tổng tiền |
| **Kết quả mong đợi** | Tổng = 150.000 × 2 + 350.000 × 1 = 650.000đ |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | High |
| **Loại test** | Positive |
| **Requirement** | R10, R11 |

---

### TC_CART_018 – Thêm cùng một sản phẩm nhiều lần vào giỏ

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_018 |
| **Tiêu đề** | Thêm 2 lần cùng sản phẩm – kiểm tra hợp nhất giỏ hàng |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có sản phẩm "Chuột" × 1 |
| **Các bước** | 1. Mở trang chi tiết sản phẩm "Chuột" <br>2. Nhấn **"Thêm vào giỏ"** lần 2 |
| **Kết quả mong đợi** | Giỏ hàng cập nhật số lượng "Chuột" thành 2 (hợp nhất), KHÔNG tạo 2 dòng riêng biệt |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Positive |
| **Requirement** | R10, R11 |

---

### TC_CART_019 – Giỏ hàng vẫn lưu sau khi đăng xuất và đăng nhập lại

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_019 |
| **Tiêu đề** | Giỏ hàng được lưu khi đăng xuất và đăng nhập lại |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đã đăng nhập; giỏ hàng có 2 sản phẩm |
| **Các bước** | 1. Đăng xuất khỏi hệ thống <br>2. Đăng nhập lại với cùng tài khoản <br>3. Mở trang giỏ hàng |
| **Kết quả mong đợi** | Giỏ hàng vẫn còn 2 sản phẩm như trước khi đăng xuất |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Medium |
| **Loại test** | Positive |
| **Requirement** | R10 |

---

### TC_CART_020 – Lọc giá với giá trị biên (giá min = 0)

| Trường | Nội Dung |
|--------|----------|
| **TC_ID** | TC_CART_020 |
| **Tiêu đề** | Lọc sản phẩm với giá min = 0 (giá trị biên) |
| **Module** | Product & Cart |
| **Điều kiện trước** | Người dùng đang ở trang danh sách sản phẩm |
| **Các bước** | 1. Mở bộ lọc giá <br>2. Nhập giá tối thiểu: `0` <br>3. Nhập giá tối đa: `200000` <br>4. Nhấn **Áp dụng** |
| **Kết quả mong đợi** | Hiển thị tất cả sản phẩm có giá từ 0 đến 200.000đ; không có lỗi |
| **Kết quả thực tế** | *(Điền sau khi thực thi)* |
| **Trạng thái** | Pass / Fail |
| **Độ ưu tiên** | Low |
| **Loại test** | Boundary |
| **Requirement** | R8 |
