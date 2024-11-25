# LAB3: INDENTIFY DESIGN ELEMENTS
### Xác dịnh các phần tử thiết kế của hệ thống "Payroll System"

## **1. Subsystem context diagram**

- ***BankSystem:***

    Hệ thống con BankSystem là một phần của hệ thống Payroll System. Nó chịu trách nhiệm xử lý các giao dịch tài chính liên quan đến việc trả lương cho nhân viên. Cụ thể, hệ thống này thực hiện các chức năng chính sau:

1. **Nhận chỉ thị thanh toán (Payment Instructions):**
   - Nhận yêu cầu thanh toán từ **Payroll System**, bao gồm các thông tin như:
     - Số tiền thanh toán.
     - Tài khoản ngân hàng của người nhận.
     - Các chi tiết giao dịch liên quan.

2. **Xử lý thanh toán (Payment Processing):**
   - Xác thực thông tin giao dịch.
   - Thực hiện giao dịch qua ngân hàng.

3. **Cung cấp số dư tài khoản (Account Balance):**
   - Cung cấp thông tin số dư tài khoản cho các hệ thống liên quan để báo cáo và kiểm tra.

4. **Gửi sao kê ngân hàng (Bank Statements):**
   - Tạo sao kê chi tiết về các giao dịch đã xử lý.
   - Gửi sao kê đến các hệ thống khác, như dịch vụ in ấn (PrintService).

![BankSystem](https://www.planttext.com/api/plantuml/png/pLEnJiCm4Dqj-H-iCj0CKVSgYaeHGoI6YaoCnhYjXMD7lWiG0V-ExP8qRWipsvtzxkwzy_CAa3li6at9DRkr1ftreT0SWCqslFUfhdj0sSmO1vQSiA8GXugoP1-KCBPOC93cEU8QQP1L1j1r0fKrGCaN9M5CPL2wBHUI4ZM4h5fpyr9BzwfyKXGZPcZTEYiam4_ZEPzqPijXtkGm2qKxYJT2sCxWccjkX9nd7fmU1LmWNIFtccBlCVJWI6l8ir53tJt1OGaRPz_xSMKHVjpNCVMQOAnfGurNTdMlTdjyb5hRjtyfyywWmb7T-NYlIaP8MPw0l9UsoZNy5rHAxW8W8PJS1ruFKiVEi5UjDrPgopmlKpij_tHbwhpFF9-y6YMJ5mnzBwWxmvmk_kGwKKR9obEB_-yR "BankSystem")

- **Interface:**
  
    - **`IBankService`** là giao diện trung gian để các hệ thống khác tương tác với **BankSystem**.
      
- **Phương thức:**

    - `processPayment(aInstruction: PaymentInstruction)`: Xử lý các chỉ thị thanh toán
    - `getAccountBalance(): AccountBalance`: Lấy số dư tài khoản hiện tại
    - `sendStatement(aStatement: BankStatement)`: Gửi sao kê chi tiết các giao dịch đã thực hiện.
    
**Mô tả giao tiếp:**

- *aInstruction*: Đối tượng chứa thông tin chỉ thị thanh toán
- *processPayment(aInstruction: PaymentInstruction)* Trả về một đối tượng xác nhận thanh toán (`PaymentConfirmation`), bao gồm trạng thái giao dịch (thành công hoặc thất bại).
- *getAccountBalance(): AccountBalance* Trả về một đối tượng số dư tài khoản (`AccountBalance`) để phục vụ mục đích báo cáo hoặc kiểm tra.
- *aStatement*: Đối tượng chứa thông tin sao kê ngân hàng.
- *sendStatement(aStatement: BankStatement)* Được gửi tới các dịch vụ như **PrintService** để in ấn hoặc lưu trữ.

**Dữ liệu trao đổi:**

- **`PaymentInstruction`**: Được gửi từ hệ thống **Payroll System** đến ***BankSystem***.

   Chứa thông tin chi tiết về giao dịch cần thực hiện, bao gồm:
    - Tên người nhận.
    - Số tài khoản ngân hàng của người nhận.
    - Số tiền cần thanh toán.
    - Ngày giao dịch.
    - Mã giao dịch (Transaction ID).
    
- **`PaymentConfirmation`**: Được tạo bởi ***BankSystem*** và gửi trả về hệ thống **Payroll System**.

  Chứa kết quả của giao dịch, bao gồm:
    - Trạng thái giao dịch (thành công, thất bại).
    - Mã giao dịch (Transaction ID).
    - Thời gian xử lý giao dịch.
    - Thông báo lỗi (nếu có).

- **`AccountBalance`**: Được lấy từ cơ sở dữ liệu ngân hàng trong ***BankSystem*** và cung cấp cho các hệ thống liên quan (như Financial Management System).

  Chứa thông tin về số dư tài khoản, bao gồm:
    - Số dư hiện tại.
    - Số dư khả dụng.
    - Lịch sử thay đổi số dư (nếu có).
 
- **`BankStatement`**: Được tạo bởi ***BankSystem*** sau khi xử lý giao dịch.

  Chứa thông tin chi tiết về các giao dịch đã thực hiện, bao gồm:
    - Danh sách các giao dịch (ngày, số tiền, trạng thái).
    - Tên tài khoản và số tài khoản liên quan.
    - Tổng kết số dư đầu kỳ và cuối kỳ.
 
- **`ErrorReport`**: Được tạo bởi ***BankSystem*** khi xảy ra sự cố trong quá trình xử lý giao dịch.

  Chứa thông tin về lỗi, bao gồm:
    - Mã lỗi (Error Code).
    - Mô tả lỗi (Error Description).
    - Thời gian xảy ra lỗi.
    - Các bước xử lý đề xuất (nếu có).
  
<hr style="border:2px solid gray">

- ***PrintService:***

    Hệ thống *PrintService* chịu trách nhiệm xử lý các yêu cầu in từ Payroll System. Nó nhận dữ liệu phiếu lương (*Payslip*) từ *PayrollController*, tương tác với máy in để hoàn tất quá trình in, và trả về trạng thái.

  ![PrintService](https://www.planttext.com/api/plantuml/png/h5B1JiCm3BtdAwnnO4XKkrTHDGauJE8mRIUEeHWMAKrAx0uguCiuy4dy0ccRL7IzxlRyx6S_E_dz_baJAyzDPSGbt3ZBtXbH6aK4YwrgGsGYQz0lG17CM92o78AYW0y1i5f1xLs9H5klBU_mjK7YvPNu4c78nZBwPrMYq0d1fY_Sep_g44avriIETPU-TMLJeUMbIWXoIF0QdEsR13yvH1Gdxfj7Qecn2hnxRyVr_iqSDfkQe55MTx9WvU9Ulnpu0OrnRsVmTMTPSx8pQgN4dY-Ac8cYJh53erWxImTTavY_H9OL9xVCWT0-qU0K_F0K14UjnCdHFxDiSW4nINUTayLv9bbSXrdTL_e3003__mC0 "PrintService")

  - Interface:

    - **`IPrintService`**: là giao diện trung gian dùng để các hệ thống tương tác với ***PrintService***.
     
  - **Phương thức:**
    - `printDocument(aDocument: Document, onPrinter: Printer)`:  
      Cho phép hệ thống gửi tài liệu cần in (ví dụ: phiếu lương) đến một máy in cụ thể.

**Mô tả giao tiếp**
- *PayrollController* gửi yêu cầu in thông qua interface *IPrintService*.  
- *IPrintService* được hiện thực bởi hệ thống *PrintService*, nơi xử lý yêu cầu và tương tác trực tiếp với máy in.

**Dữ liệu trao đổi**
- **`Document`**: Tài liệu cần in (ví dụ: phiếu lương).  
- **`Printer`**: Máy in nhận dữ liệu in.

<hr style="border:2px solid gray">

- ***ProjectManagementDatabase:***

  Hệ thống *ProjectManagementDatabase* là cơ sở dữ liệu kế thừa chứa thông tin về dự án, mã chi phí và dữ liệu liên quan. *PayrollController* sử dụng hệ thống này để truy vấn thông tin dự án phục vụ tính toán bảng lương.

  ![ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/f5AzJiCm4Dxz5ASoq0vHzwgoAW5392fLT6Ay9jVKoB63VG4YuCaOU2HU0Rj98qiPkztvFdr_yj_FxyOpEcvhBMxXpXfsLej2e_Smss4NDZsyQd8pG0-JLrYlYtwH4Zu5m789hosvRkVi2nLyZuppXVWMGI4tJEw81GbrcI1FS0Vq5FX6sC1O4G-Wt1pjl1dc4bQmPwTCjGXJGjEBxTk3xpnJ7KyVtHYhnstHO4KrcL6uZxTDVFYHeOaCmStDewfE_4nQs_Shh3qOLdnnb5o39frFKaRO4sbaPOq_gSQBQVDP9gVrhSxjA_9GHiOtXM9QyLUM9L55aZfofdutPChuFVu1003__mC0 "ProjectManagementDatabase")

  - Interface:

    - **`IProjectDatabase`**: là giao diện trung gian để tương tác với các hệ thống trong ***ProjectManagementDatabase***
      
  - **Phương thức:**
    - `getProjectInfo(projectId: String): ProjectData`:  
      Lấy thông tin chi tiết về một dự án dựa trên mã dự án.

**Mô tả giao tiếp**
- *PayrollController* gửi truy vấn thông qua interface *IProjectDatabase*.  
- *IProjectDatabase* được hiện thực bởi hệ thống *ProjectManagementDatabase*, nơi cung cấp thông tin cần thiết.

**Dữ liệu trao đổi**
- **`ProjectData`**: Dữ liệu dự án, bao gồm thông tin mã dự án, chi phí, và tiến độ.

----

## **2. Analysis class to design element map**

### Mapping Analysis Classes to Design Elements

| **Analysis Class**          | **Design Element**               | **Description** |
|-----------------------------|----------------------------------|-----------------|
| **PayrollController**        | Controller                       | Coordinates the processing of requests in the system.      |
| **Employee**                 | Entity                           | Represents employee data and information.                  |
| **Payslip**                  | Entity                           | Represents employee payslips, storing payment details and salary breakdowns.   |
| **Printer**                  | Entity                           | Represents the printer for handling print jobs.            |
| **PrintService**             | Subsystem Proxy                  | Subsystem responsible for handling print requests from the Payroll System. |
| **BankSystem**               | Subsystem Proxy                  | Subsystem responsible for processing banking transactions. |
| **ProjectManagementDatabase**| Subsystem Proxy                  | Subsystem providing project and charge code information.   |
| **IPrintService**            | Interface                        | Interface providing printing functionalities in the system. |
| **IProjectDatabase**         | Interface                        | Interface providing functionalities to query project information. |

## **3. Design element to owning package map**

### Mapping Design Elements to Owning Packages

| **Design Element**              | **Owning Package**      |                                                                
|----------------------------------|-------------------------|
| **PayrollController**            | `controller`            | 
| **Employee**                     | `entity`                | 
| **Payslip**                      | `entity`                |
| **Printer**                      | `entity`                |
| **PrintService**                 | `subsystem.print`       | 
| **BankSystem**                   | `subsystem.bank`        |
| **ProjectManagementDatabase**    | `subsystem.database`    | 
| **IPrintService**                | `interfaces`            | 
| **IProjectDatabase**             | `interfaces`            | 

## **4. Architectural layers and their dependencies**

![Layers](https://www.planttext.com/api/plantuml/png/b9I_Rjim4CPtFSNL7Je5sOt0o5zaSGAZyTBnJD4I6ufaICgjK6Jkt4VeK7GgiiT3Xpo9dg2lq2CbHKegDyXcMtVVT_UxJ_wp_NteF5fV5Z9va_ArK1pUdvqiZoxFvsV093gNl8DbVVzJPN0kK4CgwkrNbHXarvXnc2miTrnvz48hc6F5xGI-931GcIomibfAED7AXm-XvE20DTzcirWEiByFEQfKSZ1jlUKt9NVUqUFRPufMA7_5xKOm7hHSkNALyxm0O_NdYZJVpaMM-mzSIlsfDp2XB-WxAOm3iYCJesthSPlqorvcUTZKmARU_kZNFIuTCN8EvZeJx8M55rOpgjMxzcKeMIdHSt0eqLPn8DCqFLAGmMW4GGUrrI3ymOLE8NmrD37ShhKj7iseq07zqXdyi_dIbXMm-lwNWTDwUmSoS2Xx1AVe4OvO779y_sDKrrVn7gyvJe4gwA-e6Rn5vP35OSVEhpzovYzYGq4hXv5Mw5wLXIviZLP4ptAqD07JAHy4ugBUVXDmKwA2d4X0HZpk4DZ3TmO-8aj68xwtDnkDmXHAH_hFGhoxcbwlrBNHRL-9PAmoAWpHJsbeRWLlpZr02aAjzMwD_-3j9JjkZTJGziacJ-8vxS9D_V7C5C6W7s7iz7n1RoFImJWfjIM7H2pye_q5003__mC0 "Layers")
