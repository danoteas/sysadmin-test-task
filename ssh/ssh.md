# SSH по ключу

## Генерация ключа

На Windows выполнил ssh-keygen -t ed25519.
Ключ сохранился в C:\Users\Mecht\.ssh\id_ed25519.

## Копирование ключа на сервер

Скопировал публичный ключ на Ubuntu командой type ... | ssh ...
Публичный ключ добавился в ~/.ssh/authorized_keys.

## Отключение входа по паролю

Отредактировал /etc/ssh/sshd_config.d/60-cloudimg-settings.conf

Установил:
PasswordAuthentication no
PubkeyAuthentication yes

Перезапустил SSH: sudo systemctl restart ssh

## Проверка

Захожу с Windows: ssh danoteas@192.168.0.200
Пароль не спрашивает, пускает сразу.

## Скриншоты

- screenshots/01-ssh-no-password.png — вход без пароля
