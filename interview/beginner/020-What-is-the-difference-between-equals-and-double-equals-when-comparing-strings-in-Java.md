# Câu hỏi
Sự khác biệt giữa == và .equals() khi so sánh chuỗi trong Java là gì?

# Trả lời ngắn gọn  
*	== so sánh địa chỉ ô nhớ của hai đối tượng. Nếu hai biến trỏ đến cùng một đối tượng trong bộ nhớ, nó trả về true, ngược lại trả về false.
*	.equals() so sánh nội dung chuỗi. Nếu hai chuỗi có cùng giá trị ký tự, nó trả về true, ngay cả khi chúng nằm ở các vùng nhớ khác nhau.


## Triển khai ý 1: == so sánh địa chỉ ô nhớ (so sánh tham chiếu)
Khi sử dụng == để so sánh hai chuỗi, Java kiểm tra xem hai biến có trỏ đến cùng một vùng nhớ hay không.
```java
public class StringComparison {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s2 = "Hello";
        String s3 = new String("Hello");

        System.out.println(s1 == s2); // ✅ true (cùng vùng nhớ trong String Pool)
        System.out.println(s1 == s3); // ❌ false (s3 là đối tượng mới trong Heap)
    }
}

```

**Giải thích**:
*	s1 và s2 đều chứa chuỗi "Hello". Do Java sử dụng String Pool, cả hai biến sẽ trỏ đến cùng một vị trí trong bộ nhớ, nên s1 == s2 trả về true.
*	s3 được tạo bằng new String("Hello"), tức là nó được cấp phát một vùng nhớ mới trong Heap. Vì vậy, s1 == s3 trả về false vì chúng không trỏ đến cùng một đối tượng.

## Triển khai ý 2: .equals() so sánh nội dung chuỗi
Phương thức .equals() trong lớp String dùng để kiểm tra nội dung của chuỗi thay vì vị trí trong bộ nhớ.
```java
public class StringComparison {
    public static void main(String[] args) {
        String s1 = "Hello";
        String s3 = new String("Hello");

        System.out.println(s1.equals(s3)); // ✅ true (cùng nội dung "Hello")
    }
}
```

**Giải thích**:
*	Mặc dù s1 và s3 nằm ở hai vùng nhớ khác nhau, nhưng vì nội dung của chúng giống nhau ("Hello"), .equals() vẫn trả về true.




