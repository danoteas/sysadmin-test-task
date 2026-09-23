# WireGuard VPN

## Установка

sudo apt install wireguard -y

## Ключи сервера

Сгенерировал ключи:
wg genkey | sudo tee /etc/wireguard/server_private.key | wg pubkey | sudo tee /etc/wireguard/server_public.key

Публичный ключ сервера: xDt94krQm9glWHLUpnQBJ+/H81OIK+HZ6ag2uGjmeUY=

## IP forwarding

Включил: sudo sysctl -w net.ipv4.ip_forward=1
Добавил в /etc/sysctl.conf, чтобы сохранилось после перезагрузки.

## Конфиг сервера

Файл /etc/wireguard/wg0.conf

Сервер:
- Address 10.0.0.1/24
- ListenPort 51820
- MASQUERADE через enp0s3 для выхода в интернет

Peer:
- Публичный ключ клиента
- AllowedIPs 10.0.0.2/32

Запуск: sudo wg-quick up wg0
Автозапуск: sudo systemctl enable wg-quick@wg0

## Клиент на Windows

Установил WireGuard с официального сайта.
Создал туннель через Add empty tunnel.
Указал:
- Address 10.0.0.2/24
- Endpoint 192.168.0.200:51820
- AllowedIPs 10.0.0.0/24
- PersistentKeepalive 25

## Проверка

На сервере: sudo wg show — видно latest handshake.
На клиенте: ping 10.0.0.1 — работает.

## Скриншоты

- screenshots/01-vpn.png — sudo wg show
- screenshots/02-vpn.png — WireGuard подключен
