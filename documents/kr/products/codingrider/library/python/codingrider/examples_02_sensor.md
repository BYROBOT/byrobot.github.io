**[*CodingRider* for python](index.md)** / **Examples** / **Sensor**

Modified : 2024.5.23

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Altitude"></a>
## 고도 데이터 확인

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


def eventAltitude(altitude):
    print("eventAltitude()")
    print("-  Temperature: {0:.3f}".format(altitude.temperature))
    print("-     Pressure: {0:.3f}".format(altitude.pressure))
    print("-     Altitude: {0:.3f}".format(altitude.altitude))
    print("- Range Height: {0:.3f}".format(altitude.rangeHeight))

if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Altitude, eventAltitude)

    # Altitude 정보 요청
    drone.sendRequest(DeviceType.Drone, DataType.Altitude)
    sleep(0.1)

    drone.close()
```

- [Altitude](03_protocol.md#Altitude)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


<a name="Motion"></a>
## Motion 센서 데이터 확인

```py
from time import sleep

from CodingRider.drone import *
from CodingRider.protocol import *


def eventMotion(motion):
    print("eventMotion()")
    print("- Accel: {0:5}, {1:5}, {2:5}".format(motion.accelX, motion.accelY, motion.accelZ))
    print("-  Gyro: {0:5}, {1:5}, {2:5}".format(motion.gyroRoll, motion.gyroPitch, motion.gyroYaw))
    print("- Angle: {0:5}, {1:5}, {2:5}".format(motion.angleRoll, motion.anglePitch, motion.angleYaw))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Motion, eventMotion)

    # Range 정보 요청
    drone.sendRequest(DeviceType.Drone, DataType.Motion)
    sleep(0.1)

    drone.close()
```

- [Motion](03_protocol.md#Motion)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>




---

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Control](examples_01_control.md)
 6. **Examples - Sensor**
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Light](examples_05_light.md)
10. [Examples - Input](examples_06_input.md)
11. [Examples - Information](examples_07_information.md)
<br>

[Index](index.md)
