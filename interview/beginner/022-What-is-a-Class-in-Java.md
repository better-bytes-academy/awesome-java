# Câu hỏi
Thế nào là lớp (Class) trong Java?

# Trả lời ngắn gọn  
Lớp (Class) trong Java là một khuôn mẫu (blueprint) để tạo ra các đối tượng (objects). Một lớp định nghĩa các thuộc tính (dữ liệu) và phương thức (hành vi) của đối tượng.

## Triển khai ý 1: Lớp là khuôn mẫu để tạo đối tượng
Lớp giúp tổ chức mã nguồn theo cách có cấu trúc, trong đó:
*	Thuộc tính (fields): Lưu trữ trạng thái của đối tượng.
*	Phương thức (methods): Xác định hành vi của đối tượng.
*	
 **Ví dụ**:
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
        Car myCar = new Car();  // Tạo đối tượng từ lớp Car
        myCar.brand = "Toyota";
        myCar.speed = 120;
        myCar.showInfo();  // ✅ Kết quả: Hãng xe: Toyota, Tốc độ: 120 km/h
    }
}

```
**Nhận xét**: Lớp Car định nghĩa thuộc tính brand và speed, cùng phương thức showInfo(). Đối tượng myCar được tạo từ lớp Car và sử dụng các thành phần của nó.

## Triển khai ý 2: Lớp giúp tái sử dụng mã nguồn và tổ chức chương trình tốt hơn
*	Dễ dàng mở rộng bằng kế thừa.
*	Giúp quản lý nhiều đối tượng có cùng kiểu dữ liệu

**Ví dụ mở rộng lớp bằng constructor**:
```java
class Student {
    String name;
    int age;

    // Constructor
    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void display() {
        System.out.println("Tên: " + name + ", Tuổi: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("An", 20);
        Student s2 = new Student("Bình", 22);

        s1.display();  // ✅ Kết quả: Tên: An, Tuổi: 20
        s2.display();  // ✅ Kết quả: Tên: Bình, Tuổi: 22
    }
}

```
**Nhận xét**: Constructor giúp khởi tạo đối tượng dễ dàng hơn thay vì gán từng giá trị riêng lẻ.




