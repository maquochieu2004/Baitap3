# Baitap3
SỬ DỤNG DOCKER TRÊN UBUNTU ĐỂ TẠO docker chứa:
Mariadb: use image: mariadb:latest để làm hệ quản trị csdl cho wordpress Phpmyadmin:sư dụng image: phpmyadmin:latest để đăng nhập vào mariadb rồi tạo csdl trống (chỉ để xem, ko cần tạo bảng từ đây, wordpress sẽ làm hết) WordPress: Use image: wordpress:latest, truyền tham số môi trường cho wordpress là các thông tin truy cập csdl mariadb, được tạo bởi Phpmyadmin Yêu cầu: sau khi có 3 dịch vụ này trong tệp docker-compose.yml : Cấu hình để hệ thống chạy Sử dụng đường hầm cloudflare để web công cộng này lên 1 tên miền phụ Tạo 1 bài viết trong wordpress giới thiệu về bản thân sinh viên: thông tin cá nhân, cơ sở thích, ... bài viết có thể chứa hình ảnh, âm thanh, video, ... Tạo 1 bài viết trong wordpress giới thiệu về chuyên ngành mà em yêu thích trong trường TNUT. bài viết phải chứa hình ảnh, video, ... Nhận xét việc sử dụng mã nguồn mở wordpress để tạo trang web (tốn công sức thế nào, dễ/khóa dùng ra sao, tài nguyên (ssh/ram) rẻ tiền của máy chủ ra sao,....)
## Bước 1: Tạo file docker-compose.yml
Tạo tệp: nano docker-compose.yml

<img width="1153" height="929" alt="image" src="https://github.com/user-attachments/assets/95577a64-25df-4412-993d-94e709af47dd" />

## Bước 2: Chạy docker soạn thảo
Chạy: docker compose up -d

<img width="807" height="911" alt="image" src="https://github.com/user-attachments/assets/8b49367e-1936-42c5-bacb-94ed3913c5dd" />

Kiểm tra container: docker ps

<img width="952" height="916" alt="image" src="https://github.com/user-attachments/assets/0c1d9c06-e731-4454-afbd-99636e65c4c9" />

## Bước 3: Truy cập website
WordPress http://IP_UBUNTU:8001 phpMyAdmin http://IP_UBUNTU:8082 Nếu chưa biết IP Ubuntu Chạy: ip

<img width="727" height="613" alt="image" src="https://github.com/user-attachments/assets/c2fe5431-2241-4267-a271-5db8ff1edd9a" />

kết quả IP Ubuntu của bạn là: 192.168.1.13 Bây giờ mở WordPress Trên trình duyệt Windows hoặc Ubuntu mở:

<img width="1685" height="934" alt="image" src="https://github.com/user-attachments/assets/40ec80fc-1fa9-4e43-9a05-000652969209" />


<img width="1650" height="953" alt="image" src="https://github.com/user-attachments/assets/00f3188d-fa3c-4c45-b690-b2648bdc8b95" />


## Tạo bài viết 1
Giới thiệu bản thân thân tạo 1 bài viết trong wordpress giới thiệu về thân sinh viên: thông tin cá nhân, sở hữu, ... bài viết có thể chứa hình ảnh, âm thanh, video, .

<img width="1650" height="953" alt="image" src="https://github.com/user-attachments/assets/a085a453-afcc-403c-8a2f-995dc66a21f8" />


Tạo bài viết 2
Tạo 1 bài viết trong wordpress giới thiệu về các ngành học mà em yêu thích trong trường TNUT. bài viết phải chứa hình ảnh, video, ... Sử dụng đường hầm cloudflare để công khai web này lên 1 tên miền phụ cloudflared --version ĐĂNG NHẬP CLOUDFLARE: đăng nhập đường hầm cloudflared TẠO TUNNEL chạy: đường hầm cloudflared tạo đường hầm wordpress Tạo file config: nano ~/.cloudflared/config.yml Vào Wordpess -> cài đặt -> tổng quan và sửa URL


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/d172c0df-9e9b-4a56-abcd-0906610cf030" />

Bản báo cáo ngắn gọn, liền mạch để bạn copy-paste dùng ngay:

---

### BÁO CÁO KẾT QUẢ THỰC HÀNH: TRIỂN KHAI WEBSITE WORDPRESS

**1. Đánh giá trải nghiệm và công sức triển khai**

* **Tối ưu thời gian:** WordPress giúp xây dựng website cực nhanh nhờ giao diện trực quan, dễ sử dụng, thao tác đăng bài viết và quản lý nội dung đa phương tiện (ảnh, video) rất đơn giản.
* **Mở rộng dễ dàng:** Kho Plugin và Theme phong phú hỗ trợ tích hợp thêm nhiều tính năng nâng cao mà không cần viết code từ đầu.

**2. Đánh giá tài nguyên máy chủ và chi phí**

* **Đặc điểm:** WordPress xử lý dữ liệu động với DB nên **ngốn RAM và CPU hơn web tĩnh**. Nếu lạm dụng cài quá nhiều plugin sẽ khiến trang web bị chậm hệ thống.
* **Tối ưu chi phí:** Dù tốn tài nguyên, hệ thống vẫn vận hành mượt mà trên các gói máy chủ/VPS giá rẻ nhờ được tối ưu qua dòng lệnh **SSH** và đóng gói bằng **Docker**.

**3. Ưu và Nhược điểm**

* **Ưu điểm:** Khởi tạo nhanh, dễ quản trị, kho tiện ích mở rộng đa dạng.
* **Nhược điểm:** Tốn tài nguyên phần cứng, dễ lag nếu xung đột plugin, cần cấu hình bảo mật kỹ lưỡng khi public lên Internet.

**4. Kiến thức thu nhận được**
Qua bài thực hành, em đã làm chủ được quy trình đóng gói và quản lý đồng bộ các container **WordPress, MariaDB, PhpMyAdmin** bằng **Docker Compose**, đồng thời biết cách đưa website local ra Internet công cộng an toàn qua **Cloudflare Tunnel**.


