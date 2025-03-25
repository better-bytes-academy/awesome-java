# Câu hỏi
Câu hỏi: Sự khác biệt giữa Checked Exception và Unchecked Exception?

# Trả lời ngắn gọn 
*	**Checked Exception**: Ngoại lệ được kiểm tra tại thời điểm biên dịch, bắt buộc phải xử lý bằng try-catch hoặc throws.
*	**Unchecked Exception**: Ngoại lệ xảy ra khi chương trình đang chạy, không bắt buộc phải xử lý, nhưng có thể gây lỗi chương trình.

## Triển khai ý 1:Checked Exception – Ngoại lệ được kiểm tra tại biên dịch
Checked Exception là những ngoại lệ mà trình biên dịch bắt buộc lập trình viên phải xử lý trước khi chạy chương trình, nhằm tránh các lỗi có thể đoán trước như lỗi nhập xuất (IOException), lỗi truy vấn CSDL (SQLException),...

**Ví dụ:**
Giả sử bạn muốn đọc dữ liệu từ một file, nhưng file có thể không tồn tại. Khi biên dịch, chương trình yêu cầu bạn phải xử lý ngoại lệ.
```java
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class CheckedExceptionExample {
    public static void main(String[] args) {
        try {
            File file = new File("data.txt");
            Scanner scanner = new Scanner(file); // Có thể ném FileNotFoundException
        } catch (FileNotFoundException e) {
            System.out.println("Lỗi: File không tồn tại!");
        }
    }
}
```

✅ Nếu không xử lý FileNotFoundException, chương trình sẽ không thể biên dịch được.

## Triển khai ý 2: Unchecked Exception – Ngoại lệ xảy ra khi chương trình chạy
Unchecked Exception là những ngoại lệ xảy ra trong thời gian chạy (Runtime), thường do lỗi logic của lập trình viên, như chia cho 0 (ArithmeticException), truy cập mảng ngoài phạm vi (ArrayIndexOutOfBoundsException), truy cập vào đối tượng null (NullPointerException),...

**Ví dụ:**
Bạn viết chương trình thực hiện phép chia, nhưng người dùng có thể nhập số 0, gây lỗi chia cho 0.
```java
public class UncheckedExceptionExample {
    public static void main(String[] args) {
        int a = 10, b = 0;
        System.out.println(a / b); // Lỗi ArithmeticException tại runtime
    }
}
```
✅ Chương trình vẫn biên dịch được nhưng sẽ lỗi tại runtime!








