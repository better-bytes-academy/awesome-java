# Câu hỏi
Tại sao Generic được sử dụng trong Java?

# Trả lời ngắn gọn  
Generic trong Java giúp tăng tính an toàn kiểu dữ liệu và tái sử dụng mã bằng cách cho phép xác định kiểu dữ liệu tại thời điểm biên dịch thay vì sử dụng kiểu Object. Điều này giúp tránh lỗi ép kiểu và làm cho mã nguồn dễ đọc hơn.


## Triển khai ý 1: Tăng tính an toàn kiểu dữ liệu (Type Safety)
Khi sử dụng Generic, bạn không cần ép kiểu thủ công, giúp tránh lỗi khi biên dịch. 

**Ví dụ thực tế (Không dùng Generic - dễ lỗi ép kiểu):**  
```java
import java.util.ArrayList;

public class Example {
    public static void main(String[] args) {
        ArrayList list = new ArrayList(); // Không dùng Generic
        list.add("Java");
        list.add(123); // Không có kiểm tra kiểu

        String str = (String) list.get(1); // Lỗi tại runtime (ClassCastException)
        System.out.println(str);
    }
}
```  
⚠ Không an toàn vì có thể thêm nhiều loại dữ liệu khác nhau.

**Ví dụ thực tế (Dùng Generic - an toàn hơn)**:
```java
import java.util.ArrayList;

public class Example {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>(); // Chỉ cho phép String
        list.add("Java");
        // list.add(123); // Lỗi biên dịch nếu cố gắng thêm số

        String str = list.get(0); // Không cần ép kiểu
        System.out.println(str);
    }
}

```
✅ Giúp mã an toàn, tránh lỗi ép kiểu tại runtime.

## Triển khai ý 2: Tái sử dụng mã (Code Reusability) 
Generic cho phép bạn tạo các lớp, giao diện, và phương thức có thể làm việc với nhiều kiểu dữ liệu khác nhau mà không cần viết nhiều phiên bản. 

**Ví dụ thực tế:**  
```java
class Box<T> { // Lớp Generic với kiểu dữ liệu T
    private T value;

    public void setValue(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }
}

public class Example {
    public static void main(String[] args) {
        Box<String> stringBox = new Box<>();
        stringBox.setValue("Hello Generic");
        System.out.println(stringBox.getValue());

        Box<Integer> intBox = new Box<>();
        intBox.setValue(100);
        System.out.println(intBox.getValue());
    }
}

```  
✅ Tạo một lớp Box dùng được cho cả String và Integer mà không cần viết nhiều lần.
