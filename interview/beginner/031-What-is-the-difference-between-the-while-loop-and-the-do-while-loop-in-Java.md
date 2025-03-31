# Câu hỏi
Sự khác biệt giữa vòng lặp while và vòng lặp do-while trong Java là gì?

# Trả lời ngắn gọn  
Vòng lặp while và do-while đều dùng để thực thi một đoạn mã lặp đi lặp lại dựa trên điều kiện. 

Sự khác biệt chính:
*	while kiểm tra điều kiện trước khi thực hiện vòng lặp → Nếu điều kiện sai ngay từ đầu, vòng lặp không chạy lần nào.
*	do-while thực thi ít nhất một lần rồi mới kiểm tra điều kiện → Đảm bảo vòng lặp luôn chạy ít nhất một lần.


## Triển khai ý 1: while kiểm tra điều kiện trước
*	while kiểm tra điều kiện trước khi thực hiện vòng lặp.
*	Nếu điều kiện sai ngay từ đầu, vòng lặp sẽ không chạy lần nào.

**Ví dụ**
```java
int i = 10;
while (i < 5) {  // Điều kiện sai ngay từ đầu
    System.out.println("Giá trị của i: " + i);
    i++;
}
System.out.println("Vòng lặp kết thúc!");

```

**Kết quả**
```java
Vòng lặp kết thúc!
```
**Lưu ý**:
*	i = 10 nhưng điều kiện i < 5 không đúng ngay từ đầu.
*	Do đó, vòng lặp không chạy lần nào.


## Triển khai ý 2: do-while luôn chạy ít nhất một lần
*	do-while chạy ít nhất một lần dù điều kiện sai.
*	Điều kiện chỉ được kiểm tra sau lần lặp đầu tiên.

**Ví dụ**
```java
int i = 10;
do {
    System.out.println("Giá trị của i: " + i);
    i++;
} while (i < 5);  // Điều kiện sai ngay từ đầu
System.out.println("Vòng lặp kết thúc!");
```

**Kết quả**
```java
Giá trị của i: 10
Vòng lặp kết thúc!
```

**Lưu ý**:
*	Mặc dù i = 10 không thỏa mãn điều kiện i < 5, vòng lặp vẫn chạy một lần.
*	Sau lần đầu tiên, điều kiện được kiểm tra và vòng lặp dừng lại.
