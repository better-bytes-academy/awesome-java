# Câu hỏi
Tính trừu tượng (Abstraction) trong Java là gì?

# Trả lời ngắn gọn  
Tính trừu tượng (Abstraction) là một trong bốn tính chất quan trọng của lập trình hướng đối tượng (OOP). Nó cho phép ẩn đi chi tiết triển khai và chỉ hiển thị những thông tin cần thiết cho người dùng. Trong Java, tính trừu tượng được thực hiện thông qua lớp trừu tượng (abstract class) và giao diện (interface).


## Triển khai ý 1: Lớp trừu tượng (abstract class)
*	Một lớp trừu tượng chứa các phương thức có thể có hoặc không có phần thân.
*	Không thể khởi tạo một đối tượng trực tiếp từ lớp trừu tượng.
*	Các lớp con kế thừa phải triển khai các phương thức trừu tượng của lớp cha.

**Ví dụ:**
```java
// Lớp trừu tượng
abstract class Animal {
    // Phương thức trừu tượng (không có phần thân)
    abstract void makeSound();
    
    // Phương thức thông thường
    void eat() {
        System.out.println("Động vật đang ăn...");
    }
}

// Lớp con kế thừa từ lớp trừu tượng và triển khai phương thức makeSound()
class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Gâu gâu!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        myDog.makeSound();  // ✅ Kết quả: "Gâu gâu!"
        myDog.eat();        // ✅ Kết quả: "Động vật đang ăn..."
    }
}

```

**Nhận xét**:
*	Animal là lớp trừu tượng vì nó chứa phương thức makeSound() mà không có phần thân.
*	Dog kế thừa từ Animal và bắt buộc phải triển khai phương thức makeSound().
*	Điều này giúp đảm bảo rằng tất cả các lớp con của Animal đều có phương thức makeSound(), nhưng cách thực hiện có thể khác nhau.


## Triển khai ý 2: Giao diện (interface)
*	Một giao diện chứa chỉ các phương thức trừu tượng (trước Java 8).
*	Lớp triển khai (implements) một giao diện phải triển khai tất cả các phương thức của giao diện đó.
*	Java hỗ trợ một lớp có thể triển khai nhiều giao diện, giúp tăng tính linh hoạt.

**Ví dụ**:
```java
// Giao diện
interface Vehicle {
    void start();
    void stop();
}

// Lớp Car triển khai giao diện Vehicle
class Car implements Vehicle {
    @Override
    public void start() {
        System.out.println("Xe hơi khởi động...");
    }

    @Override
    public void stop() {
        System.out.println("Xe hơi dừng lại...");
    }
}

public class Main {
    public static void main(String[] args) {
        Vehicle myCar = new Car();
        myCar.start();  // ✅ Kết quả: "Xe hơi khởi động..."
        myCar.stop();   // ✅ Kết quả: "Xe hơi dừng lại..."
    }
}


```
**Nhận xét**:
*	Vehicle là một giao diện, chỉ chứa phương thức trừu tượng.
*	Car phải triển khai tất cả các phương thức của Vehicle.
*	Giao diện giúp đảm bảo rằng mọi phương tiện (Vehicle) phải có chức năng start() và stop(), nhưng cách thực hiện sẽ tùy vào từng loại phương tiện.
