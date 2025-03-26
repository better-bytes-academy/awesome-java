# Câu hỏi
Từ khóa instanceof trong Java là gì?

# Trả lời ngắn gọn  
Từ khóa instanceof trong Java được dùng để kiểm tra xem một đối tượng có phải là thể hiện của một lớp hoặc một lớp con của nó hay không.
**Cú pháp**:
```java
object instanceof ClassName
```
Nếu object thuộc về ClassName hoặc lớp con của nó, kết quả trả về true, ngược lại trả về false.

## Triển khai ý 1: Kiểm tra kiểu dữ liệu của đối tượng
*	instanceof giúp kiểm tra xem một đối tượng có thuộc về một lớp cụ thể hay không.
*	Hữu ích khi làm việc với kế thừa (inheritance) và đa hình (polymorphism).

**Ví dụ**
```java
class Animal { }
class Dog extends Animal { }

public class TestInstanceof {
    public static void main(String[] args) {
        Dog d = new Dog();
        System.out.println(d instanceof Dog);     // true
        System.out.println(d instanceof Animal);  // true (do Dog kế thừa Animal)
    }
}

```
**Kết quả**
```java
true  
true
```
**Lưu ý**:
*	instanceof cũng kiểm tra quan hệ kế thừa giữa các lớp.
*	Dog là một Animal, nên d instanceof Animal trả về true.


## Triển khai ý 2: Kiểm tra đối tượng trước khi ép kiểu (Type Casting)
*	Tránh lỗi ClassCastException khi ép kiểu.
*	Trước khi ép kiểu từ lớp cha xuống lớp con, dùng instanceof để kiểm tra xem đối tượng có thuộc lớp con đó không.

**Ví dụ**
```java
class Animal { }
class Dog extends Animal { }
class Cat extends Animal { }

public class TestCasting {
    public static void main(String[] args) {
        Animal a = new Dog(); // Đối tượng thuộc lớp Dog nhưng được tham chiếu bởi Animal

        if (a instanceof Dog) {
            Dog d = (Dog) a; // Ép kiểu an toàn
            System.out.println("Ép kiểu Dog thành công!");
        }

        if (a instanceof Cat) {
            Cat c = (Cat) a; // Không ép kiểu vì a không phải là Cat
            System.out.println("Ép kiểu Cat thành công!");
        } else {
            System.out.println("Ép kiểu Cat thất bại!");
        }
    }
}
```

**Kết quả**
```java
Ép kiểu Dog thành công!  
Ép kiểu Cat thất bại!
```

**Lưu ý**:
*	a được tham chiếu bởi Animal nhưng thực tế là Dog.
*	a instanceof Dog → true, nên ép kiểu an toàn.
*	a instanceof Cat → false, nên tránh lỗi ClassCastException.


