# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
- Яськов Антоний Михайлович
- РИ210942
Отметка о выполнении заданий (заполняется студентом):

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
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.


## Задание 1
### Реализовать совместную работу Python-GoogleSheets-Unity
- Подключаю API для работы с таблицами и диском в google console
![image](https://user-images.githubusercontent.com/70794890/194406437-fa08e65b-c2ae-4f74-b8a5-13c520bab74f.png)
![image](https://user-images.githubusercontent.com/70794890/194406496-6414a37b-41f2-4f3a-b24c-f2edcdb4c096.png)

- Реализовываю запись данных из скрипта на python в google-таблицу
![image](https://user-images.githubusercontent.com/70794890/194407355-adc42dff-d14f-48c4-9cc3-460f606af392.png)
![image](https://user-images.githubusercontent.com/70794890/194407392-4fd5ac21-3b32-4df1-b787-af20a256675c.png)

- Создаю проект на Unity и подключаю к нему данные из гугл-таблицы
![image](https://user-images.githubusercontent.com/70794890/194407616-6324a327-85d5-46e9-b767-47f43577e043.png)
![image](https://user-images.githubusercontent.com/70794890/194407806-94271c20-93fe-44d8-99b9-000d34cb5821.png)

- Пишу функционал на Unity который воспроизводит аудио в зависимости от значения данных из таблицы
![image](https://user-images.githubusercontent.com/70794890/194408001-52cbabe0-2e89-499a-95d4-82150e30acbe.png)
![image](https://user-images.githubusercontent.com/70794890/194408036-39585a85-25e7-41b3-9224-e7ada5de62af.png)



## Задание 2
### Реализовать запись в google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы №1. 
#### Немного изменил данные: анализирую наиболее эффективный размер шага. Увеличиваю шаг в 10 раз в каждой строке(итерации) таблицы и смотрю какие "потери" получатся на 100 итерации
- Ввожу методы и переменные из прошлой лабораторой работы
![image](https://user-images.githubusercontent.com/70794890/194423681-7e9ecc0e-cbe4-43fe-af59-9264abf60074.png)
![image](https://user-images.githubusercontent.com/70794890/194423715-7117bace-de06-4e63-b5f9-1dc04a78896d.png)

- Заполняю таблицу данными 

![image](https://user-images.githubusercontent.com/70794890/194424033-7d09f091-b20f-4c10-a3f8-825594b9f891.png)
![image](https://user-images.githubusercontent.com/70794890/194424077-a3034122-f46a-407c-8156-645456a3971a.png)



## Задание 3
### Разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от данных во 2 задании.
- Модифицирую dataSet под текующую задачу
![image](https://user-images.githubusercontent.com/70794890/194426708-b66ae8b8-8979-41fc-973a-41415cd7e7cf.png)
![image](https://user-images.githubusercontent.com/70794890/194426859-8f390105-0b25-44e3-8639-d9fc2b87ccfb.png)
- Делаю обработчик сценария

![image](https://user-images.githubusercontent.com/70794890/194426972-d4c08da9-963d-4682-9290-9637fbffa9ec.png)

Thread(3000) использовал тк методы Unity почему-то не останавливалаи выполнение программы и аудио глушили друг друга.

Сценарий следующий: Если с новым шагом наши "потери" на одной и той же итерации меньше, то значит шаг выбран правильно и играет хорошая аудиодоржка, если равны, но играет нормальная, если "потери" стали больше, то играет плохая музыка.
![image](https://user-images.githubusercontent.com/70794890/194427393-8621470d-4aad-42ba-becf-bbad1c053228.png)



## Выводы

В результате данной лабораторной работы я познакомился с тем как можно связать гугл-таблицы, unity и python. Также лучше разобрался в движке Unity.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
