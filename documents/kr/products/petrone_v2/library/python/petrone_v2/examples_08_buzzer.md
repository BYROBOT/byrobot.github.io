**[*petrone_v2* for python](index.md)** / **Examples** / **Buzzer**

Modified : 2017.10.27

---

<br>


## <a name="Buzzer">sendBuzzer 함수 테스트</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")
    

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


## <a name="BuzzerScale">'학교 종이 땡땡땡' 일부 연주</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")
    

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

- [sendBuzzer()](04_drone.md#sendBuzzer)
- [sendBuzzerScale()](04_drone.md#sendBuzzerScale)


<br>
<br>


## <a name="Class_Buzzer">Buzzer 클래스 데이터를 직접 채워서 전송하기</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


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
12. **Examples - Buzzer**
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

[Tutorial for Mac](../tutorial_for_mac/)

<br>

[Index](index.md)
