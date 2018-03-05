**[*petrone_v2* for python](index.md)** / **Examples** / **Error**

Modified : 2018.3.5

---

<br>


## <a name="Error_ImuCalibrating">IMU 센서 보정</a>

```py
from time import sleep

from petrone_v2.drone import *
from petrone_v2.protocol import *


def checkError(error, flag):
    if error & flag.value != 0:
        return True
    else:
        return False

def eventError(error):
    
    print("* eventError() / SystemTime({0:10}) / ErrorFlagsForSensor({1:032b}) / ErrorFlagsForState({2:032b})".format(error.systemTime, error.errorFlagsForSensor, error.errorFlagsForState))

    if checkError(error.errorFlagsForSensor, ErrorFlagsForSensor.Imu_Calibrating):
        print("    - IMU 센서를 보정 중입니다.")


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Error, eventError)

    drone.sendPing(DeviceType.Controller)
    sleep(0.1)

    drone.sendCommand(CommandType.ClearGyroBias)
    sleep(0.1)

    for i in range(30, 0, -1):
        print(i)
        sleep(1)

        error = drone.getData(DataType.Error)
        if not checkError(error.errorFlagsForSensor, ErrorFlagsForSensor.Imu_Calibrating):
            print("* IMU 센서 보정이 완료되었습니다.")
            break

    drone.close()
```

- [Error](03_protocol.md#Error)
- [sendPing()](04_drone.md#sendPing)


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
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. **Examples - Error**

<br>

[Index](index.md)
