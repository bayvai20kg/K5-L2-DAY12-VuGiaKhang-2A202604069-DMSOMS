# Danh sách lớp v0 — Vũ Gia Khang · G01

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_state` | open / closed / unknown | Phát hiện buồn ngủ (mắt nhắm lâu, tính chỉ số PERCLOS để kích hoạt cảnh báo rung vô lăng/âm thanh) | Có, trừ khi tròng kính bị đốm phản xạ LED NIR che khuất |
| 2 | `gaze_zone` | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện mất tập trung (xao nhãng nhìn đùi lướt điện thoại hoặc nhìn màn hình trung tâm quá 2–3 giây) | Có, nhận diện qua hướng xoay khuôn mặt và vị trí con ngươi |
| 3 | `glasses` | none / clear / sun / unknown | Tùy biến thuật toán nhận diện mắt (tránh nhầm đốm sáng phản quang là mắt mở; cảnh báo kính râm che mắt) | Có, trên ảnh cận hồng ngoại NIR thì tròng kính râm tối màu có thể trông trong suốt |
| 4 | `hand_on_wheel` | yes / no / unknown | Giám sát mức độ sẵn sàng kiểm soát xe (Hands-on/off), cảnh báo tài xế tiếp quản vô lăng trong hệ thống tự hành ADAS L2/L3 | Có, biên dạng bàn tay và vành vô lăng hiển thị rõ ràng trên camera NIR |
| 5 | `phone_state` | held / mounted / lap | Phát hiện hành vi sử dụng điện thoại khi đang điều khiển phương tiện để cảnh báo nguy cơ tai nạn | Có nếu nhìn thấy cạnh, góc hoặc ánh sáng màn hình điện thoại |
| 6 | `face13_landmarks` | 13 điểm mốc mặt | Tính toán góc quay đầu (yaw, pitch, roll) và đo độ mở mí mắt chính xác phục vụ thuật toán nhận diện tư thế lái | Có, 13 điểm giải phẫu (mắt, mũi, môi) nổi bật trên ảnh NIR |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` (seat occupancy) | rear_left / rear_middle / rear_right | Nhận diện có người ngồi ở hàng ghế sau để bật chuông nhắc thắt dây an toàn cho đúng ghế đó | Có, hình khối cơ thể người phân biệt tốt trên ảnh IR |
| 2 | `seatbelt` | worn_correct / worn_incorrect / not_worn / unknown | Cảnh báo hành khách chưa thắt dây an toàn hoặc thắt dây sai quy cách (luồn dưới nách) | Kém hơn trên RGB nếu áo tối màu, nhưng vẫn phân biệt được nếu bề mặt dây có phản quang khác áo |
| 3 | `infant_seat` | facing: rear / front | Tự động vô hiệu hóa túi khí phía trước nếu nôi em bé lắp quay ngược chiều (`rear-facing`) để tránh lực nổ làm tổn thương bé | Có, hình dáng nôi xách em bé rất đặc trưng |
| 4 | `child_seat` | occupied: no / yes / unknown | Cảnh báo bỏ quên trẻ em ở hàng ghế sau khi tài xế tắt máy và rời xe (Child Presence Detection - CPD theo chuẩn Euro NCAP) | Có, hình dáng ghế trẻ em lớn có tựa đầu cao rất rõ nét |
| 5 | `leftover_object` | bag / box / cup / other | Cảnh báo hành khách để quên đồ đạc cá nhân (balo, vali, túi xách, hộp đồ) khi rời xe taxi / robotaxi | Có, nhận diện tốt qua hình khối hộp hoặc quai xách của vật |
| 6 | `passenger_count` | số nguyên (1, 2, 3...) | Đếm số lượng hành khách khoang sau để quản lý tải trọng xe và phát hiện chở quá số người quy định | Có, tổng hợp số lượng box `person` phát hiện được |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. **Câu hỏi:** Đối với nôi em bé (`infant_seat`), Guideline v1.0 chỉ có thuộc tính `facing` (`rear`/`front`) mà không có thuộc tính `occupied` để ghi nhận nôi đang có em bé hay nôi trống. Đề xuất bổ sung thuộc tính `occupied` cho `infant_seat` hoặc quy định rõ có cần vẽ thêm box `person` cho em bé nằm trong nôi hay không?  
   **Khung ví dụ:** `S03_rgb` / `S03_ir`  
   **Bạn tạm gán thế nào và vì sao:** Tạm thời chỉ vẽ box `infant_seat` ôm trọn nôi và gán thuộc tính `facing` theo đúng schema v1.0 để file export hợp lệ và script `cabin_check.py` không báo lỗi, đồng thời ghi chú ca này vào báo cáo.

2. **Câu hỏi:** Trên ảnh camera tài xế (`D##`) của xe tự lái thử nghiệm, tài xế thường xuyên buông tay khỏi vô lăng. Trường hợp tài xế chỉ đặt hờ 1–2 ngón tay chạm nhẹ vào vành vô lăng (không nắm tay) thì nên gán `on_wheel = yes` hay `no`?  
   **Khung ví dụ:** `D05.png`  
   **Bạn tạm gán thế nào và vì sao:** Tạm thời gán `on_wheel = no` vì chỉ chạm hờ ngón tay thì tài xế chưa sẵn sàng tiếp quản lực lái (takeover) ngay lập tức khi xảy ra tình huống khẩn cấp, việc gán `no` giúp hệ thống ADAS đưa ra cảnh báo an toàn hơn.
