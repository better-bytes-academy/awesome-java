# Câu hỏi
Sự khác nhau giữa lỗi (Error) và ngoại lệ (Exception) trong Java?

# Trả lời ngắn gọn  
*	**Error** là lỗi nghiêm trọng do hệ thống gây ra, thường không thể xử lý được bằng mã Java. Ví dụ: OutOfMemoryError, StackOverflowError.
*	**Exception** là lỗi xảy ra trong quá trình chạy chương trình, có thể bắt và xử lý được bằng try-catch. Ví dụ: NullPointerException, IOException.


## Triển khai ý 1: Error – Lỗi nghiêm trọng không thể xử lý
Lỗi thuộc lớp java.lang.Error, xảy ra do các vấn đề nghiêm trọng như tràn bộ nhớ hoặc lỗi hệ thống.

**Ví dụ**
```java
public class StackOverflowExample {
    public static void recursiveMethod() {
        recursiveMethod(); // Gọi đệ quy vô hạn
    }

    public static void main(String[] args) {
        recursiveMethod(); // Gây ra StackOverflowError
    }
}
```

**Kết quả**
```java
Exception in thread "main" java.lang.StackOverflowError
```
**Lưu ý**: Error không thể xử lý bằng try-catch vì nó thường yêu cầu sửa mã nguồn hoặc tăng tài nguyên hệ thống.


## Triển khai ý 2: Exception – Lỗi có thể xử lý được
Exception xảy ra khi chương trình chạy nhưng vẫn có thể kiểm soát bằng cách bắt lỗi (try-catch).

**Ví dụ**
```java
public class ExceptionExample {
    public static void main(String[] args) {
        try {
            int result = 10 / 0; // Lỗi chia cho 0
        } catch (ArithmeticException e) {
            System.out.println("Lỗi: Không thể chia cho 0!");
        }
    }
}

```

**Kết quả**
```java
Lỗi: Không thể chia cho 0!
```
**Lưu ý**: Exception có thể bắt bằng try-catch để tránh chương trình bị dừng đột ngột.





