# CHỈ SỐ KIỂM THỬ (TEST METRICS)
## E-Commerce Website – Manual Testing
**Ngày lập:** 23/03/2026 | **Chu kỳ:** Sprint 1

---

## Chỉ Số 1: Tỷ Lệ Thực Thi Test (Test Execution Rate)

### Công Thức
```
Test Execution Rate = (Số TC đã thực thi / Tổng số TC) × 100%
```

### Kết Quả

| Module | Tổng TC | TC Đã Thực Thi | Execution Rate |
|--------|---------|----------------|----------------|
| Authentication | 15 | 15 | 100% |
| Product & Cart | 20 | 20 | 100% |
| Checkout | 10 | 10 | 100% |
| **Tổng** | **45** | **45** | **100%** |

**Breakdown:**
```
Pass     = 31 / 45 = 68.9%
Fail     = 13 / 45 = 28.9%
Blocked  =  1 / 45 =  2.2%
```

### Biểu Đồ (ASCII)
```
Test Execution Results
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
PASS    [████████████████████████████░░░░] 68.9%
FAIL    [█████████████░░░░░░░░░░░░░░░░░░░] 28.9%
BLOCKED [█░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░░]  2.2%
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Nhận xét:** Tỷ lệ thực thi đạt 100% (tất cả 45 TC đã được chạy). Tỷ lệ Pass 68.9% dưới ngưỡng chấp nhận 80%, cần khắc phục bug trước khi release.

---

## Chỉ Số 2: Mật Độ Lỗi Theo Module (Defect Density per Module)

### Công Thức
```
Defect Density = Số Bug phát hiện / Tổng số TC của Module
```

### Kết Quả

| Module | Số Bug | Số TC | Defect Density | Đánh Giá |
|--------|--------|-------|----------------|---------|
| Authentication | 4 | 15 | **0.27 bug/TC** | ⚠️ Trung bình |
| Product & Cart | 5 | 20 | **0.25 bug/TC** | ⚠️ Trung bình |
| Checkout | 4 | 10 | **0.40 bug/TC** | 🔴 Cao |
| **Tổng** | **13** | **45** | **0.29 bug/TC** | |

### Biểu Đồ Mật Độ Lỗi
```
Defect Density by Module
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Auth      (0.27) [█████████████░░░░░░░░░░░░░░░░]
Cart      (0.25) [████████████░░░░░░░░░░░░░░░░░]
Checkout  (0.40) [████████████████████░░░░░░░░░]  ← Rủi ro cao nhất
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

**Nhận xét:** Module Checkout có mật độ lỗi cao nhất (0.40 bug/TC). Cần tập trung nguồn lực phát triển và testing vào module này.

---

## Chỉ Số 3: Phân Bố Mức Độ Nghiêm Trọng (Severity Distribution)

### Kết Quả

| Severity | Số Bug | Tỷ Lệ | Module |
|----------|--------|-------|--------|
| 🔴 Critical | 5 | 38.5% | Auth (2), Cart (1), Checkout (2) |
| 🟠 Major | 6 | 46.1% | Auth (1), Cart (3), Checkout (2) |
| 🟡 Minor | 2 | 15.4% | Auth (1), Cart (1) |
| **Tổng** | **13** | **100%** | |

### Biểu Đồ Phân Bố
```
Severity Distribution of 13 Bugs
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Critical  5 bugs  [████████████████████░░░░░░░░░] 38.5%
Major     6 bugs  [████████████████████████░░░░░] 46.1%
Minor     2 bugs  [████████░░░░░░░░░░░░░░░░░░░░░] 15.4%
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

### Phân Bố Bug Theo Module × Severity

| Module | Critical | Major | Minor | Tổng |
|--------|---------|-------|-------|------|
| Authentication | 2 | 1 | 1 | **4** |
| Product & Cart | 1 | 3 | 1 | **5** |
| Checkout | 2 | 2 | 0 | **4** |
| **Tổng** | **5** | **6** | **2** | **13** |

**Nhận xét:** 84.6% lỗi ở mức Critical và Major – tỷ lệ rất cao, cho thấy chất lượng code cần cải thiện. Đặc biệt chú ý đến lỗ hổng bảo mật và lỗi tính tiền.

---

## Chỉ Số 4: Độ Bao Phủ Yêu Cầu (Requirement Coverage %)

### Công Thức
```
Requirement Coverage = (Số Requirement được bao phủ / Tổng số Requirement) × 100%
```

### Kết Quả

| Module | Tổng Requirement | Requirement Covered | Coverage |
|--------|-----------------|---------------------|---------|
| Authentication | R1–R6 (6) | 6 | 100% |
| Product & Cart | R7–R12 (6) | 6 | 100% |
| Checkout | R13–R16 (4) | 4 | 100% |
| **Tổng** | **16** | **16** | **100%** ✅ |

### Chi Tiết Test Case trên mỗi Requirement

| Req ID | Số TC Mapping | Loại TC |
|--------|--------------|---------|
| R1 | 3 TC | Positive, Negative |
| R2 | 2 TC | Negative, Validation |
| R3 | 3 TC | Positive, Boundary, Negative |
| R4 | 3 TC | Positive, Negative |
| R5 | 4 TC | Negative, Security |
| R6 | 2 TC | Positive, Negative |
| R7 | 4 TC | Positive, Negative, Boundary, Security |
| R8 | 4 TC | Positive, Negative, Boundary |
| R9 | 1+ TC | Positive |
| R10 | 6 TC | Positive, Negative, Boundary |
| R11 | 5 TC | Positive, Boundary, Negative |
| R12 | 2 TC | Positive |
| R13 | 4 TC | Negative, Security, Validation |
| R14 | 3 TC | Positive, Negative |
| R15 | 4 TC | Positive, Negative, Security |
| R16 | 1+ TC | Positive |

**Nhận xét:** Đạt độ bao phủ 100% (vượt yêu cầu tối thiểu 95%). Mỗi requirement đều có ít nhất 2 test case (đạt yêu cầu bài tập).

---

## Chỉ Số 5: Tỷ Lệ Lỗi Theo Loại Test

| Loại Test | Số TC | Số Fail | Fail Rate |
|-----------|-------|---------|-----------|
| Positive | 18 | 2 | 11.1% |
| Negative | 14 | 5 | 35.7% |
| Boundary | 7 | 3 | 42.9% |
| Security | 4 | 2 | 50.0% |
| Validation | 5 | 1 | 20.0% |

**Nhận xét:** Test case loại Security và Boundary có tỷ lệ thất bại cao nhất, phản ánh nhiều vấn đề về validation và bảo mật trong hệ thống.

---

## Tổng Hợp Dashboard

```
┌─────────────────────────────────────────────────┐
│         TESTING METRICS DASHBOARD               │
├──────────────────┬──────────────────────────────┤
│ Execution Rate   │ 100%  (45/45 TC)              │
│ Pass Rate        │ 68.9%  ⚠️ (Below 80% target)  │
│ Defect Density   │ 0.29 bug/TC                   │
│ Req. Coverage    │ 100%  ✅                       │
│ Total Bugs       │ 13 (5 Critical, 6 Major)      │
│ Release Status   │ ❌ NO-RELEASE                  │
└──────────────────┴──────────────────────────────┘
```

---

*Tài liệu lập ngày: 23/03/2026 | Phiên bản: v1.0*
