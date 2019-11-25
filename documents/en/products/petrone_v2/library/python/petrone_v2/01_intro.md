**[*petrone_v2* for python](index.md)** / **Intro**

Modified : 2018.3.5

---

* Kramdown table of contents
{:toc .toc}


<br>

# 1. *petrone_v2* for python 소개

***petrone_v2* for python**은 python에서 ***PETRONE V2***를 쉽게 사용할 수 있도록 도와주는 라이브러리입니다.

[https://pypi.python.org/pypi/petrone_v2](https://pypi.python.org/pypi/petrone_v2)


<br>
<br>


# 2. 설치

아래의 명령을 실행하시면 *petrone_v2*가 설치됩니다.

```
> pip install petrone_v2
```

<br>

최신 버전이 설치되지 않는다면 아래의 명령을 사용하시기 바랍니다.

```
> pip --no-cache-dir install petrone_v2
```


<br>
<br>


# 3. 삭제

아래의 명령을 실행하시면 *petrone_v2*가 삭제됩니다.

```
> pip uninstall petrone_v2
```


<br>
<br>


# 4. 시리얼 포트 검색


Drone 클래스 내부에서 pyserial을 사용하여 시리얼 포트에 연결합니다. 시리얼 포트에 연결하려면 장치 이름을 알고 있어야 합니다. 이 때 필요한 것이 컴퓨터에 연결된 시리얼 통신 장치들을 검색할 수 있는 명령입니다. 이 명령은 **pyserial**에서 제공하고 있습니다.

(**pyserial**은 *petrone_v2*를 설치한 경우 함께 설치됩니다.)

<br>

아래는 컴퓨터에 연결된 시리얼 통신 장치들의 이름을 확인하는 코드입니다.

```py
from serial.tools.list_ports import comports

for port, desc, hwid in sorted(comports()):
    print("%s" % (port))
```

<br>

장치에 대한 상세한 정보를 확인하려면 아래의 코드를 실행해보시기 바랍니다.

```py
from serial.tools.list_ports import comports

nodes = comports()

count = 0;
for node in nodes:
    print("[{0}]".format(count))
    print("         device: ", node.device)
    print("    description: ", node.description)
    print("   manufacturer: ", node.manufacturer)
    print("           hwid: ", node.hwid)
    print("      interface: ", node.interface)
    print("       location: ", node.location)
    print("           name: ", node.name)
    count += 1
```


<br>
<br>


# 5. 응용 프로젝트 예제

아래는 응용 프로젝트 예제입니다.

일반적인 진행 순서는 '**드론 객체 생성**' -> '**시리얼 포트 연결**' -> '**명령**' -> '**시리얼 포트 닫기**' 입니다.

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *

if __name__ == '__main__':

    drone = Drone()       # 드론 객체 생성
    drone.open("COM22")   # 시리얼 포트 연결

    drone.sendBuzzer(BuzzerMode.Scale, BuzzerScale.C4.value, 500)   # 버저에 4옥타브 도 소리를 500ms 동안 내라고 명령하기
    sleep(1)              # 1초간 sleep

    drone.close()         # 시리얼 포트 닫기 및 내부 데이터 수신 스레드 종료
```

<br>

open() 함수 사용 시 인자를 넣지 않으면, 내부에서 시리얼 포트를 검색하여 가장 마지막에 검색된 장치에 연결을 시도합니다.

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *

if __name__ == '__main__':

    drone = Drone()       # 드론 객체 생성
    drone.open()          # 시리얼 포트 연결(내부에서 시리얼 포트 리스트를 읽어서 마지막 장치에 연결)

    drone.sendBuzzer(BuzzerMode.Scale, BuzzerScale.C4.value, 500)   # 버저에 4옥타브 도 소리를 500ms 동안 내라고 명령하기
    sleep(1)              # 1초간 sleep

    drone.close()         # 시리얼 포트 닫기 및 내부 데이터 수신 스레드 종료
```


<br>

---

<h3><i>petrone_v2</i> for python</H3>

 1. **Intro**
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Ping](examples_01_ping.md)
 6. [Examples - Information](examples_02_information.md)
 7. [Examples - Pairing](examples_03_pairing.md)
 8. [Examples - Control](examples_04_control.md)
 9. [Examples - Sensor](examples_05_sensor.md)
10. [Examples - Motor](examples_06_motor.md)
11. [Examples - Setup](examples_07_setup.md)
12. [Examples - Buzzer](examples_08_buzzer.md)
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
