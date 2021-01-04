**[*e_drone* for python](index.md)** / **Drone**

Modified : 2021.1.4

---

<h3>Command Line 명령어를 소개합니다.</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# Command Line 명령어

e_drone 라이브러리는 소스 코드 작성없이 원하는 명령을 실행하거나 데이터를 확인할 수 있는 command line 명령어를 
지원하고 있습니다. 아래에서 소개하는 명령어를 실행하여 간단하게 데이터를 확인하거나 작동해보시기 바랍니다.


<div align="center">
    <img src="../images/02_commandline_commandlist.png">
    <p>실행 가능한 명령 리스트</p>
</div>


<br>


# 1. control

조종

<br>

## 1.1. accel, wheel

최대 속도의 40% 속도로 3초간 전진하는 명령은 다음과 같습니다.


```
> python -m e_drone control 40 0 3000
```

<br>


## 1.2. Position

자동차를 특정 위치로 이동하는 명령입니다.

차례대로 x축(앞뒤, +가 앞)으로 0.1m, y축(좌우, +가 왼쪽)으로 0.1m 위치로 0.2m/s의 속도로 이동하는 명령은 다음과 같습니다.

```
> python -m e_drone position 0.1 0.1 0.2
```

<br>


## 1.3. Heading

자동차를 지정한 방향으로 회전 시킬 때 사용합니다.

왼쪽으로 30도를 10deg/sec 속도로 회전하는 명령은 다음과 같습니다.


```
> python -m e_drone heading 30 10
```


<br>
<br>






# 2. request

데이터 요청

<br>

## 2.1. State 데이터 요청(USB/BLE)

State 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drone request State 10 0.5
```

<div align="center">
    <img src="../images/02_commandline_request_state.png">
    <p>State 요청 실행 결과</p>
</div>

<br>


## 2.2. Motion 데이터 요청(USB)

Motion 데이터를 10회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drone request Motion 10 0.2
```

<div align="center">
    <img src="../images/02_commandline_request_motion.png">
    <p>Motion 요청 실행 결과</p>
</div>

<br>


## 2.3. RawLineTracer 데이터 요청(USB)

RawLineTracer 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drone request RawLineTracer 10 0.2
```

<div align="center">
    <img src="../images/02_commandline_request_rawlinetracer.png">
    <p>RawLineTracer 요청 실행 결과</p>
</div>

<br>


## 2.4. RawCard 데이터 요청(USB)

RawCard 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drone request RawCard 10 0.5
```

<div align="center">
    <img src="../images/02_commandline_request_rawcard.png">
    <p>RawCard 요청 실행 결과</p>
</div>

<br>


## 2.5. RawCard 데이터 중 색상 인식 범위 출력 요청(USB)

RawCard 데이터 중 색상 인식 범위 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drone request RawCardRange 10 0.5
```

<div align="center">
    <img src="../images/02_commandline_request_rawcardrange.png">
    <p>RawCardRange 요청 실행 결과</p>
</div>


<br>
<br>





# 3. light

LED 제어


<br>


## 3.1. RGB LED 제어(USB/BLE)

RGB LED 제어 시 아래와 같은 순서로 명령을 내리면 됩니다.

python -m e_drone light body [hold, flicker, flickerdouble, dimming, sunrise, sunset, rainbow, rainbow2] [interval] [R] [G] [B]

hold 상태일 때 interval은 밝기를 의미합니다. 값의 범위는 0 ~ 255입니다.

R, G, B 모두 값의 범위는 0 ~ 255입니다.

```
> python -m e_drone light body hold 100 50 50 10
> python -m e_drone light body flicker 100 50 50 10
> python -m e_drone light body flickerdouble 100 50 50 10
> python -m e_drone light body dimming 3 50 50 10
> python -m e_drone light body sunrise 5 50 50 10
> python -m e_drone light body sunset 5 50 50 10
> python -m e_drone light body rainbow 8 50 50 10
> python -m e_drone light body rainbow2 8 50 50 10
```


<br>

## 3.2. 단색 LED 제어(USB/BLE)

단색 LED 제어 시 아래와 같은 순서로 명령을 내리면 됩니다.

python -m e_drone light [front, head, tail, left, right] [hold, flicker, flickerdouble, dimming, sunrise, sunset] [interval]

hold 상태일 때 interval은 밝기를 의미합니다. 값의 범위는 0 ~ 255입니다.

```
> python -m e_drone light front hold 100
> python -m e_drone light head hold 100
> python -m e_drone light tail hold 100
> python -m e_drone light left hold 100
> python -m e_drone light right hold 100
```


<br>
<br>


# 4. buzzer

버저

<br>

## 4.1. 버저 작동(USB/BLE)

1000Hz의 소리를 500ms 동안 내게 합니다.

```
> python -m e_drone buzzer 1000 500
```

<div align="center">
    <img src="../images/02_commandline_buzzer.png">
    <p>Buzzer 테스트</p>
</div>



<br>
<br>



# 5. Bluetooth Low Energy

Bluetooth Low Energy 연결을 지원하는 Link 모듈을 통해 E-Drive 장치에 연결하는 기능을 지원합니다.

<br>
<br>

## 5.1. 장치 연결(USB)

마지막으로 연결한 시리얼 통신 장치에 연결한 후 가장 신호가 센 E-Drive 장치에 BLE 연결을 시도합니다.

```
> python -m e_drone connect
```

<br>


## 5.2. 장치 연결 해제(USB)

BLE 연결된 장치가 있으면 해제합니다.

```
> python -m e_drone disconnect
```


<br>
<br>





<br>




---

<h3><i>e_drone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. [Drone](05_drone.md)
 6. [Examples - Ping](examples_01_ping.md)
 7. [Examples - Information](examples_02_information.md)
 8. [Examples - Pairing](examples_03_pairing.md)
 9. [Examples - Control](examples_04_control.md)
10. [Examples - Sensor](examples_05_sensor.md)
11. [Examples - Motor](examples_06_motor.md)
12. [Examples - Setup](examples_07_setup.md)
13. [Examples - Buzzer](examples_08_buzzer.md)
14. [Examples - Vibrator](examples_09_vibrator.md)
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
