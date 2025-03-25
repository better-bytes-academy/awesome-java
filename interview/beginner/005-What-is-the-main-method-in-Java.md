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
 2. static (Phương thức tĩnh)
•	Cho phép JVM gọi main() mà không cần tạo đối tượng của lớp.
•	Nếu bỏ static, chương trình sẽ yêu cầu tạo đối tượng trước khi gọi main(), không phù hợp với Java.
3. void (Không có giá trị trả về)
•	main() không cần trả về kết quả cho JVM, nên khai báo void.
•	Nếu đổi thành kiểu khác (ví dụ: int), chương trình sẽ báo lỗi.
Ví dụ về lỗi khi bỏ static hoặc public:
**Ví dụ thực tế:**    
```java
public class Test {
    void main(String[] args) { // Thiếu static và public
        System.out.println("Lỗi sẽ xảy ra!");
    }
}
```
**Kết quả**
```java
Error: Main method not found in class Test
```
JVM không thể tìm thấy main() đúng chuẩn nên chương trình không thể chạy.

**Kết luận**
•	Phương thức main() là điểm bắt đầu của chương trình Java.
•	public cho phép JVM truy cập từ bên ngoài.
•	static giúp gọi main() mà không cần tạo đối tượng.
•	void đảm bảo main() không cần trả về giá trị.
•	Nếu không có main(), chương trình Java không thể chạy.


