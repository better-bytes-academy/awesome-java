# Câu hỏi
Sự khác biệt giữa Stack và Heap trong Java là gì?

# Trả lời ngắn gọn  
*	Stack: Bộ nhớ dành cho các biến cục bộ và lời gọi hàm, có tốc độ truy cập nhanh, quản lý theo cơ chế LIFO (Last In, First Out).
*	Heap: Bộ nhớ dành cho đối tượng (Objects) và dữ liệu động, có thể truy cập toàn cục nhưng chậm hơn do cần quản lý bộ nhớ tự động (Garbage Collection).

# Chi tiết kèm ví dụ thực tế  
Java quản lý bộ nhớ thông qua hai khu vực chính: Stack (ngăn xếp) và Heap (đống).

## Triển khai ý 1: Stack – Dành cho biến cục bộ và lời gọi hàm
*	Lưu trữ biến nguyên thủy (int, double, boolean, ...) và tham chiếu đến đối tượng.
*	Dữ liệu trong Stack tự động hủy khi phương thức kết thúc.
*	Quản lý bộ nhớ theo LIFO (Last In, First Out).
*	Tốc độ truy cập nhanh, do không cần dọn dẹp bộ nhớ thủ công.

**Ví dụ thực tế:**  
```java
public class StackExample {
    public static void main(String[] args) {
        int x = 10; // Biến nguyên thủy lưu trong Stack
        int y = sum(x, 5); // Gọi hàm sum(), tạo Stack Frame mới
        System.out.println(y); // Output: 15
    }

    public static int sum(int a, int b) {
        return a + b; // Khi kết thúc, biến a và b bị xóa khỏi Stack
    }
}
```  
👉 Mỗi lần gọi hàm, Java tạo một Stack Frame mới chứa biến cục bộ. Khi hàm kết thúc, Stack Frame bị xóa.

## Triển khai ý 2: Heap – Dành cho đối tượng và dữ liệu động  
*	Lưu trữ đối tượng (Objects) và mảng.
*	Đối tượng trên Heap được truy cập thông qua tham chiếu (references) từ Stack.
*	Java quản lý bộ nhớ Heap bằng Garbage Collector (GC) để giải phóng dữ liệu không còn sử dụng.
*	Tốc độ truy cập chậm hơn Stack do quản lý bộ nhớ phức tạp hơn.

**Ví dụ thực tế:**  
```java
class Person {
    String name;

    Person(String name) {
        this.name = name;
    }
}

public class HeapExample {
    public static void main(String[] args) {
        Person p1 = new Person("John"); // Đối tượng được tạo trên Heap
        Person p2 = new Person("Alice"); // Một đối tượng khác trên Heap
        System.out.println(p1.name + " & " + p2.name);
    }
}
```  
👉 p1 và p2 là biến tham chiếu trong Stack, nhưng đối tượng Person được lưu trên Heap.

**Kết luận**
*	Stack dùng để lưu trữ biến cục bộ và lời gọi hàm, có tốc độ nhanh nhưng giới hạn kích thước.
*	Heap dùng để lưu trữ đối tượng, quản lý bộ nhớ phức tạp hơn nhưng linh hoạt hơn.
*	Kết hợp Stack và Heap giúp Java quản lý bộ nhớ hiệu quả, tránh lỗi tràn bộ nhớ (Stack Overflow) và tối ưu hiệu suất. 

