**[*CodingRider* for python](index.md)** / **Examples** / **Vibrator**

Modified : 2024.5.17

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Vibrator"></a>
## sendVibrator 함수 테스트

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    drone.sendVibrator(100, 200, 1200)
    sleep(1)

    drone.close()
```

- [sendVibrator()](04_drone.md#sendVibrator)


<br>
<br>


<a name="Class_Vibrator"></a>
## Vibrator 클래스 데이터를 직접 채워서 전송하기

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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

- [Vibrator](03_protocol.md#Vibrator)


<br>


---

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Control](examples_01_control.md)
 6. [Examples - Sensor](examples_02_sensor.md)
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. **Examples - Vibrator**
10. [Examples - Light](examples_06_light.md)
11. [Examples - Input](examples_07_input.md)
12. [Examples - Information](examples_08_information.md)
<br>

[Index](index.md)
