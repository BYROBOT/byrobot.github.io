**[*e_drone* for python](index.md)** / **Examples** / **Light**

Modified : 2021.12.31

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="LightManual"></a>
## send_light_manual() 함수를 사용하여 조종기와 드론 LED 제어하기

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.send_light_manual(DeviceType.CONTROLLER, 0xFF, 0)
    sleep(1)


    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000011, 10);     sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000011, 100);    sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000011, 0);      sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000110, 10);     sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000110, 100);    sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000110, 0);      sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000101, 10);     sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000101, 100);    sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, 0b00000101, 0);      sleep(1)

    drone.send_light_manual(DeviceType.DRONE, 0b00000110, 10);     sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00000110, 100);    sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00000110, 0);      sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00001100, 10);     sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00001100, 100);    sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00001100, 0);      sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00001010, 10);     sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00001010, 100);    sleep(1)
    drone.send_light_manual(DeviceType.DRONE, 0b00001010, 0);      sleep(1)


    drone.close()
```

- [send_light_manual()](05_drone.md#send_light_manual)


<br>
<br>


<a name="LightManualColorFlag"></a>
## send_light_manual() 함수를 사용하여 조종기와 드론 LED 제어하기

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()


    drone.send_light_manual(DeviceType.CONTROLLER, 0xFF, 0)
    sleep(1)


    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_RED.value, 10);        sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_RED.value, 100);       sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_RED.value, 0);         sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_GREEN.value, 10);      sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_GREEN.value, 100);     sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_GREEN.value, 0);       sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_BLUE.value, 10);       sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_BLUE.value, 100);      sleep(1)
    drone.send_light_manual(DeviceType.CONTROLLER, LightFlagsController.BODY_BLUE.value, 0);        sleep(1)


    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_RED.value, 10);        sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_RED.value, 100);       sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_RED.value, 0);         sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_GREEN.value, 10);      sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_GREEN.value, 100);     sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_GREEN.value, 0);       sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_BLUE.value, 10);       sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_BLUE.value, 100);      sleep(1)
    drone.send_light_manual(DeviceType.DRONE, LightFlagsDrone.BODY_BLUE.value, 0);        sleep(1)


    drone.close()
```

- [send_light_manual()](05_drone.md#send_light_manual)


<br>
<br>


<a name="LightMode"></a>
## Light 모드, 이벤트 함수를 사용하여 드론과 조종기 LED 제어하기

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    print("BODY_HOLD - Turn off")
    drone.send_light_mode_color(DeviceType.DRONE, LightModeDrone.BODY_HOLD, 255, 0, 0, 0)
    drone.send_light_mode_color(DeviceType.CONTROLLER, LightModeController.BODY_HOLD, 255, 0, 0, 0)
    sleep(2)

    print("BODY_HOLD - Yellow")
    drone.send_light_mode_color(DeviceType.DRONE, LightModeDrone.BODY_HOLD, 255, 200, 200, 0)
    drone.send_light_mode_color(DeviceType.CONTROLLER, LightModeController.BODY_HOLD, 200, 200, 200, 0)
    sleep(2)


    # send_light_event_color*
    print("BODY_DIMMING 3 - White")
    drone.send_light_event_color(DeviceType.DRONE, LightModeDrone.BODY_DIMMING, 3, 3, 200, 200, 200)
    drone.send_light_event_color(DeviceType.CONTROLLER, LightModeController.BODY_DIMMING, 3, 3, 200, 200, 200)
    sleep(3)

    # send_light_event_colors*
    print("BODY_DIMMING 4 - Cyan")
    drone.send_light_event_colors(DeviceType.DRONE, LightModeDrone.BODY_DIMMING, 3, 3, Colors.CYAN)
    drone.send_light_event_colors(DeviceType.CONTROLLER, LightModeController.BODY_DIMMING, 3, 3, Colors.CYAN)
    sleep(3)


    #send_light_mode_color
    print("BODY_DIMMING 1 - Magenta")
    drone.send_light_mode_color(DeviceType.DRONE, LightModeDrone.BODY_DIMMING, 3, 200, 0, 200)
    drone.send_light_mode_color(DeviceType.CONTROLLER, LightModeController.BODY_DIMMING, 3, 200, 0, 200)
    sleep(3)

    #send_light_mode_colors
    print("BODY_DIMMING 2 - GreenYellow")
    drone.send_light_mode_colors(DeviceType.DRONE, LightModeDrone.BODY_DIMMING, 3, Colors.GREENYELLOW)
    drone.send_light_mode_colors(DeviceType.CONTROLLER, LightModeController.BODY_DIMMING, 3, Colors.GREENYELLOW)
    sleep(3)


    drone.close()
```

- [send_light_mode_color()](05_drone.md#send_light_mode_color)
- [send_light_mode_colors()](05_drone.md#send_light_mode_colors)
- [send_light_event_color()](05_drone.md#send_light_event_color)
- [send_light_event_colors()](05_drone.md#send_light_event_colors)


<br>
<br>


## 조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColor / send_light_mode_color 함수 사용)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 10, 1):
        
        r    = int(random.randint(0, 255))
        g    = int(random.randint(0, 255))
        b    = int(random.randint(0, 255))

        data_array = drone.send_light_mode_color(DeviceType.CONTROLLER, LightModeController.BODY_DIMMING, 1, r, g, b)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.6)
    
    drone.close()
```

- [send_light_mode_color()](05_drone.md#send_light_mode_color)


<br>
<br>


<a name="Class_LightModeColor"></a>
## 조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColor / 클래스 데이터를 채워서 전송)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.data_type = DataType.LIGHT_MODE
    header.length    = LightModeColor.get_size()
    header.from_     = DeviceType.BASE
    header.to_       = DeviceType.CONTROLLER

    data = LightModeColor()

    data.mode.mode      = LightModeController.BODY_DIMMING.value
    data.mode.interval  = 1

    for i in range(0, 10, 1):
        
        data.color.r    = int(random.randint(0, 255))
        data.color.g    = int(random.randint(0, 255))
        data.color.b    = int(random.randint(0, 255))

        data_array = drone.transfer(header, data)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.6)
    
    drone.close()
```

- [LightModeColor](04_protocol.md#LightModeColor)


<br>
<br>


## 조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / send_light_mode_colors 함수 사용)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 10, 1):
        
        colors = Colors(random.randint(0, Colors.END_OF_TYPE.value))

        data_array = drone.send_light_mode_colors(DeviceType.CONTROLLER, LightModeController.BODY_DIMMING, 1, colors)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.6)
    
    drone.close()
```

- [send_light_mode_colors()](05_drone.md#send_light_mode_colors)


<br>
<br>


<a name="Class_LightModeColors"></a>
## 조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / 클래스 데이터를 채워서 전송)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.data_type = DataType.LIGHT_MODE
    header.length    = LightModeColors.get_size()
    header.from_     = DeviceType.BASE
    header.to_       = DeviceType.CONTROLLER

    data = LightModeColors()

    data.mode.mode      = LightModeController.BODY_DIMMING.value
    data.mode.interval  = 1

    for i in range(0, 10, 1):
        
        data.colors    = Colors(random.randint(0, Colors.END_OF_TYPE.value))

        data_array = drone.transfer(header, data)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.6)
    
    drone.close()
```

- [LightModeColors](04_protocol.md#LightModeColors)


<br>
<br>


<a name="Class_LightDefaultModeColor"></a>
## 드론의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / sendLightDefaultColor 함수 사용)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone(True, True, True, True, True)
    drone.open()

    for i in range(0, 10, 1):
        
        r    = int(random.randint(0, 255))
        g    = int(random.randint(0, 255))
        b    = int(random.randint(0, 255))

        data_array = drone.sendLightDefaultColor(LightModeDrone.BodyDimming, 1, r, g, b)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(2)
    
    drone.close()
```

- [LightModeColor](04_protocol.md#LightModeColor)
- [sendLightDefaultColor()](05_drone.md#sendLightDefaultColor)


<br>
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
14. [Examples - Vibrator](examples_09_vibrator.md)
15. **Examples - Light**
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
