# Câu hỏi
Từ khóa final trong Java là gì?

# Trả lời ngắn gọn  
final là một từ khóa trong Java được sử dụng để định nghĩa hằng số, ngăn chặn kế thừa hoặc ngăn chặn ghi đè phương thức.
* final với biến: Giá trị không thể thay đổi sau khi gán.
* final với phương thức: Không thể bị ghi đè (override) trong lớp con.
* final với lớp: Không thể bị kế thừa.


## Triển khai ý 1: final với biến – Hằng số
*	Khi khai báo một biến với final, giá trị của nó không thể thay đổi sau khi gán.
*	Nếu biến final là biến đối tượng, tham chiếu của biến không thể thay đổi, nhưng dữ liệu bên trong đối tượng vẫn có thể thay đổi.

**Ví dụ**:
```java
class Example {
    final int MAX_VALUE = 100; // Hằng số

    void show() {
        // MAX_VALUE = 200; // ❌ Lỗi: Không thể gán lại giá trị
        System.out.println("MAX_VALUE: " + MAX_VALUE);
    }
}

public class TestFinal {
    public static void main(String[] args) {
        Example ex = new Example();
        ex.show();
    }
}

```

**Kết quả**
```java
MAX_VALUE: 100
```
**Lưu ý**:
*	Biến MAX_VALUE không thể thay đổi sau khi gán giá trị ban đầu.
*	Nếu là biến instance, giá trị phải được khởi tạo ngay khi khai báo hoặc trong constructor.

## Triển khai ý 2: final với phương thức và lớp
1. final với phương thức – Ngăn ghi đè (override)
* Khi một phương thức được khai báo với final, lớp con không thể ghi đè phương thức đó.

**Ví dụ**:
```java
class Parent {
    final void display() {
        System.out.println("Phương thức final trong lớp cha");
    }
}

class Child extends Parent {
    // void display() { ❌ Lỗi: Không thể override phương thức final
    //     System.out.println("Ghi đè không hợp lệ");
    // }
}

public class TestFinalMethod {
    public static void main(String[] args) {
        Child c = new Child();
        c.display(); // ✅ Gọi phương thức từ lớp cha
    }
}

```
**Kết quả**
```java
Phương thức final trong lớp cha
```
**Lưu ý**:
*	Giúp bảo vệ logic quan trọng không bị thay đổi trong lớp con.
*	Hữu ích trong lập trình framework để ngăn chặn việc ghi đè ngoài ý muốn.

2. final với lớp – Ngăn kế thừa
*	Khi một lớp được khai báo với final, không lớp nào có thể kế thừa nó.

**Ví dụ**:
```java
final class FinalClass {
    void show() {
        System.out.println("Lớp final không thể kế thừa");
    }
}

// class SubClass extends FinalClass { ❌ Lỗi: Không thể kế thừa lớp final
// }

public class TestFinalClass {
    public static void main(String[] args) {
        FinalClass obj = new FinalClass();
        obj.show();
    }
}
```

**Kết quả**
```java
Lớp final không thể kế thừa
```

**Lưu ý**:
*	Thường dùng để bảo vệ các lớp quan trọng, như java.lang.String.
*	Ví dụ: String là một lớp final để đảm bảo tính bất biến.



