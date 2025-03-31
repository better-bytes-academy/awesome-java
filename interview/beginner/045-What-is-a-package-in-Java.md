# Câu hỏi
Package trong Java là gì?

# Trả lời ngắn gọn  
Package trong Java là một nhóm các lớp, giao diện và các package con được tổ chức theo một cấu trúc thư mục giúp quản lý mã nguồn dễ dàng hơn, tránh xung đột tên lớp và hỗ trợ khả năng tái sử dụng mã.
 
## Triển khai ý 1: Package giúp tổ chức mã nguồn một cách khoa học
*	Package trong Java tương tự như thư mục trên máy tính, giúp phân loại các lớp có chức năng tương tự vào cùng một nhóm.
*	Điều này giúp mã nguồn dễ quản lý, bảo trì và đọc hiểu hơn.

**Ví dụ**
```java
package com.myapp.models; // Định nghĩa package

public class User {
    public String name;

    public User(String name) {
        this.name = name;
    }

    public void displayUser() {
        System.out.println("Tên người dùng: " + name);
    }
}

```
**Giải thích**:
*	package com.myapp.models; giúp tổ chức lớp User vào thư mục models của ứng dụng myapp.
*	Điều này giúp khi dự án lớn, chúng ta có thể dễ dàng tìm kiếm và sử dụng lại mã.



## Triển khai ý 2: Package giúp tránh xung đột tên lớp
Khi làm việc với nhiều thư viện, có thể có hai lớp trùng tên. Package giúp phân biệt chúng.

**Ví dụ**
```java
import java.util.Date; // Sử dụng Date của Java
import java.sql.Date;  // Sử dụng Date của SQL

public class Main {
    public static void main(String[] args) {
        java.util.Date date1 = new java.util.Date(); // Định dạng ngày của Java
        java.sql.Date date2 = new java.sql.Date(System.currentTimeMillis()); // Định dạng ngày của SQL
        
        System.out.println("java.util.Date: " + date1);
        System.out.println("java.sql.Date: " + date2);
    }
}

```
**Giải thích**:
*	Java có hai lớp Date trong java.util và java.sql.
*	Nhờ package, ta có thể phân biệt và sử dụng cả hai mà không bị lỗi.


**Kết luận**
*	Package giúp tổ chức mã nguồn, tránh xung đột tên và hỗ trợ tái sử dụng mã.
*	Sử dụng package để định nghĩa thư mục chứa lớp và import để sử dụng lại lớp từ các package khác.







