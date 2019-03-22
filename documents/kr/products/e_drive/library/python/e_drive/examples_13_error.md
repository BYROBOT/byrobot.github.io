**[*e_drive* for python](index.md)** / **Examples** / **Error**

Modified : 2019.1.11

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
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Command Line](05_commandline.md)
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
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. **Examples - Error**

<br>

[Index](index.md)
