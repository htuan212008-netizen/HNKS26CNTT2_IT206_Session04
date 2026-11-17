# [Phân tích] So sánh Trade-off các giải pháp ra lệnh cho Kỹ thuật Prompting Nâng cao (Logic & Chuỗi)
## Bước 1: Đề xuất 2 prompt mẫu
Giải pháp 1:
```
"Hãy đóng vai nhân viên CSKH. Kiểm tra dữ liệu đơn hàng và xử lý yêu cầu đổi trả cho khách hàng
theo chính sách đổi trả trong 7 ngày."
```
Giải pháp 2:
```
"Bạn là Trợ lý CSKH bán lẻ. Hãy thực hiện đúng quy trình 3 bước sau:
Bước 1: Kiểm tra dữ liệu đầu vào xem có bị thiếu sót (Mã đơn, Ngày mua) không.
Nếu thiếu,dừng lại và yêu cầu bổ sung.
Bước 2: Đối chiếu điều kiện thời gian đổi trả trong 7 ngày.
Bước 3: Đưa ra quyết định nghiệp vụ và soạn phản hồi lịch sự cho khách."
```
## Bước 2: Lập bảng so sánh Trade-off
| Tiêu chí | Giải pháp 1 (Đơn giản) | Giải pháp 2 (Chi tiết) |
| :--- | :--- | :--- |
| **Độ dễ hiểu** | Cao | Trung bình |
| **Tốn token** | Ít | Nhiều hơn |
| **Chặn lỗi biên** | Trung bình | Cực tốt |
## Bước 3: Lựa chọn và chạy thử
- Lựa chọn: Chọn Giải pháp 2 vì có kỹ thuật Chain-of-Thought (từng bước logic) và kiểm soát lỗi biên tốt hơn,
phù hợp với bài toán tự động hóa nghiệp vụ.
- Chạy thử
```test
1. [Kiểm tra dữ liệu]: Trạng thái LỖI - Thiếu "Mã đơn hàng" và "Ngày mua".
2. [Phân tích logic]: Không đủ căn cứ thời gian để áp dụng chính sách đổi trả 7 ngày.
3. [Quyết định]: Yêu cầu khách hàng cung cấp bổ sung thông tin.
4. [Phản hồi khách]: "Dạ chào anh/chị, để hỗ trợ đổi trả nhanh chóng, anh/chị vui lòng cung cấp thêm
Mã đơn hàng và Ngày mua giúp cửa hàng nhé ạ!"
```
