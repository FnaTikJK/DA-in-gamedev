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
### Реализовать систему машинного обучения в связке Python - Google-Sheets – Unity.
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
- На 3 моделях
  ![1 тест](https://user-images.githubusercontent.com/70794890/197556372-36ad4c11-02e7-453f-b454-bf7dc6fdc4ee.png)
- На 9 моделях
  ![тест 2](https://user-images.githubusercontent.com/70794890/197556416-fbaf8155-bfcc-4eae-b3c7-269120da9b0d.png)
- На 27 моделях
  ![тест 3](https://user-images.githubusercontent.com/70794890/197556462-effaecf4-40f1-42df-93bd-95346f531fff.png)
  
Выводы:
  Скорость обучения Нейронной прямо пропорциональна кол-ву моделей, которые мы используем для обучения

  

## Задание 2
### Подробно опишите каждую строку файла конфигурации нейронной сети, доступного в папке с файлами проекта
```
behaviors:
  RollerBall: # id агента
    trainer_type: ppo # режим обучения (Proximal Policy Optimization)
    hyperparameters:
      batch_size: 10 # количество опыта на каждой итерации
      buffer_size: 100 # количество опыта, которое нужно набрать перед обновлением модели
      learning_rate: 3.0e-4 # начальная скорость обучения
      beta: 5.0e-4 # сила регуляции энтропии, увеличивает случайность действий
      epsilon: 0.2 # порог расхождений между старой и новой политиками при обновлении
      lambd: 0.99 # насколько агент полагается на свою текущую оценку значений при расчете предсказаний
      num_epoch: 3 # количество проходов, которые необходимо выполнить через буфер опыта при выполнении оптимизации
      learning_rate_schedule: linear # определяет как скорость обучения изменяется с течением времени
                                     # linear линейно уменьшает скорость
    network_settings:
      normalize: false # отключаем нормализацию входных данных
      hidden_units: 128 # количество нейронов в скрытых слоях сети
      num_layers: 2 # количество скрытых слоёв в сети
    reward_signals:
      extrinsic:
        gamma: 0.99 # коэффициент скидки для будущих вознаграждений
        strength: 1.0 # коэффициент на который умножается вознаграждение
    max_steps: 500000 # общее количество шагов, которые должны быть выполнены в среде до завершения обучения
    time_horizon: 64 # сколько опыта нужно собрать для каждого агента, прежде чем добавлять его в буфер
    summary_freq: 10000 # количество опыта, который необходимо собрать перед созданием и отображением статистики обучения
    
    
DecisionRequester запрашивает принятие решения на основе сделанных наблюдений через определенные промежутки времени.

BehaviorParameters определяет, сколько наблюдений мы принимаем и какую форму будут принимать выводимые действия.

BehaviorType имеет три варианта: эвристический (heuristic), по умолчанию (default) и вывод (inference). При установке значения по умолчанию, если нейронная сеть была сгенерирована, агент будет выполнять Inference, поскольку он использует нейронную сеть для принятия решений. Когда нейронная сеть не предусмотрена, она будет использовать эвристику. Эвристический метод можно рассматривать как традиционный подход к искусственному интеллекту, при котором программист вводит все возможные команды непосредственно в объект. Если установлено значение Heuristic only, агент будет запускать все, что находится в эвристическом методе.
```


## Задание 3
### Доработайте сцену и обучите ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета

-Изменяю скрипт
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

    public GameObject Target1;
    public GameObject Target2;
    private bool isTarget1Touched;
    private bool isTarget2Touched;

    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }

        Target1.transform.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
        Target2.transform.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
        Target1.SetActive(true);
        Target2.SetActive(true);
        isTarget1Touched = false;
        isTarget2Touched = false;
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target1.transform.localPosition);
        sensor.AddObservation(Target2.transform.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(isTarget1Touched);
        sensor.AddObservation(isTarget2Touched);
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

        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target1.transform.localPosition);
        float distanceToTarget1 = Vector3.Distance(this.transform.localPosition, Target2.transform.localPosition);

        if (!isTarget1Touched & distanceToTarget < 1.42f)
        {
            isTarget1Touched = true;
            Target1.SetActive(false);
        }
        if (!isTarget2Touched & distanceToTarget1 < 1.42f)
        {
            isTarget2Touched = true;
            Target2.SetActive(false);
        }
        if (isTarget1Touched & isTarget2Touched)
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
- Обучаю модель
  ![last](https://user-images.githubusercontent.com/70794890/197560976-b20bf060-f721-4bf3-b80f-36cf758470b1.png)


## Выводы
Я познакомился с программными средствами для создания системы машинного обучения и ее интеграции в Unity, лучше стал разбираться в скриптах для Unity.
Игровой баланс - соблюдение равновесия между различными экономическими показателями в игре, чтобы игровой процесс захватывал игрока и был интересен. Мы можем использовать машинное обучение для выявления наиболее оптимальных условий для игрока и экономической ситуации в игре со множеством параметров.


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
