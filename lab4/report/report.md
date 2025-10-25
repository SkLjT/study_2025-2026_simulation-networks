---
## Front matter
title: "Отчёт по лабораторной работе №4" 
subtitle: "Эмуляция и измерение задержек в глобальных сетях"
author: "Лушин Артём Андреевич"

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
biblatex: false
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
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Основной целью работы является знакомство с NETEM - инструментов для тестирования производительности приложений в визуальной сети, а также получение навыков проведения интерактивного и воспроизводимого экспериментов по измерению задержки и её дрожания в моделируемой сети в среде Mininet. 

# Выполнение лабораторной работы

1) Я запустил виртуальную среду с mininet и подключился к основной ос. В виртуальной машине исправил права запуска. Скопировал значение куки своего пользователя для пользователя рут.

![Права запуска](/home/aalushin1/study_2025-2026_/lab4/report/image/1.png){#fig:001 width=70%} 

2) Задал простейшую топологию, состоящую из двух хостов, коммутатора и контроллёра. 

![Простейшая топология](/home/aalushin1/study_2025-2026_/lab4/report/image/2.png){#fig:002 width=70%} 

3) На хостах ввёл команду, что определения IP. 

![Адреса хостов](/home/aalushin1/study_2025-2026_/lab4/report/image/3.png){#fig:003 width=70%} 

4) Проверил подключение между хостами с помощью команды пинг. Минимальная задержка - 0,034. Среднее - 2,11. Максимальная 7,72.\

![Проверка подключений](/home/aalushin1/study_2025-2026_/lab4/report/image/4.png){#fig:004 width=70%}

5) На хосте 1 добавил задержку 100мс. 

![Задержка на хосте 1](/home/aalushin1/study_2025-2026_/lab4/report/image/5.png){#fig:005 width=70%}

6) Проверил соединение от хоста 1 к хосту 2. Минимальная задержка - 101. Средняя - 102. Максимальная - 103.

![Соединение от хоста 1](/home/aalushin1/study_2025-2026_/lab4/report/image/6.png){#fig:006 width=70%}

7) На хосте 2 добавил такую же задержку 100 мс. 

![Задержка на хосте 2](/home/aalushin1/study_2025-2026_/lab4/report/image/7.png){#fig:007 width=70%}

8) Проверил соединение. Теперь минимальная задержка - 201. Средняя - 202,4. Максимальная - 204. 

![Проверка соединений между хостами](/home/aalushin1/study_2025-2026_/lab4/report/image/8.png){#fig:008 width=70%}

9) Изменил задержку на двух хостах до 50 мс. 

![Понижение задержка на хостах](/home/aalushin1/study_2025-2026_/lab4/report/image/9.png){#fig:009 width=70%}

10) Проверил соединение от первого хоста, ко второму. Теперь минимальная задержка составила 101. Средняя 102.3. Максимальная - 104. 

![Соединение между хостами](/home/aalushin1/study_2025-2026_/lab4/report/image/10.png){#fig:010 width=70%}

11) Восстановил конфигурацию, удалив все правила. 

![Восстановление конфигурации на компах](/home/aalushin1/study_2025-2026_/lab4/report/image/11.png){#fig:011 width=70%}

12) Проверил соединение между хостами. Искусственная задержка теперь отсутствует. 

![Проверка без задержке](/home/aalushin1/study_2025-2026_/lab4/report/image/12.png){#fig:012 width=70%}

13) Добавил задержку на первый хост 100мс с отклонением в 10.

![Задержка с отклонением](/home/aalushin1/study_2025-2026_/lab4/report/image/13.png){#fig:013 width=70%}

14) Проверил соединение между хостами. Теперь минимальная задержка - 100. Максимальная - 110.

![Проверка соединений с отклонением](/home/aalushin1/study_2025-2026_/lab4/report/image/14.png){#fig:014 width=70%}

15) Восстановил конфигурацию по умолчанию.

![Восстановление конфигурации](/home/aalushin1/study_2025-2026_/lab4/report/image/15.png){#fig:015 width=70%}

16) Добавил к конфигурации задержку в 100мс с отклонением в 10мс. А так же значение корреляции 25%.

![Добавление корреляции](/home/aalushin1/study_2025-2026_/lab4/report/image/16.png){#fig:016 width=70%}

17) Убедился, что пакеты имеют задержку в 100 мс с отклонением в 10 и корреляцией. 

![Отправка пакетов с корреляцией](/home/aalushin1/study_2025-2026_/lab4/report/image/17.png){#fig:017 width=70%}

18) Указал нормальное распределение задержки на хосте 1.

![Нормальное распределение на хосте](/home/aalushin1/study_2025-2026_/lab4/report/image/18.png){#fig:018 width=70%}

19) Проверил подключение с нормальным распределением задержки.

![Пингование с нормальным распределением](/home/aalushin1/study_2025-2026_/lab4/report/image/19.png){#fig:019 width=70%}

20) Обновил репозиторий программного обеспечения на виртуальной машине. 

![Обновление репозитория](/home/aalushin1/study_2025-2026_/lab4/report/image/20.png){#fig:020 width=70%}

21) Установил пакеты geeqie. 

![Установка geeqie](/home/aalushin1/study_2025-2026_/lab4/report/image/21.png){#fig:021 width=70%}

22) Создал каталог где буду выполнять лабораторную.

![Создание каталога](/home/aalushin1/study_2025-2026_/lab4/report/image/22.png){#fig:022 width=70%}

23) Создал файл lab_netem_i.py. Вписал туда скрипт для эксперимента.

![Скрипт lab_netem_i](/home/aalushin1/study_2025-2026_/lab4/report/image/23.png){#fig:023 width=70%}

24) Создал скрипт для визуализации ping_plot. Этот скрипт будет визуализировать результаты эксперимента.

![Скрипт для визуализации](/home/aalushin1/study_2025-2026_/lab4/report/image/24.png){#fig:024 width=70%}

25) Задал права доступа к файлам скрипта.

![Права доступа](/home/aalushin1/study_2025-2026_/lab4/report/image/25.png){#fig:025 width=70%}

26) Создал Makefile для управления процессом проведения эксперимента. 

![Makefile](/home/aalushin1/study_2025-2026_/lab4/report/image/26.png){#fig:026 width=70%}

27) Запустил эксперимент. 

![Запуск эксперимента](/home/aalushin1/study_2025-2026_/lab4/report/image/27.png){#fig:027 width=70%}

28) Посмотрел какой график построил наш скрипт.

![График после первого эксперимента](/home/aalushin1/study_2025-2026_/lab4/report/image/28.png){#fig:028 width=70%}

29) Из файла ping.dat удалил первую строку и заново построил график. График изменился. 

![Удаление данных из файла](/home/aalushin1/study_2025-2026_/lab4/report/image/29.png){#fig:029 width=70%}

![Построение нового графика](/home/aalushin1/study_2025-2026_/lab4/report/image/30.png){#fig:030 width=70%}

30) Разработал собственный скрипт для вычисление. Добавил правило в файл Makefile. Запустил скрипт и зачем очистил выполненную работу. 

![Собственный скрипт](/home/aalushin1/study_2025-2026_/lab4/report/image/31.png){#fig:031 width=70%}

![Изменение Makefile](/home/aalushin1/study_2025-2026_/lab4/report/image/32.png){#fig:032 width=70%}

![Демонстрация результата](/home/aalushin1/study_2025-2026_/lab4/report/image/33.png){#fig:033 width=70%}

31) Реализовал воспроизводимые эксперименты по изменению задержек. Построил график для каждого нового эксперимента. 

![Изменение задержек](/home/aalushin1/study_2025-2026_/lab4/report/image/34.png){#fig:034 width=70%}

![График к новому скрипту](/home/aalushin1/study_2025-2026_/lab4/report/image/35.png){#fig:035 width=70%}

![Результаты скрипта](/home/aalushin1/study_2025-2026_/lab4/report/image/36.png){#fig:036 width=70%}

32) Изменил задержку и добавил отклонение. 

![Добавление отклонения](/home/aalushin1/study_2025-2026_/lab4/report/image/37.png){#fig:037 width=70%}

![Построение графика](/home/aalushin1/study_2025-2026_/lab4/report/image/38.png){#fig:038 width=70%}

![Результаты с отклонением](/home/aalushin1/study_2025-2026_/lab4/report/image/39.png){#fig:039 width=70%}

33) Добавил корреляцию и провёл новый эксперимент.

![Эксперимент с корреляцией](/home/aalushin1/study_2025-2026_/lab4/report/image/40.png){#fig:040 width=70%}

![График с корреляцией](/home/aalushin1/study_2025-2026_/lab4/report/image/41.png){#fig:041 width=70%}

![Результаты работы с корреляцией](/home/aalushin1/study_2025-2026_/lab4/report/image/42.png){#fig:042 width=70%}

34) Изменил эксперимент, чтобы было нормальное распределение. Провёл те же эксперименты и посмотрел на график.

![Эксперимент с нормальным распределением](/home/aalushin1/study_2025-2026_/lab4/report/image/43.png){#fig:043 width=70%}

![График с нормальным распределением](/home/aalushin1/study_2025-2026_/lab4/report/image/44.png){#fig:044 width=70%}

![Результат работы с нормальным распределением](/home/aalushin1/study_2025-2026_/lab4/report/image/45.png){#fig:045 width=70%}

# Вывод 

Я познакомился с NETEM - инструментом для тестирования производительности приложений в визуальной сети, а также получил навыки проведения интерактивных и воспроизводимых экспериментов по измерению задержки и её дрожанию в моделируемой сети. 
