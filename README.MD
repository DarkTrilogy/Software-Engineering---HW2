# Домашнее задание: Работа с серверами и SSH

## Цель работы
Освоить базовые операции работы с SSH:
- установка и настройка SSH-сервера
- подключение к удалённому серверу
- копирование файлов по SCP
- настройка доступа по SSH-ключам

Окружение выполнения:
- Хостовая ОС: macOS
- Виртуализация: Oracle VirtualBox
- Гостевая ОС: Ubuntu
- SSH-сервер: OpenSSH

---

## Кейс 1: Установка и настройка SSH-сервера

### Выполненные шаги

1. Установлен SSH-сервер:
```bash
sudo apt update
sudo apt install openssh-server -y
```
2. Запущен сервер:
```bash
sudo systemctl start ssh
```
3. Проверен статус сервиса:
```bash
sudo systemctl status ssh
```
Результат![1. ssh-status.jpg](screenshots/1.%20ssh-status.jpg)
SSH-сервер установлен и запущен, статус — active (running).

## Кейс 2: Подключение к удалённому серверу

### Выполненные шаги

1. Подключение к серверу выполнено командой:
```bash
ssh admin@192.168.3.70
```
После ввода пароля выполнен успешный вход в систему.

Результат ![2. ssh-connect.jpg](screenshots/2.%20ssh-connect.jpg)
Успешное подключение к удалённому серверу по SSH.

## Кейс 3: Копирование файлов с помощью SCP

### Выполненные шаги

1. Копирование файла на сервер:
```bash
scp test.txt admin@192.168.3.70:/home/admin/test
```
Результат ![file-on-host.jpg](screenshots/3.%20ssh-upload/file-on-host.jpg) ![file-on-host-2.jpg](screenshots/3.%20ssh-upload/file-on-host-2.jpg) ![file-on-server.jpg](screenshots/3.%20ssh-upload/file-on-server.jpg)
2. Копирование файла с сервера:
```bash
scp admin@192.168.3.70:/home/admin/test/file_to_host.txt ./test_copy.txt
```
Результат ![4. ssh-download.jpg](screenshots/4.%20ssh-download.jpg)
Файлы успешно переданы на сервер и получены обратно.

## Кейс 4: Работа с SSH-ключами

### Выполненные шаги

1. Генерация ключей:
```bash
ssh-keygen
```
Ключи созданы в директории ~/.ssh/.

2. Копирование публичного ключа на сервер:
```bash
ssh-copy-id admin@192.168.3.70
```

3. Подключение без пароля
```bash
ssh admin@192.168.3.70
```
Результат ![ssh-keygen.jpg](screenshots/5.%20ssh-key-loign/ssh-keygen.jpg) ![ssh-enter-by-key.jpg](screenshots/5.%20ssh-key-loign/ssh-enter-by-key.jpg)
SSH-ключи сгенерированы\
Публичный ключ добавлен на сервер\
Подключение выполняется без ввода пароля


## Вывод
В ходе работы были успешно выполнены все четыре практических кейса по теме SSH. Настроен безопасный доступ к серверу, реализована передача файлов и вход по ключам.