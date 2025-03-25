# Câu hỏi
Các kiểu dữ liệu cơ bản có sẵn trong Java?

# Trả lời ngắn gọn  
Java cung cấp 8 kiểu dữ liệu nguyên thủy (primitive data types), bao gồm: byte, short, int, long, float, double, char, và boolean. Những kiểu này giúp Java xử lý dữ liệu hiệu quả và tối ưu bộ nhớ.

# Chi tiết kèm ví dụ thực tế  
Trong Java, kiểu dữ liệu nguyên thủy là những kiểu được tích hợp sẵn trong ngôn ngữ, giúp quản lý bộ nhớ và hiệu suất tốt hơn so với kiểu dữ liệu đối tượng..

## Triển khai ý 1: Nhóm kiểu số nguyên 
Các kiểu số nguyên trong Java bao gồm:
1. byte (8-bit): Phạm vi từ -128 đến 127
2. short (16-bit): Phạm vi từ -32,768 đến 32,767
3. int (32-bit): Phạm vi từ -2^31 đến 2^31-1
4. long (64-bit): Phạm vi từ -2^63 đến 2^63-1
 
**Ví dụ thực tế:**  
Bạn viết một chương trình Java đơn giản:  
```java
public class IntegerExample {
    public static void main(String[] args) {
        int age = 25;
        long population = 7800000000L;
        System.out.println("Tuổi: " + age);
        System.out.println("Dân số thế giới: " + population);
    }
}
```  
**Kết quả**
```java
Tuổi: 25  
Dân số thế giới: 7800000000  

```

## Triển khai ý 2: Nhóm kiểu số thực và kiểu ký tự 
1.	float (32-bit): Dùng cho số thực có độ chính xác đơn.
2.	double (64-bit): Dùng cho số thực có độ chính xác kép (mặc định cho số thực).
3.	char (16-bit): Đại diện cho một ký tự Unicode (chữ cái, số, ký tự đặc biệt).
 
**Ví dụ thực tế:**  
```java
public class FloatCharExample {
    public static void main(String[] args) {
        float pi = 3.14f;
        char grade = 'A';
        System.out.println("Số pi: " + pi);
        System.out.println("Xếp loại: " + grade);
    }
}
```
**Kết quả**
```java
Số pi: 3.14  
Xếp loại: A  
```

