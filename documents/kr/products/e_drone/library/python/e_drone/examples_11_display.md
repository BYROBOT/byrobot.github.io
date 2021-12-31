**[*e_drone* for python](index.md)** / **Examples** / **Display**

Modified : 2021.12.31

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="DisplayAll"></a>
## 모든 디스플레이 제어 명령을 차례대로 실행

```py
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    delay = 0.5
    
    drone.send_display_clear_all(DisplayPixel.BLACK)
    sleep(delay)

    drone.send_display_clear(59, 27, 10, 10, DisplayPixel.WHITE)
    sleep(delay)

    drone.send_display_invert(54, 22, 20, 20)
    sleep(delay)

    drone.send_display_draw_point(64, 32, DisplayPixel.WHITE)
    sleep(delay)

    drone.send_display_draw_line(10, 10, 118, 54, DisplayPixel.WHITE, DisplayLine.DOTTED)
    sleep(delay)

    drone.send_display_draw_rect(44, 12, 40, 40, DisplayPixel.WHITE, False, DisplayLine.DASHED)
    sleep(delay)

    drone.send_display_draw_circle(64, 32, 20, DisplayPixel.WHITE, True)
    sleep(delay)
    
    drone.send_display_draw_string(10, 10, "HELLO", DisplayFont.LIBERATION_MONO_5X8, DisplayPixel.WHITE)
    sleep(delay)
    
    drone.send_display_draw_string_align(0, 128, 30, "E-DRONE", DisplayAlign.CENTER, DisplayFont.LIBERATION_MONO_10X16, DisplayPixel.WHITE)
    sleep(delay)
    
    drone.close()
```

- [send_display_clear_all()](05_drone.md#send_display_clear_all)
- [send_display_clear()](05_drone.md#send_display_clear)
- [send_display_invert()](05_drone.md#send_display_invert)
- [send_display_draw_point()](05_drone.md#send_display_draw_point)
- [send_display_draw_line()](05_drone.md#send_display_draw_line)
- [send_display_draw_rect()](05_drone.md#send_display_draw_rect)
- [send_display_draw_circle()](05_drone.md#send_display_draw_circle)
- [send_display_draw_string()](05_drone.md#send_display_draw_string)
- [send_display_draw_string_align()](05_drone.md#send_display_draw_string_align)


<br>
<br>


<a name="DisplayClear"></a>
## 무작위 위치와 크기의 Clear를 100회 전송 (send_display_clear 함수 사용)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 100, 1):

        width      = int(random.randint(0, 127))
        height     = int(random.randint(0, 63))
        x          = int(random.randint(0, 127) - width / 2)
        y          = int(random.randint(0, 63) - height / 2)
        pixel      = DisplayPixel(int(random.randint(0, 1)))

        data_array = drone.send_display_clear(x, y, width, height, pixel)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.03)
    
    drone.close()
```

- [send_display_clear()](05_drone.md#send_display_clear)


<br>
<br>


## 무작위 위치와 크기의 Clear를 100회 전송 (클래스 데이터 채워서 전송)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.data_type = DataType.DISPLAY_CLEAR
    header.length    = DisplayClear.get_size()
    header.from_     = DeviceType.BASE
    header.to_       = DeviceType.CONTROLLER

    data = DisplayClear()

    for i in range(0, 100, 1):

        data.width      = int(random.randint(0, 127))
        data.height     = int(random.randint(0, 63))
        data.x          = int(random.randint(0, 127) - data.width / 2)
        data.y          = int(random.randint(0, 63) - data.height / 2)
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))

        data_array = drone.transfer(header, data)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.03)
    
    drone.close()
```

- [DisplayClear](04_protocol.md#DisplayClear)


<br>
<br>


<a name="DisplayDrawLine"></a>
## 무작위 위치와 길이의 선을 100번 그리기 (send_display_draw_line 함수 사용)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()
    
    drone.send_display_clear_all(DisplayPixel(int(random.randint(0, 1))))
    sleep(0.1)

    for i in range(0, 100, 1):

        x1          = int(random.randint(0, 127))
        y1          = int(random.randint(0, 63))
        x2          = int(random.randint(0, 127))
        y2          = int(random.randint(0, 63))
        pixel       = DisplayPixel(int(random.randint(0, 1)))
        line        = DisplayLine(int(random.randint(0, 2)))

        data_array = drone.send_display_draw_line(x1, y1, x2, y2, pixel, line)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.02)
    
    drone.close()
```

- [send_display_clear_all()](05_drone.md#send_display_clear_all)
- [send_display_draw_line()](05_drone.md#send_display_draw_line)


<br>
<br>


<a name="DisplayDrawCircle"></a>
## 무작위 위치와 크기의 원을 100번 출력하기 (send_display_draw_circle 함수 사용)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone(True, False, False, True, True)
    drone.open()

    for i in range(0, 100, 1):

        x          = int(random.randint(0, 127))
        y          = int(random.randint(0, 63))
        radius     = int(random.randint(0, 63))
        pixel      = DisplayPixel(int(random.randint(0, 1)))
        flag_fill  = bool(random.randint(0, 1))

        drone.send_display_draw_circle(x, y, radius, pixel, flag_fill)
        sleep(0.05)

    drone.close()
```

- [send_display_draw_circle()](05_drone.md#send_display_draw_circle)


<br>
<br>


## 무작위 위치와 크기의 원을 100번 출력하기 (클래스 데이터 채워서 전송)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':
    
    drone = Drone()
    drone.open()

    header = Header()

    header.data_type = DataType.DISPLAY_DRAW_CIRCLE
    header.length    = DisplayDrawCircle.get_size()
    header.from_     = DeviceType.BASE
    header.to_       = DeviceType.CONTROLLER

    data = DisplayDrawCircle()

    for i in range(0, 100, 1):

        data.x          = int(random.randint(0, 127))
        data.y          = int(random.randint(0, 63))
        data.radius     = int(random.randint(0, 63))
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.flag_fill   = bool(random.randint(0, 1))

        data_array = drone.transfer(header, data)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.03)
    
    drone.close()

```

- [DisplayDrawCircle](04_protocol.md#DisplayDrawCircle)


<br>
<br>


<a name="DisplayDrawRect"></a>
## 무작위 위치와 크기의 사각형을 100번 출력하기 (send_display_draw_rect 함수 사용)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 100, 1):

        width      = int(random.randint(0, 127))
        height     = int(random.randint(0, 63))
        x          = int(random.randint(0, 127) - width / 2)
        y          = int(random.randint(0, 63) - height / 2)
        pixel      = DisplayPixel(int(random.randint(0, 1)))
        flag_fill  = bool(random.randint(0, 1))
        line       = DisplayLine(int(random.randint(0, 2)))

        data_array = drone.send_display_draw_rect(x, y, width, height, pixel, flag_fill, line)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.03)
    
    drone.close()
```

- [send_display_draw_rect()](05_drone.md#send_display_draw_rect)


<br>
<br>


## 무작위 위치와 크기의 사각형을 100번 출력하기 (클래스 데이터 채워서 전송)

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.data_type = DataType.DISPLAY_DRAW_RECT
    header.length    = DisplayDrawRect.get_size()
    header.from_     = DeviceType.BASE
    header.to_       = DeviceType.CONTROLLER

    data = DisplayDrawRect()

    for i in range(0, 100, 1):

        data.width      = int(random.randint(0, 127))
        data.height     = int(random.randint(0, 63))
        data.x          = int(random.randint(0, 127) - data.width / 2)
        data.y          = int(random.randint(0, 63) - data.height / 2)
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.flag_fill  = bool(random.randint(0, 1))
        data.line       = DisplayLine(int(random.randint(0, 2)))

        data_array = drone.transfer(header, data)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.03)
    
    drone.close()
```

- [DisplayDrawRect](04_protocol.md#DisplayDrawRect)


<br>
<br>


<a name="DisplayDrawString"></a>
## 'HELLO' 문자열을 무작위 위치에 100번 출력하기

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':
    
    drone = Drone()
    drone.open()

    header = Header()

    header.data_type = DataType.DISPLAY_DRAW_STRING
    header.length   = DisplayDrawString.get_size()
    header.from_    = DeviceType.BASE
    header.to_      = DeviceType.CONTROLLER

    data = DisplayDrawString()

    for i in range(0, 100, 1):

        data.x          = int(random.randint(0, 127))
        data.y          = int(random.randint(0, 63))
        data.font       = DisplayFont(int(random.randint(0, 1)))
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.message    = "HELLO"
        
        header.length   = DisplayDrawString.get_size() + len(data.message)

        data_array = drone.transfer(header, data)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.03)
    
    drone.close()
```

- [DisplayDrawString](04_protocol.md#DisplayDrawString)


<br>
<br>


<a name="DisplayDrawStringAlign"></a>
## 'LOVE' 문자열을 왼쪽, 중앙, 오른쪽 정렬을 사용하여 무작위 위치에 100번 출력하기

```py
import random
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()

    header.data_type = DataType.DISPLAY_DRAW_STRING_ALIGN
    header.length    = DisplayDrawStringAlign.get_size()
    header.from_     = DeviceType.BASE
    header.to_       = DeviceType.CONTROLLER

    data = DisplayDrawStringAlign()

    for i in range(0, 100, 1):

        data.x_start    = 0
        data.x_end      = 127
        data.y          = int(random.randint(0, 63))
        data.align      = DisplayAlign(int(random.randint(0, 2)))
        data.font       = DisplayFont(int(random.randint(0, 1)))
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.message    = "LOVE"

        header.length   = DisplayDrawStringAlign.get_size() + len(data.message)

        data_array = drone.transfer(header, data)
        print("{0} / {1}".format(i, convert_byte_array_to_string(data_array)))

        sleep(0.03)

    drone.close()
```

- [DisplayDrawStringAlign](04_protocol.md#DisplayDrawStringAlign)


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
15. [Examples - Light](examples_10_light.md)
16. **Examples - Display**
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
