**[*petrone* for python](index.md)** / **Examples** / **Information**

Modified : 2018.11.26

---

* Kramdown table of contents
{:toc .toc}


<br>


<a name="UpdateInformation_petrone_link"></a>
## PETRONE LINK 모듈의 펌웨어 정보 요청

페트론 링크 모듈의 펌웨어 정보를 요청합니다.

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
    drone.open()
    
    # 장치에 연결된 경우 정보 요청
    if drone.isOpen():

        # 펌웨어 정보 요청
        print("Request information of PETRONE LINK firmware.")
        drone.sendUpdateLookupTarget(DeviceType.Link)
        sleep(2)

    drone.close()
```

<br>

실행 결과는 다음과 같습니다.

```py
[     0.120] Connected.(COM44)
Request information of PETRONE LINK firmware.
0A 55 90 04 03 00 00 00 7E DC
FF
FF
0A 55 91 0B 00 03 00 00 00 07 11 00 10 0A 15 F9 C1
[     0.130] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0xC1F9]
eventUpdateInformation() / ModeUpdate.None_ / DeviceType.Link / ImageType.ImageSingle / Ver:17 / 2016.10.21
[     2.133] Closing serial port.
```


<br>
<br>


<a name="UpdateInformation_short"></a>
## 드론의 펌웨어 정보 요청(짧은 코드)

마지막으로 검색된 시리얼 포트에 연결하여 가장 신호 세기가 강한 드론에 자동으로 연결 후 펌웨어 정보를 요청합니다.

시리얼 포트와 드론의 이름을 지정할 수도 있습니다.

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
<br>



<a name="UpdateInformation_long"></a>
## 드론의 펌웨어 정보 요청(긴 코드)

마지막으로 검색된 시리얼 포트에 연결하여 가장 신호 세기가 강한 드론에 연결 후 펌웨어 정보를 요청합니다.

PETRONE LINK 내부에서 발생하는 이벤트에 대한 로그를 모두 확인할 수 있습니다.

```py
from time import sleep

from petrone.drone import *
from petrone.protocol import *
from petrone.system import *


devices = []


def eventLinkState(data):
    print("eventLinkState() / {0} / {1}".format(data.modeLink, data.modeLinkBroadcast))


def eventLinkEvent(data):
    print("eventLinkEvent() / {0} / {1}".format(data.eventLink, data.eventResult))


def eventLinkEventAddress(data):
    print("eventLinkEventAddress() / {0} / {1} / {2}".format(data.eventLink, data.eventResult, convertByteArrayToString(data.address)))


def eventLinkRssi(data):
    print("eventLinkRssi() / {0}".format(data.rssi))


def eventLinkDiscoveredDevice(data):
    print("eventLinkDiscoveredDevice() / {0} / {1} / {2} / {3}".format(data.index, convertByteArrayToString(data.address), data.name, data.rssi))
    global devices
    devices.append(data)


def eventState(data):
    print("eventState() / {0} / {1} / {2} / {3} / {4} / {5} / {6}".format(data.modeVehicle, data.modeSystem, data.modeFlight, data.modeDrive, data.sensorOrientation, data.headless, data.battery))


def eventUpdateInformation(data):
    print("eventUpdateInformation() / {0} / {1} / {2} / {3} / {4} / {5} / {6}".format(data.modeUpdate, data.deviceType, data.imageType, data.version, data.year, data.month, data.day))


if __name__ == '__main__':
    
    # Drone의 객체 생성
    drone = Drone(True, True, True, True, True)

    # 이벤트 핸들링 함수 등록
    print("Connect callback function.")
    drone.setEventHandler(DataType.LinkState, eventLinkState)
    drone.setEventHandler(DataType.LinkEvent, eventLinkEvent)
    drone.setEventHandler(DataType.LinkEventAddress, eventLinkEventAddress)
    drone.setEventHandler(DataType.LinkRssi, eventLinkRssi)
    drone.setEventHandler(DataType.LinkDiscoveredDevice, eventLinkDiscoveredDevice)
    drone.setEventHandler(DataType.State, eventState)
    drone.setEventHandler(DataType.UpdateInformation, eventUpdateInformation)

    # 시리얼 포트 연결
    drone.open()

    # 시스템 리셋
    #drone.sendLinkSystemReset()
    #sleep(3)

    # ModeBroadcast 모드를 변경
    drone.sendLinkModeBroadcast(ModeLinkBroadcast.Active)
    #drone.sendLinkModeBroadcast(ModeLinkBroadcast.Passive)
    sleep(0.2)

    # LINK 펌웨어 정보 요청
    print("Request firmware information.")
    drone.sendUpdateLookupTarget(DeviceType.Link)
    sleep(1)

    # BLE 장치 검색 시작
    print("Discover start.")
    drone.sendLinkDiscoverStart()
    sleep(3)

    length = len(devices)

    if length > 0:
        closestDevice = devices[0]

        # BLE 장치가 2개 이상 검색된 경우 가장 가까운 장치를 선택
        if len(devices) > 1:
            for i in range(len(devices)):
                if closestDevice.rssi < devices[i].rssi:
                    closestDevice = devices[i]

        # 연결
        print("Connect device. {0}".format(closestDevice.index))
        drone.sendLinkConnect(closestDevice.index)
        sleep(5)

        # 메인 펌웨어 정보 요청
        print("Request DroneMain.")
        drone.sendUpdateLookupTarget(DeviceType.DroneMain)
        sleep(3)

        # 통신 펌웨어 정보 요청
        print("Request DroneSub.")
        drone.sendUpdateLookupTarget(DeviceType.DroneSub)
        sleep(3)

        # State 정보 요청
        print("Request state.")
        drone.sendRequest(DataType.State)
        sleep(2)

        # 장치 연결 해제
        print("Disconnect device.")
        drone.sendLinkDisconnect()
        sleep(3)

    drone.close()
```

<br>

실행 결과는 다음과 같습니다.

```py
Connect callback function.
[     0.080] Connected.(COM40)]
0A 55 11 02 E0 02 83 33
0A 55 E0 02 02 02 AA AC
[     0.086] Success / Receiver / Section.End / Receive complete / DataType.LinkState / [receive: 0xACAA]
eventLinkState() / ModeLink.Ready / ModeLinkBroadcast.Active
Request firmware information.
0A 55 90 04 03 00 00 00 7E DC
0A 55 91 0B 00 03 00 00 00 07 12 00 11 09 1D 40 CC
[     0.292] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0xCC40]
eventUpdateInformation() / ModeUpdate.None_ / DeviceType.Link / ImageType.ImageSingle / 18 / 17 / 9 / 29
Discover start.
0A 55 11 02 E2 00 A3 75
0A 55 E1 02 04 00 FA 50
[     1.291] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x50FA]
eventLinkEvent() / EventLink.ScanStop / 0
[     1.291] EventLink.ScanStop]
0A 55 E1 02 03 00 6D C9
[     1.300] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xC96D]
eventLinkEvent() / EventLink.Scanning / 0
[     1.301] EventLink.Scanning]
0A 55 E4 1C 00 A8 B5 60 78 D5 A4 50 45 54 52 4F 4E 45 20 36 35 30 34 00 00 00 00 00 00 00 00 D1 28 24
[     1.462] Success / Receiver / Section.End / Receive complete / DataType.LinkDiscoveredDevice / [receive: 0x2428]
eventLinkDiscoveredDevice() / 0 / A8 B5 60 78 D5 A4  / PETRONE 6504 / -47
[     1.463] LinkDiscoveredDevice / 0 / A8 B5 60 78 D5 A4  / PETRONE 6504 / -47]
0A 55 E1 02 04 00 FA 50
[     2.893] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x50FA]
eventLinkEvent() / EventLink.ScanStop / 0
[     2.894] EventLink.ScanStop]
Connect device. 0
0A 55 11 02 E4 00 05 DF
0A 55 E0 02 03 02 9B 9F
[     4.296] Success / Receiver / Section.End / Receive complete / DataType.LinkState / [receive: 0x9F9B]
eventLinkState() / ModeLink.Connecting / ModeLinkBroadcast.Active
0A 55 E2 08 06 00 A8 B5 60 78 D5 A4 59 0E
[     4.299] Success / Receiver / Section.End / Receive complete / DataType.LinkEventAddress / [receive: 0x0E59]
eventLinkEventAddress() / EventLink.Connecting / 0 / A8 B5 60 78 D5 A4
[     4.300] EventLink.Connecting]
0A 55 E1 02 0B 00 C4 40
[     4.473] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x40C4]
eventLinkEvent() / EventLink.PairingStart / 0
[     4.473] EventLink.PairingStart]
0A 55 E0 02 04 02 0C 06
[     4.476] Success / Receiver / Section.End / Receive complete / DataType.LinkState / [receive: 0x060C]
eventLinkState() / ModeLink.Connected / ModeLinkBroadcast.Active
0A 55 E2 08 07 00 A8 B5 60 78 D5 A4 8A 49
[     4.480] Success / Receiver / Section.End / Receive complete / DataType.LinkEventAddress / [receive: 0x498A]
eventLinkEventAddress() / EventLink.Connected / 0 / A8 B5 60 78 D5 A4
[     4.481] EventLink.Connected]
0A 55 E1 02 0D 05 C7 BA
[     4.625] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xBAC7]
eventLinkEvent() / EventLink.PairingFailed / 5
[     4.625] EventLink.PairingFailed]
0A 55 E1 02 0F 01 21 9C
[     4.827] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x9C21]
eventLinkEvent() / EventLink.LookupAttribute / 1
[     4.828] EventLink.LookupAttribute]
0A 55 E1 02 0F 01 21 9C
[     5.027] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x9C21]
eventLinkEvent() / EventLink.LookupAttribute / 1
[     5.028] EventLink.LookupAttribute]
0A 55 E1 02 12 00 2F F9
[     5.030] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xF92F]
eventLinkEvent() / EventLink.DiscoverService / 0
[     5.031] EventLink.DiscoverService]
0A 55 E1 02 1B 00 B7 43
[     5.229] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x43B7]
eventLinkEvent() / EventLink.GapLinkParamUpdate / 0
[     5.229] EventLink.GapLinkParamUpdate]
0A 55 E1 02 0F 02 42 AC
[     5.232] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xAC42]
eventLinkEvent() / EventLink.LookupAttribute / 2
[     5.232] EventLink.LookupAttribute]
0A 55 E1 02 14 12 FA 61
[     5.234] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x61FA]
eventLinkEvent() / EventLink.DiscoverCharacteristicDroneData / 18
[     5.235] EventLink.DiscoverCharacteristicDroneData]
0A 55 E1 02 0F 02 42 AC
[     5.340] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xAC42]
eventLinkEvent() / EventLink.LookupAttribute / 2
[     5.341] EventLink.LookupAttribute]
0A 55 E1 02 15 16 4F 12
[     5.343] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x124F]
eventLinkEvent() / EventLink.DiscoverCharacteristicDroneConfig / 22
[     5.343] EventLink.DiscoverCharacteristicDroneConfig]
0A 55 E1 02 0F 02 42 AC
[     5.364] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xAC42]
eventLinkEvent() / EventLink.LookupAttribute / 2
[     5.365] EventLink.LookupAttribute]
0A 55 E1 02 13 00 1E CA
[     5.367] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xCA1E]
eventLinkEvent() / EventLink.DiscoverCharacteristic / 0
[     5.368] EventLink.DiscoverCharacteristic]
0A 55 E1 02 0F 03 63 BC
[     5.390] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xBC63]
eventLinkEvent() / EventLink.LookupAttribute / 3
[     5.391] EventLink.LookupAttribute]
0A 55 E1 02 0F 03 63 BC
[     5.414] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xBC63]
eventLinkEvent() / EventLink.LookupAttribute / 3
[     5.415] EventLink.LookupAttribute]
0A 55 E1 02 0F 03 63 BC
[     5.417] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xBC63]
eventLinkEvent() / EventLink.LookupAttribute / 3
[     5.418] EventLink.LookupAttribute]
0A 55 E1 02 20 00 D8 9A
[     5.420] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x9AD8]
eventLinkEvent() / EventLink.SetNotify / 0
[     5.421] EventLink.SetNotify]
0A 55 E1 02 17 00 DA 06
[     5.423] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x06DA]
eventLinkEvent() / EventLink.DiscoverCCCD / 0
[     5.423] EventLink.DiscoverCCCD]
0A 55 E1 02 18 00 E4 16
[     5.426] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x16E4]
eventLinkEvent() / EventLink.ReadyToControl / 0
[     5.426] EventLink.ReadyToControl]
0A 55 E1 02 1F 00 73 8F
[     5.439] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x8F73]
eventLinkEvent() / EventLink.RspWriteSuccess / 0
[     5.441] EventLink.RspWriteSuccess]
0A 55 E1 02 21 00 E9 A9
[     5.519] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xA9E9]
eventLinkEvent() / EventLink.Write / 0
[     5.519] EventLink.Write]
0A 55 E1 02 1F 00 73 8F
[     5.539] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x8F73]
eventLinkEvent() / EventLink.RspWriteSuccess / 0
[     5.540] EventLink.RspWriteSuccess]
0A 55 E1 02 21 00 E9 A9
[     5.619] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xA9E9]
eventLinkEvent() / EventLink.Write / 0
[     5.620] EventLink.Write]
0A 55 E1 02 1F 00 73 8F
[     5.638] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x8F73]
eventLinkEvent() / EventLink.RspWriteSuccess / 0
[     5.639] EventLink.RspWriteSuccess]
0A 55 E1 02 21 00 E9 A9
[     5.723] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xA9E9]
eventLinkEvent() / EventLink.Write / 0
[     5.724] EventLink.Write]
0A 55 E1 02 1F 00 73 8F
[     5.738] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x8F73]
eventLinkEvent() / EventLink.RspWriteSuccess / 0
[     5.739] EventLink.RspWriteSuccess]
Request DroneMain.
0A 55 90 04 01 00 00 00 16 31
0A 55 E1 02 21 00 E9 A9
[     9.294] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xA9E9]
eventLinkEvent() / EventLink.Write / 0
[     9.295] EventLink.Write]
0A 55 E1 02 1F 00 73 8F
[     9.315] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x8F73]
eventLinkEvent() / EventLink.RspWriteSuccess / 0
[     9.316] EventLink.RspWriteSuccess]
0A 55 91 0B 01 01 00 00 00 01 27 00 11 06 08 71 3A
[     9.321] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0x3A71]
eventUpdateInformation() / ModeUpdate.Ready / DeviceType.DroneMain / ImageType.ImageA / 39 / 17 / 6 / 8
Request DroneSub.
0A 55 90 04 02 00 00 00 CA AA
0A 55 E1 02 21 00 E9 A9
[    12.298] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xA9E9]
eventLinkEvent() / EventLink.Write / 0
[    12.299] EventLink.Write]
0A 55 91 0B 01 02 00 00 00 01 12 00 10 07 0E C0 C0
[    12.331] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0xC0C0]
eventUpdateInformation() / ModeUpdate.Ready / DeviceType.DroneSub / ImageType.ImageA / 18 / 16 / 7 / 14
0A 55 E1 02 1F 00 73 8F
[    12.333] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x8F73]
eventLinkEvent() / EventLink.RspWriteSuccess / 0
[    12.334] EventLink.RspWriteSuccess]
Request state.
0A 55 04 01 31 83 C9
0A 55 E1 02 21 00 E9 A9
[    15.300] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0xA9E9]
eventLinkEvent() / EventLink.Write / 0
[    15.301] EventLink.Write]
0A 55 E1 02 1F 00 73 8F
[    15.328] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x8F73]
eventLinkEvent() / EventLink.RspWriteSuccess / 0
[    15.328] EventLink.RspWriteSuccess]
0A 55 31 07 10 04 01 01 01 02 64 76 48
[    15.332] Success / Receiver / Section.End / Receive complete / DataType.State / [receive: 0x4876]
eventState() / ModeVehicle.FlightGuard / ModeSystem.Running / ModeFlight.Ready / ModeDrive.Ready / SensorOrientation.Normal / Headless.Normal / 100
Disconnect device.
0A 55 11 02 E5 00 34 EC
0A 55 E0 02 05 02 3D 35
[    17.299] Success / Receiver / Section.End / Receive complete / DataType.LinkState / [receive: 0x353D]
eventLinkState() / ModeLink.Disconnecting / ModeLinkBroadcast.Active
0A 55 E0 02 02 02 AA AC
[    17.329] Success / Receiver / Section.End / Receive complete / DataType.LinkState / [receive: 0xACAA]
eventLinkState() / ModeLink.Ready / ModeLinkBroadcast.Active
0A 55 E1 02 1A 16 71 02
[    17.331] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x0271]
eventLinkEvent() / EventLink.Disconnected / 22
[    17.332] EventLink.Disconnected]
[    20.295] Closing serial port.]
```


<br>


---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. **Examples - Information**
 6. [Examples - Imu](examples_02_imu.md)
 7. [Examples - Test Flight](examples_03_test_flight.md)
 8. [Examples - Light](examples_04_light.md)

<br>

[Index](index.md)
