# Câu hỏi
Iterator là gì trong Java?

# Trả lời ngắn gọn  
Iterator trong Java là một giao diện (interface) trong java.util dùng để duyệt qua các phần tử của Collection (List, Set, Queue) một cách tuần tự mà không cần truy cập trực tiếp vào cấu trúc dữ liệu bên trong. Iterator hỗ trợ xóa phần tử an toàn trong khi duyệt qua danh sách.


## Triển khai ý 1: Iterator giúp duyệt qua Collection một cách tuần tự
Iterator cung cấp các phương thức chính:
*	hasNext() → Kiểm tra còn phần tử tiếp theo hay không.
*	next() → Lấy phần tử tiếp theo.
*	remove() → Xóa phần tử hiện tại (tùy chọn).

**Ví dụ thực tế:**  
Duyệt qua danh sách sinh viên bằng Iterator.
```java
import java.util.*;

public class IteratorExample {
    public static void main(String[] args) {
        List<String> students = new ArrayList<>();
        students.add("Alice");
        students.add("Bob");
        students.add("Charlie");

        Iterator<String> iterator = students.iterator();
        
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
    }
}

```  
**Kết quả**
```java
Alice  
Bob  
Charlie  
```
✅Lợi ích: Duyệt danh sách mà không cần dùng vòng lặp for hoặc truy cập trực tiếp chỉ mục (index).
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
