**[*CodingRider* for python](index.md)** / **Examples** / **Input**

Modified : 2024.5.23

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Button"></a>
## 버튼 입력값 출력

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


def eventButton(button):
    print("eventButton() / " +
        "Button: 0b{0:16}, Event: {1:6}".format(bin(button.button)[2:].zfill(16), button.event.name))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

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


<a name="Joystick"></a>
## 조이스틱 입력값 출력

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


def eventJoystick(joystick):
    print("eventJoystick() / " +
        "L: ({0:4}, {1:4}), {2:5}, {3:5} / ".format(joystick.left.x, joystick.left.y, joystick.left.direction.name, joystick.left.event.name) +
        "R: ({0:4}, {1:4}), {2:5}, {3:5}".format(joystick.right.x, joystick.right.y, joystick.right.direction.name, joystick.right.event.name))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

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

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Control](examples_01_control.md)
 6. [Examples - Sensor](examples_02_sensor.md)
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Light](examples_05_light.md)
10. **Examples - Input**
11. [Examples - Information](examples_07_information.md)
<br>

[Index](index.md)
