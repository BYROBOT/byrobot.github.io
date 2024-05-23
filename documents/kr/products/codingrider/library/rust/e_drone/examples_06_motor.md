**[*e_drone* for python](index.md)** / **Examples** / **Motor**

Modified : 2018.7.6

---

<br>


## <a name="Motor">모터 동작 테스트</a>

드론의 전체 모터를 각각 다른 속도로 동작시켰다가 정지합니다.

통신 과정에서 문제가 생겨 모터 제어 명령이 전달되지 않을 수도 있으니 드론을 잘 잡은 채로 시도하시기 바랍니다.

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def eventAck(ack):
    print("eventAck() / {0} / 0x{1:04X} / {2}".format(ack.dataType.name, ack.crc16, ack.systemTime))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Ack, eventAck)
    sleep(0.01)


    drone.sendMotor(1000, 1200, 1300, 1400)
    sleep(1)

    drone.sendMotor(0, 0, 0, 0)
    sleep(0.1)


    drone.close()
```

- [Ack](03_protocol.md#Ack)
- [sendMotor()](04_drone.md#sendMotor)


<br>
<br>


## <a name="MotorSingle">MotorSingle 동작 테스트</a>

우측 앞 모터 속도를 점점 올렸다가 다시 내린 후 정지하는 명령을 차례로 실행합니다.

통신 과정에서 문제가 생겨 모터 제어 명령이 전달되지 않을 수도 있으니 드론을 잘 잡은 채로 시도하시기 바랍니다.

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def eventAck(ack):
    print("eventAck() / {0} / 0x{1:04X} / {2}".format(ack.dataType.name, ack.crc16, ack.systemTime))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Ack, eventAck)
    sleep(0.01)


    drone.sendMotorSingle(0, Rotation.Clockwise, 1000)
    sleep(2)

    drone.sendMotorSingle(0, Rotation.Clockwise, 2000)
    sleep(2)

    drone.sendMotorSingle(0, Rotation.Clockwise, 3000)
    sleep(2)

    drone.sendMotorSingle(0, Rotation.Clockwise, 2000)
    sleep(2)

    drone.sendMotorSingle(0, Rotation.Clockwise, 1000)
    sleep(2)

    drone.sendStop()
    sleep(0.1)


    drone.close()
```

- [Ack](03_protocol.md#Ack)
- [sendMotorSingle()](04_drone.md#sendMotorSingle)


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
10. **Examples - Motor**
11. [Examples - Setup](examples_07_setup.md)
12. [Examples - Buzzer](examples_08_buzzer.md)
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)


<br>

[Index](index.md)
