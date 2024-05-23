**[*e_drive* for python](index.md)** / **Examples** / **Error**

Modified : 2019.4.15

---

<br>


## <a name="Error_MotionCalibrating">Motion 센서 보정</a>

```py
# 드론 센서 캘리브레이션 요청 후 에러로 나타난 캘리브레이션 진행 상태를 화면에 표시
from time import sleep

from e_drive.drone import *
from e_drive.protocol import *


def checkError(error, flag):
    if error & flag.value != 0:
        return True
    else:
        return False

def eventError(error):
    
    print("* eventError() / SystemTime({0:10}) / ErrorFlagsForSensor({1:032b}) / ErrorFlagsForState({2:032b})".format(error.systemTime, error.errorFlagsForSensor, error.errorFlagsForState))

    if checkError(error.errorFlagsForSensor, ErrorFlagsForSensor.Motion_Calibrating):
        print("    - MOTION 센서를 보정 중입니다.")


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.setEventHandler(DataType.Error, eventError)

    drone.sendPing(DeviceType.Controller)
    sleep(0.1)

    drone.sendCommand(CommandType.ClearBias)
    sleep(0.1)

    for i in range(30, 0, -1):
        print(i)
        sleep(1)

        error = drone.getData(DataType.Error)
        if error and not checkError(error.errorFlagsForSensor, ErrorFlagsForSensor.Motion_Calibrating):
            print("* MOTION 센서 보정이 완료되었습니다.")
            break

    drone.close()
```

- [Error](03_protocol.md#Error)
- [sendPing()](04_drone.md#sendPing)


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
 9. [Examples - Sensor](examples_04_sensor.md)
10. [Examples - Motor](examples_05_motor.md)
11. [Examples - Setup](examples_06_setup.md)
12. [Examples - Buzzer](examples_07_buzzer.md)
13. [Examples - Light](examples_08_light.md)
14. **Examples - Error**

<br>

[Index](index.md)
