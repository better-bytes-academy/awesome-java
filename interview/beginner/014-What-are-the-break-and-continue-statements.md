# Câu hỏi
Câu lệnh break và continue là gì?

# Trả lời ngắn gọn  
*	break: Dùng để thoát hoàn toàn khỏi vòng lặp hoặc switch-case ngay khi điều kiện được thỏa mãn.
*	continue: Dùng để bỏ qua lần lặp hiện tại và chuyển sang lần lặp tiếp theo mà không thực hiện các lệnh phía sau nó.



## Triển khai ý 1: break thoát khỏi vòng lặp 
Khi gặp break, chương trình sẽ dừng vòng lặp ngay lập tức mà không kiểm tra hoặc thực thi tiếp các phần còn lại.  

**Ví dụ thực tế:**  
Tìm số đầu tiên chia hết cho 3 trong một danh sách số.
```java
public class BreakExample {
    public static void main(String[] args) {
        int[] numbers = {1, 5, 7, 9, 12, 15};

        for (int num : numbers) {
            if (num % 3 == 0) {
                System.out.println("Số chia hết cho 3 đầu tiên: " + num);
                break; // Thoát khỏi vòng lặp ngay khi tìm thấy số đầu tiên
            }
        }
    }
}

```  
✅ Khi tìm thấy số chia hết cho 3 đầu tiên (9), vòng lặp dừng ngay lập tức.

📌 Ứng dụng thực tế của break: Dùng để dừng tìm kiếm khi đã đạt được điều kiện mong muốn, giúp tăng hiệu suất chương trình.

## Triển khai ý 2: continue bỏ qua lần lặp hiện tại
Khi gặp continue, chương trình sẽ bỏ qua phần còn lại của lần lặp hiện tại và tiếp tục vòng lặp với giá trị tiếp theo. 

**Ví dụ thực tế:**  
In các số từ 1 đến 10, nhưng bỏ qua số chia hết cho 3.
```java
public class ContinueExample {
    public static void main(String[] args) {
        for (int i = 1; i <= 10; i++) {
            if (i % 3 == 0) {
                continue; // Bỏ qua số chia hết cho 3
            }
            System.out.print(i + " ");
        }
    }
}

```  
✅ Chương trình sẽ in: 1 2 4 5 7 8 10 (bỏ qua 3, 6, 9).

📌 Ứng dụng thực tế của continue: Dùng khi muốn bỏ qua một số giá trị nhất định mà không làm gián đoạn toàn bộ vòng lặp.




**Kết luận**
*	break: Dùng để thoát khỏi vòng lặp hoặc switch-case ngay lập tức.
*	continue: Dùng để bỏ qua lần lặp hiện tại và tiếp tục vòng lặp.
*	Cả hai lệnh này giúp tối ưu hóa luồng điều khiển trong chương trình, giúp mã nguồn dễ hiểu và hiệu suất tốt hơn. 

