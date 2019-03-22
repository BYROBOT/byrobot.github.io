**[*e_drive* for python](index.md)** / **Drone**

Modified : 2019.3.22

---

<h3>Command Line 명령어를 소개합니다.</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


# Command Line 명령어

e_drive 라이브러리는 소스 코드 작성없이 원하는 명령을 실행하거나 데이터를 확인할 수 있는 command line 명령어를 
지원하고 있습니다. 아래에서 소개하는 명령어를 실행하여 간단하게 데이터를 확인하거나 작동해보시기 바랍니다.

<br>


# request

데이터 요청

<br>

### State 데이터 요청

State 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request State 10 0.5
```

<div align="center">
    <img src="../images/05_commandline_request_state.png">
    <p>State 요청 실행 결과</p>
</div>

<br>


### Motion 데이터 요청

Motion 데이터를 10회 0.2초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request Motion 10 0.2
```

<div align="center">
    <img src="../images/05_commandline_request_motion.png">
    <p>Motion 요청 실행 결과</p>
</div>

<br>


### RawLineTracer 데이터 요청

RawLineTracer 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawLineTracer 10 0.2
```

<div align="center">
    <img src="../images/05_commandline_request_rawlinetracer.png">
    <p>RawLineTracer 요청 실행 결과</p>
</div>

<br>


### RawCard 데이터 요청

RawCard 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawCard 10 0.5
```

<div align="center">
    <img src="../images/05_commandline_request_rawcard.png">
    <p>RawCard 요청 실행 결과</p>
</div>

<br>


### RawCard 데이터 중 색상 인식 범위 출력 요청

RawCard 데이터 중 색상 인식 범위 데이터를 10회 0.5초 주기로 요청하는 명령은 다음과 같습니다.

```
> python -m e_drive request RawCardRange 10 0.5
```

<div align="center">
    <img src="../images/05_commandline_request_rawcardrange.png">
    <p>RawCardRange 요청 실행 결과</p>
</div>


<br>
<br>



# buzzer

버저

<br>

### 버저 작동

1000Hz의 소리를 500ms 동안 내게 합니다.

```
> python -m e_drive buzzer 1000 500
```

<div align="center">
    <img src="../images/05_commandline_buzzer.png">
    <p>Buzzer 테스트</p>
</div>



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
