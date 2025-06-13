# Hướng Dẫn Chạy LibraryManagementApplication

## 1. Yêu cầu môi trường

- **Python:** Cài đặt Python 3.10 trở lên  
  Tải tại: [https://www.python.org/downloads/](https://www.python.org/downloads/)
- **Pip:** Đảm bảo đã cài đặt pip để quản lý các thư viện Python  
  Kiểm tra bằng lệnh:  

  ```sh
  pip --version
  ```

- **SQL Server:** Cài đặt SQL Server 2017 trở lên và SQL Server Management Studio (SSMS)

---

## 2. Cài đặt Database từ file .bak

1. **Mở SQL Server Management Studio (SSMS)**
2. **Kết nối tới SQL Server** bằng tài khoản sa hoặc tài khoản có quyền restore database.
3. **Restore database:**
   - Chuột phải vào mục Databases → chọn Restore Database...
   - Ở mục Source, chọn Device → nhấn ... → Add → chọn file  
     3.ScriptAndBackUp/LibraryManagementApplication.bak trong source code.
   - Đặt tên database là LibraryManagementApplication (hoặc tên bạn muốn).
   - Nhấn OK để tiến hành restore.
4. **Kiểm tra lại**: Sau khi restore xong, kiểm tra trong danh sách database đã có LibraryManagementApplication.

---

## 3. Cấu hình kết nối Database

- **File cấu hình:**  
  2.SourceCode/LibraryManagementSystem/config.json

- **Nội dung mẫu:**

  ```json
	{
		"DB_SERVER": "172.16.1.240",
		"DB_NAME": "LibraryManagement",
		"DB_USERNAME": "sa",
		"DB_PASSWORD": "12345678aA@"
	}
  ```

  - **url:** Địa chỉ kết nối tới SQL Server, thay đổi localhost và databaseName nếu cần. Đảm bảo cài đặt driver ODBC cho SQL Server.
  - **user:** Tài khoản SQL Server (thường là sa).
  - **password:** Mật khẩu của tài khoản SQL Server.
  - **hashKey:** Không thay đổi nếu không có yêu cầu bảo mật đặc biệt.

> **Lưu ý:** Nếu SQL Server của bạn chạy port khác 1433, hãy sửa lại port trong chuỗi kết nối. Cài đặt thư viện `pyodbc` bằng lệnh: `pip install pyodbc`.

---

## 4. Tài khoản đăng nhập mặc định

- **Tài khoản Admin:**
  - Username: Admin
  - Password: 12345678aA@

> Bạn có thể đăng nhập bằng tài khoản này sau khi chạy ứng dụng.  
> Để tạo thêm tài khoản, hãy sử dụng chức năng quản lý tài khoản trong giao diện Admin.

---

## 5. Cài đặt và chạy ứng dụng

- Ứng dụng mặc định chạy ở chế độ Admin. Chạy file `main.py` bằng lệnh:

  ```sh
  python main.py
  ```

---

## 6. Một số lưu ý

- Nếu gặp lỗi kết nối database, kiểm tra lại thông tin trong `config.json` và đảm bảo SQL Server đang chạy.
- Để đổi mật khẩu/tài khoản admin, có thể thao tác trực tiếp trên database hoặc qua giao diện Admin.
- Nếu muốn đổi port SQL Server, sửa lại trong chuỗi kết nối `url`.
- Hoặc cài đủ thư viên cần thiết để có thể chạy

---
