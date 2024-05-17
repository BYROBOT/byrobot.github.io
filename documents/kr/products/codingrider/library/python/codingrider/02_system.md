**[*CodingRider* for python](index.md)** / **System**

Modified : 2024.5.17

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

    #                          AAAABBCC, AAAA(Project Number), BB(Device Type), CC(Revision)
    Drone_11_Drone_P0		= 0x000B1000	# reserve
    Drone_11_Drone_P1		= 0x000B1001	# 65 no coding
    Drone_11_Drone_P2		= 0x000B1002	# fixWing
    Drone_11_Drone_P3		= 0x000B1003	# 65 coding
    Drone_11_Drone_P4		= 0x000B1004	# 95 battle drone
    Drone_11_Drone_P5		= 0x000B1005	# skykick evolution drone
    Drone_11_Drone_P6		= 0x000B1006	# reserve
    Drone_11_Drone_P7		= 0x000B1007	# reserve
    Drone_11_Drone_P8		= 0x000B1008	# reserve
    Drone_11_Drone_P9		= 0x000B1009	# reserve
    
    Drone_11_Controller_P0	= 0x000B2000	# 65 Drone, No USB, Fixed Wing, Return
    Drone_11_Controller_P1	= 0x000B2001	# 65 drone, USB
    Drone_11_Controller_P2	= 0x000B2002	# 65 drone, No USB
    Drone_11_Controller_P3	= 0x000B2003	# Bird Wing, Fixed Wing, NoReturn
    Drone_11_Controller_P4	= 0x000B2004	#  Battle drone, USB
    Drone_11_Controller_P5	= 0x000B2005	# skykick evolution controller
    Drone_11_Controller_P6	= 0x000B2006	# reserve
    Drone_11_Controller_P7	= 0x000B2007	# reserve
    Drone_11_Controller_P8	= 0x000B2008	# reserve
    Drone_11_Controller_P9	= 0x000B2009	# reserve
    
    Drone_11_Link_P0		= 0x000B3000	# Drone_11_Link_P0 RoboRobo
    Drone_11_Link_P1		= 0x000B3001	# reserve
    
    # Drone_12  chip
    Drone_12_Drone_P0		= 0x000C1000	# coding drone stm32f401rc + xn297
    Drone_12_Drone_P1		= 0x000C1001	# coding drone STM32F407VE + nrf24l01
    Drone_12_Drone_P2		= 0x000C1002	# reserve
    
    Drone_12_Controller_P0	= 0x000C2000	# coding drone stm32f401rc + xn297
    Drone_12_Controller_P1	= 0x000C2001	# coding drone STM32F407VE + nrf24l01
    Drone_12_Controller_P2	= 0x000C2002	# reserve
        
    Drone_12_Link_P0		= 0x000C3000	# Drone_12_Link_P0
    Drone_12_Link_P1		= 0x000C3001	# 	reserve		
    
    Drone_12_Tester_P0		= 0x000CA000	# Drone All Tester
    Drone_12_Tester_P1		= 0x000CA001	# reserve
```


<br>
<br>


<a name="DeviceType"></a>
## DeviceType

장치 타입

주로 데이터 송수신 시 데이터를 보낸 곳과 받을 곳을 지정할 때 사용합니다.

```py
class DeviceType(Enum):

    None_       = 0x00

    Drone       = 0x10     # 드론(Server)

    Controller  = 0x20     # 조종기(Client)

    LinkClient  = 0x30     # 링크 모듈(Client)
    LinkServer  = 0x31     # 링크 모듈(Server)
    BleClient   = 0x32     # BLE 클라이언트
    BleServer   = 0x33     # BLE 서버

    Range       = 0x40     # 거리 센서 모듈

    Base        = 0x70     # 베이스

    ByScratch   = 0x80     # 바이스크래치
    Scratch     = 0x81     # 스크래치
    Entry       = 0x82     # 네이버 엔트리

    Tester      = 0xA0     # 테스터
    Monitor     = 0xA1     # 모니터
    Updater     = 0xA2     # 펌웨어 업데이트 도구
    Encrypter   = 0xA3     # 암호화 도구

    EndOfType   = 0xA4

    Whispering      = 0xFE # 바로 인접한 장치까지만 전달(받은 장치는 자기 자신에게 보낸 것처럼 처리하고 타 장치에 전달하지 않음)
    Broadcasting    = 0xFF  # 연결된 모든 장치에 전달
```


<br>
<br>


<a name="ModeControlFlight"></a>
## ModeControlFlight

비행 제어 모드

CodingRider에서는 **Attitude**와 **Position**만 지원합니다.
다른 모드로 변경할 경우 무시합니다.

```py
class ModeControlFlight(Enum):
    
    None_       = 0x00

    Attitude    = 0x10     # 자세 - X,Y는 각도(deg)로 입력받음, Z,Yaw는 속도(m/s)로 입력 받음
    Position    = 0x11     # 위치 - X,Y,Z,Yaw는 속도(m/s)로 입력 받음
    
    EndOfType   = 0x14
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

    EndOfType           = 0x06
```


<br>
<br>


<a name="ModeFlight"></a>
## ModeFlight

비행 제어기 동작 모드

```py
class ModeFlight(Enum):
    
    None_       = 0x00      # 없음
            
    Ready       = 0x10      # 준비
    
    Start       = 0x11      # 이륙 준비
    Takeoff     = 0x12      # 이륙 (Flight로 자동전환)
    Flight      = 0x13      # 비행
    Landing     = 0x14      # 착륙
    Flip        = 0x15      # 회전
    Reverse     = 0x16      # 뒤집기
    
    Stop        = 0x20      # 강제 정지
    
    Accident    = 0x30      # 사고 (Ready로 자동전환)
    Error       = 0x31      # 오류
    
    Test        = 0x40      # 테스트 모드
    
    EndOfType   = 0x41
```


<br>
<br>


<a name="ModeUpdate"></a>
## ModeUpdate

업데이트 동작 모드

```py
class ModeUpdate(Enum):
    
    None_               = 0x00

    Ready               = 0x01      # 업데이트 가능 상태
    Update              = 0x02      # 업데이트 중
    Complete            = 0x03      # 업데이트 완료

    Failed              = 0x04      # 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우 등)

    NotAvailable        = 0x05      # 업데이트 불가능 상태(Debug 모드 등)
    RunApplication      = 0x06      # 어플리케이션 동작 중
    NotRegistered       = 0x07      # 등록되지 않음

    EndOfType           = 0x08
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
    
    None_           = 0x00      # 없음
    
    Stop            = 0x10      # 정지
    Takeoff         = 0x11      # 이륙
    Landing         = 0x12      # 착륙
    
    Reverse         = 0x13      # 뒤집기
    
    FlipFront       = 0x14      # 회전
    FlipRear        = 0x15      # 회전
    FlipLeft        = 0x16      # 회전
    FlipRight       = 0x17      # 회전
    
    Return          = 0x18      # Return
    
    ResetHeading    = 0xA0      # 헤딩 리셋(헤들리스 모드 일 때 현재 heading을 0도로 변경)
    
    EndOfType       = 0xA1
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

CodingRider에는 총 4개의 모터가 있으며, 왼쪽 앞 모터부터 각각 0, 1, 2, 3번으로 번호가 부여되어 있습니다.

드론 비행 시에 0번과 2번 모터는 시계방향(Clockwise), 1번과 3번 모터는 반시계방향(Counterclockwise)으로 회전합니다.

CodingRider는 회전 방향이 각각 기본 방향으로 고정되어 있어서 정해진 방향이 아니면 동작하지 않습니다.

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

    EndOfType           = 0x03
```


<br>
<br>


<a name="TrimDirection"></a>
## TrimDirection

트림

트림 설정 값을 한 단계씩 올리거나 낮출 때 사용합니다.

```py
class TrimDirection(Enum):
    
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

<h3><i>CodingRider</i> for python</H3>

 1. [Intro](01_intro.md)
 2. **System**
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Control](examples_01_control.md)
 6. [Examples - Sensor](examples_02_sensor.md)
 7. [Examples - Setup](examples_03_setup.md)
 8. [Examples - Buzzer](examples_04_buzzer.md)
 9. [Examples - Vibrator](examples_05_vibrator.md)
10. [Examples - Light](examples_06_light.md)
11. [Examples - Input](examples_07_input.md)
12. [Examples - Information](examples_08_information.md)
<br>

[Index](index.md)
