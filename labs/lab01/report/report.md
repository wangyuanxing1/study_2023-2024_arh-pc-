---
## Front matter
title: "Отчёт по лабораторной работе"
subtitle: "Простейший вариант"
author: "Ван Юаньсин"

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

Целью данной лабораторной работы является приобретение практических 

навыков работы с операционной системойLinuxна уровне командной строки 

(организация файловой системы, навигация по файловой системе, создание и 

удаление файлов и директорий).

# Задание

1. Перемещение по файловой системе. 
2. Создание пустых файлови каталогов. 
3. Перемещение и удаление файлов или каталогов. 
4. Команда cat: вывод содержимого файлов. 
5. Выполнение заданий для самостоятельной работы.

# Теоретическое введение

Файловая система определяет способ организации, хранения и именования 

данных на носителях информации в компьютерах и представляет собой 

иерархическую структуру в виде вложенных друг в друга каталогов 

(директорий), содержащих все файлы. В ОС Linuxкаталог, который является 

“вершиной” файловой системы, называется корневым каталогом, 

обозначается символом **/**и содержит все остальные каталоги и файлы. В 

большинстве Linux-систем поддерживается стандарт иерархии файловой 

системы (FilesystemHierarchyStandard, FHS), унифицирующий 

местонахождение файлов и каталогов. Это означает, что в корневом каталоге 

находятся только подкаталоги со стандартными именами и типами данных, 

которые могут попасть в тот или иной каталог. Так, в любой Linux-системе 

всегда есть каталоги /etc, /home, /usr/binи т.п.

| Имя каталога | Описание каталога                                                                                                          |
|--------------|----------------------------------------------------------------------------------------------------------------------------|
| `/`          | Корневая директория, содержащая всю файловую                                                                               |
| `/bin `      | Основные системные утилиты, необходимые как в однопользовательском режиме, так и при обычной работе всем пользователям     |
| `/etc`       | Общесистемные конфигурационные файлы и файлы конфигурации установленных программ                                           |
| `/home`      | Содержит домашние директории пользователей, которые, в свою очередь, содержат персональные настройки и данные пользователя |
| `/media`     | Точки монтирования для сменных носителей                                                                                   |
| `/root`      | Домашняя директория пользователя  `root`                                                                                   |
| `/tmp`       | Временные файлы                                                                                                            |
| `/usr`       | Вторичная иерархия для данных пользователя                                                                                 |

Обратиться к файлу, расположенному в каком-то каталоге, можно указав путь 

к нему. Существует несколько видов путей к файлу: 

• **полный или абсолютный путь**—начинается от корня (/), образуется 

перечислением всех каталогов, разделённых прямым слешем (/), и 

завершается именем файла.

• **относительный путь** —так же как и полный путь, строится перечислением 

через (/) всех каталогов, но начинается от текущего каталога (каталога, в 

котором “находится” пользователь.

Таким образом, в Linuxесли имя объекта начинается с /,то системой это 

интерпретируется как полный путь, в любом другом случае —как 

относительный. В Linuxлюбой пользователь имеет домашний каталог, 

который, как правило, имеет имя пользователя. В домашних каталогах 

хранятся документы и настройки пользователя. Для обозначения домашнего 

каталога используется знак тильды (~). При переходе из домашнего каталога 

знак тильды будет заменён на имя нового текущего каталога.

В операционной системе GNULinuxвзаимодействие пользователя с 

системой обычно осуществляется с помощью командной строки посредством 

построчного ввода команд.

Первые задачи, которые приходится решать в любой системе это —работа с 

данными (обычно хранящимися в файлах) и управление работающими в 

системе программами (процессами). Для получения достаточно подробной 

информации по каждой из команд используйте команду **man**.

**Таблица3.2.**Основныекомандывзаимодействияпользователясфайловойсистемой

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/00.png)

# Выполнение лабораторной работы

**4.1Перемещениепофайловойсистеме**

Открываю терминал и убеждаюсь, что нахожусь в домашнем каталоге.

С помощью команды pwdузнаюполный путь к моему домашнему каталогу.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/01.png)

**рис.4.1.1** Полный путь к домашнему каталогу

Перехожув подкаталог Документы моегодомашнего каталога,указав 

относительный путь.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/02.png)

**рис.4.1.2**перемещение в подкаталог Документы

Перехожув каталог local–подкаталог usrкорневого каталога,указав 

абсолютный путь к нему.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/03.png)

**рис.4.1.3** Перемещение в подкаталог local

Используюкомбинацию cd-для возвращения в последний посещённый

каталоги попадаю в каталог Документы.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/04.png)

**рис.4.1.4**Использование комбинации cd-

Использую комбинациюcd..для перехода на один каталог выше по иерархии

и попадаю в домашний каталог.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/05.png)

**рис.4.1.5**Использование комбинации cd..

Вывожусписок файлов моегодомашнего каталогас помощью команды ls.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/06.png)

**рис.4.1.6**Использование команды ls

Убеждаюсьв том, что список файлов,полученных с помощью команды ls, 

совпадает с файлами, отображающимися в графическом файловом 

менеджере.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/07.png)

**рис.4.1.6**Файлы графического файлового менеджера

Вывожусписок файлов подкаталога Документы моегодомашнего каталога, 

указав относительный путь, и узнаю, что список пуст.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/08.png)

**рис.4.1.7**Список файлов подкаталога Документы

Вывожусписок файлов каталога /usr/local, указав абсолютный путь к нему.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/09.png)

**рис.4.1.7**Список файлов каталога/usr/local

**4.2Созданиепустыхфайловикаталогов**

Создаюв домашнем каталоге подкаталог с именем parentdirс помощью 

команды mkdir.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/10.png)

**рис.4.2.1** Создание подкаталога

С помощью командыlsпроверяю, что каталог создан. 

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/11.png)

**рис.4.2.2**Проверка наличия каталога с помощью команды ls

Создаюподкаталог dirв каталогеparentdir, затем перемещаюсь в каталог 

parentdirи,задав несколько аргументов команде mkdir,создаю каталоги dir1, 

dir2иdir3.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/12.png)

**рис.4.2.3**Создание нескольких подкаталогов 

Создаюподкаталог newdirв домашнем каталоге, указав путь в явном виде, т.к 

нахожусьсейчас в каталоге parentdir.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/13.png)

**рис.4.2.4**Созданиеподкаталога из другого каталога

Проверяюналичиекаталогаnewdirв домашнем каталоге с помощью команды

ls~.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/14.png)

**рис.4.2.5**Проверка наличия каталога в домашнем каталогe

Создаюиерархическую цепочку подкаталоговnewdir/dir1/dir2в домашнем 

каталогес помощью опции -p.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/15.png)

**рис.4.2.6**Созданиеиерархической цепочки подкаталогов

Создаюфайл test.txtв каталоге ~/newdir/dir1/dir2с помощью команды touchи

Проверяюналичие файла с помощью команды.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/16.png)

**рис.4.2.7**Созданиефайла с использованием команды touch

**4.3Перемещениеиудалениефайловили каталогов**

Запросив подтверждение на удаление каждого файла в текущем каталогес 

помощью команды rmи опции -i, удаляюв подкаталоге /newdir/dir1/dir2/ все 

файлы с именами, заканчивающимися на .txt, и проверяю, выполнилась ли 

команда.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/17.png)

**рис.4.3.1**Удаление файлов с подтверждением

Рекурсивно удаляюиз текущего каталога без запроса подтверждения на 

удаление каталог newdir, а также файлы, чьи имена начинаются с dirв 

каталоге parentdir, затем проверяю, что команда выполнилась.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/18.png)

**рис.4.3.2**Рекурсивное удалениекаталога и файлов

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/19.png)

**рис.4.3.3**Проверка выполнения команды

Создаюкаталогиparentdir1/dir1, parentdir2/dir2иparentdir3ифайлыtest1.txtи 

text2.txtсоответственнов домашнем каталоге.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/20.png)

**рис.4.3.4**Создание каталогов и файлов в домашнем каталоге 10

Используя команды cpи mv,перемещаюфайл test1.txtи копируюфайл

test2.txtв каталог parentdir3.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/21.png)

**рис.4.3.5**Копирование и перемещение файлов

С помощью команды lsпроверяюкорректность выполненных команд.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/22.png)

**рис.4.3.6**Проверка правильности выполнения команд

Переименовываюфайл test1.txtиз каталога parentdir3 в newtest.txt,

запрашивая подтверждение перед перезаписью, а файл test2.txtкопируюпод 

именем subtest2.txt.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/23.png)

**рис.4.3.7**Переименовывание файлов

Переименовываюкаталог dir1 в каталоге parentdir1 в newdir.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/24.png)

**рис.4.3.8**Переименовываниекаталога

**4.4Командаcat:выводсодержимого файлов**

Используем команду catдля объединенияфайловподкаталога /etc/hostsи 

выводаих на стандартный вывод.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/25.png)

**рис.4.4.1**Использование команды cat

**4.5Выполнениезаданийдля самостоятельнойработы**

**1.**Воспользовавшись командой pwd, узнаюполный путь к своей домашней 

директории.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/26.png)

**рис.4.5.1**Команда pwd

2.Ввожу последовательность данных мне команд

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/27.png)

**рис.4.5.2**Последовательность данных команд

Я возвращаюсь в домашний каталог и создаю подкаталог tmp.Перейдя в 

данный подкаталог,я отслеживаю его абсолютный путь. Когда я задаю

команду cd/tmp,созданный мною подкаталог становиться подкаталогом 

корневого каталога, а эта директория есть в системе по умолчанию и путь к н

ей отличен от созданной мной директории, поэтому при использованииpwd я

 перехожу в другой каталог tmp,о чем и пишет нам система, выводя на 

консоль/tmp.

3.Пользуясь командами cdи ls, рассматриваюфайлыкорневого каталога, 

домашнего каталога, каталогов /etcи /usr/local.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/28.png)

**рис.4.5.3**Файлы корневого каталога

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/29.png)

**рис.4.5.4**Файлы домашнегокаталога

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/30.png)

**рис.4.5.5**Файлы каталога/usr/local

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/31.png)

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/32.png)

**рис.4.5.6/7**Файлы каталога/etc

4.Cоздаюкаталог tempи каталог labsс подкаталогами lab1,lab2 и lab3 одной 

командой. В каталоге tempсоздаюфайлы text1.txt,text2.txt,text3.txt. 

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/33.png)

**рис.4.5.8**Создание каталогов и файлов

Пользуясь командой ls, убеждаюсь, что каталоги и файлы созданы.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/34.png)

**рис.4.5.9**Проверка правильности выполнения команд

5.Cпомощью текстового редактора записываюв файл text1.txtсвое имя, в 

файл text2.txtсвоюфамилию, в файл text3.txtсвою учебную группу. 

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/35.png)

**рис.4.5.10**Запись имени в текстовый файл

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/36.png)

**рис.4.5.11**Запись фамилиив текстовый файл

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/37.png)

**рис.4.5.12**Запись учебной группыв текстовый файл

Вывожуна экран содержимое файлов, используя команду cat

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/38.png)

**рис.4.5.13**Использование команды cat

6.Копируювсе файлы, чьи имена заканчиваются на .txt, из каталога ~/tempв 

каталог labs. Переименовываюфайлы каталога labsи перемещаюих.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/39.png)

**рис.4.5.14**Копирование файлов

Переименовываюфайлы каталога labsи перемещаюих.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/40.png)

**рис.4.5.15**Переименовывание и перемещение файлов

Убеждаюсь, что работа выполнена верно.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/41.png)

**рис.4.5.16**Проверка правильности выполнения команд

7.С помощью команды lsнахожу все созданные в ходе выполнения 

лабораторной работы файлы и каталогииудаляюих с помощью команды rm 

и опции рекурсивного удаления -R.

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab01/presentation/image/42.png)

**рис.4.5.17**Рекурсивное удаление файлов и каталогов

# Выводы

Благодаряданнойлабораторнойработеяосвоилабазовыенавыкиработыс

команднойстрокойоперационнойсистемыLinux, такиекакорганизация 

файловой системы, навигация по файловой системе, создание и удаление ф

айлов и директорий,научилась многим другим основным понятиям. 

Данные навыки сильно помогут мне в дальнейшей работе с данной 

операционной системой.

# Список литературы{.unnumbered}

1. GDB: The GNU Project Debugger. —URL: https://www.gnu.org/software/gdb/. 
2. GNU Bash Manual. —2016. —URL: https://www.gnu.org/software/bash/manual/. 
3. Midnight Commander Development Center. —2021. —URL: https://midnight-commander. 

org/. 

4. NASMAssembly Language Tutorials. —2021. —URL: https://asmtutor.com/. 
5. Newham C.Learning the bash Shell: Unix Shell Programming. —O’Reilly Media, 2005. —

354 с. —(In a Nutshell). —ISBN 0596009658. —URL: 

http://www.amazon.com/Learningbash-Shell-Programming-Nutshell/dp/0596009658. 

6. RobbinsA. Bash Pocket Reference. —O’Reilly Media, 2016. —156 с. —ISBN 978-
7. 
8. The NASM documentation. —2021. —URL: https://www.nasm.us/docs.php. 
9. Zarrelli G. Mastering Bash. —Packt Publishing, 2017. —502 с. —ISBN 9781784396879. 
10. Колдаев В. Д., Лупин С. А. Архитектура ЭВМ. —М. : Форум, 2018. 
11. Куляс О. Л., Никитин К. А. Курс программирования на ASSEMBLER. —М. : Солон-

Пресс, 2017. 

11. Новожилов О. П. Архитектура ЭВМ и систем. —М. : Юрайт, 2016. 
12. Расширенный ассемблер: NASM. —2021. —URL: 

https://www.opennet.ru/docs/RUS/nasm/. 

13. Робачевский А., Немнюгин С., Стесик О. Операционная система UNIX. —2-е изд. —

БХВПетербург, 2010. —656 с. —ISBN978-5-94157-538-1. 

14. Столяров А. Программирование на языке ассемблера NASMдля ОС Unix. —2-е изд. 

—М. : МАКС Пресс, 2011. —URL: http://www.stolyarov.info/books/asm_unix. 

15. Таненбаум Э. Архитектура компьютера. —6-е изд. —СПб. : Питер, 2013. —874 с. —

(Классика ComputerScience). 

16. Таненбаум Э., Бос Х. Современные операционные системы. —4-е изд. —СПб. : 

Питер, 2015. —1120 с.—(Классика ComputerScience).
