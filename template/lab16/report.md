---
## Front matter
title: "Лабораторная работа №16"
subtitle: "Базовая защита от атак типа «brute force»"
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

Целью данной работы является получение навыков работы с программным средством Fail2ban для обеспечения базовой защиты от атак типа «brute force».

# Выполнение лабораторной работы

На сервере установим fail2ban (рис. [-@fig:001]):

![Установка на сервере fail2ban.](image/1.png){#fig:001 width=70%}

Запустим сервер fail2ban (рис. [-@fig:002]):

![Запуск сервера fail2ban.](image/2.png){#fig:002 width=70%}

В дополнительном терминале запустим просмотр журнала событий fail2ban (рис. [-@fig:003]):

![Запуск просмотра в дополнительном терминале журнала событий fail2ban.](image/3.png){#fig:003 width=70%}

Создадим файл с локальной конфигурацией fail2ban (рис. [-@fig:004]):

![Создание файла с локальной конфигурацией fail2ban.](image/4.png){#fig:004 width=70%}

В файле /etc/fail2ban/jail.d/customisation.local зададим время блокирования на 1 час и включим защиту SSH (рис. [-@fig:005]):

![Настройка в файле /etc/fail2ban/jail.d/customisation.local времени блокирования на 1 час и включение защиты SSH.](image/5.png){#fig:005 width=70%}

Перезапустим fail2ban (рис. [-@fig:006]):

![Перезапуск fail2ban.](image/6.png){#fig:006 width=70%}

Посмотрим журнал событий (рис. [-@fig:007]):

![Просмотр журнала событий.](image/7.png){#fig:007 width=70%}

В файле /etc/fail2ban/jail.d/customisation.local включим защиту HTTP (рис. [-@fig:008]):

![Включение защиты HTTP в файле /etc/fail2ban/jail.d/customisation.local.](image/8.png){#fig:008 width=70%}

Перезапустим fail2ban (рис. [-@fig:009]):

![Перезапуск fail2ban.](image/9.png){#fig:009 width=70%}

После чего посмотрим журнал событий (рис. [-@fig:010]):

![Просмотр журнала событий.](image/10.png){#fig:010 width=70%}

В файле /etc/fail2ban/jail.d/customisation.local включим защиту почты (рис. [-@fig:011]):

![Включение защиты почты в файле /etc/fail2ban/jail.d/customisation.local.](image/11.png){#fig:011 width=70%}

Снова перезапустим fail2ban (рис. [-@fig:012]):

![Повторный перезапуск fail2ban.](image/12.png){#fig:012 width=70%}

И посмотрим журнал событий (рис. [-@fig:013]):

![Просмотр журнала событий.](image/13.png){#fig:013 width=70%}

На сервере посмотрим статус fail2ban, статус защиты SSH в fail2ban и установим максимальное количество ошибок для SSH, равное 2 (рис. [-@fig:014]):

![Просмотр на сервере статуса fail2ban, статуса защиты SSH в fail2ban и установка максимального количества ошибок для SSH (=2).](image/14.png){#fig:014 width=70%}

С клиента попытаемся зайти по SSH на сервер с неправильным паролем (рис. [-@fig:015]):

![Попытка зайти с клиента по SSH на сервер с неправильным паролем.](image/15.png){#fig:015 width=70%}

На сервере посмотрим статус защиты SSH и разблокируем IP-адрес клиента. После чего вновь посмотрим статус защиты SSH и убедимся, что блокировка клиента снята (рис. [-@fig:016]):

![Просмотр на сервере статуса защиты SSH, разблокировка IP-адреса клиента и повторная проверка.](image/16.png){#fig:016 width=70%}

На сервере внесём изменение в конфигурационный файл /etc/fail2ban/jail.d/customisation.local, добавив в раздел по умолчанию игнорирование адреса клиента (рис. [-@fig:017]):

![Добавление в раздел по умолчанию игнорирование адреса клиента в конфигурационном файле /etc/fail2ban/jail.d/customisation.local.](image/17.png){#fig:017 width=70%}

Перезапустим fail2ban (рис. [-@fig:018]):

![Перезапуск fail2ban.](image/18.png){#fig:018 width=70%}

Далее посмотрим журнал событий (рис. [-@fig:019]):

![Просмотр журнала событий.](image/19.png){#fig:019 width=70%}

Вновь попытаемся войти с клиента на сервер с неправильным паролем (рис. [-@fig:020]) и посмотрим статус защиты SSH (рис. [-@fig:021]):

![Попытка войти с клиента на сервер с неправильным паролем.](image/20.png){#fig:020 width=70%}

![Просмотр статуса защиты SSH.](image/21.png){#fig:021 width=70%}

На виртуальной машине server перейдём в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/, создадим в нём каталог protect, в который поместим в соответствующие подкаталоги конфигурационные файлы. В каталоге /vagrant/provision/server создадим исполняемый файл protect.sh (рис. [-@fig:022]):

![Переход на виртуальной машине server в каталог для внесения изменений в настройки внутреннего окружения /vagrant/provision/server/, создание в нём каталога protect, в который помещаем в соответствующие подкаталоги конфигурационные файлы. Создание в каталоге /vagrant/provision/server исполняемого файла protect.sh.](image/22.png){#fig:022 width=70%}

Открыв его на редактирование, пропишем в нём скрипт (рис. [-@fig:023]):

![Открытие файла на редактирование и добавление в него скрипта.](image/23.png){#fig:023 width=70%}

Для отработки созданного скрипта во время загрузки виртуальной машины server в конфигурационном файле Vagrantfile добавим в соответствующем разделе конфигураций для сервера (рис. [-@fig:024]):

![Добавление конфигураций в конфигурационном файле Vagrantfile для сервера](image/24.png){#fig:024 width=70%}

# Выводы

В ходе выполнения лабораторной работы были получены навыки работы с программным средством Fail2ban для обеспечения базовой защиты от атак типа «brute force».

# Ответы на контрольные вопросы:

1.	Поясните принцип работы Fail2ban. - Fail2ban является инструментом для защиты от атак на серверы, основанных на анализе журналов. Он мониторит журналы системы на предмет неудачных попыток входа или других событий, а затем блокирует IP-адреса атакующих с использованием системных средств, таких как iptables. Принцип работы:
Мониторинг журналов на предмет определенных событий.
Обнаружение повторных неудачных попыток входа или других нарушений.
Динамическое обновление правил брандмауэра для блокировки атакующих IP-адресов.

2.	Настройки какого файла более приоритетны: jail.conf или jail.local? - Настройки файла jail.local имеют более высокий приоритет и перекрывают настройки из jail.conf. Таким образом, если есть конфликтующие настройки, они будут использоваться из jail.local.

3.	Как настроить оповещение администратора при срабатывании Fail2ban? - В файле jail.local нужно указать параметр destemail и задать адрес электронной почты, а также параметр action с указанием определенного действия (например, action_mw для отправки почты).

4.	Поясните построчно настройки по умолчанию в конфигурационном файле /etc/fail2ban/jail.conf, относящиеся к веб-службе. – 
Пример настроек для веб-службы в файле jail.conf:
[apache]
enabled  = true
port     = http,https
filter   = apache-auth
logpath  = /var/log/apache*/*error.log

5.	Поясните построчно настройки по умолчанию в конфигурационном файле /etc/fail2ban/jail.conf, относящиеся к почтовой службе. – 
Пример настроек для почтовой службы в файле jail.conf:
[postfix]
enabled  = true
filter   = postfix
action   = iptables-multiport[name=postfix, port="submission,smtps", protocol=tcp]

6.	Какие действия может выполнять Fail2ban при обнаружении атакующего IP-адреса? Где можно посмотреть описание действий для последующего использования в настройках Fail2ban? - Fail2ban может выполнять различные действия, такие как блокировка IP-адреса с использованием брандмауэра, отправка уведомлений, добавление в черные списки и т.д. Описание действий можно найти в конфигурационных файлах в разделе action.

7.	Как получить список действующих правил Fail2ban? - Используйте команду: fail2ban-client status.

8.	Как получить статистику заблокированных Fail2ban адресов? - Используйте команду: fail2ban-client status <jail_name>. 

9.	Как разблокировать IP-адрес? - Используйте команду: fail2ban-client set <jail_name> unbanip <ip_address>.

# Список литературы{.unnumbered}

::: {#refs}
:::
