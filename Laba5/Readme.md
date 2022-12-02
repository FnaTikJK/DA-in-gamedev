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
![image](https://user-images.githubusercontent.com/70794890/205243155-41a4daf4-b597-43fd-9ab6-75b7b3c54c52.png)


Установил tensorflow, запустил tensorboard. Поулчил следующие графики

![2022-12-02_12-52-56](https://user-images.githubusercontent.com/70794890/205243278-d293ff84-8ac0-44bf-ac95-d682893876aa.png)

![2022-12-02_12-53-12](https://user-images.githubusercontent.com/70794890/205243285-20f0c581-0622-4607-bb92-753c4340beec.png)




## Задание 2
### Измените параметры файла. yaml-агента и определить какие параметры и как влияют на обучение модели
num_epoch = 3 => 10
Получил следующие графики
![image](https://user-images.githubusercontent.com/70794890/205248609-ee571774-422d-441d-a9f6-8fa851c712b8.png)

![image](https://user-images.githubusercontent.com/70794890/205248645-480ff42f-ae70-4a4d-8396-67aa24f53e4b.png)


learning_rate = 3.0e-4 => 0.5e-4
![image](https://user-images.githubusercontent.com/70794890/205250444-49db8620-ef95-4944-8242-75c847478404.png)

![image](https://user-images.githubusercontent.com/70794890/205250480-4cf08f28-beb5-4e1d-a7f3-07c3f80fa76a.png)

beta = 1.0e-2 => 1.0e-4

![image](https://user-images.githubusercontent.com/70794890/205252144-561d86d7-c79f-4d6a-ae36-764f97dc1f67.png)

![image](https://user-images.githubusercontent.com/70794890/205252178-17db0a38-b138-41e8-97a2-715fce358e8e.png)

lambd = 0.95 => 0.7

![image](https://user-images.githubusercontent.com/70794890/205253388-d0651812-2d99-45c8-8a2f-9c211f5fb503.png)


![image](https://user-images.githubusercontent.com/70794890/205253539-8fdc66e5-81aa-4055-bc3c-eb4eac943b72.png)








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
