---
## Front matter
title: "Отчёт по лабораторной работе №5" 
subtitle: "Эмуляция и измерение потерь пакетов в глобальных сетях"
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

Основной целью работы является получение навыков проведения интерактивных экспериментов в среде Mininet по исследованию параметров сети, связанных с потерей, дублированием, изменением порядка и поврежденияем пакетов при передачи данных. Эти параметры влияют на производительность протоколов и сетей. 

# Выполнение лабораторной работы

1) Я запустил виртуальную среду с mininet и подключился к основной ос. В виртуальной машине исправил права запуска. Скопировал значение куки своего пользователя для пользователя рут.

![Изменения прав доступа](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/1.png){#fig:001 width=70%} 

2) Задал простейшую топологию, состояющую из двух хостов, коммутатора и контролёра. 

![Простейшая топология](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/2.png){#fig:002 width=70%}

3) На хостах ввёл команду ifconfig, чтобы отобразить информацию об устройствах. 

![Информация об устройствах](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/3.png){#fig:003 width=70%} 

4) Проверил подключение между хостами с помощью команды ping. 

![Пингование](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/4.png){#fig:004 width=70%} 

5) На первом хосте добавил 10% потери пакетов к интерфейсу. 

![Добавление потерь](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/5.png){#fig:005 width=70%}

6) Проверил соединение с добавлением потерь. Видно, что некоторые номера теряются, а процент потерь составил 9%. 

![Пингование с потерей](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/6.png){#fig:006 width=70%}

![Результаты пингования](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/7.png){#fig:007 width=70%}

7) К второму хосту также добавил 10% потери пакетов. 

![Потеря пакетов у второго хоста](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/8.png){#fig:008 width=70%}

8) Проверил соединение между хостами. Теперь процент потери пакетов стал больше, так как процент потери есть и на первом, и на втором хосте. 

![Пингование с задержкой на двух хостах](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/9.png){#fig:009 width=70%} 

![Результат пингования](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/10.png){#fig:010 width=70%} 

9) Восстановил первоначальную конфигурацию на двух хостах.

![Восстановление конфигурации](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/11.png){#fig:011 width=70%} 

10) Убедился, что соединение от хоста не имеет явной потери пакетов. 

![Отсутствие потери](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/12.png){#fig:012 width=70%} 

11) Добавил коэффициент потери пакетов 50%. И каждая последующая вероятность зависит на 50% от последней. 

![Потери пакетов 50%](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/13.png){#fig:013 width=70%} 

12) Проверил, что соединение между хостами имеет потерю пакетов в 50%.

![Пингование с 50%](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/14.png){#fig:014 width=70%} 

13) Добавил на интерфейсах узла 0,01% повреждения пакетов.

![Добавление повреждения пакетов](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/15.png){#fig:015 width=70%}

14) Проверил конфигурацию. 

![Проверка конфигурации](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/16.png){#fig:016 width=70%}

15) Запустил Iperf3 в клиентском режиме.

![Запуск клиента](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/17.png){#fig:017 width=70%} 

16) Восстановил конфигурацию на узлах. Добавил в конфигурацию правило, что 25% пакетов с корреляцией в 50% будут отправляться немедленно, а остальные 75% с задержкой в 10мс. 

![Добавление двойного условия](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/18.png){#fig:018 width=70%}

17) Посмотрел, что новое условие работает как нужно. 

![Пиноование](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/19.png){#fig:019 width=70%}

18) Установил значения по умолчанию. Задал процент дублирования пакетов 50%.

![Установка дублирования](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/20.png){#fig:020 width=70%} 

19) Проверил, что соединение между хостами имеет дублированные пакеты. Затем восстановил конфигурацию.

![Пингование с дублированием](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/21.png){#fig:021 width=70%}

20) Создал каталог, где будет выполняться последующий скрипт. 

![Создание каталога](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/22.png){#fig:022 width=70%}

21) Создал файл, где будет прописан скрипт.

![Создание файла со скриптом](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/23.png){#fig:023 width=70%}

22) Прописал скрипт программы. 

![Создание скрипта](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/24.png){#fig:024 width=70%}

23) Скорректировал скрипт так, чтобы в отдельный файл выводилась информация о потерях пакетов. 

![Корректировка скрипта](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/25.png){#fig:025 width=70%}

24) Создал Makefile для управления процессом проведения эксперимента. 

![Создание Makefile](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/26.png){#fig:026 width=70%} 

25) Выполнил эксперимент. 

![Эксперимент](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/27.png){#fig:027 width=70%}

26) Самостоятельно реализовал воспроизводимые эксперименты по исследованию сети. Эксперимент 1. 

![Скрипт эксперимента 1](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/28.png){#fig:028 width=70%} 

![Результаты эксперимента 1](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/29.png){#fig:029 width=70%} 

27) Провёл эксперимент 2.

![Скрипт эксперимента 2](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/30.png){#fig:030 width=70%} 

![Результаты эксперимента 2](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/31.png){#fig:031 width=70%} 

28) Провёл эксперимент 3. 

![Скрипт эксперимента 3](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/32.png){#fig:032 width=70%}

![Результаты эксперимента 3](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/33.png){#fig:033 width=70%} 

29) Провёл эксперимент 4.

![Скрипт эксперимента 4](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/34.png){#fig:034 width=70%}

![Результаты эксперимента 4](/home/aalushin1/study_2025-2026_simulation-networks/lab5/report/image/35.png){#fig:035 width=70%} 

# Вывод 

Я получил навыки проведения интерактивных экспериментов по исследованию параметров сети, связанных с потерей, дублированием, изменением порядка и повреждениями пакетов при передачи данных. Эти параметры влияют на производительность протоколов и сети. 
