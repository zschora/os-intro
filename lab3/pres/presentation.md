---
## Front matter
lang: ru-RU
title: Создание отчета в Markdown
author: |
	Шалыгин Георгий Эдуардович
institute: |
	РУДН, Москва
date: 2021

## Formatting
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true

---

# Me

Шалыгин Георгий Эдуардович, РУДН, 1 курс, НФИбд-02-20

# Markdown

Чтобы создать заголовок, используйте знак (#)

Чтобы задать для текста полужирное начертание, заключите его в двойные звездочки: This text is \**bold**

Чтобы задать для текста курсивное начертание, заключите его в одинарные звездочки: This text is \*italic*.

Чтобы задать для текста полужирное и курсивное начертание, заключите его в тройные звездочки: This is text is both \*\*\*bold and italic***.

Блоки цитирования создаются с помощью символа >:

Неупорядоченный (маркированный) список можно отформатировать с помощью звездочек или тире.

Чтобы вложить один список в другой, добавьте отступ для элементов дочернего списка.

# Результаты

Был создан следующий отчет:

![Отчет](D:\рудн\works\2020-2021\Операционные системы\laboratory\lab3\pres\image\1.png){ #fig:001 width=70% }

Его можно импортировать как pdf или docx:

![импорт](D:\рудн\works\2020-2021\Операционные системы\laboratory\lab3\pres\image\2.png){ #fig:001 width=70% }

# Вывод

В процессе лабораторной работы были созданы отчет и презентация с помощь языка разметки Markdown.