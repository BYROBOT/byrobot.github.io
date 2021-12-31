**[*e_drone* for python](index.md)** / **Examples** / **Pairing**

Modified : 2021.12.31

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Pairing"></a>
## 페어링 변경 후 변경된 정보 확인

```py
# 조종기의 페어링 정보를 변경하고, 변경된 정보를 요청한 후 응답을 기다려 출력하는 예제
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone(False)
    drone.open()

    # 페어링 설정
    drone.send_pairing(DeviceType.CONTROLLER, 0x0001, 0x0002, 0x0003, 0x04, 0x05, 0x06, 0x07, 0x08)
    sleep(0.01)

    # 페어링데이터 요청
    drone.send_request(DeviceType.CONTROLLER, DataType.PAIRING)

    time_start = time.time()

    while True:
        sleep(0.01)
        data_type = drone.check()
        
        if data_type == DataType.PAIRING:
            pairing = drone.get_data(DataType.PAIRING)

            print("Address: 0x{0:04X}{1:04X}{2:04X} / {0}.{1}.{2}".format(
                pairing.address_0, 
                pairing.address_1, 
                pairing.address_2))

            print("Scramble: {0}".format(pairing.scramble))

            print("Channel: {0} / {1} / {2} / {3}".format(
                pairing.channel_0,
                pairing.channel_1,
                pairing.channel_2,
                pairing.channel_3))

            break

        if time.time() > time_start + 1:
            break

    drone.close()
```

- [send_pairing()](05_drone.md#send_pairing)
- [send_request()](05_drone.md#send_request)
- [Pairing](04_protocol.md#Pairing)



<br>
<br>


## 페어링 변경 후 변경된 정보 확인(이벤트 함수 등록)

```py
# 조종기의 페어링 정보를 변경하고, 변경된 정보를 요청한 후 이벤트 핸들러를 통해 응답을 출력하는 예제
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_pairing(pairing):
    print("event_pairing()")

    print("Address: 0x{0:04X}{1:04X}{2:04X} / {0}.{1}.{2}".format(
        pairing.address_0, 
        pairing.address_1, 
        pairing.address_2))

    print("Scramble: {0}".format(pairing.scramble))

    print("Channel: {0} / {1} / {2} / {3}".format(
        pairing.channel_0,
        pairing.channel_1,
        pairing.channel_2,
        pairing.channel_3))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.PAIRING, event_pairing)

    # 페어링 설정
    drone.send_pairing(DeviceType.CONTROLLER, 0x0001, 0x0002, 0x0003, 0x04, 0x05, 0x06, 0x07, 0x08)
    sleep(0.01)

    # 페어링데이터 요청
    drone.send_request(DeviceType.CONTROLLER, DataType.PAIRING)
    sleep(0.1)
    
    drone.close()
```

- [send_pairing()](05_drone.md#send_pairing)
- [send_request()](05_drone.md#send_request)
- [Pairing](04_protocol.md#Pairing)


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
 8. **Examples - Pairing**
 9. [Examples - Control](examples_04_control.md)
10. [Examples - Sensor](examples_05_sensor.md)
11. [Examples - Motor](examples_06_motor.md)
12. [Examples - Setup](examples_07_setup.md)
13. [Examples - Buzzer](examples_08_buzzer.md)
14. [Examples - Vibrator](examples_09_vibrator.md)
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
