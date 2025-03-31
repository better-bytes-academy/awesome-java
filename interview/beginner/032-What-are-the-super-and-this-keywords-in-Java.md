# Câu hỏi
Từ khóa super và this trong Java là gì?

# Trả lời ngắn gọn  
*	super: Dùng để gọi constructor hoặc phương thức của lớp cha (superclass).
*	this: Dùng để tham chiếu đến biến, phương thức hoặc constructor của chính lớp hiện tại.

## Triển khai ý 1: this – Tham chiếu đến lớp hiện tại
*	this dùng để phân biệt giữa biến instance và tham số cùng tên.
*	this() có thể được sử dụng để gọi constructor khác trong cùng một lớp.

**Ví dụ**
```java
class Student {
    String name;
    
    // Constructor với tham số trùng tên biến instance
    Student(String name) {
        this.name = name; // Dùng this để phân biệt biến instance
    }
    
    void display() {
        System.out.println("Tên sinh viên: " + this.name);
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student("An");
        s1.display();
    }
}

```
**Kết quả**
```java
Tên sinh viên: An
```
**Lưu ý**: Nếu không dùng this.name = name;, chương trình sẽ không biết đang gán tham số cho biến nào.

 
## Triển khai ý 2: super – Tham chiếu đến lớp cha
*	super giúp truy cập phương thức hoặc biến của lớp cha.
*	super() dùng để gọi constructor của lớp cha (bắt buộc phải là lệnh đầu tiên trong constructor).

**Ví dụ**
```java
class Parent {
    String message = "Xin chào từ lớp cha!";
    
    Parent() {
        System.out.println("Constructor lớp cha được gọi");
    }
}

class Child extends Parent {
    String message = "Xin chào từ lớp con!";
    
    Child() {
        super(); // Gọi constructor lớp cha
        System.out.println("Constructor lớp con được gọi");
    }
    
    void display() {
        System.out.println(super.message); // Gọi biến của lớp cha
    }
}

public class Main {
    public static void main(String[] args) {
        Child c = new Child();
        c.display();
    }
}

```

**Kết quả**
```java
Constructor lớp cha được gọi  
Constructor lớp con được gọi  
Xin chào từ lớp cha!
```

**Lưu ý**:
*	super() gọi constructor của lớp cha trước khi chạy constructor của lớp con.
*	super.message dùng để gọi biến message từ lớp cha.

