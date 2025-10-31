---
## Front matter
lang: ru-RU
title: Лабораторная работа №9
subtitle: Настройка POP3/IMAP сервера
author:
  - Спелов А. Н.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 30 октября 2025

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'

## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
---

# Информация

## Докладчик

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

  * Спелов Андрей Николаевич
  * НПИбд-02-23 Студ. билет: 1132231839
  * Российский университет дружбы народов
  * [1132231839@pfur.ru](mailto:1132231839@pfur.ru)

:::
::: {.column width="30%"}
:::
::::::::::::::

# Вводная часть

## Цель работы

- Целью данной работы является приобретение практических навыков по установке и простейшему конфигурированию POP3/IMAP-сервера.

# Основная часть

## Установка Dovecot

- Открытие режима суперпользователя и установка пакета dovecot telnet.

![](./image/1.png)

## Настройка Dovecot

- Список почтовых протоколов

![](./image/2.png)

## Настройка Dovecot

- Настраиваем месторасположение почтовых ящиков пользователей

![](./image/3.png)

## Настройка Postfix

- Настройка в Postfix каталога для доставки почты.

![](./image/4.png)

## Настройка Dovecot

- Конфигурация межсетевого экрана, разрешив работать службам протоколов POP3 и IMAP.

![](./image/5.png)

## Настройка Dovecot

- Восстановление контекста безопасности в SELinux. Перезапуск Postfix и запуск Dovecot.

![](./image/6.png)

## Проверка работы Dovecot

- Просмотр на терминале сервера имеющейся почты и mailbox пользователя.

![](./image/7.png)

## Установка Evolution

- Установка Evolution на клиенте

![](./image/8.png)

## Настройка Evolution

- Настройка почтового клиента

![](./image/9.png)

## Настройка Evolution

- Настройка почтового клиента

![](./image/10.png)

## Настройка Evolution

- Настройка почтового клиента

![](./image/11.png)

## Проверка работы Dovecot

- Отправка из почтового клиента нескольких тестовых писем и проверка их доставки.

![](./image/12.png)

## Проверка работы Dovecot

- Просмотр сообщений, выдающихся при мониторинге почтовой службы на сервере.Просмотр сообщений, выдающихся при использовании doveadm и mail.

![](./image/13.png)

## Проверка работы Dovecot

- Подключение с помощью протокола Telnet к почтовому серверу по протоколу POP3 (через порт 110), ввод своего логина для подключения и пароля

![](./image/14.png)

## Проверка работы Dovecot

- Получение списка писем, получение первого письма из списка, удаление второго письма из списка, завершение сеанса работы с telnet.

![](./image/15.png)

## Внесение изменений в настройки внутреннего окружения виртуальной машины

- Переход на виртуальной машине server в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/. Помещение в соответствующие подкаталоги конфигурационных файлов Dovecot и замена конфигурационного файла Postfix.

![](./image/16.png)

## Внесение изменений в настройки внутреннего окружения виртуальной машины

- Внесение изменений в файл /vagrant/provision/server/mail.sh.

![](./image/17.png)

## Внесение изменений в настройки внутреннего окружения виртуальной машины

- Корректирование на виртуальной машине client в каталоге /vagrant/provision/client файла mail.sh.

![](./image/18.png)

# Вывод

## Вывод

- В ходе выполнения лабораторной работы были приобретены практические навыки по установке и простейшему конфигурированию POP3/IMAP-сервера.