**[*CodingRider* for python](index.md)** / **Examples** / **Light**

Modified : 2024.5.23

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="LightManual"></a>
## sendLightManual() 함수를 사용하여 조종기 LED 제어하기

```py
import random
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.sendLightManual(DeviceType.Controller, 0xFF, 0)
    sleep(1)
    
    
    drone.sendLightManual(DeviceType.Controller, 0b00000011, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000011, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000011, 0)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000110, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000110, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000110, 0)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000101, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000101, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Controller, 0b00000101, 0)
    sleep(1)


    drone.close()
```

- [sendLightManual()](04_drone.md#sendLightManual)


<br>
<br>

## sendLightManual() 함수를 사용하여 드론 LED 제어하기

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.sendLightManual(DeviceType.Drone, 0xFF, 0)
    sleep(1)


    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyRed.value, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyRed.value, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyRed.value, 0)
    sleep(1)

    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyGreen.value, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyGreen.value, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyGreen.value, 0)
    sleep(1)

    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyBlue.value, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyBlue.value, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyBlue.value, 0)
    sleep(1)


    drone.sendLightManual(DeviceType.Drone, 0x06, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, 0x06, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, 0x06, 0)
    sleep(1)

    drone.sendLightManual(DeviceType.Drone, 0x0A, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, 0x0A, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, 0x0A, 0)
    sleep(1)

    drone.sendLightManual(DeviceType.Drone, 0x0C, 10)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, 0x0C, 100)
    sleep(1)
    
    drone.sendLightManual(DeviceType.Drone, 0x0C, 0)
    sleep(1)


    drone.close()
```

- [sendLightManual()](04_drone.md#sendLightManual)


<br>
<br>



## sendLightMode, sendLightEvent 함수를 사용하여 드론 LED 제어하기


```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.sendLightModeColor(LightModeDrone.BodyHold, 200, 0, 200, 200)
    sleep(1)


    # sendLightModeColor*
    drone.sendLightModeColor(LightModeDrone.BodyDimming, 3, 0, 0, 200)
    sleep(3)
    
    # sendLightEventColor*
    drone.sendLightEventColor(LightModeDrone.BodyDimming, 3, 5, 200, 200, 200)
    sleep(3)
    

    drone.close()
```

- [sendLightModeColor()](04_drone.md#sendLightModeColor)
- [sendLightEventColor()](04_drone.md#sendLightEventColor)


<br>
<br>


## 드론의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (sendLightModeColor 함수 사용)

```py
import random
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 10, 1):
        
        r    = int(random.randint(0, 255))
        g    = int(random.randint(0, 255))
        b    = int(random.randint(0, 255))

        dataArray = drone.sendLightModeColor(LightModeDrone.BodyDimming, 1, r, g, b)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.6)
    
    drone.close()
```

- [sendLightModeColor()](04_drone.md#sendLightModeColor)


<br>
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
 9. **Examples - Light**
10. [Examples - Input](examples_06_input.md)
11. [Examples - Information](examples_07_information.md)
<br>

[Index](index.md)
