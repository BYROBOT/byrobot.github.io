**[*e_drone* for python](index.md)** / **Examples** / **Setup**

Modified : 2022.1.14

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="ModeControlFlight"></a>
## 드론 비행 제어 모드를 변경 후 확인

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_state(state):
    print("{0}".format(state.mode_control_flight))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.STATE, event_state)


    # 비행 제어 모드를 ModeControlFlight.Attitude 으로 변경
    drone.send_mode_control_flight(ModeControlFlight.ATTITUDE)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.STATE)
    sleep(0.1)


    # 비행 제어 모드를 ModeControlFlight.POSITION 으로 변경
    drone.send_mode_control_flight(ModeControlFlight.POSITION)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.STATE)
    sleep(0.1)


    drone.close()
```

- [State](04_protocol.md#State)
- [send_mode_control_flight()](05_drone.md#send_mode_control_flight)
- [send_request()](05_drone.md#send_request)


<br>
<br>


<a name="Speed"></a>
## 드론 Speed 설정 변경 후 확인

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_state(state):
    print("Speed: {0}".format(state.control_speed))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.STATE, event_state)


    # 제어 속도를 1로 변경(1, 2, 3 중에 선택)
    drone.send_command(DeviceType.DRONE, CommandType.CONTROL_SPEED, 1)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.STATE)
    sleep(0.1)


    # 제어 속도를 2로 변경(1, 2, 3 중에 선택)
    drone.send_command(DeviceType.DRONE, CommandType.CONTROL_SPEED, 2)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.STATE)
    sleep(0.1)


    # 제어 속도를 3으로 변경(1, 2, 3 중에 선택)
    drone.send_command(DeviceType.DRONE, CommandType.CONTROL_SPEED, 3)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.STATE)
    sleep(0.1)


    drone.close()
```

- [State](04_protocol.md#State)
- [send_headless()](05_drone.md#send_command)
- [send_request()](05_drone.md#send_request)





<a name="Headless"></a>
## 드론 Headless 설정 변경 후 확인

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_state(state):
    print("{0}".format(state.headless))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.STATE, event_state)


    # 드론을 Headless 설정을 Headless 모드로 변경
    drone.send_headless(Headless.HEADLESS)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.STATE)
    sleep(0.1)


    # 드론을 Headless 설정을 Normal 모드로 변경
    drone.send_headless(Headless.NORMAL)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.STATE)
    sleep(0.1)


    drone.close()
```

- [State](04_protocol.md#State)
- [send_headless()](05_drone.md#send_headless)
- [send_request()](05_drone.md#send_request)


<br>
<br>


<a name="Trim"></a>
## 드론 Trim 설정 변경 후 확인

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_trim(trim):
    print("{0}, {1}, {2}, {3}".format(trim.roll, trim.pitch, trim.yaw, trim.throttle))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.TRIM, event_trim)


    # 드론 비행 트림 설정 변경
    drone.send_trim(10, 20, 30, 40)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.TRIM)
    sleep(0.1)


    # 드론 비행 트림 설정 변경
    drone.send_trim(0, 0, 0, 0)
    sleep(0.01)

    # 변경 사항을 확인
    drone.send_request(DeviceType.DRONE, DataType.TRIM)
    sleep(0.1)


    drone.close()
```

- [TrimFlight](04_protocol.md#TrimFlight)
- [sendTrimFlight()](05_drone.md#sendTrimFlight)
- [send_request()](05_drone.md#send_request)


<br>

---

<h3><i>e_drone</i> for python</H3>

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
