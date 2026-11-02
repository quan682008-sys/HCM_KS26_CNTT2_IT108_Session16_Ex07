# HCM_KS26_CNTT2_IT108_Session16_Ex07
##  1. Những lỗi sai của thực tập sinh

Theo em, bản báo cáo có 4 lỗi chính:

- **DNS:** Trình duyệt cần phân giải tên miền `carepulse.vn` thành địa chỉ IP chứ không gửi trực tiếp toàn bộ URL để tìm máy chủ.
- **TCP/TLS:** Khi sử dụng HTTPS, trình duyệt phải thiết lập kết nối và mã hóa trước khi trao đổi dữ liệu.
- **HTTP 404:** Máy chủ cơ sở dữ liệu bị lỗi không có nghĩa là hồ sơ bệnh nhân đã bị xóa.
- **DevTools:** Chỉnh sửa nội dung trong tab Elements chỉ thay đổi giao diện trên máy đang sử dụng, không thay đổi dữ liệu gốc.

Ngoài ra, trình duyệt không vẽ trực tiếp JavaScript mà phải xử lý HTML thành DOM, CSS thành CSSOM rồi mới dựng giao diện.

---

##  2. Phân biệt các mã HTTP

- **200 OK:** Yêu cầu được xử lý thành công.
- **404 Not Found:** Không tìm thấy tài nguyên được yêu cầu.
- **500 Internal Server Error:** Máy chủ gặp lỗi trong quá trình xử lý.

Nếu backend gặp lỗi khi truy vấn cơ sở dữ liệu thì có thể trả về mã 500, không phải 404. Nếu hệ thống báo sai rằng hồ sơ đã bị xóa, bệnh nhân có thể hoang mang, lo lắng và mất niềm tin vào bệnh viện.

---

##  Phần 2: Sửa lỗi và hoàn thiện

### 3. Quy trình HTTP Request đúng

1. Bệnh nhân truy cập CarePulse
2. **DNS Lookup:** Tìm địa chỉ IP của máy chủ
3. **TCP/TLS Handshake:** Thiết lập kết nối HTTPS an toàn
4. **HTTP Request & Response:** Trình duyệt gửi yêu cầu xem kết quả, Server truy vấn Database
5. Database gặp lỗi → Server trả về 500
6. **Rendering:** HTML → DOM, CSS → CSSOM, Layout → Paint
7. Trình duyệt hiển thị thông báo lỗi

### 4. Vì sao sửa Elements không thay đổi Database?

Khi thực tập sinh dùng F12 để sửa chữ thành "Âm tính - Bình thường", nội dung chỉ thay đổi tạm thời trong DOM trên RAM của máy tính.

Dữ liệu xét nghiệm thật vẫn được lưu trên Database của máy chủ CarePulse. Muốn thay đổi dữ liệu phải thực hiện qua hệ thống backend có quyền truy cập hợp lệ.

Khi tải lại trang bằng F5, nội dung chỉnh sửa tạm thời sẽ mất và trình duyệt lấy dữ liệu từ hệ thống.
