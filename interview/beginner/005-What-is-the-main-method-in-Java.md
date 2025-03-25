# Câu hỏi
Phương thức main trong Java là gì? Vai trò của public, static, và void trong phương thức main?

# Trả lời ngắn gọn  
Phương thức main là điểm bắt đầu của mọi chương trình Java. Khi chạy chương trình, JVM sẽ tìm và thực thi phương thức main().

# Chi tiết kèm ví dụ thực tế  
Mỗi chương trình Java đều cần có phương thức main(), vì đây là nơi JVM bắt đầu thực thi mã nguồn.

## Triển khai ý 1: Phương thức main() là điểm bắt đầu của chương trình
Java không biên dịch trực tiếp thành mã máy (machine code) như C/C++, mà thành bytecode - một dạng mã trung gian. Bytecode này được JVM diễn giải và thực thi. Vì JVM có sẵn trên nhiều nền tảng (Windows, macOS, Linux…), mã Java chỉ cần viết một lần là có thể chạy khắp nơi.  
**Ví dụ thực tế:**  
Bạn viết một chương trình Java đơn giản:  
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào, Java!");
    }
}
```
**Kết quả**
```java
Xin chào, Java!
```
Khi chạy chương trình, JVM sẽ tìm main() và bắt đầu thực thi mã bên trong.

## Triển khai ý 2: Vai trò của public, static, và void  
 1. `public` (Phạm vi truy cập công khai)
* Giúp JVM có thể gọi `main()` từ bên ngoài lớp.
* Nếu bỏ `public`, JVM không thể truy cập `main()`, gây lỗi khi chạy chương trình.
 
**Ví dụ thực tế:**  
Giả sử bạn phát triển một ứng dụng tính toán đơn giản:  
```java
public class Calculator {
    public static void main(String[] args) {
        int a = 5, b = 10;
        System.out.println("Tổng: " + (a + b));
    }
}
```  

