<h1 align="center">
  Hướng dẫn sử dụng
</h1>

## Database

Nằm trong folder `./back_end/sql`  
Database management systems: `PostgreSQL`  
Database name: `db_baemin` ( có thể thay đổi trong .env.sample )

`postgres_db_baemin.sql`: file chứa định nghĩa table và column.  
`postgres_db_baemin_data.sql`: file chứa mock data.

```
NestJS cần có data base để chạy.
Chạy toàn bộ script SQL trong 2 file trên để có database.
```

## Build dự án bằng docker

```bash
# production
$ docker compose up -d
```

## Postman

File JSON của `Postman` nằm trong folder `./back_end/postman`

## Lưu ý

Khi vào `/dashboard` sẽ không có dữ liệu trong 60 giây đầu tiên.  
Sau 60 giây tải lại trang sẽ có dữ liệu.

### **Nguyên nhân:**

`DASHBOARD` là trang `ISR` (Incremental Static Regeneration), nên khi build sẽ yêu cầu fetch data từ phía backend để có dữ liệu tạo trang.

Nhưng Backend lại được build cùng lúc với Frontend, nên không thể truy cập backend. Dẫn đến không có dữ liệu.

Trang `DASHBOARD` được cài đặt sẽ fetch dữ liệu mới trong vòng 60 giây `(revalidate = 60)`, nên sẽ cập nhật dữ liệu sau mỗi 60 giây.
