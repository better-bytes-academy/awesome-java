# Câu hỏi
++i và i++ khác nhau như thế nào?

# Trả lời ngắn gọn  
*	++i (tiền tố): Tăng giá trị của i trước khi sử dụng.
*	i++ (hậu tố): Sử dụng giá trị hiện tại của i, sau đó mới tăng.


## Triển khai ý 1: ++i tăng giá trị trước khi sử dụng
**Cách hoạt động**:
*	Tăng i trước, rồi trả về giá trị mới của i.
*	Thường nhanh hơn i++ trong một số trường hợp tối ưu hóa hiệu suất.

**Ví dụ**
```java
int i = 5;
int result = ++i;  // Tăng i trước, rồi gán vào result
System.out.println("i = " + i);       // Output: i = 6
System.out.println("result = " + result); // Output: result = 6

```
**Giải thích**:
*	++i tăng i lên 6 trước.
*	Sau đó, 6 được gán vào result.


## Triển khai ý 2: i++ sử dụng giá trị trước, tăng sau
**Cách hoạt động**:
*	Trả về giá trị hiện tại của i, sau đó mới tăng lên.
*	Thường dùng khi giá trị ban đầu cần được sử dụng trước.

**Ví dụ**
```java
int i = 5;
int result = i++;  // Gán i vào result trước, sau đó tăng i
System.out.println("i = " + i);       // Output: i = 6
System.out.println("result = " + result); // Output: result = 5

```

**Giải thích**:
*	i++ gán 5 vào result trước.
*	Sau đó, i mới tăng lên 6.














