---
## Front matter
title: "Лабораторная работа №15"
subtitle: "Настройка сетевого журналирования"
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

Целью данной работы является получение навыков по работе с журналами системных событий.

# Выполнение лабораторной работы

На сервере создадим файл конфигурации сетевого хранения журналов(рис. [-@fig:001]).

![Создание на сервере файла конфигурации сетевого хранения журналов.](image/1.png){#fig:001 width=70%}

В файле конфигурации /etc/rsyslog.d/netlog-server.conf включим приём записей журнала по TCP-порту 514 (рис. [-@fig:002]).

![Включение в файле конфигурации /etc/rsyslog.d/netlog-server.conf приёма записей журнала по TCP-порту 514.](image/2.png){#fig:002 width=70%}

Перезапустим службу rsyslog и посмотрим, какие порты, связанные с rsyslog, прослушиваются(рис. [-@fig:003]).

![Перезапуск службы rsyslog и просмотр прослушиваемых портов, связанных с rsyslog.](image/3.png){#fig:003 width=70%}

На сервере настроим межсетевой экран для приёма сообщений по TCP-порту 514(рис. [-@fig:004]).

![Настройка на сервере межсетевого экрана для приёма сообщений по TCP-порту 514.](image/4.png){#fig:004 width=70%}

На клиенте создадим файл конфигурации сетевого хранения журналов (рис. [-@fig:005]).

![Создание на клиенте файла конфигурации сетевого хранения журналов.](image/5.png){#fig:005 width=70%}

Далее в файле конфигурации /etc/rsyslog.d/netlog-client.conf включим перенаправление сообщений журнала на 514 TCP-порт сервера (рис. [-@fig:006]).

![Включение в файле конфигурации /etc/rsyslog.d/netlog-client.conf перенаправления сообщений журнала на 514 TCP-порт сервера.](image/6.png){#fig:006 width=70%}

Перезапустим службу rsyslog (рис. [-@fig:007]).

![Перезапуск службы rsyslog.](image/7.png){#fig:007 width=70%}

На сервере просмотрим один из файлов журнала(рис. [-@fig:008]).

![Просмотр на сервере одного из файлов журнала.](image/8.png){#fig:008 width=70%}

На сервере под пользователем anspelov запустим графическую программу для просмотра журналов (рис. [-@fig:009]).

![Запуск на сервере под пользователем anspelov графической программы для просмотра журналов.](image/9.png){#fig:009 width=70%}

На сервере установим просмотрщик журналов системных сообщений(рис. [-@fig:010]).

![Установка на сервере просмотрщика журналов системных сообщений.](image/10.png){#fig:010 width=70%}

Просмотрим логи(рис. [-@fig:011]).

![Просмотр логов.](image/11.png){#fig:011 width=70%}

На виртуальной машине server перейдём в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/, создадим в нём каталог netlog, в который поместим в соответствующие подкаталоги конфигурационные файлы. В каталоге /vagrant/provision/server создадим исполняемый файл netlog.sh(рис. [-@fig:012]).

![Переход на виртуальной машине server в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/, создание в нём каталога netlog, в который помещаем в соответствующие подкаталоги конфигурационные файлы. Создание в каталоге /vagrant/provision/server исполняемого файла netlog.sh.](image/12.png){#fig:012 width=70%}

Открыв его на редактирование, пропишем в нём скрипт (рис. [-@fig:013]).

![Открытие файла на редактирование и добавление в него скрипта.](image/13.png){#fig:013 width=70%}

На виртуальной машине client перейдём в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/client/, создадим в нём каталог nentlog, в который поместим в соответствующие подкаталоги конфигурационные файлы. В каталоге /vagrant/provision/client создадим исполняемый файл netlog.sh(рис. [-@fig:014]).

![Переход на виртуальной машине client в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/client/, создание в нём каталога nentlog, в который помещаем в соответствующие подкаталоги конфигурационные файлы. Создание в каталоге /vagrant/provision/client исполняемого файла netlog.sh.](image/14.png){#fig:014 width=70%}

Открыв его на редактирование, пропишем в нём скрипт (рис. [-@fig:015]).

![Открытие файла на редактирование и добавление в него скрипта.](image/15.png){#fig:015 width=70%}

Для отработки созданных скриптов во время загрузки виртуальных машин server и client в конфигурационном файле Vagrantfile добавим в соответствующих разделах конфигураций для сервера и клиента (рис. [-@fig:016]).

![Добавление конфигураций в конфигурационном файле Vagrantfile для сервера и клиента.](image/16.png){#fig:016 width=70%}

# Выводы

В ходе выполнения лабораторной работы были получены навыки по работе с журналами системных событий.

# Ответы на контрольные вопросы:

1. Какой модуль rsyslog вы должны использовать для приёма сообщений от journald? - Для приёма сообщений от journald в rsyslog используется модуль imjournal.

2. Как называется устаревший модуль, который можно использовать для включения приёма сообщений журнала в rsyslog? - Устаревший модуль для приема сообщений журнала в rsyslog - imuxsock (или imuxsock_legacy).

3. Чтобы убедиться, что устаревший метод приёма сообщений из journald в rsyslog не используется, какой дополнительный параметр следует использовать? - Для предотвращения использования устаревшего метода можно использовать параметр SystemMaxUseForward=no в файле /etc/systemd/journald.conf.

4. В каком конфигурационном файле содержатся настройки, которые позволяют вам настраивать работу журнала? - Настройки, позволяющие настроить работу журнала, содержатся в файле /etc/systemd/journald.conf.

5. Каким параметром управляется пересылка сообщений из journald в rsyslog? - Для управления пересылкой сообщений из journald в rsyslog используется параметр ForwardToSyslog=yes в файле /etc/systemd/journald.conf.

6. Какой модуль rsyslog вы можете использовать для включения сообщений из файла журнала, не созданного rsyslog? - Для включения сообщений из файла журнала, не созданного rsyslog, используется модуль imfile.

7. Какой модуль rsyslog вам нужно использовать для пересылки сообщений в базу данных MariaDB? - Для пересылки сообщений в базу данных MariaDB используется модуль ommysql или ommysqlps.

8. Какие две строки вам нужно включить в rsyslog.conf, чтобы позволить текущему журнальному серверу получать сообщения через TCP? - Добавьте следующие строки в rsyslog.conf:
$ModLoad imtcp
$InputTCPServerRun 514

9. Как настроить локальный брандмауэр, чтобы разрешить приём сообщений журнала через порт TCP 514? – 
Используйте команды для открытия порта:
sudo firewall-cmd --permanent --add-port=514/tcp
sudo firewall-cmd --reload
Или:
sudo iptables -A INPUT -p tcp --dport 514 -j ACCEPT
sudo service iptables save
sudo service iptables restart

# Список литературы{.unnumbered}

::: {#refs}
:::
