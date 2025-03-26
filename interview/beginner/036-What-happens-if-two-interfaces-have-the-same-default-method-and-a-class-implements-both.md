# Câu hỏi
Nếu hai interface có cùng một phương thức mặc định (default method), điều gì sẽ xảy ra khi một class implements cả hai?

# Trả lời ngắn gọn  
⚠ Lỗi xung đột phương thức xảy ra nếu một class implements hai interface có cùng phương thức mặc định (default method).

✅ Cách giải quyết:
1.	Override phương thức trong class để giải quyết xung đột.
2.	Gọi phương thức cụ thể từ một interface bằng InterfaceName.super.methodName().


## Triển khai ý 1: Lỗi xung đột khi hai interface có cùng default method
**Giải thích**:	Nếu cả hai interface có cùng một phương thức mặc định (default method), khi một class implements cả hai, Java không biết dùng phương thức nào → gây lỗi.

**Ví dụ gây lỗi xung đột:**
```java
interface A {
    default void show() {
        System.out.println("Interface A");
    }
}

interface B {
    default void show() {
        System.out.println("Interface B");
    }
}

// ❌ Lỗi: Xung đột phương thức
class MyClass implements A, B {
    // Không override -> lỗi
}

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.show();
    }
}

```
**Kết quả**
```java
class MyClass inherits unrelated defaults for show() from types A and B
```

**Nguyên nhân**: MyClass không biết nên dùng show() từ A hay B.


## Triển khai ý 2: Giải quyết xung đột bằng cách override phương thức
**Cách giải quyết**:
*	Override phương thức trong MyClass để chọn cách thực hiện.
*	Có thể gọi một phương thức cụ thể từ interface bằng InterfaceName.super.methodName().

**Ví dụ hợp lệ**:
```java
interface A {
    default void show() {
        System.out.println("Interface A");
    }
}

interface B {
    default void show() {
        System.out.println("Interface B");
    }
}

// ✅ Giải quyết xung đột bằng override
class MyClass implements A, B {
    @Override
    public void show() {
        System.out.println("Class MyClass is resolving conflict");
        A.super.show(); // Gọi phương thức từ interface A
    }
}

public class Main {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        obj.show();
    }
}

```

**Kết quả**
```java
Class MyClass is resolving conflict
Interface A
```

**Lý do hợp lệ**:
*	MyClass override show(), tránh xung đột.
*	A.super.show(); giúp gọi phương thức cụ thể từ A.




