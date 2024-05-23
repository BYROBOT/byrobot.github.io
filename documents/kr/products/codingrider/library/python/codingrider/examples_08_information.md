**[*CodingRider* for python](index.md)** / **Examples** / **Information**

Modified : 2024.5.17

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Information"></a>
## 조종기의 펌웨어 정보 요청

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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


<a name="Class_Information"></a>
## 조종기의 펌웨어 정보 요청(이벤트 함수 등록)

```py
# 조종기의 펌웨어 정보를 요청하고, 이벤트 핸들러를 통해 응답을 출력하는 예제
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Control](examples_01_control.md)
 6. [Examples - Sensor](examples_02_sensor.md)
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Vibrator](examples_05_vibrator.md)
10. [Examples - Light](examples_06_light.md)
11. [Examples - Input](examples_07_input.md)
12. **Examples - Information**
<br>

[Index](index.md)
