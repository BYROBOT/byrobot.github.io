**[*e_drive* for python](index.md)** / **Examples** / **Ping**

Modified : 2019.4.12

---

<br>


## <a name="Ping">Ping 테스트</a>

조종기에 **Ping**을 보내고, **Ack** 응답을 받아서 화면에 출력하는 예제입니다.

**sendPing()** 함수를 호출하고 응답을 받을 때까지 기다리는 시간이 필요하기 때문에 **sleep()** 함수를 사용했습니다.

데이터 송수신 과정에서 문제가 생겨 **Ack**를 받지 못하는 경우가 있을 수 있으므로 1초 동안 응답이 없으면 수신처리를 종료하게 하였습니다.

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone(False)
    drone.open()

    drone.sendPing(DeviceType.Controller)

    timeStart = time.time()

    while True:
        sleep(0.01)
        dataType = drone.check()

        if dataType == DataType.Ack:
            ack = drone.getData(DataType.Ack)
            print("{0} / {1} / {2:04X}".format(ack.dataType.name, ack.systemTime, ack.crc16))
            print("T: {0}".format(time.time() - timeStart))
            break;

        # 1초 동안 응답이 없을 경우 응답 확인을 빠져나감
        if time.time() > timeStart + 1:
            print("Time Over")
            break;

    drone.close()
```

- [Ack](03_protocol.md#Ack)
- [sendPing()](04_drone.md#sendPing)


<br>
<br>


## <a name="Class_Ping">Ping 테스트(이벤트 함수 등록)</a>

조종기에 **Ping**을 보내고, **Ack** 응답을 받아서 화면에 출력하는 예제입니다.

수신 받을 데이터를 처리하는 함수를 만들어 **setEventHandler(DataType, function)**를 사용하여 등록하면 해당 데이터를 받았을 때 미리 연결한 함수를 호출합니다.

마지막 **sleep(0.1)**은 **Ping** 전송 후 **Ack** 응답이 들어올 때까지 기다리기 위해 사용하였습니다.

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


def eventAck(ack):
    print("eventAck()")
    print("{0} / {1} / {2:04X}".format(ack.dataType.name, ack.systemTime, ack.crc16))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Ack, eventAck)

    # Ping 전송
    drone.sendPing(DeviceType.Controller)
    
    sleep(0.1)

    drone.close()
```

- [Ack](03_protocol.md#Ack)
- [sendPing()](04_drone.md#sendPing)


<br>


---

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. [Drone](05_drone.md)
 6. **Examples - Ping**
 7. [Examples - Information](examples_02_information.md)
 8. [Examples - Control](examples_03_control.md)
 9. [Examples - Sensor](examples_04_sensor.md)
10. [Examples - Motor](examples_05_motor.md)
11. [Examples - Setup](examples_06_setup.md)
12. [Examples - Buzzer](examples_07_buzzer.md)
13. [Examples - Light](examples_08_light.md)
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
