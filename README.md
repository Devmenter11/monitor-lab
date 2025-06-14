# monitor-lab

Clone git
    docker-compose up -d
Sau khi chạy thì tạo ra 4 volume:
Sau đó vào volume của prometheus_config để thêm 1 file web.yml
có nội dung sau:

    -------------------------------------------------------------------

basic_auth_users:
  admin: $2b$12$wPCmohSoeYBRYmwO0qPZI.PMB83.wYCUlVTyAYj64C0zs.OMiIAyW

    --------------------------------------------------------------

Có thể sử dụng user khác bằng cách chạy file hashpw.py :
--->  python3 hashpw.py

Sửa nội dung file của prometheus.yml trong volume của prometheus_config:
Có thể sd luon file: /prometheus/prometheus2.yml
