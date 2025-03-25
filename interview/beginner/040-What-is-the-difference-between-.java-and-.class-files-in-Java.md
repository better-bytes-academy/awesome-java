# Câu hỏi
Tệp .java và .class trong Java có gì khác nhau?

# Trả lời ngắn gọn  
*	Tệp .java: Chứa mã nguồn Java do lập trình viên viết.
*	Tệp .class: Chứa mã bytecode sau khi biên dịch từ .java, có thể chạy trên JVM.

**Quá trình chuyển đổi**: Tệp .java được biên dịch bằng javac để tạo ra tệp .class, sau đó JVM đọc và thực thi mã bytecode trong .class.
 
## Triển khai ý 1: .java là mã nguồn do lập trình viên viết
**Đặc điểm**:
*	Chứa mã nguồn Java với các lớp, phương thức, biến…
*	Được lập trình viên chỉnh sửa, biên dịch trước khi chạy.
*	Phải có phần mở rộng .java.

**Ví dụ: Tạo tệp HelloWorld.java**
```java
// Đây là mã nguồn trong tệp HelloWorld.java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào, Java!");
    }
}

```
**Giải thích**:
*	HelloWorld.java chứa mã nguồn chương trình.
*	Chưa thể chạy trực tiếp, cần biên dịch thành .class.

## Triển khai ý 2: .class là mã bytecode do trình biên dịch tạo ra
**Đặc điểm**:
*	Được tạo ra sau khi biên dịch bằng javac.
*	Chứa mã bytecode có thể chạy trên JVM.
*	Không thể đọc trực tiếp như .java, chỉ dành cho JVM xử lý.

**Ví dụ**

**Bước 1:** Biên dịch tệp .java
```java
javac HelloWorld.java
```
Lệnh này tạo ra HelloWorld.class.

**Bước 2:** Chạy chương trình bằng JVM
```java
java HelloWorld
```

**Kết quả**
```java
Xin chào, Java!
```
**Giải thích**:
*	javac chuyển mã nguồn từ HelloWorld.java thành HelloWorld.class (bytecode).
*	JVM đọc và thực thi HelloWorld.class, hiển thị kết quả.

