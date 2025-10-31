---
## Front matter
title: "Лабораторная работа №9"
subtitle: "Настройка POP3/IMAP сервера"
author: "Спелов Андрей Николаевич"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью данной работы является приобретение практических навыков по установке и простейшему конфигурированию POP3/IMAP-сервера.

# Выполнение лабораторной работы

На виртуальной машине server войдём под нашим пользователем и откроем терминал. Перейдём в режим суперпользователя: 
sudo -i 
И установим необходимые для работы пакеты(рис. [-@fig:001]).

![Открытие режима суперпользователя и установка пакета dovecot telnet.](image/1.png){#fig:001 width=70%}

Теперь проделаем определённые действия в конфигурационных файлах: В конфигурационном файле /etc/dovecot/dovecot.conf пропишем список почтовых протоколов, по которым разрешено работать Dovecot. (рис. [-@fig:002]).

![Список почтовых протоколов](image/2.png){#fig:002 width=70%}

Проверим, что в конфигурационном файле /etc/dovecot/conf.d/10-auth.conf укажем метод аутентификации plain.(Указан) 
В конфигурационном файле /etc/dovecot/conf.d/auth-system.conf.ext проверим, что для поиска пользователей и их паролей используется pam и файл passwd.
В конфигурационном файле /etc/dovecot/conf.d/10-mail.conf настроим месторасположение почтовых ящиков пользователей.(рис. [-@fig:003]).

![Настраиваем месторасположение почтовых ящиков пользователей](image/3.png){#fig:003 width=70%}

В Postfix зададим каталог для доставки почты(рис. [-@fig:004]).

![Настройка в Postfix каталога для доставки почты.](image/4.png){#fig:004 width=70%}

Сконфигурируем межсетевой экран, разрешив работать службам протоколов POP3 и IMAP (рис. [-@fig:005]).

![Конфигурация межсетевого экрана, разрешив работать службам протоколов POP3 и IMAP.](image/5.png){#fig:005 width=70%}

Восстановим контекст безопасности в SELinux: 
restorecon -vR /etc 
После чего перезапустим Postfix и запустим Dovecot (рис. [-@fig:006]).

![Восстановление контекста безопасности в SELinux. Перезапуск Postfix и запуск Dovecot.](image/6.png){#fig:006 width=70%}

На терминале сервера запустим мониторинг и для просмотра имеющейся почты используем: 
MAIL=~/Maildir mail 
А для просмотра mailbox пользователя на сервере используем:
doveadm mailbox list -u anspelov (рис. [-@fig:007]).

![Просмотр на терминале сервера имеющейся почты и mailbox пользователя.](image/7.png){#fig:007 width=70%}

На виртуальной машине client войдём под нашим пользователем и откроем терминал. Перейдём в режим суперпользователя и установим почтовый клиент Evolution.(рис. [-@fig:008]).

![Установка Evolution на клиенте](image/8.png){#fig:008 width=70%}

Далее запустим и настроим почтовый клиент Evolution: в окне настройки учётной записи почты укажем имя, адрес почты в виде anspelov@anspelov.net  (рис. [-@fig:009]).

![Настройка почтового клиента](image/9.png){#fig:009 width=70%}

В качестве IMAP-сервера для входящих сообщений и SMTP-сервера для исходящих сообщений пропишем mail.anspelov.net, в качестве пользователя для входящих и исходящих сообщений укажем anspelov. проверим номера портов: для IMAP — порт 143. проверим настройки SSL и метода аутентификации: для IMAP— STARTTLS(рис. [-@fig:010]).

![Настройка почтового клиента](image/10.png){#fig:010 width=70%}

Проверим номера портов: для SMTP — порт 25. проверим настройки SSL и метода аутентификации: для SMTP — без аутентификации, аутентификация — «Без аутентификации»(рис. [-@fig:011]).

![Настройка почтового клиента](image/11.png){#fig:011 width=70%}

Из почтового клиента отправим себе несколько тестовых писем, убедимся, что они доставлены(рис. [-@fig:012]).

![Отправка из почтового клиента нескольких тестовых писем и проверка их доставки.](image/12.png){#fig:012 width=70%}

Параллельно посмотрим, какие сообщения выдаются при мониторинге почтовой службы на сервере, а также при использовании doveadm и mail (рис. [-@fig:013]).

![Просмотр сообщений, выдающихся при мониторинге почтовой службы на сервере.Просмотр сообщений, выдающихся при использовании doveadm и mail.](image/13.png){#fig:013 width=70%}

Проверим работу почтовой службы, используя на сервере протокол Telnet:  подключимся с помощью протокола Telnet к почтовому серверу по протоколу POP3, введём свой логин для подключения и пароль(рис. [-@fig:014]).

![Подключение с помощью протокола Telnet к почтовому серверу по протоколу POP3 (через порт 110), ввод своего логина для подключения и пароля](image/14.png){#fig:014 width=70%}

С помощью команды list получим список писем, с помощью команды retr 1 получим первое письмо из списка, с помощью команды dele 2 удалим второе письмо из списка, с помощью команды quit завершим сеанс работы с telnet (рис. [-@fig:015]).

![Получение списка писем, получение первого письма из списка, удаление второго письма из списка, завершение сеанса работы с telnet.](image/15.png){#fig:015 width=70%}

На виртуальной машине server перейдём в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/. В соответствующие подкаталоги поместим конфигурационные файлы Dovecot и заменим конфигурационный файл Postfix(рис. [-@fig:016]).

![Переход на виртуальной машине server в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/. Помещение в соответствующие подкаталоги конфигурационных файлов Dovecot и замена конфигурационного файла Postfix.](image/16.png){#fig:016 width=70%}

Внесём изменения в файл /vagrant/provision/server/mail.sh, добавив в него строки(рис. [-@fig:017]).

![Внесение изменений в файл /vagrant/provision/server/mail.sh.](image/17.png){#fig:017 width=70%}

На виртуальной машине client в каталоге /vagrant/provision/client скорректируем файл mail.sh (рис. [-@fig:018]).

![Корректирование на виртуальной машине client в каталоге /vagrant/provision/client файла mail.sh.](image/18.png){#fig:018 width=70%}

# Выводы

В ходе выполнения лабораторной работы были приобретены практические навыки по установке и простейшему конфигурированию POP3/IMAP-сервера.

# Ответы на контрольные вопросы:

1.	За что отвечает протокол SMTP? - Отвечает за отправку электронной почты. Этот протокол используется для передачи писем от отправителя к почтовому серверу и от сервера к серверу.

2.	За что отвечает протокол IMAP? - Отвечает за доступ и управление электронной почтой на сервере. Позволяет клиентским приложениям просматривать, синхронизировать и управлять сообщениями, хранящимися на почтовом сервере.

3.	За что отвечает протокол POP3? - Отвечает за получение электронной почты. Письма загружаются с почтового сервера на клиентский компьютер, и после этого они обычно удаляются с сервера (но это можно настроить).

4.	В чём назначение Dovecot? - Это почтовый сервер, который предоставляет поддержку протоколов IMAP и POP3. Dovecot обеспечивает доступ к электронной почте на сервере, а также хранение и управление сообщениями.

5.	В каких файлах обычно находятся настройки работы Dovecot? За что отвечает каждый из файлов? – 
/etc/dovecot/dovecot.conf: Основной файл конфигурации Dovecot.
/etc/dovecot/conf.d/: Дополнительные файлы конфигурации, разделенные на отдельные модули.

6.	В чём назначение Postfix? - Это почтовый сервер (MTA - Mail Transfer Agent), отвечающий за отправку и маршрутизацию электронной почты.

7.	Какие методы аутентификации пользователей можно использовать в Dovecot и в чём их отличие? – 
PLAIN: Передача учетных данных в открытом виде (не рекомендуется, если соединение не защищено).
LOGIN: Аутентификация по протоколу LOGIN, который шифрует только пароль.

8.	Приведите пример заголовка письма с пояснениями его полей. – 
From: john.doe@example.com
To: jane.smith@example.com
Subject: Meeting Tomorrow
Date: Tue, 6 Dec 2023 14:30:00 +0000

9.	Приведите примеры использования команд для работы с почтовыми протоколами через терминал (например через telnet). - 
Использование Telnet для проверки SMTP:
telnet example.com 25
EHLO example.com
MAIL FROM: sender@example.com
RCPT TO: recipient@example.com
DATA
Subject: Test Email
This is a test email.
.
QUIT
Использование Telnet для проверки POP3:
telnet example.com 110
USER your_username
PASS your_password
LIST
RETR 1
QUIT

10.	Приведите примеры с пояснениями по работе с doveadm. - 
Получение информации о пользователях:
doveadm user user@example.com
Получение списка всех писем пользователя:
doveadm search mailbox INBOX ALL
Удаление письма:
doveadm expunge -u user@example.com mailbox INBOX uid <UID>

# Список литературы{.unnumbered}

::: {#refs}
:::
