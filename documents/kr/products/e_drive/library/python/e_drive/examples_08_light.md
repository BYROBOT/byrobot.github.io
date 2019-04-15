**[*e_drive* for python](index.md)** / **Examples** / **Light**

Modified : 2019.4.15

---

<br>


## <a name="LightManual">sendLightManual() 함수를 사용하여 조종기 LED 제어하기</a>

```py
import random
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.sendLightManual(DeviceType.Controller, 0xFF, 0)
    sleep(1);
    
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyRed.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyRed.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyRed.value, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyGreen.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyGreen.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyGreen.value, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyBlue.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyBlue.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.BodyBlue.value, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000011, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000011, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000011, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000110, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000110, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000110, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000101, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000101, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b00000101, 0)
    sleep(1);


    drone.close()
```

- [sendLightManual()](04_drone.md#sendLightManual)


<br>
<br>

## sendLightManual() 함수를 사용하여 드론 LED 제어하기

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.sendLightManual(DeviceType.Drone, 0xFF, 0)
    sleep(1);


    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyRed.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyRed.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyRed.value, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyGreen.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyGreen.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyGreen.value, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyBlue.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyBlue.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.BodyBlue.value, 0)
    sleep(1);


    drone.sendLightManual(DeviceType.Drone, 0x06, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x06, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x06, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, 0x0A, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x0A, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x0A, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, 0x0C, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x0C, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x0C, 0)
    sleep(1);


    drone.close()
```

- [sendLightManual()](04_drone.md#sendLightManual)


<br>
<br>


## <a name="LightMode">sendLightMode, sendLightEvent 함수를 사용하여 조종기 LED 제어하기</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    print("BodyHold")
    drone.sendLightModeColor(LightModeController.BodyHold, 200, 200, 200, 0)
    sleep(2); 
    

    #sendLightModeColor
    print("BodyDimming 1")
    drone.sendLightModeColor(LightModeController.BodyDimming, 3, 200, 0, 200)
    sleep(3);
    
    #sendLightModeColors
    print("BodyDimming 2")
    drone.sendLightModeColors(LightModeController.BodyDimming, 3, Colors.Cyan)
    sleep(3);
    

    # sendLightEventColor*
    print("BodyDimming 3")
    drone.sendLightEventColor(LightModeController.BodyDimming, 3, 3, 200, 200, 200)
    sleep(3);
    
    # sendLightEventColors*
    print("BodyDimming 4")
    drone.sendLightEventColors(LightModeController.BodyDimming, 3, 3, Colors.Magenta)
    sleep(3);
    

    drone.close()
```

- [sendLightModeColor()](04_drone.md#sendLightModeColor)
- [sendLightModeColors()](04_drone.md#sendLightModeColors)
- [sendLightEventColor()](04_drone.md#sendLightEventColor)
- [sendLightEventColors()](04_drone.md#sendLightEventColors)


<br>
<br>


## sendLightMode, sendLightEvent 함수를 사용하여 드론 LED 제어하기


```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.sendLightModeColor(LightModeDrone.BodyHold, 200, 0, 200, 200)
    sleep(1);


    # sendLightModeColor*
    drone.sendLightModeColor(LightModeDrone.BodyDimming, 3, 0, 0, 200)
    sleep(3);
    
    # sendLightModeColors*
    drone.sendLightModeColors(LightModeDrone.BodyDimming, 3, Colors.Cyan)
    sleep(3);
    

    # sendLightEventColor*
    drone.sendLightEventColor(LightModeDrone.BodyDimming, 3, 5, 200, 200, 200)
    sleep(3);
    
    # sendLightEventColors*
    drone.sendLightEventColors(LightModeDrone.BodyDimming, 3, 3, Colors.Magenta)
    sleep(3);
    

    drone.close()
```

- [sendLightModeColor()](04_drone.md#sendLightModeColor)
- [sendLightModeColors()](04_drone.md#sendLightModeColors)
- [sendLightEventColor()](04_drone.md#sendLightEventColor)
- [sendLightEventColors()](04_drone.md#sendLightEventColors)


<br>
<br>


## 조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColor / sendLightModeColor 함수 사용)

```py
import random
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 10, 1):
        
        r    = int(random.randint(0, 255))
        g    = int(random.randint(0, 255))
        b    = int(random.randint(0, 255))

        dataArray = drone.sendLightModeColor(LightModeController.BodyDimming, 1, r, g, b)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.6)
    
    drone.close()
```

- [sendLightModeColor()](04_drone.md#sendLightModeColor)


<br>
<br>


## <a name="Class_LightModeColor">조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColor / 클래스 데이터를 채워서 전송)</a>

```py
import random
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.dataType = DataType.LightMode
    header.length   = LightModeColor.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = LightModeColor()

    data.mode.mode      = LightModeController.BodyDimming.value
    data.mode.interval  = 1

    for i in range(0, 10, 1):
        
        data.color.r    = int(random.randint(0, 255))
        data.color.g    = int(random.randint(0, 255))
        data.color.b    = int(random.randint(0, 255))

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.6)
    
    drone.close()
```

- [LightModeColor](03_protocol.md#LightModeColor)


<br>
<br>


## 조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / sendLightModeColors 함수 사용)

```py
import random
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 10, 1):
        
        colors = Colors(random.randint(0, Colors.EndOfType.value))

        dataArray = drone.sendLightModeColors(LightModeController.BodyDimming, 1, colors)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.6)
    
    drone.close()
```

- [sendLightModeColors()](04_drone.md#sendLightModeColors)


<br>
<br>


## <a name="Class_LightModeColors">조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / 클래스 데이터를 채워서 전송)</a>

```py
import random
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.dataType = DataType.LightMode
    header.length   = LightModeColors.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = LightModeColors()

    data.mode.mode      = LightModeController.BodyDimming.value
    data.mode.interval  = 1

    for i in range(0, 10, 1):
        
        data.colors    = Colors(random.randint(0, Colors.EndOfType.value))

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.6)
    
    drone.close()
```

- [LightModeColors](03_protocol.md#LightModeColors)


<br>
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
12. [Examples - Buzzer](examples_07_buzzer.md)
13. **Examples - Light**
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
