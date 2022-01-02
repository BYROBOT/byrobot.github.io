**[*e_drone* for python](index.md)** / **Examples** / **Error**

Modified : 2022.1.3

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Error_MotionCalibrating"></a>
## Motion 센서 캘리브레이션

```py
# 드론 센서 캘리브레이션 요청 후 에러로 나타난 캘리브레이션 진행 상태를 화면에 표시
from time import sleep

from e_drone.drone import *
from e_drone.protocol import *


def check_error(error, flag):
    if error & flag.value != 0:
        return True
    else:
        return False

def event_error(error):
    
    print("* eventError() / SystemTime({0:10}) / ErrorFlagsForSensor({1:032b}) / ErrorFlagsForState({2:032b})".format(error.system_time, error.error_flags_for_sensor, error.error_flags_for_state))

    if check_error(error.error_flags_for_sensor, ErrorFlagsForSensor.MOTION_CALIBRATING):
        print("    - The Motion Sensor is being calibrated.")


if __name__ == '__main__':

    drone = Drone()
    drone.open()

    # 이벤트 핸들링 함수 등록
    drone.set_event_handler(DataType.ERROR, event_error)

    drone.send_ping(DeviceType.CONTROLLER)
    sleep(0.1)

    drone.send_command(DeviceType.DRONE, CommandType.CLEAR_BIAS)
    sleep(0.1)

    for i in range(30, 0, -1):
        print(i)
        sleep(1)

        error = drone.get_data(DataType.ERROR)
        if error and not check_error(error.error_flags_for_sensor, ErrorFlagsForSensor.MOTION_CALIBRATING):
            print("* The Motion Sensor Calibration is completed.")
            break

    drone.close()
```

- [Error](04_protocol.md#Error)
- [send_ping()](05_drone.md#send_ping)


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
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. **Examples - Error**

<br>

[Index](index.md)
