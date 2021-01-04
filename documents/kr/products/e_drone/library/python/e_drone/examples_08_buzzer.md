**[*e_drone* for python](index.md)** / **Examples** / **Buzzer**

Modified : 2021.1.4

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Buzzer"></a>
## sendBuzzer 함수 테스트

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()
    

    drone.sendBuzzer(BuzzerMode.Mute, BuzzerScale.Mute.value, 500)
    sleep(1)

    drone.sendBuzzer(BuzzerMode.Scale, BuzzerScale.C4.value, 500)
    sleep(1)

    drone.sendBuzzer(BuzzerMode.Hz, 500, 500)
    sleep(1)


    drone.sendBuzzerMute(100)
    drone.sendBuzzerMuteReserve(100)
    sleep(1.2)


    drone.sendBuzzerScale(BuzzerScale.C5, 500)
    drone.sendBuzzerScaleReserve(BuzzerScale.D5, 500)
    sleep(1.2)


    drone.sendBuzzerHz(1000, 500)
    drone.sendBuzzerHzReserve(1200, 500)
    sleep(1.2)
    

    drone.close()
```

- [sendBuzzer()](05_drone.md#sendBuzzer)
- [sendBuzzerMute()](05_drone.md#sendBuzzerMute)
- [sendBuzzerScale()](05_drone.md#sendBuzzerScale)
- [sendBuzzerScaleReserve()](05_drone.md#sendBuzzerScaleReserve)
- [sendBuzzerHz()](05_drone.md#sendBuzzerHz)
- [sendBuzzerHzReserve()](05_drone.md#sendBuzzerHzReserve)


<br>
<br>


<a name="BuzzerScale"></a>
## '학교 종이 땡땡땡' 일부 연주

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()
    
    drone.sendBuzzer(BuzzerMode.Mute, BuzzerScale.Mute.value, 100)
    sleep(0.2);
    
    drone.sendBuzzerScale(BuzzerScale.G4, 300);     sleep(0.4);
    drone.sendBuzzerScale(BuzzerScale.G4, 300);     sleep(0.4);
    drone.sendBuzzerScale(BuzzerScale.A4, 300);     sleep(0.4);
    drone.sendBuzzerScale(BuzzerScale.A4, 300);     sleep(0.4);
    drone.sendBuzzerScale(BuzzerScale.G4, 300);     sleep(0.4);
    drone.sendBuzzerScale(BuzzerScale.G4, 300);     sleep(0.4);
    drone.sendBuzzerScale(BuzzerScale.E4, 300);     sleep(0.4);

    drone.close()
```

- [sendBuzzer()](05_drone.md#sendBuzzer)
- [sendBuzzerScale()](05_drone.md#sendBuzzerScale)


<br>
<br>


<a name="Class_Buzzer"></a>
## Buzzer 클래스 데이터를 직접 채워서 전송하기

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    header = Header()
    
    header.dataType = DataType.Buzzer
    header.length   = Buzzer.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller


    data = Buzzer()

    data.mode       = BuzzerMode.Scale
    data.value      = BuzzerScale.C5.value
    data.time       = 500

    drone.transfer(header, data)
    sleep(1)


    data.mode       = BuzzerMode.Hz
    data.value      = 1200
    data.time       = 500

    drone.transfer(header, data)
    sleep(1)


    drone.close()
```

- [Buzzer](04_protocol.md#Buzzer)


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
13. **Examples - Buzzer**
14. [Examples - Vibrator](examples_09_vibrator.md)
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
