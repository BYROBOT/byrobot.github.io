**[*e_drone* for python](index.md)** / **Intro**

Modified : 2021.12.31

---

* Kramdown table of contents
{:toc .toc}

<br>


# 시작하기 전에

아직 Python을 설치하지 않으셨다면 다음 문서를 먼저 확인하시기 바랍니다.

[Install Python 3 on macOS](/documents/kr/manual/install_python_3_on_mac_os/)

<br>
<br>



# 1. *e_drone* for python 소개

***e_drone* for python**은 python에서 ***E-DRONE***을 쉽게 사용할 수 있도록 도와주는 라이브러리입니다.

<br>

* The Python Package Index (PyPI)<br>
  [https://pypi.org/project/e-drone/](https://pypi.org/project/e-drone/)

* 라이브러리 저장소<br>
  [https://github.com/byrobot-python/e_drone](https://github.com/byrobot-python/e_drone)

* 예제 저장소<br>
  [https://github.com/byrobot-python/e_drone_examples](https://github.com/byrobot-python/e_drone_examples)


<br>
<br>



# 2. 설치

아래의 명령을 실행하시면 *e_drone*이 설치됩니다.

```
> pip install e_drone
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 install e_drone
```


<br>

최신 버전이 설치되지 않는다면 아래의 명령을 사용하시기 바랍니다.

```
> pip --no-cache-dir install e_drone
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 --no-cache-dir install e_drone
```

<br>
<br>



# 3. 업그레이드

최신 버전으로 업그레이드 하시려면 아래의 명령을 실행하시면 됩니다.

```
> pip install --upgrade e_drone
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 install --upgrade e_drone
```

<br>
<br>



# 4. 삭제

아래의 명령을 실행하시면 *e_drone*이 삭제됩니다.

```
> pip uninstall e_drone
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 uninstall e_drone
```

<br>
<br>



# 5. 시리얼 포트 검색


Drone 클래스 내부에서 pyserial을 사용하여 시리얼 포트에 연결합니다. 시리얼 포트에 연결하려면 장치 이름을 알고 있어야 합니다. 이 때 필요한 것이 컴퓨터에 연결된 시리얼 통신 장치들을 검색할 수 있는 명령입니다. 이 명령은 **pyserial**에서 제공하고 있습니다.

(**pyserial**은 *e_drone*을 설치한 경우 함께 설치됩니다.)

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



# 6. 응용 프로젝트 예제

아래는 응용 프로젝트 예제입니다.

일반적인 진행 순서는 '**드론 객체 생성**' -> '**시리얼 포트 연결**' -> '**명령**' -> '**시리얼 포트 닫기**' 입니다.

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':

    drone = Drone()       # 드론 객체 생성
    drone.open("COM22")   # 시리얼 포트 연결

    drone.send_buzzer(BuzzerMode.SCALE, BuzzerScale.C4.value, 500)   # 버저에 4옥타브 도 소리를 500ms 동안 내라고 명령하기
    sleep(1)              # 1초간 sleep

    drone.close()         # 시리얼 포트 닫기 및 내부 데이터 수신 스레드 종료
```

<br>

open() 함수 사용 시 인자를 넣지 않으면, 내부에서 시리얼 포트를 검색하여 가장 마지막에 검색된 장치에 연결을 시도합니다.

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *

if __name__ == '__main__':

    drone = Drone()       # 드론 객체 생성
    drone.open()          # 시리얼 포트 연결(내부에서 시리얼 포트 리스트를 읽어서 마지막 장치에 연결)

    drone.send_buzzer(BuzzerMode.SCALE, BuzzerScale.C4.value, 500)   # 버저에 4옥타브 도 소리를 500ms 동안 내라고 명령하기
    sleep(1)              # 1초간 sleep

    drone.close()         # 시리얼 포트 닫기 및 내부 데이터 수신 스레드 종료
```


<br>

---

<h3><i>e_drone</i> for python</H3>

 1. **Intro**
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
