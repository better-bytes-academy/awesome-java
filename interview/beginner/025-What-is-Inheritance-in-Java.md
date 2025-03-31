# Câu hỏi
Tính kế thừa (Inheritance) trong Java là gì?

# Trả lời ngắn gọn  
Tính kế thừa (Inheritance) là một trong bốn tính chất của lập trình hướng đối tượng (OOP), cho phép một lớp con (child class) kế thừa các thuộc tính và phương thức từ một lớp cha (parent class). Điều này giúp tái sử dụng mã nguồn, giảm trùng lặp và tăng tính mở rộng của chương trình.


## Triển khai ý 1: Kế thừa giúp tái sử dụng mã nguồn
*	Khi một lớp (child class) kế thừa từ lớp khác (parent class), nó có thể sử dụng lại các thuộc tính và phương thức mà không cần định nghĩa lại.
*	Giảm trùng lặp mã, giúp chương trình dễ bảo trì hơn.

**Ví dụ**
```java
// Lớp cha (Super Class)
class Animal {
    String name;

    void eat() {
        System.out.println(name + " đang ăn...");
    }
}

// Lớp con (Sub Class) kế thừa từ Animal
class Dog extends Animal {
    void bark() {
        System.out.println(name + " sủa gâu gâu!");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.name = "Buddy";
        
        dog.eat();  // ✅ Kế thừa từ lớp cha
        dog.bark(); // ✅ Phương thức riêng của lớp con
    }
}

```
**Nhận xét**:
*	Lớp Dog kế thừa từ Animal, nên tự động có thuộc tính name và phương thức eat().
*	Dog có thể mở rộng thêm phương thức riêng (bark()) mà không làm thay đổi lớp cha.


## Triển khai ý 2: Hỗ trợ đa hình và mở rộng tính năng
*	Lớp con có thể ghi đè (override) phương thức của lớp cha để thay đổi hành vi theo nhu cầu.
*	Giúp chương trình dễ dàng mở rộng mà không làm thay đổi mã nguồn gốc.

**Ví dụ minh họa: Ghi đè phương thức (@Override)**
```java
// Lớp cha
class Animal {
    void makeSound() {
        System.out.println("Động vật phát ra âm thanh...");
    }
}

// Lớp con ghi đè phương thức của lớp cha
class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("Meo meo!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal myCat = new Cat();
        myCat.makeSound();  // ✅ Kết quả: "Meo meo!" (Ghi đè phương thức)
    }
}

```

**Nhận xét**:
*	Cat kế thừa từ Animal, nhưng đã ghi đè (@Override) phương thức makeSound() để có hành vi riêng.
*	Khi gọi makeSound(), chương trình sẽ sử dụng phương thức của Cat thay vì Animal.

