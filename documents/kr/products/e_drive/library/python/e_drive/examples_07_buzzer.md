**[*e_drive* for python](index.md)** / **Examples** / **Buzzer**

Modified : 2019.4.15

---

<br>


## <a name="Buzzer">sendBuzzer 함수 테스트</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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


## <a name="BuzzerScale">'학교 종이 땡땡땡' 일부 연주</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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

- [sendBuzzer()](04_drone.md#sendBuzzer)
- [sendBuzzerScale()](04_drone.md#sendBuzzerScale)


<br>
<br>


## <a name="Class_Buzzer">Buzzer 클래스 데이터를 직접 채워서 전송하기</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. [Protocol](04_protocol.md)
 5. [Drone](05_drone.md)
 6. [Examples - Ping](examples_01_ping.md)
 7. [Examples - Information](examples_02_information.md)
 8. [Examples - Control](examples_03_control.md)
 9. [Examples - Sensor](examples_04_sensor.md)
10. [Examples - Motor](examples_05_motor.md)
11. [Examples - Setup](examples_06_setup.md)
12. **Examples - Buzzer**
13. [Examples - Light](examples_08_light.md)
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
