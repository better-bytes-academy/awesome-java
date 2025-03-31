# Câu hỏi
Tính đa hình (Polymorphism) trong Java là gì?

# Trả lời ngắn gọn  
Tính đa hình (Polymorphism) là một trong bốn tính chất của lập trình hướng đối tượng (OOP), cho phép một phương thức có thể có nhiều cách thực hiện khác nhau, tùy thuộc vào ngữ cảnh. Trong Java, tính đa hình có hai dạng chính: đa hình tại thời điểm biên dịch (compile-time polymorphism) và đa hình tại thời điểm chạy (runtime polymorphism).


## Triển khai ý 1: Đa hình tại thời điểm biên dịch (Method Overloading)
*	Khi một lớp có nhiều phương thức cùng tên nhưng khác nhau về số lượng hoặc kiểu tham số.
*	Điều này giúp tăng tính linh hoạt mà không cần tạo nhiều tên phương thức khác nhau.

**Ví dụ**:
```java
class MathUtils {
    // Phương thức tính tổng hai số nguyên
    int sum(int a, int b) {
        return a + b;
    }

    // Phương thức tính tổng ba số nguyên
    int sum(int a, int b, int c) {
        return a + b + c;
    }

    // Phương thức tính tổng hai số thực
    double sum(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        MathUtils math = new MathUtils();
        
        System.out.println(math.sum(2, 3));       // ✅ Gọi sum(int, int)
        System.out.println(math.sum(2, 3, 4));    // ✅ Gọi sum(int, int, int)
        System.out.println(math.sum(2.5, 3.5));   // ✅ Gọi sum(double, double)
    }
}

```
**Nhận xét**:
*	Phương thức sum() có nhiều phiên bản (overloading) với số lượng tham số và kiểu dữ liệu khác nhau.
*	Trình biên dịch xác định phương thức nào sẽ được gọi dựa trên kiểu dữ liệu của đối số.

## Triển khai ý 2: Đa hình tại thời điểm chạy (Method Overriding)
*	Khi một lớp con (child class) ghi đè (@Override) phương thức của lớp cha (parent class).
*	Giúp lớp con có thể thay đổi hành vi của phương thức mà nó kế thừa.

**Ví dụ**:
```java
// Lớp cha
class Animal {
    void makeSound() {
        System.out.println("Động vật phát ra âm thanh...");
    }
}

// Lớp con ghi đè phương thức của lớp cha
class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Gâu gâu!");
    }
}

// Lớp con khác ghi đè phương thức của lớp cha
class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Meo meo!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myDog = new Dog();
        Animal myCat = new Cat();
        
        myDog.makeSound();  // ✅ Kết quả: "Gâu gâu!"
        myCat.makeSound();  // ✅ Kết quả: "Meo meo!"
    }
}

```
**Nhận xét**:
*	Dog và Cat kế thừa từ Animal, nhưng mỗi lớp ghi đè (@Override) phương thức makeSound() theo cách riêng.
*	Khi gọi makeSound(), Java sẽ thực thi phương thức phù hợp với đối tượng thực tế (Dog hoặc Cat).
