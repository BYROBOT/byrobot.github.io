**[*CodingRider* for python](index.md)** / **Examples** / **Buzzer**

Modified : 2024.5.17

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Buzzer"></a>
## sendBuzzer 함수 테스트

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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

- [sendBuzzer()](04_drone.md#sendBuzzer)
- [sendBuzzerMute()](04_drone.md#sendBuzzerMute)
- [sendBuzzerScale()](04_drone.md#sendBuzzerScale)
- [sendBuzzerScaleReserve()](04_drone.md#sendBuzzerScaleReserve)
- [sendBuzzerHz()](04_drone.md#sendBuzzerHz)
- [sendBuzzerHzReserve()](04_drone.md#sendBuzzerHzReserve)


<br>
<br>


<a name="BuzzerScale"></a>
## '학교 종이 땡땡땡' 일부 연주

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()
    
    drone.sendBuzzer(BuzzerMode.Mute, BuzzerScale.Mute.value, 100)
    sleep(0.2)
    
    drone.sendBuzzerScale(BuzzerScale.G4, 300)     
    sleep(0.4)
    drone.sendBuzzerScale(BuzzerScale.G4, 300)     
    sleep(0.4)
    drone.sendBuzzerScale(BuzzerScale.A4, 300)     
    sleep(0.4)
    drone.sendBuzzerScale(BuzzerScale.A4, 300)     
    sleep(0.4)
    drone.sendBuzzerScale(BuzzerScale.G4, 300)     
    sleep(0.4)
    drone.sendBuzzerScale(BuzzerScale.G4, 300)     
    sleep(0.4)
    drone.sendBuzzerScale(BuzzerScale.E4, 300)     
    sleep(0.4)

    drone.close()
```

- [sendBuzzer()](04_drone.md#sendBuzzer)
- [sendBuzzerScale()](04_drone.md#sendBuzzerScale)


<br>
<br>


<a name="Class_Buzzer"></a>
## Buzzer 클래스 데이터를 직접 채워서 전송하기

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


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

- [Buzzer](03_protocol.md#Buzzer)


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
 8. **Examples - Buzzer**
 9. [Examples - Vibrator](examples_05_vibrator.md)
10. [Examples - Light](examples_06_light.md)
11. [Examples - Input](examples_07_input.md)
12. [Examples - Information](examples_08_information.md)
<br>

[Index](index.md)
