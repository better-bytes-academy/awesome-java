# Câu hỏi
Sự khác nhau giữa String Pool và Heap Memory khi lưu trữ chuỗi trong Java?

# Trả lời ngắn gọn  
Trong Java, chuỗi (String) có thể được lưu trữ ở hai vùng nhớ khác nhau:
*	String Pool (String Intern Pool) – Lưu trữ chuỗi trong một bộ nhớ đặc biệt bên trong Heap Memory. Nếu một chuỗi đã tồn tại, Java sẽ tái sử dụng thay vì tạo mới.
*	Heap Memory – Tạo một đối tượng String mới hoàn toàn, ngay cả khi nội dung giống nhau.


## Triển khai ý 1: String Pool giúp tái sử dụng chuỗi, tiết kiệm bộ nhớ
**Cách hoạt động**:
*	Khi tạo chuỗi bằng dấu "" (ví dụ: "Hello"), chuỗi sẽ được lưu vào String Pool.
*	Nếu cùng một chuỗi được tạo lại, Java sẽ tái sử dụng chuỗi cũ thay vì tạo mới.

**Ví dụ**:
```java
public class StringPoolExample {
    public static void main(String[] args) {
        String s1 = "Java";  // Tạo trong String Pool
        String s2 = "Java";  // Tái sử dụng chuỗi từ String Pool

        System.out.println(s1 == s2);  // ✅ true (cùng tham chiếu đến String Pool)
    }
}

```
**Kết quả**
```java
true
```
**Giải thích**:	s1 và s2 trỏ đến cùng một chuỗi "Java" trong String Pool, giúp tiết kiệm bộ nhớ.


## Triển khai ý 2: Heap Memory tạo chuỗi mới ngay cả khi nội dung giống nhau
**Cách hoạt động**:
*	Khi tạo chuỗi bằng new String(), chuỗi sẽ lưu vào Heap Memory thay vì String Pool.
*	Mỗi lần dùng new String(), Java tạo một đối tượng mới, ngay cả khi nội dung giống nhau.

**Ví dụ**
```java
public class HeapMemoryExample {
    public static void main(String[] args) {
        String s1 = new String("Java");  // Luôn tạo đối tượng mới trên Heap
        String s2 = new String("Java");  // Đối tượng mới trên Heap

        System.out.println(s1 == s2);  // ❌ false (khác tham chiếu)
        System.out.println(s1.equals(s2));  // ✅ true (so sánh nội dung)
    }
}

```

**Kết quả**
```java
false
true

```

**Giải thích**:
*	s1 và s2 chứa cùng nội dung "Java" nhưng là hai đối tượng khác nhau trong Heap Memory.
*	== kiểm tra tham chiếu → false, vì s1 và s2 trỏ đến hai đối tượng khác nhau.
*	.equals() kiểm tra nội dung → true, vì "Java".equals("Java").







