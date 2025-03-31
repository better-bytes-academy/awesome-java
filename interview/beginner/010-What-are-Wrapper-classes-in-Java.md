# Câu hỏi
Các lớp Wrapper trong Java là gì?

# Trả lời ngắn gọn  
Các lớp Wrapper trong Java là các lớp trong gói java.lang dùng để bao bọc (wrap) kiểu dữ liệu nguyên thủy thành đối tượng. Điều này giúp làm việc với kiểu dữ liệu nguyên thủy dễ dàng hơn trong các cấu trúc yêu cầu đối tượng, như Collection (List, Set, Map).


## Triển khai ý 1: Danh sách các lớp Wrapper
Mỗi kiểu dữ liệu nguyên thủy (primitive type) trong Java đều có một lớp Wrapper tương ứng:
| Kiểu nguyên thủy | Lớp Wapper |
|---------|-----|
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

**Ví dụ**: Chuyển đổi từ kiểu nguyên thủy sang lớp Wrapper (Boxing)
```java
int num = 10;
Integer obj = Integer.valueOf(num); // Boxing (chuyển từ int sang Integer)
System.out.println(obj); // Kết quả: 10

```

**Ví dụ**: Chuyển đổi từ lớp Wrapper sang kiểu nguyên thủy (Unboxing)
```java
Integer obj = Integer.valueOf(20);
int num = obj.intValue(); // Unboxing (chuyển từ Integer sang int)
System.out.println(num); // Kết quả: 20
```

## Triển khai ý 2: Ứng dụng của lớp Wrapper
1.	Sử dụng trong Collections (List, Set, Map)
*	Java Collections chỉ làm việc với đối tượng, không thể lưu kiểu nguyên thủy.
*	Lớp Wrapper giúp đưa giá trị nguyên thủy vào ArrayList, HashSet, HashMap, v.v.

```java
import java.util.ArrayList;
public class WrapperExample {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        list.add(100); // Autoboxing: int -> Integer
        list.add(200);
        System.out.println(list); // [100, 200]
    }
}
```

2.	Chuyển đổi kiểu dữ liệu giữa String và số
```java
String str = "123";
int number = Integer.parseInt(str); // Chuyển String thành int
System.out.println(number + 10); // Kết quả: 133
```

3.	Xử lý giá trị null (tránh lỗi NullPointerException)
```java
Integer obj = null; // Lớp Wrapper có thể nhận giá trị null, còn int thì không
if (obj != null) {
    int value = obj; // Unboxing
    System.out.println(value);
} else {
    System.out.println("Giá trị là null");
}
```

**Kết luận**
*	Lớp Wrapper giúp làm việc với kiểu nguyên thủy dưới dạng đối tượng.
*	Cần thiết khi sử dụng Collection, Generic, hoặc xử lý dữ liệu đầu vào từ chuỗi.
*	Hỗ trợ tính năng Autoboxing (tự động chuyển đổi kiểu nguyên thủy thành Wrapper) và Unboxing (ngược lại). 

