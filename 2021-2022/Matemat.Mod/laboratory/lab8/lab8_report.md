---
# Front matter
title: "Лабораторная работа 8. Модель конкуренции двух фирм"
subtitle: "Вариант 30"
author: "Асеинова Елизавета Валерьевна"

# Generic otions
lang: ru-RU
toc-title: "Содержание"

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

В данной работе мы должны изучить модель конкуренции двух фирм и построить соответствующие графики в OpenModelica.

# Задание

## Случай 1
Рассмотрим две фирмы, производящие взаимозаменяемые товары одинакового качества и находящиеся в одной рыночной нише. Считаем, что в рамках нашей модели конкурентная борьба ведётся только рыночными методами. То есть, конкуренты могут влиять на противника путем изменения параметров своего производства: себестоимость, время цикла, но не могут прямо вмешиваться в
ситуацию на рынке («назначать» цену или влиять на потребителей каким-либо иным способом.) Будем считать, что постоянные издержки пренебрежимо малы, и в модели учитывать не будем.

В этом случае динамика изменения объемов продаж
фирмы 1 и фирмы 2 описывается следующей системой уравнений:

$$\frac{dM_1}{d\theta} = M_1 - \frac{b}{c_1}M_1M_2- \frac{a_1}{c_1}M_1^2$$
$$\frac{dM_2}{d\theta} = \frac{c_2}{c_1}M_2- \frac{b}{c_1}M_1M_2 - \frac{a_2}{c_1}M_2^2$$

где

$$a_1 = \frac{p_{cr}}{\tau_1^2 p_1^2Nq},a_2 = \frac{p_{cr}}{\tau_2^2 p_2^2Nq}, b = \frac{p_{cr}}{\tau_1^2p_1^2\tau_2^2p^2_2Nq}$$

$$c_1 = \frac{p_{cr}-p_1}{\tau_1p_1}, c_2 = \frac{p_{cr}-p_2}{\tau_2p_2}$$

## Случай 2
Рассмотрим модель, когда, помимо экономического фактора
влияния (изменение себестоимости, производственного цикла, использованиекредита и т.п.), используются еще и социально-психологические факторы –формирование общественного предпочтения одного товара другому, не зависимо от
их качества и цены. В этом случае взаимодействие двух фирм будет зависеть друг от друга, соответственно коэффициент перед
M1M2 будет отличаться.

Пусть в рамках рассматриваемой модели динамика изменения объемов продаж фирмы 1 и фирмы 2 описывается следующей системой уравнений:

$$\frac{dM_1}{d\theta} = M_1 - (\frac{b}{c_1} + 0,0002)M_1M_2- \frac{a_1}{c_1}M_1^2$$
$$\frac{dM_2}{d\theta} = \frac{c_2}{c_1}M_2- \frac{b}{c_1}M_1M_2 - \frac{a_2}{c_1}M_2^2$$

Для обоих случаев рассмотрим задачу со следующими начальными условиями и параметрами:
$$M_0^1 = 8.8, M_0^2 = 9.9$$
$$p_{cr} = 30, N = 80, q = 1$$
$$\tau_1 = 25, \tau_2 = 20$$
$$p_1 = 10.1, p_2 = 11.5$$

1. Постройте графики изменения оборотных средств фирмы 1 и фирмы 2 без учета постоянных издержек и с веденной нормировкой для случая 1.

2. Постройте графики изменения оборотных средств фирмы 1 и фирмы 2 без учета постоянных издержек и с веденной нормировкой для случая 2


# Теоретическое введение
Рассмотрим две фирмы, производящие взаимозаменяемые товары одинакового качества и находящиеся в одной рыночной нише. Последнее означает, что у потребителей в этой нише нет априорных предпочтений, и они приобретут тот или иной товар, не обращая внимания на знак фирмы. В 1м случае, на рынке устанавливается единая цена, которая определяется балансом суммарного предложения и спроса. Иными словами, в рамках нашей модели конкурентная борьба ведётся только рыночными методами. То есть, конкуренты могут влиять на противника путем изменения параметров своего производства: себестоимость, время цикла, но не могут прямо вмешиваться в ситуацию на рынке («назначать» цену или влиять на потребителей каким- либо иным способом.)

$$\frac{dM_1}{d\theta} = M_1 - \frac{b}{c_1}M_1M_2- \frac{a_1}{c_1}M_1^2$$
$$\frac{dM_2}{d\theta} = \frac{c_2}{c_1}M_2- \frac{b}{c_1}M_1M_2 - \frac{a_2}{c_1}M_2^2$$

где $\theta = \frac{t}{c_1}$.

Во 2-м случае помимо экономического фактора влияния (изменение себестоимости, производственного цикла, использование кредита и т.п.), используются еще и социально-психологические факторы – формирование общественного предпочтения одного товара другому, не зависимо от их качества и цены. В этом случае взаимодействие двух фирм будет зависеть друг от друга, соответственно коэффициент перед M_1M_2 будет отличаться. Тогда имеем

$$\frac{dM_1}{d\theta} = M_1 - (\frac{b}{c_1}+K)M_1M_2- \frac{a_1}{c_1}M_1^2$$
$$\frac{dM_2}{d\theta} = \frac{c_2}{c_1}M_2- (\frac{b}{c_1}+L)M_1M_2 - \frac{a_2}{c_1}M_2^2$$

где $\theta = \frac{t}{c_1}$ и $K$, $L$ - соответствующие коэффициенты социально-психологического фактора.[^1]

Для 2х случаев соответствующие коэффициенты:

$$a_1 = \frac{p_{cr}}{\tau_1^2 p_1^2Nq}, \ a_2 = \frac{p_{cr}}{\tau_2^2 p_2^2Nq}, \ b = \frac{p_{cr}}{\tau_1^2p_1^2\tau_2^2p^2_2Nq} \ c_1 = \frac{p_{cr}-p_1}{\tau_1p_1}, c_2 = \frac{p_{cr}-p_2}{\tau_2p_2} $$

Общие обозначения:

$N$ - число потребителей производимого продукта.

$\tau$ - длительность производственного цикла.

$p_{cr}$ - рыночная цена товара.

$p$ - себестоимость продукта, то есть переменные издержки на производство единицы продукции.

$q$ - максимальная потребность одного человека в продукте в единицу времени.

$\theta = \frac{t}{c_1}$ - безразмерное время.


# Выполнение лабораторной работы

1. Задаем начальные параметры(риc.[-@fig:001])

![Начальные условия](screens/1.png){#fig:001 width=70%}

2. Задаем коэффициенты(риc.[-@fig:002])

![Коэффициенты](screens/2.png){#fig:002 width=70%}

3. Определяем M1 и М2(риc.[-@fig:003])

![М1 и М2](screens/3.png){#fig:003 width=70%}

4. Прописываем уравнения для 1 и 2 случая(риc.[-@fig:004])

![Уравнения](screens/4.png){#fig:004 width=70%}

5. Получаем график для 1 случая(риc.[-@fig:005])

![График 1](screens/5.png){#fig:005 width=70%}

6. Получаем график для 2 случая(риc.[-@fig:006])

![График 2](screens/6.png){#fig:006 width=70%}

# Выводы 

В данной лабораторной работе мы изучили модель конкуренции двух фирм и построили графики для 2-х разных случаев.

# Список литературы

1. Кулябов, Д.С. Модель конкуренции двух фирм [Текст] / Д.С.Кулябов. - Москва: - 7 с.

[^1]: Кулябов, Д.С. Модель конкуренции двух фирм.