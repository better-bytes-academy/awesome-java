# Câu hỏi
Exception là gì trong Java?

# Trả lời ngắn gọn  
Exception (ngoại lệ) trong Java là một sự kiện xảy ra trong quá trình thực thi chương trình, làm gián đoạn luồng chương trình bình thường. Java cung cấp cơ chế xử lý ngoại lệ để phát hiện và xử lý lỗi một cách an toàn, tránh làm chương trình bị dừng đột ngột.


## Triển khai ý 1: Exception là lỗi xảy ra trong lúc chạy chương trình 
Một số lỗi phổ biến dẫn đến ngoại lệ:
*	Chia cho 0 (ArithmeticException)
*	Truy cập phần tử ngoài phạm vi mảng (ArrayIndexOutOfBoundsException)
*	Làm việc với đối tượng null (NullPointerException)
  
**Ví dụ thực tế: Chia số cho 0 gây lỗi ArithmeticException**   
```java
public class ExceptionExample {
    public static void main(String[] args) {
        int a = 10, b = 0;
        int result = a / b; // Lỗi chia cho 0
        System.out.println("Kết quả: " + result);
    }
}

```  
**Kết quả**
```java
Exception in thread "main" java.lang.ArithmeticException: / by zero
```
Lỗi này có thể khiến chương trình bị dừng đột ngột nếu không xử lý

## Triển khai ý 2: Java cung cấp cơ chế xử lý ngoại lệ để tránh lỗi chương trình
Java sử dụng khối try-catch để xử lý ngoại lệ mà không làm gián đoạn chương trình.

**Ví dụ thực tế: Xử lý lỗi chia cho 0 bằng try-catch**   
```java
public class ExceptionHandlingExample {
    public static void main(String[] args) {
        try {
            int a = 10, b = 0;
            int result = a / b;
            System.out.println("Kết quả: " + result);
        } catch (ArithmeticException e) {
            System.out.println("Lỗi: Không thể chia cho 0!");
        }
        System.out.println("Chương trình vẫn tiếp tục chạy...");
    }
}

```  

**Kết quả**
```java
Lỗi: Không thể chia cho 0!  
Chương trình vẫn tiếp tục chạy...
```
Chương trình không bị dừng nhờ cơ chế xử lý ngoại lệ.

**Kết luận**
*	Exception là lỗi xảy ra trong lúc chạy chương trình.
*	Có thể xử lý bằng try-catch để tránh gián đoạn chương trình.
*	Giúp chương trình hoạt động ổn định và dễ bảo trì hơn.

