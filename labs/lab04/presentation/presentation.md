---
## Front matter
lang: ru-RU
title: Лабораторная работа №4
subtitle: Подготовка экспериментального стенда GNS3
author:
  - Демидова Е. А.
institute:
  - Российский университет дружбы народов, Москва, Россия
date: 28 сентября 2023

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

Установка и настройка GNS3 и сопутствующего программного обеспечения.

## Задание

1. Установить GNS3-all-in-one, GNS3 VM, проверить корректность запуска.
2. Импортировать в GNS3 образ маршрутизатора FRR.
3. Импортировать в GNS3 образ маршрутизатора VyOS.

# Установка  GNS3-all-in-one, GNS3 VM

## Установка  GNS3-all-in-one

```
sudo add-apt-repository ppa:gns3/ppa
sudo apt update                                
sudo apt install gns3-gui gns3-server
```

## Установка  GNS3-all-in-one

![Установка GNS3-all-in-one](image/1.png){#fig:001 width=70%}

## Установка  GNS3 VM

![Импорт конфигураций](image/2.png){#fig:002 width=70%}

## Установка  GNS3 VM

![Параметры импорта](image/3.png){#fig:003 width=70%}

## Установка  GNS3 VM

![Настройка виртуальной машины GNS3 VM в VirtualBox](image/5.png){#fig:004 width=70%}

## Установка  GNS3 VM

```
vboxmanage modifyvm "GNS3 VM" --nested-hw-virt on
```

![Включение Nested VT-x/AMD-V](image/4.png){#fig:005 width=60%}

## Запуск экземпляра GNS3 в VirtualBox

![Мастер настройки](image/6.png){#fig:006 width=70%}

## Запуск экземпляра GNS3 в VirtualBox

![Окно с итоговыми настройками](image/7.png){#fig:007 width=70%}

## Запуск экземпляра GNS3 в VirtualBox

![Экземпляр GNS3 в VirtualBox](image/8.png){#fig:008 width=70%}

# Добавление образа маршрутизатора FRR

## Добавление образа маршрутизатора FRR

![Создание нового шаблона](image/9.png){#fig:009 width=70%} 

## Добавление образа маршрутизатора FRR

![Выбор образа](image/10.png){#fig:010 width=70%}

## Добавление образа маршрутизатора FRR

![Скачивание файлов](image/11.png){#fig:011 width=70%}

## Добавление образа маршрутизатора FRR

![Импорт образа](image/12.png){#fig:012 width=70%}

## Добавление образа маршрутизатора FRR

![Краткая информация об устройстве](image/13.png){#fig:013 width=60%}

## Добавление образа маршрутизатора FRR

![Настройка образа маршрутизатора: General settings](image/14.png){#fig:014 width=40%}

## Добавление образа маршрутизатора FRR

![Настройка образа маршрутизатора: HDD](image/15.png){#fig:015 width=70%}

# Добавление образа маршрутизатора VyOS

## Добавление образа маршрутизатора VyOS

Скачали  файл vyos-edu.gns3a из репозитория: https://github.com/yamadharma/vyos-build/releases. Затем импортировали vyos-edu.gns3a в GNS3 через пункт меню File>Import appliance.

## Добавление образа маршрутизатора VyOS

![Добавление образа устройства в GNS3: выбор места установки](image/17.png){#fig:016 width=70%}

## Добавление образа маршрутизатора VyOS

![Выбор версии образа](image/18.png){#fig:017 width=70%}

## Добавление образа маршрутизатора VyOS

![Установка образа маршрутизатора VyOS](image/19.png){#fig:018 width=70%}

## Добавление образа маршрутизатора VyOS

![Завершение установки образа маршрутизатора VyOS](image/20.png){#fig:019 width=70%}

## Добавление образа маршрутизатора VyOS

![Настройка образа маршрутизатора VyOS](image/21.png){#fig:020 width=40%}

# Выводы

В результате выполнения лабораторной работы были установлены  GNS3-all-in-one, GNS3 VM и проверена корректность их работы. Также импортированы образы маршрутизаторов FRR и VyOS.