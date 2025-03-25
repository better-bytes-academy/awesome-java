# Câu hỏi
Constructor là gì? Có bao nhiêu loại constructor trong Java?

# Trả lời ngắn gọn  
Constructor là một phương thức đặc biệt trong Java được gọi tự động khi tạo đối tượng, dùng để khởi tạo giá trị cho các biến của lớp.

Có 3 loại constructor trong Java:
1.	Constructor mặc định (Default Constructor) – Không có tham số.
2.	Constructor có tham số (Parameterized Constructor) – Có tham số để gán giá trị khi tạo đối tượng.
3.	Constructor sao chép (Copy Constructor) – Dùng để tạo bản sao của một đối tượng khác.


## Triển khai ý 1: Constructor mặc định (Default Constructor)
*	Là constructor không có tham số.
*	Nếu lập trình viên không khai báo constructor, Java sẽ tự động tạo một constructor mặc định.
*	Chủ yếu dùng để khởi tạo giá trị mặc định cho đối tượng.

**Ví dụ**
```java
class Student {
    String name;
    int age;

    // Constructor mặc định
    Student() {
        name = "Không xác định";
        age = 18;
    }

    void display() {
        System.out.println("Tên: " + name + ", Tuổi: " + age);
    }
}

public class TestDefaultConstructor {
    public static void main(String[] args) {
        Student s1 = new Student(); // Gọi constructor mặc định
        s1.display();
    }
}
```

**Kết quả**
```java
Tên: Không xác định, Tuổi: 18
```
**Lưu ý**:
*	Constructor mặc định rất hữu ích khi cần tạo đối tượng với giá trị mặc định.
*	Nếu có constructor khác, Java sẽ không tự động tạo constructor mặc định.


## Triển khai ý 2:

