# Câu hỏi
Lệnh import được sử dụng ở đâu trong một chương trình Java?

# Trả lời ngắn gọn  
Lệnh import trong Java được sử dụng ở đầu tệp mã nguồn (trước khi khai báo lớp) để nhập các lớp hoặc gói cần thiết từ thư viện Java hoặc từ mã nguồn khác. Điều này giúp lập trình viên sử dụng các lớp mà không cần viết đầy đủ đường dẫn gói của chúng.


## Triển khai ý 1: import được sử dụng để truy cập các lớp có sẵn trong Java 
Java cung cấp nhiều thư viện sẵn có, và import giúp chúng ta sử dụng mà không cần viết tên đầy đủ của lớp.  
**Ví dụ thực tế:**  
```java
import java.util.ArrayList; // Nhập lớp ArrayList từ gói java.util
public class Example {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>(); // Dùng ArrayList mà không cần viết java.util.ArrayList
        list.add("Java");
        System.out.println(list);
    }
}

```  
✅ Giúp mã nguồn gọn hơn, dễ đọc hơn.

## Triển khai ý 2: import dùng để nhập các lớp do lập trình viên tự định nghĩa  
Nếu bạn có một lớp trong gói khác, bạn có thể sử dụng import để tái sử dụng mà không cần khai báo đường dẫn đầy đủ.

**Ví dụ thực tế:**    
```java
import mypackage.MyClass; // Nhập lớp MyClass từ gói mypackage

public class Example {
    public static void main(String[] args) {
        MyClass obj = new MyClass(); // Dùng MyClass mà không cần viết mypackage.MyClass
    }
}

```  
✅ Dễ dàng tổ chức và quản lý mã nguồn.
