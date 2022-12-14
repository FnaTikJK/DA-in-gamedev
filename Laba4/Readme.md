# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #4 выполнил(а):
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
### В проекте Unity реализовать перцетрон, который умеет производить вычисления OR, AND, NAND, XOR.
#### OR
Перцептрон легко научился выполнять логическую ИЛИ (иногда хватало всего 4 эпох)
![image](https://user-images.githubusercontent.com/70794890/204290361-cf7fc0ab-7709-4030-bd4a-6613ff013fd6.png)
#### AND
Перцептрон также легко справился с этой задачей, но здесь уже пришлось немного увеличить кол-во эпох
![image](https://user-images.githubusercontent.com/70794890/204290608-3ba186d5-8a41-4098-8ca7-90e9a04ab11e.png)
#### NAND
Обратное И Перцептрон тоже решил.
![image](https://user-images.githubusercontent.com/70794890/204291259-29e31355-f5f9-479e-935d-dbeab904bdff.png)
#### XOR
По причине которую описал Minsky, Перцпептрон не в состоянии решить исключающее или. Для демонстрации невоможности решения задачи "обучу" перцептрон на 1000 эпохах
![image](https://user-images.githubusercontent.com/70794890/204292385-3d0bd31c-b30f-460a-bb0c-bc4720766ab1.png)



## Задание 2
### Построить графики зависимости ошибки обучения эпох от количества. Указать от чего зависит необходимое количество эпох обучения.
![image](https://user-images.githubusercontent.com/70794890/204296929-69a12703-5fb3-4c2b-9b87-75e17dde31e9.png)

График AND не везде видно, тк он слился с NAND.

Кол-во эпох обучения зависит от Весов и смещения или bias, которые задаются условиями задачи.


## Задание 3
### Построить визуальную модель работы перцетрона на сцене Unity.
Создаю скрипт для симуляции логического И
```
using UnityEngine;

public class SimulateAND : MonoBehaviour
{
    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject.GetComponent<Renderer>().material.color == Color.white 
            && gameObject.GetComponent<Renderer>().material.color == Color.white)
        {
            other.gameObject.GetComponent<Renderer>().material.color = Color.white;
            gameObject.GetComponent<Renderer>().material.color = Color.white;
        }
        else
        {
            other.gameObject.GetComponent<Renderer>().material.color = Color.black;
            gameObject.GetComponent<Renderer>().material.color = Color.black;
        }
    }
}
```
Белый цвет - 1. Чёрный цвет - 0

Подготавливаю сцену
![image](https://user-images.githubusercontent.com/70794890/204313158-4ac53cb7-5484-488e-add3-c089021f58fa.png)
Результат
![image](https://user-images.githubusercontent.com/70794890/204313314-8f083050-58c5-4ccd-8551-fdefb29c5ed7.png)


## Выводы

В результате данной лабораторной работы я познакомился с Перцептроном, научился интегрировать его в Unity, узнал про эпохи обучения, ошибку и их взаимосвязь.

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
