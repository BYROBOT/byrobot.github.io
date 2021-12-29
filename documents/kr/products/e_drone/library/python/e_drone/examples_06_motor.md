**[*e_drone* for python](index.md)** / **Examples** / **Motor**

Modified : 2021.12.29

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Motor"></a>
## 모터 동작 테스트

드론의 전체 모터를 각각 다른 속도로 동작시켰다가 정지합니다.

통신 과정에서 문제가 생겨 모터 제어 명령이 전달되지 않을 수도 있으니 드론을 잘 잡은 채로 시도하시기 바랍니다.

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_ack(ack):
    print("event_ack() / {0} / 0x{1:04X} / {2}".format(ack.data_type.name, ack.crc16, ack.system_time))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.ACK, event_ack)
    sleep(0.01)


    drone.send_motor(100, 0, 0, 0)
    sleep(3)

    drone.send_motor(0, 100, 0, 0)
    sleep(3)
    
    drone.send_motor(0, 0, 100, 0)
    sleep(3)
    
    drone.send_motor(0, 0, 0, 100)
    sleep(3)

    drone.send_motor(0, 0, 0, 0)
    sleep(0.1)


    drone.close()
```

- [Ack](04_protocol.md#Ack)
- [sendMotor()](05_drone.md#sendMotor)


<br>
<br>


<a name="MotorSingle"></a>
## MotorSingle 동작 테스트

우측 앞 모터 속도를 점점 올렸다가 다시 내린 후 정지하는 명령을 차례로 실행합니다.

통신 과정에서 문제가 생겨 모터 제어 명령이 전달되지 않을 수도 있으니 드론을 잘 잡은 채로 시도하시기 바랍니다.

```py
# MotorSingle 동작 테스트
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_ack(ack):
    print("event_ack()")
    print("-   DataType: {0}".format(ack.data_type.name))
    print("-      CRC16: 0x{0:04X}".format(ack.crc16))
    print("- SystemTime: {0}".format(ack.system_time))


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.ACK, event_ack)
    sleep(0.01)


    drone.send_motor_single(0, 200)
    sleep(2)

    drone.send_motor_single(0, 0)
    sleep(1)

    drone.send_motor_single(1, 200)
    sleep(2)

    drone.send_motor_single(1, 0)
    sleep(1)

    drone.send_motor_single(2, 200)
    sleep(2)

    drone.send_motor_single(2, 0)
    sleep(1)

    drone.send_motor_single(3, 200)
    sleep(2)

    drone.send_motor_single(3, 0)
    sleep(1)


    drone.close()
```

- [Ack](04_protocol.md#Ack)
- [sendMotorSingle()](05_drone.md#sendMotorSingle)


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
11. **Examples - Motor**
12. [Examples - Setup](examples_07_setup.md)
13. [Examples - Buzzer](examples_08_buzzer.md)
14. [Examples - Vibrator](examples_09_vibrator.md)
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)


<br>

[Index](index.md)
