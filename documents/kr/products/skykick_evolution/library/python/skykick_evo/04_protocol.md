**[*e_drone* for python](index.md)** / **Protocol**

Modified : 2021.1.4

---

<h3>데이터 송수신과 관련된 정의를 소개합니다.</h3>

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="DataType"></a>
## DataType

데이터 타입

전송하는 데이터의 형식을 알려줍니다.

```py
class DataType(Enum):
    
    None_                       = 0x00      # 없음
    
    Ping                        = 0x01      # 통신 확인
    Ack                         = 0x02      # 데이터 수신에 대한 응답
    Error                       = 0x03      # 오류(reserve, 비트 플래그는 추후에 지정)
    Request                     = 0x04      # 지정한 타입의 데이터 요청
    Information                 = 0x07      # 펌웨어 및 장치 정보
    Control                     = 0x10      # 조종

    Command                     = 0x11      # 명령
    Pairing                     = 0x12      # 페어링
    ResponseRate                = 0x13      # RF 응답률

    # Light
    LightManual                 = 0x20      # LED 수동 제어
    LightMode                   = 0x21      # LED 모드
    LightEvent                  = 0x22      # LED 이벤트
    LightDefault                = 0x23      # LED 초기 모드

    # 상태, 센서
    State                       = 0x40      # 드론의 상태(비행 모드 방위기준 배터리량)
    Altitude                    = 0x43      # 높이, 고도
    Motion                      = 0x44      # Motion 센서 데이터(IMU)
    VisionSensor                = 0x47      # Vision X, Y, Z 데이터

    # 설정
    Count                       = 0x50      # 카운트
    Trim                        = 0x52      # 트림

    # Devices
    Motor                       = 0x60      # 모터 제어 및 현재 제어값 확인
    Buzzer                      = 0x62      # 부저 제어

    # Input
    Button                      = 0x70      # 버튼 입력
    Joystick                    = 0x71      # 조이스틱 입력

    # Information Assembled
    InformationAssembledForController   = 0xA0      # 자주 갱신되는 비행 데이터 모음

    EndOfType                           = 0xDC
```


<br>
<br>


<a name="CommandType"></a>
## CommandType

명령 타입

단일 명령 또는 추가 옵션을 보내는 것으로 실행할 수 있는 기능들을 담고 있습니다.

```py
class CommandType(Enum):
    
    None_                   = 0x00      # 없음

    Stop                    = 0x01      # 정지

    # 설정
    ModeControlFlight       = 0x02      # 비행 제어 모드 설정
    Headless                = 0x03      # 헤드리스 모드 선택
    Trim                    = 0x04      # 트림 변경

    ClearBias               = 0x05      # 자이로 바이어스 리셋(트림도 같이 초기화 됨)
    ClearTrim               = 0x06      # 트림 초기화

    FlightEvent             = 0x07      # 비행 이벤트 실행

    SetDefault              = 0x08      # 기본 설정으로 초기화

    EndOfType               = 0xEC
```


<br>
<br>


<a name="Header"></a>
## Header

헤더

헤더 뒤에 이어지는 데이터의 타입과 길이, 데이터를 전송하는 곳과 수신 받을 곳을 담고 있습니다.

```py
class Header(ISerializable):

    def __init__(self):
        self.dataType    = DataType.None_
        self.length      = 0
        self.from_       = DeviceType.None_
        self.to_         = DeviceType.None_
```

| 변수 이름     | 형식                                    | 크기     | 범위    | 설명                       |
|:-------------:|:---------------------------------------:|:--------:|:-------:|:---------------------------|
| dataType      | [DataType](#DataType)                   | 1 Byte   | -       | 데이터의 타입              |
| length        | UInt8                                   | 1 Byte   | 0 ~ 255 | 데이터의 길이              |
| from_         | [DeviceType](03_system.md#DeviceType)   | 1 Byte   | -       | 데이터를 전송하는 장치     |
| to_           | [DeviceType](03_system.md#DeviceType)   | 1 Byte   | -       | 데이터를 수신하는 장치     |


<br>
<br>


<a name="Ping"></a>
## Ping

Ping

다른 장치와의 연결 상태를 확인할 때 사용합니다. 상대 장치는 Ping에 대한 응답으로 Ack를 전송합니다.

조종기나 드론에서 Ping 전송 시 systemTime에는 Ping을 전송하는 장치의 시스템 시간 값이 들어갑니다.

```py
class Ping(ISerializable):

    def __init__(self):
        self.systemTime     = 0
```

| 변수 이름    | 형식            | 크기     | 범위   | 설명              |
|:------------:|:---------------:|:--------:|:------:|:------------------|
| systemTime   | UInt64          | 8 Byte   | -      | 시스템 시간       |

- e.g. [Ping 테스트(이벤트 함수 등록)](examples_01_ping.md#Class_Ping)


<br>
<br>


<a name="Ack"></a>
## Ack

응답

드론이나 조종기에 데이터 요청을 전송한 경우 해당하는 데이터를 응답합니다. 만약 해당 데이터가 준비되지 않은 경우에는 Ack를 응답으로 전송합니다.

데이터를 전송한 장치는 Ack를 확인하여 데이터가 정상적으로 전달되었는지 확인할 수 있습니다.

```py
class Ack(ISerializable):

    def __init__(self):
        self.systemTime     = 0
        self.dataType       = DataType.None_
        self.crc16          = 0
```

| 변수 이름      | 형식                    | 크기     | 범위  | 설명                                     |
|:--------------:|:-----------------------:|:--------:|:-----:|:-----------------------------------------|
| systemTime     | UInt64                  | 8 Byte   | -     | 시스템 시간                              |
| dataType       | [DataType](#DataType)   | 1 Byte   | -     | 수신 받은 데이터 타입                    |
| crc16          | UInt16                  | 2 Byte   | -     | 수신 받은 헤더와 데이터의 CRC16 값       |

- e.g. [Ping 테스트(이벤트 함수 등록)](examples_01_ping.md#Class_Ping)


<br>
<br>


<a name="Error"></a>
## Error

오류

드론에 문제가 생긴 경우 Error 클래스를 600ms 주기로 RF를 통해 전송합니다.

errorFlagsForSensor와 errorFlagsForState는 각각의 값에 해당하는 플래그를 조합하여 여러 오류들이 동시에 발생하는 것을 표시합니다.

문제가 완전히 없어진 경우 Error 플래그를 0으로 초기화하여 추가로 5회 전송 후 전송을 중단합니다.

```py
class Error(ISerializable):

    def __init__(self):
        self.systemTime             = 0
        self.errorFlagsForSensor    = 0
        self.errorFlagsForState     = 0
```

| 변수 이름            | 형식                                                     | 크기     | 범위  | 설명                  |
|:--------------------:|:--------------------------------------------------------:|:--------:|:-----:|:----------------------|
| systemTime           | UInt64                                                   | 8 Byte   | -     | 시스템 시간           |
| errorFlagsForSensor  | [ErrorFlagsForSensor](03_system.md#ErrorFlagsForSensor)  | 4 Byte   | -     | 센서 오류 플래그 조합 |
| errorFlagsForState   | [ErrorFlagsForState](03_system.md#ErrorFlagsForState)    | 4 Byte   | -     | 상태 오류 플래그 조합 |

- e.g. [IMU 센서 보정](examples_13_error.md#Error_ImuCalibrating)


<br>
<br>


<a name="Request"></a>
## Request

요청

드론이나 조종기에 데이터를 요청할 때 사용합니다.

```py
class Request(ISerializable):

    def __init__(self):
        self.dataType    = DataType.None_
```

| 변수 이름     | 형식                        | 크기     | 범위  | 설명                  |
|:-------------:|:---------------------------:|:--------:|:-----:|:----------------------|
| dataType      | [DataType](#DataType)       | 1 Byte   | -     | 요청할 데이터 타입    |


<br>
<br>


<a name="Information"></a>
## Information

펌웨어 정보

현재 펌웨어의 정보와 업데이트 진행 상황 등을 포함하고 있습니다.

```py
class Information(ISerializable):

    def __init__(self):
        self.modeUpdate     = ModeUpdate.None_

        self.modelNumber    = ModelNumber.None_
        self.version        = Version()

        self.year           = 0
        self.month          = 0
        self.day            = 0
```

| 변수 이름     | 형식                                      | 크기     | 범위 | 설명                |
|:-------------:|:-----------------------------------------:|:--------:|:----:|:--------------------|
| modeUpdate    | [ModeUpdate](03_system.md#ModeUpdate)     | 1 Byte   | -    | 업데이트 진행 상황  |
| modelNumber   | [ModelNumber](03_system.md#ModelNumber)   | 4 Byte   | -    | 모델 번호           |
| version       | [Version](#Version)                       | 4 Byte   | -    | 펌웨어의 버전       |
| year          | UInt16                                    | 2 Byte   | -    | 펌웨어 빌드 년      |
| month         | UInt8                                     | 1 Byte   | -    | 펌웨어 빌드 월      |
| day           | UInt8                                     | 1 Byte   | -    | 펌웨어 빌드 일      |

- e.g. [조종기의 펌웨어 정보 요청(이벤트 함수 등록)](examples_12_information.md#Class_Information)


<br>
<br>


<a name="Pairing"></a>
## Pairing

페어링

장치의 페어링 정보를 확인하거나 변경할 때 사용합니다.

```py
class Pairing(ISerializable):

    def __init__(self):
        self.address0       = 0
        self.address1       = 0
        self.address2       = 0
        self.address3       = 0
        self.address4       = 0
```

| 변수 이름       | 형식      | 크기     | 범위       | 설명               |
|:---------------:|:---------:|:--------:|:----------:|:-------------------|
| address0        | UInt8     | 1 Byte   | 0 ~ 127    | 장치의 주소 0      |
| address1        | UInt8     | 1 Byte   | 0 ~ 127    | 장치의 주소 1      |
| address2        | UInt8     | 1 Byte   | 0 ~ 127    | 장치의 주소 2      |
| address3        | UInt8     | 1 Byte   | 0 ~ 127    | 장치의 주소 3      |
| address4        | UInt8     | 1 Byte   | 0 ~ 127    | 장치의 주소 4      |


<br>
<br>


<a name="ResponseRate"></a>
## Rssi

RSSI

Signal response rate

[http://www.metageek.com/training/resources/understanding-response_rate.html](http://www.metageek.com/training/resources/understanding-responseRate.html)

현재 무선으로 연결된 장치의 데이터 응답률을 반환합니다.

```py
class Rssi(ISerializable):

    def __init__(self):
        self.responseRate       = 0
```

| 변수 이름    | 형식     | 범위      | 크기     | 설명        |
|:------------:|:--------:|:---------:|:--------:|:------------|
| responseRate | Int8     | 0 ~ 100   | 1 Byte   | 신호 응답률 |


<br>
<br>


<a name="Command"></a>
## Command

명령

드론 또는 조종기에 명령을 전달할 때 사용합니다.

option에는 각 형식의 value 값 또는 숫자 값을 넣으셔야 합니다.

```py
class Command(ISerializable):

    def __init__(self):
        self.commandType    = CommandType.None_
        self.option         = 0
```

| 변수 이름      | 형식                                                 | 크기     | 범위   | 설명       |
|:--------------:|:----------------------------------------------------:|:--------:|:------:|:-----------|
| commandType    | [CommandType](#CommandType)                          | 1 Byte   | -      | 명령 타입  |
| option         | [ModeControlFlight](03_system.md#ModeControlFlight)  | 1 Byte   | -      | 옵션       |
|                | [FlightEvent](03_system.md#FlightEvent)              | 1 Byte   | -      |            |
|                | [Headless](03_system.md#Headless)                    | 1 Byte   | -      |            |
|                | [TrimIncDec](03_system.md#TrimIncDec)                | 1 Byte   | -      |            |
|                | UInt8                                                | 1 Byte   | -      |            |


<br>
<br>


<a name="ControlQuad8"></a>
## ControlQuad8

비행 조종

```py
class ControlQuad8(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
        self.throttle   = 0
```

| 변수 이름   | 형식      | 크기     | 범위       | 설명       |
|:-----------:|:---------:|:--------:|:----------:|:-----------|
| roll        | Int8      | 1 Byte   | -100 ~ 100 | Roll       |
| pitch       | Int8      | 1 Byte   | -100 ~ 100 | Pitch      |
| yaw         | Int8      | 1 Byte   | -100 ~ 100 | Yaw        |
| throttle    | Int8      | 1 Byte   | -100 ~ 100 | Throttle   |


<br>
<br>


<a name="ControlQuad8AndRequestData"></a>
## ControlQuad8AndRequestData

비행 조종 + 데이터 요청

```py
class ControlQuad8AndRequestData(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
        self.throttle   = 0
        self.dataType   = DataType.None_
```

| 변수 이름   | 형식                    | 크기     | 범위       | 설명                  |
|:-----------:|:-----------------------:|:--------:|:----------:|:----------------------|
| roll        | Int8                    | 1 Byte   | -100 ~ 100 | Roll                  |
| pitch       | Int8                    | 1 Byte   | -100 ~ 100 | Pitch                 |
| yaw         | Int8                    | 1 Byte   | -100 ~ 100 | Yaw                   |
| throttle    | Int8                    | 1 Byte   | -100 ~ 100 | Throttle              |
| dataType    | [DataType](#DataType)   | 1 Byte   | -          | 요청할 데이터 타입    |


<br>
<br>


<a name="ControlPosition16"></a>
## ControlPosition16

드론 이동 명령

모든 변수에 2byte 정수를 사용하는 대신 position과 velocity의 값에 x10을 적용.

```py
class ControlPosition16(ISerializable):

    def __init__(self):
        self.positionX          = 0
        self.positionY          = 0
        self.positionZ          = 0

        self.velocity          = 0

        self.heading            = 0
        self.rotationalVelocity = 0
```

| 변수 이름             | 형식   | 크기     | 범위                       | 단위          | 설명                 |
|:---------------------:|:------:|:--------:|:--------------------------:|:--------------|:---------------------|
| positionX             | Int16  | 2 Byte   | -100 ~ 100(-10.0 ~ 10.0)   | meter x 10    | 앞(+), 뒤(-)         |
| positionY             | Int16  | 2 Byte   | -100 ~ 100(-10.0 ~ 10.0)   | meter x 10    | 좌(+), 우(-)         |
| positionZ             | Int16  | 2 Byte   | -100 ~ 100(-10.0 ~ 10.0)   | meter x 10    | 위(+), 아래(-)       |
| velocity              | Int16  | 2 Byte   | 5 ~ 20(0.5 ~ 2.0)          | m/s x 10      | 위치 이동 속도       |
| heading               | Int16  | 2 Byte   | -360 ~ 360                 | degree        | 좌회전(+), 우회전(-) |
| rotationalVelocity    | Int16  | 2 Byte   | 10 ~ 360                   | degree/s      | 좌우 회전 속도       |


<br>
<br>


<a name="ControlPosition"></a>
## ControlPosition

드론 이동 명령

position과 velocity는 실수 값, heading과 rotationalVelocity에는 정수 값 사용

```py
class ControlPosition(ISerializable):

    def __init__(self):
        self.positionX          = 0
        self.positionY          = 0
        self.positionZ          = 0

        self.velocity           = 0

        self.heading            = 0
        self.rotationalVelocity = 0
```

| 변수 이름             | 형식   | 크기     | 범위           | 단위     | 설명                 |
|:---------------------:|:------:|:--------:|:--------------:|:---------|:---------------------|
| positionX             | float  | 4 Byte   | -10.0 ~ 10.0   | meter    | 앞(+), 뒤(-)         |
| positionY             | float  | 4 Byte   | -10.0 ~ 10.0   | meter    | 좌(+), 우(-)         |
| positionZ             | float  | 4 Byte   | -10.0 ~ 10.0   | meter    | 위(+), 아래(-)       |
| velocity              | float  | 4 Byte   | 0.5 ~ 2.0      | m/s      | 위치 이동 속도       |
| heading               | Int16  | 2 Byte   | -360 ~ 360     | degree   | 좌회전(+), 우회전(-) |
| rotationalVelocity    | Int16  | 2 Byte   | 10 ~ 360       | degree/s | 좌우 회전 속도       |


<br>
<br>


<a name="LightModeDrone"></a>
## LightModeDrone

드론 LED 동작 모드

```py
class LightModeDrone(Enum):
    
    None_                   = 0x00

    RearNone                = 0x10
    RearManual              = 0x11      # 수동 제어
    RearHold                = 0x12      # 지정한 색상을 계속 켬
    RearFlicker             = 0x13      # 깜빡임
    RearFlickerDouble       = 0x14      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    RearDimming             = 0x15      # 밝기 제어하여 천천히 깜빡임

    BodyNone                = 0x20
    BodyManual              = 0x21      # 수동 제어
    BodyHold                = 0x22      # 지정한 색상을 계속 켬
    BodyFlicker             = 0x23      # 깜빡임
    BodyFlickerDouble       = 0x24      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    BodyDimming             = 0x25      # 밝기 제어하여 천천히 깜빡임

    ANone                   = 0x30
    AManual                 = 0x31      # 수동 제어
    AHold                   = 0x32      # 지정한 색상을 계속 켬
    AFlicker                = 0x33      # 깜빡임
    AFlickerDouble          = 0x34      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    ADimming                = 0x35      # 밝기 제어하여 천천히 깜빡임

    BNone                   = 0x40
    BManual                 = 0x41      # 수동 제어
    BHold                   = 0x42      # 지정한 색상을 계속 켬
    BFlicker                = 0x43      # 깜빡임
    BFlickerDouble          = 0x44      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    BDimming                = 0x45      # 밝기 제어하여 천천히 깜빡임

    CNone                   = 0x50
    CManual                 = 0x51      # 수동 제어
    CHold                   = 0x52      # 지정한 색상을 계속 켬
    CFlicker                = 0x53      # 깜빡임
    CFlickerDouble          = 0x54      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    CDimming                = 0x55      # 밝기 제어하여 천천히 깜빡임

    EndOfType               = 0x56
```


<br>
<br>


<a name="LightFlagsDrone"></a>
## LightFlagsDrone

드론 LED 플래그

```py
class LightFlagsDrone(Enum):
    
    None_               = 0x0000

    Rear                = 0x0001
    BodyRed             = 0x0002
    BodyGreen           = 0x0004
    BodyBlue            = 0x0008

    A                   = 0x0010
    B                   = 0x0020
    CRed                = 0x0040
    CGreen              = 0x0080
    CBlue               = 0x0100
```


<br>
<br>


<a name="LightModeController"></a>
## LightModeController

조종기 LED 동작 모드

```py
class LightModeController(Enum):
    
    None_               = 0x00

    # Body
    BodyNone            = 0x20
    BodyManual          = 0x21      # 수동 조작
    BodyHold            = 0x22
    BodyFlicker         = 0x23
    BodyFlickerDouble   = 0x24
    BodyDimming         = 0x25

    EndOfType           = 0x26
```


<br>
<br>


<a name="LightFlagsController"></a>
## LightFlagsController

조종기 LED 플래그

```py
class LightFlagsController(Enum):
    
    None_               = 0x00

    BodyRed             = 0x80
    BodyGreen           = 0x40
    BodyBlue            = 0x20
```


<br>
<br>


<a name="Color"></a>
## Color

RGB LED 색상 설정

0일 때 꺼지고 255일 때 가장 밝습니다.

```py
class Color(ISerializable):

    def __init__(self):
        self.r      = 0
        self.g      = 0
        self.b      = 0
```

| 변수 이름   | 형식    | 크기     | 범위     | 설명    |
|:-----------:|:-------:|:--------:|:--------:|:--------|
| r           | UInt8   | 1 Byte   | 0 ~ 255  | Red     |
| g           | UInt8   | 1 Byte   | 0 ~ 255  | Green   |
| b           | UInt8   | 1 Byte   | 0 ~ 255  | Blue    |


<br>
<br>


<a name="Colors"></a>
## Colors

색상 팔레트 인덱스

드론과 조종기 내부에 정의된 팔레트의 색상 인덱스입니다.
의도보다 색상이 더 밝게 표현되기 때문에 테스트 후 사용하기를 권해드립니다.

```py
class Colors(Enum):

    AliceBlue              = 0
    AntiqueWhite           = 1
    Aqua                   = 2
    Aquamarine             = 3
    Azure                  = 4
    Beige                  = 5
    Bisque                 = 6
    Black                  = 7
    BlanchedAlmond         = 8
    Blue                   = 9
    BlueViolet             = 10
    Brown                  = 11
    BurlyWood              = 12
    CadetBlue              = 13
    Chartreuse             = 14
    Chocolate              = 15
    Coral                  = 16
    CornflowerBlue         = 17
    Cornsilk               = 18
    Crimson                = 19
    Cyan                   = 20
    DarkBlue               = 21
    DarkCyan               = 22
    DarkGoldenRod          = 23
    DarkGray               = 24
    DarkGreen              = 25
    DarkKhaki              = 26
    DarkMagenta            = 27
    DarkOliveGreen         = 28
    DarkOrange             = 29
    DarkOrchid             = 30
    DarkRed                = 31
    DarkSalmon             = 32
    DarkSeaGreen           = 33
    DarkSlateBlue          = 34
    DarkSlateGray          = 35
    DarkTurquoise          = 36
    DarkViolet             = 37
    DeepPink               = 38
    DeepSkyBlue            = 39
    DimGray                = 40
    DodgerBlue             = 41
    FireBrick              = 42
    FloralWhite            = 43
    ForestGreen            = 44
    Fuchsia                = 45
    Gainsboro              = 46
    GhostWhite             = 47
    Gold                   = 48
    GoldenRod              = 49
    Gray                   = 50
    Green                  = 51
    GreenYellow            = 52
    HoneyDew               = 53
    HotPink                = 54
    IndianRed              = 55
    Indigo                 = 56
    Ivory                  = 57
    Khaki                  = 58
    Lavender               = 59
    LavenderBlush          = 60
    LawnGreen              = 61
    LemonChiffon           = 62
    LightBlue              = 63
    LightCoral             = 64
    LightCyan              = 65
    LightGoldenRodYellow   = 66
    LightGray              = 67
    LightGreen             = 68
    LightPink              = 69
    LightSalmon            = 70
    LightSeaGreen          = 71
    LightSkyBlue           = 72
    LightSlateGray         = 73
    LightSteelBlue         = 74
    LightYellow            = 75
    Lime                   = 76
    LimeGreen              = 77
    Linen                  = 78
    Magenta                = 79
    Maroon                 = 80
    MediumAquaMarine       = 81
    MediumBlue             = 82
    MediumOrchid           = 83
    MediumPurple           = 84
    MediumSeaGreen         = 85
    MediumSlateBlue        = 86
    MediumSpringGreen      = 87
    MediumTurquoise        = 88
    MediumVioletRed        = 89
    MidnightBlue           = 90
    MintCream              = 91
    MistyRose              = 92
    Moccasin               = 93
    NavajoWhite            = 94
    Navy                   = 95
    OldLace                = 96
    Olive                  = 97
    OliveDrab              = 98
    Orange                 = 99
    OrangeRed              = 100
    Orchid                 = 101
    PaleGoldenRod          = 102
    PaleGreen              = 103
    PaleTurquoise          = 104
    PaleVioletRed          = 105
    PapayaWhip             = 106
    PeachPuff              = 107
    Peru                   = 108
    Pink                   = 109
    Plum                   = 110
    PowderBlue             = 111
    Purple                 = 112
    RebeccaPurple          = 113
    Red                    = 114
    RosyBrown              = 115
    RoyalBlue              = 116
    SaddleBrown            = 117
    Salmon                 = 118
    SandyBrown             = 119
    SeaGreen               = 120
    SeaShell               = 121
    Sienna                 = 122
    Silver                 = 123
    SkyBlue                = 124
    SlateBlue              = 125
    SlateGray              = 126
    Snow                   = 127
    SpringGreen            = 128
    SteelBlue              = 129
    Tan                    = 130
    Teal                   = 131
    Thistle                = 132
    Tomato                 = 133
    Turquoise              = 134
    Violet                 = 135
    Wheat                  = 136
    White                  = 137
    WhiteSmoke             = 138
    Yellow                 = 139
    YellowGreen            = 140
    
    EndOfType              = 141
```


<br>
<br>


<a name="LightManual"></a>
## LightManual

LED 수동 제어

flag로 지정한 LED의 밝기를 변경합니다. 지정하지 않은 LED의 밝기는 그대로 유지됩니다. 밝기 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

flags에는 [LightFlagsDrone](#LightFlagsDrone), [LightFlagsController](#LightFlagsController)의 value 값을 사용하시거나 직접 플래그에 해당하는 비트를 선택하시면 됩니다.

```py
class LightManual(ISerializable):

    def __init__(self):
        self.flags          = 0
        self.brightness     = 0
```

| 변수 이름   | 형식   | 크기     | 범위              | 설명            |
|:-----------:|:------:|:--------:|:-----------------:|:----------------|
| flags       | UInt16 | 2 Byte   | 0x0000 ~ 0xFFFF   | LED 선택 플래그 |
| brightness  | UInt8  | 1 Byte   | 0 ~ 255           | 밝기            |


<br>
<br>


<a name="LightMode"></a>
## LightMode

LED 모드

mode 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.


```py
class LightMode(ISerializable):

    def __init__(self):
        self.mode        = 0
        self.interval    = 0
```

| 변수 이름   | 형식      | 크기     | 범위       | 설명                           |
|:-----------:|:---------:|:--------:|:----------:|:-------------------------------|
| mode        | UInt8     | 1 Byte   | -          | LED 동작 모드                  |
| interval    | UInt16    | 2 Byte   | 0 ~ 65535  | 내부 밝기 제어 함수 호출 주기  |


<br>
<br>


<a name="LightModeColor"></a>
## LightModeColor

LED 모드 변경(RGB)

RGB 색상을 직접 지정하여 LED 동작 모드를 변경합니다.

```py
class LightModeColor(ISerializable):
    
    def __init__(self):
        self.mode       = LightMode()
        self.color      = Color()
```

| 변수 이름   | 형식                     | 크기     | 범위   | 설명           |
|:-----------:|:------------------------:|:--------:|:------:|:---------------|
| mode        | [LightMode](#LightMode)  | 3 Byte   | -      | LED 동작 모드  |
| color       | [Color](#Color)          | 3 Byte   | -      | LED RGB 색상   |

- e.g. [조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColor / 클래스 데이터를 채워서 전송)](examples_10_light.md#Class_LightModeColor)


<br>
<br>


<a name="LightModeColors"></a>
## LightModeColors

LED 모드 변경(Palette)

팔레트 인덱스를 사용하여 LED 동작 모드를 변경합니다.

```py
class LightModeColors(ISerializable):
    
    def __init__(self):
        self.mode       = LightMode()
        self.colors     = Colors.Black
```

| 변수 이름  | 형식                      | 크기     | 범위  | 설명               |
|:----------:|:-------------------------:|:--------:|:-----:|:-------------------|
| mode       | [LightMode](#LightMode)   | 3 Byte   | -     | LED 동작 모드      |
| colors     | [Colors](#Colors)         | 1 Byte   | -     | LED 팔레트 인덱스  |

- e.g. [조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / 클래스 데이터를 채워서 전송)](examples_10_light.md#Class_LightModeColors)


<br>
<br>


<a name="LightEvent"></a>
## LightEvent

LED 이벤트

이벤트는 지정한 횟수만큼의 동작을 실행하고 끝나면, 이전에 Mode로 설정된 동작을 다시 실행합니다.

event 변수에는 [LightModeDrone](#LightModeDrone), [LightModeController](#LightModeController)의 value 값을 사용합니다.

```py
class LightEvent(ISerializable):

    def __init__(self):
        self.event      = 0
        self.interval   = 0
        self.repeat     = 0
```

| 변수 이름  | 형식     | 크기     | 범위       | 설명                           |
|:----------:|:--------:|:--------:|:----------:|:-------------------------------|
| event      | UInt8    | 1 Byte   | -          | LED 동작 모드                  |
| interval   | UInt16   | 2 Byte   | 0 ~ 65535  | 내부 색상 변화 함수 호출 주기  |
| repeat     | UInt8    | 1 Byte   | 0 ~ 255    | 반복 횟수                      |


<br>
<br>


<a name="LightEventColor"></a>
## LightEventColor

LED 이벤트 변경(RGB)

RGB 색상을 직접 지정하여 LED 이벤트를 실행합니다.

```py
class LightEventColor(ISerializable):
    
    def __init__(self):
        self.event      = LightEvent()
        self.color      = Color()
```

| 변수 이름   | 형식                        | 크기     | 범위  | 설명           |
|:-----------:|:---------------------------:|:--------:|:-----:|:---------------|
| event       | [LightEvent](#LightEvent)   | 4 Byte   | -     | LED 이벤트     |
| color       | [Color](#Color)             | 3 Byte   | -     | LED RGB 색상   |



<br>
<br>


<a name="LightEventColors"></a>
## LightEventColors

LED 이벤트 변경(Palette)

팔레트 인덱스를 사용하여 LED 동작 모드를 변경합니다.

```py
class LightEventColors(ISerializable):
    
    def __init__(self):
        self.event      = LightEvent()
        self.colors     = Colors.Black
```

| 변수 이름 | 형식                       | 크기     | 범위  | 설명              |
|:---------:|:--------------------------:|:--------:|:-----:|:------------------|
| event     | [LightEvent](#LightEvent)  | 4 Byte   | -     | LED 이벤트        |
| colors    | [Colors](#Colors)          | 1 Byte   | -     | LED 팔레트 인덱스 |



<br>
<br>


<a name="DisplayPixel"></a>
## DisplayPixel

픽셀 색상

```py
class DisplayPixel(Enum):
    
    Black               = 0x00
    White               = 0x01
    Inverse             = 0x02
```


<br>
<br>


<a name="DisplayFont"></a>
## DisplayFont

폰트

```py
class DisplayFont(Enum):
    
    LiberationMono5x8   = 0x00
    LiberationMono10x16 = 0x01
```


<br>
<br>


<a name="DisplayAlign"></a>
## DisplayAlign

문자열 정렬

```py
class DisplayAlign(Enum):
    
    Left                = 0x00
    Center              = 0x01
    Right               = 0x02
```


<br>
<br>


<a name="DisplayLine"></a>
## DisplayLine

선

```py
class DisplayLine(Enum):
    
    Solid               = 0x00
    Dotted              = 0x01
    Dashed              = 0x02
```


<br>
<br>


<a name="DisplayClearAll"></a>
## DisplayClearAll

화면 전체 지우기

```py
class DisplayClearAll(ISerializable):

    def __init__(self):
        self.pixel       = DisplayPixel.White
```

| 변수 이름   | 형식                           | 크기     | 범위 | 설명        |
|:-----------:|:------------------------------:|:--------:|:----:|:------------|
| pixel       | [DisplayPixel](#DisplayPixel)  | 1 Byte   | -    | 채울 색상   |


<br>
<br>


<a name="DisplayClear"></a>
## DisplayClear

선택 영역 지우기

```py
class DisplayClear(ISerializable):

    def __init__(self):
        self.x           = 0
        self.y           = 0
        self.width       = 0
        self.height      = 0
        self.pixel       = DisplayPixel.White
```

| 변수 이름  | 형식                            | 크기     | 범위          | 설명            |
|:----------:|:-------------------------------:|:--------:|:-------------:|:----------------|
| x          | Int16                           | 2 Byte   | -2000 ~ 2000  | X축 시작 위치   |
| y          | Int16                           | 2 Byte   | -2000 ~ 2000  | Y축 시작 위치   |
| width      | Int16                           | 2 Byte   | -2000 ~ 2000  | 너비            |
| height     | Int16                           | 2 Byte   | -2000 ~ 2000  | 높이            |
| pixel      | [DisplayPixel](#DisplayPixel)   | 1 Byte   | -             | 채울 색상       |


<br>
<br>


<a name="DisplayClear"></a>
## DisplayClear

선택 영역 반전

```py
class DisplayInvert(ISerializable):

    def __init__(self):
        self.x           = 0
        self.y           = 0
        self.width       = 0
        self.height      = 0
```

| 변수 이름   | 형식    | 크기     | 범위          | 설명           |
|:-----------:|:-------:|:--------:|:-------------:|:---------------|
| x           | Int16   | 2 Byte   | -2000 ~ 2000  | X축 시작 위치  |
| y           | Int16   | 2 Byte   | -2000 ~ 2000  | Y축 시작 위치  |
| width       | Int16   | 2 Byte   | -2000 ~ 2000  | 너비           |
| height      | Int16   | 2 Byte   | -2000 ~ 2000  | 높이           |


<br>
<br>


<a name="DisplayDrawPoint"></a>
## DisplayDrawPoint

점 찍기

```py
class DisplayDrawPoint(ISerializable):

    def __init__(self):
        self.x           = 0
        self.y           = 0
        self.pixel       = DisplayPixel.White
```

| 변수 이름  | 형식                           | 크기     | 범위          | 설명       |
|:----------:|:------------------------------:|:--------:|:-------------:|:-----------|
| x          | Int16                          | 2 Byte   | -2000 ~ 2000  | X축 위치   |
| y          | Int16                          | 2 Byte   | -2000 ~ 2000  | Y축 위치   |
| pixel      | [DisplayPixel](#DisplayPixel)  | 1 Byte   | -             | 점 색상    |


<br>
<br>


<a name="DisplayDrawLine"></a>
## DisplayDrawLine

선 그리기

```py
class DisplayDrawLine(ISerializable):

    def __init__(self):
        self.x1          = 0
        self.y1          = 0
        self.x2          = 0
        self.y2          = 0
        self.pixel       = DisplayPixel.White
        self.line        = DisplayLine.Solid
```

| 변수 이름  | 형식                           | 크기     | 범위          | 설명           |
|:----------:|:------------------------------:|:--------:|:-------------:|:---------------|
| x1         | Int16                          | 2 Byte   | -2000 ~ 2000  | X축 시작 위치  |
| y1         | Int16                          | 2 Byte   | -2000 ~ 2000  | Y축 시작 위치  |
| x2         | Int16                          | 2 Byte   | -2000 ~ 2000  | X축 끝 위치    |
| y2         | Int16                          | 2 Byte   | -2000 ~ 2000  | Y축 끝 위치    |
| pixel      | [DisplayPixel](#DisplayPixel)  | 1 Byte   | -             | 선 색상        |
| line       | [DisplayLine](#DisplayLine)    | 1 Byte   | -             | 선 형태        |


<br>
<br>


<a name="DisplayDrawRect"></a>
## DisplayDrawRect

사각형 그리기

```py
class DisplayDrawRect(ISerializable):

    def __init__(self):
        self.x           = 0
        self.y           = 0
        self.width       = 0
        self.height      = 0
        self.pixel       = DisplayPixel.White
        self.flagFill    = True
        self.line        = DisplayLine.Solid
```

| 변수 이름  | 형식                            | 크기     | 범위          | 설명                     |
|:----------:|:-------------------------------:|:--------:|:-------------:|:-------------------------|
| x          | Int16                           | 2 Byte   | -2000 ~ 2000  | X축 시작 위치            |
| y          | Int16                           | 2 Byte   | -2000 ~ 2000  | Y축 시작 위치            |
| width      | Int16                           | 2 Byte   | -2000 ~ 2000  | 너비                     |
| height     | Int16                           | 2 Byte   | -2000 ~ 2000  | 높이                     |
| pixel      | [DisplayPixel](#DisplayPixel)   | 1 Byte   | -             | 색상                     |
| flagFill   | Bool                            | 1 Byte   | -             | True인 경우 내부를 채움  |
| line       | [DisplayLine](#DisplayLine)     | 1 Byte   | -             | 선 형태                  |


<br>
<br>


<a name="DisplayDrawCircle"></a>
## DisplayDrawCircle

원 그리기

```py
class DisplayDrawCircle(ISerializable):

    def __init__(self):
        self.x          = 0
        self.y          = 0
        self.radius     = 0
        self.pixel      = DisplayPixel.White
        self.flagFill   = True
```

| 변수 이름 | 형식                           | 크기     | 범위          | 설명                    |
|:---------:|:------------------------------:|:--------:|:-------------:|:------------------------|
| x         | Int16                          | 2 Byte   | -2000 ~ 2000  | X축 중심점 위치         |
| y         | Int16                          | 2 Byte   | -2000 ~ 2000  | Y축 중심점 위치         |
| radius    | Int16                          | 2 Byte   | 1 ~ 2000      | 반지름                  |
| pixel     | [DisplayPixel](#DisplayPixel)  | 1 Byte   | -             | 색상                    |
| flagFill  | Bool                           | 1 Byte   | -             | True인 경우 내부를 채움 |


<br>
<br>


<a name="DisplayDrawString"></a>
## DisplayDrawString

문자열 그리기

```py
class DisplayDrawString(ISerializable):

    def __init__(self):
        self.x          = 0
        self.y          = 0
        self.font       = DisplayFont.LiberationMono5x8
        self.pixel      = DisplayPixel.White
        self.message    = ""
```

| 변수 이름  | 형식                            | 크기          | 범위          | 설명           |
|:----------:|:-------------------------------:|:-------------:|:-------------:|:---------------|
| x          | Int16                           | 2 Byte        | -2000 ~ 2000  | X축 위치       |
| y          | Int16                           | 2 Byte        | -2000 ~ 2000  | Y축 위치       |
| font       | [DisplayFont](#DisplayFont)     | 1 Byte        | -             | 폰트           |
| pixel      | [DisplayPixel](#DisplayPixel)   | 1 Byte        | -             | 색상           |
| message    | ASCII String                    | 12 Byte 이하  | -             | 표시할 문자열  |


<br>
<br>


<a name="DisplayDrawStringAlign"></a>
## DisplayDrawStringAlign

문자열 정렬하여 그리기

***x_start***와 ***x_end*** 사이에 지정한 위치로 문자열을 정렬하여 표시합니다.

```py
class DisplayDrawStringAlign(ISerializable):

    def __init__(self):
        
        self.x_start    = 0
        self.x_end      = 0
        self.y          = 0
        self.align      = DisplayAlign.Center
        self.font       = DisplayFont.LiberationMono5x8
        self.pixel      = DisplayPixel.White
        self.message    = ""
```

| 변수 이름  | 형식                            | 크기          | 범위          | 설명           |
|:----------:|:-------------------------------:|:-------------:|:-------------:|:---------------|
| x_start    | Int16                           | 2 Byte        | -2000 ~ 2000  | X축 시작 위치  |
| x_end      | Int16                           | 2 Byte        | -2000 ~ 2000  | X축 끝 위치    |
| y          | Int16                           | 2 Byte        | -2000 ~ 2000  | Y축 위치       |
| align      | [DisplayAlign](#DisplayAlign)   | 1 Byte        | -             | 정렬           |
| font       | [DisplayFont](#DisplayFont)     | 1 Byte        | -             | 폰트           |
| pixel      | [DisplayPixel](#DisplayPixel)   | 1 Byte        | -             | 색상           |
| message    | ASCII String                    | 12 Byte 이하  | -             | 표시할 문자열  |


<br>
<br>


<a name="BuzzerMode"></a>
## BuzzerMode

버저 모드

```py
class BuzzerMode(Enum):

    Stop                = 0     # 정지(Mode에서의 Stop은 통신에서 받았을 때 Buzzer를 끄는 용도로 사용, set으로만 호출)

    Mute                = 1     # 묵음 즉시 적용
    MuteReserve         = 2     # 묵음 예약

    Scale               = 3     # 음계 즉시 적용
    ScaleReserve        = 4     # 음계 예약

    Hz                  = 5     # 주파수 즉시 적용
    HzReserve           = 6     # 주파수 예약

    EndOfType           = 7
```


<br>
<br>


<a name="BuzzerScale"></a>
## BuzzerScale

버저 음계

```py
class BuzzerScale(Enum):

    C1 = 0x00; CS1 = 0x01; D1 = 0x02; DS1 = 0x03; E1 = 0x04; F1 = 0x05; FS1 = 0x06; G1 = 0x07; GS1 = 0x08; A1 = 0x09; AS1 = 0x0A; B1 = 0x0B;
    C2 = 0x0C; CS2 = 0x0D; D2 = 0x0E; DS2 = 0x0F; E2 = 0x10; F2 = 0x11; FS2 = 0x12; G2 = 0x13; GS2 = 0x14; A2 = 0x15; AS2 = 0x16; B2 = 0x17;
    C3 = 0x18; CS3 = 0x19; D3 = 0x1A; DS3 = 0x1B; E3 = 0x1C; F3 = 0x1D; FS3 = 0x1E; G3 = 0x1F; GS3 = 0x20; A3 = 0x21; AS3 = 0x22; B3 = 0x23;
    C4 = 0x24; CS4 = 0x25; D4 = 0x26; DS4 = 0x27; E4 = 0x28; F4 = 0x29; FS4 = 0x2A; G4 = 0x2B; GS4 = 0x2C; A4 = 0x2D; AS4 = 0x2E; B4 = 0x2F;

    C5 = 0x30; CS5 = 0x31; D5 = 0x32; DS5 = 0x33; E5 = 0x34; F5 = 0x35; FS5 = 0x36; G5 = 0x37; GS5 = 0x38; A5 = 0x39; AS5 = 0x3A; B5 = 0x3B;
    C6 = 0x3C; CS6 = 0x3D; D6 = 0x3E; DS6 = 0x3F; E6 = 0x40; F6 = 0x41; FS6 = 0x42; G6 = 0x43; GS6 = 0x44; A6 = 0x45; AS6 = 0x46; B6 = 0x47;
    C7 = 0x48; CS7 = 0x49; D7 = 0x4A; DS7 = 0x4B; E7 = 0x4C; F7 = 0x4D; FS7 = 0x4E; G7 = 0x4F; GS7 = 0x50; A7 = 0x51; AS7 = 0x52; B7 = 0x53;
    C8 = 0x54; CS8 = 0x55; D8 = 0x56; DS8 = 0x57; E8 = 0x58; F8 = 0x59; FS8 = 0x5A; G8 = 0x5B; GS8 = 0x5C; A8 = 0x5D; AS8 = 0x5E; B8 = 0x5F;

    EndOfType   = 0x60

    Mute        = 0xEE  # 묵음
    Fin         = 0xFF  # 악보의 끝
```


<br>
<br>


<a name="Buzzer"></a>
## Buzzer

버저

BuzzerMode가 **BuzzerMode.Scale**이거나 **BuzzerMode.ScaleReserve**인 경우 value에는 [BuzzerScale](#BuzzerScale)의 value 값을 사용하시면 됩니다.

BuzzerMode가 **BuzzerMode.Hz**이거나 **BuzzerMode.HzReserve**인 경우 value에는 Hz 값을 사용하시면 됩니다.

```py
class Buzzer(ISerializable):

    def __init__(self):
        self.mode       = BuzzerMode.Stop
        self.value      = 0
        self.time       = 0
```

| 변수 이름  | 형식                      | 크기   | 범위       | 설명                   |
|:----------:|:-------------------------:|:------:|:----------:|:-----------------------|
| mode       | [BuzzerMode](#BuzzerMode) | 1 Byte | -          | 버저 동작 모드         |
| value      | UInt16                    | 2 Byte | 0 ~ 8000   | Scale 값 또는 Hz 값    |
| time       | UInt16                    | 2 Byte | 0 ~ 65,535 | 소리를 지속할 시간(ms) |

- e.g. [Buzzer 클래스 데이터를 직접 채워서 전송하기](examples_08_buzzer.md#Class_Buzzer)

<br>
<br>


<a name="VibratorMode"></a>
## VibratorMode

진동 모드

```py
class VibratorMode(Enum):

    Stop                = 0     # 정지

    Instantally         = 1     # 즉시 적용
    Continually         = 2     # 예약

    EndOfType           = 3
```


<br>
<br>


<a name="Vibrator"></a>
## Vibrator

진동

```py
class Vibrator(ISerializable):

    def __init__(self):
        self.mode       = VibratorMode.Stop
        self.on         = 0
        self.off        = 0
        self.total      = 0
```

| 변수 이름  | 형식                          | 크기     | 범위        | 설명                |
|:----------:|:-----------------------------:|:--------:|:-----------:|:--------------------|
| mode       | [VibratorMode](#VibratorMode) | 1 Byte   | -           | 진동 동작 모드      |
| on         | UInt16                        | 2 Byte   | 0 ~ 65,535  | 진동을 켠 시간(ms)  |
| off        | UInt16                        | 2 Byte   | 0 ~ 65,535  | 진동을 끈 시간(ms)  |
| total      | UInt16                        | 2 Byte   | 0 ~ 65,535  | 전체 동작 시간(ms)  |

- e.g. [Vibrator 클래스 데이터를 직접 채워서 전송하기](examples_09_vibrator.md#Class_Vibrator)


<br>
<br>


<a name="ButtonFlagController"></a>
## ButtonFlagController

조종기 버튼 플래그

```py
class ButtonFlagController(Enum):

    None_               = 0x0000
    
    FrontLeftTop        = 0x0001
    FrontLeftBottom     = 0x0002
    FrontRightTop       = 0x0004
    FrontRightBottom    = 0x0008
    
    TopLeft             = 0x0010
    TopRight            = 0x0020    # POWER ON/OFF
    
    MidUp               = 0x0040
    MidLeft             = 0x0080
    MidRight            = 0x0100
    MidDown             = 0x0200
    
    BottomLeft          = 0x0400
    BottomRight         = 0x0800
```


<br>
<br>


<a name="ButtonFlagDrone"></a>
## ButtonFlagDrone

드론 버튼 플래그

```py
class ButtonFlagDrone(Enum):

    None_           = 0x0000
    
    Reset           = 0x0001
```


<br>
<br>


<a name="ButtonEvent"></a>
## ButtonEvent

버튼 이벤트

```py
class ButtonEvent(Enum):

    None_             = 0x0000
    
    Down              = 0x0001  # 누르기 시작
    Press             = 0x0002  # 누르는 중
    Up                = 0x0003  # 뗌
    
    EndContinuePress  = 0x0004  # 연속 입력 종료
```


<br>
<br>


<a name="Button"></a>
## Button

버튼 입력

button에는 [ButtonFlagController](#ButtonFlagController) 또는 [ButtonFlagDrone](#ButtonFlagDrone) 의 플래그가 조합된 값이 들어옵니다.

```py
class Button(ISerializable):

    def __init__(self):
        self.button     = 0
        self.event      = ButtonEvent.None_
```

| 변수 이름 | 형식                        | 크기     | 범위  | 설명         |
|:---------:|:---------------------------:|:--------:|:-----:|:-------------|
| button    | UInt16                      | 2 Byte   | -     | 버튼 입력    |
| event     | [ButtonEvent](#ButtonEvent) | 1 Byte   | -     | 버튼 이벤트  |

- e.g. [버튼 입력값 출력](examples_12_input.md#Button)


<br>
<br>


<a name="JoystickDirection"></a>
## JoystickDirection

조이스틱 방향

```py
class JoystickDirection(Enum):

    None_   = 0         # 정의하지 않은 영역(무시함)

    VT      = 0x10      #   위(세로)
    VM      = 0x20      # 중앙(세로)
    VB      = 0x40      # 아래(세로)

    HL      = 0x01      #   왼쪽(가로)
    HM      = 0x02      #   중앙(가로)
    HR      = 0x04      # 오른쪽(가로)

    TL = 0x11;  TM = 0x12;  TR = 0x14
    ML = 0x21;  CN = 0x22;  MR = 0x24
    BL = 0x41;  BM = 0x42;  BR = 0x44
```


<br>
<br>


<a name="JoystickEvent"></a>
## JoystickEvent

조이스틱 이벤트

```py
class JoystickEvent(Enum):

    None_       = 0     # 이벤트 없음
    
    In          = 1     # 특정 영역에 진입
    Stay        = 2     # 특정 영역에서 상태 유지
    Out         = 3     # 특정 영역에서 벗어남
    
    EndOfType   = 4
```


<br>
<br>


<a name="JoystickBlock"></a>
## JoystickBlock

조이스틱 하나의 축

```py
class JoystickBlock(ISerializable):

    def __init__(self):
        self.x          = 0
        self.y          = 0
        self.direction  = JoystickDirection.None_
        self.event      = JoystickEvent.None_
```

| 변수 이름  | 형식                                    | 크기     | 범위          | 설명           |
|:----------:|:---------------------------------------:|:--------:|:-------------:|:---------------|
| x          | Int8                                    | 1 Byte   | -100 ~ 100    | X축 값         |
| y          | Int8                                    | 1 Byte   | -100 ~ 100    | Y축 값         |
| direction  | [JoystickDirection](#JoystickDirection) | 1 Byte   | -             | 조이스틱 방향  |
| event      | [JoystickEvent](#JoystickEvent)         | 1 Byte   | -             | 이벤트         |


<br>
<br>


<a name="Joystick"></a>
## Joystick

조이스틱 좌우 입력

```py
class Joystick(ISerializable):

    def __init__(self):
        self.left       = JoystickBlock()
        self.right      = JoystickBlock()
```

| 변수 이름 | 형식                             | 크기     | 범위  | 설명            |
|:---------:|:--------------------------------:|:--------:|:-----:|:----------------|
| left      | [JoystickBlock](#JoystickBlock)  | 4 Byte   | -     | 왼쪽 조이스틱   |
| right     | [JoystickBlock](#JoystickBlock)  | 4 Byte   | -     | 오른쪽 조이스틱 |

- e.g. [조이스틱 입력값 출력](examples_12_input.md#Joystick)


<br>
<br>


<a name="RawFlow"></a>
## RawFlow

옵티컬 플로우로 계산한 상대 위치 값

```py
class Flow(ISerializable):

    def __init__(self):
        self.x     = 0
        self.y     = 0
```

| 변수 이름  | 형식      | 크기     | 범위  | 설명    |
|:----------:|:---------:|:--------:|:-----:|:--------|
| x          | Float32   | 4 Byte   | -     | X축(m)  |
| y          | Float32   | 4 Byte   | -     | Y축(m)  |


<br>
<br>


<a name="State"></a>
## State

드론 상태

```py
class State(ISerializable):

    def __init__(self):
        self.modeSystem         = ModeSystem.None_
        self.modeFlight         = ModeFlight.None_

        self.modeControlFlight  = ModeControlFlight.None_
        self.modeMovement       = ModeMovement.None_
        self.headless           = Headless.None_
        self.sensorOrientation  = SensorOrientation.None_
        self.battery            = 0
```

| 변수 이름         | 형식                                                | 크기     | 범위     | 설명                   |
|:-----------------:|:---------------------------------------------------:|:--------:|:--------:|:-----------------------|
| modeSystem        | [ModeSystem](03_system.md#ModeSystem)               | 1 Byte   | -        | System 동작 모드       |
| modeFlight        | [ModeFlight](03_system.md#ModeFlight)               | 1 Byte   | -        | 비행 제어기 동작 모드  |
| modeControlFlight | [ModeControlFlight](03_system.md#ModeControlFlight) | 1 Byte   | -        | 비행 제어 모드         |
| modeMovement      | [ModeMovement](03_system.md#ModeMovement)           | 1 Byte   | -        | 이동 상태              |
| headless          | [Headless](03_system.md#Headless)                   | 1 Byte   | -        | Headless 설정 상태     |
| sensorOrientation | [SensorOrientation](03_system.md#SensorOrientation) | 1 Byte   | -        | 센서 방향              |
| battery           | UInt8                                               | 1 Byte   | 0 ~ 100  | 드론 배터리 잔량       |

- e.g. [드론 모드를 변경 후 확인](examples_07_setup.md#ModeVehicle)


<br>
<br>


<a name="Altitude"></a>
## Altitude

고도 데이터

```py
class Altitude(ISerializable):

    def __init__(self):
        self.temperature    = 0
        self.pressure       = 0
        self.altitude       = 0
        self.rangeHeight    = 0
```

| 변수 이름   | 형식     | 크기     | 범위 | 설명                            |
|:-----------:|:--------:|:--------:|:----:|:--------------------------------|
| temperature | Float32  | 4 Byte   | -    | 온도(℃)                         |
| pressure    | Float32  | 4 Byte   | -    | 압력                            |
| altitude    | Float32  | 4 Byte   | -    | 압력을 해발고도로 변환한 값(m)  |
| rangeHeight | Float32  | 4 Byte   | -    | 거리센서에서 출력한 높이 값(m)  |

- e.g. [고도 데이터 확인](examples_05_sensor.md#Altitude)


<br>
<br>


<a name="Motion"></a>
## Motion

Motion 센서 데이터와 드론의 자세

angleRoll, anglePitch, angleYaw는 Attitude에서 받을 수 있는 드론의 자세값과 같은 값입니다.

accelX, accelY, accelZ 값은 **x10**을 한 값입니다.

```py
class Motion(ISerializable):

    def __init__(self):
        self.accelX     = 0
        self.accelY     = 0
        self.accelZ     = 0
        self.gyroRoll   = 0
        self.gyroPitch  = 0
        self.gyroYaw    = 0
        self.angleRoll  = 0
        self.anglePitch = 0
        self.angleYaw   = 0
```

| 변수 이름  | 형식   | 크기    | 범위                              | 단위                 | 설명          |
|:----------:|:------:|:-------:|:---------------------------------:|:--------------------:|:--------------|
| accelX     | Int16  | 2 Byte  | -1568 ~ 1568<br>(-156.8 ~ 156.8)  | m/s<sup>2</sup> x 10 | 가속도 X      |
| accelY     | Int16  | 2 Byte  | -1568 ~ 1568<br>(-156.8 ~ 156.8)  | m/s<sup>2</sup> x 10 | 가속도 Y      |
| accelZ     | Int16  | 2 Byte  | -1568 ~ 1568<br>(-156.8 ~ 156.8)  | m/s<sup>2</sup> x 10 | 가속도 Z      |
| gyroRoll   | Int16  | 2 Byte  | -2000 ~ 2000                      | degree/s             | 자이로 Roll   |
| gyroPitch  | Int16  | 2 Byte  | -2000 ~ 2000                      | degree/s             | 자이로 Pitch  |
| gyroYaw    | Int16  | 2 Byte  | -2000 ~ 2000                      | degree/s             | 자이로 Yaw    |
| angleRoll  | Int16  | 2 Byte  | -180 ~ 180                        | degree               | 자세 Roll     |
| anglePitch | Int16  | 2 Byte  | -180 ~ 180                        | degree               | 자세 Pitch    |
| angleYaw   | Int16  | 2 Byte  | -180 ~ 180                        | degree               | 자세 Yaw      |

- e.g. [Motion 센서 데이터 확인](examples_05_sensor.md#Imu)


<br>
<br>


<a name="Vector"></a>
## Vector

벡터

```py
class Vector(ISerializable):

    def __init__(self):
        self.x      = 0
        self.y      = 0
        self.z      = 0
```

| 변수 이름  | 형식    | 크기     | 범위              | 설명    |
|:----------:|:-------:|:--------:|:-----------------:|:--------|
| x          | Int16   | 2 Byte   | -32,768 ~ 32,767  | X       |
| y          | Int16   | 2 Byte   | -32,768 ~ 32,767  | Y       |
| z          | Int16   | 2 Byte   | -32,768 ~ 32,767  | Z       |


<br>
<br>


<a name="Count"></a>
## Count

카운트

각 카운트 값은 드론 내부에 UInt32로 저장하고 있지만, 전송 시에는 UInt16으로 변환하여 전송합니다. 만약 더 큰 값이 필요한 상황이 생기면 변경할 예정입니다.(6만번 이상 이착륙 등)

```py
class Count(ISerializable):

    def __init__(self):
        self.timeSystem     = 0
        self.timeFlight     = 0
        self.countTakeOff   = 0
        self.countLanding   = 0
        self.countAccident  = 0
```

| 변수 이름        | 형식       | 크기     | 범위       | 설명             |
|:----------------:|:----------:|:--------:|:----------:|:-----------------|
| timeSystem       | UInt32     | 4 Byte   | -          | 사용 시간(ms)   |
| timeFlight       | UInt32     | 4 Byte   | -          | 비행 시간(ms)    |
| countTakeOff     | UInt16     | 2 Byte   | 0 ~ 65535  | 이륙 횟수        |
| countLanding     | UInt16     | 2 Byte   | 0 ~ 65535  | 착륙 횟수        |
| countAccident    | UInt16     | 2 Byte   | 0 ~ 65535  | 충돌 횟수        |


<br>
<br>


<a name="Trim"></a>
## Trim

비행 트림 설정

호버링 시 기체가 한쪽으로 쏠리는 현상이 발생하면 반대 방향으로 적절한 값을 주어 정상적으로 동작하게 만들 수 있습니다.

```py
class Trim(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
        self.throttle   = 0
```

| 변수 이름 | 형식     | 크기     | 범위         | 설명       |
|:---------:|:--------:|:--------:|:------------:|:-----------|
| roll      | Int16    | 2 Byte   | -200 ~ 200   | Roll       |
| pitch     | Int16    | 2 Byte   | -200 ~ 200   | Pitch      |
| yaw       | Int16    | 2 Byte   | -200 ~ 200   | Yaw        |
| throttle  | Int16    | 2 Byte   | -200 ~ 200   | Throttle   |

- e.g. [드론 Trim 설정 변경 후 확인](examples_07_setup.md#Trim)


<br>
<br>


<a name="MotorBlock"></a>
## MotorBlock

모터 블럭

```py
class MotorBlock(ISerializable):

    def __init__(self):
        self.rotation   = Rotation.None_
        self.value      = 0
```

| 변수 이름  | 형식                               | 크기     | 범위      | 설명           |
|:----------:|:----------------------------------:|:--------:|:---------:|:---------------|
| rotation   | [Rotation](03_system.md#Rotation)  | 1 Byte   | -         | 모터 회전 방향 |
| value      | UInt16                             | 2 Byte   | 0 ~ 4095  | 모터 회전 속도 |


<br>
<br>


<a name="Motor"></a>
## Motor

모터 전체 제어

모터 순서는 왼쪽 앞부터 시계 방향입니다.

```py
class Motor(ISerializable):

    def __init__(self):
        self.motor      = []
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
```

| 변수 이름  | 형식                        | 크기     | 범위  | 설명           |
|:----------:|:---------------------------:|:--------:|:-----:|:---------------|
| motor[0]   | [MotorBlock](#MotorBlock)   | 3 Byte   | -     | 왼쪽 앞 모터   |
| motor[1]   | [MotorBlock](#MotorBlock)   | 3 Byte   | -     | 오른쪽 앞 모터 |
| motor[2]   | [MotorBlock](#MotorBlock)   | 3 Byte   | -     | 오른쪽 뒤 모터 |
| motor[3]   | [MotorBlock](#MotorBlock)   | 3 Byte   | -     | 왼쪽 뒤 모터   |


<br>

---

<h3><i>skykick</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [Command Line](02_commandline.md)
 3. [System](03_system.md)
 4. **Protocol**
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
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
