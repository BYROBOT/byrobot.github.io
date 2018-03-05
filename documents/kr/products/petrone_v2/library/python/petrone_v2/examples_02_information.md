**[*petrone_v2* for python](index.md)** / **Examples** / **Information**

Modified : 2018.3.5

---

<br>


## <a name="Information">조종기의 펌웨어 정보 요청</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone(False)
    drone.open("COM22")

    drone.sendRequest(DeviceType.Controller, DataType.Information)

    timeStart = time.time()

    while True:
        sleep(0.01)
        dataType = drone.check()
        
        if dataType == DataType.Information:
            information = drone.getData(DataType.Information)
            print("{0} / 0x{0:08X}".format(information.version.v))
            print("{0}.{1}.{2}.{3}".format(
                information.version.major,
                information.version.minor,
                information.version.stage.name,
                information.version.build))
            break;

        if time.time() > timeStart + 1:
            break;
    
    drone.close()
```

- [Information](03_protocol.md#Information)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="Class_Information">조종기의 펌웨어 정보 요청(이벤트 함수 등록)</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventInformation(information):
    print("eventInformation()")
    print("{0} / 0x{0:08X}".format(information.version.v))
    print("{0}.{1}.{2}.{3}".format(
        information.version.major,
        information.version.minor,
        information.version.stage.name,
        information.version.build))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

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

<h3><i>petrone_v2</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Ping](examples_01_ping.md)
 6. **Examples - Information**
 7. [Examples - Pairing](examples_03_pairing.md)
 8. [Examples - Control](examples_04_control.md)
 9. [Examples - Sensor](examples_05_sensor.md)
10. [Examples - Motor](examples_06_motor.md)
11. [Examples - Setup](examples_07_setup.md)
12. [Examples - Buzzer](examples_08_buzzer.md)
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
