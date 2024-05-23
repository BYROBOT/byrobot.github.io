**[*petrone_v2* for python](index.md)** / **Examples** / **Sensor**

Modified : 2017.10.27

---

<br>


## <a name="Pressure">압력 센서 데이터 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventPressure(pressure):
    print("eventPressure()")
    print("-    Pressure: {0:.3f}".format(pressure.pressure))
    print("- Temperature: {0:.3f}".format(pressure.temperature))

if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Pressure, eventPressure)

    # Pressure 정보 요청
    drone.sendRequest(DeviceType.Drone, DataType.Pressure)
    sleep(0.1)

    drone.close()
```

- [Pressure](03_protocol.md#Pressure)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="Range">거리 센서 데이터 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventRange(range):
    print("eventRange()")
    print("- Bottom: {0:0.3f}m".format(range.bottom))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Range, eventRange)

    # Range 정보 요청
    drone.sendRequest(DeviceType.Drone, DataType.Range)
    sleep(0.1)

    drone.close()
```

- [Range](03_protocol.md#Range)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="Imu">IMU 센서 데이터 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventImu(imu):
    print("eventImu()")
    print("- Accel: {0:5}, {1:5}, {2:5}".format(imu.accelX, imu.accelY, imu.accelZ))
    print("-  Gyro: {0:5}, {1:5}, {2:5}".format(imu.gyroRoll, imu.gyroPitch, imu.gyroYaw))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Imu, eventImu)

    # Range 정보 요청
    drone.sendRequest(DeviceType.Drone, DataType.Imu)
    sleep(0.1)

    drone.close()
```

- [Imu](03_protocol.md#Imu)
- [sendRequest()](04_drone.md#sendRequest)


<br>
<br>


## <a name="Attitude">자세 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventAttitude(attitude):
    print("eventAttitude() / {0:0.1f}, {1:0.1f}, {2:0.1f}".format(attitude.roll, attitude.pitch, attitude.yaw))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

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
<br>


## <a name="IrMessage">적외선 데이터 송수신 확인</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def eventIrMessage(irMessage):
    print("eventIrMessage()")
    print("{0} / 0x{1:8X} / {1}".format(irMessage.direction, irMessage.irData))


if __name__ == '__main__':

    drone = Drone()
    drone.open("COM22")

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.IrMessage, eventIrMessage)

    # 적외선 데이터 전송
    drone.sendIrMessage(0x12345678)
    sleep(0.2)

    drone.close()
```

- [IrMessage](03_protocol.md#IrMessage)
- [sendRequest()](04_drone.md#sendRequest)


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
 9. **Examples - Sensor**
10. [Examples - Motor](examples_06_motor.md)
11. [Examples - Setup](examples_07_setup.md)
12. [Examples - Buzzer](examples_08_buzzer.md)
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
