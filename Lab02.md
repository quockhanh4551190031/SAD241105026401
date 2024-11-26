# LAB2: Phân tích và mô phỏng hệ thống **Payroll System**

## **1. Phân tích các ca sử dụng trong hệ thống Payroll System**
### **1.1 Các ca sử dụng chính**
1. **Maintain Timecard (Quản lý bảng chấm công):**
   - **Chức năng:** Cho phép nhân viên tạo hoặc cập nhật bảng chấm công.
   - **Tương tác chính:**
     - Nhân viên nhập giờ làm việc.
     - Lấy dữ liệu charge codes từ hệ thống **Project Management Database**.
     - Lưu bảng chấm công.

2. **Generate Paycheck (Tạo bảng lương):**
   - **Chức năng:** Tính toán và tạo bảng lương dựa trên thông tin bảng chấm công của nhân viên.
   - **Tương tác chính:**
     - Thu thập thông tin bảng chấm công từ nhân viên.
     - Tính toán tiền lương.
     - Lưu thông tin vào hệ thống **Paycheck**.

3. **Manage Employee Records (Quản lý hồ sơ nhân viên):**
   - **Chức năng:** Quản lý thông tin nhân viên (thêm, sửa, xóa hồ sơ).
   - **Tương tác chính:**
     - Truy xuất thông tin từ cơ sở dữ liệu.
     - Cập nhật hồ sơ cá nhân nhân viên.
     - Lưu thay đổi vào cơ sở dữ liệu.

4. **Process Direct Deposit (Xử lý tiền gửi trực tiếp):**
   - **Chức năng:** Gửi tiền lương đến tài khoản ngân hàng của nhân viên.
   - **Tương tác chính:**
     - Trích xuất thông tin bảng lương từ **Paycheck**.
     - Gửi thông tin đến hệ thống ngân hàng (**BankSystem**).

---

## **2. Mô phỏng Java cho ca sử dụng Maintain Timecard**

### **2.1 Mã Java**

```java
import java.util.HashMap;
import java.util.Map;

class Timecard {
    private Map<String, Double> chargeHours; // Lưu thông tin mã charge và số giờ làm việc.

    public Timecard() {
        this.chargeHours = new HashMap<>();
    }

    // Thêm hoặc cập nhật giờ làm việc cho mã charge.
    public void updateHours(String chargeCode, double hours) {
        chargeHours.put(chargeCode, hours);
    }

    // Hiển thị thông tin bảng chấm công.
    public void display() {
        System.out.println("Timecard Details:");
        for (Map.Entry<String, Double> entry : chargeHours.entrySet()) {
            System.out.println("Charge Code: " + entry.getKey() + ", Hours: " + entry.getValue());
        }
    }

    // Lưu bảng chấm công (giả lập việc lưu vào cơ sở dữ liệu).
    public void save() {
        System.out.println("Timecard has been saved successfully!");
    }
}

class TimecardController {
    private Timecard currentCard;

    public TimecardController() {
        this.currentCard = new Timecard(); // Tạo mới nếu chưa tồn tại.
    }

    // Lấy bảng chấm công hiện tại.
    public Timecard getCurrentTimecard() {
        return currentCard;
    }

    // Hiển thị bảng chấm công.
    public void displayTimecard() {
        currentCard.display();
    }

    // Nhập giờ làm việc và lưu bảng chấm công.
    public void maintainTimecard(String chargeCode, double hours) {
        System.out.println("Updating hours for Charge Code: " + chargeCode);
        currentCard.updateHours(chargeCode, hours);
    }

    // Lưu bảng chấm công.
    public void saveTimecard() {
        currentCard.save();
    }
}

public class PayrollSystem {
    public static void main(String[] args) {
        TimecardController controller = new TimecardController();

        // Hiển thị bảng chấm công (ban đầu trống).
        controller.displayTimecard();

        // Thêm giờ làm việc cho charge codes.
        controller.maintainTimecard("CHG001", 8.0);
        controller.maintainTimecard("CHG002", 4.5);

        // Hiển thị bảng chấm công đã cập nhật.
        controller.displayTimecard();

        // Lưu bảng chấm công.
        controller.saveTimecard();
    }
}
