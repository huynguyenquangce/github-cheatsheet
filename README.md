# github-cheatsheet
This is a Cheatsheet for Github CLI

# 📘 Git Commit Flags Cheat Sheet

Bảng dưới đây tổng hợp các flag thường dùng với `git commit`, kèm theo ví dụ thực tế:

| Flag            | Chức năng                                                                 | Ví dụ lệnh sử dụng |
|------------------|---------------------------------------------------------------------------|--------------------|
| `-m`            | Thêm message trực tiếp khi commit                                         | `git commit -m "Fix bug login"` |
| `-a`            | Tự động stage các file đã được track (bỏ qua file mới chưa `add`)        | `git commit -a -m "Update main.cpp"` |
| `--amend`       | Chỉnh sửa commit gần nhất                                                 | `git commit --amend -m "Thêm README.md"` |
| `-v`            | Hiển thị diff khi mở editor để commit                                     | `git commit -v` |
| `--no-edit`     | Dùng lại commit message cũ (thường dùng kèm với `--amend`)               | `git commit --amend --no-edit` |
| `--allow-empty` | Tạo commit dù không thay đổi gì (ví dụ để trigger CI/CD)                 | `git commit --allow-empty -m "Trigger deploy"` |
| `--author`      | Ghi đè tên tác giả commit                                                 | `git commit -m "Update" --author="Huy <huy@example.com>"` |
| `--date`        | Ghi đè ngày commit                                                        | `git commit -m "Log test" --date="2024-04-18T12:00:00"` |

---

📌 **Ghi chú thêm**:
- `-a` chỉ hoạt động với các file đã được Git theo dõi (`tracked`).
- `--amend` chỉ nên dùng nếu commit chưa được push lên remote.
- `--allow-empty` rất hữu ích để test, trigger các pipeline tự động.

---


# 📘 Git Push Flags Cheat Sheet

Dưới đây là các flag thường dùng với lệnh `git push`, kèm theo ví dụ thực tế:

| Flag             | Chức năng                                                                | Ví dụ lệnh sử dụng |
|-------------------|--------------------------------------------------------------------------|--------------------|
| `-u`              | Thiết lập upstream cho nhánh local (mối liên kết với remote)            | `git push -u origin main` |
| `-f`              | Lực đẩy (force push), thay thế lịch sử của remote branch                | `git push -f origin main` |
| `--all`           | Đẩy tất cả các nhánh local lên remote                                    | `git push --all origin` |
| `--tags`          | Đẩy tất cả các tag lên remote                                            | `git push --tags` |
| `--dry-run`       | Kiểm tra lệnh push mà không thực sự đẩy thay đổi lên remote             | `git push --dry-run` |
| `--delete`        | Xóa nhánh trên remote (giống `git branch -d` nhưng với remote)          | `git push --delete origin feature-branch` |
| `--set-upstream`  | Cài đặt nhánh upstream cho nhánh local                                  | `git push --set-upstream origin feature-branch` |
| `--quiet`         | Giảm thiểu thông báo khi push                                            | `git push --quiet` |

---

## 📝 Giải thích các flag:

- `-u` hoặc `--set-upstream`: Thiết lập liên kết giữa nhánh local và remote, giúp bạn không cần phải chỉ định remote và nhánh mỗi lần push. Ví dụ, khi bạn chạy `git push -u origin main`, lần sau chỉ cần dùng `git push`.
- `-f`: Lực đẩy các thay đổi lên remote, rất nguy hiểm khi bạn đang làm việc với nhiều người, vì nó sẽ thay thế lịch sử của nhánh trên remote.
- `--all`: Đẩy tất cả các nhánh của bạn lên remote, giúp đồng bộ tất cả các nhánh khi làm việc với nhiều nhánh.
- `--tags`: Dùng khi bạn muốn đẩy tất cả các tags (thường dùng trong release).
- `--dry-run`: Lệnh giả lập (không thực hiện thay đổi) cho phép bạn kiểm tra những gì sẽ được đẩy lên remote mà không thay đổi gì.
- `--delete`: Dùng để xóa một nhánh trên remote, ví dụ khi nhánh đã hoàn thành và không cần nữa.
- `-f`: Lệnh **force push**, cho phép bạn đẩy dữ liệu lên remote ngay cả khi lịch sử commit của bạn có sự thay đổi. Lệnh này rất mạnh mẽ và có thể gây hại nếu bạn không cẩn thận, vì nó thay thế lịch sử của nhánh trên remote.
---

📌 **Lưu ý**:
- `git push -f` nên dùng cẩn thận vì nó có thể khiến người khác gặp sự cố khi đồng bộ lại với remote.
- Nếu bạn không muốn push một nhánh mà mình đã tạo, bạn có thể gỡ liên kết remote bằng cách sử dụng `git push --delete origin <branch-name>`.

---

# 📘 Kết nối giữa Local Repository và Remote Repository

Dưới đây là các lệnh và flag thường dùng khi kết nối giữa local repository và remote repository.

---

## 1. **Thêm Remote Repository**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git remote add`                | Thêm remote repository vào local repository          | `git remote add origin git@github.com:user/repo.git` |

> **Lưu ý**: `origin` là tên mặc định của remote repository. Bạn có thể thay thế bằng tên khác nếu muốn.

---

## 2. **Kiểm tra Remote Repository**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git remote -v`                 | Kiểm tra các remote repository được liên kết         | `git remote -v` |

> **Lưu ý**: Lệnh này hiển thị tên remote và URL của repository liên kết.

---

## 3. **Thay đổi URL của Remote Repository**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git remote set-url`            | Thay đổi URL của remote repository                   | `git remote set-url origin git@github.com:user/new-repo.git` |

> **Lưu ý**: Dùng khi bạn muốn thay đổi remote repository sau khi đã thêm hoặc để thay đổi URL (ví dụ khi chuyển từ HTTPS sang SSH).

---

## 4. **Xóa Remote Repository**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git remote remove`             | Xóa một remote repository khỏi local repository      | `git remote remove origin` |

> **Lưu ý**: Lệnh này xóa remote `origin` khỏi local repository. Cẩn thận khi sử dụng.

---

## 5. **Kiểm tra Tình Trạng Kết Nối Remote**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git remote show`               | Hiển thị thông tin chi tiết về remote repository     | `git remote show origin` |

> **Lưu ý**: Lệnh này cung cấp thông tin chi tiết về remote repository, bao gồm URL và các nhánh đang được theo dõi.

---

## 6. **Pull Dữ Liệu từ Remote Repository**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git pull`                      | Kéo dữ liệu mới từ remote repository về local       | `git pull origin main` |

> **Lưu ý**: `git pull` kết hợp giữa `git fetch` và `git merge`, giúp đồng bộ dữ liệu giữa local và remote.

---

## 7. **Push Dữ Liệu Lên Remote Repository**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git push`                      | Đẩy thay đổi từ local lên remote repository          | `git push origin main` |

> **Lưu ý**: Khi bạn thực hiện `git push`, chắc chắn rằng bạn đã commit thay đổi của mình.

---

## 8. **Kết Nối và Thiết Lập Upstream Branch**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git push -u`                   | Thiết lập nhánh upstream khi push lần đầu           | `git push -u origin feature-branch` |

> **Lưu ý**: Sau khi thiết lập upstream, bạn chỉ cần sử dụng `git push` mà không cần chỉ định remote và nhánh nữa.

---

## 9. **Kiểm tra Liên Kết Remote**

| Lệnh                           | Chức năng                                            | Ví dụ lệnh sử dụng |
|---------------------------------|------------------------------------------------------|--------------------|
| `git config --get remote.origin.url` | Kiểm tra URL của remote repository hiện tại    | `git config --get remote.origin.url` |

> **Lưu ý**: Lệnh này giúp bạn xác định chính xác URL của remote repository mà bạn đang làm việc.

---

## 📌 **Lưu ý quan trọng:**

- Khi bạn thêm hoặc thay đổi remote repository, hãy chắc chắn kiểm tra lại với lệnh `git remote -v` để đảm bảo đúng URL.
- Mỗi khi bạn thay đổi nhánh hoặc làm việc với nhiều remote repository, hãy chắc chắn rằng bạn đã thiết lập nhánh upstream với `git push -u`.
- Việc cấu hình đúng remote URL là rất quan trọng để tránh các lỗi khi thực hiện `git push` hoặc `git pull`.

---

# 📘 Checking history commit

Dưới đây là các lệnh và flag thường dùng để kiểm tra lịch sử commit trong Git.

---

## 1. **Kiểm Tra Lịch Sử Commit**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git log`                       | Hiển thị lịch sử commit từ mới nhất                      | `git log` |
| `git log --oneline`             | Hiển thị lịch sử commit theo dạng rút gọn (1 dòng mỗi commit) | `git log --oneline` |

> **Lưu ý**: Lệnh `git log` hiển thị chi tiết lịch sử commit, bao gồm mã hash của commit, tác giả, ngày tháng và thông điệp commit. Flag `--oneline` giúp rút gọn, hiển thị mỗi commit trên một dòng.

---

## 2. **Hiển Thị Lịch Sử Commit Có Thời Gian hoặc Tác Giả Cụ Thể**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git log --author`              | Hiển thị các commit của một tác giả cụ thể               | `git log --author="Huy"` |
| `git log --since`               | Hiển thị các commit từ một thời gian cụ thể             | `git log --since="2024-01-01"` |
| `git log --until`               | Hiển thị các commit đến một thời gian cụ thể             | `git log --until="2024-04-01"` |

> **Lưu ý**: Các flag này cho phép bạn lọc lịch sử commit dựa trên tác giả hoặc thời gian. Cả `--since` và `--until` hỗ trợ nhiều định dạng thời gian khác nhau.

---

## 3. **Hiển Thị Lịch Sử Commit Với Diff**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git log -p`                    | Hiển thị lịch sử commit cùng với thay đổi (diff) trong mỗi commit | `git log -p` |
| `git log --stat`                | Hiển thị lịch sử commit với thống kê thay đổi về file (số lượng dòng thêm/sửa) | `git log --stat` |

> **Lưu ý**: Flag `-p` hiển thị toàn bộ thay đổi (diff) của các commit, còn `--stat` chỉ hiển thị thống kê về các thay đổi ở mức file (chứ không phải chi tiết nội dung).

---

## 4. **Lịch Sử Commit Theo Nhánh Cụ Thể**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git log <branch>`              | Hiển thị lịch sử commit của nhánh cụ thể                 | `git log feature-branch` |

> **Lưu ý**: Thay `<branch>` bằng tên nhánh bạn muốn kiểm tra lịch sử commit. Ví dụ, `git log main` sẽ hiển thị lịch sử commit của nhánh `main`.

---

## 5. **Hiển Thị Lịch Sử Commit Với Các Điều Kiện Tìm Kiếm Phức Tạp**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git log --grep`                | Tìm commit theo thông điệp commit (message)             | `git log --grep="fix bug"` |

> **Lưu ý**: Dùng `--grep` để tìm commit dựa trên từ khóa trong message. Ví dụ, `git log --grep="bug"` sẽ tìm tất cả các commit có từ "bug" trong thông điệp.

---

## 6. **Lịch Sử Commit Theo Thời Gian và Các Thông Số Khác**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git log --reverse`             | Hiển thị lịch sử commit theo thứ tự ngược lại (cũ nhất trước, mới nhất sau) | `git log --reverse` |
| `git log --graph`               | Hiển thị lịch sử commit dưới dạng đồ thị, thể hiện nhánh và hợp nhất | `git log --graph` |
| `git log --abbrev-commit`       | Hiển thị hash commit rút gọn thay vì toàn bộ hash       | `git log --abbrev-commit` |

> **Lưu ý**: 
> - `--reverse` giúp bạn xem commit từ cũ nhất đến mới nhất.
> - `--graph` tạo đồ thị hiển thị cấu trúc nhánh của các commit, rất hữu ích khi làm việc với các nhánh phức tạp.

---

## 📌 **Lưu ý quan trọng**:

- Bạn có thể kết hợp các flag này với nhau để tạo ra các câu lệnh tùy chỉnh. Ví dụ: `git log --oneline --author="Huy" --since="2024-01-01"`.
- Lệnh `git log` có thể tốn thời gian nếu bạn có lịch sử commit quá dài. Hãy sử dụng các filter như `--since`, `--until`, hoặc `--author` để giảm phạm vi tìm kiếm.
- Dùng `git log --graph --oneline` khi bạn cần có cái nhìn trực quan về lịch sử nhánh và các commit.

---

# 📘 Quản Lý Nhánh trong Git

Dưới đây là các lệnh và flag thường dùng khi làm việc với nhánh trong Git.

---

## 1. **Hiển Thị Danh Sách Nhánh**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git branch`                    | Hiển thị danh sách tất cả các nhánh trong repository   | `git branch` |
| `git branch -a`                 | Hiển thị tất cả các nhánh, bao gồm các nhánh remote    | `git branch -a` |

> **Lưu ý**: Lệnh `git branch` chỉ hiển thị các nhánh local. Thêm flag `-a` để hiển thị cả các nhánh remote.

---

## 2. **Tạo Nhánh Mới**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git branch <branch-name>`      | Tạo nhánh mới                                          | `git branch feature-xyz` |

> **Lưu ý**: Nhánh mới sẽ được tạo từ nhánh hiện tại, nhưng bạn vẫn ở trên nhánh cũ cho đến khi chuyển sang nhánh mới.

---

## 3. **Chuyển Đổi Giữa Các Nhánh**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git checkout <branch-name>`    | Chuyển sang nhánh đã tồn tại                           | `git checkout feature-xyz` |
| `git switch <branch-name>`      | Chuyển sang nhánh đã tồn tại (dùng trong phiên bản Git 2.23 trở lên) | `git switch feature-xyz` |

> **Lưu ý**: `git switch` là lệnh mới được giới thiệu trong Git 2.23, giúp thao tác chuyển nhánh dễ dàng hơn so với `git checkout`.

---

## 4. **Tạo và Chuyển Sang Nhánh Mới**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git checkout -b <branch-name>` | Tạo và chuyển sang nhánh mới cùng lúc                   | `git checkout -b feature-xyz` |
| `git switch -c <branch-name>`   | Tạo và chuyển sang nhánh mới cùng lúc (dùng trong Git 2.23+) | `git switch -c feature-xyz` |

> **Lưu ý**: Cả hai lệnh này giúp bạn tạo nhánh mới và chuyển sang nhánh đó trong một bước duy nhất.

---

## 5. **Xóa Nhánh**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git branch -d <branch-name>`   | Xóa nhánh local (nếu nhánh đã được merge)               | `git branch -d feature-xyz` |
| `git branch -D <branch-name>`   | Xóa nhánh local ngay cả khi nhánh chưa được merge       | `git branch -D feature-xyz` |

> **Lưu ý**: Sử dụng `-D` thay vì `-d` để xóa một nhánh mà không cần kiểm tra xem nó đã được merge chưa.

---

## 6. **Hiển Thị Nhánh Hiện Tại**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git branch --show-current`     | Hiển thị nhánh hiện tại                                | `git branch --show-current` |

> **Lưu ý**: Lệnh này giúp bạn nhanh chóng biết mình đang ở trên nhánh nào.

---

## 7. **Liệt Kê Các Nhánh Đã Được Merge và Chưa Merge**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git branch --merged`           | Liệt kê các nhánh đã được merge vào nhánh hiện tại     | `git branch --merged` |
| `git branch --no-merged`        | Liệt kê các nhánh chưa được merge vào nhánh hiện tại   | `git branch --no-merged` |

> **Lưu ý**: Lệnh này giúp bạn xác định các nhánh đã hoặc chưa được merge vào nhánh hiện tại, từ đó đưa ra quyết định về việc xóa các nhánh không cần thiết.

---

## 8. **Kiểm Tra Nhánh Remote**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git branch -r`                 | Hiển thị các nhánh remote                              | `git branch -r` |

> **Lưu ý**: Lệnh này chỉ hiển thị các nhánh remote mà bạn đang theo dõi.

---

## 9. **Đổi Tên Nhánh**

| Lệnh                           | Chức năng                                               | Ví dụ lệnh sử dụng |
|---------------------------------|---------------------------------------------------------|--------------------|
| `git branch -m <new-branch-name>` | Đổi tên nhánh hiện tại                                | `git branch -m feature-xyz feature-abc` |

> **Lưu ý**: Lệnh này giúp bạn đổi tên nhánh mà bạn đang làm việc trên đó.

---

## 📌 **Lưu ý quan trọng**:

- Khi làm việc với nhánh, hãy luôn chắc chắn rằng bạn đã commit hoặc stashed mọi thay đổi trước khi chuyển nhánh, để tránh mất dữ liệu.
- Sử dụng `git branch -d` để xóa nhánh đã được merge. Tuy nhiên, nếu nhánh chưa được merge và bạn muốn xóa nó, dùng `git branch -D`.
- Với các phiên bản Git từ 2.23 trở lên, bạn nên sử dụng `git switch` và `git restore` thay vì `git checkout` để dễ sử dụng hơn.

---





