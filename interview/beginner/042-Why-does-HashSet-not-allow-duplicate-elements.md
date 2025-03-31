# Câu hỏi
Tại sao HashSet không cho phép phần tử trùng lặp?

# Trả lời ngắn gọn  
HashSet không cho phép phần tử trùng lặp vì nó sử dụng cơ chế băm (hashing) và so sánh bằng phương thức equals() để kiểm tra xem một phần tử đã tồn tại hay chưa. Khi thêm một phần tử mới, HashSet kiểm tra xem phần tử đó có cùng hash code với phần tử khác trong tập hợp hay không. Nếu có, nó tiếp tục kiểm tra bằng equals(). Nếu equals() trả về true, phần tử mới sẽ không được thêm vào.


## Triển khai ý 1: Cơ chế băm của HashSet
**Cách hoạt động**:
*	HashSet sử dụng bảng băm (hash table) để lưu trữ các phần tử.
*	Khi thêm một phần tử, Java sẽ tính toán giá trị hash code bằng phương thức hashCode().
*	Nếu hash code đã tồn tại, nó tiếp tục gọi equals() để kiểm tra xem hai phần tử có thực sự giống nhau không.

**Ví dụ**
```java
import java.util.HashSet;

public class HashSetExample {
    public static void main(String[] args) {
        HashSet<String> set = new HashSet<>();
        set.add("Java");
        set.add("Python");
        set.add("Java"); // Phần tử trùng lặp, không được thêm vào

        System.out.println(set); // Output: [Java, Python]
    }
}

```
**Giải thích**:
*	Java được thêm vào tập hợp lần đầu tiên.
*	Khi thêm Java lần thứ hai, hashCode() của nó giống với phần tử đã tồn tại, equals() trả về true, nên nó không được thêm vào.


## Triển khai ý 2: equals() và hashCode() đảm bảo duy nhất
**Cách hoạt động**:
*	HashSet sử dụng hashCode() để nhóm phần tử vào bucket (vùng chứa trong bảng băm).
*	Sau đó, nó gọi equals() để đảm bảo không có phần tử trùng nhau.

**Ví dụ minh họa với lớp tùy chỉnh:**
```java
import java.util.HashSet;
import java.util.Objects;

class Student {
    String name;

    Student(String name) {
        this.name = name;
    }

    @Override
    public int hashCode() {
        return Objects.hash(name);
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Student student = (Student) obj;
        return Objects.equals(name, student.name);
    }
}

public class HashSetCustomExample {
    public static void main(String[] args) {
        HashSet<Student> students = new HashSet<>();
        students.add(new Student("Alice"));
        students.add(new Student("Bob"));
        students.add(new Student("Alice")); // Trùng lặp, không được thêm vào

        System.out.println(students.size()); // Output: 2
    }
}

```

**Giải thích**: Khi thêm Student("Alice") lần thứ hai, hashCode() giống nhau và equals() trả về true, nên HashSet không thêm phần tử này.

