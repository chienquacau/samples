# Vị trí: Innovator (Người đổi mới)

## Tóm tắt

Innovator là vị trí theo dõi và đối chiếu các "mẫu" (sample) — kênh truyền thông, nhân sự
sale, nhân sự dịch vụ — cả bên ngoài (đối thủ) lẫn bên trong (nội bộ Quả Cầu), nhằm tìm ra
điểm làm tốt hơn ở mẫu tốt nhất và áp dụng (nhân rộng) cho các mẫu còn lại, để liên tục
nâng cao hiệu suất tối ưu nhất — đo bằng chỉ số tối quan trọng: **số lượng Lead**.

Tên gọi "Innovator" thể hiện đúng bản chất công việc: vừa **kế thừa** (theo dõi, giữ lại
cái đang chạy tốt) vừa **đổi mới** (tìm và nhân rộng cái tốt hơn).

## Phạm vi theo dõi

Innovator theo dõi 3 nhóm mẫu trong `channel-tracking/`:

1. **Kênh truyền thông**: kênh đối thủ (`group=competitor`) và kênh của Quả Cầu (`group=own`).
2. **Sale**: các nhân viên sale tham gia các chapter BNI khác nhau.
3. **Dịch vụ**: nhân sự phụ trách/kiểm soát dịch vụ trong nội bộ công ty.

## Nhiệm vụ chính

1. **Theo dõi mẫu**: Đảm bảo dữ liệu snapshot của từng mẫu (kênh/sale/dịch vụ) được cập
   nhật đều đặn (khuyến nghị hàng tuần) vào các file snapshot tương ứng.
2. **So sánh mẫu**: Đối chiếu các mẫu cùng nhóm với nhau (kênh đối thủ vs kênh mình, sale
   với sale, nhân sự dịch vụ với nhân sự dịch vụ) để xác định mẫu có chỉ số tốt nhất liên
   quan đến Lead.
3. **Phân tích**: Tìm ra lý do mẫu tốt nhất vượt trội — cách làm, nội dung, quy trình,
   hành vi cụ thể nào tạo ra khác biệt.
4. **Đề xuất & áp dụng**: Đề xuất cách áp dụng điểm tốt đó cho các mẫu còn lại (bao gồm cả
   việc "copy" cách làm hay của đối thủ cho kênh của mình). Theo dõi việc áp dụng này như
   một phiên bản mới của mẫu.
5. **Ghi log phiên bản**: Mọi chu trình so sánh → phân tích → áp dụng đều được ghi lại vào
   `channel-tracking/benchmark_log.csv`, bao gồm chỉ số trước và sau khi áp dụng, để đánh
   giá cải tiến có thực sự hiệu quả hay không.
6. **Báo cáo**: Định kỳ báo cáo lại cho các bên liên quan (chủ kênh, trưởng nhóm sale,
   trưởng bộ phận dịch vụ) về mẫu nào đang dẫn đầu và khuyến nghị nên học hỏi điều gì.

## Quy trình làm việc

Theo quy trình 3 bước định nghĩa trong [`../POLICY.md`](../POLICY.md):

**Bước 1 — So sánh** → **Bước 2 — Phân tích** → **Bước 3 — Áp dụng (nâng cấp phiên bản)**

## Lưu ý

- Innovator không tự ý thay đổi cách vận hành của nhân sự khác; vai trò là đề xuất dựa trên
  dữ liệu, quyết định áp dụng cuối cùng thuộc về người/bộ phận liên quan (trừ khi được giao
  quyền trực tiếp).
- Mọi so sánh phải đảm bảo "so cùng nhóm" (cùng nền tảng/thể loại kênh, cùng chapter sale,
  cùng vị trí dịch vụ) để kết quả có ý nghĩa.
