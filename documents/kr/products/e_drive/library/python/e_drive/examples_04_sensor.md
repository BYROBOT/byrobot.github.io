**[*e_drive* for python](index.md)** / **Examples** / **Sensor**

Modified : 2019.4.15

---

<br>


## <a name="Altitude">고도 데이터 확인</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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


## <a name="Motion">Motion 센서 데이터 확인</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


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


## <a name="Attitude">자세 확인</a>

```py
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


def eventAttitude(attitude):
    print("eventAttitude() / {0:0.1f}, {1:0.1f}, {2:0.1f}".format(attitude.roll, attitude.pitch, attitude.yaw))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Attitude, eventAttitude)

    # Range 정보 요청
    drone.sendRequest(DeviceType.Drone, DataType.Attitude)
    sleep(0.1)

    drone.close()
```

- [Attitude](03_protocol.md#Attitude)
- [sendRequest()](04_drone.md#sendRequest)


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
 9. **Examples - Sensor**
10. [Examples - Motor](examples_05_motor.md)
11. [Examples - Setup](examples_06_setup.md)
12. [Examples - Buzzer](examples_07_buzzer.md)
13. [Examples - Light](examples_08_light.md)
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
