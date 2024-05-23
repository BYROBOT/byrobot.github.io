**[*CodingRider* for python](index.md)** / **Examples** / **Control**

Modified : 2024.5.23

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="ControlWhileAndLanding"></a>
## 이륙, 호버링, 착륙 테스트

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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


<a name="ControlWhile"></a>
## 이륙, 호버링, 하강, 정지 테스트

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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


<a name="ControlPosition"></a>
## 이륙, 호버링, 전진, 착륙 테스트

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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


<a name="ControlReturnHome"></a>
## 이륙, 호버링, 1미터 전진, 1미터 오른쪽 이동, 리턴 홈 테스트

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. **Examples - Control**
 6. [Examples - Sensor](examples_02_sensor.md)
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Light](examples_05_light.md)
10. [Examples - Input](examples_06_input.md)
11. [Examples - Information](examples_07_information.md)
<br>

[Index](index.md)
