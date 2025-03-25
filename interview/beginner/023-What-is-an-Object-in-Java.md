# Câu hỏi
Đối tượng (Object) trong Java là gì?

# Trả lời ngắn gọn  
Đối tượng (Object) trong Java là một thể hiện cụ thể của một lớp (class). Đối tượng có trạng thái (thuộc tính) và hành vi (phương thức) được định nghĩa bởi lớp.


## Triển khai ý 1: Đối tượng là thể hiện cụ thể của lớp
*	Lớp (class) chỉ là một khuôn mẫu, không có giá trị thực tế.
*	Đối tượng là một thực thể cụ thể được tạo từ lớp, có dữ liệu riêng.

**Ví dụ:**
```java
class Car {
    String brand;  // Thuộc tính
    int speed;

    void showInfo() {  // Phương thức
        System.out.println("Hãng xe: " + brand + ", Tốc độ: " + speed + " km/h");
    }
}

public class Main {
    public static void main(String[] args) {
        Car car1 = new Car();  // Tạo đối tượng từ lớp Car
        car1.brand = "Toyota";
        car1.speed = 120;
        car1.showInfo();  // ✅ Kết quả: Hãng xe: Toyota, Tốc độ: 120 km/h

        Car car2 = new Car();
        car2.brand = "Honda";
        car2.speed = 100;
        car2.showInfo();  // ✅ Kết quả: Hãng xe: Honda, Tốc độ: 100 km/h
    }
}

```
**Nhận xét**: car1 và car2 là hai đối tượng khác nhau của lớp Car, mỗi đối tượng có trạng thái riêng.

## Triển khai ý 2: Đối tượng có thể thao tác dữ liệu và gọi phương thức
*	Một đối tượng có thể gọi các phương thức để thay đổi trạng thái hoặc thực hiện hành động.
*	Java tạo đối tượng bằng từ khóa new, sau đó cấp phát bộ nhớ cho nó.

**Ví dụ đối tượng gọi phương thức để thay đổi dữ liệu:**
```java
class Student {
    String name;
    int age;

    void setInfo(String n, int a) {  // Gán giá trị cho đối tượng
        name = n;
        age = a;
    }

    void display() {
        System.out.println("Tên: " + name + ", Tuổi: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.setInfo("An", 20);
        s1.display();  // ✅ Kết quả: Tên: An, Tuổi: 20

        Student s2 = new Student();
        s2.setInfo("Bình", 22);
        s2.display();  // ✅ Kết quả: Tên: Bình, Tuổi: 22
    }
}

```
**Nhận xét**: Phương thức setInfo() giúp gán giá trị cho đối tượng thay vì gán thủ công.
