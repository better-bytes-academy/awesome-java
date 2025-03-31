# Câu hỏi
Sự khác nhau giữa switch và if-else trong Java?

# Trả lời ngắn gọn  
Cả switch và if-else đều được dùng để kiểm tra điều kiện trong Java, nhưng có sự khác biệt:
*	if-else: Dùng khi có nhiều điều kiện phức tạp, hỗ trợ mọi kiểu dữ liệu boolean.
*	switch: Dùng khi có nhiều trường hợp so sánh với một giá trị cố định, giúp code ngắn gọn hơn khi có nhiều điều kiện.

Dùng switch khi có nhiều giá trị cố định, if-else khi điều kiện linh hoạt hơn.


## Triển khai ý 1: if-else linh hoạt hơn, hỗ trợ điều kiện phức tạp
*	if-else có thể kiểm tra nhiều loại điều kiện (so sánh số, chuỗi, boolean, điều kiện logic…).
*	Dùng tốt khi điều kiện phức tạp, như kiểm tra phạm vi (>, <, >=, <=, &&, ||).

**Ví dụ**
```java
public class IfElseExample {
    public static void main(String[] args) {
        int age = 20;

        if (age < 18) {
            System.out.println("Bạn chưa đủ tuổi.");
        } else if (age >= 18 && age < 60) {
            System.out.println("Bạn là người trưởng thành.");
        } else {
            System.out.println("Bạn là người cao tuổi.");
        }
    }
}

```

**Kết quả**
```java
Bạn là người trưởng thành
```
**Giải thích**:
*	if-else kiểm tra điều kiện phức tạp (age < 18, age >= 18 && age < 60, age >= 60).
*	Không thể sử dụng switch ở đây vì điều kiện là khoảng giá trị, không phải giá trị cố định.



## Triển khai ý 2: switch giúp code gọn hơn khi kiểm tra giá trị cố định
*	switch chỉ so sánh giá trị cố định (int, char, String, enum,…) với một số case cụ thể.
*	Giúp code gọn hơn khi có nhiều lựa chọn cụ thể.

**Ví dụ**
```java
public class SwitchExample {
    public static void main(String[] args) {
        int day = 3;

        switch (day) {
            case 1:
                System.out.println("Chủ nhật");
                break;
            case 2:
                System.out.println("Thứ Hai");
                break;
            case 3:
                System.out.println("Thứ Ba");
                break;
            default:
                System.out.println("Không hợp lệ");
        }
    }
}

```

**Kết quả**
```java
Thứ Ba
```
**Giải thích**:
*	switch kiểm tra giá trị cố định (1, 2, 3…), giúp code gọn gàng hơn if-else.
*	Dùng break để tránh kiểm tra tiếp các case không cần thiết.




