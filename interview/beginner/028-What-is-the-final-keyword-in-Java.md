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
