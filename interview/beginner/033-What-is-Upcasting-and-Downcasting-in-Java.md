# Câu hỏi
Upcasting và Downcasting trong Java là gì?

# Trả lời ngắn gọn  
Upcasting và Downcasting là hai loại ép kiểu (type casting) trong Java khi làm việc với kế thừa.
*	Upcasting: Ép kiểu từ lớp con lên lớp cha (an toàn, tự động hoặc tường minh).
*	Downcasting: Ép kiểu từ lớp cha xuống lớp con (cần tường minh, có thể gây lỗi ClassCastException).


## Triển khai ý 1: Upcasting – Ép kiểu từ lớp con lên lớp cha
*	Khi một đối tượng của lớp con được gán cho biến của lớp cha, chỉ các phương thức của lớp cha có thể được truy cập.
*	Điều này giúp tăng tính linh hoạt khi sử dụng đa hình (polymorphism).
*	Có thể tự động hoặc tường minh (không cần hoặc cần (Parent) khi gán giá trị).

**Ví dụ**
```java
class Parent {
    void show() {
        System.out.println("Phương thức lớp cha");
    }
}

class Child extends Parent {
    void display() {
        System.out.println("Phương thức lớp con");
    }
}

public class Main {
    public static void main(String[] args) {
        Parent obj = new Child(); // Upcasting (tự động)
        obj.show(); // Chỉ gọi được phương thức lớp cha
        // obj.display(); // Lỗi biên dịch vì obj chỉ thấy các phương thức của Parent
    }
}

```

**Kết quả**
```java
Phương thức lớp cha
```

**Lưu ý**:
*	Upcasting không thể truy cập các phương thức riêng của lớp con (chẳng hạn display() của Child).
*	Đây là cơ chế phổ biến khi sử dụng đa hình (polymorphism) trong Java.


## Triển khai ý 2: Downcasting – Ép kiểu từ lớp cha xuống lớp con
*	Khi muốn sử dụng phương thức của lớp con từ một biến kiểu lớp cha, cần ép kiểu tường minh.
*	Nếu đối tượng gốc không phải của lớp con thực sự, sẽ gây ra ClassCastException.
*	Trước khi downcast, nên kiểm tra kiểu bằng instanceof để tránh lỗi.

**Ví dụ**
```java
class Parent {
    void show() {
        System.out.println("Phương thức lớp cha");
    }
}

class Child extends Parent {
    void display() {
        System.out.println("Phương thức lớp con");
    }
}

public class Main {
    public static void main(String[] args) {
        Parent obj = new Child(); // Upcasting
        if (obj instanceof Child) { // Kiểm tra trước khi downcast
            Child childObj = (Child) obj; // Downcasting (tường minh)
            childObj.display(); // Gọi phương thức lớp con
        }
    }
}

```
**Kết quả**
```java
Phương thức lớp con
```

**Lưu ý**:
*	Phải dùng (Child) obj để ép kiểu vì Java không tự động hỗ trợ downcasting.
*	Kiểm tra kiểu bằng instanceof giúp tránh ClassCastException khi ép kiểu.













