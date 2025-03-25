# Câu hỏi
Giải thích trình dọn rác (Garbage Collector) trong Java?

# Trả lời ngắn gọn  
Garbage Collector (GC) trong Java là một cơ chế tự động quản lý bộ nhớ, giúp loại bỏ các đối tượng không còn được tham chiếu để giải phóng bộ nhớ Heap. Điều này giúp lập trình viên không cần xóa thủ công như trong C/C++.


## Triển khai ý 1: Cách hoạt động của Garbage Collector 
GC xác định các đối tượng không còn tham chiếu bằng các thuật toán như:
*	Mark and Sweep: Đánh dấu các đối tượng còn được sử dụng, sau đó xóa những đối tượng không còn tham chiếu.
*	Generational Garbage Collection: Chia bộ nhớ Heap thành 3 vùng (Young Generation, Old Generation, Permanent Generation) để tối ưu hiệu suất.

**Ví dụ về đối tượng không còn tham chiếu (eligible for GC)**  

```java
class GarbageExample {
    public static void main(String[] args) {
        Person p1 = new Person("John"); // Tạo đối tượng John trên Heap
        p1 = new Person("Alice"); // Đối tượng John không còn tham chiếu và có thể bị GC dọn dẹp
        System.gc(); // Yêu cầu GC chạy (không đảm bảo sẽ chạy ngay lập tức)
    }
}

class Person {
    String name;
    Person(String name) {
        this.name = name;
    }

    @Override
    protected void finalize() throws Throwable {
        System.out.println("GC dọn dẹp: " + this.name);
    }
}

```  
**Kết quả**
```java
GC dọn dẹp: John
```
(GC có thể không chạy ngay lập tức vì JVM quyết định).

## Triển khai ý 2: Các cách để đối tượng trở thành garbage 
1. Gán tham chiếu thành null
   ```java
String str = new String("Hello");
str = null; // Đối tượng "Hello" không còn tham chiếu
   ```
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
