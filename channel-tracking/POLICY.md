# Quy định: Cơ chế Benchmark (So sánh – Phân tích – Áp dụng)

## 1. Mục tiêu

Mục tiêu tối quan trọng (North Star metric) của toàn bộ cơ chế này là **số lượng Lead**.

Mọi hoạt động theo dõi, so sánh, phân tích trong thư mục `channel-tracking/` đều phục vụ
một mục đích duy nhất: tìm ra "mẫu" (sample) nào — kênh, nhân sự sale, nhân sự dịch vụ —
đang tạo ra hiệu suất/lead tốt hơn, từ đó học hỏi và áp dụng điểm tốt đó cho các mẫu còn lại.

Hệ thống này **chỉ** là hệ thống lấy dữ liệu để báo cáo và đưa ra đề xuất cải tiến.
Nó không tự động thực thi hành động — con người (Innovator) ra quyết định áp dụng.

## 2. Nguyên tắc "Mẫu" (Sample)

Một "mẫu" là bất kỳ thực thể nào có thể đo lường và so sánh được hiệu suất theo thời gian.
Có 3 nhóm mẫu trong dự án này:

| Nhóm | Thư mục | Thực thể | Đối tượng so sánh |
|---|---|---|---|
| Kênh truyền thông | `channel-tracking/channels.csv` + `snapshots.csv` | Kênh MXH (Facebook, TikTok, YouTube...) | Kênh đối thủ (`group=competitor`) so với kênh của mình (`group=own`) |
| Sale | `channel-tracking/sales/` | Nhân viên sale tham gia các chapter BNI | Nhân viên với nhau theo chapter |
| Dịch vụ | `channel-tracking/service/` | Nhân sự phụ trách dịch vụ/kiểm soát dịch vụ | Nhân sự với nhau theo vị trí/phòng ban |

Mỗi nhóm có 2 loại file:
- **File danh mục** (registry): mô tả tĩnh về thực thể (tên, phân loại, ngày thêm, trạng thái).
- **File snapshot**: dữ liệu đo lường theo thời gian, mỗi lần chụp (chu kỳ khuyến nghị: **hàng tuần**)
  thêm một dòng mới — không ghi đè dữ liệu cũ, để giữ lịch sử.

## 3. Phân loại kênh truyền thông

Trong `channels.csv`:
- `group`: `competitor` (đối thủ) hoặc `own` (kênh của Quả Cầu).
- `platform`: nền tảng (Facebook, TikTok, YouTube, Zalo, Instagram...).
- `category`: thể loại nội dung của kênh (ví dụ: giáo dục, giải trí, bán hàng trực tiếp, review...).

Khi thêm kênh của mình để so sánh, tạo dòng mới trong `channels.csv` với `group=own`,
điền đầy đủ `platform` và `category` giống cách phân loại kênh đối thủ để đảm bảo so sánh
đồng nhất (apples-to-apples).

## 4. Quy trình Benchmark (3 bước)

1. **So sánh (Compare)**: Tổng hợp dữ liệu snapshot mới nhất của các mẫu cùng nhóm
   (cùng `platform`/`category` đối với kênh; cùng chapter đối với sale; cùng vị trí đối với
   dịch vụ). Xác định mẫu có chỉ số tốt nhất liên quan đến Lead.
2. **Phân tích (Analyze)**: Tìm ra *vì sao* mẫu tốt nhất vượt trội — nội dung, cách làm,
   hành vi, quy trình nào khác biệt. Ghi nhận phát hiện (`finding`).
3. **Áp dụng (Apply)**: Đề xuất và áp dụng điểm tốt đó cho các mẫu còn lại (copy cách làm
   hay). Ghi nhận mỗi lần áp dụng là một **phiên bản (version)** mới của mẫu được cải tiến,
   log lại trong `benchmark_log.csv` kèm chỉ số trước/sau để đo hiệu quả của cải tiến.

Toàn bộ lịch sử của chu trình 3 bước trên được lưu trong `channel-tracking/benchmark_log.csv`.

## 5. Vị trí phụ trách

Vị trí **Innovator** (Người đổi mới) chịu trách nhiệm vận hành toàn bộ quy trình này.
Xem mô tả chi tiết tại [`roles/INNOVATOR.md`](roles/INNOVATOR.md).

## 6. Cấu trúc thư mục

```
channel-tracking/
├── POLICY.md              # Quy định này
├── benchmark_log.csv       # Log so sánh / phân tích / áp dụng / phiên bản
├── channels.csv            # Danh mục kênh (đối thủ + của mình)
├── snapshots.csv           # Snapshot chỉ số kênh theo tuần
├── sales/
│   ├── sales_reps.csv      # Danh mục nhân viên sale (theo chapter BNI)
│   └── sales_snapshots.csv # Snapshot hiệu suất sale theo tuần
├── service/
│   ├── staff.csv           # Danh mục nhân sự dịch vụ
│   └── staff_snapshots.csv # Snapshot hiệu suất dịch vụ theo tuần
└── roles/
    └── INNOVATOR.md        # Mô tả vị trí Innovator
```
