# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #3 выполнил(а):
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
Познакомиться с программными средствами для создания системы машинного обучения и ее интеграции в Unity.


## Задание 1
### 
- Создаю пустой проект на Unity 
  ![2022-10-24_17-49-05](https://user-images.githubusercontent.com/70794890/197545531-e5bb62ae-4745-4ec9-a52f-96fef5e5571f.png)
- Устанавливаю packages для Unity
  ![2022-10-24_17-49-37](https://user-images.githubusercontent.com/70794890/197545862-4c16c7fb-8391-43c1-878b-e1075780f0cc.png)
- Скачиваю нужные библиотеки для Python
  ![2022-10-24_17-50-53](https://user-images.githubusercontent.com/70794890/197548868-c4414281-c230-4751-8efc-14ff4c1493b1.png)
- Создаю на сцене плоскость, куб и сферу
  ![2022-10-24_17-57-34](https://user-images.githubusercontent.com/70794890/197546168-6f052b17-edd1-4741-94f3-e1f8a29449b8.png)
- Создаю скрипт RollerAgent и подключаю его к шару
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    // Start is called before the first frame update
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }

    public Transform Target;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }

        Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);

        if(distanceToTarget < 1.42f)
        {
            SetReward(1.0f);
            EndEpisode();
        }
        else if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}

```

- Объекту «сфера» добавляю компоненты Rigidbody, Decision Requester, Behavior Parameters и настраиваю их
  ![2022-10-24_19-11-14](https://user-images.githubusercontent.com/70794890/197548113-40d54c92-77e0-4477-babf-5de0957e4498.png)
- Добавляю файл конфигурации для нейронной сети 
    ![image](https://user-images.githubusercontent.com/70794890/197548068-678cb27e-b557-438a-b95e-9ffcf46aaa99.png)
- Запускаю работу ML агента
  

## Задание 2
### 



## Задание 3
### 



## Выводы
Я познакомился с программными средствами для создания системы машинного обучения и ее интеграции в Unity.


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
