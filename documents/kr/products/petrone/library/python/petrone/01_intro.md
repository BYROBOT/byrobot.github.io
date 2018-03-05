**[*petrone* for python](index.md)** / **Intro**

Modified : 2017.09.29

---

* Kramdown table of contents
{:toc .toc}

<br>


# 시작하기 전에

아직 Python을 설치하지 않으셨다면 다음 문서를 먼저 확인하시기 바랍니다.

[Install Python 3 on macOS](/documents/kr/manual/install_python_3_on_mac_os/)


<br>
<br>


# 1. *petrone* for python 소개

***petrone* for python**은 python에서 ***PETRONE LINK***를 통해 ***PETRONE***을 쉽게 사용할 수 있도록 도와주는 라이브러리입니다.

[https://pypi.python.org/pypi/petrone](https://pypi.python.org/pypi/petrone)


<br>
<br>


# 2. 설치

아래의 명령을 실행하시면 *petrone*이 설치됩니다.

```
> pip install petrone
```

<br>

최신 버젼이 설치되지 않는다면 아래의 명령을 사용하시기 바랍니다.

```
> pip --no-cache-dir install petrone
```


<br>
<br>


# 3. 삭제

아래의 명령을 실행하시면 *petrone*이 삭제됩니다.

```
> pip uninstall petrone
```


<br>
<br>


# 4. 시리얼 포트 검색


Drone 클래스 내부에서 pyserial을 사용하여 시리얼 포트에 연결합니다. 시리얼 포트에 연결하려면 장치 이름을 알고 있어야 합니다. 이 때 필요한 것이 컴퓨터에 연결된 시리얼 통신 장치들을 검색할 수 있는 명령입니다. 이 명령은 **pyserial**에서 제공하고 있습니다.

(**pyserial**은 *petrone*를 설치한 경우 함께 설치됩니다.)

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

일반적인 진행 순서는 '**드론 객체 생성**' -> '**시리얼 포트 연결**' -> '**PETRONE 검색**' ->  '**PETRONE 연결**' -> '**PETRONE 사용**' ->  '**PETRONE 연결 해제**' ->  '**시리얼 포트 닫기**' 입니다.

```py
from time import sleep

from petrone.drone import *
from petrone.protocol import *
from petrone.system import *


def eventUpdateInformation(data):
    print("eventUpdateInformation() / {0} / {1} / {2} / Ver:{3} / 20{4:02}.{5}.{6}".format(data.modeUpdate, data.deviceType, data.imageType, data.version, data.year, data.month, data.day))


if __name__ == '__main__':
    
    # Drone의 객체 생성
    drone = Drone(True, True, True, True, True)

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.UpdateInformation, eventUpdateInformation)

    # 장치에 연결
    drone.connect()    # 마지막으로 연결된 시리얼 포트와 검색된 장치(페트론) 중 가장 신호가 강한 장치에 연결
    #drone.connect(portName="COM14", deviceName="PETRONE 6504")      # 시리얼 포트와 장치(페트론)를 지정하여 연결
    sleep(1)
    
    # 장치에 연결된 경우 정보 요청
    if drone.isConnected():

        # 장치 메인 펌웨어 정보 요청
        print("Request information of main firmware.")
        drone.sendUpdateLookupTarget(DeviceType.DroneMain)
        sleep(2)

        # 장치 통신 펌웨어 정보 요청
        print("Request information of sub firmware.")
        drone.sendUpdateLookupTarget(DeviceType.DroneSub)
        sleep(2)

        # 장치 연결 해제
        print("Disconnect device.")
        drone.sendLinkDisconnect()
        sleep(0.2)

    drone.close()
```

<br>

실행 결과는 다음과 같습니다.

```py
[     0.012] Connected.(COM40)]
0A 55 11 02 E0 03 A2 23
0A 55 11 02 E2 00 A3 75
0A 55 E1 02 04 00 FA 50
[     0.220] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x50FA]
[     0.220] EventLink.ScanStop]
0A 55 E4 1C 00 A8 B5 60 78 D5 A4 50 45 54 52 4F 4E 45 20 36 35 30 34 00 00 00 00 00 00 00 00 D6 CF 54
[     0.283] Success / Receiver / Section.End / Receive complete / DataType.LinkDiscoveredDevice / [receive: 0x54CF]
[     0.283] LinkDiscoveredDevice / 0 / A8 B5 60 78 D5 A4  / PETRONE 6504 / -42]
0A 55 E1 02 04 00 FA 50
[     1.825] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x50FA]
[     1.825] EventLink.ScanStop]
0A 55 11 02 E4 00 05 DF
0A 55 E2 08 07 00 A8 B5 60 78 D5 A4 8A 49
[     2.436] Success / Receiver / Section.End / Receive complete / DataType.LinkEventAddress / [receive: 0x498A]
[     2.436] EventLink.Connected]
0A 55 E1 02 18 00 E4 16
[     3.400] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x16E4]
[     3.401] EventLink.ReadyToControl]
Request information of main firmware.
0A 55 90 04 01 00 00 00 16 31
0A 55 91 0B 01 01 00 00 00 01 27 00 11 06 08 71 3A
[     4.754] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0x3A71]
eventUpdateInformation() / ModeUpdate.Ready / DeviceType.DroneMain / ImageType.ImageA / Ver:39 / 2017.6.8
Request information of sub firmware.
0A 55 90 04 02 00 00 00 CA AA
0A 55 91 0B 01 02 00 00 00 01 12 00 10 07 0E C0 C0
[     6.752] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0xC0C0]
eventUpdateInformation() / ModeUpdate.Ready / DeviceType.DroneSub / ImageType.ImageA / Ver:18 / 2016.7.14
Disconnect device.
0A 55 11 02 E5 00 34 EC
0A 55 E1 02 1A 16 71 02
[     8.752] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x0271]
[     8.752] EventLink.Disconnected]
[     8.923] Closing serial port.]
```


<br>

---

<h3><i>petrone</i> for python</H3>

 1. **Intro**
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)

<br>

[Index](index.md)
