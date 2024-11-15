# Phân tích kiến trúc

### Đề xuất kiến trúc:

- **Kiến trúc lựa chọn:** Áp dụng kiến trúc ***Layered*** và ***Microservices*** tùy theo phạm vi và độ phức tạp của hệ thống.
  - **Kiến trúc Layered:**  Thích hợp nếu hệ thống chỉ phục vụ một số lượng người dùng nhất định, không yêu cầu mở rộng quá nhiều. *Các tầng*:
    - **User Layer:**: Giao diện người dùng.
    - **Application Layer (Business Logic) :** Xử lý nghiệp vụ
    - **Data Access Layer**: Quản lý giao tiếp với cơ sở dữ liệu.
    - **Database Layer**: Lưu trữ dữ liệu hệ thống.
  - **Kiến trúc Microverse:** Hữu ích nếu hệ thống cần hỗ trợ nhiều người dùng, yêu cầu khả năng mở rộng linh hoạt và xử lý các dịch vụ độc lập. Các dịch vụ sẽ được phân chia thành: dịch vụ chấm công, dịch vụ tính lương, dịch vụ nhân sự, v.v.

# Cơ chế phân tích


# Phân tích *Payment*


# Phân tích *Maintain Timecard*
