University: [ITMO University](https://itmo.ru/ru/)

Faculty: [FICT](https://fict.itmo.ru)

Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)

Year: 2024/2025

Group: K3320

Author: Shimchenko Alexandra Sergeevna

Lab: Lab1

Date of create: 26.03.2025

Date of finished: 5.04.2025

# Отчет по лабораторной работе №1 "Установка CHR и Ansible, настройка VPN" #

## Цель работы: ##
Целью данной работы является развертывание виртуальной машины на базе платформы Microsoft Azure с установленной системой контроля конфигураций Ansible и установка CHR в VirtualBox

## Ход работы: ##

### Создание виртуальной машины Ubuntu в Selectel ###
В начале создаётся виртуальная машина со следующими параметрами
![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/c69f88e4-e54e-4ee9-abfd-949d8b6533f7)

### Создание виртуальной машины RouterOS и подключение к ней через WinBox ###
С официального сайта MikroTik был скачан образ RouterOS и установлен с помощью VirtualBox

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/42ab814c-cf6d-4a2f-a3db-4a8b96d066fd)

Также был настроен сетевой мост

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/9cada01c-2e45-401e-82de-e54f4ce7435c)

С помощью Winbox подключимся к CHR (используя логин, пароль и ip)

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/0fa80880-d35c-4554-8c91-d831b3370b54)

Подключение произошло успешно 

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/407182e5-1d46-40c4-b10c-72387cf5dcda)

### Настройка VPN сервера ###

Также установим Pyhton и Ansible для виртуальной машины Ubuntu
Для этого пропишем команды:

```
sudo apt update
sudo apt install python3-pip
sudo pip3 install ansible
```

Для организации VPN-туннеля между сервером автоматизации и локальным компьютером был развернут OpenVPN-сервер через AmneziaVPN. В настройках отключены TLS-авторизация и блокировка DNS-запросов вне VPN, а также выбраны алгоритмы шифрования SHA256 (для аутентификации) и AES-256-GCM (для передачи данных). 

![Конфигурация OpenVPN](images/vpn_config.png)

С помощью OpenVPN Connect запустили экспортированный из AmneziaVPN `.ovpn`-файл, после этого VPN-туннель был успешно установлен. 
![Конфигурация OpenVPN](images/vpn_config.png)

Внешний IP-адрес сервера — `31.129.45.104`, что подтверждает корректность маршрутизации трафика через VPN.

![Подключение к VPN](images/openvpn_connect.png)


### Донастройка CHR ###

Откроем установленное приложение WinBox и добавим ранее загруженный файл.

![изображение](https://github.com/fiji6479/2023_2024-network_programming-k34212-gomzyakov_a_n/assets/71012423/b71eb9ff-e78b-4621-80a4-a34e1ac5a30d)

## Вывод ##

В результате выполнения лабораторной работы были получены навыки по развертыванию виртуальной машины на платформе Selectel. Также был установлен CHR в VirtualBox и настроен VPN туннель между сервером и клиентом.
