Cách chạy Loki tích hợp với grafana theo dõi log: 

    docker-compose up -d

! chú ý: Nếu chạy docker của promtail thì cần phải cho những file log của các dịch vụ lấy log vào container

Cài bằng systemctl:

----------------------------------------------------------------------------------

    mkdir -p /opt/promtail
    cd /opt/promtail
    wet https://github.com/grafana/loki/releases/download/v3.4.1/promtail-linux-amd64.zip
    unzip promtail-linux-amd64.zip
    chmod +x promtail-linux-amd64
    mv promtail-linux-amd64 promtail

----------------------------------------------------------------------------------

Tạo file config promtail-config.yaml như trên 
Chạy bằng systemctl bằng cách:

    nano /etc/systemd/system/promtail.service

           ---------------------------------------------------------------

[Unit]
Description=Promtail Log Collector
After=network.target

[Service]
Type=simple
ExecStart=/opt/promtail/promtail --config.file=/opt/promtail/promtail-config.yaml
Restart=on-failure

[Install]
WantedBy=multi-user.target

           ---------------------------------------------------------------

sau đó chạy các lệnh sau:
    sudo systemctl daemon-reexec
    sudo systemctl daemon-reload
    sudo systemctl enable --now promtail
