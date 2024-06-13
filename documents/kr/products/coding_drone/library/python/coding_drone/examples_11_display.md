**[*CodingDrone* for python](index.md)** / **Examples** / **Display**

Modified : 2024.6.13

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="DisplayAll"></a>
## 모든 디스플레이 제어 명령을 차례대로 실행

```py
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    delay = 0.5
    
    drone.sendDisplayClearAll(DisplayPixel.Black)
    sleep(delay)

    drone.sendDisplayClear(59, 27, 10, 10, DisplayPixel.White)
    sleep(delay)

    drone.sendDisplayInvert(54, 22, 20, 20)
    sleep(delay)

    drone.sendDisplayDrawPoint(64, 32, DisplayPixel.White)
    sleep(delay)

    drone.sendDisplayDrawLine(10, 10, 118, 54, DisplayPixel.White, DisplayLine.Dotted)
    sleep(delay)

    drone.sendDisplayDrawRect(44, 12, 40, 40, DisplayPixel.White, False, DisplayLine.Dashed)
    sleep(delay)

    drone.sendDisplayDrawCircle(64, 32, 20, DisplayPixel.White, True)
    sleep(delay)
    
    drone.sendDisplayDrawString(10, 10, "HELLO", DisplayFont.LiberationMono5x8, DisplayPixel.White)
    sleep(delay)
    
    drone.sendDisplayDrawStringAlign(0, 128, 30, "CodingDrone", DisplayAlign.Center, DisplayFont.LiberationMono10x16, DisplayPixel.White)
    sleep(delay)
    
    drone.close()
```

- [sendDisplayClearAll()](05_drone.md#sendDisplayClearAll)
- [sendDisplayClear()](05_drone.md#sendDisplayClear)
- [sendDisplayInvert()](05_drone.md#sendDisplayInvert)
- [sendDisplayDrawPoint()](05_drone.md#sendDisplayDrawPoint)
- [sendDisplayDrawLine()](05_drone.md#sendDisplayDrawLine)
- [sendDisplayDrawRect()](05_drone.md#sendDisplayDrawRect)
- [sendDisplayDrawCircle()](05_drone.md#sendDisplayDrawCircle)
- [sendDisplayDrawString()](05_drone.md#sendDisplayDrawString)
- [sendDisplayDrawStringAlign()](05_drone.md#sendDisplayDrawStringAlign)


<br>
<br>


<a name="DisplayClear"></a>
## 무작위 위치와 크기의 Clear를 100회 전송 (sendDisplayClear 함수 사용)

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 100, 1):

        width      = int(random.randint(0, 127))
        height     = int(random.randint(0, 63))
        x          = int(random.randint(0, 127) - width / 2)
        y          = int(random.randint(0, 63) - height / 2)
        pixel      = DisplayPixel(int(random.randint(0, 1)))

        dataArray = drone.sendDisplayClear(x, y, width, height, pixel)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.03)
    
    drone.close()
```

- [sendDisplayClear()](05_drone.md#sendDisplayClear)


<br>
<br>


## 무작위 위치와 크기의 Clear를 100회 전송 (클래스 데이터 채워서 전송)

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.dataType = DataType.DisplayClear
    header.length   = DisplayClear.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = DisplayClear()

    for i in range(0, 100, 1):

        data.width      = int(random.randint(0, 127))
        data.height     = int(random.randint(0, 63))
        data.x          = int(random.randint(0, 127) - data.width / 2)
        data.y          = int(random.randint(0, 63) - data.height / 2)
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.03)
    
    drone.close()
```

- [DisplayClear](04_protocol.md#DisplayClear)


<br>
<br>


<a name="DisplayDrawLine"></a>
## 무작위 위치와 길이의 선을 100번 그리기 (sendDisplayDrawLine 함수 사용)

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()
    
    drone.sendDisplayClearAll(DisplayPixel(int(random.randint(0, 1))))
    sleep(0.1)

    for i in range(0, 100, 1):

        x1          = int(random.randint(0, 127))
        y1          = int(random.randint(0, 63))
        x2          = int(random.randint(0, 127))
        y2          = int(random.randint(0, 63))
        pixel       = DisplayPixel(int(random.randint(0, 1)))
        line        = DisplayLine(int(random.randint(0, 2)))

        dataArray = drone.sendDisplayDrawLine(x1, y1, x2, y2, pixel, line)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.02)
    
    drone.close()
```

- [sendDisplayClearAll()](05_drone.md#sendDisplayClearAll)
- [sendDisplayDrawLine()](05_drone.md#sendDisplayDrawLine)


<br>
<br>


<a name="DisplayDrawCircle"></a>
## 무작위 위치와 크기의 원을 100번 출력하기 (sendDisplayDrawCircle 함수 사용)

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone(True, False, False, True, True)
    drone.open()

    for i in range(0, 100, 1):

        x          = int(random.randint(0, 127))
        y          = int(random.randint(0, 63))
        radius     = int(random.randint(0, 63))
        pixel      = DisplayPixel(int(random.randint(0, 1)))
        flagFill   = bool(random.randint(0, 1))

        drone.sendDisplayDrawCircle(x, y, radius, pixel, flagFill)
        sleep(0.05)

    drone.close()
```

- [sendDisplayDrawCircle()](05_drone.md#sendDisplayDrawCircle)


<br>
<br>


## 무작위 위치와 크기의 원을 100번 출력하기 (클래스 데이터 채워서 전송)

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':
    
    drone = Drone()
    drone.open()

    header = Header()

    header.dataType = DataType.DisplayDrawCircle
    header.length   = DisplayDrawCircle.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = DisplayDrawCircle()

    for i in range(0, 100, 1):

        data.x          = int(random.randint(0, 127))
        data.y          = int(random.randint(0, 63))
        data.radius     = int(random.randint(0, 63))
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.flagFill   = bool(random.randint(0, 1))

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.03)
    
    drone.close()

```

- [DisplayDrawCircle](04_protocol.md#DisplayDrawCircle)


<br>
<br>


<a name="DisplayDrawRect"></a>
## 무작위 위치와 크기의 사각형을 100번 출력하기 (sendDisplayDrawRect 함수 사용)

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    for i in range(0, 100, 1):

        width      = int(random.randint(0, 127))
        height     = int(random.randint(0, 63))
        x          = int(random.randint(0, 127) - width / 2)
        y          = int(random.randint(0, 63) - height / 2)
        pixel      = DisplayPixel(int(random.randint(0, 1)))
        flagFill   = bool(random.randint(0, 1))
        line       = DisplayLine(int(random.randint(0, 2)))

        dataArray = drone.sendDisplayDrawRect(x, y, width, height, pixel, flagFill, line)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.03)
    
    drone.close()
```

- [sendDisplayDrawRect()](05_drone.md#sendDisplayDrawRect)


<br>
<br>


## 무작위 위치와 크기의 사각형을 100번 출력하기 (클래스 데이터 채워서 전송)

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()
    
    header.dataType = DataType.DisplayDrawRect
    header.length   = DisplayDrawRect.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = DisplayDrawRect()

    for i in range(0, 100, 1):

        data.width      = int(random.randint(0, 127))
        data.height     = int(random.randint(0, 63))
        data.x          = int(random.randint(0, 127) - data.width / 2)
        data.y          = int(random.randint(0, 63) - data.height / 2)
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.flagFill   = bool(random.randint(0, 1))
        data.line       = DisplayLine(int(random.randint(0, 2)))

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

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

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':
    
    drone = Drone()
    drone.open()

    header = Header()

    header.dataType = DataType.DisplayDrawString
    header.length   = DisplayDrawString.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = DisplayDrawString()

    for i in range(0, 100, 1):

        data.x          = int(random.randint(0, 127))
        data.y          = int(random.randint(0, 63))
        data.font       = DisplayFont(int(random.randint(0, 1)))
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.message    = "HELLO"
        
        header.length   = DisplayDrawString.getSize() + len(data.message)

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.03)
    
    drone.close()
```

- [DisplayDrawString](04_protocol.md#DisplayDrawString)


<br>
<br>


<a name="DisplayDrawStringAlign"></a>
## 'LOVE' 문자열을 왼쪽, 중앙, 오른쪽 정렬을 사용하여 무작위 위치에 10번 출력하기

```py
import random
from time import sleep

from CodingDrone.drone import *
from CodingDrone.protocol import *


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    header = Header()

    header.dataType = DataType.DisplayDrawStringAlign
    header.length   = DisplayDrawStringAlign.getSize()
    header.from_    = DeviceType.Tester
    header.to_      = DeviceType.Controller

    data = DisplayDrawStringAlign()

    for i in range(0, 10, 1):

        data.x_start    = 0
        data.x_end      = 127
        data.y          = int(random.randint(0, 63))
        data.align      = DisplayAlign(int(random.randint(0, 2)))
        data.font       = DisplayFont(int(random.randint(0, 1)))
        data.pixel      = DisplayPixel(int(random.randint(0, 1)))
        data.message    = "LOVE"

        header.length   = DisplayDrawStringAlign.getSize() + len(data.message)

        dataArray = drone.transfer(header, data)
        print("{0} / {1}".format(i, convertByteArrayToString(dataArray)))

        sleep(0.03)

    drone.close()
```

- [DisplayDrawStringAlign](04_protocol.md#DisplayDrawStringAlign)


<br>


---

<h3><i>CodingDrone</i> for python</H3>

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
