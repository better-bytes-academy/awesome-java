# Câu hỏi
Khối static là gì?

# Trả lời ngắn gọn  
Khối static trong Java là một khối mã được thực thi chỉ một lần khi lớp được tải vào bộ nhớ, trước cả khi đối tượng của lớp được tạo ra hoặc phương thức main() chạy.


## Triển khai ý 1: Cách hoạt động của khối static  
*	Một lớp có thể có nhiều khối static, và chúng sẽ được thực thi theo thứ tự xuất hiện.
*	Khối static được sử dụng để khởi tạo dữ liệu tĩnh (static fields) hoặc thực hiện các tác vụ khởi động quan trọng.
 
**Ví dụ thực tế:**   
```java
class StaticBlockExample {
    static {
        System.out.println("Khối static 1 được thực thi");
    }

    static {
        System.out.println("Khối static 2 được thực thi");
    }

    public static void main(String[] args) {
        System.out.println("Phương thức main chạy");
    }
}
```  
**Kết quả**
```java
Khối static 1 được thực thi  
Khối static 2 được thực thi  
Phương thức main chạy  
```
**Giải thích**:Các khối static được thực thi trước khi phương thức main() chạy.


## Triển khai ý 2: Ứng dụng của khối static
1.	Khởi tạo biến static
```java
class Example {
    static int number;
    static {
        number = 100;
        System.out.println("Biến static được khởi tạo: " + number);
    }
}

public class Test {
    public static void main(String[] args) {
        System.out.println("Chương trình bắt đầu");
        Example obj = new Example(); // Khi lớp Example được tải, khối static chạy trước
    }
}
```
**Kết quả**
```java
Biến static được khởi tạo: 100  
Chương trình bắt đầu  
```
2.	Tải thư viện hoặc tài nguyên chỉ một lần
```java
class DatabaseConnection {
    static {
        System.out.println("Kết nối cơ sở dữ liệu được thiết lập");
    }
}

public class Main {
    public static void main(String[] args) {
        DatabaseConnection db1 = new DatabaseConnection();
        DatabaseConnection db2 = new DatabaseConnection(); // Không chạy lại khối static
    }
}

```
**Kết quả**
```java
Kết nối cơ sở dữ liệu được thiết lập  
```

**Giải thích**: Khối static chỉ chạy một lần duy nhất khi lớp được tải.
**Kết luận:**
*	Khối static chạy trước phương thức main() và chỉ thực thi một lần duy nhất.
*	Được sử dụng để khởi tạo biến tĩnh, tải tài nguyên hoặc thực hiện các tác vụ khởi động quan trọng
