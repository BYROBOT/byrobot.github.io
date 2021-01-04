**[*e_drone* for python](index.md)** / **Examples** / **Vibrator**

Modified : 2021.1.4

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Vibrator"></a>
## sendVibrator 함수 테스트

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    drone.sendVibrator(100, 200, 1200)
    sleep(1)

    drone.close()
```

- [sendVibrator()](05_drone.md#sendVibrator)


<br>
<br>


<a name="Class_Vibrator"></a>
## Vibrator 클래스 데이터를 직접 채워서 전송하기

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


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

- [Vibrator](04_protocol.md#Vibrator)


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
 9. [Examples - Control](examples_04_control.md)
10. [Examples - Sensor](examples_05_sensor.md)
11. [Examples - Motor](examples_06_motor.md)
12. [Examples - Setup](examples_07_setup.md)
13. [Examples - Buzzer](examples_08_buzzer.md)
13. **Examples - Vibrator**
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
