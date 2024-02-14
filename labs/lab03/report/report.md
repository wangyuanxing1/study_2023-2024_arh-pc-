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

Целью работы является освоение процедуры оформления отчетов с помощью

легковесного языка разметки Markdown.

# Задание

1. Обновление локального репозитория.
2. Создание отчетов в формате .pdf и .docx.
3. Заполнения отчета по лабораторной работе.
4. Задание для самостоятельной работы.

# Теоретическое введение

Markdown - легковесный язык разметки, созданный с целью обозначения фор-

матирования в простом тексте, с максимальным сохранением его читаемости

человеком, и пригодный для машинного преобразования в языки для продви-

нутых публикаций. Чтобы создать заголовок, используйте знак #. Чтобы задать

для текста полужирное начертание, заключите его в двойные звездочки. Чтобы

задать для текста курсивное начертание, заключите его в одинарные звездоч-

ки. Чтобы задать для текста полужирное и курсивное начертание, заключите

его в тройные звездочки. Блоки цитирования создаются с помощью символа >.

Синтаксис Markdown для встроенной ссылки состоит из части [link text], пред-

ставляющей текст гиперссылки, и части (file-name.md) – URL-адреса или имени

файла, на который дается ссылка. Markdown поддерживает как встраивание фраг-

ментов кода в предложение, так и их размещение между предложениями в виде

отдельных огражденных блоков. Огражденные блоки кода — это простой способ

выделить синтаксис для фрагментов кода.

# Выполнение лабораторной работы

**4.1 Обновление локального репозитория**

Открываю терминал, перехожу в каталог курса, сформированный при выпол-

нении лабораторной работы №2 и обновляю локальный репозиторий, скачав

изменения из удаленного репозитория с помощью команды git pull.![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab03/report/image/01.png)) (рис. 4.10).

**4.2 Создание отчетов в формате .pdf и .docx**

Перехожу в каталог с шаблоном отчета по лабораторной работе №3 и про-

вожу компиляцию шаблона с использованием Makefile:ввожу команду make и

генерирую файлы report.pdf и report.docx. ![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab03/report/image/02.png))(рис. 4.10)

Рис. 4.2: Создание файлов с помощью команды make

Открываю файловый менеджер и проверяю корректность полученных файлов.

(рис. 4.10).

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab03/report/image/03.png))

Рис. 4.3: Проверка создания отчетов

Удалите полученный файлы с помощью команды make clean. (рис. 4.10).

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab03/report/image/04.png))

Рис. 4.4: Удаление файлов с помощью команды make clean

Проверяю, что файлы report.pdf и report.docx действительно были удалены.

(рис. 4.10).

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab03/report/image/05.png)

Рис. 4.5: Проверка удаления файлов

**4.3 Заполненияотчетаполабораторнойработе**

Спомощьютекстовогоредактораоткрываюфайлreport.mdивнимательно

изучаюегоструктуру,заполняюотчет.(рис.4.10).

![](https://github.com/wangyuanxing1/study_2023-2024_arh-pc-/blob/master/labs/lab03/report/image/06.png)



# Выводы

Благодаряданнойлабораторнойработеяосвоилапроцедурыоформления

отчетоввMarkdown,которыепомогутмнепривыполнениипоследующихлабо-

раторныхработ.

# Список литературы{.unnumbered}

1.GDB:TheGNUProjectDebugger.—URL:https://www.gnu.org/software/gdb/.

2.GNUBashManual.—2016.—URL:https://www.gnu.org/software/bash/manual/.

3.MidnightCommanderDevelopmentCenter.—2021.—URL:https://midnight-commander.org/.

4.NASMAssemblyLanguageTutorials.—2021.—URL:https://asmtutor.com/.

5.NewhamC.LearningthebashShell:UnixShellProgramming.—O’ReillyMedia,2005.—354с.—(InaNutshell).—ISBN0596009658.—URL:

http://www.amazon.com/Learningbash-Shell-Programming-Nutshell/dp/0596009658.

6.RobbinsA.BashPocketReference.—O’ReillyMedia,2016.—156с.—ISBN978-1491941591.
