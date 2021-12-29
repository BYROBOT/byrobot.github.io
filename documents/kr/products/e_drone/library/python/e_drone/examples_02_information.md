**[*e_drone* for python](index.md)** / **Examples** / **Information**

Modified : 2021.12.29

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Information"></a>
## 조종기의 펌웨어 정보 요청

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone(False)
    drone.open()

    drone.send_request(DeviceType.CONTROLLER, DataType.INFORMATION)

    time_start = time.time()

    while True:
        sleep(0.01)
        dataType = drone.check()
        
        if dataType == DataType.INFORMATION:
            information = drone.get_data(DataType.INFORMATION)
            print("ModeUpdate: {0}".format(information.mode_update))
            print("ModelNumber: {0}".format(information.model_number))
            print("Version: {0}.{1}.{2} / {3} / 0x{3:08X}".format(
                information.version.major,
                information.version.minor,
                information.version.build,
                information.version.v))
            print("Release Date: {0}.{1}.{2}".format(
                information.year,
                information.month,
                information.day))
            break

        if time.time() > time_start + 1:
            break

    drone.close()
```

- [Information](04_protocol.md#Information)
- [sendRequest()](05_drone.md#sendRequest)


<br>
<br>


<a name="Class_Information"></a>
## 조종기의 펌웨어 정보 요청(이벤트 함수 등록)

```py
# 조종기의 펌웨어 정보를 요청하고, 이벤트 핸들러를 통해 응답을 출력하는 예제
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_information(information):
    print("event_information()")
    print("ModeUpdate: {0}".format(information.mode_update))
    print("ModelNumber: {0}".format(information.model_number))
    print("Version: {0}.{1}.{2} / {3} / 0x{3:08X}".format(
        information.version.major,
        information.version.minor,
        information.version.build,
        information.version.v))
    print("Release Date: {0}.{1}.{2}".format(
        information.year,
        information.month,
        information.day))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.INFORMATION, event_information)

    # Information 정보 요청
    drone.send_request(DeviceType.CONTROLLER, DataType.INFORMATION)
    sleep(0.1)

    drone.close()
```

- [Information](04_protocol.md#Information)
- [sendRequest()](05_drone.md#sendRequest)


<br>


---

<h3><i>e_drone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. [Drone](05_drone.md)
 6. [Examples - Ping](examples_01_ping.md)
 7. **Examples - Information**
 8. [Examples - Pairing](examples_03_pairing.md)
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
