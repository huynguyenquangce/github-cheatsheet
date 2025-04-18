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
