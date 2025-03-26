# Câu hỏi
Sự khác nhau giữa Array và ArrayList trong Java?

# Trả lời ngắn gọn  
*	Array là cấu trúc dữ liệu tĩnh có kích thước cố định, trong khi ArrayList là danh sách động có thể thay đổi kích thước linh hoạt.
*	Array có hiệu suất tốt hơn khi truy cập phần tử, nhưng ArrayList cung cấp nhiều phương thức hỗ trợ giúp thao tác dữ liệu dễ dàng hơn.


## Triển khai ý 1: Kích thước và khả năng mở rộng
* Array có kích thước cố định ngay từ khi khởi tạo và không thể thay đổi.
* ArrayList có thể mở rộng hoặc thu nhỏ tùy theo số phần tử được thêm vào.

**Ví dụ:**
```java
// Mảng có kích thước cố định
int[] arr = new int[3]; 
arr[0] = 1;
arr[1] = 2;
arr[2] = 3;
// arr[3] = 4;  // ❌ Lỗi: Vượt quá kích thước mảng

// ArrayList có kích thước linh hoạt
import java.util.ArrayList;
ArrayList<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
list.add(3);
list.add(4);  // ✅ Không lỗi, danh sách tự mở rộng

```
**Nhận xét**:
*	Nếu bạn biết trước số lượng phần tử cố định, hãy sử dụng Array.
*	Nếu bạn cần danh sách động thay đổi linh hoạt, ArrayList là lựa chọn tốt hơn.


## Triển khai ý 2: Hiệu suất và phương thức hỗ trợ
* Array nhanh hơn ArrayList khi truy xuất phần tử, do không có overhead từ các phương thức bổ sung.
* ArrayList tiện lợi hơn vì có nhiều phương thức hỗ trợ như add(), remove(), contains(), size() giúp thao tác dễ dàng hơn.

**Ví dụ**:
```java
// Truy cập phần tử trong mảng
int[] arr = {1, 2, 3};
System.out.println(arr[1]);  // ✅ Kết quả: 2

// Truy cập phần tử trong ArrayList
ArrayList<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
list.add(3);
System.out.println(list.get(1));  // ✅ Kết quả: 2

```
**Nhận xét**:
*	Khi cần hiệu suất cao, đặc biệt với dữ liệu lớn, hãy sử dụng Array.
*	Khi cần thao tác danh sách dễ dàng với nhiều phương thức hỗ trợ, ArrayList là lựa chọn tốt hơn.




