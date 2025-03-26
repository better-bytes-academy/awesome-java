# Câu hỏi
Tại sao phương thức equals() cần được override khi làm việc với đối tượng?

# Trả lời ngắn gọn  
Phương thức equals() trong Java mặc định được kế thừa từ Object, nhưng nó chỉ so sánh địa chỉ bộ nhớ của hai đối tượng thay vì nội dung bên trong. Do đó, khi làm việc với đối tượng, chúng ta cần override equals() để định nghĩa cách so sánh phù hợp, đảm bảo tính đúng đắn khi so sánh dữ liệu thực sự bên trong đối tượng.

## Triển khai ý 1: Mặc định equals() so sánh địa chỉ bộ nhớ
Mặc định, equals() trong lớp Object chỉ kiểm tra xem hai biến tham chiếu có trỏ đến cùng một đối tượng hay không, thay vì so sánh giá trị thực tế bên trong đối tượng.

**Ví dụ**
```java
class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        Person p1 = new Person("Alice");
        Person p2 = new Person("Alice");

        System.out.println(p1.equals(p2)); // false
    }
}

```
**Giải thích**: Dù cả hai đối tượng p1 và p2 đều có giá trị name = "Alice", nhưng equals() trả về false vì nó đang so sánh địa chỉ bộ nhớ của hai biến tham chiếu khác nhau.



## Triển khai ý 2: Override equals() để so sánh nội dung thực tế
Khi override equals(), chúng ta có thể định nghĩa cách so sánh hợp lý, chẳng hạn như dựa trên giá trị của thuộc tính.

**Ví dụ**
```java
class Person {
    String name;

    public Person(String name) {
        this.name = name;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true; // Cùng tham chiếu => true
        if (obj == null || getClass() != obj.getClass()) return false; // Khác kiểu => false

        Person person = (Person) obj; // Ép kiểu
        return this.name.equals(person.name); // So sánh giá trị thuộc tính
    }
}

public class Main {
    public static void main(String[] args) {
        Person p1 = new Person("Alice");
        Person p2 = new Person("Alice");

        System.out.println(p1.equals(p2)); // true
    }
}

```
**Giải thích**: Sau khi override equals(), hai đối tượng p1 và p2 được coi là bằng nhau vì chúng có cùng giá trị thuộc tính name.

**Kết luận**
*	Mặc định, equals() chỉ so sánh địa chỉ bộ nhớ, dẫn đến kết quả sai khi so sánh đối tượng có cùng dữ liệu.
*	Việc override equals() giúp đảm bảo so sánh đúng nội dung bên trong đối tượng, đặc biệt quan trọng khi sử dụng trong tập hợp như HashSet, ArrayList…

