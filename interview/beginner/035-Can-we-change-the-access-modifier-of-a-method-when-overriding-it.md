# Câu hỏi
Có thể thay đổi quyền truy cập (access modifier) của phương thức khi override không?

# Trả lời ngắn gọn  
Có thể thay đổi access modifier khi override, nhưng phải tuân theo nguyên tắc:
* Có thể mở rộng quyền truy cập (từ chặt hơn → rộng hơn).
* Không thể thu hẹp quyền truy cập (từ rộng hơn → chặt hơn).


## Triển khai ý 1: Có thể mở rộng quyền truy cập
*	Khi override một phương thức từ lớp cha, ta có thể mở rộng phạm vi truy cập để phương thức dễ được sử dụng hơn.
*	Ví dụ: từ protected lên public là hợp lệ.

**Ví dụ hợp lệ (Mở rộng quyền truy cập):**
```java
class Parent {
    protected void show() {  // Lớp con có thể mở rộng quyền truy cập
        System.out.println("Parent show()");
    }
}

class Child extends Parent {
    @Override
    public void show() {  // ✅ Hợp lệ: Từ protected → public
        System.out.println("Child show()");
    }
}

public class Main {
    public static void main(String[] args) {
        Parent obj = new Child();
        obj.show();  // Output: Child show()
    }
}

```
✅ Lý do hợp lệ: public rộng hơn protected, giúp phương thức dễ truy cập hơn.


## Triển khai ý 2: Không thể thu hẹp quyền truy cập
*	Nếu lớp cha khai báo phương thức public, lớp con không thể giảm cấp xuống protected hoặc private.
*	Điều này gây lỗi biên dịch vì vi phạm nguyên tắc thay thế Liskov (LSP) – nơi một lớp con phải duy trì hành vi của lớp cha.

**Ví dụ lỗi khi thu hẹp quyền truy cập:**
```java
class Parent {
    public void display() {
        System.out.println("Parent display()");
    }
}

class Child extends Parent {
    @Override
    private void display() {  // ❌ Lỗi: Không thể giảm từ public → private
        System.out.println("Child display()");
    }
}

```

**Kết quả**
```java
display() in Child cannot override display() in Parent  
attempting to assign weaker access privileges; was public

```
**Nguyên nhân**: public trong lớp cha có phạm vi rộng nhất, nên lớp con không thể giảm xuống private hoặc protected.


