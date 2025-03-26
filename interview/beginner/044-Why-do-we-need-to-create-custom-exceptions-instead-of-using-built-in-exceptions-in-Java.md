# Câu hỏi
Tại sao chúng ta cần tạo ngoại lệ tùy chỉnh thay vì sử dụng ngoại lệ có sẵn?

# Trả lời ngắn gọn  
Ngoại lệ tùy chỉnh (Custom Exception) giúp:
1.	Diễn giải rõ ràng lỗi xảy ra trong chương trình bằng cách tạo các ngoại lệ có tên phù hợp với nghiệp vụ.
2.	Tạo logic xử lý lỗi cụ thể cho ứng dụng, thay vì chỉ sử dụng ngoại lệ chung chung có sẵn.


## Triển khai ý 1: Giúp mã dễ hiểu và phù hợp với nghiệp vụ
Nếu chỉ dùng các ngoại lệ có sẵn như IllegalArgumentException, NullPointerException, người đọc mã khó hiểu được lỗi liên quan đến nghiệp vụ gì.

**Ví dụ: Sử dụng ngoại lệ có sẵn, khó hiểu**
```java
public class BankAccount {
    private double balance = 5000;

    public void withdraw(double amount) {
        if (amount > balance) {
            throw new IllegalArgumentException("Số tiền rút không hợp lệ!");
        }
        balance -= amount;
    }
}
```

❌ Ở đây, IllegalArgumentException không mô tả rõ lỗi thuộc về tài khoản ngân hàng.

✅ Cách cải tiến: Tạo ngoại lệ tùy chỉnh InsufficientFundsException

```java
class InsufficientFundsException extends Exception {
    public InsufficientFundsException(String message) {
        super(message);
    }
}

public class BankAccount {
    private double balance = 5000;

    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException("Số dư không đủ để rút tiền!");
        }
        balance -= amount;
    }
}
```
Bây giờ, khi lỗi xảy ra, ta biết ngay nó liên quan đến số dư tài khoản.

## Triển khai ý 2: Giúp xử lý lỗi tốt hơn trong chương trình
Ngoại lệ tùy chỉnh cho phép viết catch để xử lý từng loại lỗi một cách riêng biệt, thay vì bắt chung chung.

**Ví dụ: Xử lí ngoại lệ cụ thể**
```java
public class ATM {
    public static void main(String[] args) {
        BankAccount account = new BankAccount();
        try {
            account.withdraw(10000); // Yêu cầu rút tiền vượt quá số dư
        } catch (InsufficientFundsException e) {
            System.out.println("Lỗi: " + e.getMessage()); // Xử lý lỗi thiếu tiền
        }
    }
}

```

**Kết quả**
```java
Lỗi: Số dư không đủ để rút tiền!
```

**Kết luận**: Ngoại lệ tùy chỉnh giúp mã nguồn dễ hiểu hơn, phản ánh rõ ràng nghiệp vụ và cho phép xử lý lỗi chuyên biệt hơn trong ứng dụng Java.


