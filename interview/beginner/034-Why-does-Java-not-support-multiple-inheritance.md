# Câu hỏi
Tại sao Java không hỗ trợ đa kế thừa?

# Trả lời ngắn gọn  
Java không hỗ trợ đa kế thừa giữa các lớp để tránh vấn đề "Diamond Problem" và đơn giản hóa thiết kế. Thay vào đó, Java sử dụng kế thừa đơn (single inheritance) kết hợp với interface để đạt được tính linh hoạt.

 
## Triển khai ý 1: Tránh vấn đề Diamond Problem
*	Trong đa kế thừa, một lớp có thể kế thừa từ nhiều lớp cha.
*	Nếu các lớp cha có phương thức trùng tên, lớp con không biết nên gọi phương thức nào → Gây ra Diamond Problem.
*	Ngôn ngữ như C++ hỗ trợ đa kế thừa nhưng yêu cầu cơ chế phức tạp để giải quyết vấn đề này.

**Ví dụ C++ (gây Diamond Problem)**:
```java
#include <iostream>
using namespace std;

class A {
public:
    void show() { cout << "Lớp A" << endl; }
};

class B : public A { };
class C : public A { };

class D : public B, public C { }; // Lớp D kế thừa từ cả B và C

int main() {
    D obj;
    obj.show(); // Lỗi: Gây mơ hồ, không biết gọi show() của B hay C
    return 0;
}
```

**Kết quả**: Lỗi biên dịch vì D có hai bản sao của show() từ A.

📌 Java giải quyết vấn đề này bằng cách cấm đa kế thừa giữa các lớp.

✅ Trong Java, chỉ có kế thừa đơn, mỗi lớp chỉ có một lớp cha duy nhất, giúp tránh Diamond Problem.

## Triển khai ý 2: Đơn giản hóa thiết kế và bảo trì mã nguồn
*	Đa kế thừa khiến code phức tạp, khó đọc và khó bảo trì.
*	Gây xung đột khi hai lớp cha có cùng phương thức nhưng thực hiện khác nhau.
*	Java thay thế đa kế thừa bằng Interface, cho phép kế thừa từ nhiều nguồn mà không gây xung đột.

**Ví dụ trong Java (sử dụng Interface thay thế đa kế thừa):**
```java
interface A {
    void show();
}

interface B {
    void show();
}

class C implements A, B { // Kế thừa nhiều interface (được phép)
    public void show() { // Phải override để tránh xung đột
        System.out.println("Lớp C định nghĩa show()");
    }
}

public class Main {
    public static void main(String[] args) {
        C obj = new C();
        obj.show();
    }
}

```

**Kết quả**:
```java
Lớp C định nghĩa show()
```

Interface không chứa logic thực thi, nên Java tránh được Diamond Problem mà vẫn hỗ trợ tính linh hoạt như đa kế thừa.
