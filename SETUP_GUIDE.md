# Линукс Систем Админист Лабораторийн Ажлын Заавар

## Даалгавар 1: Syslog Сервер Байгуулалт

### Алхам 1: Rsyslog суулгалт
sudo apt-get update
sudo apt-get install rsyslog

### Алхам 2: Rsyslog конфигурацийг засах
sudo nano /etc/rsyslog.conf

Дараах мөрүүдийг uncomment хийх (# устгах):
$ModLoad imudp
$UDPServerRun 514

### Алхам 3: Rsyslog рестарт
sudo systemctl restart rsyslog
sudo systemctl status rsyslog

## Даалгавар 2: Веб Сервер Асаалт

### Apache суулгалт:
sudo apt-get install apache2
sudo systemctl start apache2
sudo systemctl enable apache2

### Nginx суулгалт:
sudo apt-get install nginx
sudo systemctl start nginx

## Даалгавар 3: NTP Сервер Байгуулалт

### Алхам 1: NTP суулгалт
sudo apt-get install ntp ntpdate

### Алхам 2: NTP конфигурацийг засах
sudo nano /etc/ntp.conf

Нэмэх:
server 0.ubuntu.pool.ntp.org iburst
server 1.ubuntu.pool.ntp.org iburst
server 2.ubuntu.pool.ntp.org iburst
server 3.ubuntu.pool.ntp.org iburst

### Алхам 3: NTP рестарт
sudo systemctl restart ntp
sudo systemctl status ntp

### Алхам 4: Stratum түвшний шалгалт
ntpq -p

## Даалгавар 5: Journal-аар Логийг Харах

### Журнал харах:
journalctl

### Сүүлийн 50 мөр:
journalctl -n 50

### Тодорхой сервисийн лог:
journalctl -u ntp
journalctl -u apache2

### Real-time лог:
journalctl -f
