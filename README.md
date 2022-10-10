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
### Pеализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы 1.
Запись в таблице:
![image](https://user-images.githubusercontent.com/105049918/194908602-4a613bf7-14c5-407b-9dd3-b4b28cefd790.png)
Код:
```py
import gspread
import numpy as np

gc = gspread.service_account(filename="unitydatascience-364207-4193ae536507.json")
sh = gc.open("UnitySheets")

x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)

def model(a, b, x):
  return a*x + b

def loss_function(a, b, x, y):
  num = len(x)
  prediction=model (a,b, x)
  return (0.5/num) * (np.square(prediction-y)).sum()

def optimize(a,b,x,y):
  num = len(x)
  prediction = model (a,b,x)
  da = (1.0/num) * ((prediction -y)*x).sum()
  db = (1.0/num) * ((prediction -y).sum())
  a = a - Lr*da
  b = b - Lr*db
  return a, b

def iterate(a,b,x,y,times) :
  for i in range(times):
    a,b = optimize (a,b,x,y)
  return a,b

a = np.random.rand(1)
print (a)
b = np.random.rand(1)
print (b)
Lr = 0.000001
for i in range(1, 12):
  a, b = iterate(a, b, x, y, i)
  prediction = model(a, b, x)
  loss = str(loss_function(a, b, x, y))
  loss = loss.replace(".", ",")
  sh.sheet1.update(("D" + str(i)), str(float(a)))
  sh.sheet1.update(("E" + str(i)), str(float(b)))
  sh.sheet1.update(("F" + str(i)), loss)
```

## Задание 3
### Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2.
Будем считать среднее значение по loss и выбирать звук:
хорошо) loss больше чем среднее значение
нормально) loss +- 50 от среднего значения
плохо) loss меньше чем среднее значение

![image](https://user-images.githubusercontent.com/105049918/194915062-4b9dff01-6c78-4238-833c-7e93925bc141.png)
```py
import gspread
import numpy as np

gc = gspread.service_account(filename="unitydatascience-364207-4193ae536507.json")
sh = gc.open("UnitySheets")

x = [3,21,22,34,54,34,55,67,89,99]
x = np.array(x)
y = [2,22,24,65,79,82,55,130,150,199]
y = np.array(y)

def model(a, b, x):
  return a*x + b

def loss_function(a, b, x, y):
  num = len(x)
  prediction=model (a,b, x)
  return (0.5/num) * (np.square(prediction-y)).sum()

def optimize(a,b,x,y):
  num = len(x)
  prediction = model (a,b,x)
  da = (1.0/num) * ((prediction -y)*x).sum()
  db = (1.0/num) * ((prediction -y).sum())
  a = a - Lr*da
  b = b - Lr*db
  return a, b

def iterate(a,b,x,y,times) :
  for i in range(times):
    a,b = optimize (a,b,x,y)
  return a,b

a = np.random.rand(1)
print (a)
b = np.random.rand(1)
print (b)
Lr = 0.000001
sumA = 0
sumB = 0
sumLoss = 0
for i in range(1, 12):
  a, b = iterate(a, b, x, y, i)
  prediction = model(a, b, x)
  loss = loss_function(a, b, x, y)
  sumA += a
  sumB += b
  sumLoss += loss
  sh.sheet1.update(("D" + str(i)), str(float(a)).replace(".", ","))
  sh.sheet1.update(("E" + str(i)), str(float(b)).replace(".", ","))
  sh.sheet1.update(("F" + str(i)), str(loss).replace(".", ","))
for i in range(1, 12):
  sh.sheet1.update(("G" + str(i)), str(sumLoss/11).replace(".", ","))
```

```С#
void Update()
        {
            if (Abs(dataSet["Mon_" + i.ToString()]) <= 50  && statusStart == false && i != dataSet.Count)
            {
                StartCoroutine(PlaySelectAudioNormal());
                Debug.Log(dataSet["Mon_" + i.ToString()]);
            }     
            else if (dataSet["Mon_" + i.ToString()] > 0 && statusStart == false && i != dataSet.Count)
            {   
                StartCoroutine(PlaySelectAudioGood());
                Debug.Log(dataSet["Mon_" + i.ToString()]);
            }
            else if (statusStart == false && i != dataSet.Count)
            {
                StartCoroutine(PlaySelectAudioBad());
                Debug.Log(dataSet["Mon_" + i.ToString()]);
            }
                
        }

        IEnumerator GoogleSheets()
        {
            UnityWebRequest currentResp = UnityWebRequest.Get("https://sheets.googleapis.com/v4/spreadsheets/1QT50QwMxz4wMMGVfEYp9t-ac274d7PdqgjTWptEM7zU/values/Лист1?key=AIzaSyAcEn3Tt_8W3pqRVhXdhC8xxgyMDZC2AvE");
            yield return currentResp.SendWebRequest();
            string rawResp = currentResp.downloadHandler.text;
            var rawJson = JSON.Parse(rawResp);
            foreach(var itemRawJson in rawJson["values"])
            {
                var parseJson = JSON.Parse(itemRawJson.ToString());
                var selectRaw = parseJson[0].AsStringList;
                dataSet.Add(("Mon_" + selectRaw[0]), (float.Parse(selectRaw[5])-(float.Parse(selectRaw[6]))));
            }
        }
```
## Выводы

Я научился делать совместную работу и передачу данных в связке Python - Google Sheets - Unity, самостоятельно разработал алгоритм воспроизведения звуков.

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
