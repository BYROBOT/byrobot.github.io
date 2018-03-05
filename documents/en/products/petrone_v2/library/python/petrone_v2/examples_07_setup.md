**[*petrone_v2* for python](index.md)** / **Examples** / **Setup**

Modified : 2017.10.27

---

<br>


## <a name="ModeVehicle">드론 모드를 변경 후 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventState(state):
    print("{0}".format(state.modeVehicle))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.State, eventState)


    # 드론을 자동차 모드로 변경
    drone.sendModeVehicle(ModeVehicle.Drive)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.State)
    sleep(0.1)


    # 드론을 비행 모드로 변경
    drone.sendModeVehicle(ModeVehicle.FlightGuard)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.State)
    sleep(0.1)


    drone.close()
```

- [State](03_protocol.md#State)
- [sendModeVehicle()](04_drone.md#sendModeVehicle)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="Headless">드론 Headless 설정 변경 후 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventState(state):
    print("{0}".format(state.headless))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


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


## <a name="Trim">Trim 변경 테스트</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventTrimFlight(trimFlight):
    print("{0}, {1}, {2}, {3}".format(trimFlight.roll, trimFlight.pitch, trimFlight.yaw, trimFlight.throttle))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.TrimFlight, eventTrimFlight)


    # 트림 설정 변경
    print("Roll Increase")
    drone.sendTrim(Trim.RollIncrease)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimFlight)
    sleep(0.2)


    # 트림 설정 변경
    print("Pitch Increase")
    drone.sendTrim(Trim.PitchIncrease)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimFlight)
    sleep(0.2)


    # 트림 설정 변경
    print("Pitch Decrease")
    drone.sendTrim(Trim.PitchDecrease)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimFlight)
    sleep(0.2)


    # 트림 설정 변경
    print("Trim Reset")
    drone.sendTrim(Trim.Reset)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimFlight)
    sleep(0.2)


    drone.close()
```

- [Trim](02_system.md#Trim)
- [sendTrim()](04_drone.md#sendTrim)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="TrimFlight">드론 TrimFlight 설정 변경 후 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventTrimFlight(trimFlight):
    print("{0}, {1}, {2}, {3}".format(trimFlight.roll, trimFlight.pitch, trimFlight.yaw, trimFlight.throttle))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.TrimFlight, eventTrimFlight)


    # 드론 비행 트림 설정 변경
    drone.sendTrimFlight(10, 20, 30, 40)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimFlight)
    sleep(0.1)


    # 드론 비행 트림 설정 변경
    drone.sendTrimFlight(0, 0, 0, 0)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimFlight)
    sleep(0.1)


    drone.close()
```

- [TrimFlight](03_protocol.md#TrimFlight)
- [sendTrimFlight()](04_drone.md#sendTrimFlight)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="TrimDrive">드론 TrimDrive 설정 변경 후 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventTrimDrive(trimDrive):
    print("{0}, {1}".format(trimDrive.wheel, trimDrive.accel))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.TrimDrive, eventTrimDrive)


    # 드론 자동차 트림 설정 변경
    drone.sendTrimDrive(10, 20)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimDrive)
    sleep(0.1)


    # 드론 자동차 트림 설정 변경
    drone.sendTrimDrive(0, 0)
    sleep(0.01)

    # 변경 사항을 확인
    drone.sendRequest(DeviceType.Drone, DataType.TrimDrive)
    sleep(0.1)


    drone.close()
```

- [TrimDrive](03_protocol.md#TrimDrive)
- [sendTrimDrive()](04_drone.md#sendTrimDrive)
- [sendRequest()](04_drone.md#sendRequest)


<br>

---

<h3><i>petrone_v2</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Ping](examples_01_ping.md)
 6. [Examples - Information](examples_02_information.md)
 7. [Examples - Pairing](examples_03_pairing.md)
 8. [Examples - Control](examples_04_control.md)
 9. [Examples - Sensor](examples_05_sensor.md)
10. [Examples - Motor](examples_06_motor.md)
11. **Examples - Setup**
12. [Examples - Buzzer](examples_08_buzzer.md)
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
