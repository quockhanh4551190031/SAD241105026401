# Lab 1: Phân Tích Kiến Trúc, Cơ Chế, Ca Sử Dụng của Payroll System

## Mục đích
Phân tích kiến trúc, cơ chế và ca sử dụng cho hệ thống "Payroll System" theo các yêu cầu đã đưa ra.

## Nội dung

### 1. Phân Tích Kiến Trúc

#### Đề Xuất Kiến Trúc
- **Kiến trúc hệ thống**: Đề xuất sử dụng kiến trúc tầng (Layered Architecture) gồm các tầng chính:
  - **Tầng Giao Diện (UI Layer)**: Cho phép người dùng tương tác với hệ thống.
  - **Tầng Dịch Vụ Ứng Dụng (Application Service Layer)**: Xử lý các logic nghiệp vụ cơ bản.
  - **Tầng Xử Lý Nghiệp Vụ (Business Logic Layer)**: Xử lý các quy trình nghiệp vụ của hệ thống Payroll.
  - **Tầng Dữ Liệu (Data Access Layer)**: Quản lý kết nối và thao tác với cơ sở dữ liệu.

- **Lý do lựa chọn kiến trúc này**:
  - Hệ thống Payroll System cần tính linh hoạt và bảo trì cao.
  - Mỗi tầng thực hiện các chức năng riêng biệt, dễ dàng mở rộng và thay đổi.

#### Biểu Đồ Package Kiến Trúc

![Package Kiến Trúc](https://www.planttext.com/api/plantuml/png/VPD1JiCm44NtaNA7KJQiUW4Mg86og5H41VG0WpEa5euTsKvHXRWx4pSGEsdhNVpdp_kPaPVEe_LTe_AiHV69DK6nMyC6ZsGB-Cupu2CKEWV55e_MABNMdkm72YeITUV8nj9FdaKzoxPLKg2NHiChsOCKT1KorAI8ilDxqdxeCvQagFlEIKrSlp6r55SfMsi4LngRSjvaGm9jzOIQEqv4jZOSuW6Lw1Jwu4q3hD0Zb4A43EVeZqshp95eLJwV1y-40Ngw3xGRU24Lvk3sidNmJlwBI8FgWIxFvjk2nU9kDb-uXSvHNv_kxrHyVk3imL4W1mU9VQHPxnWuZfhj5IcgU-ibqtG34y-5NC4Q3vTj1rIo2YdvFsqSCqhq5tIoMBQBuIjWPwcIh0CGm-APnzJ_iKmRny31vrXWLtkwpBCbwIgyory0 "Package Kiến Trúc")

### 2. Cơ Chế Phân Tích

#### Đề Xuất Cơ Chế Giải Quyết Trong Bài Toán
- **Xử lý phân quyền**: Đảm bảo rằng chỉ người dùng có thẩm quyền mới có thể thực hiện các thao tác nhạy cảm như chỉnh sửa thông tin lương.
- **Quản lý thời gian chấm công**: Theo dõi, quản lý chính xác số giờ làm việc và loại thời gian của từng nhân viên.
- **Xử lý tính toán lương**: Hệ thống cần cơ chế để tính toán lương theo các công thức và quy định khác nhau.

#### Danh Sách Cơ Chế Phù Hợp
1. **Phân quyền người dùng**
2. **Quản lý chấm công và làm thêm giờ**
3. **Tính toán lương và khấu trừ**
4. **Quản lý và lưu trữ lịch sử lương**

### 3. Phân Tích Ca Sử Dụng: Payment

#### Xác Định Các Lớp Phân Tích
- **Lớp `Employee`**: Đại diện cho nhân viên, chứa thông tin cá nhân và thông tin lương.
- **Lớp `Payroll`**: Đảm nhận tính toán và xử lý lương.
- **Lớp `PaymentMethod`**: Xác định phương thức thanh toán, có thể bao gồm chuyển khoản hoặc tiền mặt.
  
#### Biểu Đồ Sequence cho Ca Sử Dụng Payment

![Biểu đồ Sequence](https://www.planttext.com/api/plantuml/png/PP7DQiCm48Jl1h_3afCBoGluK49_eBs5fj2pB6zR4KchhbQ5l7sbs9PBSfxP-MPtzr4KItAsRPGMOdXsmT8PiMr25emsGNc1pK6T7NevC6cCaNW3Aa88Lwvtur0h7Y-gw2lrGVdJ4VdNQBmOXdWBORBs3GEnJ0HkcxPPEi7kFZDxOFn966NkrDtbc50qqJryeRnGulX1VCAnmtdqzIcxHCEkHaXY3z-hTGafgbPM9wi45uHobBnKq11xYEZ7HLufMwZM8LPQc7oFv3yDEoM6VCLnwUoH9zgwVpSFhPbR6BEfbE1_UnJlRN2MbwjL_37fyhnohtqkdv_-1m00 "Biểu đồ Sequence cho Ca Sử dụng Payment")

#### Thuộc Tính và Quan Hệ
- **`Employee`**: Các thuộc tính như `name`, `id`, `position`, `salary`.
- **`Payroll`**: Các thuộc tính như `grossPay`, `deductions`, `netPay`.
  
### 4. Phân Tích Ca Sử Dụng: Maintain Timecard

#### Xác Định Các Lớp Phân Tích
- **Lớp `Employee`**: Đại diện cho nhân viên, liên kết với thẻ chấm công.
- **Lớp `Timecard`**: Chứa thông tin về số giờ làm việc của nhân viên.
- **Lớp `Attendance`**: Xử lý thông tin điểm danh và thời gian làm việc.

#### Biểu Đồ Sequence cho Ca Sử Dụng Maintain Timecard

![Biểu đồ Sequence](https://www.planttext.com/api/plantuml/png/TP312i9034Jl2_iFeVV-W8XKxCM3UAXwZzjK0jrjILE_trr1B5kzpioR2QacHT7PzzQWqq7WEf5OCqQH7OyO58ea7OEITEYeoCmBUt8exGa3FaZ-sVN-72rhKXUKkxmKDj3CTyyA7y2QF9AeV2roD-ovHQKbkOejsNHAsiFdbu4Q5TUJsxBykNaOGiVYKNa8rbGKslS7Nm00 "Biểu đồ Sequence cho Ca sử dụng Maintain Timecard")

#### Thuộc Tính và Quan Hệ
- **`Employee`**: Thuộc tính `id`, `name`.
- **`Timecard`**: Thuộc tính `workHours`, `overtimeHours`.
  
### 5. Hợp Nhất Kết Quả Phân Tích

#### Tổng hợp các lớp chính

1. **UI Layer:**
   - `PayrollInterface`,`UserInterface`.
2. **Application Service Layer:**
   - `PayrollService`,`AuthenticationService`.
3. **Business Logic Layer:**
   - `PayrollProcessor`,`TimecardManager`,`PaymentCalculator`
4. **Data Access Layer:**
   - `EmployeeDAO`,`TimecardDAO`,`PaymentDAO`

