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

---

📌 **Lưu ý**:
- `git push -f` nên dùng cẩn thận vì nó có thể khiến người khác gặp sự cố khi đồng bộ lại với remote.
- Nếu bạn không muốn push một nhánh mà mình đã tạo, bạn có thể gỡ liên kết remote bằng cách sử dụng `git push --delete origin <branch-name>`.

---

