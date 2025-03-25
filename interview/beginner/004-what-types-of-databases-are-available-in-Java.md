# Câu hỏi
Các kiểu dữ liệu cơ bản có sẵn trong Java?

# Trả lời ngắn gọn  
Java cung cấp 8 kiểu dữ liệu nguyên thủy (primitive data types), bao gồm: byte, short, int, long, float, double, char, và boolean. Những kiểu này giúp Java xử lý dữ liệu hiệu quả và tối ưu bộ nhớ.

# Chi tiết kèm ví dụ thực tế  
Trong Java, kiểu dữ liệu nguyên thủy là những kiểu được tích hợp sẵn trong ngôn ngữ, giúp quản lý bộ nhớ và hiệu suất tốt hơn so với kiểu dữ liệu đối tượng..

## Triển khai ý 1: Nhóm kiểu số nguyên 
Các kiểu số nguyên trong Java bao gồm:
1	byte (8-bit): Phạm vi từ -128 đến 127
2	short (16-bit): Phạm vi từ -32,768 đến 32,767
3	int (32-bit): Phạm vi từ -2^31 đến 2^31-1
4	long (64-bit): Phạm vi từ -2^63 đến 2^63-1
 
**Ví dụ thực tế:**  
Bạn viết một chương trình Java đơn giản:  
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào, Java!");
    }
}
```  
Sau khi biên dịch bằng lệnh `javac HelloWorld.java`, bạn được file `HelloWorld.class` (bytecode). File này có thể chạy trên Windows, Linux hay macOS mà không cần chỉnh sửa, miễn là máy cài JVM.

## Triển khai ý 2: JVM đóng vai trò trung gian  
JVM là lớp trừu tượng hóa giữa bytecode và phần cứng thực tế. Mỗi hệ điều hành có phiên bản JVM riêng, nhưng giao diện và cách hoạt động của JVM là thống nhất. Điều này đảm bảo mã Java hoạt động đồng nhất trên mọi nền tảng.  
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
Bạn biên dịch trên macOS, sau đó copy file `.class` sang một máy Windows và chạy bằng lệnh `java Calculator`. Kết quả "Tổng: 15" sẽ hiển thị giống nhau, vì JVM trên Windows xử lý bytecode tương tự như JVM trên macOS.

Nhờ bytecode và JVM, Java đạt được tính "platform-independent", giúp lập trình viên tiết kiệm thời gian và công sức khi triển khai ứng dụng trên nhiều hệ điều hành khác nhau.
