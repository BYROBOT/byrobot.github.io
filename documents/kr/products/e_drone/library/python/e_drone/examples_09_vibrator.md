**[*petrone_v2* for python](index.md)** / **Examples** / **Vibrator**

Modified : 2018.3.5

---

<br>


## <a name="Vibrator">sendVibrator 함수 테스트</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    drone.sendVibrator(100, 200, 1200)
    sleep(1)

    drone.close()
```

- [sendVibrator()](04_drone.md#sendVibrator)


<br>
<br>


## <a name="Class_Vibrator">Vibrator 클래스 데이터를 직접 채워서 전송하기</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    header = Header()
    
    header.dataType = DataType.Vibrator
    header.length   = Vibrator.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = Vibrator()

    data.mode       = VibratorMode.Instantally
    data.on         = 100
    data.off        = 200
    data.total      = 1200

    drone.transfer(header, data)
    sleep(1)


    drone.close()
```

- [Vibrator](03_protocol.md#Vibrator)


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
 8. [Examples - Control](examples_04_control.md)
 9. [Examples - Sensor](examples_05_sensor.md)
10. [Examples - Motor](examples_06_motor.md)
11. [Examples - Setup](examples_07_setup.md)
12. [Examples - Buzzer](examples_08_buzzer.md)
13. **Examples - Vibrator**
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
