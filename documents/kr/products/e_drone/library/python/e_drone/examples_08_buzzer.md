**[*e_drone* for python](index.md)** / **Examples** / **Buzzer**

Modified : 2021.12.29

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Buzzer"></a>
## send_buzzer 함수 테스트

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()
    

    drone.send_buzzer(BuzzerMode.MUTE, BuzzerScale.MUTE.value, 500)
    sleep(1)

    drone.send_buzzer(BuzzerMode.SCALE, BuzzerScale.C4.value, 500)
    sleep(1)

    drone.send_buzzer(BuzzerMode.HZ, 500, 500)
    sleep(1)


    drone.send_buzzer_mute(100)
    drone.send_buzzer_mute_reserve(100)
    sleep(1.2)


    drone.send_buzzer_scale(BuzzerScale.C5, 500)
    drone.send_buzzer_scale_reserve(BuzzerScale.D5, 500)
    sleep(1.2)


    drone.send_buzzer_hz(1000, 500)
    drone.send_buzzer_hz_reserve(1200, 500)
    sleep(1.2)
    

    drone.close()
```

- [send_buzzer()](05_drone.md#send_buzzer)
- [send_buzzer_mute()](05_drone.md#send_buzzer_mute)
- [send_buzzer_scale()](05_drone.md#send_buzzer_scale)
- [send_buzzer_scale_reserve()](05_drone.md#send_buzzer_scale_reserve)
- [send_buzzer_hz()](05_drone.md#send_buzzer_hz)
- [send_buzzer_hz_reserve()](05_drone.md#send_buzzer_hz_reserve)


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
    
    drone.send_buzzer(BuzzerMode.MUTE, BuzzerScale.MUTE.value, 100)
    sleep(0.2);
    
    drone.send_buzzer_scale(BuzzerScale.G4, 500);     sleep(0.5);
    drone.send_buzzer_scale(BuzzerScale.G4, 500);     sleep(0.5);
    drone.send_buzzer_scale(BuzzerScale.A4, 500);     sleep(0.5);
    drone.send_buzzer_scale(BuzzerScale.A4, 500);     sleep(0.5);
    drone.send_buzzer_scale(BuzzerScale.G4, 500);     sleep(0.5);
    drone.send_buzzer_scale(BuzzerScale.G4, 500);     sleep(0.5);
    drone.send_buzzer_scale(BuzzerScale.E4, 500);     sleep(0.5);

    drone.close()
```

- [send_buzzer()](05_drone.md#send_buzzer)
- [send_buzzer_scale()](05_drone.md#send_buzzer_scale)


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
    
    header.data_type = DataType.BUZZER
    header.length    = Buzzer.get_size()
    header.from_     = DeviceType.BASE
    header.to_       = DeviceType.CONTROLLER


    data = Buzzer()

    data.mode       = BuzzerMode.SCALE
    data.value      = BuzzerScale.C5.value
    data.time       = 500

    drone.transfer(header, data)
    sleep(1)


    data.mode       = BuzzerMode.HZ
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
