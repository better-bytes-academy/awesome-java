# Câu hỏi
Sự khác biệt giữa kiểu dữ liệu nguyên thủy (primitive type) và kiểu dữ liệu tham chiếu (reference type) trong Java là gì?

# Trả lời ngắn gọn  
*	Kiểu dữ liệu nguyên thủy (primitive type): Lưu trữ giá trị trực tiếp trong bộ nhớ.
*	Kiểu dữ liệu tham chiếu (reference type): Lưu trữ địa chỉ của đối tượng trong bộ nhớ Heap, không phải giá trị trực tiếp.

# Chi tiết kèm ví dụ thực tế  
Trong Java, có hai loại kiểu dữ liệu chính: nguyên thủy (primitive) và tham chiếu (reference).

## Triển khai ý 1: Kiểu dữ liệu nguyên thủy (primitive type)
*	Có 8 loại: byte, short, int, long, float, double, char, boolean.
*	Lưu trữ giá trị thực trong bộ nhớ Stack.
*	Không phải là đối tượng, hoạt động nhanh hơn
  
**Ví dụ thực tế:**  
```java
public class PrimitiveExample {
    public static void main(String[] args) {
        int a = 10;
        int b = a; // Sao chép giá trị a vào b
        
        b = 20; // Chỉ thay đổi b, a vẫn giữ nguyên giá trị 10

        System.out.println("a: " + a); // Output: a: 10
        System.out.println("b: " + b); // Output: b: 20
    }
}
```  
👉 Giá trị của a không bị thay đổi, vì b chỉ là một bản sao độc lập.

## Triển khai ý 2: Kiểu dữ liệu tham chiếu (reference type) 
*	Bao gồm các đối tượng, mảng, chuỗi (String), và lớp tự định nghĩa.
*	Lưu trữ địa chỉ (reference) của đối tượng trong bộ nhớ Heap, còn biến tham chiếu nằm trong Stack.
*	Khi gán một biến tham chiếu cho biến khác, cả hai đều trỏ đến cùng một đối tượng.
 
**Ví dụ thực tế:**  
```java
class Person {
    String name;

    Person(String name) {
        this.name = name;
    }
}

public class ReferenceExample {
    public static void main(String[] args) {
        Person p1 = new Person("John");
        Person p2 = p1; // p2 trỏ đến cùng đối tượng với p1

        p2.name = "David"; // Thay đổi giá trị của p2 cũng làm thay đổi p1

        System.out.println("p1.name: " + p1.name); // Output: p1.name: David
        System.out.println("p2.name: " + p2.name); // Output: p2.name: David
    }
}

```  
👉 Cả p1 và p2 đều trỏ đến cùng một đối tượng, nên thay đổi p2 cũng ảnh hưởng đến p1.

**Kết luận**
*	Kiểu nguyên thủy lưu trữ giá trị trực tiếp, hoạt động nhanh hơn và độc lập.
*	Kiểu tham chiếu lưu địa chỉ của đối tượng, khi thay đổi dữ liệu thì tất cả biến trỏ đến đối tượng đó đều bị ảnh hưởng.
*	Hiểu rõ sự khác biệt này giúp tránh lỗi khi thao tác với đối tượng và biến trong Java.

