**[*e_drone* for python](index.md)** / **System**

Modified : 2021.12.29

---

<h3>System과 관련된 정의를 소개합니다.</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="ModelNumber"></a>
## ModelNumber

모델 번호

장치의 모델 번호입니다. 현재는 펌웨어 업데이트 시 제품을 확인하는 용도로 사용합니다.

```py
class ModelNumber(Enum):

    NONE = 0x00000000

    #                    AAAABBCC, AAAA(Project Number), BB(Device Type), CC(Revision)
    DRONE_3_DRONE_P1 = 0x00031001       # Lightrone / GD65 / HW2181
    DRONE_3_DRONE_P2 = 0x00031002       # Soccer Drone / HW2181
    DRONE_3_DRONE_P3 = 0x00031003       # GD240 / HW2181
    DRONE_3_DRONE_P4 = 0x00031004       # GD50N / HW2181
    DRONE_3_DRONE_P5 = 0x00031005       # GD30 / HW2181
    DRONE_3_DRONE_P6 = 0x00031006       # Soccer Drone 2 / HW2181
    DRONE_3_DRONE_P7 = 0x00031007       # SKYKICKV2 / HW2181 
    DRONE_3_DRONE_P8 = 0x00031008       # GD65 / HW2181
    DRONE_3_DRONE_P9 = 0x00031009       # GD65 / HW2181
    DRONE_3_DRONE_P10 = 0x0003100A      # Battle Drone / SPI / HW2181

    DRONE_3_CONTROLLER_P1 = 0x00032001  # (obsolete)
    DRONE_3_CONTROLLER_P2 = 0x00032002  # HW2000
    DRONE_3_CONTROLLER_P3 = 0x00032003  # HW2000B
    DRONE_3_CONTROLLER_P4 = 0x00032004
    DRONE_3_CONTROLLER_P5 = 0x00032005

    DRONE_3_LINK_P0 = 0x00033000

    DRONE_3_ANALYZER_P0 = 0x00034100    # for soccer drone

    DRONE_3_TESTER_P4 = 0x0003A004      # (obsolete)
    DRONE_3_TESTER_P6 = 0x0003A006      # Battle Drone Tester

    DRONE_4_DRONE_P4 = 0x00041004       # (obsolete)
    DRONE_4_DRONE_P5 = 0x00041005       # HW2000, 2m range sensor
    DRONE_4_DRONE_P6 = 0x00041006       # HW2000B, 4m range sensor
    DRONE_4_DRONE_P7 = 0x00041007       # HW2000B, 4m range sensor, BLDC Motor

    DRONE_4_CONTROLLER_P1 = 0x00042001  # (obsolete)
    DRONE_4_CONTROLLER_P2 = 0x00042002  # HW2000
    DRONE_4_CONTROLLER_P3 = 0x00042003  # HW2000B
    DRONE_4_CONTROLLER_P4 = 0x00042004  # HW2000B + PA
    DRONE_4_CONTROLLER_P5 = 0x00042005  # HW2000B + PA

    DRONE_4_LINK_P0 = 0x00043000

    DRONE_4_TESTER_P4 = 0x0004A004      # (obsolete)
    DRONE_4_TESTER_P6 = 0x0004A006
    DRONE_4_TESTER_P7 = 0x0004A007

    DRONE_4_MONITOR_P4 = 0x0004A104     # (obsolete)

    DRONE_7_DRONE_P1 = 0x00071001       # (obsolete)
    DRONE_7_DRONE_P2 = 0x00071002       # Coding Car

    DRONE_7_BLE_CLIENT_P0 = 0x00073200  # Coding Car Link
    DRONE_7_BLE_CLIENT_P5 = 0x00073205  # Coding Car Tester BLE

    DRONE_7_BLE_SERVER_P2 = 0x00073302  # Coding Car Ble Module

    DRONE_7_TESTER_P4 = 0x0003A004      # (obsolete)
    DRONE_7_TESTER_P5 = 0x0003A005      # (obsolete)
    DRONE_7_TESTER_P6 = 0x0003A006

    DRONE_7_MONITOR_P4 = 0x0003A104     # (obsolete)
    DRONE_7_MONITOR_P5 = 0x0003A105

    DRONE_8_DRONE_P0 = 0x00081000       # (obsolete)
    DRONE_8_DRONE_P1 = 0x00081001       # Coding Drone

    DRONE_8_TESTER_P4 = 0x0008A004      # (obsolete)
    DRONE_8_TESTER_P6 = 0x0008A006

    DRONE_8_MONITOR_P6 = 0x0008A106
```


<br>
<br>


<a name="DeviceType"></a>
## DeviceType

장치 타입

주로 데이터 송수신 시 데이터를 보낸 곳과 받을 곳을 지정할 때 사용합니다.

```py
class DeviceType(Enum):

    NONE = 0x00

    DRONE = 0x10        # 드론(Server)

    CONTROLLER = 0x20   # 조종기(Client)

    LINK = 0x30         # 링크 모듈(Client)
    LINK_SERVER = 0x31  # 링크 모듈(Server, 링크 모듈이 서버로 동작하는 경우에만 통신 타입을 잠시 바꿈)
    BLE_CLIENT = 0x32   # BLE 클라이언트
    BLE_SERVER = 0x33   # BLE 서버

    RANGE = 0x40        # 거리 센서 모듈
    ANALYZER = 0x41     # 분석 모듈

    BASE = 0x70         # 베이스

    BYSCRATCH = 0x80    # 바이스크래치
    SCRATCH = 0x81      # 스크래치
    ENTRY = 0x82        # 네이버 엔트리

    TESTER = 0xA0       # 테스터
    MONITOR = 0xA1      # 모니터
    UPDATER = 0xA2      # 펌웨어 업데이트 도구
    ENCRYPTER = 0xA3    # 암호화 도구

    # 바로 인접한 장치까지만 전달(받은 장치는 자기 자신에게 보낸 것처럼 처리하고 타 장치에 전달하지 않음)
    WHISPERING = 0xFE
    BROADCASTING = 0xFF
```


<br>
<br>


<a name="ModeControlFlight"></a>
## ModeControlFlight

비행 제어 모드

e_drone에서는 **ATTITUDE**와 **POSITION**만 지원합니다.
다른 모드로 변경할 경우 무시합니다.

```py
class ModeControlFlight(Enum):

    NONE = 0x00

    ATTITUDE = 0x10     # 자세 - X, Y는 각도(deg)로 입력받음, Z, Yaw는 속도(m/s)로 입력 받음
    POSITION = 0x11     # 위치 - X, Y, Z, Yaw는 속도(m/s)로 입력 받음
    MANUAL = 0x12       # 고도를 수동으로 조종함
    RATE = 0x13         # Rate - X, Y는 각속도(deg/s)로 입력받음, Z, Yaw는 속도(m/s)로 입력 받음
    FUNCTION = 0x14     # 기능

    END_OF_TYPE = 0x15
```


<br>
<br>


<a name="ModeSystem"></a>
## ModeSystem

System 동작 모드

```py
class ModeSystem(Enum):

    NONE = 0x00

    BOOT = 0x10
    START = 0x11
    RUNNING = 0x12
    READY_TO_RESET = 0x13

    ERROR = 0xA0

    END_OF_TYPE = 0xA1
```


<br> 
<br>


<a name="ModeFlight"></a>
## ModeFlight

비행 제어기 동작 모드

```py
class ModeFlight(Enum):

    NONE = 0x00

    READY = 0x10

    START = 0x11
    TAKEOFF = 0x12
    FLIGHT = 0x13
    LANDING = 0x14
    FLIP = 0x15
    REVERSE = 0x16

    STOP = 0x20

    ACCIDENT = 0x30
    ERROR = 0x31

    TEST = 0x40

    END_OF_TYPE = 0x41
```


<br>
<br>


<a name="ModeUpdate"></a>
## ModeUpdate

업데이트 동작 모드

```py
class ModeUpdate(Enum):

    NONE = 0x00

    READY = 0x01            # 업데이트 가능 상태
    UPDATE = 0x02           # 업데이트 중
    COMPLETE = 0x03         # 업데이트 완료

    FAILED = 0x04           # 업데이트 실패(업데이트 완료까지 갔으나 body의 Crc16이 일치하지 않는 경우 등)

    NOT_AVAILABLE = 0x05    # 업데이트 불가능 상태(Debug 모드 등)
    RUN_APPLICATION = 0x06  # 어플리케이션 동작 중
    NOT_REGISTERED = 0x07   # 등록되지 않음

    END_OF_TYPE = 0x08
```


<br>
<br>


<a name="ErrorFlagsForSensor"></a>
## ErrorFlagsForSensor

센서 오류 플래그

```py
class ErrorFlagsForSensor(Enum):

    NONE = 0x00000000

    MOTION_NO_ANSWER = 0x00000001           # Motion 센서 응답 없음
    MOTION_WRONG_VALUE = 0x00000002         # Motion 센서 잘못된 값
    MOTION_NOT_CALIBRATED = 0x00000004      # Gyro Bias 보정이 완료되지 않음
    MOTION_CALIBRATING = 0x00000008         # Gyro Bias 보정 중

    PRESSURE_NO_ANSWER = 0x00000010         # 압력 센서 응답 없음
    PRESSURE_WRONG_VALUE = 0x00000020       # 압력 센서 잘못된 값

    RANGE_GROUND_NO_ANSWER = 0x00000100     # 바닥 거리 센서 응답 없음
    RANGE_GROUND_WRONG_VALUE = 0x00000200   # 바닥 거리 센서 잘못된 값
    RANGE_FRONT_NO_ANSWER = 0x00000400 	    # 정면 거리 센서 응답 없음
    RANGE_FRONT_WRONG_VALUE = 0x00000800    # 정면 거리 센서 잘못된 값

    FLOW_NO_ANSWER = 0x00001000             # Flow 센서 응답 없음
    FLOW_WRONG_VALUE = 0x00002000           # Flow 잘못된 값
    FLOW_CANNOT_RECOGNIZE_GROUND_IMAGE = 0x00004000     # 바닥 이미지를 인식할 수 없음

    RF_NO_ANSWER = 0x10000000               # RF 응답 없음
    RF_PAIRED = 0x20000000                  # RF 페어링 완료
    RF_CONNECTED = 0x40000000               # RF 연결됨
```


<br>
<br>


<a name="ErrorFlagsForState"></a>
## ErrorFlagsForState

상태 오류 플래그

```py
class ErrorFlagsForState(Enum):

    NONE = 0x00000000

    NOT_REGISTERED = 0x00000001                     # 장치 등록이 안됨
    FLASH_READ_LOCK_UNLOCKED = 0x00000002           # 플래시 메모리 읽기 Lock이 안 걸림
    BOOTLOADER_WRITE_LOCK_UNLOCKED = 0x00000004     # 부트로더 영역 쓰기 Lock이 안 걸림
    LOW_BATTERY = 0x00000008                        # Low Battery

    TAKEOFF_FAILURE_CHECK_PROPELLER_AND_MOTOR = 0x00000010  # 이륙 실패
    CHECK_PROPELLER_VIBRATION = 0x00000020          # 프로펠러 진동발생
    ATTITUDE_NOT_STABLE = 0x00000040                # 자세가 많이 기울어져 있거나 뒤집어져 있을때

    CANNOT_FLIP_LOW_BATTERY = 0x00000100            # 배터리가 30이하
    CANNOT_FLIP_TOO_HEAVY = 0x00000200              # 기체가 무거움
```


<br>
<br>


<a name="FlightEvent"></a>
## FlightEvent

비행 이벤트

```py
class FlightEvent(Enum):

    NONE = 0x00

    STOP = 0x10
    TAKEOFF = 0x11
    LANDING = 0x12

    REVERSE = 0x13

    FLIP_FRONT = 0x14
    FLIP_REAR = 0x15
    FLIP_LEFT = 0x16
    FLIP_RIGHT = 0x17

    RETURN_HOME = 0x18

    SHOT = 0x90
    UNDER_ATTACK = 0x91

    RESET_HEADING = 0xA0

    END_OF_TYPE = 0xA1
```


<br>
<br>


<a name="Direction"></a>
## Direction

방향

```py
class Direction(Enum):

    NONE = 0x00

    LEFT = 0x01
    FRONT = 0x02
    RIGHT = 0x03
    REAR = 0x04

    TOP = 0x05
    BOTTOM = 0x06

    CENTER = 0x07

    END_OF_TYPE = 0x08
```


<br>
<br>


<a name="Rotation"></a>
## Rotation

회전 방향

모터를 작동시킬 때 회전 방향을 지정하는데 사용합니다.

E-DRONE에는 총 4개의 모터가 있으며, 왼쪽 앞 모터부터 각각 0, 1, 2, 3번으로 번호가 부여되어 있습니다.

드론 비행 시에 0번과 2번 모터는 시계방향(Clockwise), 1번과 3번 모터는 반시계방향(Counterclockwise)으로 회전합니다.

E-DRONE은 회전 방향이 각각 기본 방향으로 고정되어 있어서 정해진 방향이 아니면 동작하지 않습니다.

```py
class Rotation(Enum):

    NONE = 0x00

    CLOCKWISE = 0x01
    COUNTERCLOCKWISE = 0x02

    END_OF_TYPE = 0x03
```


<br>
<br>


<a name="SensorOrientation"></a>
## SensorOrientation

센서 방향

드론이 뒤집어졌을 때 상태를 확인하는 용도입니다.

```py
class SensorOrientation(Enum):

    NONE = 0x00

    NORMAL = 0x01
    REVERSE_START = 0x02
    REVERSED = 0x03

    END_OF_TYPE = 0x04
```


<br>
<br>


<a name="Headless"></a>
## Headless

Headless모드

**Headless**를 선택할 경우, ***드론이 이륙할 때 바라보는 방향***이나 ***사용자가 방향을 초기화 할 때 드론이 바라보는 방향***을 앞으로 지정합니다. 이 방향을 기준으로 전후좌우 방향이 고정되어 드론이 어느 쪽으로 바라보더라도 지정한 방향을 기준으로 움직입니다.

**Normal**을 선택할 경우, 드론이 바라보는 방향을 기준으로 전후좌우로 움직입니다.

```py
class Headless(Enum):

    NONE = 0x00

    HEADLESS = 0x01      # Headless
    NORMAL = 0x02      # Normal

    END_OF_TYPE = 0x03
```


<br>
<br>


<a name="ModeMovement"></a>
## ModeMovement

이동 상태

드론의 현재 이동 상태를 나타냅니다.

```py
class ModeMovement(Enum):

    NONE = 0x00

    READY = 0x01      # Ready
    HOVERING = 0x02      # Hovering
    MOVING = 0x03      # Moving
    RETURN_HOME = 0x04      # Return Home

    END_OF_TYPE = 0x05
```


<br>


---

<h3><i>e_drone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. **System**
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
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
