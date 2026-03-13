---
## Front matter
title: "Отчёт по лабораторной работе №3"
subtitle: "Математические основы защиты информации и информационной безопасности"
author: "Ли Хан"

## Generic otions
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true
toc-depth: 2
lof: true
lot: true
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
mainfont: IBM Plex Serif
romanfont: IBM Plex Serif
sansfont: IBM Plex Sans
monofont: IBM Plex Mono
mathfont: STIX Two Math
mainfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
romanfontoptions: Ligatures=Common,Ligatures=TeX,Scale=0.94
sansfontoptions: Ligatures=Common,Ligatures=TeX,Scale=MatchLowercase,Scale=0.94
monofontoptions: Scale=MatchLowercase,Scale=0.94,FakeStretch=0.9
mathfontoptions:
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
  - \usepackage{float}
  - \floatplacement{figure}{H}
---

# Цель работы

Изучить математическую логику шифрования гаммированием с использованием базы индексации $А=1$. Через детальный пошаговый вывод освоить процесс объединения индексов открытого текста и гаммы при операциях по модулю 33, а также проверить точность реализации алгоритма.

# Анализ выполненного упражнения

## Анализ принципа реализации алгоритма

Шифрование гаммированием — это метод симметричного шифрования, суть которого заключается в наложении последовательности «гаммы» на символы открытого текста.

- Процесс оцифровки: Каждой букве алфавита присваивается порядковый номер (например, А=1, Б=2 ... Я=33).

- Логика шифрования: Порядковый номер символа текста $p_i$ складывается с номером символа гаммы $k_i$. Результат вычисляется по модулю $N$ (размер алфавита): $c_i = (p_i + k_i) \pmod N$.

- Логика дешифрования: Благодаря свойствам модульной арифметики, обратный процесс выполняется по формуле: $p_i = (c_i - k_i + N) \pmod N$.

## принципа реализации алгоритма компилятора

![принципа реализации алгоритма компилятора](image/01.png)

## результат

![принципа реализации алгоритма результат](image/02.png)

# Вывод

В ходе выполнения работы была успешно реализована система шифрования с использованием конечной гаммы. Эксперимент подтвердил, что стойкость данного метода напрямую зависит от длины и характеристик гаммы. При наличии ключа симметричность модульных операций позволяет полностью восстановить исходное сообщение без потерь.

