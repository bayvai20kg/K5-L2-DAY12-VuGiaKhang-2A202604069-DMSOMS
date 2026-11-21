# Nhật ký sử dụng AI — Ngày 12

Họ tên: Vũ Gia Khang · Nhóm: G01

1. **Công cụ:** Antigravity (Google DeepMind)
   - **Mục đích:** Giải thích mục tiêu bài lab, hệ thống quy tắc Guideline Cabin v1.0, và phân biệt giữa DMS vs OMS.
   - **Câu hỏi / prompt:** "doc folder, giai thich bai lab hom nay va huong dan toi cach lam bai lab nay", "dms va oms la gi"
   - **Cách dùng kết quả:** Nắm rõ lịch trình thực hiện, các tiêu chí đánh giá trong Rubric và hiểu đúng ý nghĩa các lớp nhãn an toàn trên xe ô tô.

2. **Công cụ:** Antigravity (Google DeepMind)
   - **Mục đích:** Hỏi về vị trí điểm mốc giải phẫu `nose_tip` và giải thích thuộc tính vùng nhìn `gaze_zone`.
   - **Câu hỏi / prompt:** "nose tip la phan nao cua mui", "gaze_zone la gi", "này là facing front hay rear"
   - **Cách dùng kết quả:** Chỉnh lại điểm chóp mũi chính xác trên ảnh khuôn mặt xoay 90°, chọn đúng giá trị vùng nhìn của tài xế và nhận biết hướng của ghế trẻ em theo xe.

3. **Công cụ:** Antigravity (Google DeepMind)
   - **Mục đích:** Cập nhật file schema tự kiểm tra `scripts/cabin_schema.py` để đồng bộ với cập nhật của Coach và kiểm tra hợp lệ file export cuối cùng.
   - **Câu hỏi / prompt:** "sửa lại file tự check cho tôi, do lab coach cập nhật file label ( thêm occupie) nhưng mà file tự kiểm tra thì chưa có", "tôi đã đưa file zip annotations vào..."
   - **Cách dùng kết quả:** Đồng bộ schema và chạy script kiểm tra 22 ảnh đạt kết quả 0 lỗi.
