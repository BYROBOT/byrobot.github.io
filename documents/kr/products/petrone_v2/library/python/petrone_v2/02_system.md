**[*petrone_v2* for python](index.md)** / **System**

Modified : 2017.09.20

---

<h3>System과 관련된 정의를 소개합니다.</h3>

---


<br>

## <a name="DeviceType">DeviceType</a>

장치 타입

주로 데이터 송수신 시 데이터를 보낸 곳과 받을 곳을 지정할 때 사용합니다.

```py
class DeviceType(Enum):
    
    None_               = 0x00

    Drone               = 0x30      # 드론
    Controller          = 0x31      # 조종기
    Link                = 0x32      # 링크 모듈
    Tester              = 0x33      # 테스터
    Monitor             = 0x34      # 모니터
    Updater             = 0x35      # 펌웨어 업데이트 도구
    Encrypter           = 0x36      # 암호화 도구
    Scratch             = 0x37      # 스크래치
    Entry               = 0x38      # 네이버 엔트리
    ByScratch           = 0x39      # 바이스크래치

    EndOfType           = 0x40

    Broadcasting        = 0xFF
```


<br>
<br>


## <a name="ModeVehicle">ModeVehicle</a>

Vehicle 동작 모드

```py
class ModeVehicle(Enum):
    
    None_               = 0x00

    FlightGuard         = 0x10
    FlightNoGuard       = 0x11
    FlightFPV           = 0x12

    Drive               = 0x20
    DriveFPV            = 0x21

    Test                = 0x30

    EndOfType           = 0x31
```


<br>
<br>


## <a name="ModeSystem">ModeSystem</a>

System 동작 모드

```py
class ModeSystem(Enum):
    
    None_               = 0x00

    Boot                = 0x01
    Start               = 0x02
    Running             = 0x03
    ReadyToReset        = 0x04
    Error               = 0x05

    EndOfType           = 0x06
```


<br>
<br>


## <a name="ModeFlight">ModeFlight</a>

비행 제어기 동작 모드

```py
class ModeFlight(Enum):
    
    None_               = 0x00

    Ready               = 0x10
    TakeOff             = 0x11
    Flight              = 0x12
    Landing             = 0x13
    Flip                = 0x14
    Reverse             = 0x15

    Stop                = 0x20

    Accident            = 0x30
    Error               = 0x31

    Test                = 0x40

    EndOfType           = 0x41
```


<br>
<br>


## <a name="ModeDrive">ModeDrive</a>

주행 제어기 동작 모드

```py
class ModeDrive(Enum):
    
    None_               = 0x00

    Ready               = 0x10
    Start               = 0x11
    Drive               = 0x12

    Stop                = 0x20

    Accident            = 0x30
    Error               = 0x31

    Test                = 0x40

    EndOfType           = 0x41
```


<br>
<br>


## <a name="ModeUpdate">ModeUpdate</a>

업데이트 동작 모드

```py
class ModeUpdate(Enum):

    None_           = 0x00
    
    Ready           = 0x01  # 업데이트 가능 상태
    Update          = 0x02  # 업데이트 중
    Complete        = 0x03  # 업데이트 완료
        
    Faild           = 0x04  # 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우 등)
    
    NotAvailable    = 0x05  # 업데이트 불가능 상태(Debug 모드 등)
    RunApplication  = 0x06  # 어플리케이션 동작 중
    
    EndOfType       = 0x07
```


<br>
<br>


## <a name="ErrorFlagsForSensor">ErrorFlagsForSensor</a>

센서 오류 플래그

```py
class ErrorFlagsForSensor(Enum):

    None_                       = 0x00000000

    Imu_NoAnswer                = 0x00000001    # IMU 응답 없음
    Imu_WrongValue              = 0x00000002
    Imu_NotCalibrated           = 0x00000004    # Gyro Bias 보정이 완료되지 않음
    Imu_Calibrating             = 0x00000008    # Gyro Bias 보정 중

    Pressure_NoAnswer           = 0x00000010    # 압력센서 응답 없음
    Pressure_WrongValue         = 0x00000020

    RangeGround_NoAnswer        = 0x00000100    # 바닥 거리센서 응답 없음
    RangeGround_WrongValue      = 0x00000200

    Camera_NoAnswer             = 0x00001000    # 카메라 응답 없음
    OpticalFlow_WrongValue      = 0x00002000

    Battery_NoAnswer            = 0x00010000    # 배터리 응답 없음
    Battery_WrongValue          = 0x00020000
    Battery_NotCalibrated       = 0x00040000    # 배터리 입력값 보정이 완료되지 않음
```


<br>
<br>


## <a name="ErrorFlagsForState">ErrorFlagsForState</a>

상태 오류 플래그

```py
class ErrorFlagsForState(Enum):

    None_                       = 0x00000000

    NotTested                   = 0x00000001    # 테스트하지 않음
```


<br>
<br>


## <a name="DevelopmentStage">DevelopmentStage</a>

개발 단계

```py
class DevelopmentStage(Enum):
    
    Alpha               = 0x00
    Beta                = 0x01 
    ReleaseCandidate    = 0x02
    Release             = 0x03
```


<br>
<br>


## <a name="FlightEvent">FlightEvent</a>

비행 이벤트

```py
class FlightEvent(Enum):
    
    None_               = 0x00

    Stop                = 0x10
    TakeOff             = 0x11
    Landing             = 0x12

    Reverse             = 0x13

    Shot                = 0x18
    UnderAttack         = 0x19

    ResetHeading        = 0x1A

    EndOfType           = 0x1B
```


<br>
<br>


## <a name="DriveEvent">DriveEvent</a>

주행 이벤트

```py
class DriveEvent(Enum):
    
    None_               = 0x00

    Stop                = 0x10
    
    Shot                = 0x11
    UnderAttack         = 0x12

    EndOfType           = 0x13
```


<br>
<br>


## <a name="Direction">Direction</a>

방향

```py
class Direction(Enum):
    
    None_               = 0x00

    Left                = 0x01
    Front               = 0x02
    Right               = 0x03
    Rear                = 0x04

    Top                 = 0x05
    Bottom              = 0x06

    EndOfType           = 0x07
```


<br>
<br>


## <a name="Rotation">Rotation</a>

회전 방향

모터를 작동시킬 때 회전 방향을 지정하는데 사용합니다.

PETRONE V2에는 총 4개의 모터가 있으며, 왼쪽 앞 모터부터 각각 0, 1, 2, 3번으로 번호가 부여되어 있습니다.

드론 비행 시에 0번과 2번 모터는 시계방향(Clockwise), 1번과 3번 모터는 반시계방향(Counterclockwise)으로 회전합니다.

0번과 1번 모터는 드론이 뒤집어졌을 때, 다시 원래 상태로 복원하기 위해 시계방향과 반시계방향 모두 동작합니다.

2번 모터는 시계 방향, 3번 모터는 반시계 방향으로만 동작합니다.

```py
class Rotation(Enum):
    
    None_               = 0x00

    Clockwise           = 0x01
    Counterclockwise    = 0x02

    EndOfType           = 0x03
```


<br>
<br>

## <a name="SensorOrientation">SensorOrientation</a>

센서 방향

드론이 뒤집어졌을 때 상태를 확인하는 용도입니다.

```py
class SensorOrientation(Enum):
    
    None_               = 0x00

    Normal              = 0x01
    ReverseStart        = 0x02
    Reversed            = 0x03

    EndOfType           = 0x04
```


<br>
<br>


## <a name="Headless">Headless</a>

Headless모드

**Headless**를 선택할 경우, ***드론이 이륙할 때 바라보는 방향***이나 ***사용자가 방향을 초기화 할 때 드론이 바라보는 방향***을 앞으로 지정합니다. 이 방향을 기준으로 전후좌우 방향이 고정되어 드론이 어느 쪽으로 바라보더라도 지정한 방향을 기준으로 움직입니다.

**Normal**을 선택할 경우, 드론이 바라보는 방향을 기준으로 전후좌우로 움직입니다.

```py
class Headless(Enum):
    
    None_               = 0x00

    Headless            = 0x01      # Headless
    Normal              = 0x02      # Normal

    EndOfType           = 0x04
```


<br>
<br>


## <a name="Trim">Trim</a>

트림

트림 설정 값을 한 단계씩 올리거나 낮출 때 사용합니다.

```py
class Trim(Enum):
    
    None_               = 0x00  # 없음

    RollIncrease        = 0x01  # Roll 증가
    RollDecrease        = 0x02  # Roll 감소
    PitchIncrease       = 0x03  # Pitch 증가
    PitchDecrease       = 0x04  # Pitch 감소
    YawIncrease         = 0x05  # Yaw 증가
    YawDecrease         = 0x06  # Yaw 감소
    ThrottleIncrease    = 0x07  # Throttle 증가
    ThrottleDecrease    = 0x08  # Throttle 감소

    Reset               = 0x09  # 전체 트림 리셋

    EndOfType           = 0x0A
```


<br>


---

<h3><i>petrone_v2</i> for python</H3>

 1. [Intro](01_intro.md)
 2. **System**
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
17. [Examples - Error](examples_13_error.md)

[Tutorial for Mac](./tutorial_for_mac/)

<br>

[Index](index.md)
