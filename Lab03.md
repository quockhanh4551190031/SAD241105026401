# LAB3: INDENTIFY DESIGN ELEMENTS
### Xác dịnh các phần tử thiết kế của hệ thống "Payroll System"

## **1. Subsystem context diagram**

- ***PrintService:***

    Hệ thống *PrintService* chịu trách nhiệm xử lý các yêu cầu in từ Payroll System. Nó nhận dữ liệu phiếu lương (*Payslip*) từ *PayrollController*, tương tác với máy in để hoàn tất quá trình in, và trả về trạng thái.

  ![PrintService](https://www.planttext.com/api/plantuml/png/h5B1JiCm3BtdAwnnO4XKkrTHDGauJE8mRIUEeHWMAKrAx0uguCiuy4dy0ccRL7IzxlRyx6S_E_dz_baJAyzDPSGbt3ZBtXbH6aK4YwrgGsGYQz0lG17CM92o78AYW0y1i5f1xLs9H5klBU_mjK7YvPNu4c78nZBwPrMYq0d1fY_Sep_g44avriIETPU-TMLJeUMbIWXoIF0QdEsR13yvH1Gdxfj7Qecn2hnxRyVr_iqSDfkQe55MTx9WvU9Ulnpu0OrnRsVmTMTPSx8pQgN4dY-Ac8cYJh53erWxImTTavY_H9OL9xVCWT0-qU0K_F0K14UjnCdHFxDiSW4nINUTayLv9bbSXrdTL_e3003__mC0 "PrintService")

  - Interface:

    - **`IPrintService`**
     
  - **Phương thức:**
    - `printDocument(aDocument: Document, onPrinter: Printer)`:  
      Cho phép hệ thống gửi tài liệu cần in (ví dụ: phiếu lương) đến một máy in cụ thể.

##### Mô tả giao tiếp
- *PayrollController* gửi yêu cầu in thông qua interface *IPrintService*.  
- *IPrintService* được hiện thực bởi hệ thống *PrintService*, nơi xử lý yêu cầu và tương tác trực tiếp với máy in.

##### Dữ liệu trao đổi
- **`Document`**: Tài liệu cần in (ví dụ: phiếu lương).  
- **`Printer`**: Máy in nhận dữ liệu in.

---

- ***ProjectManagementDatabase:***

  Hệ thống *ProjectManagementDatabase* là cơ sở dữ liệu kế thừa chứa thông tin về dự án, mã chi phí và dữ liệu liên quan. *PayrollController* sử dụng hệ thống này để truy vấn thông tin dự án phục vụ tính toán bảng lương.

  ![ProjectManagementDatabase](https://www.planttext.com/api/plantuml/png/f5AzJiCm4Dxz5ASoq0vHzwgoAW5392fLT6Ay9jVKoB63VG4YuCaOU2HU0Rj98qiPkztvFdr_yj_FxyOpEcvhBMxXpXfsLej2e_Smss4NDZsyQd8pG0-JLrYlYtwH4Zu5m789hosvRkVi2nLyZuppXVWMGI4tJEw81GbrcI1FS0Vq5FX6sC1O4G-Wt1pjl1dc4bQmPwTCjGXJGjEBxTk3xpnJ7KyVtHYhnstHO4KrcL6uZxTDVFYHeOaCmStDewfE_4nQs_Shh3qOLdnnb5o39frFKaRO4sbaPOq_gSQBQVDP9gVrhSxjA_9GHiOtXM9QyLUM9L55aZfofdutPChuFVu1003__mC0 "ProjectManagementDatabase")

  - Interface:

    - **`IProjectDatabase`**
  - **Phương thức:**
    - `getProjectInfo(projectId: String): ProjectData`:  
      Lấy thông tin chi tiết về một dự án dựa trên mã dự án.

##### Mô tả giao tiếp
- *PayrollController* gửi truy vấn thông qua interface *IProjectDatabase*.  
- *IProjectDatabase* được hiện thực bởi hệ thống *ProjectManagementDatabase*, nơi cung cấp thông tin cần thiết.

##### Dữ liệu trao đổi
- **`ProjectData`**: Dữ liệu dự án, bao gồm thông tin mã dự án, chi phí, và tiến độ.

----

## **2. Analysis class to design element map**

# Mapping Analysis Classes to Design Elements

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

# Mapping Design Elements to Owning Packages

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
