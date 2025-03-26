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

## Triển khai ý 2: Iterator hỗ trợ xóa phần tử an toàn trong khi duyệt

**Ví dụ thực tế:**  
Xóa tất cả sinh viên có tên bắt đầu bằng chữ B.
```java
import java.util.*;

public class RemoveUsingIterator {
    public static void main(String[] args) {
        List<String> students = new ArrayList<>();
        students.add("Alice");
        students.add("Bob");
        students.add("Charlie");
        
        Iterator<String> iterator = students.iterator();
        
        while (iterator.hasNext()) {
            String name = iterator.next();
            if (name.startsWith("B")) {
                iterator.remove(); // Xóa phần tử an toàn
            }
        }

        System.out.println(students); // Output: [Alice, Charlie]
    }
}

```  
✅ Lớp Iterator giúp xóa phần tử mà không gây lỗi ConcurrentModificationException.

**Kết luận**
*	Iterator giúp duyệt qua Collection một cách tuần tự.
*	Có thể xóa phần tử an toàn trong khi duyệt mà không gây lỗi.
*	Thay thế vòng lặp for khi không cần truy cập trực tiếp chỉ mục.

