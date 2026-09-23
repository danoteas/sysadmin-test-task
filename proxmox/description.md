# Proxmox VE

## Установка

Установил Proxmox VE 9.2.2 в VirtualBox.
VM: 4 GB RAM, 2 CPU, 32 GB диск.
Сеть: Сетевой мост.
Включил nested virtualization через VBoxManage.

IP веб-интерфейса: https://192.168.0.201:8006
Логин: root

## Создание VM

Создал виртуальную машину test-vm со следующими параметрами:

- Name: test-vm
- RAM: 1024 MB
- CPU: 1 core, тип kvm64
- Диск: 8 GB на local-lvm, шина SCSI
- Сеть: VirtIO, bridge vmbr0
- ISO: ubuntu-24.04.5-live-server-amd64.iso

## Установка ОС

Запустил VM, открыл Console в веб-интерфейсе.
Загрузился установщик Ubuntu Server.
Прошла установка, VM загрузилась.

Так как Proxmox работает внутри VirtualBox без полной вложенной виртуализации,
в настройках VM отключил KVM hardware virtualization.
Используется программная эмуляция — для тестового задания этого достаточно.

## Скриншоты

- screenshots/01-proxmox.png — веб-интерфейс Proxmox
- screenshots/02-proxmox.png — Console запущенной VM
