# Câu hỏi
Có thể tạo một đối tượng từ một abstract class không?

# Trả lời ngắn gọn  
❌ Không thể tạo trực tiếp một đối tượng từ abstract class.

✅ Nhưng có thể tạo đối tượng gián tiếp bằng cách: Kế thừa abstract class và tạo đối tượng từ subclass.


## Triển khai ý 1: Không thể tạo trực tiếp đối tượng từ abstract class
*	Một abstract class có thể chứa phương thức trừu tượng (abstract method) chưa được định nghĩa.
*	Do đó, nếu Java cho phép tạo trực tiếp một đối tượng từ abstract class, nó sẽ không biết phải thực thi phương thức trừu tượng như thế nào.

**Ví dụ gây lỗi**:
```java
abstract class Animal {
    abstract void makeSound(); // Phương thức trừu tượng không có phần thân
}

// ❌ Lỗi: Không thể khởi tạo đối tượng từ abstract class
public class Main {
    public static void main(String[] args) {
        Animal a = new Animal(); // Lỗi biên dịch
    }
}

```

**Kết quả**
```java
Animal is abstract; cannot be instantiated
```

**Nguyên nhân**: Animal là abstract class, không thể khởi tạo trực tiếp.

## Triển khai ý 2: Có thể tạo đối tượng gián tiếp bằng cách kế thừa
*	Tạo một subclass kế thừa từ abstract class.
*	Cài đặt đầy đủ phương thức trừu tượng rồi mới tạo đối tượng.

**Ví dụ hợp lệ**:
```java
abstract class Animal {
    abstract void makeSound(); // Phương thức trừu tượng

    void sleep() { // Phương thức thông thường
        System.out.println("Animal is sleeping");
    }
}

// ✅ Giải quyết bằng cách tạo subclass
class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("Woof! Woof!");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog(); // Tạo đối tượng từ subclass
        a.makeSound(); // Output: Woof! Woof!
        a.sleep();     // Output: Animal is sleeping
    }
}
```
✅ **Lý do hợp lệ**:
*	Dog kế thừa Animal và cung cấp cài đặt cho makeSound().
*	Có thể tạo đối tượng từ Dog, nhưng vẫn sử dụng tham chiếu kiểu Animal


