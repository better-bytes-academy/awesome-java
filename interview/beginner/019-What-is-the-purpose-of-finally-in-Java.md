# Câu hỏi
finally trong Java dùng để làm gì?

# Trả lời ngắn gọn  
*	finally là một khối mã đi kèm với try-catch, luôn được thực thi dù có ngoại lệ xảy ra hay không.
*	Thường dùng để giải phóng tài nguyên như đóng file, kết nối cơ sở dữ liệu,...


## Triển khai ý 1: finally luôn được thực thi
Trong Java, khi một ngoại lệ xảy ra trong khối try, chương trình có thể nhảy vào catch để xử lý lỗi. Tuy nhiên, khối finally sẽ luôn luôn chạy ngay cả khi có hoặc không có ngoại lệ.

**Ví dụ:**
```java
public class FinallyExample {
    public static void main(String[] args) {
        try {
            System.out.println("Bắt đầu khối try.");
            int result = 10 / 0; // Lỗi chia cho 0 (ArithmeticException)
        } catch (ArithmeticException e) {
            System.out.println("Lỗi: Chia cho 0!");
        } finally {
            System.out.println("Khối finally luôn được thực thi.");
        }
    }
}

```
**Kết quả**
```java
Bắt đầu khối try.  
Lỗi: Chia cho 0!  
Khối finally luôn được thực thi.  

```
✅ Dù có ngoại lệ, khối finally vẫn chạy.

## Triển khai ý 2: finally dùng để giải phóng tài nguyên
Khối finally thường được dùng để đóng tài nguyên như file, kết nối mạng, hoặc database, đảm bảo chương trình không bị rò rỉ tài nguyên.

**Ví dụ thực tế: Đóng kết nối file**
```java
import java.io.*;

public class FinallyFileExample {
    public static void main(String[] args) {
        FileReader file = null;
        try {
            file = new FileReader("data.txt");
            BufferedReader br = new BufferedReader(file);
            System.out.println(br.readLine());
        } catch (IOException e) {
            System.out.println("Lỗi khi đọc file!");
        } finally {
            try {
                if (file != null) {
                    file.close();
                    System.out.println("File đã được đóng.");
                }
            } catch (IOException e) {
                System.out.println("Lỗi khi đóng file!");
            }
        }
    }
}

```
Nếu không dùng finally, file có thể không được đóng nếu có lỗi xảy ra!

