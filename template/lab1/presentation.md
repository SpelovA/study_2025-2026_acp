---
## Front matter
lang: ru-RU
title: Лабораторная работа №1
subtitle: Подготовка лабораторного стенда
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

- Целью данной работы является приобретение практических навыков установки Rocky Linux на виртуальную машину с помощью инструмента Vagrant.

# Основная часть

## Подготовка

- Создание каталога для проекта.

![](./image/1.png)

## Подготовка

- Размещение образа варианта операционной системы Rocky Linux в рабочем каталоге.

![](./image/2.png)

## Подготовка

- Проверка конфигурационного файла Vagrantfile.

![](./image/3.png)

## Установка окружения виртуальной машины

- Ввод необходимых команд.

![](./image/4.png)

## Установка окружения виртуальной машины

- Регистрации образа виртуальной машины в vagrant.

![](./image/5.png)

## Работа с окружением виртуальной машины

- Запуск виртуальной машины Server.

![](./image/6.png)

## Работа с окружением виртуальной машины

- Запуск виртуальной машины Client.

![](./image/7.png)

## Работа с окружением виртуальной машины

- Вход под пользователем vagrant.

![](./image/8.png)

## Работа с окружением виртуальной машины

- Подключение к серверу из консоли.

![](./image/9.png)

## Работа с окружением виртуальной машины

- Переход к пользователю anspelov.

![](./image/10.png)

## Работа с окружением виртуальной машины

- Проверка на сервере.

![](./image/11.png)

## Работа с окружением виртуальной машины

- Выключение виртуальных машин.

![](./image/12.png)

# Вывод

## Вывод

- В ходе выполнения лабораторной работы были приобретены практические навыки установки Rocky Linux на виртуальную машину с помощью инструмента Vagrant.