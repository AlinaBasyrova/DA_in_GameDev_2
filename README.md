# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
- Басырова Алина Радмировна
- РИ-220942

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Структура отчета
- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Задание 2.
- Задание 3.
- Выводы.

## Цель работы
научиться передавать в Unity данные из Google Sheets с помощью Python.

## Задание 1
### Выберите одну из компьютерных игр, приведите скриншот её геймплея и краткое описание концепта игры. Выберите одну из игровых переменных в игре (ресурсы, внутри игровая валюта, здоровье персонажей и т.д.), опишите её роль в игре, условия изменения / появления и диапазон допустимых значений. Постройте схему экономической модели в игре и укажите место выбранного ресурса в ней.


Minecraft - комьютерная игра в жанре песочница. Главной целью игры являются разведка, открытие и исследование мира пещер и подземелий, а также строительство собственных зданий и сооружений. Игрок может добывать ресурсы, обрабатывать их на других объектах и сражаться с монстрами.

В качестве игрового ресурса я выбрала шкалу голода. Голод представляет собой индикатор, состоящи1 из 10 голеней. Одна половина голени представляет одно очко голода. Таким образом, полная полоса состоит из двадцати очков голода. Она пополняется за счёт употребления еды и уменьшается за счёт действий игрока, таких как бег, плавание, добывание или нанесение урона. Количество единиц голода игрока контролирует регенерацию здоровья и способность к бегу или плаванию. Когда уровень голода достаточно высокий, здоровье игрока восстанавливается. Если он падает ниже определенного порога, игрок теряет способность к бегу.

- Когда шкала голода находится на уровне 18 или выше, здоровье медленно восстанавливается.
- Когда шкала голода находится на уровне 17 очков или ниже, здоровье игрока естественным образом не восстанавливается.
- Если шкала голода находится на уровне 6 (HungerHungerHunger) очков или ниже, игрок не может бежать.
- Когда шкала голода доходит до 0 (Empty Hunger) , здоровье игрока истощается.

  ![image](https://github.com/AlinaBasyrova/DA_in_GameDev_2/assets/129521982/125059f8-d6e7-46ad-b55a-5b8a1b005b6a)
  ![image](https://github.com/AlinaBasyrova/DA_in_GameDev_2/assets/129521982/f0a55997-7fb7-4cd0-908a-65c63f0ebc5e)




## Задание 2
### С помощью скрипта на языке Python заполните google-таблицу данными, описывающими выбранную игровую переменную в выбранной игре (в качестве таких переменных может выступать игровая валюта, ресурсы, здоровье и т.д.). Средствами google-sheets визуализируйте данные в google-таблице (постройте график, диаграмму и пр.) для наглядного представления выбранной игровой величины.


## Задание 3
### Настройте на сцене Unity воспроизведение звуковых файлов, описывающих динамику изменения выбранной переменной. Например, если выбрано здоровье главного персонажа вы можете выводить сообщения, связанные с его состоянием.


## Выводы

В процессе выполнения лабораторной работы я научился передавать в Unity данные из Google Sheets с помощью Python, а также познакомился с https://console.cloud.google.com .

| Plugin | README |
| ------ | ------ |
| GitHub | [plugins/github/README.md][PlGh] |
| Visual Studio| [plugins/visualstudio/README.md][PlGh] |
| Unity | [plugins/unity/README.md][PlMe] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
