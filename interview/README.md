# Câu hỏi phỏng vấn Java
Mục này chứa các câu hỏi phỏng vấn Java từ cơ bản tới nâng cao. Cách contribute vào repo:
1. Fork repo về GitHub cá nhân.
2. Thêm câu hỏi và câu trả lời tương ứng: Câu trả lời có 2 phần:
    - Trong file này: câu trả lời ngắn gọn
    - Tạo file tương ứng trong folder của level theo template

## Level beginner
| Câu hỏi | Tag | Câu trả lời |
|---------|-----|------------|
| [Java là gì và tại sao nó được gọi là "platform-independent"](beginner/001-what-is-java.md) | java_basic | Java là ngôn ngữ lập trình hướng đối tượng, và nó "platform-independent" nhờ JVM - Java Virtual Machine, cho phép mã bytecode chạy trên bất kỳ hệ điều hành nào có JVM |
| Sự khác biệt giữa JDK, JRE và JVM | java_basic | JDK là bộ công cụ phát triển, JRE là môi trường chạy Java, còn JVM là máy ảo thực thi bytecode |
| Khai báo biến trong Java như thế nào? Hãy cho một ví dụ | java_basic | Biến được khai báo với kiểu dữ liệu và tên, ví dụ: int number = 10; |
| Các kiểu dữ liệu cơ bản có sẵn trong Java? | java_basic | Java cung cấp 8 kiểu dữ liệu nguyên thủy (primitive data types), bao gồm: byte, short, int, long, float, double, char, và boolean. Những kiểu này giúp Java xử lý dữ liệu hiệu quả và tối ưu bộ nhớ. |
| Phương thức main trong Java là gì?  | java_basic | Phương thức main là điểm bắt đầu của mọi chương trình Java. Khi chạy chương trình, JVM sẽ tìm và thực thi phương thức main(). |
| Sự khác biệt giữa kiểu dữ liệu nguyên thủy và kiểu dữ liệu tham chiếu trong Java là gì? | java_basic | - **Kiểu dữ liệu nguyên thủy**: Lưu trữ giá trị trực tiếp trong bộ nhớ. <br> - **Kiểu dữ liệu tham chiếu**: Lưu trữ địa chỉ của đối tượng trong bộ nhớ Heap, không phải giá trị trực tiếp. |
| Sự khác biệt giữa Stack và Heap trong Java là gì? | java_basic | -	**Stack**: Bộ nhớ dành cho các biến cục bộ và lời gọi hàm, có tốc độ truy cập nhanh, quản lý theo cơ chế LIFO. <br> -	**Heap**: Bộ nhớ dành cho đối tượng và dữ liệu động, có thể truy cập toàn cục nhưng chậm hơn do cần quản lý bộ nhớ tự động (Garbage Collection). |
| Giải thích trình dọn rác (Garbage Collector) trong Java? | java_basic | Garbage Collector (GC) trong Java là một cơ chế tự động quản lý bộ nhớ, giúp loại bỏ các đối tượng không còn được tham chiếu để giải phóng bộ nhớ Heap. Điều này giúp lập trình viên không cần xóa thủ công như trong C/C++. |
| Khối static là gì? | java_basic | Khối static trong Java là một khối mã được thực thi chỉ một lần khi lớp được tải vào bộ nhớ, trước cả khi đối tượng của lớp được tạo ra hoặc phương thức main() chạy. |
| Các lớp Wrapper trong Java là gì? | java_basic | Các lớp Wrapper trong Java là các lớp trong gói java.lang dùng để bao bọc (wrap) kiểu dữ liệu nguyên thủy thành đối tượng. Điều này giúp làm việc với kiểu dữ liệu nguyên thủy dễ dàng hơn trong các cấu trúc yêu cầu đối tượng, như Collection (List, Set, Map). |
| Lệnh import được sử dụng ở đâu trong một chương trình Java? | java_basic | Lệnh import trong Java được sử dụng ở đầu tệp mã nguồn (trước khi khai báo lớp) để nhập các lớp hoặc gói cần thiết từ thư viện Java hoặc từ mã nguồn khác. Điều này giúp lập trình viên sử dụng các lớp mà không cần viết đầy đủ đường dẫn gói của chúng. |
| Tại sao Generic được sử dụng trong Java? | java_basic | Generic trong Java giúp tăng tính an toàn kiểu dữ liệu và tái sử dụng mã bằng cách cho phép xác định kiểu dữ liệu tại thời điểm biên dịch thay vì sử dụng kiểu Object. Điều này giúp tránh lỗi ép kiểu và làm cho mã nguồn dễ đọc hơn. |
| Tại sao Java không hỗ trợ con trỏ? | java_basic | Java không hỗ trợ con trỏ để đảm bảo an toàn bộ nhớ và giảm độ phức tạp lập trình. Việc sử dụng con trỏ có thể gây lỗi truy cập bộ nhớ hoặc rò rỉ bộ nhớ, nên Java thay thế bằng tham chiếu và Garbage Collector để quản lý bộ nhớ tự động.; |
| Câu lệnh break và continue là gì? | java_basic | - **break**: Dùng để thoát hoàn toàn khỏi vòng lặp hoặc switch-case ngay khi điều kiện được thỏa mãn. <br> - **continue**: Dùng để bỏ qua lần lặp hiện tại và chuyển sang lần lặp tiếp theo mà không thực hiện các lệnh phía sau nó. |
| Khai báo biến trong Java như thế nào? Hãy cho một ví dụ | java_basic | Biến được khai báo với kiểu dữ liệu và tên, ví dụ: int number = 10; |
| Khai báo biến trong Java như thế nào? Hãy cho một ví dụ | java_basic | Biến được khai báo với kiểu dữ liệu và tên, ví dụ: int number = 10; |
| Khai báo biến trong Java như thế nào? Hãy cho một ví dụ | java_basic | Biến được khai báo với kiểu dữ liệu và tên, ví dụ: int number = 10; |
| Khai báo biến trong Java như thế nào? Hãy cho một ví dụ | java_basic | Biến được khai báo với kiểu dữ liệu và tên, ví dụ: int number = 10; |
| Khai báo biến trong Java như thế nào? Hãy cho một ví dụ | java_basic | Biến được khai báo với kiểu dữ liệu và tên, ví dụ: int number = 10; |
| Khai báo biến trong Java như thế nào? Hãy cho một ví dụ | java_basic | Biến được khai báo với kiểu dữ liệu và tên, ví dụ: int number = 10; |

## Level intermediate
| Câu hỏi | Tag | Câu trả lời |
|---------|-----|------------|
| Explain the internal working of ConcurrentHashMap. How does it achieve thread safety, and what are its performance trade-offs | java_collection | [Xem chi tiết](intermediate/000-concurrent-hashmap.md) |
| Câu hỏi 2 | Tag 2 | Câu trả lời 2 |
| Câu hỏi 3 | Tag 3 | Câu trả lời 3 |
## Level advance
