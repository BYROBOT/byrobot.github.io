**[*petrone_v2* for python](index.md)** / **Intro**

Modified : 2018.3.5

---

* Kramdown table of contents
{:toc .toc}

<br>


# 시작하기 전에

아직 Python을 설치하지 않으셨다면 다음 문서를 먼저 확인하시기 바랍니다.

[Install Python 3 on macOS](/documents/kr/manual/install_python_3_on_mac_os/)


<br>
<br>


# 1. *petrone_v2* for python 소개

***petrone_v2* for python**은 python에서 ***E-DRONE***를 쉽게 사용할 수 있도록 도와주는 라이브러리입니다.

[https://pypi.python.org/pypi/petrone_v2](https://pypi.python.org/pypi/petrone_v2)


<br>
<br>


# 2. 설치

아래의 명령을 실행하시면 *petrone_v2*가 설치됩니다.

```
> pip install petrone_v2
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 install petrone_v2
```

<div align="center">
    <img src="../01_intro_1_install_petrone_v2.png" alt="install_petrone_v2">
</div>


<br>

최신 버젼이 설치되지 않는다면 아래의 명령을 사용하시기 바랍니다.

```
> pip --no-cache-dir install petrone_v2
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 --no-cache-dir install petrone_v2
```


<br>
<br>


# 3. 삭제

아래의 명령을 실행하시면 *petrone_v2*가 삭제됩니다.

```
> pip uninstall petrone_v2
```

**macOS** 에서는 아래와 같이 실행하시기 바랍니다.

```
> pip3 uninstall petrone_v2
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


# 6. macOS에서 Visual Studio Code를 사용하여 예제 실행하기

아래는 Visual Studio Code 처음 실행 화면입니다.

<div align="center">
    <img src="../01_intro_2_run_example_1.png" alt="run_example_1">
</div>

여기에서 화면 좌측 상단의 <b>새 파일</b>을 선택하시면 빈 파일이 열립니다. 빈 파일에 아래의 코드를 복사해서 붙여 넣으시면 됩니다.
<br>
<br>

```python
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventInformation(information):
    print("eventInformation()")
    print("{0} / 0x{0:08X}".format(information.version.v))
    print("{0}.{1}.{2}.{3}".format(
        information.version.major,
        information.version.minor,
        information.version.stage.name,
        information.version.build))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Information, eventInformation)

    # Information 정보 요청
    drone.sendRequest(DeviceType.Controller, DataType.Information)
    sleep(0.1)

    drone.close()
```

예제는 아래의 소스에서 포트 이름을 지운 것입니다.

[조종기의 펌웨어 정보 요청(이벤트 함수 등록)](https://byrobot.github.io/documents/kr/products/petrone_v2/library/python/petrone_v2/examples_02_information/#Class_Information)

<br>

<div align="center">
    <img src="../01_intro_2_run_example_2.png" alt="run_example_2">
</div>

예제 코드를 붙여 넣은 화면입니다.
<br>
<br>


<div align="center">
    <img src="../01_intro_2_run_example_3.png" alt="run_example_3">
</div>

파일을 저장해야 실행할 수 있습니다. 메뉴에서 <b>파일</b> -> <b>저장</b>을 선택합니다.
<br>
<br>


<div align="center">
    <img src="../01_intro_2_run_example_4.png" alt="run_example_4">
</div>

여기에서는 <b>사용자/byrobot/Works</b> 폴더에 <b>test_sendrequest.py</b> 라는 이름으로 저장하였습니다.
<br>
<br>


<div align="center">
    <img src="../01_intro_2_run_example_5.png" alt="run_example_5">
</div>

파일을 저장하자 코드 문법이 강조되었습니다.
<br>
<br>


<div align="center">
    <img src="../01_intro_2_run_example_6.png" alt="run_example_6">
</div>

화면의 빈 공간에 오른클릭을 하면 위와 같은 메뉴를 볼 수 있습니다. 예제를 실행하려면 여기에서 <b>Run Python File in Terminal</b>를 선택하면 됩니다.
<br>
<br>


<div align="center">
    <img src="../01_intro_2_run_example_7.png" alt="run_example_7">
</div>

E-DRONE 조종기가 맥에 연결되어 있다면 위와 비슷한 결과를 확인할 수 있습니다. 만약 조종기가 연결되지 않았거나 연결에 문제가 있다면 아무런 결과도 표시하지 않습니다.
<br>

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
