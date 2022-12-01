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
### Интегрировать экономическую систему в проект Unity и обучить Ml Agent.
Скачал проект, установил необходимые библиотеки запустил обучение ml-агента
![image](https://user-images.githubusercontent.com/70794890/205007629-b4ec7cac-543f-4533-ba8f-3581bde4840d.png)

Установил tensorflow, запустил tensorboard. Поулчил следующие графики

![image](https://user-images.githubusercontent.com/70794890/205011559-f819c4eb-806c-4309-8b62-614572436d41.png)

![image](https://user-images.githubusercontent.com/70794890/205011606-b21d1bc9-5003-4b91-9a27-e507db5f7ef5.png)



## Задание 2
### Измените параметры файла. yaml-агента и определить какие параметры и как влияют на обучение модели




## Задание 3
### Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.

Да, должна, тк решение задачи, которую писали до этого - минимизация этой функции. Это значит, что если программа работает корректно, то и loss стремится к нулю.
Приведу пример
- Беру другие данные 

![image](https://user-images.githubusercontent.com/70794890/190989316-311d9950-66aa-4d19-b204-ab5a5f829233.png)
- Смотрю "потери" на 1 шаге 

![image](https://user-images.githubusercontent.com/70794890/190989369-6f26e787-f827-4c28-888e-a0a4e13cd641.png)
- Смотрю "потери" на 1000 шаге

![image](https://user-images.githubusercontent.com/70794890/190989427-55de8039-59ab-4dee-84cd-76b5a1291815.png)

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
