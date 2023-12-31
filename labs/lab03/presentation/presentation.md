---
## Front matter
lang: ru-RU
title: Лабораторная работа №3
subtitle: Анализ трафика в Wireshark
author:
  - Демидова Екатерина Алексеевна
institute:
  - Российский университет дружбы народов
date: 23 сентября 2023

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
---
# Вводная часть

## Цель работы

Изучение посредством Wireshark кадров Ethernet, анализ PDU протоколов транспортного и прикладного уровней стека TCP/IP.

## Задание

1. MAC-адресация
   1. Изучение возможностей команды ipconfig для ОС типа Windows (ifconfig для систем типа Linux).
   2. Определение MAC-адреса устройства и его типа.
2. Анализ кадров канального уровня в Wireshark
   1. Установить на домашнем устройстве Wireshark.
   2. С помощью Wireshark захватить и проанализировать пакеты ARP и ICMP в части кадров канального уровня
3. Анализ протоколов транспортного уровня в Wireshark. С помощью Wireshark захватить и проанализировать пакеты HTTP, DNS в части заголовков и информации протоколов TCP, UDP, QUIC.
4. Анализ handshake протокола TCP в Wireshark.С помощью Wireshark проанализировать handshake протокола TCP.

# Выполнение лабораторной работы

# MAC-адресация

## MAC-адресация

С помощью команды `ifconfig` выведем информацию о текущем сетевом соединении.

![Вывод команды `ifconfig`](image/1.png){#fig:001 width=70%}

## MAC-адресация

Так же добавив название сетевого интерфейса можно вывести информацию только о нём.

![Вывод информации о конкретном сетевом интерфейсе`](image/2.png){#fig:002 width=70%}

## MAC-адресация

Теперь выключим сетевой интерфейс добавив команду `down`(с помощью команды`up` его можно включить).

![Выключение сетевого интерфейса и демонстрация опции `-a`](image/3.png){#fig:003 width=65%}

## MAC-адресация

Также можно использовать опцию `-s`, с помощью которой выводится краткий список интерфейсов. 

![Использование опции `-s`](image/4.png){#fig:004 width=70%}

## MAC-адресация

![Демонстрация MAC-адреса](image/5.png){#fig:005 width=70%}

## MAC-адресация

Первые три байта e8:f4:08 в этом адресе соответствуют индентификатору производителя. Последние три байта c4:e3:ca индентифицируют сетевой интерфейс. 

![Демонстрация производителя сетевого оборудования](image/6.png){#fig:006 width=40%}

## MAC-адресация

Возьмем первый байт e8 и переведём его в двоичную систему. Получим 11101000. Так как последний бит ноль, то адрес является индивидуальным. А так как предпоследний бит ноль, то адрес глобально администрируемый.

# Анализ кадров канального уровня в Wireshark

Запустим wireshark и начнем захват трафика.

![Захват трафика в wireshark](image/9.png){#fig:007 width=50%}

## Анализ кадров канального уровня в Wireshark

![Определение IP-адреса устройства и шлюза по умолчанию](image/7.png){#fig:008 width=60%}

## Анализ кадров канального уровня в Wireshark

С помощью команды `ping 192.168.1.1` пропингуем шлюз по умолчанию. 

![Пингование шлюза по умолчанию](image/8.png){#fig:009 width=70%}

## Анализ кадров канального уровня в Wireshark

![Кадр ICMP - эхо-запрос](image/10.png){#fig:010 width=70%}

## Анализ кадров канального уровня в Wireshark

![Кадр ICMP - эхо-ответ](image/11.png){#fig:011 width=70%}

## Анализ кадров канального уровня в Wireshark

![Кадр ARP](image/12.png){#fig:012 width=70%}

## Анализ кадров канального уровня в Wireshark

Теперь начнём новый процесс захвата трафика и пропингуем сайт wikipedia.org. 

![Пингование сайта wikipedia.org](image/13.png){#fig:013 width=70%}

## Анализ кадров канального уровня в Wireshark

![Пингование сайта wikipedia.org. Кадр ICMP - эхо-запрос](image/14.png){#fig:014 width=70%}

## Анализ кадров канального уровня в Wireshark

![Пингование сайта wikipedia.org. Кадр ICMP - эхо-ответ](image/15.png){#fig:015 width=70%}

## Анализ кадров канального уровня в Wireshark

![Пингование сайта wikipedia.org. Кадр ARP - запрос](image/16.png){#fig:016 width=70%}

## Анализ кадров канального уровня в Wireshark

![Пингование сайта wikipedia.org. Кадр ARP - ответ](image/17.png){#fig:017 width=60%}

# Анализ протоколов транспортного уровня в Wireshark

## Анализ протоколов транспортного уровня в Wireshark

Порт источника задан случайно, выбором из непривелигированных и незанятых портов, и равен 555882, порт назначения равен 80 - это стандартный порт HTTP. 

![Запрос HTTP по протоколу TCP](image/18.png){#fig:018 width=50%}

## Анализ протоколов транспортного уровня в Wireshark

В случае ответа порты заданы наоборот, то есть источник - 80 порт, назначение - 55582. 

![Ответ HTTP по протоколу TCP](image/19.png){#fig:019 width=60%}

## Анализ протоколов транспортного уровня в Wireshark

В разделе HTP можно увидеть ссылку на html-страницу.

![Раздел HTP](image/20.png){#fig:020 width=60%}

## Анализ протоколов транспортного уровня в Wireshark

![Раздел Line-based text data](image/21.png){#fig:021 width=70%}

## Анализ протоколов транспортного уровня в Wireshark

![Запрос dns по протоколу UDP](image/22.png){#fig:022 width=70%}

## Анализ протоколов транспортного уровня в Wireshark

В случае ответа порты заданы наоборот, то есть источник - 53 порт, назначение - 59084.

![Ответ DNS по протоколу UDP](image/23.png){#fig:023 width=60%}   

## Анализ протоколов транспортного уровня в Wireshark

![Запрос QUIC по протоколу UDP](image/24.png){#fig:024 width=70%} 

## Анализ протоколов транспортного уровня в Wireshark

В случае ответа порты заданы наоборот, то есть источник - 443 порт, назначение - 47597.

![Ответ QUIC по протоколу UDP](image/25.png){#fig:025 width=60%}  

## Анализ протоколов транспортного уровня в Wireshark

![Вкладка QUIK IETF в случае запроса quik](image/26.png){#fig:026 width=70%}  

## Анализ протоколов транспортного уровня в Wireshark

![Вкладка QUIK IETF в случае ответа quik](image/27.png){#fig:027 width=70%}  

# Анализ handshake протокола TCP в Wireshark

## Анализ handshake протокола TCP в Wireshark

Режим активного доступа. Во вкладке с флагами видно, что установлен бит SYN(Syn: set). Порядковый номер равен 3980370530.

![Первая ступень handshake протокола TCP](image/28.png){#fig:028 width=70%}  

## Анализ handshake протокола TCP в Wireshark

Режим пассивного доступа. Во вкладке с флагами видно, что установлены биты SYN и ACK(Syn: set, Acknowldgment: set). Порядковый номер содержит значение ISSb и равен 452625189. Поле номер подтверждения равен значению ISSa, которое получил в предыдущем пакете, плюс 1, то есть 3980370531.

![Вторая ступень handshake протокола TCP](image/29.png){#fig:029 width=50%}  

## Анализ handshake протокола TCP в Wireshark

Завершение рукопожатия. Во вкладке с флагами видно, что установлен бит ACK(Acknowldgment: set). Порядковый номер равен ISSa+1 и равен 3980370531. Поле номер подтверждения равен значению ISSb, которое получил в предыдущем пакете, плюс 1, то есть 452625190.

![Третья ступень handshake протокола TCP](image/30.png){#fig:030 width=50%}  

## Анализ handshake протокола TCP в Wireshark

На графике видно, что сначала клиент послал сообщение на сервер(стрелка вправо), а значение seq = 0. Затем сервер откликнулся(стрелка влево), значение seq = 0, а значение ack = 1. И в третьем пакете клиент оправил подтверждение получение SYN-сегмента(стрелка влево), оба значения syn и ack стали равны 1.

![График потока](image/31.png){#fig:031 width=50%}  

# Заключение

## Выводы

В результате выполнения лабораторной работы посредством Wireshark были изучены кадры Ethernet, а также проанализированы PDU протоколы транспортного и прикладного уровней стека TCP/IP.


