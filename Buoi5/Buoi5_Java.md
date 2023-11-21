# DEV THÌ KHÔNG CHỈ VIẾT CODE
## 1. Version Control là gì? Tại sao lại phải sử dụng Version Control
- **`Version Control System (VCS)`** là hệ thống kiểm soát phiên bản, giúp theo dõi và quản lý các thay đổi đối với hệ thống tập tin.
  - Nó hỗ trợ người dùng chia sẻ và báo cáo thông tin về những thay đổi trên file hoặc thư mục.
  - Nó giúp quản lý các hành động thêm, sửa và xóa các tệp và thư mục.

Một số Version control phổ biến bao gồm **Git, Mercurial, và SVN**. **Git** là một trong những VCS phổ biến nhất, được sử dụng rộng rãi trong cộng đồng phát triển phần mềm.

- Lý do sử dụng VCS:
  - Lưu lại lịch sử các version của bất kỳ thay đổi nào của dự án. Giúp xem lại các sự thay đổi hoặc khôi phục `(revert)` lại sau này.
  - Việc chia sẻ code trở nên dễ dàng hơn, lập trình viên có thể để public cho bất kỳ ai, hoặc private chỉ cho một số người có thẩm quyền có thể truy cập và lấy code về.

## 2. Các khái niệm về Git: Local Repository, Remote Repository, Branch, Commit, Merge, Pull, Push, Clone, Fork.

> **Tham Khảo: [GIT](https://topdev.vn/blog/git-la-gi/#_git-la-gi-5)**

- `Git` là một hệ thống quản lý phiên bản phân tán `(Distributed Version Control System – DVCS)`, nó là một trong những hệ thống quản lý phiên bản phân tán phổ biến nhất hiện nay. Git cung cấp cho mỗi lập trình viên kho lưu trữ `(repository)` riêng chứa toàn bộ lịch sử thay đổi.

**Khác biệt giữa Git và các VCS khác**

-  Hầu hết các hệ thống khác đều lưu trữ thông tin dưới dạng danh sách các thay đổi dựa trên file.

![Alt text](image.png)

- Git không nghĩ đến hoặc lưu trữ dữ liệu của mình theo cách này. Thay vào đó, Git coi thông tin được lưu trữ là một tập hợp các `snapshot` – ảnh chụp toàn bộ nội dung tất cả các file tại thời điểm.
- Mỗi khi bạn **`commit`**, Git sẽ **`chụp`** và tạo ra một `snapshot` cùng một tham chiếu tới `snapshot` đó. Để hiệu quả, nếu các tệp không thay đổi, Git sẽ không lưu trữ lại file - chỉ là một liên kết đến tệp giống file trước đó mà nó đã lưu trữ. Git nghĩ về dữ liệu của nó giống như dưới đây:

![Alt text](image-1.png)

>Đây là điểm khác biệt quan trọng giữa Git và gần như tất cả các VCS khác. Nó khiến Git phải xem xét lại hầu hết mọi khía cạnh của kiểm soát phiên bản mà hầu hết các hệ thống khác đã sao chép từ thế hệ trước. Điều này làm cho Git giống như một hệ thống tệp nhỏ với một số công cụ cực kỳ mạnh mẽ được xây dựng trên nó, thay vì chỉ đơn giản là một VCS.

**Lợi ích của Git**

- Dễ sử dụng, thao tác nhanh, gọn, lẹ và rất an toàn.
- Dễ dàng kết hợp các phân nhánh `(branch)`, có thể giúp quy trình làm việc code theo nhóm đơn giản hơn rất nhiều.
- Chỉ cần clone mã nguồn từ kho chứa hoặc clone một phiên bản thay đổi nào đó từ kho chứa, hoặc một nhánh nào đó từ kho chứa là bạn có thể làm việc ở mọi lúc mọi nơi.
- Deployment sản phẩm của bạn một cách không thể nào dễ dàng hơn.

### 2.1. Repository
Là nơi lưu trữ tất cả những thông tin cần thiết để duy trì và quản lý các sửa đổi và lịch sử của dự án (nơi trữ source code và các thay đổi trên đống source code này)
#### 2.1.1. Local Repository

- Là `repository` nằm trên chính máy tính của chúng ta, `repository` này sẽ đồng bộ hóa với `remote repository` bằng các lệnh của git.

#### 2.1.2. Remote Repository

- Là `repository` được cài đặt trên server chuyên dụng. Ví dụ: `GitHub, GitLab, Bitbucket,...`

- Khi tự khởi tạo một `repository`, chúng ta gõ lệnh `$ git init`, lệnh này sẽ tạo ra một thư mục `.git` và đây chính là repository còn phần code nằm cùng với thư mục `.git` được gọi là `Working Directory`
- Sau khi gõ lệnh git init, nếu nhận được thông báo như sau thì việc thực hiện tạo repository đã thành công: `Initialized empty Git repository in path_to_folder/.git/`

### 2.2. Branch

- Các `Branch (nhánh)` đại diện cho các phiên bản cụ thể của một kho lưu trữ tách ra từ project chính của bạn.
- Branch cho phép bạn theo dõi các thay đổi thử nghiệm bạn thực hiện đối với kho lưu trữ và có thể hoàn nguyên về các phiên bản cũ hơn.
- Branch trong Git được chia làm 2 loại, là `branch master (nhánh chính)` và các branch khác do bạn tạo ra trong quá trình làm việc. 
- **Branch master:** Là nhánh đầu tiên khi khởi tạo một Git repository, branch master thường là nơi chứa source code đang chạy ổn định. 
- **Các loại branch:**
    - ***Branch local:*** là branch lưu ở local (tất nhiên rồi). Nó có thể được liên kết với 1 branch ở remote hoặc không. Hiển thị branch có trên local ta dùng lệnh `git branch`.
    - ***Branch remote:*** là branch lưu ở remote. Branch này có thể `fetch` về local nhưng không tạo thêm branch ở local. Hiểu đơn giản là bạn có thể tải branch ở remote về nhưng không tạo 1 branch ở local với tên tương tự và tất nhiên sẽ không liên kết nó với một branch local nào cả. Để hiển thị branch remote có trên local dùng lệnh `git branch -r`

**Tạo branch**: `$ git branch <branchname>`

**Xoá một branch ở phía local** 
**Cách 1:** `$ git branch --delete <branch_name>`
hoặc `$ git branch -d <branch_name>`

**Cách 2:** `$ git branch --delete --force <branch_name>`
hoặc `$ git branch -D <branch_name>`

**Xoá một branch remote lưu ở local**
`$ git branch --delete --remotes <remote_name>/<branch_name>` 
hoặc `$ git branch -d -r <remote_name>/<branch_name>`

>**NOTE
> - Cách 1 chỉ xóa được branch local khi nó đã được Merge vào branch hiện tại và nó đã được push lên remote nếu nó có liên kết với một branch remote.
> - Cách 2 sẽ xóa được mọi branch kể cả không thỏa mãn điều kiện kể trên. Chỉ xóa được branch khi đang ở branch khác.

**Xoá một branch ở phía remote**
`$ git push <remote_name> --delete <branch_name>`

## 4. UML là gì? Lí do cần vẽ UML
- **UML** (Unified Modeling Language - ngôn ngữ mô hình hóa thống nhất) là một ngôn ngữ mô hình gồm các ký hiệu đồ họa mà các phương pháp hướng đối tượng sử dụng để thiết kế các hệ thống thông tin một cách nhanh chóng.
- **UML** sử dụng một hệ thống ký hiệu thống nhất biểu diễn các Phần tử mô hình `(model elements)`. Tập hợp các phần tử mô hình tạo thành các Sơ đồ `UML (UML diagrams)`. Có các loại sơ đồ UML chủ yếu sau:

  - *Sơ đồ lớp (Class Diagram)*
  - *Sơ đồ đối tượng (Object Diagram)*
  - *Sơ đồ tình huống sử dụng (Use Cases Diagram)*
  - *Sơ đồ trình tự (Sequence Diagram)*
  - *Sơ đồ cộng tác (Collaboration Diagram hay là Composite Structure Diagram)*
  - *Sơ đồ trạng thái (State Machine Diagram)*
  - *Sơ đồ thành phần (Component Diagram)*
  - *Sơ đồ hoạt động (Activity Diagram)*
  - *Sơ đồ triển khai (Deployment Diagram)*
  - *Sơ đồ gói (Package Diagram)*
  - *Sơ đồ liên lạc (Communication Diagram)*
  - *Sơ đồ tương tác (Interaction Overview Diagram - UML 2.0)*
  - *Sơ đồ phối hợp thời gian (Timing Diagram - UML 2.0)*

- **Lý do cần vẽ UML:**
  - *Hiểu rõ Yêu Cầu:* UML giúp mô tả và hiểu rõ các yêu cầu của hệ thống từ góc độ người quản lý dự án và người sử dụng.
  - *Thiết Kế Hệ Thống:* UML cung cấp các biểu đồ và ký hiệu để thiết kế cấu trúc và cách thức hoạt động của hệ thống.
  - *Giao Tiếp Hiệu Quả:* UML tạo ra một ngôn ngữ chung để mô tả ý tưởng và thiết kế, giúp tăng cường giao tiếp giữa các thành viên trong nhóm phát triển và giữa nhóm phát triển và người quản lý.
  - *Tạo Ra Tài Liệu Hệ Thống:* UML giúp tạo ra tài liệu dự án đồng thời và thực hiện, giúp dễ dàng theo dõi và duy trì hệ thống.
  - *Kiểm Tra và Đánh Giá Thiết Kế:* Các biểu đồ UML, như biểu đồ lớp, biểu đồ tuần tự, và biểu đồ use case, có thể được sử dụng để kiểm tra và đánh giá thiết kế của hệ thống trước khi bắt đầu quá trình phát triển.
  - *Quản Lý Các Yếu Tố Phức Tạp:* UML giúp quản lý sự phức tạp của hệ thống bằng cách tạo ra các mô hình trừu tượng để giảm bớt sự phức tạp và tăng tính rõ ràng.
  - *Phân Chia Công Việc:* UML có thể được sử dụng để phân chia công việc giữa các thành viên trong nhóm phát triển và làm cho mỗi người hiểu rõ vai trò và trách nhiệm của mình.

## 5. Mô hình Class Diagram, Activity Diagram
### 5.1 Class Diagram

