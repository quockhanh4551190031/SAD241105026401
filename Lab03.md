# LAB3: INDENTIFY DESIGN ELEMENTS
### Xác dịnh các phần tử thiết kế của hệ thống "Payroll System"

**1. Subsystem context diagram**

- ***BankSystem:***

    Hệ thống *BankSystem* chịu trách nhiệm xử lý các giao dịch ngân hàng, bao gồm nhận yêu cầu thanh toán từ *PayrollSystem* và giao tiếp với ngân hàng để thực hiện thanh toán hoặc nhận phản hồi.

    ![BankSystem](https://www.planttext.com/api/plantuml/png/P9313S8m34NlcSBgdGKue8e9aCe29XWKaJWbTWwThGT6OWNIgg4L7FtzzFpbz_XgHJ5f3jwWrPYWEU6GelVG3Q8K6a219JA9h2BVFK5pH7viY7MicYdvheofrjrXmy8UEk8hz3W4OeL4pqoYPaCi_4JcIt0Acf2bt72HP-xFU5w18fG-ij2FiPOfKaND0XpLtPp5sTgMIjC_FW000F__0m00 "BankSystem")

  - Interface:

      - **Đầu vào**:
        
          Từ *PayrollSystem*: Yêu cầu thanh toán (bao gồm thông tin nhân viên, số tiền thanh toán, tài khoản đích).

      - **Đầu ra**:
        
          Đến *Bank*: Gửi giao dịch thanh toán

          Đến *PayrollSystem*: Phản hồi trạng thái giao dịch (thành công, thất bại)

  - Dữ liệu trao đổi:

      Thông tin nhân viên, tài khoản ngân hàng, số tiền cần thanh toán
  
- ***PrintService:***

    Hệ thống *PrintService* xử lý yêu cầu in các tài liệu như phiếu lương, báo cáo. Hệ thống này giao tiếp với máy in để thực hiện in ấn và trả về trạng thái hoàn thành cho *PayrollSystem*.

  ![PrintService](https://www.planttext.com/api/plantuml/png/P9313S8m34NldiBgdGLwG9LOe58d2Ab1GMbS71Ufit5W95QWKHEWwj7_l__rvVVprKGrejFWmLXbmQerix3tsCrHQQZGHCmI25aruUffeSG5xKWUpjBA_0dVggIH_7mIWD9_E6uoM6D7eSSnQIXqdoWgR8YI85dWLjXIZ9c_yHcAjozk2uEMXz6JKhzlphDgFAsCuu21rLsSDUc0PfcN_lG1003__mC0 "PrintService")

  - Interface:

      - **Đầu vào**:
        
          Từ *PayrollSystem*: Yêu cầu in tài liệu (thông tin phiếu lương hoặc báo cáo).
      
      - **Đầu ra**:
        
          Đến *Printer*: Gửi dữ liệu cần in.

          Đến *PayrollSystem*: Trạng thái in (hoàn thành, thất bại)

  - Dữ liệu trao đổi:

      Nội dung tài liệu cần in, số lượng bản in

- ***ProjectManagementDatabase:***

  Hệ thống *ProjectManagementDatabase* là cơ sở dữ liệu kế thừa (legacy database), lưu trữ thông tin về các dự án, mã chi phí và các thông tin liên quan. Hệ thống này chỉ cung cấp dữ liệu đọc (read-only) cho *PayrollSystem* để hỗ trợ tính toán và quản lý.

  ![ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/R90n3i8m34NtdCBgpWKw80RMIa1FO5fJ5IKEE0vIpyR0aRW2WHAKIepsV_xVzlF-s0H5qUYimKwzGBN3IRorq4v1oLM00Ruj8zGfyc0fKUBFgMgGSI17h5jKF6AWUQ39PNPTo3_HvB3LkfY16lQHP8BB709z4aoX9xfWM-B-Wu3GDL9GKu8BsmDf5FxdbnUf8Lrs6tk2aKzU7EhesMnInFj5Bm000F__0m00 "ProjectManagementDatabase")

  - Interface:

      - **Đầu vào**:
        
          Từ *PayrollSystem*: Truy vấn thông tin dự án hoặc mã chi phí
        
      - **Đầu ra**:
        
          Trả về dữ liệu được yêu cầu
  
