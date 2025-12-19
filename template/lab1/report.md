---
## Front matter
title: "Лабораторная работа №1"
subtitle: "Подготовка лабораторного стенда"
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

Целью данной работы является приобретение практических навыков установки Rocky Linux на виртуальную машину с помощью инструмента Vagrant.

# Выполнение лабораторной работы

Перед началом работы с Vagrant создадим каталог для проекта. В ОС Windows C:\work\anspelov\packer и C:\work\anspelov\vagrant (рис. [-@fig:001]).

![Создание каталога для проекта.](image/1.png){#fig:001 width=70%}

В созданном рабочем каталоге разместим образ варианта операционной системы Rocky Linux, в этом практикуме используем Rocky-10-x86_64-minimal.iso (рис. [-@fig:002]). В этом же каталоге разместим подготовленные заранее для работы с Vagrant файлы и создадим каталог provision с подкаталогами default, server и client, в которых будут размещаться скрипты, изменяющие настройки внутреннего окружения базового (общего) образа виртуальной машины, сервера или клиента соответственно.

![Размещение образа варианта операционной системы Rocky Linux в рабочем каталоге.](image/2.png){#fig:002 width=70%}

Для отработки созданных скриптов во время загрузки виртуальных машин убедимся, что в конфигурационном файле Vagrantfile до строк с конфигурацией сервера имеется определённая запись (дана в лабораторной работе) (рис. [-@fig:003]).

![Проверка конфигурационного файла Vagrantfile.](image/3.png){#fig:003 width=70%}

Используя FAR, перейдем в созданный нами рабочий каталог с проектом. В этом же каталоге должен быть размещён файл packer.exe. В командной строке введем команды для начала автоматической установки образа операционной системы Rocky Linux в VirtualBox и последующего формирования box-файла с дистрибутивом Rocky Linux для VirtualBox (рис. [-@fig:004]):

![Ввод необходимых команд.](image/4.png){#fig:004 width=70%}

Для регистрации образа виртуальной машины в vagrant в командной строке введем (рис. [-@fig:005]):

![Регистрации образа виртуальной машины в vagrant.](image/5.png){#fig:005 width=70%}

Для запуска виртуальной машины Server введем в консоли (рис. [-@fig:006]):

![Запуск виртуальной машины Server.](image/6.png){#fig:006 width=70%}

Для запуска виртуальной машины Client введите в консоли (рис. [-@fig:007]):

![Запуск виртуальной машины Client.](image/7.png){#fig:007 width=70%}

Убедимся, что запуск обеих виртуальных машин прошёл успешно, залогинемся под пользователем vagrant с паролем vagrant в графическом окружении (рис. [-@fig:008]).

![Вход под пользователем vagrant.](image/8.png){#fig:008 width=70%}

Подключимся к серверу из консоли: vagrant ssh server Ввод пароль vagrant (рис. [-@fig:009]).

![Подключение к серверу из консоли.](image/9.png){#fig:009 width=70%}

Перейдем к пользователю anspelov (рис. [-@fig:010]): su – anspelov

![Переход к пользователю anspelov.](image/10.png){#fig:010 width=70%}

Отлогинемся и выполним тоже самое для клиента (рис. [-@fig:011]).

![Проверка на сервере.](image/11.png){#fig:011 width=70%}

Выключите обе виртуальные машины (рис. [-@fig:012]): vagrant halt server vagrant halt client

![Выключение виртуальных машин.](image/12.png){#fig:012 width=70%}

# Выводы

В ходе выполнения лабораторной работы были приобретены практические навыки установки Rocky Linux на виртуальную машину с помощью инструмента Vagrant.

# Ответы на контрольные вопросы:

1.	Для чего предназначен Vagrant? – Это инструмент для создания и управления средами виртуальных машин в одном рабочем процессе. Он позволяет автоматизировать процесс установки на виртуальную машину как основного дистрибутива операционной системы, так и настройки необходимого в дальнейшем программного обеспечения.

2.	Что такое box-файл? В чём назначение Vagrantfile? - box-файл (или Vagrant Box) — сохранённый образ виртуальной машины с развёрнутой в ней операционной системой, box-файл используется как основа для клонирования виртуальных машин с теми или иными настройками. Vagrantfile — конфигурационный файл, написанный на языке Ruby, в котором указаны настройки запуска виртуальной машины.

3.	Приведите описание и примеры вызова основных команд Vagrant. 
vagrant help — вызов справки по командам Vagrant; 
vagrant box list — список подключённых к Vagrant box-файлов; 
vagrant box add — подключение box-файла к Vagrant; 
vagrant destroy— отключение box-файла от Vagrant и удаление его из виртуального окружения; 
vagrant init — создание «шаблонного» конфигурационного файла Vagrantfile для его последующего изменения; 
vagrant up — запуск виртуальной машины с использованием инструкций по запуску из конфигурационного файла Vagrantfile; 
vagrant reload — перезагрузка виртуальной машины; 
vagrant halt — остановка и выключение виртуальной машины; 
vagrant provision — настройка внутреннего окружения имеющейся виртуальной машины (например, добавление новых инструкций (скриптов) в ранее созданную виртуальную машину); 
vagrant ssh — подключение к виртуальной машине через ssh.

4.	Дайте построчные пояснения содержания файлов vagrant-rocky.pkr.hcl, ks.cfg, Vagrantfile, Makefile.
Vagrantfile - Первые две строки указывают на режим работы с Vagrantfile и использование языка Ruby. Затем идёт цикл do, заменяющий конструкцию Vagrant.configure далее по тексту на config. Строка config.vm.box = "BOX_NAME" задаёт название образа (box-файла) виртуальной машины (обычно выбирается из официального репозитория). Строка config.vm.hostname = "HOST_NAME" задаёт имя виртуальной машины. Конструкция config.vm.network задаёт тип сетевого соединения и может иметь следующие назначения: – config.vm.network "private_network", ip: "xxx.xxx.xxx.xxx" — адрес из внутренней сети; – config.vm.network "public_network", ip: "xxx.xxx.xxx.xxx" — публичный адрес, по которому виртуальная машина будет доступна; – config.vm.network "private_network", type: "dhcp" — адрес, назначаемый по протоколу DHCP. Строка config.vm.define "VM_NAME" задаёт название виртуальной машины, по которому можно обращаться к ней из Vagrant и VirtualBox. В конце идёт конструкция, определяющая параметры провайдера, а именно запуск виртуальной машины без графического интерфейса и с выделением 1 ГБ памяти.

# Список литературы{.unnumbered}

::: {#refs}
:::
