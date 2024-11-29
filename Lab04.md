# Tài liệu thiết kế ca sử dụng - Payroll System

## 1. Tổng quan yêu cầu
Dựa trên kết quả từ **Lab2** (phân tích ca sử dụng) và **Lab3** (phần tử thiết kế), hệ thống cần hỗ trợ các tính năng chính:
1. **Quản lý thông tin nhân viên.**
2. **Quản lý chấm công.**
3. **Tính toán và phê duyệt bảng lương.**
4. **Thanh toán lương qua hệ thống ngân hàng.**
5. **Xem báo cáo lương.**

---

## 2. Actors trong hệ thống
- **Nhân viên (Employee):** Nhận lương, kiểm tra bảng lương cá nhân.
- **Quản lý nhân sự (HR Manager):** Quản lý thông tin nhân viên, ngày công và phê duyệt bảng lương.
- **Kế toán (Accountant):** Xử lý và phê duyệt lương.
- **Hệ thống ngân hàng (Banking System):** Xử lý thanh toán lương.

---

## 3. Danh sách ca sử dụng
### Ca sử dụng chính:
1. **Quản lý thông tin nhân viên**
   - Cập nhật thông tin nhân viên.
   - Xem danh sách nhân viên.

2. **Quản lý chấm công**
   - Ghi nhận ngày công của nhân viên.
   - Xem và chỉnh sửa bảng chấm công.

3. **Tính toán bảng lương**
   - Xác định lương cơ bản.
   - Tính phụ cấp, khấu trừ, lương cuối cùng.
   - Phê duyệt bảng lương.

4. **Thanh toán lương**
   - Gửi dữ liệu thanh toán đến hệ thống ngân hàng.
   - Xác nhận thanh toán thành công.

5. **Xem báo cáo lương**
   - Nhân viên: Xem bảng lương cá nhân.
   - HR Manager: Xem báo cáo tổng hợp lương theo tháng.

---

## 4. Sơ đồ Use Case
![Sơ đồ](https://www.planttext.com/api/plantuml/png/TLHDQzj04BthLmo-X_w34jU414gBQpUbjx9TRQIbgrsn6gM8qdFfiOVUeuPU0gOjv6HHUbZ8_zX_qf6LjQEF-6BmlFVcpPjP7nV8B9QPYfIuG403LYOfGYoju2YDZXX7Os7sCdK_D5nATwDdm0euoN9bAY52_LNfjzSQbFiBUWSjVFDdXpnRlM2Q9S86w7E__KUTNDqfpJatfKQcCG3EVFC5CFNDDvs0Jbgrr5tfP0T_nlI7TLMWoAAezSXqeWJCbgooHYdeIZFu505zoa9mLb1vuRURd9pH5qsPkbjIHgdllHx6Eb-yEyzZXc8_Nq_chSWWPZg5mjKydMA_aUBZDFSqbPq1tSvqLG5lNGJUId1ZupcYqDI0Z_i-uHJ8rxQrRpOCthTn9q0_RdzcVQcJME9ZGg_TXYHsuOEw-trN7sWBfdYfQFJxAFl4PUfk82uhMWs6vWE1UPvRSpbDFoNJ4cBV_08bIQEa9R3W90YioJAnCq6dq1-VqWxPJV0MHbz8cqrJQMDzknHMtMtkuSwMmXP6CxLcYjbgGiFLfcKQGDzy9nNQndK-ZA1LwXHM8ZSMeyzH5Au1ZewUFj9j_qG2Pd23ethloaRLqIsD48CJcTJlpN5uf04oEfSnP70GOy33XH_UzRv3Vwt71AO_gly0)

## 5. Lý do thiết kế các ca sử dụng

1. **Quản lý thông tin nhân viên:**

   - Dữ liệu nhân viên chính xác là nền tảng để tính lương.
   - Đảm bảo quản lý thông tin nhân sự hiệu quả.

2. **Quản lý chấm công:**

   - Chấm công chính xác giúp tính toán lương và các khoản phụ cấp hoặc phạt hợp lý.

3. **Tính toán bảng lương:**

   - Tự động hóa giúp tránh sai sót trong tính toán thủ công.
   - Kế toán phê duyệt để đảm bảo tính minh bạch.

4. **Thanh toán lương:**

   - Đảm bảo quá trình thanh toán lương nhanh chóng, hiệu quả và chính xác qua hệ thống ngân hàng.

5. **Xem báo cáo lương:**

   - Nhân viên kiểm tra thông tin lương cá nhân.
   - HR Manager theo dõi chi phí lương theo tháng hoặc quý.

## 6. Tích hợp và mở rộng

- Hệ thống cần khả năng tích hợp với các dịch vụ ngân hàng hoặc hệ thống quản lý tài chính bên ngoài.
- Dễ dàng mở rộng để thêm các tính năng như quản lý thuế, bảo hiểm xã hội.
