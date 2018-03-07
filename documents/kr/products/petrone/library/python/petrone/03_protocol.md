**[*petrone* for python](index.md)** / **Protocol**

Modified : 2018.3.7

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
    
    ##### BLE + Serial #####
    Ping                        = 0x01      # 통신 확인
    Ack                         = 0x02      # 데이터 수신에 대한 응답
    Error                       = 0x03      # 오류(reserve 비트 플래그는 추후에 지정)
    Request                     = 0x04      # 지정한 타입의 데이터 요청
    Passcode                    = 0x05      # 새로운 페어링 비밀 번호

    Control                     = 0x10      # 조종
    Command                     = 0x11      # 명령
    Command2                    = 0x12      # 다중 명령(2가지 설정을 동시에 변경)
    Command3                    = 0x13      # 다중 명령(3가지 설정을 동시에 변경)

    # Light
    LightMode                   = 0x20      # LED 모드 지정
    LightMode2                  = 0x21      # LED 모드 지정 2개
    LightModeCommand            = 0x22      # LED 모드 커맨드
    LightModeCommandIr          = 0x23      # LED 모드 커맨드 IR 데이터 송신
    LightModeColor              = 0x24      # LED 모드 3색 직접 지정
    LightModeColor2             = 0x25      # LED 모드 3색 직접 지정 2개

    LightEvent                  = 0x26      # LED 이벤트
    LightEvent2                 = 0x27      # LED 이벤트 2개
    LightEventCommand           = 0x28      # LED 이벤트 커맨드
    LightEventCommandIr         = 0x29      # LED 이벤트 커맨드 IR 데이터 송신
    LightEventColor             = 0x2A      # LED 이벤트 3색 직접 지정
    LightEventColor2            = 0x2B      # LED 이벤트 3색 직접 지정 커맨드

    LightModeDefaultColor       = 0x2C      # LED 초기 모드 3색 직접 지정
    LightModeDefaultColor2      = 0x2D      # LED 초기 모드 3색 직접 지정 2개

    # 상태 설정
    Address                     = 0x30      # IEEE Address
    State                       = 0x31      # 드론의 상태(비행 모드 방위기준 배터리량)
    Attitude                    = 0x32      # 드론의 자세(Angle)
    GyroBias                    = 0x33      # 자이로 바이어스 값
    TrimAll                     = 0x34      # 전체 트림
    TrimFlight                  = 0x35      # 비행 트림
    TrimDrive                   = 0x36      # 주행 트림

    CountFlight                 = 0x37      # 비행 관련 카운트 
    CountDrive                  = 0x38      # 주행 관련 카운트 

    # IR
    IrMessage                   = 0x40      # IR 데이터 송수신

    # Sensor and control
    Imu                         = 0x50      # IMU Raw
    Pressure                    = 0x51      # 압력 센서 데이터
    ImageFlow                   = 0x52      # ImageFlow
    Button                      = 0x53      # 버튼
    Battery                     = 0x54      # 배터리
    Motor                       = 0x55      # 모터 제어 및 현재 제어값 확인
    Temperature                 = 0x56      # 온도
    Range                       = 0x57      # 적외선 거리 센서

    # Firmware update
    UpdateLookupTarget          = 0x90      # 업데이트 대상 장치 검색
    UpdateInformation           = 0x91      # 업데이트 정보
    Update                      = 0x92      # 업데이트 16바이트 단위
    UpdateLocationCorrect       = 0x93      # 업데이트 위치 정정

    # LINK 모듈
    LinkState                   = 0xE0      # 링크 모듈의 상태
    LinkEvent                   = 0xE1      # 링크 모듈의 이벤트
    LinkEventAddress            = 0xE2      # 링크 모듈의 이벤트 + 주소
    LinkRssi                    = 0xE3      # 링크와 연결된 장치의 RSSI값
    LinkDiscoveredDevice        = 0xE4      # 검색된 장치
    LinkPasscode                = 0xE5      # 페어링 시 필요한 Passcode 설정

    Message                     = 0xF0      # 문자열 메세지

    EndOfType                   = 0xFF
```


<br>
<br>


<a name="CommandType"></a>
## CommandType

명령 타입

단일 명령 또는 추가 옵션을 보내는 것으로 실행할 수 있는 기능들을 담고 있습니다.

```py
class CommandType(Enum):
    
    None_                       = 0x00      # 없음

    # 설정
    ModeVehicle                 = 0x10      # Vehicle 동작 모드 전환

    # 제어
    Headless                    = 0x20      # 헤드리스 모드 선택
    Trim                        = 0x21      # 트림 변경
    FlightEvent                 = 0x22      # 비행 이벤트 실행
    DriveEvent                  = 0x23      # 주행 이벤트 실행
    Stop                        = 0x24      # 정지

    ResetHeading                = 0x50      # 헤딩 리셋
    ClearGyroBias               = 0x51      # 자이로 바이어스 리셋(트림도 같이 초기화 됨)
    ClearTrim                   = 0x52      # 트림 초기화

    # 통신[Wireless Lan]
    ResetWirelessLan            = 0x70		# 무선랜 설정 리셋
    WirelessLanConnected        = 0x70      # 무선랜 연결
    WirelessLanDisconnected     = 0x70      # 무선랜 연결 해제

    # 통신[Bluetooth]
    PairingActivate             = 0x80      # 페어링 활성화
    PairingDeactivate           = 0x81      # 페어링 비활성화
    AdvertisingStart            = 0x82      # 장치를 검색 가능한 상태로 변경
    AdvertisingStop             = 0x83      # 장치를 검색 불가능한 상태로 변경
    TerminateConnection         = 0x84      # 연결 종료
    ClearBondList               = 0x85      # 본딩된 장치 리스트 제거

    # 요청
    Request                     = 0x90      # 지정한 타입의 데이터 요청
    UpdateCompleteSub           = 0x90      # 업데이트 완료 처리(Sub)
    ClearUpdateAreaMain         = 0x90      # 업데이트 할 영역 지우기(Main)


    # LINK 모듈
    LinkModeBroadcast           = 0xE0      # LINK 송수신 모드 전환
    LinkSystemReset             = 0xE1      # 시스템 재시작
    LinkDiscoverStart           = 0xE2      # 장치 검색 시작
    LinkDiscoverStop            = 0xE3      # 장치 검색 중단
    LinkConnect                 = 0xE4      # 지정한 인덱스의 장치 연결
    LinkDisconnect              = 0xE5      # 연결 해제
    LinkRssiPollingStart        = 0xE6      # RSSI 수집 시작
    LinkRssiPollingStop         = 0xE7      # RSSI 수집 중단

    EndOfType                   = 0xFF
```


<br>
<br>


<a name="Header"></a>
## Header

헤더

헤더 뒤에 이어지는 데이터의 타입과 길이를 담고 있습니다.

```py
class Header(ISerializable):

    def __init__(self):
        self.dataType    = DataType.None_
        self.length      = 0
```

| 변수 이름     | 형식                                    | 범위    | 크기     | 설명                       |
|:-------------:|:---------------------------------------:|:-------:|:--------:|:---------------------------|
| dataType      | [DataType](#DataType)                   | -       | 1 Byte   | 데이터의 타입              |
| length        | UInt8                                   | 0 ~ 255 | 1 Byte   | 데이터의 길이              |


<br>
<br>


<a name="Ping"></a>
## Ping

Ping

다른 장치와의 연결 상태를 확인할 때 사용합니다. 상대 장치는 Ping에 대한 응답으로 Ack를 전송합니다.

드론에서 Ping 전송 시 systemTime에는 Ping을 전송하는 장치의 시스템 시간 값이 들어갑니다.

```py
class Ping(ISerializable):

    def __init__(self):
        self.systemTime     = 0
```

| 변수 이름    | 형식            | 범위   | 크기     | 설명              |
|:------------:|:---------------:|:------:|:--------:|:------------------|
| systemTime   | UInt32          | -      | 4 Byte   | 시스템 시간       |


<br>
<br>


<a name="Ack"></a>
## Ack

응답

드론에 데이터 요청을 전송한 경우 해당하는 데이터를 응답합니다. 만약 해당 데이터가 준비되지 않은 경우에는 Ack를 응답으로 전송합니다.

데이터를 전송한 장치는 Ack를 확인하여 데이터가 정상적으로 전달되었는지 확인할 수 있습니다.

```py
class Ack(ISerializable):

    def __init__(self):
        self.systemTime     = 0
        self.dataType       = DataType.None_
```

| 변수 이름      | 형식                    | 범위  | 크기     | 설명                                     |
|:--------------:|:-----------------------:|:-----:|:--------:|:-----------------------------------------|
| systemTime     | UInt32                  | -     | 4 Byte   | 시스템 시간                              |
| dataType       | [DataType](#DataType)   | -     | 1 Byte   | 수신 받은 데이터 타입                    |


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

| 변수 이름     | 형식                        | 범위  | 크기     | 설명                  |
|:-------------:|:---------------------------:|:-----:|:--------:|:----------------------|
| dataType      | [DataType](#DataType)       | -     | 1 Byte   | 요청할 데이터 타입    |


<br>
<br>


<a name="Control"></a>
## Control

조종

비행 및 주행에 모두 사용할 수 있습니다.

```py
class Control(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
        self.throttle   = 0
```

| 변수 이름   | 형식      | 범위       | 크기     | 설명       |
|:-----------:|:---------:|:----------:|:--------:|:-----------|
| roll        | Int8      | -100 ~ 100 | 1 Byte   | Roll       |
| pitch       | Int8      | -100 ~ 100 | 1 Byte   | Pitch      |
| yaw         | Int8      | -100 ~ 100 | 1 Byte   | Yaw        |
| throttle    | Int8      | -100 ~ 100 | 1 Byte   | Throttle   |


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

| 변수 이름      | 형식                                    | 범위   | 크기     | 설명       |
|:--------------:|:---------------------------------------:|:------:|:--------:|:-----------|
| commandType    | [CommandType](#CommandType)             | -      | 1 Byte   | 명령 타입  |
| option         | [ModeVehicle](02_system.md#ModeVehicle) | -      | 1 Byte   | 옵션       |
|                | [FlightEvent](02_system.md#FlightEvent) | -      | 1 Byte   |            |
|                | [DriveEvent](02_system.md#DriveEvent)   | -      | 1 Byte   |            |
|                | [Headless](02_system.md#Headless)       | -      | 1 Byte   |            |
|                | [Trim](02_system.md#Trim)               | -      | 1 Byte   |            |
|                | UInt8                                   | -      | 1 Byte   |            |


<br>
<br>


<a name="LightModeDrone"></a>
## LightModeDrone

드론 LED 동작 모드

```py
class LightModeDrone(Enum):
    
    None_               = 0x00

    EyeNone             = 0x10
    EyeHold             = 0x11      # 지정한 색상을 계속 켬
    EyeMix              = 0x12      # 순차적으로 LED 색 변경
    EyeFlicker          = 0x13      # 깜빡임    	
    EyeFlickerDouble    = 0x14      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)    	
    EyeDimming          = 0x15      # 밝기 제어하여 천천히 깜빡임

    ArmNone             = 0x40
    ArmHold             = 0x41      # 지정한 색상을 계속 켬
    ArmMix              = 0x42      # 순차적으로 LED 색 변경
    ArmFlicker          = 0x43      # 깜빡임
    ArmFlickerDouble    = 0x44      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    ArmDimming          = 0x45      # 밝기 제어하여 천천히 깜빡임
    ArmFlow             = 0x46      # 앞에서 뒤로 흐름
    ArmFlowReverse      = 0x47      # 뒤에서 앞으로 흐름

    EndOfType           = 0x48
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

| 변수 이름   | 형식    | 범위     | 크기     | 설명    |
|:-----------:|:-------:|:--------:|:--------:|:--------|
| r           | UInt8   | 0 ~ 255  | 1 Byte   | Red     |
| g           | UInt8   | 0 ~ 255  | 1 Byte   | Green   |
| b           | UInt8   | 0 ~ 255  | 1 Byte   | Blue    |


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


<a name="LightMode"></a>
## LightMode

LED 모드

팔레트 인덱스를 사용하여 LED 동작 모드를 변경합니다.

```py
class LightMode(ISerializable):

    def __init__(self):
        self.mode        = LightModeDrone.None_
        self.colors      = Colors.Black
        self.interval    = 0
```

| 변수 이름   | 형식                              | 범위       | 크기     | 설명                           |
|:-----------:|:---------------------------------:|:----------:|:--------:|:-------------------------------|
| mode        | [LightModeDrone](#LightModeDrone) | -          | 1 Byte   | 드론 LED 동작 모드             |
| colors      | [Colors](#Colors)                 | -          | 1 Byte   | LED 팔레트 인덱스              |
| interval    | UInt8                             | 0 ~ 255    | 1 Byte   | 내부 밝기 제어 함수 호출 주기  |


<br>
<br>


<a name="LightModeCommand"></a>
## LightModeCommand

LED 모드 변경(Palette) + Command

LightMode에 Command를 추가하여 전송합니다.

```py
class LightModeCommand(ISerializable):
    
    def __init__(self):
        self.lightMode  = LightMode()
        self.command    = Command()
```

| 변수 이름  | 형식                     | 범위  | 크기     | 설명           |
|:----------:|:------------------------:|:-----:|:--------:|:---------------|
| lightMode  | [LightMode](#LightMode)  | -     | 3 Byte   | LED 모드       |
| command    | [Command](#Command)      | -     | 2 Byte   | 명령           |


<br>
<br>


<a name="LightModeCommandIr"></a>
## LightModeCommandIr

LED 모드 변경(Palette) + Command + IR

LightModeCommand에 적외선 전송 데이터를 추가하여 전송합니다.

```py
class LightModeCommandIr(ISerializable):
    
    def __init__(self):
        self.lightMode  = LightMode()
        self.command    = Command()
        self.irData     = 0
```

| 변수 이름  | 형식                      | 범위                     | 크기     | 설명                |
|:----------:|:-------------------------:|:------------------------:|:--------:|:--------------------|
| lightMode  | [LightMode](#LightMode)   | -                        | 3 Byte   | LED 모드            |
| command    | [Command](#Command)       | -                        | 2 Byte   | 명령                |
| irData     | UInt32                    | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 적외선 전송 데이터  |


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
        self.interval   = 0
```

| 변수 이름   | 형식                              | 범위     | 크기     | 설명                           |
|:-----------:|:---------------------------------:|:--------:|:--------:|:-------------------------------|
| mode        | [LightModeDrone](#LightModeDrone) | -        | 1 Byte   | 드론 LED 동작 모드             |
| color       | [Color](#Color)                   | -        | 3 Byte   | LED RGB 색상                   |
| interval    | UInt8                             | 0 ~ 255  | 1 Byte   | 내부 밝기 제어 함수 호출 주기  |


<br>
<br>


<a name="LightEvent"></a>
## LightEvent

LED 이벤트 변경(Palette)

팔레트 인덱스를 사용하여 LED 이벤트를 실행합니다.

```py
class LightEvent(ISerializable):
    
    def __init__(self):
        self.event      = LightModeDrone.None_
        self.colors     = Colors.Black
        self.interval   = 0
        self.repeat     = 0
```

| 변수 이름  | 형식                              | 범위     | 크기     | 설명                           |
|:----------:|:---------------------------------:|:--------:|:--------:|:-------------------------------|
| event      | [LightModeDrone](#LightModeDrone) | -        | 1 Byte   | 드론 LED 동작 모드             |
| colors     | [Colors](#Colors)                 | -        | 1 Byte   | LED 팔레트 인덱스              |
| interval   | UInt8                             | 0 ~ 255  | 1 Byte   | 내부 색상 변화 함수 호출 주기  |
| repeat     | UInt8                             | 0 ~ 255  | 1 Byte   | 반복 횟수                      |


<br>
<br>


<a name="LightEventCommand"></a>
## LightEventCommand

LED 이벤트 변경(Palette) + Command

LightEvent에 Command를 추가하여 전송합니다.

```py
class LightEventCommand(ISerializable):
    
    def __init__(self):
        self.lightEvent = LightEvent()
        self.command    = Command()
```

| 변수 이름  | 형식                      | 범위 | 크기     | 설명               |
|:----------:|:-------------------------:|:----:|:--------:|:-------------------|
| lightEvent | [LightEvent](#LightEvent) | -    | 4 Byte   | LED 이벤트         |
| command    | [Command](#Command)       | -    | 2 Byte   | 명령               |



<br>
<br>


<a name="LightEventCommandIr"></a>
## LightEventCommandIr

LED 모드 변경(Palette) + Command + IR

LightEventCommand에 적외선 전송 데이터를 추가하여 전송합니다.

```py
class LightEventCommandIr(ISerializable):
    
    def __init__(self):
        self.lightEvent = LightEvent()
        self.colors     = Colors.Black
        self.command    = Command()
        self.irData     = 0
```

| 변수 이름  | 형식                        | 범위                     | 크기     | 설명               |
|:----------:|:---------------------------:|:------------------------:|:--------:|:-------------------|
| lightEvent | [LightEvent](#LightEvent)   | -                        | 4 Byte   | LED 이벤트         |
| command    | [Command](#Command)         | -                        | 2 Byte   | 명령               |
| irData     | UInt32                      | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 적외선 전송 데이터 |


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

| 변수 이름  | 형식                              | 범위     | 크기     | 설명                           |
|:----------:|:---------------------------------:|:--------:|:--------:|:-------------------------------|
| event      | [LightModeDrone](#LightModeDrone) | -        | 1 Byte   | 드론 LED 동작 모드             |
| color      | [Color](#Color)                   | -        | 3 Byte   | LED RGB 색상                   |
| interval   | UInt8                             | 0 ~ 255  | 1 Byte   | 내부 색상 변화 함수 호출 주기  |
| repeat     | UInt8                             | 0 ~ 255  | 1 Byte   | 반복 횟수                      |


<br>
<br>


<a name="Address"></a>
## Address

장치 주소

장치에 부여되는 고유 번호입니다.

```py
class Address(ISerializable):

    def __init__(self):
        self.address    = bytearray()
```

| 변수 이름  | 형식          | 범위  | 크기     | 설명         |
|:----------:|:-------------:|:-----:|:--------:|:-------------|
| address    | UInt8 Array   | -     | 6 Byte   | 장치 주소    |


<br>
<br>


<a name="State"></a>
## State

드론 상태

```py
class State(ISerializable):

    def __init__(self):
        self.modeVehicle        = ModeVehicle.None_

        self.modeSystem         = ModeSystem.None_
        self.modeFlight         = ModeFlight.None_
        self.modeDrive          = ModeDrive.None_

        self.sensorOrientation  = SensorOrientation.None_
        self.headless           = Headless.None_
        self.battery            = 0
```

| 변수 이름         | 형식                                                | 범위     | 크기     | 설명                   |
|:-----------------:|:---------------------------------------------------:|:--------:|:--------:|:-----------------------|
| modeVehicle       | [ModeVehicle](02_system.md#ModeVehicle)             | -        | 1 Byte   | Vehicle 동작 모드      |
| modeSystem        | [ModeSystem](02_system.md#ModeSystem)               | -        | 1 Byte   | System 동작 모드       |
| modeFlight        | [ModeFlight](02_system.md#ModeFlight)               | -        | 1 Byte   | 비행 제어기 동작 모드  |
| modeDrive         | [ModeDrive](02_system.md#ModeDrive)                 | -        | 1 Byte   | 주행 제어기 동작 모드  |
| sensorOrientation | [SensorOrientation](02_system.md#SensorOrientation) | -        | 1 Byte   | 센서 방향              |
| headless          | [Headless](02_system.md#Headless)                   | -        | 1 Byte   | Headless 설정 상태     |
| battery           | UInt8                                               | 0 ~ 100  | 1 Byte   | 드론 배터리 잔량       |


<br>
<br>


<a name="Attitude"></a>
## Attitude

자세

```py
class Attitude(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
```

| 변수 이름  | 형식       | 범위              | 크기     | 설명       |
|:----------:|:----------:|:-----------------:|:--------:|:-----------|
| roll       | Int16      | -32,768 ~ 32,767  | 2 Byte   | Roll       |
| pitch      | Int16      | -32,768 ~ 32,767  | 2 Byte   | Pitch      |
| yaw        | Int16      | -32,768 ~ 32,767  | 2 Byte   | Yaw        |


<br>
<br>


<a name="GyroBias"></a>
## GyroBias

자이로 바이어스

[Attitude](#Attitude)을 상속받습니다.

```py
class GyroBias(Attitude):
    pass
```

| 변수 이름 | 형식   | 범위              | 크기     | 설명    |
|:---------:|:------:|:-----------------:|:--------:|:--------|
| roll      | Int16  | -32,768 ~ 32,767  | 2 Byte   | Roll    |
| pitch     | Int16  | -32,768 ~ 32,767  | 2 Byte   | Pitch   |
| yaw       | Int16  | -32,768 ~ 32,767  | 2 Byte   | Yaw     |


<br>
<br>


<a name="TrimFlight"></a>
## TrimFlight

비행 트림 설정

호버링 시 기체가 한쪽으로 쏠리는 현상이 발생하면 반대 방향으로 적절한 값을 주어 정상적으로 동작하게 만들 수 있습니다.

```py
class TrimFlight(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
        self.throttle   = 0
```

| 변수 이름 | 형식     | 범위         | 크기     | 설명       |
|:---------:|:--------:|:------------:|:--------:|:-----------|
| roll      | Int16    | -200 ~ 200   | 2 Byte   | Roll       |
| pitch     | Int16    | -200 ~ 200   | 2 Byte   | Pitch      |
| yaw       | Int16    | -200 ~ 200   | 2 Byte   | Yaw        |
| throttle  | Int16    | -200 ~ 200   | 2 Byte   | Throttle   |


<br>
<br>


<a name="TrimDrive"></a>
## TrimDrive

주행 트림 설정

자동차 모드로 동작 시 직진이 잘 안될 경우 휘어지는 반대 방향으로 wheel 값을 주어 정상적으로 동작하게 만들 수 있습니다.

```py
class TrimDrive(ISerializable):

    def __init__(self):
        self.wheel      = 0
```

| 변수 이름 | 형식     | 범위           | 크기     | 설명    |
|:---------:|:--------:|:--------------:|:--------:|:--------|
| wheel     | Int16    | -200 ~ 200     | 2 Byte   | Wheel   |


<br>
<br>


<a name="CountFlight"></a>
## CountFlight

비행 카운터

각 카운터 값은 드론 내부에 UInt32로 저장하고 있지만 전송 시에는 UInt16으로 변환하여 전송합니다. 만약 더 큰 값이 필요한 상황이 생기면 변경할 예정입니다.(6만번 이상 이착륙 등)

```py
class CountFlight(ISerializable):

    def __init__(self):
        self.timeFlight     = 0

        self.countTakeOff   = 0
        self.countLanding   = 0
        self.countAccident  = 0
```

| 변수 이름        | 형식       | 범위       | 크기     | 설명             |
|:----------------:|:----------:|:----------:|:--------:|:-----------------|
| timeFlight       | UInt64     | -          | 8 Byte   | 비행 시간(ms)    |
| countTakeOff     | UInt16     | 0 ~ 65535  | 2 Byte   | 이륙 횟수        |
| countLanding     | UInt16     | 0 ~ 65535  | 2 Byte   | 착륙 횟수        |
| countAccident    | UInt16     | 0 ~ 65535  | 2 Byte   | 충돌 횟수        |


<br>
<br>


<a name="CountDrive"></a>
## CountDrive

주행 카운터

각 카운터 값은 드론 내부에 UInt32로 저장하고 있지만 전송 시에는 UInt16으로 변환하여 전송합니다. 만약 더 큰 값이 필요한 상황이 생기면 변경할 예정입니다.(6만번 이상 이착륙 등)

countAccident 변수는 주행 중 충돌을 카운트 하기 위해 만든 변수이나 실제 주행 시 노면이 고르지 못할 때의 충격에 의해서도 카운트가 증가하는 문제가 있습니다. 현재로는 크게 의미가 없는 값으로 생각하시면 됩니다.

```py
class CountDrive(ISerializable):
    
    def __init__(self):
        self.timeDrive      = 0

        self.countAccident  = 0
```

| 변수 이름     | 형식     | 범위          | 크기     | 설명           |
|:-------------:|:--------:|:-------------:|:--------:|:---------------|
| timeDrive     | UInt64   | -             | 8 Byte   | 주행 시간(ms)  |
| countAccident | UInt16   | 0 ~ 65,535    | 2 Byte   | 충돌 횟수      |


<br>
<br>


<a name="IrMessage"></a>
## IrMessage

적외선 데이터 송수신

적외선 데이터 수신기가 드론 전면과 후면에 각각 1개씩 부착되어 있습니다.

direction은 어떤 수신기가 데이터를 받았는지를 알려주는 역할을 합니다.

```py
class IrMessage(ISerializable):

    def __init__(self):
        self.direction  = Direction.None_
        self.irData     = 0
```

| 변수 이름   | 형식                                 | 범위                     | 크기     | 설명                              |
|:-----------:|:------------------------------------:|:------------------------:|:--------:|:----------------------------------|
| direction   | [Direction](02_system.md#System_Direction)  | -                        | 1 Byte   | 적외선 데이터를 받은 센서의 위치  |
| irData      | UInt32                               | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 데이터                            |


<br>
<br>


<a name="Imu"></a>
## Imu

IMU 센서 데이터와 드론의 자세

angleRoll, anglePitch, angleYaw는 Attitude에서 받을 수 있는 드론의 자세값과 같은 값입니다.

```py
class Imu(ISerializable):

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

| 변수 이름  | 형식     | 범위              | 크기     | 설명           |
|:----------:|:--------:|:-----------------:|:--------:|:---------------|
| accelX     | Int16    | -32,768 ~ 32,767  | 2 Byte   | 가속도 X       |
| accelY     | Int16    | -32,768 ~ 32,767  | 2 Byte   | 가속도 Y       |
| accelZ     | Int16    | -32,768 ~ 32,767  | 2 Byte   | 가속도 Z       |
| gyroRoll   | Int16    | -32,768 ~ 32,767  | 2 Byte   | 자이로 Roll    |
| gyroPitch  | Int16    | -32,768 ~ 32,767  | 2 Byte   | 자이로 Pitch   |
| gyroYaw    | Int16    | -32,768 ~ 32,767  | 2 Byte   | 자이로 Yaw     |
| angleRoll  | Int16    | -32,768 ~ 32,767  | 2 Byte   | 자세 Roll      |
| anglePitch | Int16    | -32,768 ~ 32,767  | 2 Byte   | 자세 Pitch     |
| angleYaw   | Int16    | -32,768 ~ 32,767  | 2 Byte   | 자세 Yaw       |


<br>
<br>


<a name="Pressure"></a>
## Pressure

압력 센서

```py
class Pressure(ISerializable):

    def __init__(self):
        self.d1             = 0
        self.d2             = 0
        self.temperature    = 0
        self.pressure       = 0
```

| 변수 이름   | 형식     | 범위 | 크기     | 설명                            |
|:-----------:|:--------:|:----:|:--------:|:--------------------------------|
| d1          | UInt32   | -    | 4 Byte   | Raw data 1                      |
| d2          | UInt32   | -    | 4 Byte   | Raw data 2                      |
| temperature | UInt32   | -    | 4 Byte   | 온도(℃)                        |
| pressure    | UInt32   | -    | 4 Byte   | 압력을 해발고도로 변환한 값(m)  |


<br>
<br>


<a name="ImageFlow"></a>
## ImageFlow

옵티컬 플로우로 계산한 상대 위치 값

```py
class ImageFlow(ISerializable):

    def __init__(self):
        self.positionX     = 0
        self.positionY     = 0
```

| 변수 이름  | 형식      | 범위  | 크기     | 설명    |
|:----------:|:---------:|:-----:|:--------:|:--------|
| positionX  | UInt32    | -     | 4 Byte   | X축(m)  |
| positionY  | UInt32    | -     | 4 Byte   | Y축(m)  |


<br>
<br>


<a name="ButtonFlagDrone"></a>
## ButtonFlagDrone

드론 버튼 플래그

```py
class ButtonFlagDrone(Enum):

    None_           = 0x00
    
    Reset           = 0x01
```


<br>
<br>


<a name="Button"></a>
## Button

버튼 입력

```py
class Button(ISerializable):

    def __init__(self):
        self.button     = 0
```

| 변수 이름 | 형식                        | 범위  | 크기     | 설명         |
|:---------:|:---------------------------:|:-----:|:--------:|:-------------|
| button    | UInt16                      | -     | 1 Byte   | 버튼 입력    


<br>
<br>


<a name="Battery"></a>
## Battery

배터리

```py
class Battery(ISerializable):

    def __init__(self):
        self.adjustGradient             = 0
        self.adjustYIntercept           = 0
        self.gradient                   = 0
        self.yIntercept                 = 0
        self.flagBatteryCalibration     = False
        self.batteryRaw                 = 0
        self.batteryPercent             = 0
        self.voltage                    = 0
```

| 변수 이름               | 형식   | 범위         | 크기     | 설명                                |
|:-----------------------:|:------:|:------------:|:--------:|:------------------------------------|
| adjustGradient          | Int16  | -            | 2 Byte   | 기울기 조정값                       |
| adjustYIntercept        | Int16  | -            | 2 Byte   | Y 절편 조정값                       |
| gradient                | Int16  | -            | 2 Byte   | 기울기                              |
| yIntercept              | Int16  | -            | 2 Byte   | Y 절편                              |
| flagBatteryCalibration  | Bool   | True / False | 1 Byte   | 배터리 캘리브레이션 완료 여부       |
| batteryRaw              | Int32  | 0 ~ 4096     | 4 Byte   | 배터리 ADC Raw 값                   |
| batteryPercent          | Int8   | 0 ~ 100      | 1 Byte   | 배터리 % 값                         |
| voltage                 | Int16  | 0 ~ 4.5      | 2 Byte   | 배터리 출력값을 Voltage로 변환한 값 |


<br>
<br>


<a name="MotorBlock"></a>
## MotorBlock

모터 블럭

특정 방향으로 정회전을 할 경우 reverse에 항상 0을 넣어야 합니다.

반대로 역회전을 할 경우 forward에 항상 0을 넣어야 합니다.

```py
class MotorBlock(ISerializable):

    def __init__(self):
        self.forward    = 0
        self.reverse    = 0
```

| 변수 이름  | 형식        | 범위      | 크기     | 설명                     |
|:----------:|:-----------:|:---------:|:--------:|:-------------------------|
| forward    | UInt16      | 0 ~ 4096  | 2 Byte   | 모터 정방향 회전 입력 값 |
| reverse    | UInt16      | 0 ~ 4096  | 2 Byte   | 모터 역방향 회전 입력 값 |


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

| 변수 이름  | 형식                        | 범위  | 크기     | 설명           |
|:----------:|:---------------------------:|:-----:|:--------:|:---------------|
| motor[0]   | [MotorBlock](#MotorBlock)   | -     | 4 Byte   | 왼쪽 앞 모터   |
| motor[1]   | [MotorBlock](#MotorBlock)   | -     | 4 Byte   | 오른쪽 앞 모터 |
| motor[2]   | [MotorBlock](#MotorBlock)   | -     | 4 Byte   | 오른쪽 뒤 모터 |
| motor[3]   | [MotorBlock](#MotorBlock)   | -     | 4 Byte   | 왼쪽 뒤 모터   |


<br>
<br>


<a name="Range"></a>
## Range

거리 센서

추가 센서 모듈을 장착하지 않으면 bottom 값만 출력됩니다.

거리 센서의 측정 가능 범위는 40mm ~ 2000mm 입니다.

```py
class Range(ISerializable):

    def __init__(self):
        self.left       = 0
        self.front      = 0
        self.right      = 0
        self.rear       = 0
        self.top        = 0
        self.bottom     = 0
```

| 변수 이름 | 형식       | 범위    | 크기     | 설명      |
|:---------:|:----------:|:-------:|:--------:|:----------|
| left      | UInt16     | -       | 2 Byte   | 좌측(mm)  |
| front     | UInt16     | -       | 2 Byte   | 정면(mm)  |
| right     | UInt16     | -       | 2 Byte   | 우측(mm)  |
| rear      | UInt16     | -       | 2 Byte   | 후면(mm)  |
| top       | UInt16     | -       | 2 Byte   | 위(mm)    |
| bottom    | UInt16     | -       | 2 Byte   | 아래(mm)  |


<br>
<br>


<a name="UpdateInformation"></a>
## UpdateInformation

펌웨어 정보

현재 펌웨어의 정보와 업데이트 진행 상황 등을 포함하고 있습니다.

```py
class UpdateInformation(ISerializable):

    def __init__(self):
        self.modeUpdate     = ModeUpdate.None_

        self.deviceType     = DeviceType.None_
        self.imageType      = ImageType.None_
        self.version        = 0

        self.year           = 0
        self.month          = 0
        self.day            = 0
```

| 변수 이름     | 형식                                  | 범위 | 크기     | 설명                |
|:-------------:|:-------------------------------------:|:----:|:--------:|:--------------------|
| modeUpdate    | [ModeUpdate](02_system.md#ModeUpdate) | -    | 1 Byte   | 업데이트 진행 상황  |
| deviceType    | [DeviceType](02_system.md#System_DeviceType) | -    | 4 Byte   | 장치 타입           |
| imageType     | [ImageType](02_system.md#System_ImageType)   | -    | 1 Byte   | 이미지 타입         |
| version       | UInt16                                | -    | 2 Byte   | 펌웨어의 버젼       |
| year          | UInt8                                 | -    | 1 Byte   | 펌웨어 빌드 년      |
| month         | UInt8                                 | -    | 1 Byte   | 펌웨어 빌드 월      |
| day           | UInt8                                 | -    | 1 Byte   | 펌웨어 빌드 일      |


<br>
<br>


<a name="LinkRssi"></a>
## LinkRssi

RSSI

Received signal strength indication

[http://www.metageek.com/training/resources/understanding-rssi.html](http://www.metageek.com/training/resources/understanding-rssi.html)

Link 모듈과 연결된 장치의 신호 세기를 반환합니다.

```py
class LinkRssi(ISerializable):

    def __init__(self):
        self.rssi       = 0
```

| 변수 이름    | 형식     | 범위      | 크기     | 설명       |
|:------------:|:--------:|:---------:|:--------:|:-----------|
| rssi         | Int8     | -100 ~ 0  | 1 Byte   | 신호 세기  |


<br>
<br>


<a name="Message"></a>
## Message

요청

문자열 데이터를 전송할 때 사용합니다.

```py
class Message():

    def __init__(self):
        self.message    = ""
```

| 변수 이름    | 형식            | 범위  | 크기               | 설명     |
|:------------:|:---------------:|:-----:|:------------------:|:---------|
| message      | ASCII String    | -     | 장치에 따라 다름   | 메세지   |


<br>

---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. **Protocol**
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)
 6. [Examples - Imu](examples_02_imu.md)
 
<br>

[Index](index.md)
