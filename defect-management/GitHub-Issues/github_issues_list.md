# DANH SÁCH BUG – GITHUB ISSUES
## Student Management System (SMS) – Sprint 1
**Tổng số bug:** 5 | **Ngày tạo:** 23/03/2026

---

## Issue #1 – [BUG] Không đăng nhập được dù nhập đúng mật khẩu

**Labels:** `bug` `critical`
**Assignee:** developer-nam
**Milestone:** Sprint 1
**Status:** Closed ✅

```markdown
## 📋 Tóm Tắt
Người dùng không thể đăng nhập dù nhập đúng email và mật khẩu đã đăng ký.

## 🖥️ Môi Trường
- Hệ điều hành: Windows 10
- Trình duyệt: Chrome 122
- URL: https://sms.example.com/login
- Tài khoản test: admin@sms.edu.vn / Admin@12345

## 🔁 Các Bước Tái Hiện
1. Mở trang https://sms.example.com/login
2. Nhập Email: admin@sms.edu.vn
3. Nhập Mật khẩu: Admin@12345
4. Nhấn nút "Đăng nhập"

## ✅ Kết Quả Mong Đợi
Đăng nhập thành công, chuyển hướng về trang Dashboard

## ❌ Kết Quả Thực Tế
Trang hiển thị lỗi: "Sai thông tin đăng nhập" dù thông tin là chính xác.
Lỗi xảy ra nhất quán sau 3 lần thử.

## 🎚️ Severity: 🔴 Critical
## 🔺 Priority: Blocker
```

**Vòng đời bug:**
```
[Open] → [Assigned: Dev Nam] → [In Progress] → [Fixed v1.0.1] → [Retest: Pass] → [Closed]
```
**Root cause:** Hàm hash mật khẩu bị lỗi sau khi migration DB – encoding UTF-8 không nhất quán.

---

## Issue #2 – [BUG] Thêm sinh viên thành công nhưng không lưu vào database

**Labels:** `bug` `critical`
**Assignee:** developer-nam
**Milestone:** Sprint 1
**Status:** Open 🔴

```markdown
## 📋 Tóm Tắt
Sau khi điền form thêm sinh viên và nhấn "Lưu", hệ thống hiển thị thông báo 
thành công nhưng sinh viên không xuất hiện trong danh sách và không có trong DB.

## 🖥️ Môi Trường
- Hệ điều hành: Windows 10
- Trình duyệt: Chrome 122
- URL: https://sms.example.com/students/add

## 🔁 Các Bước Tái Hiện
1. Đăng nhập với tài khoản Admin
2. Vào menu "Quản lý Sinh viên" → "Thêm sinh viên"
3. Nhập: Tên: Nguyễn Văn A, MSSV: 20220001, Ngành: CNTT
4. Nhấn nút "Lưu"
5. Kiểm tra danh sách sinh viên

## ✅ Kết Quả Mong Đợi
Sinh viên được lưu vào DB và xuất hiện trong danh sách

## ❌ Kết Quả Thực Tế
Thông báo "Thêm sinh viên thành công" nhưng tải lại trang → không có dữ liệu.
Kiểm tra DB confirm: bảng students không có record mới.

## 🎚️ Severity: 🔴 Critical
## 🔺 Priority: Blocker
```

**Vòng đời bug:**
```
[Open] → [Assigned: Dev Nam] → [In Progress] → ❌ Chưa Fixed
```

---

## Issue #3 – [BUG] Tìm kiếm sinh viên phân biệt chữ hoa/thường

**Labels:** `bug` `minor` `ui`
**Assignee:** developer-linh
**Milestone:** Sprint 1
**Status:** Closed ✅

```markdown
## 📋 Tóm Tắt
Chức năng tìm kiếm phân biệt hoa/thường: tìm "nguyen" không ra kết quả, 
nhưng "Nguyen" trả về đúng.

## 🖥️ Môi Trường
- Hệ điều hành: Windows 11
- Trình duyệt: Firefox 123
- URL: https://sms.example.com/students/search

## 🔁 Các Bước Tái Hiện
1. Đăng nhập, vào trang Tìm kiếm sinh viên
2. Nhập từ khoá: "nguyen van a" (chữ thường)
3. Nhấn Enter
4. Thử lại với "Nguyen Van A" (đúng chữ hoa)

## ✅ Kết Quả Mong Đợi
Cả 2 trường hợp đều trả về sinh viên "Nguyễn Văn A"

## ❌ Kết Quả Thực Tế
"nguyen van a" → Không có kết quả
"Nguyen Van A" → Có kết quả đúng

## 🎚️ Severity: 🟡 Minor
## 🔺 Priority: Medium
```

**Vòng đời bug:**
```
[Open] → [Assigned: Dev Linh] → [Fixed: LOWER() SQL] → [Retest: Pass] → [Closed]
```

---

## Issue #4 – [BUG] Không validate định dạng email khi thêm sinh viên

**Labels:** `bug` `major` `security`
**Assignee:** developer-linh
**Milestone:** Sprint 1
**Status:** Fixed – Pending Retest 🟠

```markdown
## 📋 Tóm Tắt
Trường Email trong form thêm sinh viên không kiểm tra định dạng, 
cho phép nhập email không hợp lệ.

## 🖥️ Môi Trường
- Trình duyệt: Chrome 122, Windows 10
- URL: https://sms.example.com/students/add

## 🔁 Các Bước Tái Hiện
1. Vào form "Thêm sinh viên"
2. Nhập Email: "noatsign" (không có @)
3. Điền các trường khác hợp lệ
4. Nhấn "Lưu"

## ✅ Kết Quả Mong Đợi
Lỗi: "Email không đúng định dạng"

## ❌ Kết Quả Thực Tế
Form được submit thành công với email "noatsign"

## 🎚️ Severity: 🟠 Major
## 🔺 Priority: High
```

**Vòng đời bug:**
```
[Open] → [Assigned: Dev Linh] → [In Progress] → [Fixed] → [QA Verify – Pending]
```

---

## Issue #5 – [BUG] Crash (500 Error) khi xoá sinh viên đang có lịch học

**Labels:** `bug` `critical` `regression`
**Assignee:** developer-nam
**Milestone:** Sprint 1
**Status:** Open 🔴

```markdown
## 📋 Tóm Tắt
Khi xoá sinh viên có liên kết với lịch học/khoá học, hệ thống báo lỗi 
500 Internal Server Error thay vì cảnh báo người dùng.

## 🖥️ Môi Trường
- Trình duyệt: Chrome 122, Windows 10
- URL: https://sms.example.com/students

## 🔁 Các Bước Tái Hiện
1. Đăng nhập Admin
2. Vào Quản lý Sinh viên
3. Chọn sinh viên MSSV: 20220001 (đã đăng ký lịch học)
4. Nhấn nút "Xoá" → Xác nhận

## ✅ Kết Quả Mong Đợi
Hiển thị cảnh báo: "Không thể xoá – sinh viên đang có lịch học. 
Vui lòng huỷ đăng ký khoá học trước."

## ❌ Kết Quả Thực Tế
Trang crash: HTTP 500 Internal Server Error
Console log: "Foreign key constraint violation on table enrollments"

## 🎚️ Severity: 🔴 Critical
## 🔺 Priority: Blocker
```

**Vòng đời bug:**
```
[Open] → [Assigned: Dev Nam] → [In Progress] → ❌ Chưa Fixed
```

---

## Tổng Hợp GitHub Issues

| Issue # | Tiêu Đề Rút Gọn | Severity | Priority | Assignee | Status |
|---------|----------------|----------|----------|---------|--------|
| #1 | Không đăng nhập dù đúng mật khẩu | 🔴 Critical | Blocker | Dev Nam | Closed ✅ |
| #2 | Thêm sinh viên không lưu DB | 🔴 Critical | Blocker | Dev Nam | Open 🔴 |
| #3 | Tìm kiếm phân biệt hoa/thường | 🟡 Minor | Medium | Dev Linh | Closed ✅ |
| #4 | Không validate email | 🟠 Major | High | Dev Linh | Fixed 🟠 |
| #5 | Crash khi xoá sinh viên | 🔴 Critical | Blocker | Dev Nam | Open 🔴 |

**Tổng kết:** 5 bugs | Critical: 3 | Major: 1 | Minor: 1 | Closed: 2 | Open: 3
