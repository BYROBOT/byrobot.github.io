**[*e_drive* for python](index.md)** / **Examples** / **Pairing**

Modified : 2019.1.10

---

<br>


## <a name="Pairing">페어링 변경 후 변경된 정보 확인</a>

```py
# 조종기의 페어링 정보를 변경하고, 변경된 정보를 요청한 후 응답을 기다려 출력하는 예제
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone(False)
    drone.open()

    # 페어링 설정
    drone.sendPairing(DeviceType.Controller, 0x0001, 0x0002, 0x0003, 0x04, 0x05)
    sleep(0.01)

    # 페어링데이터 요청
    drone.sendRequest(DeviceType.Controller, DataType.Pairing)
    
    timeStart = time.time()

    while True:
        sleep(0.01)
        dataType = drone.check()
        
        if    dataType == DataType.Pairing:
            pairing = drone.getData(DataType.Pairing)

            print("Address: 0x{0:04X}{1:04X}{2:04X} / {0}.{1}.{2}".format(
                pairing.address0, 
                pairing.address1, 
                pairing.address2))

            print("Scramble: {0}".format(pairing.scramble))
            print("Channel: {0}".format(pairing.channel))
            break

        if time.time() > timeStart + 1:
            break
    
    drone.close()
```

- [sendPairing()](04_drone.md#sendPairing)
- [sendRequest()](04_drone.md#sendRequest)
- [Pairing](03_protocol.md#Pairing)



<br>
<br>


## 페어링 변경 후 변경된 정보 확인(이벤트 함수 등록)

```py
# 조종기의 페어링 정보를 변경하고, 변경된 정보를 요청한 후 이벤트 핸들러를 통해 응답을 출력하는 예제
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


def eventPairing(pairing):
    print("eventPairing()")

    print("Address: 0x{0:04X}{1:04X}{2:04X} / {0}.{1}.{2}".format(
        pairing.address0, 
        pairing.address1, 
        pairing.address2))

    print("Scramble: {0}".format(pairing.scramble))
    print("Channel: {0}".format(pairing.channel))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Pairing, eventPairing)

    # 페어링 설정
    drone.sendPairing(DeviceType.Controller, 0x0005, 0x0006, 0x0007, 0x08, 0x09)
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

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Command Line](05_commandline.md)
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
