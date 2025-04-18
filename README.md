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


