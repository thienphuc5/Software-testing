# JIRA WORKFLOW – DEFECT MANAGEMENT
## Student Management System (SMS) – Sprint 1

---

## 1. Cấu Hình Jira Project

| Thông Tin | Giá Trị |
|-----------|---------|
| **Project Name** | Student Management System |
| **Project Key** | SMS |
| **Project Type** | Scrum Software Development |
| **Sprint** | Sprint 1 – Defect Tracking |
| **Team** | Nhóm ABC |

---

## 2. Issue Types

| Type | Icon | Mô Tả |
|------|------|--------|
| **Bug** | 🐛 | Lỗi phần mềm cần sửa |
| **Task** | ✅ | Công việc cần thực hiện |
| **Story** | 📖 | Yêu cầu người dùng |

### Custom Fields Bổ Sung:
| Field | Values |
|-------|--------|
| **Severity** | Critical / Major / Minor / Trivial |
| **Priority** | Blocker / High / Medium / Low |
| **Test Environment** | Chrome/Win10, Firefox/Win11,... |
| **Found In Build** | v1.0.0, v1.0.1,... |
| **Fix Version** | v1.1.0 |

---

## 3. Workflow Chuẩn Doanh Nghiệp

```
┌─────────┐    ┌──────┐    ┌─────────────┐    ┌─────────┐    ┌───────────┐    ┌──────┐
│   New   │───▶│ Open │───▶│ In Progress │───▶│  Fixed  │───▶│ QA Verify │───▶│ Done │
└─────────┘    └──────┘    └─────────────┘    └─────────┘    └───────────┘    └──────┘
                               │                                    │
                               │ (Không thể                         │ (Verify Fail –
                               │  tái hiện)                         │  bug vẫn còn)
                               ▼                                    ▼
                         ┌──────────┐                         ┌──────────┐
                         │ Rejected │                         │  Reopen  │
                         └──────────┘                         └──────────┘
```

### Mô Tả Từng Trạng Thái:

| Trạng Thái | Người Phụ Trách | Hành Động |
|-----------|----------------|-----------|
| **New** | Tester | Bug vừa được tạo |
| **Open** | QA Lead / PM | Đã xác nhận, gán cho Developer |
| **In Progress** | Developer | Đang phân tích và sửa |
| **Fixed** | Developer | Đã sửa, chờ QA xác nhận |
| **QA Verify** | Tester | Đang kiểm tra lại (retest) |
| **Done** | Tester | Bug đã sửa xong và xác nhận |
| **Rejected** | Developer | Bug không hợp lệ / không tái hiện được |
| **Reopen** | Tester | Bug vẫn còn sau khi "sửa" |

---

## 4. Labels & Components

### Labels:
- `critical` – bug mức Critical
- `blocker` – chặn release
- `regression` – bug tái phát
- `ui` – giao diện
- `security` – bảo mật
- `performance` – hiệu năng

### Components:
- Authentication
- Student Management
- Search
- Authorization
- UI/UX

---

## 5. Roles & Responsibilities

| Vai Trò | Jira Permission | Trách Nhiệm |
|---------|----------------|-------------|
| **Tester (QA)** | Create, Edit, Transition | Tạo bug, retest, close |
| **Developer** | Edit, Transition | Nhận bug, fix, chuyển → Fixed |
| **Project Manager** | All | Phân loại ưu tiên, quản lý sprint |
| **QA Lead** | Edit, Transition | Review chất lượng bug report |
