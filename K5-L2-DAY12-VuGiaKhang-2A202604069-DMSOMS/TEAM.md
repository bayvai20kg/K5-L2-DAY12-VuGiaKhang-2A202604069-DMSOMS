# TEAM — Ngày 12

Mã bộ ảnh: **G01** · Hình thức: nhóm

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Vũ Gia Khang | 2A202604069 | có | Nguyễn Bình Anh (2A202604063) | 75 dòng |
| Nguyễn Bình Anh | 2A202604063 | có | Vũ Gia Khang (2A202604069) | 75 dòng |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- `D05.png` (phone): Bạn Nguyễn Bình Anh vẽ box phone khi tài xế giơ tay áp gần tai, nhưng ảnh không thấy rõ góc cạnh hay màn hình điện thoại. Theo Guideline 4.7, mình không vẽ box phone. Hai bạn đã xin ý kiến coach và thống nhất theo quy tắc: chỉ vẽ phone khi thấy cạnh/góc máy.
- `S06_ir.png` / `S06_rgb.png`: Bạn Nguyễn Bình Anh gán trùng cả `child_seat` và `infant_seat` trên cùng một ghế `rear_right`. Coach hướng dẫn xác định lại loại ghế (đây là infant_seat dạng nôi xách) và xóa box trùng.

## Cá nhân

### VuGiaKhang-2A202604069
- Phần mình làm: Tự gán nhãn toàn bộ 22 ảnh cốt lõi (16 ảnh OMS và 6 ảnh DMS), thực hiện tự kiểm tra bằng script `cabin_check.py`, rà soát các bất đồng khi review chéo và hoàn thiện báo cáo E1–E5.
- Điều mình học được hôm nay: Hiểu rõ nguyên lý hoạt động của hệ thống DMS/OMS, sự khác biệt giữa ảnh cận hồng ngoại NIR thật và IR mô phỏng, và tầm quan trọng của việc gán nhãn theo xe / theo người thay vì theo màn hình.

### NguyenBinhAnh-2A202604063
- Phần mình làm: Tự gán nhãn 22 ảnh cốt lõi trên CVAT, xuất file `job_16_annotations_...`, thực hiện chạy diff đối chiếu chéo và cùng thống nhất xử lý các bất đồng nhãn.
- Điều mình học được hôm nay: Nắm được quy tắc không suy đoán (unknown) đối với mắt bị che khuất và cách phân biệt các loại ghế trẻ em trên khoang sau OMS.
