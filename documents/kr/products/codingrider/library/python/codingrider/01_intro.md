
**[*CodingRider* for python](index.md)** / **Intro**

Modified : 2024.5.17

---

* Kramdown table of contents
{:toc .toc}

<br>


# 시작하기 전에

아직 Python을 설치하지 않으셨다면 다음 문서를 먼저 확인하시기 바랍니다.

[Install Python 3 on macOS](/documents/kr/manual/install_python_3_on_mac_os/)

<br>
<br>



# 1. *CodingRider* for python 소개

***CodingRider* for python**은 python에서 ***CodingRider***을 쉽게 사용할 수 있도록 도와주는 라이브러리입니다.

[https://pypi.org/project/CodingRider/](https://pypi.org/project/CodingRider/)

<br>
<br>



# 2. 설치

아래의 명령을 실행하시면 *CodingRider*가 설치됩니다.

```
> pip install CodingRider
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 install CodingRider
```


<br>

최신 버전이 설치되지 않는다면 아래의 명령을 사용하시기 바랍니다.

```
> pip --no-cache-dir install CodingRider
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 --no-cache-dir install CodingRider
```

<br>
<br>



# 3. 업그레이드

최신 버전으로 업그레이드 하시려면 아래의 명령을 실행하시면 됩니다.

```
> pip install --upgrade CodingRider
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 install --upgrade CodingRider
```

<br>
<br>



# 4. 삭제

아래의 명령을 실행하시면 *CodingRider*이 삭제됩니다.

```
> pip uninstall CodingRider
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 uninstall CodingRider
```

<br>
<br>



# 5. 시리얼 포트 검색


Drone 클래스 내부에서 pyserial을 사용하여 시리얼 포트에 연결합니다. 시리얼 포트에 연결하려면 장치 이름을 알고 있어야 합니다. 이 때 필요한 것이 컴퓨터에 연결된 시리얼 통신 장치들을 검색할 수 있는 명령입니다. 이 명령은 **pyserial**에서 제공하고 있습니다.

(**pyserial**은 *CodingRider*을 설치한 경우 함께 설치됩니다.)

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

count = 0
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

from CodingRider.drone import *
from CodingRider.protocol import *

if __name__ == '__main__':

    drone = Drone()       # 드론 객체 생성
    drone.open()   # 시리얼 포트 연결

    drone.sendBuzzer(BuzzerMode.Scale, BuzzerScale.C4.value, 500)   # 버저에 4옥타브 도 소리를 500ms 동안 내라고 명령하기
    sleep(1)              # 1초간 sleep

    drone.close()         # 시리얼 포트 닫기 및 내부 데이터 수신 스레드 종료
```

<br>

open() 함수 사용 시 인자를 넣지 않으면, 내부에서 시리얼 포트를 검색하여 가장 마지막에 검색된 장치에 연결을 시도합니다.

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *

if __name__ == '__main__':

    drone = Drone()       # 드론 객체 생성
    drone.open()          # 시리얼 포트 연결(내부에서 시리얼 포트 리스트를 읽어서 마지막 장치에 연결)

    drone.sendBuzzer(BuzzerMode.Scale, BuzzerScale.C4.value, 500)   # 버저에 4옥타브 도 소리를 500ms 동안 내라고 명령하기
    sleep(1)              # 1초간 sleep

    drone.close()         # 시리얼 포트 닫기 및 내부 데이터 수신 스레드 종료
```


<br>

---

<h3><i>CodingRider</i> for python</H3>

 1. **Intro**
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Control](examples_01_control.md)
 6. [Examples - Sensor](examples_02_sensor.md)
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Vibrator](examples_05_vibrator.md)
10. [Examples - Light](examples_06_light.md)
11. [Examples - Input](examples_07_input.md)
12. [Examples - Information](examples_08_information.md)
<br>

[Index](index.md)
