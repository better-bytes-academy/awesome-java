# Câu hỏi
Throw và Throws trong Java

# Trả lời ngắn gọn  
*	throw: Dùng để ném một ngoại lệ cụ thể trong phương thức.
*	throws: Khai báo một hoặc nhiều ngoại lệ mà phương thức có thể ném ra, yêu cầu xử lý ở nơi gọi nó.



## Triển khai ý 1: throw ném một ngoại lệ cụ thể
Lệnh throw được sử dụng bên trong một phương thức hoặc khối lệnh để ném một đối tượng ngoại lệ (Exception). Sau khi ném ngoại lệ, chương trình dừng thực thi tại vị trí đó, trừ khi ngoại lệ được xử lý (try-catch).

**Ví dụ:**
```java
public class ThrowExample {
    public static void checkAge(int age) {
        if (age < 18) {
            throw new IllegalArgumentException("Tuổi phải >= 18");
        }
        System.out.println("Bạn đủ điều kiện!");
    }

    public static void main(String[] args) {
        checkAge(16); // Sẽ ném ra IllegalArgumentException
```

**Kết quả**
```java
Exception in thread "main" java.lang.IllegalArgumentException: Tuổi phải >= 18
```


## Triển khai ý 2: throws khai báo ngoại lệ của phương thức
Lệnh throws được dùng trong khai báo phương thức để chỉ ra rằng phương thức có thể ném ngoại lệ. Nếu một phương thức gọi một phương thức có throws, nó phải xử lý ngoại lệ hoặc tiếp tục khai báo throws.

**Ví du:**
```java
import java.io.IOException;

public class ThrowsExample {
    // Khai báo phương thức có thể ném IOException
    public static void readFile() throws IOException {
        throw new IOException("Lỗi khi đọc file");
    }

    public static void main(String[] args) {
        try {
            readFile();
        } catch (IOException e) {
            System.out.println("Ngoại lệ được xử lý: " + e.getMessage());
        }
    }
}
```
**Kết quả**
```java
Ngoại lệ được xử lý: Lỗi khi đọc file
```
