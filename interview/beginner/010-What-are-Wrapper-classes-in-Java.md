# Câu hỏi
Các lớp Wrapper trong Java là gì?

# Trả lời ngắn gọn  
Các lớp Wrapper trong Java là các lớp trong gói java.lang dùng để bao bọc (wrap) kiểu dữ liệu nguyên thủy thành đối tượng. Điều này giúp làm việc với kiểu dữ liệu nguyên thủy dễ dàng hơn trong các cấu trúc yêu cầu đối tượng, như Collection (List, Set, Map).


## Triển khai ý 1: Danh sách các lớp Wrapper
Mỗi kiểu dữ liệu nguyên thủy (primitive type) trong Java đều có một lớp Wrapper tương ứng:

**Ví dụ thực tế:**  
```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào, Java!");
    }
}
```  


## Triển khai ý 2: JVM đóng vai trò trung gian  


