---
## Front matter
lang: ru-RU
title: Лабораторная работа №16
subtitle: Базовая защита от атак типа «brute force»
author:
  - Спелов А. Н.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 17 декабря 2025

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

- Целью данной работы является приобретение навыков настройки сервера NFS для удалённого доступа к ресурсам.

# Основная часть

## Защита с помощью Fail2ban

- Установка на сервере fail2ban.

![](./image/1.png)

## Защита с помощью Fail2ban

- Запуск сервера fail2ban.

![](./image/2.png)

## Защита с помощью Fail2ban

- Запуск просмотра в дополнительном терминале журнала событий fail2ban.

![](./image/3.png)

## Защита с помощью Fail2ban

- Создание файла с локальной конфигурацией fail2ban.

![](./image/4.png)

## Защита с помощью Fail2ban

- Настройка в файле /etc/fail2ban/jail.d/customisation.local времени блокирования на 1 час и включение защиты SSH.

![](./image/5.png)

## Защита с помощью Fail2ban

- Перезапуск fail2ban.

![](./image/6.png)

## Защита с помощью Fail2ban

- Просмотр журнала событий.

![](./image/7.png)

## Защита с помощью Fail2ban

- Включение защиты HTTP в файле /etc/fail2ban/jail.d/customisation.local.

![](./image/8.png)

## Защита с помощью Fail2ban

- Перезапуск fail2ban.

![](./image/9.png)

## Защита с помощью Fail2ban

- Просмотр журнала событий.

![](./image/10.png)

## Защита с помощью Fail2ban

- Включение защиты почты в файле /etc/fail2ban/jail.d/customisation.local.

![](./image/11.png)

## Защита с помощью Fail2ban

- Повторный перезапуск fail2ban.

![](./image/12.png)

## Защита с помощью Fail2ban

- Просмотр журнала событий.

![](./image/13.png)

## Проверка работы Fail2ban

- Просмотр на сервере статуса fail2ban, статуса защиты SSH в fail2ban и установка максимального количества ошибок для SSH (=2).

![](./image/14.png)

## Проверка работы Fail2ban

- Попытка зайти с клиента по SSH на сервер с неправильным паролем.

![](./image/15.png)

## Проверка работы Fail2ban

- Просмотр на сервере статуса защиты SSH, разблокировка IP-адреса клиента и повторная проверка.

![](./image/16.png)

## Проверка работы Fail2ban

- Добавление в раздел по умолчанию игнорирование адреса клиента в конфигурационном файле /etc/fail2ban/jail.d/customisation.local.

![](./image/17.png)

## Проверка работы Fail2ban

- Перезапуск fail2ban.

![](./image/18.png)

## Проверка работы Fail2ban

- Просмотр журнала событий.

![](./image/19.png)

## Проверка работы Fail2ban

- Попытка войти с клиента на сервер с неправильным паролем.

![](./image/20.png)

## Проверка работы Fail2ban

- Просмотр статуса защиты SSH.

![](./image/21.png)

## Внесение изменений в настройки внутреннего окружения виртуальных машин

- Переход на виртуальной машине server в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/, создание в нём каталога protect, в который помещаем в соответствующие подкаталоги конфигурационные файлы. Создание в каталоге /vagrant/provision/server исполняемого файла protect.sh.

![](./image/22.png)

## Внесение изменений в настройки внутреннего окружения виртуальных машин

- Открытие файла на редактирование и добавление в него скрипта.

![](./image/23.png)

## Внесение изменений в настройки внутреннего окружения виртуальных машин

- Добавление конфигураций в конфигурационном файле Vagrantfile для сервера.

![](./image/24.png)

# Вывод

## Вывод

- В ходе выполнения лабораторной работы были получены навыки работы с программным средством Fail2ban для обеспечения базовой защиты от атак типа «brute force».