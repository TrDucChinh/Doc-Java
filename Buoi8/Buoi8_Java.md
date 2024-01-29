

# MỘT SỐ CẤU TRÚC DỮ LIỆU THƯỜNG THẤY TRONG JAVA
## Cấu trúc dữ liệu là gì, sử dụng khi nào?
### Cấu trúc dữ liệu là gì?
**Tham Khảo: [Cấu trúc dữ liệu là gì?](https://mikotech.vn/cau-truc-du-lieu-la-gi/)**
- Cấu trúc dữ liệu (**Data structure**) là cách sắp xếp và lưu trữ dữ liệu trong máy tính để có thể truy cập và xử lý một cách hiệu quả.
- Nó định nghĩa cách mà dữ liệu được tổ chức, quan hệ giữa các phần tử dữ liệu và các thao tác có thể thực hiện trên dữ liệu đó.
- **Cấu trúc dữ liệu** cung cấp các phương thức và thuật toán để thao tác, truy xuất, chèn, xóa và sắp xếp dữ liệu.
### Các đặc tính của Data structure
- **Data structure** được phân loại theo đặc tính của chúng:
  - **Tuyến tính hoặc phi tuyến tính:** Đặc tính này mô tả liệu các mục dữ liệu được sắp xếp theo thứ tự hay không.
    - **Tuyến tính:** các cấu trúc dữ liệu mà các phần tử dữ liệu được sắp xếp theo một thứ tự nhất định `(danh sách, mảng, hàng đợi, stack...)`
    - **Không tuyến tính:** các cấu trúc dữ liệu mà các phần tử dữ liệu được sắp xếp theo một thứ tự không nhất định `(cây, đồ thị..)`
  - **Đồng nhất hoặc không đồng nhất:** Đặc tính này mô tả liệu tất cả các mục dữ liệu trong một kho lưu trữ nhất định có cùng loại hay không.
  - **Tĩnh hoặc động:** Đặc tính này mô tả cách các cấu trúc dữ liệu được biên dịch. 
    - **Data structure tĩnh** có kích thước, cấu trúc và vị trí bộ nhớ cố định tại thời điểm biên dịch. 
    - **Data structure động** có kích thước, cấu trúc và vị trí bộ nhớ có thể thu nhỏ hoặc mở rộng, tùy thuộc vào việc sử dụng.

![Alt text](image.png)

### Data structure được sử dụng khi nào?
- **Lưu trữ và truy xuất dữ liệu:** Cấu trúc dữ liệu như mảng, danh sách, hàng đợi và cây được sử dụng để lưu trữ và truy xuất dữ liệu một cách có tổ chức và hiệu quả. Chúng cho phép truy cập và thao tác dữ liệu một cách nhanh chóng và dễ dàng.
- **Tìm kiếm và sắp xếp:** Cấu trúc dữ liệu như cây nhị phân, hash map và đồ thị được sử dụng để thực hiện các phép tìm kiếm và sắp xếp dữ liệu. Chúng cung cấp các thuật toán tối ưu để tìm kiếm phần tử cụ thể hoặc sắp xếp dữ liệu theo một tiêu chí nhất định.
- **Quản lý dữ liệu:** Cấu trúc dữ liệu được sử dụng để quản lý và mô hình hóa các mối quan hệ và liên kết giữa các đối tượng hoặc dữ liệu. Chúng cho phép xác định các mối quan hệ phức tạp và thực hiện các phép toán liên quan đến dữ liệu liên quan.
- **Tối ưu hóa hiệu suất:** Sử dụng các cấu trúc dữ liệu phù hợp có thể cải thiện hiệu suất và thời gian chạy của chương trình. Lựa chọn đúng cấu trúc dữ liệu có thể giảm thiểu số lần truy cập đến dữ liệu, giảm bớt thời gian thực thi và tối ưu hóa tài nguyên máy tính.
- **Tạo các dạng dữ liệu phức tạp:** Cấu trúc dữ liệu cho phép tạo ra các dạng dữ liệu phức tạp hơn như hàng đợi ưu tiên, cấu trúc dữ liệu đa chiều, đồ thị định hướng, và nhiều hơn nữa. Chúng mở rộng khả năng biểu diễn và xử lý dữ liệu trong các ứng dụng phức tạp.

## Interface Iterable, Collection -> List, Set, Queue.
### Interface Iterable
- **Iterator Interface** của `Collections` trong Java cho phép chúng ta truy cập các phần tử của các tập hợp và được sử dụng để duyệt qua các phần tử trong tập hợp như `Map, List hoặc Set`.
- Nó giúp dễ dàng truy xuất các phần tử của một tập hợp và thực hiện các thao tác trên mỗi phần tử. Nó có một Interface con là `ListIterator.`
- Chúng ta chỉ có thể duyệt qua các phần tử theo hướng về phía trước bằng cách sử dụng `Interface` này. Ngoài ra, việc sử dụng `ListIterator Interface`, kế thừa `Iterator`, có thể duyệt phần tử theo cả hai hướng. Cả hai thao tác đọc và loại bỏ phần tử đều có thể được thực hiện bởi `Iterator Interface.`
- Tất cả các tập hợp trong Java bao gồm một phương thức iterator(). Phương thức này trả về một đối tượng của vòng lặp được sử dụng để lặp qua các phần tử của tập hợp.
### Các phương thức của Iterator
- Phương thức hasNext(): Trả về true nếu tồn tại một phần tử trong tập hợp.
- Phương thức next(): Trả về phần tử tiếp theo của tập hợp.
- Phương thức remove(): Loại bỏ phần tử cuối cùng được trả về bởi next().
- Phương thức forEachRemaining(): Thực hiện hành động được chỉ định cho từng phần tử còn lại của tập hợp.
>**Ví dụ:**
```Java
import java.util.ArrayList; 
import java.util.Iterator; 
class Main {     
        public static void main(String[] args) {
            ArrayList<Integer> so_nguyen = new ArrayList<>();         
            so_nguyen.add(34);         
            so_nguyen.add(25);         
            so_nguyen.add(58);         
            System.out.println(so_nguyen);         
            Iterator<Integer> phan_tu = so_nguyen.iterator();         
            int i = phan_tu.next();         
            System.out.println(i);         
            phan_tu.remove();         
            while(phan_tu.hasNext()) {
                phan_tu.forEachRemaining((gia_tri) -> System.out.print(gia_tri + " "));         
            }     
        } 
}

[34, 25, 58]
34
25 58
```
- `phan_tu.forEachRemaining((gia_tri) -> System.out.print(gia_tri + " "));` chúng ta đã truyền biểu thức lambda làm đối số của phương thức forEachRemaining(). Phương thức này sẽ in tất cả các phần tử còn lại của danh sách mảng.
### Collection -> List, Set, Queue
- **Collection Interface** là `Interface gốc của Collection Framework`. Sẽ không có sự triển khai trực tiếp vào Interface này. Tuy nhiên, nó được triển khai thông qua các `Interface con như List, Set hoặc Queue`.

![Alt text](image-1.png)

**1. List Interface**
List Interface là một tập hợp có thứ tự cho phép chúng ta thêm và bớt các phần tử như một mảng.

**2. Set Interface**
Set Interface cho phép chúng ta lưu trữ các phần tử trong các tập hợp khác nhau tương tự như tập hợp trong toán học. Nó không thể có các phần tử trùng lặp.

**3. Queue Interface**
Queue Interface được sử dụng khi chúng ta muốn lưu trữ và truy cập các phần tử theo cách Vào trước, Ra sau (FIFO)

### Các phương thức của Collection Interface
- **Collection Interface** bao gồm nhiều phương thức khác nhau có thể được sử dụng để thực hiện các thao tác khác nhau trên các đối tượng. Các phương thức này có sẵn trong tất cả các Interface con của nó.
    - **Phương thức add()** được sử dụng để chèn phần tử được chỉ định.
    - **Phương thức size()** được sử dụng để trả về kích thước.
    - **Phương thức remove()** được sử dụng để xóa phần tử được chỉ định.
    - **Phương thức iterator()** được sử dụng để trả về một vòng lặp để truy cập các phần tử.
    - **Phương thức addAll()** được sử dụng để thêm tất cả các phần tử của một tập hợp cụ thể.
    - **Phương thức removeAll(**) được sử dụng để xóa tất cả các phần tử của tập hợp được chỉ định.
    - **Phương thức clear()** được sử dụng để xóa tất cả các phần tử.
- **