**[*petrone_v2* for python](index.md)** / **Examples** / **Pairing**

Modified : 2017.09.20

---

<br>


## <a name="Pairing">페어링 변경 후 변경된 정보 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone(False)
    drone.open("COM22")

    # 페어링 설정
    drone.sendPairing(DeviceType.Controller, 0x0005, 0x0004, 0x03)
    sleep(0.01)

    # 페어링데이터 요청
    drone.sendRequest(DeviceType.Controller, DataType.Pairing)
    
    timeStart = time.time()

    while True:
        sleep(0.01)
        dataType = drone.check()
        
        if    dataType == DataType.Pairing:
            pairing = drone.getData(DataType.Pairing)
            print("{0} / {1} / {2}".format(
                pairing.addressLocal, 
                pairing.addressRemote, 
                pairing.channel))
            break;

        if time.time() > timeStart + 1:
            break;
    
    drone.close()
```

- [sendPairing()](04_drone.md#sendPairing)
- [sendRequest()](04_drone.md#sendRequest)
- [Pairing](03_protocol.md#Pairing)



<br>
<br>


## 페어링 변경 후 변경된 정보 확인(이벤트 함수 등록)

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventPairing(pairing):
    print("eventPairing()")
    print("{0} / {1} / {2}".format(
        pairing.addressLocal, 
        pairing.addressRemote, 
        pairing.channel))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Pairing, eventPairing)

    # 페어링 설정
    drone.sendPairing(DeviceType.Controller, 0x0005, 0x0004, 0x03)
    sleep(0.01)

    # 페어링데이터 요청
    drone.sendRequest(DeviceType.Controller, DataType.Pairing)
    sleep(0.1)
    
    drone.close()
```

- [sendPairing()](04_drone.md#sendPairing)
- [sendRequest()](04_drone.md#sendRequest)
- [Pairing](03_protocol.md#Pairing)


<br>


---

<h3><i>petrone_v2</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Ping](examples_01_ping.md)
 6. [Examples - Information](examples_02_information.md)
 7. **Examples - Pairing**
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

[Tutorial for Mac](./tutorial_for_mac/)

<br>

[Index](index.md)
