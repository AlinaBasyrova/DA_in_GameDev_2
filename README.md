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

- Когда шкала голода достигает 20, здоровье восстанавливается на 1 очко жизни (половина сердца) каждые 1/2 секунды.‌ 
- Когда шкала голода находится на уровне 18 или выше, здоровье медленно восстанавливается на 1 очко жизни каждые 4 секунды.
- Когда шкала голода находится на уровне 17 очков или ниже, здоровье игрока естественным образом не восстанавливается и не убывает.
- Если шкала голода находится на уровне 6  очков или ниже, игрок не может бежать.
- Когда шкала голода доходит до 0  , здоровье игрока убывает на 1 очко жизни каждые 4 секунды.

  ![image](https://github.com/AlinaBasyrova/DA_in_GameDev_2/assets/129521982/125059f8-d6e7-46ad-b55a-5b8a1b005b6a)
  ![image](https://github.com/AlinaBasyrova/DA_in_GameDev_2/assets/129521982/f0a55997-7fb7-4cd0-908a-65c63f0ebc5e)




## Задание 2
### С помощью скрипта на языке Python заполните google-таблицу данными, описывающими выбранную игровую переменную в выбранной игре (в качестве таких переменных может выступать игровая валюта, ресурсы, здоровье и т.д.). Средствами google-sheets визуализируйте данные в google-таблице (постройте график, диаграмму и пр.) для наглядного представления выбранной игровой величины.

Ход работы:
- Настроить доступ к google-таблице по api, написать код генерации данных с помощью Python. В первом столбце таблицы показывается номер генерации, во втором - количество очков голода, в третьем - изменения шкалы здоровья за секунду.

```py
import gspread
import numpy as np
gc = gspread.service_account(filename='da-in-gamedev-2-404609-c13383911b0b.json')
sh = gc.open("DA_2")
price = np.random.randint(0, 20, 11)
mon = list(range(1,11))
i = 0
while i <= len(mon):
    i += 1
    if i == 0:
        continue
    else:
        hunger = price[i-1]
        hearts_changing = 0
        if hunger == 0:
            hearts_changing = -0.25
        if hunger > 17:
            hearts_changing = 0.25
        if hunger == 20:
            hearts_changing = 2
        hearts_changing = str(hearts_changing)
        hunger = str(hunger)
        hearts_changing = hearts_changing.replace('.',',')
        sh.sheet1.update(('A' + str(i)), str(i))
        sh.sheet1.update(('B' + str(i)), hunger)
        sh.sheet1.update(('C' + str(i)), hearts_changing)

        print(hunger)
print('Done')
```

- Передать данные в таблицу, построить график изменения очков жизни в зависимости от количества очков голода.

![image](https://github.com/AlinaBasyrova/DA_in_GameDev_2/assets/129521982/50369c93-c2f1-4b02-aa5e-d1b48ad00272)

![image](https://github.com/AlinaBasyrova/DA_in_GameDev_2/assets/129521982/ae685348-fcbd-45bb-a7bd-79dafda607b0)


## Задание 3
### Настройте на сцене Unity воспроизведение звуковых файлов, описывающих динамику изменения выбранной переменной. Например, если выбрано здоровье главного персонажа вы можете выводить сообщения, связанные с его состоянием.

```py
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Networking;
using SimpleJSON;

public class NewBehaviourScript : MonoBehaviour
{
    public AudioClip goodSpeak;
    public AudioClip normalSpeak;
    public AudioClip badSpeak;
    private AudioSource selectAudio;
    private Dictionary<string,float> dataSet = new Dictionary<string, float>();
    private bool statusStart = false;
    private int i = 1;

    // Start is called before the first frame update
    void Start()
    {
        StartCoroutine(GoogleSheets());
    }

    // Update is called once per frame
    void Update()
    {
        if (dataSet["Mon_" + i.ToString()] >= 18 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioGood());
            Debug.Log(dataSet["Mon_" + i.ToString()] + " Good");
        }

        if (dataSet["Mon_" + i.ToString()] <=6 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioBad());
            Debug.Log(dataSet["Mon_" + i.ToString()] + " Bad");
        }

        if (dataSet["Mon_" + i.ToString()] > 6 & dataSet["Mon_" + i.ToString()] < 18 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlaySelectAudioNormal());
            Debug.Log(dataSet["Mon_" + i.ToString()] + " Normal");
        }

    }
IEnumerator GoogleSheets()
    {
        UnityWebRequest curentResp = 
            UnityWebRequest.Get("https://sheets.googleapis.com/v4/spreadsheets/1ZSpkCkga4817WRdTNutVTqWq9o456WExtbbYC7rHDbE/values/Sheet1?key=AIzaSyD9KX2Ec6h2P8mib_r8jCiA1GwszhpSlnU");
        yield return curentResp.SendWebRequest();
        string rawResp = curentResp.downloadHandler.text;
        var rawJson = JSON.Parse(rawResp);
        foreach (var itemRawJson in rawJson["values"])
        {
            var parseJson = JSON.Parse(itemRawJson.ToString());
            var selectRow = parseJson[0].AsStringList;
            dataSet.Add(("Mon_" + selectRow[0]), float.Parse(selectRow[1]));
        }
    }

    IEnumerator PlaySelectAudioGood()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = goodSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioNormal()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = normalSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(3);
        statusStart = false;
        i++;
    }
    IEnumerator PlaySelectAudioBad()
    {
        statusStart = true;
        selectAudio = GetComponent<AudioSource>();
        selectAudio.clip = badSpeak;
        selectAudio.Play();
        yield return new WaitForSeconds(4);
        statusStart = false;
        i++;
    }
}
```

![image](https://github.com/AlinaBasyrova/DA_in_GameDev_2/assets/129521982/d0fa6267-3114-4c20-ac0e-4a8f4f2617f7)



## Выводы

В процессе выполнения лабораторной работы я научился передавать в Unity данные из Google Sheets с помощью Python, а также познакомился с https://console.cloud.google.com .

| Plugin | README |
| ------ | ------ |
| GitHub | [plugins/github/README.md][PlGh] |
| Visual Studio| [plugins/visualstudio/README.md][PlGh] |
| Unity | [plugins/unity/README.md][PlMe] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
