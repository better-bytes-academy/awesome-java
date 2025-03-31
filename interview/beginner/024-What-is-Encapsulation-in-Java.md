# Câu hỏi
Tính đóng gói (Encapsulation) trong Java là gì?

# Trả lời ngắn gọn  
Tính đóng gói (Encapsulation) là một trong bốn tính chất của lập trình hướng đối tượng (OOP), giúp bảo vệ dữ liệu bằng cách che giấu thông tin bên trong lớp và chỉ cho phép truy cập thông qua các phương thức đặc biệt.

 
## Triển khai ý 1: Đóng gói giúp ẩn dữ liệu và kiểm soát truy cập
*	Dữ liệu của đối tượng (thuộc tính) được khai báo là private để không thể truy cập trực tiếp từ bên ngoài.
*	Cung cấp các phương thức getter và setter để truy cập hoặc thay đổi dữ liệu một cách có kiểm soát.
*	Giúp bảo mật thông tin và tránh việc thay đổi giá trị không mong muốn.

**Ví dụ**
```java
class Person {
    private String name;  // Thuộc tính bị đóng gói (private)
    private int age;

    // Constructor để khởi tạo đối tượng
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter để lấy giá trị
    public String getName() {
        return name;
    }

    public int getAge() {
        return age;
    }

    // Setter để cập nhật giá trị
    public void setAge(int age) {
        if (age > 0) {  // Kiểm tra hợp lệ trước khi thay đổi
            this.age = age;
        } else {
            System.out.println("Tuổi không hợp lệ!");
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person("An", 20);
        
        System.out.println("Tên: " + p.getName());  // ✅ Truy cập dữ liệu thông qua getter
        System.out.println("Tuổi: " + p.getAge());

        p.setAge(25);  // ✅ Cập nhật dữ liệu thông qua setter
        System.out.println("Tuổi mới: " + p.getAge());

        p.setAge(-5);  // ❌ In ra lỗi vì tuổi không hợp lệ
    }
}

```

**Nhận xét**:
*	Thuộc tính name và age bị đóng gói (private) => Không thể truy cập trực tiếp từ ngoài lớp.
*	Phương thức getName(), getAge() giúp đọc dữ liệu an toàn.
*	Phương thức setAge() giúp kiểm soát và đảm bảo dữ liệu hợp lệ trước khi thay đổi.

## Triển khai ý 2: Đóng gói giúp dễ bảo trì và mở rộng
*	Khi cần thay đổi logic xử lý dữ liệu, chỉ cần sửa trong lớp mà không ảnh hưởng đến nơi sử dụng.
*	Giúp mã nguồn dễ hiểu, gọn gàng, dễ bảo trì và mở rộng.

**Ví dụ: Thêm điều kiện kiểm tra dữ liệu**
```java
public void setName(String name) {
    if (name.length() > 2) { 
        this.name = name;
    } else {
        System.out.println("Tên quá ngắn!");
    }
}

```
**Nhận xét**: Nhờ đóng gói, ta có thể thêm logic kiểm tra mà không cần sửa tất cả chương trình.
