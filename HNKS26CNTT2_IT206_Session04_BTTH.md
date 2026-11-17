# [BTTH] Bài tập thực hành tổng hợp
## Báo cáo thiết kế giải pháp
- Bài toán: Tự động hóa quy trình xử lý yêu cầu đổi trả/khiếu nại khách hàng tại cửa hàng bán lẻ.
- Kỹ thuật ứng dụng:
```
Chain-of-Thought (CoT): AI thực hiện tư duy từng bước logic (Kiểm tra dữ liệu => Đối chiếu chính sách
=> Đưa ra quyết định.
Prompt Chaining: Chia nhỏ các tác vụ tuần tự khép kín để chặn lỗi dữ liệu rỗng/sai lệch
tránh làm sai lệch kết quả.
```
## Prompt thực thi các bước
```prompt
Bạn là Trợ lý CSKH bán lẻ. Hãy thực hiện chính xác quy trình 3 bước sau:
- Bước 1 (Kiểm tra dữ liệu): Kiểm tra dữ liệu đầu vào xem có thiếu thông tin cốt lõi (Mã đơn hàng, Ngày mua) không.
Nếu thiếu, dừng xử lý và xuất yêu cầu bổ sung.
- Bước 2 (Phân tích logic): Đối chiếu điều kiện thời gian đổi trả trong 7 ngày.
- Bước 3 (Kết quả & Phản hồi): Đưa ra quyết định nghiệp vụ và soạn thảo câu trả lời lịch sự cho khách.

--- DỮ LIỆU ĐẦU VÀO ---
- Mã đơn hàng: [Để trống để test lỗi]
- Tên khách hàng: Nguyễn Văn A
- Sản phẩm mua: Áo polo
- Ngày mua: [Để trống]
- Nội dung khiếu nại: Sản phẩm bị lỗi đường may.
```
## kết quả đầu ra sạch lỗi của AI
```
1. [Kiểm tra dữ liệu]: Trạng thái LỖI - Thiếu "Mã đơn hàng" và "Ngày mua".
2. [Phân tích logic (CoT)]: Không đủ căn cứ thời gian để áp dụng chính sách đổi trả 7 ngày.
3. [Quyết định nghiệp vụ]: Yêu cầu khách hàng cung cấp bổ sung thông tin còn thiếu.
4. [Phản hồi khách hàng]: "Dạ chào anh Nguyễn Văn A, cửa hàng rất tiếc về lỗi sản phẩm.
Để hỗ trợ đổi trả nhanh chóng, anh vui lòng cung cấp thêm
Mã đơn hàng và Ngày mua giúp cửa hàng nhé ạ!"
```
