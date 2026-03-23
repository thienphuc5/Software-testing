# BÁO CÁO QUẢN LÝ LỖI PHẦN MỀM
## Defect Management Report – Student Management System (SMS)
**Nhóm:** ABC | **Ngày lập:** 23/03/2026 | **Sprint:** Sprint 1

---

## 1. Giới Thiệu

Báo cáo này tổng hợp toàn bộ quy trình quản lý lỗi (Defect Management) thực hiện trong Sprint 1 của dự án **Student Management System (SMS)** – một hệ thống web quản lý sinh viên với các chức năng: Đăng nhập, CRUD sinh viên, Tìm kiếm, Phân quyền.

Nhóm sử dụng hai công cụ song song:
- **GitHub Issues** – quản lý bug mức đơn giản / open-source
- **Jira Software** – mô phỏng quy trình doanh nghiệp chuyên nghiệp

---

## 2. Danh Sách Bug Tổng Hợp

### 2.1 GitHub Issues (5 bugs)

| # | Tiêu Đề | Severity | Priority | Status |
|---|---------|----------|----------|--------|
| #1 | Không đăng nhập dù đúng mật khẩu | 🔴 Critical | Blocker | ✅ Closed |
| #2 | Thêm sinh viên không lưu DB | 🔴 Critical | Blocker | 🔴 Open |
| #3 | Tìm kiếm phân biệt hoa/thường | 🟡 Minor | Medium | ✅ Closed |
| #4 | Không validate email | 🟠 Major | High | 🟠 Fixed |
| #5 | Crash khi xoá sinh viên có lịch học | 🔴 Critical | Blocker | 🔴 Open |

### 2.2 Jira (10 bugs)

| Jira ID | Tiêu Đề Rút Gọn | Severity | Status |
|---------|----------------|----------|--------|
| SMS-001 | Không đăng nhập dù đúng thông tin | 🔴 Critical | ✅ Done |
| SMS-002 | Thêm sinh viên không lưu DB | 🔴 Critical | 🔴 Open |
| SMS-003 | Search case-sensitive | 🟡 Minor | ✅ Done |
| SMS-004 | Không validate email | 🟠 Major | 🟠 QA Verify |
| SMS-005 | Crash xoá sinh viên | 🔴 Critical | 🟡 In Progress |
| SMS-006 | Phân quyền sai (Student thấy Admin) | 🔴 Critical | 🔴 Open |
| SMS-007 | Không hiển thị lỗi đăng nhập sai | 🟠 Major | ✅ Done |
| SMS-008 | Không phân trang 100+ bản ghi | 🟠 Major | 🟡 In Progress |
| SMS-009 | Tiếng Việt hiển thị sai dấu | 🟠 Major | ✅ Done |
| SMS-010 | Button ẩn trên màn hình nhỏ | 🟡 Minor | ✅ Done |

---

## 3. Phân Tích 2 Bug Nghiêm Trọng Nhất

### 🐛 Bug Nghiêm Trọng #1: SMS-006 / Issue #N/A
### "Phân quyền sai – Student thấy chức năng Admin"

#### Mô Tả Chi Tiết:
Đây là **lỗ hổng bảo mật nghiêm trọng nhất** trong Sprint 1. Một tài khoản sinh viên thông thường có thể nhìn thấy – và truy cập – các chức năng quản trị hệ thống dành riêng cho Admin.

#### Phân Tích Tác Động:
| Khía Cạnh | Mức Độ Ảnh Hưởng |
|-----------|-----------------|
| **Tính bảo mật** | 🔴 Cực kỳ nghiêm trọng – dữ liệu toàn bộ sinh viên có thể bị sửa/xoá |
| **Tính toàn vẹn dữ liệu** | 🔴 Cao – sinh viên có thể thay đổi điểm số, thông tin |
| **Trải nghiệm người dùng** | 🟠 Trung bình – UI hiển thị menu không phù hợp |
| **Tuân thủ quy định** | 🔴 Cao – vi phạm nguyên tắc Least Privilege |

#### Root Cause (Nguyên Nhân Gốc):
```
// Code lỗi (pseudocode)
if (user.isLoggedIn) {
    showAdminMenu();  // Không kiểm tra role!
}

// Code đúng
if (user.isLoggedIn && user.role === 'ADMIN') {
    showAdminMenu();
}
```
→ Middleware kiểm tra quyền chỉ áp dụng ở API layer nhưng **bị bỏ qua ở Frontend rendering**.

#### Hướng Xử Lý:
1. Thêm role-based rendering ở frontend
2. Bổ sung middleware `requireAdmin()` cho tất cả routes Admin
3. Kiểm tra phân quyền cả ở Frontend (UI ẩn) lẫn Backend (API từ chối)
4. Regression test toàn bộ các endpoint

---

### 🐛 Bug Nghiêm Trọng #2: SMS-002 / GitHub Issue #2
### "Thêm sinh viên thành công nhưng không lưu vào database"

#### Mô Tả Chi Tiết:
Hệ thống hiển thị thông báo thành công **giả** – dữ liệu không được persisted vào database. Đây là lỗi dữ liệu (data integrity) ảnh hưởng trực tiếp đến nghiệp vụ cốt lõi.

#### Phân Tích Tác Động:
| Khía Cạnh | Mức Độ Ảnh Hưởng |
|-----------|-----------------|
| **Chức năng chính** | 🔴 Cực kỳ nghiêm trọng – CRUD không hoạt động |
| **Tin cậy dữ liệu** | 🔴 Cao – người dùng tin rằng đã lưu nhưng thực ra không |
| **Nghiệp vụ** | 🔴 Cao – không thể vận hành hệ thống |
| **Khó phát hiện** | 🟠 Cao – thông báo "thành công" gây misleading |

#### Root Cause (Nguyên Nhân Gốc):
```javascript
// Code lỗi
async function addStudent(data) {
    const response = await fetch('/api/students', {
        method: 'POST',
        body: JSON.stringify(data)
    });
    showSuccess("Thêm thành công!");  // Gọi TRƯỚC khi check response!
    // Thiếu: if (!response.ok) throw new Error(...)
}

// Code đúng
async function addStudent(data) {
    const response = await fetch('/api/students', { ... });
    if (!response.ok) {
        showError("Lỗi khi lưu dữ liệu!");
        return;
    }
    showSuccess("Thêm thành công!");
}
```
→ Frontend gọi `showSuccess()` mà **không chờ xác nhận từ API**, trong khi API thực tế đang thất bại do transaction bị rollback.

#### Hướng Xử Lý:
1. Luôn kiểm tra `response.ok` trước khi hiển thị thông báo
2. Thêm error handling toàn diện cho mọi API call
3. Log lỗi phía server để dễ debug
4. Thêm test case kiểm tra DB trực tiếp sau khi thêm

---

## 4. So Sánh GitHub Issues vs Jira

| Tiêu Chí | GitHub Issues | Jira Software |
|----------|--------------|--------------|
| **Dễ cài đặt** | ⭐⭐⭐⭐⭐ Không cần setup | ⭐⭐⭐ Cần cấu hình project |
| **Dễ sử dụng hàng ngày** | ⭐⭐⭐⭐⭐ Giao diện đơn giản | ⭐⭐⭐ Cần thời gian làm quen |
| **Workflow tùy chỉnh** | ⭐⭐ Chỉ có Open/Closed | ⭐⭐⭐⭐⭐ Tùy chỉnh hoàn toàn |
| **Báo cáo & Dashboard** | ⭐⭐ Hạn chế | ⭐⭐⭐⭐⭐ Rất mạnh |
| **Tích hợp CI/CD** | ⭐⭐⭐⭐⭐ Tích hợp GitHub Actions | ⭐⭐⭐⭐ Tích hợp nhiều tool |
| **Phù hợp doanh nghiệp** | ⭐⭐⭐ Dự án nhỏ/OSS | ⭐⭐⭐⭐⭐ Tiêu chuẩn ngành |
| **Quản lý Sprint/Agile** | ⭐⭐ Hỗ trợ cơ bản (Projects) | ⭐⭐⭐⭐⭐ Agile đầy đủ |
| **Chi phí** | ✅ Miễn phí | 🟡 Miễn phí ≤10 người |
| **Custom Fields** | ❌ Không có | ✅ Đầy đủ |
| **Severity/Priority field** | ❌ Chỉ qua Label | ✅ Custom field riêng |
| **Bug Life Cycle tracking** | ⭐⭐ Thủ công | ⭐⭐⭐⭐⭐ Tự động + lịch sử |
| **File đính kèm** | ✅ Cơ bản | ✅ Đầy đủ |
| **Tích hợp email/Slack** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |

### Khi Nào Dùng GitHub Issues?
- Dự án mã nguồn mở (OSS)
- Nhóm nhỏ (< 5 người), ít bug
- Team đã dùng GitHub cho code → tiện quản lý cùng chỗ
- Muốn liên kết bug với commit/PR cụ thể dễ dàng

### Khi Nào Dùng Jira?
- Dự án doanh nghiệp quy mô lớn
- Cần workflow phức tạp (nhiều trạng thái, nhiều vai trò)
- Cần báo cáo, dashboard, burn-down chart
- QA team cần quản lý test plan kết hợp bug tracking

---

## 5. Nhận Xét Quy Trình Defect Management

### 5.1 Điểm Mạnh Đã Thực Hiện Được
- ✅ Bug được ghi nhận nhanh chóng sau khi phát hiện (< 30 phút)
- ✅ Mỗi bug có đầy đủ: steps to reproduce, expected, actual
- ✅ Phân loại Severity và Priority rõ ràng
- ✅ Vòng đời bug được theo dõi minh bạch
- ✅ Retest được thực hiện trước khi close bug

### 5.2 Điểm Cần Cải Thiện
- ⚠️ Một số bug thiếu screenshot minh chứng (cần có ảnh)
- ⚠️ Thời gian sửa bug Critical quá lâu (> 2 ngày)
- ⚠️ Chưa có quy trình escalation khi bug Critical quá hạn
- ⚠️ Root cause analysis chưa được ghi chú đầy đủ cho mọi bug

### 5.3 Bài Học Rút Ra
1. **Thông tin đủ = Bug được sửa nhanh**: Bug có steps to reproduce rõ ràng được sửa nhanh hơn 40% so với bug mô tả mơ hồ
2. **Severity ≠ Priority**: Bug Minor về UI có thể có Priority High nếu ảnh hưởng đến khách hàng lớn
3. **Communication quan trọng**: Dev cần được thông báo ngay khi có bug Blocker
4. **Retest bắt buộc**: Không nên close bug chỉ dựa trên lời "đã fix" của developer

---

## 6. Thống Kê Sprint 1

| Chỉ Số | GitHub Issues | Jira |
|--------|--------------|------|
| Tổng bug | 5 | 10 |
| Critical | 3 | 4 |
| Major | 1 | 4 |
| Minor | 1 | 2 |
| Bug Closed/Done | 2 (40%) | 5 (50%) |
| Bug Open | 3 (60%) | 5 (50%) |

---

## 7. Phân Công Vai Trò Nhóm ABC

| Thành Viên | Vai Trò Sprint 1 | Số Bug Tạo |
|-----------|-----------------|-----------|
| Nguyễn Thiện Phúc | Tester (QA) | 6 bugs |
| [Thành viên 2] | Developer | Fix 5 bugs |
| [Thành viên 3] | Project Manager | Quản lý tiến độ |
| [Thành viên 4] | Developer | Fix 3 bugs |

---

*Tài liệu lập ngày: 23/03/2026 | Nhóm ABC | Phiên bản: v1.0*
