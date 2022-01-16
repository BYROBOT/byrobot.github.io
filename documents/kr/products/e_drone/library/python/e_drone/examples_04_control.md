**[*e_drone* for python](index.md)** / **Examples** / **Control**

Modified : 2021.1.4

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="ControlWhileAndLanding"></a>
## 이륙, 호버링, 착륙 테스트

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


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

- [sendTakeOff()](05_drone.md#sendTakeOff)
- [sendControlWhile()](05_drone.md#sendControlWhile)
- [sendLanding()](05_drone.md#sendLanding)


<br>
<br>


<a name="ControlWhile"></a>
## 이륙, 호버링, 하강, 정지 테스트

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


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

- [sendTakeOff()](05_drone.md#sendTakeOff)
- [sendControlWhile()](05_drone.md#sendControlWhile)
- [sendStop()](05_drone.md#sendStop)


<br>
<br>


<a name="ControlPosition"></a>
## 이륙, 호버링, 전진, 착륙 테스트

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


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

- [sendTakeOff()](05_drone.md#sendTakeOff)
- [sendControlWhile()](05_drone.md#sendControlWhile)
- [sendControlPosition()](05_drone.md#sendControlPosition)
- [sendLanding()](05_drone.md#sendLanding)


<br>
<br>


<a name="ControlReturnHome"></a>
## 이륙, 호버링, 1미터 전진, 1미터 오른쪽 이동, 리턴 홈 테스트

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


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

- [sendTakeOff()](05_drone.md#sendTakeOff)
- [sendControlWhile()](05_drone.md#sendControlWhile)
- [sendControlPosition()](05_drone.md#sendControlPosition)
- [sendFlightEvent()](05_drone.md#sendFlightEvent)
- [sendLanding()](05_drone.md#sendLanding)


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
 8. [Examples - Pairing](examples_03_pairing.md)
 9. **Examples - Control**
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
