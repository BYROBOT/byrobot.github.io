**[*e_drive* for python](index.md)** / **Examples** / **Control**

Modified : 2019.4.12

---

<br>


## <a name="ControlWhileAndLanding">이륙, 호버링, 착륙 테스트</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    print("TakeOff")
    drone.sendTakeOff()
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Hovering")
    for i in range(3, 0, -1):
        print("{0}".format(i))
        drone.sendControlWhile(0, 0, 0, 0, 1000)
        sleep(0.01)

    print("Landing")
    drone.sendLanding()
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)

    drone.close()
```

- [sendTakeOff()](04_drone.md#sendTakeOff)
- [sendControlWhile()](04_drone.md#sendControlWhile)
- [sendLanding()](04_drone.md#sendLanding)


<br>
<br>


## <a name="ControlWhile">이륙, 호버링, 하강, 정지 테스트</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    print("TakeOff")
    drone.sendTakeOff()
    sleep(0.01)

    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 6400)
    sleep(0.01)

    print("Throttle down")
    drone.sendControlWhile(0, 0, 0, -25, 3600)
    sleep(0.01)

    print("Stop")
    drone.sendStop()
    sleep(0.01)


    drone.close()
```

- [sendTakeOff()](04_drone.md#sendTakeOff)
- [sendControlWhile()](04_drone.md#sendControlWhile)
- [sendStop()](04_drone.md#sendStop)


<br>
<br>


## <a name="ControlPosition">이륙, 호버링, 전진, 착륙 테스트</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    print("TakeOff")
    drone.sendTakeOff()
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 3600)
    for i in range(3, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Go Front 1 meter")
    drone.sendControlPosition16(10, 0, 0, 5, 0, 0)
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Landing")
    drone.sendLanding()
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)


    drone.close()
```

- [sendTakeOff()](04_drone.md#sendTakeOff)
- [sendControlWhile()](04_drone.md#sendControlWhile)
- [sendControlPosition()](04_drone.md#sendControlPosition)
- [sendLanding()](04_drone.md#sendLanding)


<br>
<br>


## <a name="ControlReturnHome">이륙, 호버링, 1미터 전진, 1미터 오른쪽 이동, 리턴 홈 테스트</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    print("TakeOff")
    drone.sendTakeOff()
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 3600)
    for i in range(3, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Go Front 1 meter")
    drone.sendControlPosition(1.0, 0, 0, 0.5, 0, 0)
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Go Right 1 meter")
    drone.sendControlPosition(0, -1.0, 0, 0.5, 0, 0)
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Return Home")
    drone.sendFlightEvent(FlightEvent.Return)
    for i in range(5, 0, -1):
        print("{0}".format(i))
        sleep(1)


    drone.close()
```

- [sendTakeOff()](04_drone.md#sendTakeOff)
- [sendControlWhile()](04_drone.md#sendControlWhile)
- [sendControlPosition()](04_drone.md#sendControlPosition)
- [sendFlightEvent()](04_drone.md#sendFlightEvent)
- [sendLanding()](04_drone.md#sendLanding)


<br>


---

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. [Drone](05_drone.md)
 6. [Examples - Ping](examples_01_ping.md)
 7. [Examples - Information](examples_02_information.md)
 8. **Examples - Control**
 9. [Examples - Sensor](examples_04_sensor.md)
10. [Examples - Motor](examples_05_motor.md)
11. [Examples - Setup](examples_06_setup.md)
12. [Examples - Buzzer](examples_07_buzzer.md)
13. [Examples - Light](examples_08_light.md)
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
