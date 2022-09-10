---
# Front matter
title: "Отчёт по лабораторной работе №1"
subtitle: "Установка и конфигурация операционной системы на виртуальную машину"
author: "Бронникова де Менезеш Эвелина"

# Generic options
lang: ru-RU
toc-title: "Содержание"

# Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

# Pdf output format
toc: true # Table of contents
toc_depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 12pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n
polyglossia-lang:
  name: russian
  options:
    - spelling=modern
    - babelshorthands=true
polyglossia-otherlangs:
  name: english
### Fonts
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
## Misc options
indent: true
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Целью данной работы является приобретение практических навыков установки операционной системы на виртуальную машину, настройки минимально необходимых для дальнейшей работы сервисов.


# Теоретическое введение

## **Техническое обеспечение**

Лабораторная работа подразумевает установку на виртуальную машину VirtualBox (https://www.virtualbox.org/) операционной системы Linux (дистрибутив Rocky (https://rockylinux.org/) или CentOS (https://www.centos.org/)).

Выполнение работы возможно как в дисплейном классе факультета физико-математических и естественных наук РУДН, так и дома. Описание выполнения работы приведено для дисплейного класса со следующими характеристиками:
– Intel Core i3-550 3.2 GHz, 4 GB оперативной памяти, 20 GB свободного места на жёстком диске;
– ОС Linux Gentoo (http://www.gentoo.ru/);
– VirtualBox верс. 6.1 или старше;
– каталог с образами ОС для работающих в дисплейном классе:
/afs/dk.sci.pfu.edu.ru/common/files/iso/.

## **Соглашения об именовании**

При выполнении работ следует придерживаться следующих правил именования: *имя виртуальной машины, имя хоста вашей виртуальной машины, пользователь внутри виртуальной машины* **должны совпадать с логином студента, выполняющего лабораторную работу**. Вы можете посмотреть ваш логин, набрав в терминале ОС типа Linux команду id -un. [^1]

[^1]:[Кулябов Д.С. Лабораторная работа № 1.  Установка и конфигурация операционной системы на виртуальную машину - 14 c.](https://esystem.rudn.ru/pluginfile.php/1651880/mod_folder/content/0/001-lab_virtualbox.pdf?forcedownload=1)

# Выполнение лабораторной работы

Для создания новой виртуальной машины необходимо запустить VirtualBox и выбрать *Машина > Создать*. Затем указать имя виртуальной машины (логин в дисплейном классе), тип операционной системы — Linux, RedHat.

![Имя и тип ОС](IBPictures01/1.3_1.png){#fig:001 width=70%}

Указать размер основной памяти виртуальной машины — 2048МБ (или большее число, кратное 1024 МБ, если позволяют технические характеристики компьютера).

![Объём памяти виртуальной машины](IBPictures01/1.3_2.png){#fig:002 width=70%}

Задать конфигурации жёсткого диска — загрузочный,VDI (BirtualBox Disk Image), динамический виртуальный диск.

![Конфигурация жёсткого диска](IBPictures01/1.3_3.png){#fig:003 width=70%}

Задать размер диска — 40 ГБ (или больше), его расположение — в данном случае /var/tmp/имя_пользователя/имя_пользователя.vdi.

![Имя и размер виртуального жёсткого диска](IBPictures01/1.3_4.png){#fig:004 width=70%}

Выбрав в VirtualBox для виртуальной машины *Настройки > Носители*, добавить новой привод оптических дисков и выбрать образ операционной системы, Rocky-9.0-x86_64-boot.iso.

![Добавление нового привода оптических дисков](IBPictures01/1.3_5.png){#fig:005 width=70%}

Затем запускается виртуальную машину. Необходимо выбрать English в качестве языка интерфейса и перейдите к настройкам установки операционной
системы.

![Выбор языка интерфейса](IBPictures01/1.3_6.png){#fig:006 width=70%}

![Настройки установки операционной системы](IBPictures01/1.3_7.png){#fig:007 width=70%}

Корректируем раскладку клавиатуры (добавился русский язык, но в качестве языка по умолчанию указан английский язык; задана комбинация клавиш для переключения между раскладками клавиатуры —  Alt + Shift ).

![Расклад клавиатуры](IBPictures01/1.3_8.png){#fig:008 width=70%}

В разделе выбора программ указывается в качестве базового окружения Server with GUI, а в качестве дополнения — Development Tools.

![Раздел выбора программ](IBPictures01/1.3_9.png){#fig:009 width=70%}

Отключается KDUMP.

![Отключение KDUMP](IBPictures01/1.3_10.png){#fig:009 width=70%}

Место установки ОС оставляем без изменений. Проверяем сетевое соединение и в качестве имени узла указываем user.localdomain, где вместо user указано имя пользователя в соответствии с соглашением об именовании. 

![Сетевое соединение](IBPictures01/1.3_11.png){#fig:010 width=70%}

Устанавливается пароль для root и пользователя с правами администратора.

![Установка пароля](IBPictures01/1.3_12.png){#fig:011 width=70%}

После завершения установки операционной системы перезапустили виртуальную машину.

Заходим в ОС под заданной при установке учётной записью. В меню *Устройства* виртуальной машины подключаем образ диска дополнений гостевой ОС. После загрузки дополнений нажимаем Enter и перезагружаем виртуальную машину.

**Домашнее задание**

Дождитесь загрузки графического окружения и откройте терминал. В окне терминала проанализируйте последовательность загрузки системы, выполнив команду dmesg. 

![Команда dmesg](IBPictures01/1.4_00.png){#fig:012 width=70%}

Можно просто просмотреть вывод этой команды: ``dmesg | less``

![Команда dmesg | less](IBPictures01/1.4_01.png){#fig:013 width=70%}

Можно использовать поиск с помощью grep: `dmesg | grep -i "то, что ищем"`
Получите следующую информацию.
1. Версия ядра Linux (Linux version).
![Версия ядра Linux](IBPictures01/1.4_1.png){#fig:014 width=70%}

2. Частота процессора (Detected Mhz processor).
![Частота процессора](IBPictures01/1.4_2.png){#fig:015 width=70%}

3. Модель процессора (CPU0).

![Частота процессора](IBPictures01/1.4_3.png){#fig:016 width=70%}

4. Объем доступной оперативной памяти (Memory available).

![Объем доступной оперативной памяти](IBPictures01/1.4_4.png){#fig:017 width=70%}

5. Тип обнаруженного гипервизора (Hypervisor detected).

![Тип обнаруженного гипервизора](IBPictures01/1.4_5.png){#fig:018 width=70%}

6. Тип файловой системы корневого раздела.

![Тип файловой системы корневого раздела](IBPictures01/1.4_6.png){#fig:019 width=70%}

7. Последовательность монтирования файловых систем.

![Последовательность монтирования файловых систем](IBPictures01/1.4_7.png){#fig:020 width=70%}

# Выводы

В ходе выполнения данной лабораторной работы приобрелись практические навыки установки операционной системы на виртуальную машину и были выполнены все задания.

# Контрольные вопросы 
1. Какую информацию содержит учётная запись пользователя?
*Учётная запись пользователя содержит информацию о имени, пароле и доступе/полномочий пользователя*
2. Укажите команды терминала и приведите примеры:
  – для получения справки по команде;
  *help, например ls --help*
  – для перемещения по файловой системе;
  *cd, например cd <имя каталога>*
  – для просмотра содержимого каталога;
  *ls, например ls <имя каталога>*
  – для определения объёма каталога;
  *du <имя каталога>*
  – для создания / удаления каталогов / файлов;
  *mkdir/rm <имя каталога/файла>*
  – для задания определённых прав на файл / каталог;
  *chmod, например chmod u+x <имя каталога/файла>*
  – для просмотра истории команд.
  *history*
3. Что такое файловая система? Приведите примеры с краткой характеристикой.
*Файловая система — правила порядка, определяющие организацию, хранение и именование данных на носителях информации. Например, система «FAT32» логически разделена на три сопредельные области: зарезервированную область для служебных структур, табличную форму указателей и зону записи содержимого файлов. Однако размер отдельных файлов на диске с этой системой не может превышать четыре гигабайта. В отличие от «exFAT», которая также отличается по сниженному числу перезаписей секторов, ответственных за хранение информации, но в остальном похоже на «FAT32».*
4. Как посмотреть, какие файловые системы подмонтированы в ОС?
*Использовать findmnt.*
5. Как удалить зависший процесс?
*Использовать kill. Например, kill <pid_процесса>*

# Библиография

1. [Кулябов Д.С. Лабораторная работа № 1.  Установка и конфигурация операционной системы на виртуальную машину - 14 c.](https://esystem.rudn.ru/pluginfile.php/1651880/mod_folder/content/0/001-lab_virtualbox.pdf?forcedownload=1)