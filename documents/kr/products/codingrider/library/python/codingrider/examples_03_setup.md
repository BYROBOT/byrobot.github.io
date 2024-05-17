**[*CodingRider* for python](index.md)** / **Examples** / **Setup**

Modified : 2024.5.17

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="ModeControlFlight"></a>
## 드론 비행 제어 모드를 변경 후 확인

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


def eventState(state):
    print("{0}".format(state.modeControlFlight))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.State, eventState)


    # 비행 제어 모드를 ModeControlFlight.Position 으로 변경
    drone.sendModeControlFlight(ModeControlFlight.Position)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.State)
    sleep(0.1)


    # 비행 제어 모드를 ModeControlFlight.Attitude 으로 변경
    drone.sendModeControlFlight(ModeControlFlight.Attitude)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.State)
    sleep(0.1)


    drone.close()
```

- [State](03_protocol.md#State)
- [sendModeControlFlight()](04_drone.md#sendModeControlFlight)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


<a name="Headless"></a>
## 드론 Headless 설정 변경 후 확인

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


def eventState(state):
    print("{0}".format(state.headless))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.State, eventState)


    # 드론을 Headless 설정을 Headless 모드로 변경
    drone.sendHeadless(Headless.Headless)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.State)
    sleep(0.1)


    # 드론을 Headless 설정을 Normal 모드로 변경
    drone.sendHeadless(Headless.Normal)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.State)
    sleep(0.1)


    drone.close()
```

- [State](03_protocol.md#State)
- [sendHeadless()](04_drone.md#sendHeadless)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


<a name="Trim"></a>
## 드론 Trim 설정 변경 후 확인

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


def eventTrim(trim):
    print("{0}, {1}, {2}, {3}".format(trim.roll, trim.pitch, trim.yaw, trim.throttle))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Trim, eventTrim)


    # 드론 비행 트림 설정 변경
    drone.sendTrim(10, 20, 30, 40)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.1)


    # 드론 비행 트림 설정 변경
    drone.sendTrim(0, 0, 0, 0)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.1)


    drone.close()
```

- [TrimFlight](03_protocol.md#TrimFlight)
- [sendTrimFlight()](04_drone.md#sendTrimFlight)
- [sendRequest()](04_drone.md#sendRequest)


<br>

---

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Control](examples_01_control.md)
 6. [Examples - Sensor](examples_02_sensor.md)
 7. **Examples - Setup**
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Vibrator](examples_05_vibrator.md)
10. [Examples - Light](examples_06_light.md)
11. [Examples - Input](examples_07_input.md)
12. [Examples - Information](examples_08_information.md)
<br>

[Index](index.md)
