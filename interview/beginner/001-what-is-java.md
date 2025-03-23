# Câu hỏi
Java là gì và tại sao nó được gọi là "platform-independent"

# Trả lời ngắn gọn  
Java là một ngôn ngữ lập trình hướng đối tượng, được gọi là "platform-independent" (độc lập nền tảng) vì mã Java sau khi biên dịch thành bytecode có thể chạy trên bất kỳ hệ điều hành nào có Java Virtual Machine (JVM).

# Chi tiết kèm ví dụ thực tế  
Java được thiết kế để giảm sự phụ thuộc vào phần cứng hoặc hệ điều hành cụ thể, nhờ vào cơ chế biên dịch và thực thi đặc biệt của nó. Dưới đây là hai lý do chính giải thích tại sao Java là "platform-independent", kèm ví dụ minh họa.

## Triển khai ý 1: Biên dịch thành bytecode  
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
