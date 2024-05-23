**[*petrone_v2* for python](index.md)** / **Examples** / **Control**

Modified : 2017.10.27

---

<br>


## <a name="ControlWhileAndLanding">이륙, 호버링, 착륙 테스트</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    print("TakeOff")
    drone.sendTakeOff()
    for i in range(2, 0, -1):
        print("{0}".format(i))
        sleep(1)

    print("Hovering")
    for i in range(5, 0, -1):
        print("{0}".format(i))
        drone.sendControlWhile(0, 0, 0, 0, 1000)
        sleep(0.01)

    print("Landing")
    dataArray = drone.sendLanding()
    sleep(0.01)

    drone.close()
```

- [sendTakeOff()](04_drone.md#sendTakeOff)
- [sendControlWhile()](04_drone.md#sendControlWhile)
- [sendLanding()](04_drone.md#sendLanding)


<br>
<br>


## <a name="ControlWhile">이륙, 조종, 정지 테스트</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    print("TakeOff")
    drone.sendTakeOff()
    sleep(0.01)

    print("Hovering")
    drone.sendControlWhile(0, 0, 0, 0, 3600)
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


---

<h3><i>petrone_v2</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Ping](examples_01_ping.md)
 6. [Examples - Information](examples_02_information.md)
 7. [Examples - Pairing](examples_03_pairing.md)
 8. **Examples - Control**
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
