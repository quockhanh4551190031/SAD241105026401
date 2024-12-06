# Thiết kế hệ thống con - Payroll System

## 1. Giới thiệu
Dựa trên kết quả từ bài Lab4 về thiết kế ca sử dụng, hệ thống **Payroll System** được chia thành các hệ thống con nhằm mục tiêu tổ chức, tái sử dụng, và dễ dàng bảo trì. Dưới đây là danh sách và chi tiết thiết kế các hệ thống con.

---

## 2. Hệ thống con

### 2.1 Hệ thống con quản lý nhân viên (Employee Management Subsystem)
**Chức năng:**
- Quản lý thông tin nhân viên (thêm, sửa, xóa, xem).
- Lưu trữ và truy xuất thông tin nhân viên từ cơ sở dữ liệu.

**Thành phần:**
- **Entity:** `Employee`
- **Database Manager:** `PayrollDBManager`
- **Controller:** `EmployeeController`

---

### 2.2 Hệ thống con quản lý chấm công (Timecard Management Subsystem)
**Chức năng:**
- Ghi nhận giờ làm việc của nhân viên.
- Chỉnh sửa và lưu thông tin chấm công.
- Hiển thị bảng chấm công theo kỳ.

**Thành phần:**
- **Entity:** `Timecard`
- **Database Manager:** `PayrollDBManager`
- **Controller:** `TimecardController`
- **Form:** `TimecardForm`

---

### 2.3 Hệ thống con xử lý bảng lương (Payroll Processing Subsystem)
**Chức năng:**
- Tính toán lương dựa trên thời gian làm việc, phụ cấp, khấu trừ.
- Quản lý bảng lương theo kỳ trả lương.
- Lưu trữ và hiển thị thông tin bảng lương.

**Thành phần:**
- **Entity:** `Paycheck`
- **Database Manager:** `PayrollDBManager`
- **Controller:** `PayrollController`

---

### 2.4 Hệ thống con thanh toán lương (Payment Subsystem)
**Chức năng:**
- Gửi yêu cầu thanh toán đến hệ thống ngân hàng.
- Xác nhận trạng thái giao dịch thanh toán.

**Thành phần:**
- **Interface:** `IBankSystem`
- **Service:** `BankingService`

---

### 2.5 Hệ thống con bảo mật và xác thực (Authentication and Security Subsystem)
**Chức năng:**
- Xác thực người dùng qua tài khoản và mật khẩu.
- Cung cấp phiên làm việc an toàn.
- Quản lý quyền truy cập theo vai trò.

**Thành phần:**
- **Form:** `LoginForm`
- **Entity:** `ISecureUser`, `EmployeeSession`
- **Controller:** `SecurityController`

---

### 2.6 Hệ thống con báo cáo (Reporting Subsystem)
**Chức năng:**
- Tổng hợp và hiển thị báo cáo lương theo tháng/quý.
- Hiển thị bảng lương chi tiết cho từng nhân viên.

**Thành phần:**
- **Controller:** `ReportController`
- **Interface:** `IReportService`

---

## 3. Sơ đồ hệ thống con
Dưới đây là sơ đồ UML thể hiện các hệ thống con và mối quan hệ phụ thuộc giữa chúng.
![Sơ đồ](https://www.planttext.com/api/plantuml/png/d5PBRjim4Dtx58HN2X1VG2YAD9y20LeqY5DqFQOc3cjA54ZAXLhaP5tqIBr2X_gBecIdMWIn-1xvvis7-llxpvMne6sHobKE_01xPEi7ABMIacrBOp5TiryhHa-tV9VcKfM8x3Daz2B5pB9jiJCZj7ku16DO1-yNtBDX6QGOiwtL8jjxIzXmxfEOYSnwgxaomWgLJSYlCqVVgCowY51x8XY396bH4PqQTvoBc1sLI3nuaITWyIsC12ME6KrGOVWURHZRllM2VLsDa_CaKkIWapEJqy7zvBoeGfjlIX-G53nB1PCaGFc0MYXQlYLBPdFGdh2SWnOLMHvtbAKKl850bdRetj9BbW_aN_IRd8paezBf98P4c5n2wTQYi0pA1EfEY8y9PxFjn0UjE1f3jRwKJ4Bp5-I7IJ8XLKLcP_Fe33YHnKR8GX8vI5v8sgE1BbdT2lNh8C-rEWOsEDki-N8NplrduCZkho4xrADjcaMiPaiqCkoI0UVrxthUa9oTKdBMB7S0mRQeZuBxSuy4rybiv4PvOqPlotdXVYZi2_451pSB6MG9so8ljB3bKf5yKdkHBPLm1PYfuID8uRhlHcFYpWPfeiAW7evooZQTyqFfvBHVWwnKsl6h2PGMDR1x_wWaEbqdXdvhmaAjoYh4iuGFTFdLIluhBNvYjT48wIfcU4653V0J-aZ5f-s97gz12x7jCKCzkADgmb8t1cxWVfkc6RT5ce8kesLgCB6rWBbcQCzfP59nmS2rCzg0bC0E30R7ePD-UrrVXLEh31pfagKojcNClko-8v-_b1lSKvbJlTou_I_P0OUy-f-9MlSty1sosRpllunYjauhZMPTuGDtfiDtbxMFdqvd1--k0uAtDYyI0iSIbQfxaHK8RiJofg6Z34SmOGNjK7sfD8n01rUimOZm7PYqHME0fpSKJbyVxpQRaz44IMSQDoRzZxf9c1tbTNM5MU8-u_y1003__mC0 "Sơ đồ hệ thống con")
