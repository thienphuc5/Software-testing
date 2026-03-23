# DANH SÁCH BUG – JIRA SOFTWARE
## Project: Student Management System (SMS) | Sprint 1
**Ngày lập:** 23/03/2026 | **Tổng số bug:** 10

---

## SMS-001 – [BUG] Đăng nhập thất bại với thông tin hợp lệ

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Không thể đăng nhập dù email và mật khẩu đúng |
| **Status** | ✅ Done |
| **Severity** | 🔴 Critical |
| **Priority** | Blocker |
| **Assignee** | dev-nam@sms.edu.vn |
| **Reporter** | qa-phuc@sms.edu.vn |
| **Environment** | Chrome 122 / Windows 10 |
| **Found In Build** | v1.0.0 |
| **Fix Version** | v1.0.1 |

**Steps to Reproduce:**
1. Mở trang `/login`
2. Nhập `admin@sms.edu.vn` / `Admin@12345`
3. Nhấn **Đăng nhập**

**Expected:** Dashboard hiển thị sau khi đăng nhập
**Actual:** Lỗi "Sai thông tin đăng nhập" mặc dù thông tin đúng

**Resolution:** Fixed – Bug do hàm `bcrypt.compare()` bị gọi với encoding sai (v1.0.1)

**Workflow:** `New → Open → In Progress → Fixed → QA Verify → Done`

---

## SMS-002 – [BUG] Thêm sinh viên thành công nhưng không lưu vào DB

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Dữ liệu sinh viên không được INSERT vào database sau khi form submit |
| **Status** | 🔴 Open |
| **Severity** | 🔴 Critical |
| **Priority** | Blocker |
| **Assignee** | dev-nam@sms.edu.vn |
| **Reporter** | qa-phuc@sms.edu.vn |
| **Environment** | Chrome 122 / Windows 10 |
| **Found In Build** | v1.0.0 |

**Steps to Reproduce:**
1. Đăng nhập Admin → Quản lý Sinh viên → Thêm mới
2. Điền đầy đủ thông tin hợp lệ
3. Nhấn **Lưu**

**Expected:** Sinh viên xuất hiện trong danh sách, record trong DB
**Actual:** Thông báo "Thêm thành công" nhưng danh sách không cập nhật

**Workflow:** `New → Open → In Progress` *(Chưa Fixed)*

---

## SMS-003 – [BUG] Tìm kiếm phân biệt hoa/thường

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Search không trả về kết quả khi nhập chữ thường |
| **Status** | ✅ Done |
| **Severity** | 🟡 Minor |
| **Priority** | Low |
| **Assignee** | dev-linh@sms.edu.vn |
| **Reporter** | qa-phuc@sms.edu.vn |
| **Environment** | Firefox 123 / Windows 11 |
| **Found In Build** | v1.0.0 |
| **Fix Version** | v1.0.1 |

**Resolution:** Fixed – Thêm `LOWER()` vào SQL query, trim whitespace phía client

**Workflow:** `New → Open → In Progress → Fixed → QA Verify → Done`

---

## SMS-004 – [BUG] Không validate email khi thêm sinh viên

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Form chấp nhận email không đúng định dạng |
| **Status** | 🟠 QA Verify |
| **Severity** | 🟠 Major |
| **Priority** | High |
| **Assignee** | dev-linh@sms.edu.vn |
| **Reporter** | qa-phuc@sms.edu.vn |
| **Environment** | Chrome 122 / Windows 10 |
| **Found In Build** | v1.0.0 |
| **Fix Version** | v1.0.1 |

**Workflow:** `New → Open → In Progress → Fixed → QA Verify` *(Đang retest)*

---

## SMS-005 – [BUG] Server crash khi xoá sinh viên có lịch học

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | HTTP 500 khi xoá sinh viên đang đăng ký khoá học |
| **Status** | 🔴 In Progress |
| **Severity** | 🔴 Critical |
| **Priority** | Blocker |
| **Assignee** | dev-nam@sms.edu.vn |
| **Reporter** | qa-phuc@sms.edu.vn |
| **Environment** | Chrome 122 / Windows 10 |
| **Found In Build** | v1.0.0 |

**Root Cause (phân tích):** Foreign key constraint chưa được xử lý → Exception không bắt → 500 error

**Workflow:** `New → Open → In Progress` *(Đang phân tích)*

---

## SMS-006 – [BUG] Phân quyền sai – User thường thấy chức năng Admin

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Tài khoản vai trò "Student" có thể nhìn thấy menu quản lý Admin |
| **Status** | 🔴 Open |
| **Severity** | 🔴 Critical |
| **Priority** | Blocker |
| **Assignee** | dev-nam@sms.edu.vn |
| **Reporter** | qa-phuc@sms.edu.vn |
| **Environment** | Chrome 122 / Windows 10 |
| **Found In Build** | v1.0.0 |

**Steps to Reproduce:**
1. Đăng nhập với tài khoản sinh viên thường: `student01@sms.edu.vn`
2. Quan sát thanh menu điều hướng

**Expected:** Chỉ thấy menu: "Xem thời khoá biểu", "Điểm số", "Thông tin cá nhân"
**Actual:** Hiển thị thêm: "Quản lý Sinh viên", "Quản lý Giảng viên", "Cài đặt hệ thống"

> ⚠️ **Đây là lỗ hổng bảo mật nghiêm trọng** – cần ưu tiên cao nhất

**Workflow:** `New → Open` *(Chờ phân công)*

---

## SMS-007 – [BUG] Không hiển thị thông báo lỗi khi đăng nhập thất bại

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Trang trắng thay vì thông báo lỗi khi sai thông tin đăng nhập |
| **Status** | ✅ Done |
| **Severity** | 🟠 Major |
| **Priority** | High |
| **Assignee** | dev-linh@sms.edu.vn |
| **Reporter** | qa-mai@sms.edu.vn |
| **Environment** | Edge 121 / Windows 10 |
| **Fix Version** | v1.0.1 |

**Workflow:** `New → Open → In Progress → Fixed → QA Verify → Done`

---

## SMS-008 – [BUG] Danh sách sinh viên không phân trang khi quá 100 bản ghi

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Trang "Danh sách sinh viên" load toàn bộ dữ liệu không phân trang, gây chậm |
| **Status** | 🟡 In Progress |
| **Severity** | 🟠 Major |
| **Priority** | Medium |
| **Assignee** | dev-linh@sms.edu.vn |
| **Reporter** | qa-mai@sms.edu.vn |
| **Environment** | Chrome 122 / Windows 10 |
| **Found In Build** | v1.0.0 |

**Steps to Reproduce:**
1. Import 150 bản ghi sinh viên vào DB
2. Truy cập trang `/students`
3. Quan sát thời gian load và UI

**Expected:** Phân trang (20 bản ghi/trang)
**Actual:** Toàn bộ 150 bản ghi load thành 1 trang, thời gian load > 8 giây

**Workflow:** `New → Open → In Progress` *(Đang develop pagination)*

---

## SMS-009 – [BUG] Ký tự đặc biệt trong tên sinh viên gây lỗi hiển thị

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Tên có dấu tiếng Việt bị hiển thị sai (dấu hỏi thay thế các ký tự) |
| **Status** | ✅ Done |
| **Severity** | 🟠 Major |
| **Priority** | High |
| **Assignee** | dev-linh@sms.edu.vn |
| **Reporter** | qa-phuc@sms.edu.vn |
| **Found In Build** | v1.0.0 |
| **Fix Version** | v1.0.1 |

**Expected:** "Nguyễn Văn An" hiển thị đúng
**Actual:** "Nguy??n V?n An" hiển thị sai dấu

**Resolution:** Fixed – Đổi charset DB từ `latin1` sang `utf8mb4`

**Workflow:** `New → Open → In Progress → Fixed → QA Verify → Done`

---

## SMS-010 – [BUG] Button "Cập nhật" bị ẩn trên màn hình nhỏ (responsive)

| Trường | Nội dung |
|--------|---------|
| **Issue Type** | 🐛 Bug |
| **Summary** | Nút "Cập nhật thông tin sinh viên" không hiển thị trên màn hình ≤ 768px |
| **Status** | ✅ Done |
| **Severity** | 🟡 Minor |
| **Priority** | Low |
| **Assignee** | dev-linh@sms.edu.vn |
| **Reporter** | qa-mai@sms.edu.vn |
| **Found In Build** | v1.0.0 |
| **Fix Version** | v1.0.1 |

**Resolution:** Fixed – CSS overflow hidden trên container button, thêm `overflow: visible`

**Workflow:** `New → Open → In Progress → Fixed → QA Verify → Done`

---

## Tổng Hợp Jira Bugs

| Jira ID | Summary | Severity | Priority | Status | Assignee |
|---------|---------|----------|----------|--------|---------|
| SMS-001 | Không đăng nhập dù đúng mật khẩu | 🔴 Critical | Blocker | ✅ Done | Dev Nam |
| SMS-002 | Thêm sinh viên không lưu DB | 🔴 Critical | Blocker | 🔴 Open | Dev Nam |
| SMS-003 | Tìm kiếm phân biệt hoa/thường | 🟡 Minor | Low | ✅ Done | Dev Linh |
| SMS-004 | Không validate email | 🟠 Major | High | 🟠 QA Verify | Dev Linh |
| SMS-005 | Server crash xoá sinh viên | 🔴 Critical | Blocker | 🟡 In Progress | Dev Nam |
| SMS-006 | Phân quyền sai – student thấy admin | 🔴 Critical | Blocker | 🔴 Open | Dev Nam |
| SMS-007 | Không hiển thị lỗi đăng nhập sai | 🟠 Major | High | ✅ Done | Dev Linh |
| SMS-008 | Không phân trang 100+ bản ghi | 🟠 Major | Medium | 🟡 In Progress | Dev Linh |
| SMS-009 | Tiếng Việt hiển thị sai dấu | 🟠 Major | High | ✅ Done | Dev Linh |
| SMS-010 | Button ẩn trên màn hình nhỏ | 🟡 Minor | Low | ✅ Done | Dev Linh |

**Phân bố Severity:** Critical: 4 | Major: 4 | Minor: 2
**Phân bố Status:** Done: 5 | Open: 2 | In Progress: 2 | QA Verify: 1
