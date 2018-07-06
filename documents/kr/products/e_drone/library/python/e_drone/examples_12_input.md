**[*e_drone* for python](index.md)** / **Examples** / **Input**

Modified : 2018.7.6

---

<br>


## <a name="Button">버튼 입력값 출력</a>

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def eventButton(button):
    print("eventButton() / " +
        "Button: 0b{0:16}, Event: {1:6}".format(bin(button.button)[2:].zfill(16), button.event.name))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Button, eventButton)

    drone.sendPing(DeviceType.Controller)

    for i in range(10, 0, -1):
        print(i)
        sleep(1)

    drone.close()
```

- [Button](03_protocol.md#Button)
- [sendPing()](04_drone.md#sendPing)


<br>
<br>


## <a name="Joystick">조이스틱 입력값 출력</a>

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def eventJoystick(joystick):
    print("eventJoystick() / " +
        "L: ({0:4}, {1:4}), {2:5}, {3:5} / ".format(joystick.left.x, joystick.left.y, joystick.left.direction.name, joystick.left.event.name) +
        "R: ({0:4}, {1:4}), {2:5}, {3:5}".format(joystick.right.x, joystick.right.y, joystick.right.direction.name, joystick.right.event.name))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Joystick, eventJoystick)

    drone.sendPing(DeviceType.Controller)

    for i in range(10, 0, -1):
        print(i)
        sleep(1)

    drone.close()
```

- [Joystick](03_protocol.md#Joystick)
- [sendPing()](04_drone.md#sendPing)


<br>


---

<h3><i>e_drone</i> for python</H3>

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
11. [Examples - Setup](examples_07_setup.md)
12. [Examples - Buzzer](examples_08_buzzer.md)
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. **Examples - Input**
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
