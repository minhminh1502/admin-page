# HƯỚNG DẪN CÀI ĐẶT DỰ ÁN GMP SYSTEM

## # Yêu cầu hệ thống

    Node: v16.0.0 or above (LTS)
    PHP: v8.2.0 or Above
    Composer: v2.0.4 or Above
    Laravel: v9.0 or Above

## # Cài đặt Yarn

Nếu Node.js >= 16.10:

    corepack enable

Nếu Node.js < 16.10:

    npm install -g yarn

Kiểm tra Yarn version:

    yarn --version

## # Cài đặt source code

1. Mở terminal tại thư mục gốc dự án.

2. Thực thi lệnh bên dưới để cài đặt thư viện PHP thông qua composer:

        composer install

3. Tìm tập tin `.env.example` tại thư mục gốc, copy & rename thành `.env`:

    Với Windows:

        copy .env.example .env

    Với Linux:

        cp .env.example .env

4. Thực thi lệnh bên dưới để tạo application key:

        php artisan key:generate

5. Sử dụng `yarn` để cài đặt các dependencies trong thư mục `node_modules`:

        yarn

6. Để chạy project, cần biên dịch JavaScript và CSS:

        yarn dev

7. Bổ sung thêm permission nếu thực thi dự án trên Linux:

        sudo chmod -R o+rw bootstrap/cache
        sudo chmod -R o+rw storage

8. Thực thi lệnh bên dưới để chạy dự án trên port `8000`:

        php artisan serve --host=0.0.0.0 --port=8000

9. Ứng dụng đã sẵn sàng truy cập thông qua URL:

        http://localhost:8000

## # Cài đặt database thông qua migration

1. Tạo empty database sử dụng MySQL:

        create schema `gmp_system` collate utf8mb4_general_ci;

2. Thiết lập thông tin kết nối CSDL trong tập tin `.env`:

        DB_CONNECTION = mysql
        DB_HOST = 127.0.0.1
        DB_PORT = 3306
        DB_DATABASE = gmp_system
        DB_USERNAME = <nhập username | mặc định là root>
        DB_PASSWORD = <nhập mật khẩu | để trống nếu không có>

3. Chạy lệnh bên dưới để tạo tables:

        php artisan migrate
4. (Tùy chọn) Chạy lệnh bên dưới để fake data cho bảng `User`:

        php artisan db:seed
