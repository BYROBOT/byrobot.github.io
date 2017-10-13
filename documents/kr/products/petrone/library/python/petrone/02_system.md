**[*petrone* for python](index.md)** / **System**

Modified : 2017.09.29

---

<h3>System과 관련된 정의를 소개합니다.</h3>

---


<br>

## <a name="DeviceType">DeviceType</a>

장치 타입

주로 실행중인 펌웨어의 버젼을 확인할 때 사용합니다.

```py
class DeviceType(Enum):
    
    None_               = 0x00

    DroneMain           = 0x01      # 드론 제어
    DroneSub            = 0x02      # 드론 통신
    Link                = 0x03      # 링크 모듈
    Tester              = 0x04      # 테스터

    EndOfType           = 0x05
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

    Boot                = 0x01      # 부팅
    Wait                = 0x02      # 연결 대기 상태

    Ready               = 0x03      # 대기 상태

    Running             = 0x04      # 메인 코드 동작

    Update              = 0x05      # 펌웨어 업데이트
    UpdateComplete      = 0x06      # 펌웨어 업데이트 완료

    Error               = 0x07      # 펌웨어 업데이트 완료

    EndOfType           = 0x08
```


<br>
<br>


## <a name="ModeFlight">ModeFlight</a>

비행 제어기 동작 모드

```py
class ModeFlight(Enum):
    
    None_               = 0x00

    Ready               = 0x01      # 비행 준비

    TakeOff             = 0x02      # 이륙 (Flight로 자동전환)
    Flight              = 0x03      # 비행
    Flip                = 0x04
    Stop                = 0x05      # 강제 정지
    Landing             = 0x06      # 착륙
    Reverse             = 0x07      # 뒤집기

    Accident            = 0x08      # 사고 (Ready로 자동전환)
    Error               = 0x09      # 오류

    EndOfType           = 0x0A
```


<br>
<br>


## <a name="ModeDrive">ModeDrive</a>

주행 제어기 동작 모드

```py
class ModeDrive(Enum):
    
    None_               = 0x00

    Ready               = 0x01      # 준비

    Start               = 0x02      # 출발
    Drive               = 0x03      # 주행
    Stop                = 0x04      # 강제 정지

    Accident            = 0x05      # 사고 (Ready로 자동전환)
    Error               = 0x06      # 오류

    EndOfType           = 0x07
```


<br>
<br>


## <a name="ModeUpdate">ModeUpdate</a>

업데이트 동작 모드

```py
class ModeUpdate(Enum):

    None_               = 0x00

    Ready               = 0x01      # 업데이트 가능 상태
    Update              = 0x02      # 업데이트 중
    Complete            = 0x03      # 업데이트 완료

    Faild               = 0x04      # 업데이트 실패(업데이트 완료까지 갔으나 body의 CRC16이 일치하지 않는 경우 등)

    EndOfType           = 0x05
```


<br>
<br>


## <a name="FlightEvent">FlightEvent</a>

비행 이벤트

```py
class FlightEvent(Enum):
    
    None_               = 0x00

    TakeOff             = 0x01      # 이륙

    FlipFront           = 0x02      # Reserved
    FlipRear            = 0x03      # Reserved
    FlipLeft            = 0x04      # Reserved
    FlipRight           = 0x05      # Reserved

    Stop                = 0x06      # 정지
    Landing             = 0x07      # 착륙
    Reverse             = 0x08      # 뒤집기

    Shot                = 0x09      # 미사일 쏠때 움직임
    UnderAttack         = 0x0A      # 미사일 맞을때 움직임

    EndOfType           = 0x0B
```


<br>
<br>


## <a name="DriveEvent">DriveEvent</a>

주행 이벤트

```py
class DriveEvent(Enum):
    
    None_               = 0x00

    Stop                = 0x01
    
    Shot                = 0x02
    UnderAttack         = 0x03

    EndOfType           = 0x04
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

    EndOfType           = 0x03
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

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. **System**
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)

<br>

[Index](index.md)
