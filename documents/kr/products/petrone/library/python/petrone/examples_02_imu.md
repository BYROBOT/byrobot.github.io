**[*petrone* for python](index.md)** / **Examples** / **Information**

Modified : 2018.5.18

---

* Kramdown table of contents
{:toc .toc}


<br>


<a name="imu_data_monitor"></a>
## IMU 데이터 요청

IMU 데이터를 50ms 주기로 10회 요청합니다.

```py
from time import sleep

from petrone.drone import *
from petrone.protocol import *
from petrone.system import *


def eventImu(data):
    print("eventImu() / | Accel (X:{0:5}, Y:{1:5}, Z:{2:5}) | Gyro (R:{3:5}, P:{4:5}, Y:{5:5}) | Angle (R:{6:4}, P:{7:4}, Y:{8:4})".format(
        data.accelX, data.accelY, data.accelZ,
        data.gyroRoll, data.gyroPitch, data.gyroYaw,
        data.angleRoll, data.anglePitch, data.angleYaw))


if __name__ == '__main__':
    
    drone = Drone(True, True, True, True, True)

    drone.setEventHandler(DataType.Imu, eventImu)

    # Connect
    drone.connect(flagSystemReset=True)
    sleep(2)
    
    if drone.isConnected():

        for i in range(0, 10, 1):
            
            drone.sendRequest(DataType.Imu)
            sleep(0.05)

        # Disconnect
        print("Disconnect device.")
        drone.sendLinkDisconnect()
        sleep(0.2)

    drone.close()
```

<br>

실행 결과는 다음과 같습니다.


<div align="center">
    <img src="../examples_02_imu_ex1.jpg" alt="example1 result">
    <p>IMU 데이터 요청</p>
</div>



<br>


---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)
 6. **Examples - Imu**
 7. [Examples - Test Flight](examples_03_test_flight.md)

<br>

[Index](index.md)
