**[*CodingDrone* for python](index.md)** / **Drone**

Modified : 2024.6.13

---

<h3>Command Line 명령어를 소개합니다.</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# Command Line 명령어

CodingDrone 라이브러리는 소스 코드 작성없이 원하는 명령을 실행하거나 데이터를 확인할 수 있는 command line 명령어를 
지원하고 있습니다. 아래에서 소개하는 명령어를 실행하여 간단하게 데이터를 확인하거나 작동해보시기 바랍니다.

```
> python -m CodingDrone
```

<div align="center">
    <img src="../images/02_commandline_commandlist.png">
    <p>실행 가능한 명령 리스트</p>
</div>


<br>
<br>


# 1. Firmware Upgrade

파이썬 라이브러리를 사용하여 드론 펌웨어를 업데이트하는 명령입니다.
드론 또는 조종기를 부트로더 모드로 USB에 연결하신 후 아래의 명령을 실행하시면 됩니다.

```
> python -m CodingDrone upgrade
```



<br>
<br>



# 2. Request Data

데이터 요청

<br>

## 2.1. State 데이터 요청

State 데이터를 10회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m CodingDrone request State 10 0.2
```

<div align="center">
    <img src="../images/02_commandline_request_state.png">
    <p>State 요청 실행 결과</p>
</div>

<br>


## 2.2. Motion 데이터 요청

Motion 데이터를 10회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m CodingDrone request Motion 10 0.2
```

<div align="center">
    <img src="../images/02_commandline_request_motion.png">
    <p>Motion 요청 실행 결과</p>
</div>

<br>



<br>
<br>



# 3. Command

명령

<br>

## 2.1. 이륙

```
> python -m CodingDrone takeoff
```


<br>


## 2.2. 착륙


```
> python -m CodingDrone landing
```


<br>


## 2.3. 정지


```
> python -m CodingDrone stop
```



<br>
<br>



# 3. Control


## 3.1. 조종 명령

<div align="center">
    <img src="../images/03_01_control.png">
    <p>조종 명령 예시 - Roll, Pitch, Yaw, Throttle</p>
</div>

```
> python -m CodingDrone control 0 30 0 0 5000
```


<br>


## 3.2. 조종 명령(위치, 방향)

<div align="center">
    <img src="../images/03_02_control_position_heading.png">
    <p>조종 명령 예시 - 위치, 방향</p>
</div>

```
> python -m CodingDrone position 5 0 0 2 90 45
```


<br>

## 3.3. 조종 명령(위치)

<div align="center">
    <img src="../images/03_03_control_position.png">
    <p>조종 명령 예시 - 위치</p>
</div>

```
> python -m CodingDrone position 5 0 0 2
```


<br>

## 3.4. 조종 명령(방향)

<div align="center">
    <img src="../images/03_04_control_heading.png">
    <p>조종 명령 예시 - 방향</p>
</div>

```
> python -m CodingDrone heading 90 45
```



<br>
<br>



# 4. buzzer

버저

<br>

## 4.1. 버저 작동

<div align="center">
    <img src="../images/04_01_buzzer.png">
    <p>버저 작동 예시</p>
</div>

400Hz의 소리를 2000ms 동안 내게 합니다.

```
> python -m CodingDrone buzzer 400 2000
```



<br>
<br>



# 5. vibrator

진동

<br>

## 5.1. 진동 작동

<div align="center">
    <img src="../images/05_01_vibrator.png">
    <p>진동 작동 예시</p>
</div>

500ms동안 켜고, 500ms 동안 끄는 동작을 2000ms 동안 실행

```
> python -m CodingDrone vibrator 500 500 2000
```



<br>
<br>



# 6. light

LED 제어


<br>


## 6.1. 단색 LED 제어

단색 LED 제어 시 아래와 같은 순서로 명령을 내리면 됩니다.

python -m CodingDrone light [rear, a, b] [hold, flicker, flickerdouble, dimming, sunrise, sunset] [interval]

hold 상태일 때 interval은 밝기를 의미합니다. 값의 범위는 0 ~ 255입니다.

<div align="center">
    <img src="../images/06_01_light_single.png">
    <p>단색 LED 작동 예시</p>
</div>

```
> python -m CodingDrone light rear hold 100
> python -m CodingDrone light a hold 100
> python -m CodingDrone light b hold 100
```


<br>

## 6.2. RGB LED 제어

RGB LED 제어 시 아래와 같은 순서로 명령을 내리면 됩니다.

python -m CodingDrone light [body] [hold, flicker, flickerdouble, dimming, sunrise, sunset, rainbow, rainbow2] [interval] [R] [G] [B]

hold 상태일 때 interval은 밝기를 의미합니다. 값의 범위는 0 ~ 255입니다.

R, G, B 모두 값의 범위는 0 ~ 255입니다.

<div align="center">
    <img src="../images/06_02_light_rgb.png">
    <p>RGB LED 작동 예시</p>
</div>

```
> python -m CodingDrone light body hold 100 50 50 10
> python -m CodingDrone light body flicker 100 50 50 10
> python -m CodingDrone light body flickerdouble 100 50 50 10
> python -m CodingDrone light body dimming 3 50 50 10
> python -m CodingDrone light body sunrise 5 50 50 10
> python -m CodingDrone light body sunset 5 50 50 10
> python -m CodingDrone light body rainbow 8 50 50 10
> python -m CodingDrone light body rainbow2 8 50 50 10
```


<br>
<br>



---

<h3><i>CodingDrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. **Command Line**
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
