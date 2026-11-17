# [Vận dụng chuyên sâu] Thiết kế giải pháp Prompting ứng dụng thực tế cho Kỹ thuật Prompting Nâng cao (Logic & Chuỗi)
## Bước 1: Thiết kế giải pháp (I/O) 
- Input: Thông tin đơn hàng và khiếu nại của khách (Mã đơn, Tên, Sản phẩm, Ngày mua, Nội dung).
- Output: Trạng thái kiểm tra dữ liệu, các bước suy luận logic (CoT), quyết định xử lý và mẫu tin nhắn phản hồi khách hàng.
## Bước 2: Viết prompt và chạy thử
- Prompt mẫu
```prompt
Bạn là nhân viên CSKH xử lý đổi trả. Hãy làm theo 3 bước:
- Bước 1: Kiểm tra xem dữ liệu đầu vào có bị thiếu thông tin cốt lõi (Mã đơn, Ngày mua) không.
Nếu thiếu, dừng lại và yêu cầu khách bổ sung.
- Bước 2: Đối chiếu với chính sách đổi trả trong 7 ngày.
- Bước 3: Đưa ra quyết định và soạn câu trả lời lịch sự cho khách.

Dữ liệu đầu vào:
- Mã đơn hàng: [Trống]
- Tên: Nguyễn Văn A
- Sản phẩm: Áo polo
- Ngày mua: [Trống]
- Nội dung: Sản phẩm bị lỗi đường may.
```
- Kết quả
```result
1. [Kiểm tra dữ liệu]: Lỗi - Thiếu "Mã đơn hàng" và "Ngày mua".
2. [Phân tích logic]: Không đủ thông tin thời gian để xác định chính sách 7 ngày, cần yêu cầu bổ sung.
3. [Quyết định]: Yêu cầu khách cung cấp thêm thông tin.
4. [Phản hồi khách]: "Dạ chào anh Nguyễn Văn A, cửa hàng rất tiếc về lỗi sản phẩm.
Để hỗ trợ đổi trả nhanh chóng, anh vui lòng
cung cấp thêm Mã đơn hàng và Ngày mua
giúp cửa hàng nhé ạ!"
```
