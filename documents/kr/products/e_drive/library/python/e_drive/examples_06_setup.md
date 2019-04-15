**[*e_drive* for python](index.md)** / **Examples** / **Setup**

Modified : 2019.4.15

---

<br>


## <a name="ModeControlFlight">드론 비행 제어 모드를 변경 후 확인</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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


## <a name="Headless">드론 Headless 설정 변경 후 확인</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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


## <a name="TrimIncDec">TrimIncDec 변경 테스트</a>

* 예제가 정상적으로 동작하지 않습니다. 추후 수정하겠습니다.

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


def eventTrim(trim):
    print("{0}, {1}, {2}, {3}".format(trim.roll, trim.pitch, trim.yaw, trim.throttle))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Trim, eventTrim)


    # 트림 설정 변경
    print("Roll Increase")
    drone.sendTrimIncDec(TrimIncDec.RollIncrease)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.2)


    # 트림 설정 변경
    print("Pitch Increase")
    drone.sendTrimIncDec(TrimIncDec.PitchIncrease)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.2)


    # 트림 설정 변경
    print("Pitch Decrease")
    drone.sendTrimIncDec(TrimIncDec.PitchDecrease)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.2)


    # 트림 설정 변경
    print("Trim Reset")
    drone.sendTrimIncDec(TrimIncDec.Reset)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.Trim)
    sleep(0.2)


    drone.close()
```

- [Trim](02_system.md#Trim)
- [sendTrim()](04_drone.md#sendTrim)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="Trim">드론 Trim 설정 변경 후 확인</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. [Drone](05_drone.md)
 6. [Examples - Ping](examples_01_ping.md)
 7. [Examples - Information](examples_02_information.md)
 8. [Examples - Control](examples_03_control.md)
 9. [Examples - Sensor](examples_04_sensor.md)
10. [Examples - Motor](examples_05_motor.md)
11. **Examples - Setup**
12. [Examples - Buzzer](examples_07_buzzer.md)
13. [Examples - Light](examples_08_light.md)
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
