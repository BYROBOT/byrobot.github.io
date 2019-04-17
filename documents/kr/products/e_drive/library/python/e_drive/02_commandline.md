**[*e_drive* for python](index.md)** / **Drone**

Modified : 2019.4.17

---

<h3>Command Line 명령어를 소개합니다.</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# Command Line 명령어

e_drive 라이브러리는 소스 코드 작성없이 원하는 명령을 실행하거나 데이터를 확인할 수 있는 command line 명령어를 
지원하고 있습니다. 아래에서 소개하는 명령어를 실행하여 간단하게 데이터를 확인하거나 작동해보시기 바랍니다.

일부 명령은 데이터의 길이가 길어 USB로 연결한 상태에서만 동작합니다. BLE로 전송 가능한 데이터 길이는 헤더 4바이트 + 데이터 16바이트를 포함하여 모두 20바이트입니다. 이를 초과하는 데이터는 USB로 연결했을 때에만 송수신 가능합니다. 편의를 위해 아래의 명령어 중 USB와 BLE 송수신 가능 여부를 제목 옆에 표기하였습니다.

<div align="center">
    <img src="../images/02_commandline_commandlist.png">
    <p>실행 가능한 명령 리스트</p>
</div>


<br>


# 1. request

데이터 요청

<br>

## 1.1. State 데이터 요청(USB/BLE)

State 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request State 10 0.5
```

<div align="center">
    <img src="../images/02_commandline_request_state.png">
    <p>State 요청 실행 결과</p>
</div>

<br>


## 1.2. Motion 데이터 요청(USB)

Motion 데이터를 10회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request Motion 10 0.2
```

<div align="center">
    <img src="../images/02_commandline_request_motion.png">
    <p>Motion 요청 실행 결과</p>
</div>

<br>


## 1.3. RawLineTracer 데이터 요청(USB)

RawLineTracer 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawLineTracer 10 0.2
```

<div align="center">
    <img src="../images/02_commandline_request_rawlinetracer.png">
    <p>RawLineTracer 요청 실행 결과</p>
</div>

<br>


## 1.4. RawCard 데이터 요청(USB)

RawCard 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawCard 10 0.5
```

<div align="center">
    <img src="../images/02_commandline_request_rawcard.png">
    <p>RawCard 요청 실행 결과</p>
</div>

<br>


## 1.5. RawCard 데이터 중 색상 인식 범위 출력 요청(USB)

RawCard 데이터 중 색상 인식 범위 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawCardRange 10 0.5
```

<div align="center">
    <img src="../images/02_commandline_request_rawcardrange.png">
    <p>RawCardRange 요청 실행 결과</p>
</div>


<br>
<br>





# 2. light

LED 제어


<br>


## 2.1. RGB LED 제어(USB/BLE)

RGB LED 제어 시 아래와 같은 순서로 명령을 내리면 됩니다.

python -m e_drive light body [hold, flicker, flickerdouble, dimming, sunrise, sunset, rainbow, rainbow2] [interval] [R] [G] [B]

hold 상태일 때 interval은 밝기를 의미합니다. 값의 범위는 0 ~ 255입니다.

R, G, B 모두 값의 범위는 0 ~ 255입니다.

```
> python -m e_drive light body hold 100 50 50 10
> python -m e_drive light body flicker 100 50 50 10
> python -m e_drive light body flickerdouble 100 50 50 10
> python -m e_drive light body dimming 3 50 50 10
> python -m e_drive light body sunrise 5 50 50 10
> python -m e_drive light body sunset 5 50 50 10
> python -m e_drive light body rainbow 8 50 50 10
> python -m e_drive light body rainbow2 8 50 50 10
```


<br>

## 2.2. 단색 LED 제어(USB/BLE)

단색 LED 제어 시 아래와 같은 순서로 명령을 내리면 됩니다.

python -m e_drive light [front, head, tail, left, right] [hold, flicker, flickerdouble, dimming, sunrise, sunset] [interval]

hold 상태일 때 interval은 밝기를 의미합니다. 값의 범위는 0 ~ 255입니다.

```
> python -m e_drive light front hold 100
> python -m e_drive light head hold 100
> python -m e_drive light tail hold 100
> python -m e_drive light left hold 100
> python -m e_drive light right hold 100
```


<br>
<br>


# 3. buzzer

버저

<br>

## 3.1. 버저 작동(USB/BLE)

1000Hz의 소리를 500ms 동안 내게 합니다.

```
> python -m e_drive buzzer 1000 500
```

<div align="center">
    <img src="../images/02_commandline_buzzer.png">
    <p>Buzzer 테스트</p>
</div>



<br>
<br>



# 4. Bluetooth Low Energy

Bluetooth Low Energy 연결을 지원하는 Link 모듈을 통해 E-Drive 장치에 연결하는 기능을 지원합니다.

<br>
<br>

## 4.1. 장치 연결(USB)

마지막으로 연결한 시리얼 통신 장치에 연결한 후 가장 신호가 센 E-Drive 장치에 BLE 연결을 시도합니다.

```
> python -m e_drive connect
```

<br>


## 4.2. 장치 연결 해제(USB)

BLE 연결된 장치가 있으면 해제합니다.

```
> python -m e_drive disconnect
```


<br>
<br>



# 5. GUI

e_drive 라이브러리에서는 시험적으로 kivy 라이브러리를 사용한 응용프로그램을 제공합니다.

e_drive 라이브러리에 의존성을 포함하지 않은 상태이기 때문에 직접 설치가 필요합니다.

<br>
kivy 라이브러리 설치는 아래의 링크를 참고하시기 바랍니다.

[Kivy Installation](https://kivy.org/doc/stable/installation/installation.html)

<br>
윈도우 버전의 설치는 아래의 링크를 참고하시기 바랍니다.

[Installation on Windows](https://kivy.org/doc/stable/installation/installation-windows.html#installation)


<br>
<br>


## 5.1. 카드 읽기 테스트(USB)

센서를 통해 읽은 카드의 색상을 GUI로 표시합니다.

```
> python -m e_drive card
```

<div align="center">
    <img src="../images/02_commandline_card.png">
    <p>카드 읽기 테스트</p>
</div>


<br>
<br>


## 5.2. 카드 목록 읽기 테스트(USB)

센서를 통해 읽은 카드와 카드 목록을 GUI로 표시합니다.

```
> python -m e_drive cards
```

<div align="center">
    <img src="../images/02_commandline_cards.png">
    <p>카드 목록 읽기 테스트</p>
</div>






<br>




---

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. **Command Line**
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. [Drone](05_drone.md)
 6. [Examples - Ping](examples_01_ping.md)
 7. [Examples - Information](examples_02_information.md)
 8. [Examples - Control](examples_03_control.md)
 9. [Examples - Sensor](examples_04_sensor.md)
10. [Examples - Motor](examples_05_motor.md)
11. [Examples - Setup](examples_06_setup.md)
12. [Examples - Buzzer](examples_07_buzzer.md)
13. [Examples - Light](examples_08_light.md)
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
