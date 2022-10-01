# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #2 выполнил(а):
- Ахидов Роман Игоревич
- РИ210934
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

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1.
### Реализовать совместную работу и передачу данных в связке Python - Google Sheets - Unity.
- ![image](https://user-images.githubusercontent.com/105049918/193399838-0853f3f5-cf3a-49d4-bae4-a100556a449a.png)
- ![image](https://user-images.githubusercontent.com/105049918/193400542-f3f561bf-b3e5-43a4-be5d-640ab44de501.png)
- ![image](https://user-images.githubusercontent.com/105049918/193400552-0e3dba01-c9d3-4cda-a6f7-f1be85846f51.png)
- ![image](https://user-images.githubusercontent.com/105049918/193420642-d47a6558-3255-4e2c-ad11-678b3592cb3f.png)
- ![image](https://user-images.githubusercontent.com/105049918/193423031-ffeead15-9ee7-4bb8-be9c-f972773d77e1.png)
- ![image](https://user-images.githubusercontent.com/105049918/193423046-3050bd9c-f75d-4b5a-b386-2f5d71f26d1c.png)
- ![image](https://user-images.githubusercontent.com/105049918/193423820-931bab71-6760-4047-b6af-9da399c6e09f.png)
- ![image](https://user-images.githubusercontent.com/105049918/193423835-1c696d30-e03c-40c9-b9d8-52335903eff5.png)
- ![image](https://user-images.githubusercontent.com/105049918/193423885-59d6d8fd-2c71-485f-b19d-ed2b2522fb68.png)





## Задание 2.
### Пошагово выполнить каждый пункт раздела "ход работы" с описанием и примерами реализации задач
Ход работы:
- Произвести подготовку данных для работы с алгоритмом линейной регрессии. 10 видов данных были установлены случайным образом, и данные находились в линейной зависимости. Данные преобразуются в формат массива, чтобы их можно было вычислить напрямую при использовании умножения и сложения.

- Определите связанные функции. Функция модели: определяет модель линейной регрессии wx+b. Функция потерь: функция потерь среднеквадратичной ошибки. Функция оптимизации: метод градиентного спуска для нахождения частных производных w и b.

![image](https://user-images.githubusercontent.com/105049918/190895477-b4f5d226-9f0d-4946-8086-b355c997776e.png)

Код задания можно посмотреть по ссылке: https://colab.research.google.com/drive/19aCJRYgkoxyFEQIqXTeDHqc-FbwNYwGW?usp=sharing

Связанными являются функции: model - loss_function, model - optimize, iterate - optimize, iterate - model; (одна из пары используется в другой)

## Задание 3
### Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.
![image](https://user-images.githubusercontent.com/105049918/190895470-fee6adae-50b6-4df4-8739-535c681ede3a.png)
При увеличении значений a или b значение функции loss_function имеет тенденцию увеличения.

### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.
![image](https://user-images.githubusercontent.com/105049918/190895556-54771d71-b5f9-4bb2-a774-a6f00ec95b22.png)
![image](https://user-images.githubusercontent.com/105049918/190895583-fa4c1a5b-0b7e-49d8-9d3e-3afe67acd1e8.png)
![image](https://user-images.githubusercontent.com/105049918/190895649-6d6ab27e-977c-45e7-b581-066acaec27cc.png)
При увеличении Lr увеличивается расфокусировка лучей. Значит Lr влияет на это.

## Выводы

Я поработал в Google Colab в первый раз, узнал что такоеп связанные функции, определил их. Установил Unity и Anaconda, но почти ничего не узнал про numpy/pandas, не до конца разобрался с Unity.

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
