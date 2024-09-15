
# SETUP

## 1. Cài Đặt Git Bash

Git Bash là một giao diện dòng lệnh cung cấp môi trường Bash cho người dùng Windows. Nó cho phép sử dụng các lệnh Unix/Linux như `ls`, `cp`, `rm`, và nhiều lệnh khác.

### 1.1. Bước 1: Tải Git Bash

- Truy cập trang web chính thức của Git: [https://git-scm.com/](https://git-scm.com/)
- Nhấn vào nút **Download for Windows** để tải về file cài đặt.

### 1.2. Bước 2: Cài Đặt Git Bash

- Mở file cài đặt vừa tải về.
- Chọn các tùy chọn theo ý muốn, có thể để mặc định.
- Khi đến phần "Adjusting your PATH environment", chọn **Use Git from the command line and also from 3rd-party software**.
- Tiếp tục cài đặt cho đến khi hoàn tất.

### 1.3. Bước 3: Kiểm Tra Cài Đặt

- Mở Git Bash từ Start Menu hoặc tìm kiếm "Git Bash".

- Gõ lệnh sau để kiểm tra phiên bản:

  ```bash
  git --version
  ```

  Nếu hiển thị phiên bản Git, bạn đã cài đặt thành công.

## 2. Cài Đặt GCC

GCC (GNU Compiler Collection) là một bộ biên dịch phổ biến cho nhiều ngôn ngữ lập trình như C, C++, và Fortran. Trên Windows, GCC thường được cài đặt qua MinGW-w64.

### 2.1. Bước 1: Tải MinGW-w64

- Truy cập trang web: [https://sourceforge.net/projects/mingw-w64/](https://sourceforge.net/projects/mingw/)
- Nhấn vào nút **Download** để tải về bản cài đặt MinGW-w64.

### 2.2. Bước 2: Cài Đặt MinGW-w64

- Mở file cài đặt vừa tải về.
- Chọn kiến trúc hệ thống phù hợp (x86_64 cho 64-bit hoặc i686 cho 32-bit).
- Chọn phiên bản GCC (thường là bản mới nhất).
- Chọn **posix** và **seh** (cho 64-bit) hoặc **dwarf** (cho 32-bit).
- Chọn thư mục cài đặt, tốt nhất là cài đặt trong thư mục gốc (ví dụ: `C:\mingw-w64`).

### 2.3. Bước 3: Cấu Hình Biến Môi Trường

- Mở **Control Panel** > **System and Security** > **System** > **Advanced system settings**.
- Chọn **Environment Variables**.
- Trong phần **System variables**, tìm và chọn biến **Path**, sau đó nhấn **Edit**.
- Nhấn **New** và thêm đường dẫn đến thư mục `bin` của MinGW-w64 (ví dụ: `C:\mingw-w64in`).
- Nhấn **OK** để lưu lại.

### 2.4. Bước 4: Kiểm Tra Cài Đặt

- Mở Git Bash.

- Gõ lệnh sau để kiểm tra phiên bản GCC:

  ```bash
  gcc --version
  ```

  Nếu hiển thị phiên bản GCC, bạn đã cài đặt thành công.

## 3. Biên Dịch Chương Trình Với GCC

Sau khi cài đặt xong GCC, bạn có thể biên dịch các chương trình C/C++ trực tiếp từ Git Bash.

### 3.1. Tạo File Mã Nguồn

Tạo một file mã nguồn đơn giản, ví dụ `hello.cpp`:

```c++
#include<bits/stdc++.h>
int main() {
    std::cout<<"Hello World!";
    return 0;
}
```

### 3.2. Biên Dịch

Sử dụng lệnh GCC để biên dịch:

```bash
gcc -o hello hello.cpp
```

### 3.3. Chạy Chương Trình

Sau khi biên dịch thành công, chạy chương trình:

```bash
./hello
```

Nếu chương trình in ra "Hello, World!" thì bạn đã biên dịch thành công.

## 4. Tổng Kết

Bạn đã cài đặt thành công Git Bash và GCC trên Windows, cũng như biên dịch và chạy chương trình C++ đơn giản. Nếu gặp bất kỳ vấn đề nào, hãy kiểm tra lại các bước hoặc tìm kiếm sự trợ giúp từ cộng đồng.

## 5. Cấu Hình Build System Cho C++

Sublime Text cung cấp hệ thống build để cho phép người dùng chạy các chương trình bên ngoài. Bạn có thể tạo một build system mới cho Sublime Text để thiết lập việc biên dịch C++.

### 5.1. Tạo Build System

1. Mở Sublime Text.

2. Chọn **Tools > Build System > New Build System**.

3. Dán đoạn mã sau vào file và lưu lại:

   ```json
   {
       "cmd": ["g++.exe", "-std=c++17", "${file}",
               "-o", "${file_base_name}.exe",
               "&&", "${file_base_name}.exe<inputf.in>outputf.out"],
       "shell": true,
       "working_dir": "$file_path",
       "selector": "source.cpp"
   }
   ```

4. Đặt tên file là `CP.sublime-build`.

### 5.2. Mô Tả

Đoạn mã trên được sử dụng để lấy input từ file `inputf.in` và ghi kết quả ra file `outputf.out`. Đây là cách thiết lập đơn giản để bạn có thể biên dịch và chạy các chương trình C++ trực tiếp từ Sublime Text với các file input/output. (`inputf.in` và `outputf.out` có thể thay đổi theo người code ví dụ `in.txt` và `ou.txt`)

## 6. Những Packages Sublime Đang Dùng

Dưới đây là danh sách các packages đang được sử dụng trong Sublime Text của bạn:

1. **A File Icon**: Cung cấp biểu tượng file tùy chỉnh cho Sublime Text.
2. **ayu**: Một chủ đề giao diện người dùng với thiết kế gọn gàng và màu sắc dễ chịu.
3. **LiveServer**: Tạo server cục bộ để xem trước thay đổi trong trình duyệt theo thời gian thực.
4. **Package Control**: Hệ thống quản lý và cài đặt packages cho Sublime Text.
5. **Python 3**: Hỗ trợ viết và chạy mã Python 3 trong Sublime Text.
6. **SourceTreeCommands**: Cung cấp các lệnh tiện dụng cho SourceTree trong Sublime Text.
7. **Sync Settings**: Đồng bộ hóa cài đặt Sublime Text giữa các máy tính khác nhau.
8. **Theme - amCoder**: Một chủ đề giao diện người dùng tối ưu hóa cho lập trình viên.
