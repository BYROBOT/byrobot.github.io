**[*e_drive* for python](index.md)** / **Drone**

Modified : 2019.3.22

---

<h3>Command Line 명령어를 소개합니다.</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


## Command Line 명령어

e_drive 라이브러리에서는 소스 코드 작성없이 원하는 명령을 실행하거나 데이터를 확인할 수 있는 command line 명령어를 
지원하고 있습니다. 아래애서 소개하는 명령어를 실행하여 간단하게 데이터를 확인하거나 자동차를 작동해보시기 바랍니다.



## request

데이터 요청


### State 데이터 요청

State 데이터를 20회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request State 20 0.2
```


### RawCard 데이터 요청

RawCard 데이터를 20회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawCard 20 0.2
```


### RawCard 데이터 중 카드 인식 센서의 입력 범위 출력 요청

RawCard 데이터 중 카드 인식 센서의 입력값 범위를 100회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawCardRange 100 0.2
```



<br>


---

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. **Command Line**
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