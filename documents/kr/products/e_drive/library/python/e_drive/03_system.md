**[*e_drive* for python](index.md)** / **System**

Modified : 2021.1.5

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

    None_                   = 0x00000000

    #                           AAAABBCC, AAAA(Project Number), BB(Device Type), CC(Revision)
    Drone_3_Drone_P1        = 0x00031001    # Drone_3_Drone_P1 (Lightrone / GD65 / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding)
    Drone_3_Drone_P2        = 0x00031002    # Drone_3_Drone_P2 (Soccer Drone / HW2181 / Keil / 7.4v / barometer / RGB LED / Shaking binding)
    Drone_3_Drone_P3        = 0x00031003    # Drone_3_Drone_P3 (GD240 / HW2181 / Keil / power button / u30 flow / 3.7v / geared motor / barometer)
    Drone_3_Drone_P4        = 0x00031004    # Drone_3_Drone_P4 (GD50N / HW2181 / Keil / power button / 3.7v / barometer)
    Drone_3_Drone_P5        = 0x00031005    # Drone_3_Drone_P5 (GD30 / HW2181 / Keil / 3.7v / nomal binding)
    Drone_3_Drone_P6        = 0x00031006    # Drone_3_Drone_P6 (Soccer Drone 2 / HW2181 / Keil / 7.4v / barometer / RGB LED / Shaking binding)
    Drone_3_Drone_P7        = 0x00031007    # Drone_3_Drone_P7 (SKYKICKV2 / SPI / HW2181 / Keil / 7.4v / barometer / RGB LED / Shaking binding)
    Drone_3_Drone_P8        = 0x00031008    # Drone_3_Drone_P8 (GD65 / SPI / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding)
    Drone_3_Drone_P9        = 0x00031009    # Drone_3_Drone_P9 (GD65 / SPI / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding / BladeType Power Connector)
    Drone_3_Drone_P10       = 0x0003100A    # Drone_3_Drone_P10 (Battle Drone / SPI / HW2181 / Keil / 3.7v / barometer / RGB LED / Shaking binding)
    
    Drone_3_Controller_P1   = 0x00032001    # Drone_3_Controller_P1 / GD65 Controller /small size
    Drone_3_Controller_P2   = 0x00032002    # Drone_3_Controller_P2 / Skykick Controller /large size
    Drone_3_Controller_P3   = 0x00032003    # Drone_3_Controller_P3 / GD65 Controller USB /small size + USB
    Drone_3_Controller_P4   = 0x00032004    # Drone_3_Controller_P4 / Battle Drone Controller USB / small size + usb
    Drone_3_Controller_P5   = 0x00032005    # Drone_3_Controller_P5 / E-Drone 4m Controller / USB / HW2181B / Keil
    
    Drone_3_Link_P0         = 0x00033000    # Drone_3_Link_P0
    
    Drone_4_Drone_P4        = 0x00041004    # Drone_4_Drone_P4 (obsolete)
    Drone_4_Drone_P5        = 0x00041005    # Drone_4_Drone_P5 (HW2000, 2m range sensor)
    Drone_4_Drone_P6        = 0x00041006    # Drone_4_Drone_P6 (HW2000B, 4m range sensor)
    Drone_4_Drone_P7        = 0x00041007    # Drone_4_Drone_P7 (HW2000B, 4m range sensor, BLDC Motor)
    
    Drone_4_Controller_P1   = 0x00042001    # Drone_4_Controller_P1 (obsolete)
    Drone_4_Controller_P2   = 0x00042002    # Drone_4_Controller_P2 (HW2000)
    Drone_4_Controller_P3   = 0x00042003    # Drone_4_Controller_P3 (HW2000B)
    
    Drone_4_Link_P0         = 0x00043000    # Drone_4_Link_P0
    
    Drone_7_Drone_P1        = 0x00071001    # Drone_7_Drone_P1 (obsolete)
    Drone_7_Drone_P2        = 0x00071002    # Drone_7_Drone_P2 / Coding Car

    Drone_7_BleClient_P0    = 0x00073200    # Drone_7_BleClient_P0 / Coding Car Link

    Drone_7_BleServer_P2    = 0x00073302    # Drone_7_BleServer_P2 / Coding Car Ble Module
    
    Drone_8_Drone_P0        = 0x00081000    # Drone_8_Drone_P0 (obsolete)
    Drone_8_Drone_P1        = 0x00081001    # Drone_8_Drone_P1 / Coding Drone
```


<br>
<br>


<a name="DeviceType"></a>
## DeviceType

장치 타입

주로 데이터 송수신 시 데이터를 보낸 곳과 받을 곳을 지정할 때 사용합니다.

```py
class DeviceType(Enum):

    None_           = 0x00

    Drone           = 0x10      # 드론(Server)

    Controller      = 0x20      # 조종기(Client)

    Link            = 0x30      # 링크 모듈(Client)
    LinkServer      = 0x31      # 링크 모듈(Server, 링크 모듈이 서버로 동작하는 경우에만 통신 타입을 잠시 바꿈)
    BleClient       = 0x32      # BLE 클라이언트
    BleServer       = 0x33      # BLE 서버

    Range           = 0x40      # 거리 센서 모듈

    Base            = 0x70      # 베이스

    ByScratch       = 0x80      # 바이스크래치
    Scratch         = 0x81      # 스크래치
    Entry           = 0x82      # 네이버 엔트리

    Tester          = 0xA0      # 테스터
    Monitor         = 0xA1      # 모니터
    Updater         = 0xA2      # 펌웨어 업데이트 도구
    Encrypter       = 0xA3      # 암호화 도구

    Whispering      = 0xFE      # 바로 인접한 장치까지만 전달(받은 장치는 자기 자신에게 보낸 것처럼 처리하고 타 장치에 전달하지 않음)
    Broadcasting    = 0xFF
```


<br>
<br>


<a name="ModeSystem"></a>
## ModeSystem

System 동작 모드

```py
class ModeSystem(Enum):
    
    None_               = 0x00

    Boot                = 0x10
    Start               = 0x11
    Running             = 0x12
    ReadyToReset        = 0x13

    Error               = 0xA0

    EndOfType           = 0xA1
```


<br>
<br>


<a name="ModeFlight"></a>
## ModeFlight

비행 제어기 동작 모드

```py
class ModeFlight(Enum):
    
    None_               = 0x00

    Ready               = 0x10

    Start               = 0x11
    TakeOff             = 0x12
    Flight              = 0x13
    Landing             = 0x14
    Flip                = 0x15
    Reverse             = 0x16

    Stop                = 0x20

    Accident            = 0x30
    Error               = 0x31

    Test                = 0x40

    EndOfType           = 0x41
```


<br>
<br>


<a name="ModeUpdate"></a>
## ModeUpdate

업데이트 동작 모드

```py
class ModeUpdate(Enum):

    None_           = 0x00
    
    Ready           = 0x01  # 업데이트 가능 상태
    Update          = 0x02  # 업데이트 중
    Complete        = 0x03  # 업데이트 완료
        
    Failed          = 0x04  # 업데이트 실패
    
    NotAvailable    = 0x05  # 업데이트 불가능 상태(Debug 모드 등)
    RunApplication  = 0x06  # 어플리케이션 동작 중
    NotRegistered   = 0x07  # 등록되지 않음
    
    EndOfType       = 0x08
```


<br>
<br>


<a name="ErrorFlagsForSensor"></a>
## ErrorFlagsForSensor

센서 오류 플래그

```py
class ErrorFlagsForSensor(Enum):

    None_                                   = 0x00000000

    Motion_NoAnswer                         = 0x00000001    # Motion 센서 응답 없음
    Motion_WrongValue                       = 0x00000002    # Motion 센서 잘못된 값
    Motion_NotCalibrated                    = 0x00000004    # Gyro Bias 보정이 완료되지 않음
    Motion_Calibrating                      = 0x00000008    # Gyro Bias 보정 중

    Pressure_NoAnswer                       = 0x00000010    # 압력 센서 응답 없음
    Pressure_WrongValue                     = 0x00000020    # 압력 센서 잘못된 값

    RangeGround_NoAnswer                    = 0x00000100    # 바닥 거리 센서 응답 없음
    RangeGround_WrongValue                  = 0x00000200    # 바닥 거리 센서 잘못된 값

    Flow_NoAnswer                           = 0x00001000    # Flow 센서 응답 없음
    Flow_WrongValue                         = 0x00002000    # Flow 잘못된 값
    Flow_CannotRecognizeGroundImage         = 0x00004000    # 바닥 이미지를 인식할 수 없음
```


<br>
<br>


<a name="ErrorFlagsForState"></a>
## ErrorFlagsForState

상태 오류 플래그

```py
class ErrorFlagsForState(Enum):

    None_                                   = 0x00000000

    NotRegistered                           = 0x00000001    # 장치 등록이 안됨
    FlashReadLock_UnLocked                  = 0x00000002    # 플래시 메모리 읽기 Lock이 안 걸림
    BootloaderWriteLock_UnLocked            = 0x00000004    # 부트로더 영역 쓰기 Lock이 안 걸림
    LowBattery                              = 0x00000008    # Low Battery
    
    TakeoffFailure_CheckPropellerAndMotor   = 0x00000010    # 이륙 실패
    CheckPropellerVibration                 = 0x00000020    # 프로펠러 진동발생
    Attitude_NotStable                      = 0x00000040    # 자세가 많이 기울어져 있거나 뒤집어져 있을때
    
    CanNotFlip_LowBattery                   = 0x00000100    # 배터리가 30이하
    CanNotFlip_TooHeavy                     = 0x00000200    # 기체가 무거움
```


<br>
<br>


<a name="FlightEvent"></a>
## FlightEvent

비행 이벤트

```py
class FlightEvent(Enum):

    None_               = 0x00

    Stop                = 0x10
    TakeOff             = 0x11
    Landing             = 0x12

    Reverse             = 0x13

    FlipFront           = 0x14
    FlipRear            = 0x15
    FlipLeft            = 0x16
    FlipRight           = 0x17

    Return              = 0x18

    Shot                = 0x90
    UnderAttack         = 0x91

    ResetHeading        = 0xA0

    EndOfType           = 0xA1
```


<br>
<br>


<a name="Direction"></a>
## Direction

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

    Center              = 0x07

    EndOfType           = 0x08
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
    
    None_               = 0x00

    Clockwise           = 0x01
    Counterclockwise    = 0x02

    EndOfType           = 0x03
```


<br>
<br>


<a name="SensorOrientation"></a>
## SensorOrientation

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


<a name="Headless"></a>
## Headless

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


<a name="ModeMovement"></a>
## ModeMovement

이동 상태

드론의 현재 이동 상태를 나타냅니다.

```py
class ModeMovement(Enum):
    
    None_               = 0x00

    Ready               = 0x01      # Ready
    Hovering            = 0x02      # Hovering
    Moving              = 0x03      # Moving
    ReturnHome          = 0x04      # Return Home

    EndOfType           = 0x05
```


<br>


---

<h3><i>e_drive</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3.  **System**
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
14. [Examples - Error](examples_09_error.md)

<br>

[Index](index.md)
