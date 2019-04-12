**[*e_drive* for python](index.md)** / **Examples** / **Information**

Modified : 2019.4.12

---

<br>


## <a name="Information">조종기의 펌웨어 정보 요청</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone(False)
    drone.open()

    drone.sendRequest(DeviceType.Controller, DataType.Information)

    timeStart = time.time()

    while True:
        sleep(0.01)
        dataType = drone.check()
        
        if dataType == DataType.Information:
            information = drone.getData(DataType.Information)
            print("ModeUpdate: {0}".format(information.modeUpdate))
            print("ModelNumber: {0}".format(information.modelNumber))
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

        if time.time() > timeStart + 1:
            break

    drone.close()
```

- [Information](03_protocol.md#Information)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="Class_Information">조종기의 펌웨어 정보 요청(이벤트 함수 등록)</a>

```py
# 조종기의 펌웨어 정보를 요청하고, 이벤트 핸들러를 통해 응답을 출력하는 예제
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


def eventInformation(information):
    print("eventInformation()")
    print("ModeUpdate: {0}".format(information.modeUpdate))
    print("ModelNumber: {0}".format(information.modelNumber))
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
    drone.setEventHandler(DataType.Information, eventInformation)

    # Information 정보 요청
    drone.sendRequest(DeviceType.Controller, DataType.Information)
    sleep(0.1)

    drone.close()
```

- [Information](03_protocol.md#Information)
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
 7. **Examples - Information**
 8. [Examples - Control](examples_03_control.md)
 9. [Examples - Sensor](examples_04_sensor.md)
10. [Examples - Motor](examples_05_motor.md)
11. [Examples - Setup](examples_06_setup.md)
12. [Examples - Buzzer](examples_07_buzzer.md)
13. [Examples - Light](examples_08_light.md)
14. [Examples - Error](examples_09_error.md)
<br>

[Index](index.md)
