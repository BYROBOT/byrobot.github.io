**[*petrone_v2* for python](index.md)** / **Examples** / **Light**

Modified : 2017.09.20

---

<br>


## <a name="LightManual">sendLightManual() 함수를 사용하여 조종기 LED 제어하기</a>

```py
import random
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    drone.sendLightManual(DeviceType.Controller, 0xFF, 0)
    sleep(1);
    
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Red.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Red.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Red.value, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Green.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Green.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Green.value, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Blue.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Blue.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, LightFlagsController.Blue.value, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b11000000, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b11000000, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b11000000, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b01100000, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b01100000, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b01100000, 0)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b10100000, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b10100000, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Controller, 0b10100000, 0)
    sleep(1);


    drone.close()
```

- [sendLightManual()](04_drone.md#sendLightManual)


<br>
<br>

## sendLightManual() 함수를 사용하여 드론 LED 제어하기

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    drone.sendLightManual(DeviceType.Drone, 0xFF, 0)
    sleep(1);


    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeRed.value | LightFlagsDrone.ArmRed.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeRed.value | LightFlagsDrone.ArmRed.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeRed.value | LightFlagsDrone.ArmRed.value, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeGreen.value | LightFlagsDrone.ArmGreen.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeGreen.value | LightFlagsDrone.ArmGreen.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeGreen.value | LightFlagsDrone.ArmGreen.value, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeBlue.value | LightFlagsDrone.ArmBlue.value, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeBlue.value | LightFlagsDrone.ArmBlue.value, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, LightFlagsDrone.EyeBlue.value | LightFlagsDrone.ArmBlue.value, 0)
    sleep(1);


    drone.sendLightManual(DeviceType.Drone, 0x82, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x82, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x82, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, 0x42, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x42, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x42, 0)
    sleep(1);

    drone.sendLightManual(DeviceType.Drone, 0x22, 10)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x22, 100)
    sleep(1);
    
    drone.sendLightManual(DeviceType.Drone, 0x22, 0)
    sleep(1);


    drone.close()
```

- [sendLightManual()](04_drone.md#sendLightManual)


<br>
<br>


## <a name="LightMode">sendLightMode, sendLightEvent 함수를 사용하여 조종기 LED 제어하기</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    drone.sendLightModeColor(LightModeController.TeamHold, 200, 0, 0, 0)
    sleep(2); 
    

    #sendLightModeColor*
    drone.sendLightModeColor(LightModeController.TeamDimming, 3, 200, 20, 20)
    sleep(1);
    
    drone.sendLightModeColorCommand(LightModeController.TeamHold, 200, 20, 200, 20, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightModeColorCommandIr(LightModeController.TeamFlicker, 200, 20, 20, 200, CommandType.None_, 0, 0x01020304)
    sleep(1);


    #sendLightModeColors*
    drone.sendLightModeColors(LightModeController.TeamDimming, 3, Colors.Red)
    sleep(1);
    
    drone.sendLightModeColorsCommand(LightModeController.TeamHold, 120, Colors.Green, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightModeColorsCommandIr(LightModeController.TeamFlicker, 200, Colors.Blue, CommandType.None_, 0, 0x01020304)
    sleep(1);


    # sendLightEventColor*
    drone.sendLightEventColor(LightModeController.TeamDimming, 3, 5, 200, 20, 20)
    sleep(1);
    
    drone.sendLightEventColorCommand(LightModeController.TeamHold, 120, 20, 20, 200, 20, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightEventColorCommandIr(LightModeController.TeamFlicker, 200, 5, 20, 20, 200, CommandType.None_, 0, 0x01020304)
    sleep(1);


    # sendLightEventColors*
    drone.sendLightEventColors(LightModeController.TeamDimming, 3, 3, Colors.Red)
    sleep(1);
    
    drone.sendLightEventColorsCommand(LightModeController.TeamHold, 200, 20, Colors.Green, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightEventColorsCommandIr(LightModeController.TeamFlicker, 200, 3, Colors.Blue, CommandType.None_, 0, 0x01020304)
    sleep(1);


    drone.close()
```

- [sendLightModeColor()](04_drone.md#sendLightModeColor)
- [sendLightModeColorCommand()](04_drone.md#sendLightModeColorCommand)
- [sendLightModeColorCommandIr()](04_drone.md#sendLightModeColorCommandIr)
- [sendLightModeColors()](04_drone.md#sendLightModeColors)
- [sendLightModeColorsCommand()](04_drone.md#sendLightModeColorsCommand)
- [sendLightModeColorsCommandIr()](04_drone.md#sendLightModeColorsCommandIr)
- [sendLightEventColor()](04_drone.md#sendLightEventColor)
- [sendLightEventColorCommand()](04_drone.md#sendLightEventColorCommand)
- [sendLightEventColorCommandIr()](04_drone.md#sendLightEventColorCommandIr)
- [sendLightEventColors()](04_drone.md#sendLightEventColors)
- [sendLightEventColorsCommand()](04_drone.md#sendLightEventColorsCommand)
- [sendLightEventColorsCommandIr()](04_drone.md#sendLightEventColorsCommandIr)


<br>
<br>


## sendLightMode, sendLightEvent 함수를 사용하여 드론 LED 제어하기


```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")


    drone.sendLightModeColor(LightModeDrone.ArmHold, 200, 0, 0, 0)
    sleep(1);


    # sendLightModeColor*
    drone.sendLightModeColor(LightModeDrone.ArmDimming, 3, 200, 20, 20)
    sleep(1);
    
    drone.sendLightModeColorCommand(LightModeDrone.ArmHold, 200, 20, 200, 20, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightModeColorCommandIr(LightModeDrone.ArmFlicker, 200, 20, 20, 200, CommandType.None_, 0, 0x01020304)
    sleep(1);


    # sendLightModeColors*
    drone.sendLightModeColors(LightModeDrone.ArmDimming, 3, Colors.Red)
    sleep(1);
    
    drone.sendLightModeColorsCommand(LightModeDrone.ArmHold, 120, Colors.Green, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightModeColorsCommandIr(LightModeDrone.ArmFlicker, 200, Colors.Blue, CommandType.None_, 0, 0x01020304)
    sleep(1);


    # sendLightEventColor*
    drone.sendLightEventColor(LightModeDrone.ArmDimming, 3, 5, 200, 20, 20)
    sleep(1);
    
    drone.sendLightEventColorCommand(LightModeDrone.ArmHold, 120, 20, 20, 200, 20, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightEventColorCommandIr(LightModeDrone.ArmFlicker, 200, 5, 20, 20, 200, CommandType.None_, 0, 0x01020304)
    sleep(1);


    # sendLightEventColors*
    drone.sendLightEventColors(LightModeDrone.ArmDimming, 3, 3, Colors.Red)
    sleep(1);
    
    drone.sendLightEventColorsCommand(LightModeDrone.ArmHold, 200, 20, Colors.Green, CommandType.None_, 0)
    sleep(1);
    
    drone.sendLightEventColorsCommandIr(LightModeDrone.ArmFlicker, 200, 5, Colors.Blue, CommandType.None_, 0, 0x01020304)
    sleep(1);


    drone.close()
```

- [sendLightModeColor()](04_drone.md#sendLightModeColor)
- [sendLightModeColorCommand()](04_drone.md#sendLightModeColorCommand)
- [sendLightModeColorCommandIr()](04_drone.md#sendLightModeColorCommandIr)
- [sendLightModeColors()](04_drone.md#sendLightModeColors)
- [sendLightModeColorsCommand()](04_drone.md#sendLightModeColorsCommand)
- [sendLightModeColorsCommandIr()](04_drone.md#sendLightModeColorsCommandIr)
- [sendLightEventColor()](04_drone.md#sendLightEventColor)
- [sendLightEventColorCommand()](04_drone.md#sendLightEventColorCommand)
- [sendLightEventColorCommandIr()](04_drone.md#sendLightEventColorCommandIr)
- [sendLightEventColors()](04_drone.md#sendLightEventColors)
- [sendLightEventColorsCommand()](04_drone.md#sendLightEventColorsCommand)
- [sendLightEventColorsCommandIr()](04_drone.md#sendLightEventColorsCommandIr)


<br>
<br>


## 조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColor / sendLightModeColor 함수 사용)

```py
import random
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    for i in range(0, 10, 1):
        
        r    = int(random.randint(0, 255))
        g    = int(random.randint(0, 255))
        b    = int(random.randint(0, 255))

        dataArray = drone.sendLightModeColor(LightModeController.TeamDimming, 1, r, g, b)
        print("{0} / {1}".format(i, dataArray))

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

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    header = Header()
    
    header.dataType = DataType.LightModeColor
    header.length   = LightModeColor.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = LightModeColor()

    data.mode.mode      = LightModeController.TeamDimming.value
    data.mode.interval  = 1

    for i in range(0, 10, 1):
        
        data.color.r    = int(random.randint(0, 255))
        data.color.g    = int(random.randint(0, 255))
        data.color.b    = int(random.randint(0, 255))

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, dataArray))

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

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    for i in range(0, 10, 1):
        
        colors = Colors(random.randint(0, Colors.EndOfType.value))

        dataArray = drone.sendLightModeColors(LightModeController.TeamDimming, 1, colors)
        print("{0} / {1}".format(i, dataArray))

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

from petrone_v2.drone import *
from petrone_v2.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    header = Header()
    
    header.dataType = DataType.LightModeColors
    header.length   = LightModeColors.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = LightModeColors()

    data.mode.mode      = LightModeController.TeamDimming.value
    data.mode.interval  = 1

    for i in range(0, 10, 1):
        
        data.colors    = Colors(random.randint(0, Colors.EndOfType.value))

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, dataArray))

        sleep(0.6)
    
    drone.close()
```

- [LightModeColors](03_protocol.md#LightModeColors)


<br>
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
13. [Examples - Vibrator](examples_09_vibrator.md)
14. **Examples - Light**
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
