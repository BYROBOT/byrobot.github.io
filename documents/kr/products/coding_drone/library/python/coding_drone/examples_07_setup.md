**[*CodingDrone* for python](index.md)** / **Examples** / **Setup**

Modified : 2024.6.13

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="ModeControlFlight"></a>
## 드론 비행 제어 모드를 변경 후 확인

```py
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


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

- [State](04_protocol.md#State)
- [sendModeControlFlight()](05_drone.md#sendModeControlFlight)
- [sendRequest()](05_drone.md#sendRequest)


<br>
<br>


<a name="Headless"></a>
## 드론 Headless 설정 변경 후 확인

```py
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


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

- [State](04_protocol.md#State)
- [sendHeadless()](05_drone.md#sendHeadless)
- [sendRequest()](05_drone.md#sendRequest)


<br>
<br>




<a name="Trim"></a>
## 드론 Trim 설정 변경 후 확인

```py
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


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

- [TrimFlight](04_protocol.md#TrimFlight)
- [sendTrimFlight()](05_drone.md#sendTrimFlight)
- [sendRequest()](05_drone.md#sendRequest)


<br>

---

<h3><i>CodingDrone</i> for python</H3>

 1. [Intro](01_intro.md)
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
12. **Examples - Setup**
13. [Examples - Buzzer](examples_08_buzzer.md)
14. [Examples - Vibrator](examples_09_vibrator.md)
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
