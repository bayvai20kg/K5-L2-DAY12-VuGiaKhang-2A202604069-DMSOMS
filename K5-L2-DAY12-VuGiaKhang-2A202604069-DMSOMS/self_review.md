# Tự đánh giá — Vũ Gia Khang · G01

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| `S04_rgb` | `person` | `seat_flip` | Thuộc tính `seat` bị nhận nhầm giá trị mặc định `driver` của CVAT, cần chỉnh thành `rear_middle` | Có |
| `S05_rgb` | `child_seat` | `seat_flip` | Cả 2 ghế trẻ em đều ghi `rear_right`, đã sửa ghế bên phải ảnh thành `rear_left` theo xe | Có |
| `D03` | `hand` | `lr_flip` | Cả 2 bàn tay bị gán cùng `side=right`, đã chỉnh bàn tay có tọa độ y lớn hơn thành `side=left` | Có |
| `D04` | `face` (`eye_right`) | `guess` | Mắt phải bị đốm phản xạ NIR che khuất nhưng từng chọn `open`, đã sửa về `unknown` | Có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Bị nhầm lẫn hướng trái/phải theo góc nhìn người quan sát thay vì theo xe (ở OMS) hoặc theo cơ thể tài xế (ở DMS), và để sót thuộc tính mặc định đầu danh sách của CVAT (như `seat=driver`).

Vì sao mình mắc: Do thói quen nhìn màn hình máy tính thấy bên nào thì chọn bên đó, chưa hình dung camera OMS quay ngược từ trước ra sau (trái ảnh là phải xe) và ảnh DMS bị xoay 90°.

Lần sau tránh bằng cách: Luôn mở mục DETAILS để kiểm tra và chọn lại từng thuộc tính ngay sau khi vẽ xong một box; xoay góc nhìn theo đúng hướng ngồi thực tế của xe trước khi gán vị trí.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: Ở ảnh `S03_rgb`, bạn Nguyễn Bình Anh vẽ thêm box `object` cho chiếc túi đặt trong ghế trẻ em theo đúng Guideline mục 4.8 ("vật trong ghế trẻ em có 2 box riêng"), còn mình bị bỏ sót box đồ vật này. Mình học được bài học phải quan sát kỹ từng chi tiết nhỏ bên trong ghế trẻ em để không bỏ sót các lớp đối tượng cần thiết cho OMS.
