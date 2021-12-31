**[*e_drone* for python](index.md)** / **Examples** / **Sensor**

Modified : 2021.12.29

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Altitude"></a>
## 고도 데이터 확인

```py
# 고도 데이터 확인
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_altitude(altitude):
    print("event_altitude()")
    print("-  Temperature: {0:.3f}".format(altitude.temperature))
    print("-     Pressure: {0:.3f}".format(altitude.pressure))
    print("-     Altitude: {0:.3f}".format(altitude.altitude))
    print("- Range Height: {0:.3f}".format(altitude.range_height))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.ALTITUDE, event_altitude)

    # Altitude 정보 요청
    drone.send_request(DeviceType.DRONE, DataType.ALTITUDE)
    sleep(0.1)

    drone.close()
```

- [Altitude](04_protocol.md#Altitude)
- [send_request()](05_drone.md#send_request)


<br>
<br>


<a name="Motion"></a>
## Motion 센서 데이터 확인

```py
# Motion 센서 데이터 확인
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_motion(motion):
    print("event_motion()")
    print("- Accel: {0:5}, {1:5}, {2:5}".format(motion.accel_x, motion.accel_y, motion.accel_z))
    print("-  Gyro: {0:5}, {1:5}, {2:5}".format(motion.gyro_roll, motion.gyro_pitch, motion.gyro_yaw))
    print("- Angle: {0:5}, {1:5}, {2:5}".format(motion.angle_roll, motion.angle_pitch, motion.angle_yaw))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.MOTION, event_motion)

    # Range 정보 요청
    drone.send_request(DeviceType.DRONE, DataType.MOTION)
    sleep(0.1)

    drone.close()
```

- [Motion](04_protocol.md#Motion)
- [send_request()](05_drone.md#send_request)


<br>
<br>


<a name="Attitude"></a>
## 자세 확인

```py
# 자세 확인
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def event_attitude(attitude):
    print("event_attitude() / {0:0.1f}, {1:0.1f}, {2:0.1f}".format(attitude.roll, attitude.pitch, attitude.yaw))


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.ATTITUDE, event_attitude)

    # Range 정보 요청
    drone.send_request(DeviceType.DRONE, DataType.ATTITUDE)
    sleep(0.1)

    drone.close()
```

- [Attitude](04_protocol.md#Attitude)
- [send_request()](05_drone.md#send_request)


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
10. **Examples - Sensor**
11. [Examples - Motor](examples_06_motor.md)
12. [Examples - Setup](examples_07_setup.md)
13. [Examples - Buzzer](examples_08_buzzer.md)
14. [Examples - Vibrator](examples_09_vibrator.md)
15. [Examples - Light](examples_10_light.md)
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
