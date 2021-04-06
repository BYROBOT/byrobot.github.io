**[*petrone_v2* for python](index.md)** / **Protocol**

Modified : 2018.8.2

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
    
    None_                       = 0x00
    
    Ping                        = 0x01      # 통신 확인
    Ack                         = 0x02      # 데이터 수신에 대한 응답
    Error                       = 0x03      # 오류
    Request                     = 0x04      # 지정한 타입의 데이터 요청
    Message                     = 0x05      # 문자열 데이터
    Reserved_1                  = 0x06      # 예약
    SystemInformation           = 0x07      # 시스템 정보
    Monitor                     = 0x08      # 디버깅용 값 배열 전송.
    SystemCounter               = 0x09      # 시스템 카운터
    Information                 = 0x0A      # 장치 정보
    UpdateLocation              = 0x0B      # 펌웨어 업데이트 위치 정정
    Update                      = 0x0C      # 펌웨어 업데이트
    Encrypt                     = 0x0D      # 펌웨어 암호화
    Address                     = 0x0E      # 장치 주소
    Administrator               = 0x0F      # 관리자 권한 획득
    Control                     = 0x10      # 조종 명령

    Command                     = 0x11      # 명령

    # Light
    LightManual                 = 0x20      # LED 수동 제어

    LightMode                   = 0x21      # LED 모드 지정
    LightModeCommand            = 0x22      # LED 모드 커맨드
    LightModeCommandIr          = 0x23      # LED 모드 커맨드 IR 데이터 송신
    LightModeColor              = 0x24      # LED 모드 3색 직접 지정
    LightModeColorCommand       = 0x25      # LED 모드 3색 직접 지정 커맨드
    LightModeColorCommandIr     = 0x26      # LED 모드 3색 직접 지정 커맨드 IR 데이터 송신
    LightModeColors             = 0x27      # LED 모드 팔레트의 색상으로 지정
    LightModeColorsCommand      = 0x28      # LED 모드 팔레트의 색상으로 지정 커맨드
    LightModeColorsCommandIr    = 0x29      # LED 모드 팔레트의 색상으로 지정 커맨드 IR 데이터 송신

    LightEvent                  = 0x2A      # LED 이벤트
    LightEventCommand           = 0x2B      # LED 이벤트 커맨드
    LightEventCommandIr         = 0x2C      # LED 이벤트 커맨드 IR 데이터 송신
    LightEventColor             = 0x2D      # LED 이벤트 3색 직접 지정
    LightEventColorCommand      = 0x2E      # LED 이벤트 3색 직접 지정 커맨드
    LightEventColorCommandIr    = 0x2F      # LED 이벤트 3색 직접 지정 커맨드 IR 데이터 송신
    LightEventColors            = 0x30      # LED 이벤트 팔레트의 색상으로 지정
    LightEventColorsCommand     = 0x31      # LED 이벤트 팔레트의 색상으로 지정 커맨드
    LightEventColorsCommandIr   = 0x32      # LED 이벤트 팔레트의 색상으로 지정 커맨드 IR 데이터 송신

    LightModeDefaultColor       = 0x33      # LED 초기 모드 3색 직접 지정

    # 상태 설정
    State                       = 0x40      # 드론의 상태(비행 모드 방위기준 배터리량)
    Attitude                    = 0x41      # 드론의 자세(Angle)
    AccelBias                   = 0x42      # 엑셀 바이어스 값
    GyroBias                    = 0x43      # 자이로 바이어스 값
    TrimAll                     = 0x44      # 전체 트림
    TrimFlight                  = 0x45      # 비행 트림
    TrimDrive                   = 0x46      # 주행 트림

    # Sensor raw data
    Imu                         = 0x50      # IMU Raw
    Pressure                    = 0x51      # 압력 센서 데이터
    Battery                     = 0x52      # 배터리
    Range                       = 0x53      # 적외선 거리 센서
    ImageFlow                   = 0x54      # ImageFlow
    CameraImage                 = 0x55      # CameraImage

    # Input
    Button                      = 0x70      # 버튼 입력
    Joystick                    = 0x71      # 조이스틱 입력

    # Devices
    Motor                       = 0x80      # 모터 제어 및 현재 제어값 확인
    MotorSingle                 = 0x81      # 한 개의 모터 제어
    IrMessage                   = 0x82      # IR 데이터 송수신
    Buzzer                      = 0x83      # 부저 제어
    Vibrator                    = 0x84      # 진동 제어

    # 카운트
    CountFlight                 = 0x90      # 비행 관련 카운트
    CountDrive                  = 0x91      # 주행 관련 카운트

    # RF
    Pairing                     = 0xA0      # 페어링
    Rssi                        = 0xA1      # RSSI

    # Display
    DisplayClear                = 0xB0      # 화면 지우기
    DisplayInvert               = 0xB1      # 화면 반전
    DisplayDrawPoint            = 0xB2      # 점 그리기
    DisplayDrawLine             = 0xB3      # 선 그리기
    DisplayDrawRect             = 0xB4      # 사각형 그리기
    DisplayDrawCircle           = 0xB5      # 원 그리기
    DisplayDrawString           = 0xB6      # 문자열 쓰기
    DisplayDrawStringAlign      = 0xB7      # 문자열 쓰기

    EndOfType                   = 0xB8
```


<br>
<br>


<a name="CommandType"></a>
## CommandType

명령 타입

단일 명령 또는 추가 옵션을 보내는 것으로 실행할 수 있는 기능들을 담고 있습니다.

```py
class CommandType(Enum):
    
    None_               = 0x00      # 없음

    # 설정
    ModeVehicle         = 0x10      # Vehicle 동작 모드 전환

    # 제어
    Headless            = 0x20      # 헤드리스 모드 선택
    Trim                = 0x21      # 트림 변경
    FlightEvent         = 0x22      # 비행 이벤트 실행
    DriveEvent          = 0x23      # 주행 이벤트 실행
    Stop                = 0x24      # 정지

    ClearTrim           = 0x50      # 트림 초기화
    ClearGyroBias       = 0x51      # 자이로 바이어스 리셋(트림도 같이 초기화 됨)

    DataStorageWrite    = 0x80      # 변경사항이 있는 경우 데이터 저장소에 기록

    # 관리자
    ClearCounter        = 0xA0      # 카운터 클리어(관리자 권한을 획득했을 경우에만 동작)
    SetTestComplete     = 0xA1      # 테스트 완료 처리

    EndOfType           = 0xA2
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

| 변수 이름     | 형식                                    | 범위    | 크기     | 설명                       |
|:-------------:|:---------------------------------------:|:-------:|:--------:|:---------------------------|
| dataType      | [DataType](#DataType)                   | -       | 1 Byte   | 데이터의 타입              |
| length        | UInt8                                   | 0 ~ 255 | 1 Byte   | 데이터의 길이              |
| from_         | [DeviceType](02_system.md#DeviceType)   | -       | 1 Byte   | 데이터를 전송하는 장치     |
| to_           | [DeviceType](02_system.md#DeviceType)   | -       | 1 Byte   | 데이터를 수신하는 장치     |


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

| 변수 이름    | 형식            | 범위   | 크기     | 설명              |
|:------------:|:---------------:|:------:|:--------:|:------------------|
| systemTime   | UInt64          | -      | 8 Byte   | 시스템 시간       |

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

| 변수 이름      | 형식                    | 범위  | 크기     | 설명                                     |
|:--------------:|:-----------------------:|:-----:|:--------:|:-----------------------------------------|
| systemTime     | UInt64                  | -     | 8 Byte   | 시스템 시간                              |
| dataType       | [DataType](#DataType)   | -     | 1 Byte   | 수신 받은 데이터 타입                    |
| crc16          | UInt16                  | -     | 2 Byte   | 수신 받은 헤더와 데이터의 CRC16 값       |

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

| 변수 이름            | 형식                                                     | 범위  | 크기     | 설명                  |
|:--------------------:|:--------------------------------------------------------:|:-----:|:--------:|:----------------------|
| systemTime           | UInt64                                                   | -     | 8 Byte   | 시스템 시간           |
| errorFlagsForSensor  | [ErrorFlagsForSensor](02_system.md#ErrorFlagsForSensor)  | -     | 4 Byte   | 센서 오류 플래그 조합 |
| errorFlagsForState   | [ErrorFlagsForState](02_system.md#ErrorFlagsForState)    | -     | 4 Byte   | 상태 오류 플래그 조합 |

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

| 변수 이름     | 형식                        | 범위  | 크기     | 설명                  |
|:-------------:|:---------------------------:|:-----:|:--------:|:----------------------|
| dataType      | [DataType](#DataType)       | -     | 1 Byte   | 요청할 데이터 타입    |


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
<br>


<a name="Version"></a>
## Version

버전

펌웨의 버전

```py
class Version(ISerializable):

    def __init__(self):
        self.build          = 0
        self.stage          = DevelopmentStage.Alpha
        self.minor          = 0
        self.major          = 0

        self.v              = 0         # build, stage, minor, major을 하나의 UInt32로 묶은 것(버전 비교 시 사용)
```

| 변수 이름  | 형식                                              | 범위       | 크기     | 설명         |
|:----------:|:-------------------------------------------------:|:----------:|:--------:|:-------------|
| build      | UInt16                                            | 0 ~ 16383  | 14 bit   | 빌드 번호    |
| stage      | [DevelopmentStage](02_system.md#DevelopmentStage) | -          | 2 bit    | 개발 단계    |
| minor      | UInt8                                             | 0 ~ 255    | 1 Byte   | 부 번호      |
| major      | UInt8                                             | 0 ~ 255    | 1 Byte   | 주 번호      |
| v          | UInt32                                            | -          | 4 Byte   | build, stage, minor, major를 하나로 묶은 것  |


<br>
<br>


<a name="SystemInformation"></a>
## SystemInformation

시스템 정보

드론과 조종기 간 장치 정보를 교환하는데 사용합니다. 추후에 계속 변경될 가능성이 있습니다.

```py
class SystemInformation(ISerializable):

    def __init__(self):
        self.crc32bootloader    = 0
        self.crc32application   = 0
```

| 변수 이름         | 형식       | 범위  | 크기    | 설명                         |
|:-----------------:|:----------:|:-----:|:-------:|:-----------------------------|
| crc32bootloader   | UInt32     | -     | 4 Byte  | Bootloader 영역의 CRC32      |
| crc32application  | UInt32     | -     | 4 Byte  | Application 영역의 CRC32     |


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

        self.deviceType     = DeviceType.None_
        self.version        = Version()

        self.year           = 0
        self.month          = 0
        self.day            = 0
```

| 변수 이름     | 형식                                  | 범위 | 크기     | 설명                |
|:-------------:|:-------------------------------------:|:----:|:--------:|:--------------------|
| modeUpdate    | [ModeUpdate](02_system.md#ModeUpdate) | -    | 1 Byte   | 업데이트 진행 상황  |
| deviceType    | [DeviceType](02_system.md#DeviceType) | -    | 1 Byte   | 장치의 타입         |
| version       | [Version](#Version)                   | -    | 4 Byte   | 펌웨어의 버전       |
| year          | UInt16                                | -    | 2 Byte   | 펌웨어 빌드 년      |
| month         | UInt8                                 | -    | 1 Byte   | 펌웨어 빌드 월      |
| day           | UInt8                                 | -    | 1 Byte   | 펌웨어 빌드 일      |

- e.g. [조종기의 펌웨어 정보 요청(이벤트 함수 등록)](examples_12_information.md#Class_Information)


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
| address    | UInt8 Array   | -     | 16 Byte  | 장치 주소    |


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


<a name="Pairing"></a>
## Pairing

페어링

장치의 페어링 정보를 확인하거나 변경할 때 사용합니다.

주소에 0x0000은 사용하지 않음, 0xFFFF는 Broadcasting.

```py
class Pairing(ISerializable):

    def __init__(self):
        self.addressLocal   = 0
        self.addressRemote  = 0
        self.channel        = 0
```

| 변수 이름       | 형식      | 범위       | 크기     | 설명               |
|:---------------:|:---------:|:----------:|:--------:|:-------------------|
| addressLocal    | UInt16    | 1 ~ 65534  | 2 Byte   | 장치의 주소        |
| addressRemote   | UInt16    | 1 ~ 65534  | 2 Byte   | 상대 장치의 주소   |
| channel         | UInt8     | 0 ~ 230    | 1 Byte   | 채널               |


<br>
<br>


<a name="Rssi"></a>
## Rssi

RSSI

Received signal strength indication

[http://www.metageek.com/training/resources/understanding-rssi.html](http://www.metageek.com/training/resources/understanding-rssi.html)

현재 무선으로 연결된 장치의 신호 세기를 반환합니다.

```py
class Rssi(ISerializable):

    def __init__(self):
        self.rssi       = 0
```

| 변수 이름    | 형식     | 범위      | 크기     | 설명       |
|:------------:|:--------:|:---------:|:--------:|:-----------|
| rssi         | Int8     | -100 ~ 0  | 1 Byte   | 신호 세기  |


<br>
<br>


<a name="ControlQuad8"></a>
## ControlQuad8

비행 조종

비행 및 주행에 모두 사용할 수 있습니다.

```py
class ControlQuad8(ISerializable):

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


<a name="ControlDouble8"></a>
## ControlDouble8

자동차 조종

드론이 자동차 모드로 동작할 때 사용할 수 있습니다.

```py
class ControlDouble8(ISerializable):

    def __init__(self):
        self.wheel      = 0
        self.accel      = 0
```

| 변수 이름  | 형식   | 범위       | 크기     | 설명         |
|:----------:|:------:|:----------:|:--------:|:-------------|
| wheel      | Int8   | -100 ~ 100 | 1 Byte   | 좌우 회전    |
| accel      | Int8   | -100 ~ 100 | 1 Byte   | 전후진 속도  |


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

- e.g. [드론 TrimFlight 설정 변경 후 확인](examples_07_setup.md#TrimFlight)


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
        self.accel      = 0
```

| 변수 이름 | 형식     | 범위           | 크기     | 설명    |
|:---------:|:--------:|:--------------:|:--------:|:--------|
| wheel     | Int16    | -200 ~ 200     | 2 Byte   | Wheel   |
| accel     | Int16    | -200 ~ 200     | 2 Byte   | Accel   |

- e.g. [드론 TrimDrive 설정 변경 후 확인](examples_07_setup.md#TrimDrive)


<br>
<br>


<a name="LightModeDrone"></a>
## LightModeDrone

드론 LED 동작 모드

```py
class LightModeDrone(Enum):
    
    None_               = 0x00

    EyeNone             = 0x10
    EyeManual           = 0x11      # 수동 제어
    EyeHold             = 0x12      # 지정한 색상을 계속 켬
    EyeFlicker          = 0x13      # 깜빡임    	
    EyeFlickerDouble    = 0x14      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)    	
    EyeDimming          = 0x15      # 밝기 제어하여 천천히 깜빡임

    ArmNone             = 0x40
    ArmManual           = 0x41      # 수동 제어
    ArmHold             = 0x42      # 지정한 색상을 계속 켬
    ArmFlicker          = 0x43      # 깜빡임    	
    ArmFlickerDouble    = 0x44      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)    	
    ArmDimming          = 0x45      # 밝기 제어하여 천천히 깜빡임

    TailNone            = 0x70
    TailManual          = 0x71      # 수동 제어
    TailHold            = 0x72      # 지정한 색상을 계속 켬
    TailFlicker         = 0x73      # 깜빡임    	
    TailFlickerDouble   = 0x74      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)    	
    TailDimming         = 0x75      # 밝기 제어하여 천천히 깜빡임

    EndOfType           = 0x76
```


<br>
<br>


<a name="LightFlagsDrone"></a>
## LightFlagsDrone

드론 LED 플래그

```py
class LightFlagsDrone(Enum):
    
    None_               = 0x00

    EyeRed              = 0x80
    EyeGreen            = 0x40
    EyeBlue             = 0x20

    ArmRed              = 0x10
    ArmGreen            = 0x08
    ArmBlue             = 0x04

    TailGreen           = 0x02
```


<br>
<br>


<a name="LightModeController"></a>
## LightModeController

조종기 LED 동작 모드

```py
class LightModeController(Enum):
    
    None_               = 0x00

    TeamNone            = 0x10
    TeamManual          = 0x11      # 수동 조작
    TeamHold            = 0x12      
    TeamFlicker         = 0x13      
    TeamFlickerDouble   = 0x14      
    TeamDimming         = 0x15      

    EndOfType           = 0x16      
```


<br>
<br>


<a name="LightFlagsController"></a>
## LightFlagsController

조종기 LED 플래그

```py
class LightFlagsController(Enum):
    
    None_               = 0x00

    Red                 = 0x80
    Green               = 0x40
    Blue                = 0x20
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

| 변수 이름   | 형식   | 범위                      | 크기     | 설명            |
|:-----------:|:------:|:-------------------------:|:--------:|:----------------|
| flags       | UInt8  | 0b00000000 ~ 0b11111111   | 1 Byte   | LED 선택 플래그 |
| brightness  | UInt8  | 0 ~ 255                   | 1 Byte   | 밝기            |


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

| 변수 이름   | 형식      | 범위       | 크기     | 설명                           |
|:-----------:|:---------:|:----------:|:--------:|:-------------------------------|
| mode        | UInt8     | -          | 1 Byte   | LED 동작 모드                  |
| interval    | UInt16    | 0 ~ 65535  | 2 Byte   | 내부 밝기 제어 함수 호출 주기  |


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

| 변수 이름   | 형식                     | 범위   | 크기     | 설명           |
|:-----------:|:------------------------:|:------:|:--------:|:---------------|
| mode        | [LightMode](#LightMode)  | -      | 3 Byte   | LED 동작 모드  |
| color       | [Color](#Color)          | -      | 3 Byte   | LED RGB 색상   |

- e.g. [조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColor / 클래스 데이터를 채워서 전송)](examples_10_light.md#Class_LightModeColor)


<br>
<br>


<a name="LightModeColorCommand"></a>
## LightModeColorCommand

LED 모드 변경(RGB) + Command

LightModeColor에 Command를 추가하여 전송합니다.

```py
class LightModeColorCommand(ISerializable):
    
    def __init__(self):
        self.mode       = LightMode()
        self.color      = Color()
        self.command    = Command()
```

| 변수 이름  | 형식                     | 범위 | 크기     | 설명           |
|:----------:|:------------------------:|:----:|:--------:|:---------------|
| mode       | [LightMode](#LightMode)  | -    | 3 Byte   | LED 동작 모드  |
| color      | [Color](#Color)          | -    | 3 Byte   | LED RGB 색상   |
| command    | [Command](#Command)      | -    | 2 Byte   | 명령           |



<br>
<br>


<a name="LightModeColorCommandIr"></a>
## LightModeColorCommandIr

LED 모드 변경(RGB) + Command + IR

LightModeColorCommand에 적외선 전송 데이터를 추가하여 전송합니다.

```py
class LightModeColorCommandIr(ISerializable):
    
    def __init__(self):
        self.mode       = LightMode()
        self.color      = Color()
        self.command    = Command()
        self.irData     = 0
```

| 변수 이름   | 형식                      | 범위                     | 크기     | 설명               |
|:-----------:|:-------------------------:|:------------------------:|:--------:|:-------------------|
| mode        | [LightMode](#LightMode)   | -                        | 3 Byte   | LED 동작 모드      |
| color       | [Color](#Color)           | -                        | 3 Byte   | LED RGB 색상       |
| command     | [Command](#Command)       | -                        | 2 Byte   | 명령               |
| irData      | UInt32                    | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 적외선 전송 데이터 |


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

| 변수 이름  | 형식                      | 범위  | 크기     | 설명               |
|:----------:|:-------------------------:|:-----:|:--------:|:-------------------|
| mode       | [LightMode](#LightMode)   | -     | 3 Byte   | LED 동작 모드      |
| colors     | [Colors](#Colors)         | -     | 1 Byte   | LED 팔레트 인덱스  |

- e.g. [조종기의 LED를 랜덤한 색으로 점점 밝아졌다 어두워지게 하는 명령을 10회 실행 (LightModeColors / 클래스 데이터를 채워서 전송)](examples_10_light.md#Class_LightModeColors)


<br>
<br>


<a name="LightModeColorsCommand"></a>
## LightModeColorsCommand

LED 모드 변경(Palette) + Command

LightModeColors에 Command를 추가하여 전송합니다.

```py
class LightModeColorsCommand(ISerializable):
    
    def __init__(self):
        self.mode       = LightMode()
        self.colors     = Colors.Black
        self.command    = Command()
```

| 변수 이름  | 형식                     | 범위  | 크기     | 설명                |
|:----------:|:------------------------:|:-----:|:--------:|:--------------------|
| mode       | [LightMode](#LightMode)  | -     | 3 Byte   | LED 동작 모드       |
| colors     | [Colors](#Colors)        | -     | 1 Byte   | LED 팔레트 인덱스   |
| command    | [Command](#Command)      | -     | 2 Byte   | 명령                |



<br>
<br>


<a name="LightModeColorCommandIr"></a>
## LightModeColorCommandIr

LED 모드 변경(Palette) + Command + IR

LightModeColorsCommand에 적외선 전송 데이터를 추가하여 전송합니다.

```py
class LightModeColorsCommandIr(ISerializable):
    
    def __init__(self):
        self.mode       = LightMode()
        self.colors     = Colors.Black
        self.command    = Command()
        self.irData     = 0
```

| 변수 이름  | 형식                      | 범위                     | 크기     | 설명                |
|:----------:|:-------------------------:|:------------------------:|:--------:|:--------------------|
| mode       | [LightMode](#LightMode)   | -                        | 3 Byte   | LED 동작 모드       |
| colors     | [Colors](#Colors)         | -                        | 1 Byte   | LED 팔레트 인덱스   |
| command    | [Command](#Command)       | -                        | 2 Byte   | 명령                |
| irData     | UInt32                    | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 적외선 전송 데이터  |


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

| 변수 이름  | 형식     | 범위       | 크기     | 설명                           |
|:----------:|:--------:|:----------:|:--------:|:-------------------------------|
| event      | UInt8    | -          | 1 Byte   | LED 동작 모드                  |
| interval   | UInt16   | 0 ~ 65535  | 2 Byte   | 내부 색상 변화 함수 호출 주기  |
| repeat     | UInt8    | 0 ~ 255    | 1 Byte   | 반복 횟수                      |


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

| 변수 이름   | 형식                        | 범위  | 크기     | 설명           |
|:-----------:|:---------------------------:|:-----:|:--------:|:---------------|
| event       | [LightEvent](#LightEvent)   | -     | 4 Byte   | LED 이벤트     |
| color       | [Color](#Color)             | -     | 3 Byte   | LED RGB 색상   |



<br>
<br>


<a name="LightEventColorCommand"></a>
## LightEventColorCommand

LED 이벤트 변경(RGB)

LightEventColor에 Command를 추가하여 전송합니다.

```py
class LightEventColorCommand(ISerializable):
    
    def __init__(self):
        self.event      = LightEvent()
        self.color      = Color()
        self.command    = Command()
```

| 변수 이름   | 형식                       | 범위 | 크기     | 설명          |
|:-----------:|:--------------------------:|:----:|:--------:|:--------------|
| event       | [LightEvent](#LightEvent)  | -    | 4 Byte   | LED 이벤트    |
| color       | [Color](#Color)            | -    | 3 Byte   | LED RGB 색상  |
| command     | [Command](#Command)        | -    | 2 Byte   | 명령          |



<br>
<br>


<a name="LightEventColorCommandIr"></a>
## LightEventColorCommandIr

LED 이벤트 변경(RGB)

LightEventColorCommand에 적외선 전송 데이터를 추가하여 전송합니다.

```py
class LightEventColorCommandIr(ISerializable):
    
    def __init__(self):
        self.event      = LightEvent()
        self.color      = Color()
        self.command    = Command()
        self.irData     = 0
```

| 변수 이름  | 형식                       | 범위                     | 크기     | 설명               |
|:----------:|:--------------------------:|:------------------------:|:--------:|:-------------------|
| event      | [LightEvent](#LightEvent)  | -                        | 4 Byte   | LED 이벤트         |
| color      | [Color](#Color)            | -                        | 3 Byte   | LED RGB 색상       |
| command    | [Command](#Command)        | -                        | 2 Byte   | 명령               |
| irData     | UInt32                     | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 적외선 전송 데이터 |


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

| 변수 이름 | 형식                       | 범위  | 크기     | 설명              |
|:---------:|:--------------------------:|:-----:|:--------:|:------------------|
| event     | [LightEvent](#LightEvent)  | -     | 4 Byte   | LED 이벤트        |
| colors    | [Colors](#Colors)          | -     | 1 Byte   | LED 팔레트 인덱스 |



<br>
<br>


<a name="LightEventColorsCommand"></a>
## LightEventColorsCommand

LED 이벤트 변경(Palette) + Command

LightEventColors에 Command를 추가하여 전송합니다.

```py
class LightEventColorsCommand(ISerializable):
    
    def __init__(self):
        self.event      = LightEvent()
        self.colors     = Colors.Black
        self.command    = Command()
```

| 변수 이름  | 형식                      | 범위 | 크기     | 설명               |
|:----------:|:-------------------------:|:----:|:--------:|:-------------------|
| event      | [LightEvent](#LightEvent) | -    | 4 Byte   | LED 이벤트         |
| colors     | [Colors](#Colors)         | -    | 1 Byte   | LED 팔레트 인덱스  |
| command    | [Command](#Command)       | -    | 2 Byte   | 명령               |



<br>
<br>


<a name="LightEventColorsCommandIr"></a>
## LightEventColorsCommandIr

LED 모드 변경(Palette) + Command + IR

LightEventColorsCommand에 적외선 전송 데이터를 추가하여 전송합니다.

```py
class LightEventColorsCommandIr(ISerializable):
    
    def __init__(self):
        self.event      = LightEvent()
        self.colors     = Colors.Black
        self.command    = Command()
        self.irData     = 0
```

| 변수 이름  | 형식                        | 범위                     | 크기     | 설명               |
|:----------:|:---------------------------:|:------------------------:|:--------:|:-------------------|
| event      | [LightEvent](#LightEvent)   | -                        | 4 Byte   | LED 이벤트         |
| colors     | [Colors](#Colors)           | -                        | 1 Byte   | LED 팔레트 인덱스  |
| command    | [Command](#Command)         | -                        | 2 Byte   | 명령               |
| irData     | UInt32                      | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 적외선 전송 데이터 |


<br>
<br>


<a name="DisplayPixel"></a>
## DisplayPixel

픽셀 색상

```py
class DisplayPixel(Enum):
    
    Black               = 0x00
    White               = 0x01
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

| 변수 이름   | 형식                           | 범위 | 크기     | 설명        |
|:-----------:|:------------------------------:|:----:|:--------:|:------------|
| pixel       | [DisplayPixel](#DisplayPixel)  | -    | 1 Byte   | 채울 색상   |


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

| 변수 이름  | 형식                            | 범위          | 크기     | 설명            |
|:----------:|:-------------------------------:|:-------------:|:--------:|:----------------|
| x          | Int16                           | -2000 ~ 2000  | 2 Byte   | X축 시작 위치   |
| y          | Int16                           | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치   |
| width      | Int16                           | -2000 ~ 2000  | 2 Byte   | 너비            |
| height     | Int16                           | -2000 ~ 2000  | 2 Byte   | 높이            |
| pixel      | [DisplayPixel](#DisplayPixel)   | -             | 1 Byte   | 채울 색상       |


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

| 변수 이름   | 형식    | 범위          | 크기     | 설명           |
|:-----------:|:-------:|:-------------:|:--------:|:---------------|
| x           | Int16   | -2000 ~ 2000  | 2 Byte   | X축 시작 위치  |
| y           | Int16   | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치  |
| width       | Int16   | -2000 ~ 2000  | 2 Byte   | 너비           |
| height      | Int16   | -2000 ~ 2000  | 2 Byte   | 높이           |


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

| 변수 이름  | 형식                           | 범위          | 크기     | 설명       |
|:----------:|:------------------------------:|:-------------:|:--------:|:-----------|
| x          | Int16                          | -2000 ~ 2000  | 2 Byte   | X축 위치   |
| y          | Int16                          | -2000 ~ 2000  | 2 Byte   | Y축 위치   |
| pixel      | [DisplayPixel](#DisplayPixel)  | -             | 1 Byte   | 점 색상    |


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

| 변수 이름  | 형식                           | 범위          | 크기     | 설명           |
|:----------:|:------------------------------:|:-------------:|:--------:|:---------------|
| x1         | Int16                          | -2000 ~ 2000  | 2 Byte   | X축 시작 위치  |
| y1         | Int16                          | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치  |
| x2         | Int16                          | -2000 ~ 2000  | 2 Byte   | X축 끝 위치    |
| y2         | Int16                          | -2000 ~ 2000  | 2 Byte   | Y축 끝 위치    |
| pixel      | [DisplayPixel](#DisplayPixel)  | -             | 1 Byte   | 선 색상        |
| line       | [DisplayLine](#DisplayLine)    | -             | 1 Byte   | 선 형태        |


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

| 변수 이름  | 형식                            | 범위          | 크기     | 설명                     |
|:----------:|:-------------------------------:|:-------------:|:--------:|:-------------------------|
| x          | Int16                           | -2000 ~ 2000  | 2 Byte   | X축 시작 위치            |
| y          | Int16                           | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치            |
| width      | Int16                           | -2000 ~ 2000  | 2 Byte   | 너비                     |
| height     | Int16                           | -2000 ~ 2000  | 2 Byte   | 높이                     |
| pixel      | [DisplayPixel](#DisplayPixel)   | -             | 1 Byte   | 색상                     |
| flagFill   | Bool                            | -             | 1 Byte   | True인 경우 내부를 채움  |
| line       | [DisplayLine](#DisplayLine)     | -             | 1 Byte   | 선 형태                  |


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

| 변수 이름 | 형식                           | 범위          | 크기     | 설명                    |
|:---------:|:------------------------------:|:-------------:|:--------:|:------------------------|
| x         | Int16                          | -2000 ~ 2000  | 2 Byte   | X축 중심점 위치         |
| y         | Int16                          | -2000 ~ 2000  | 2 Byte   | Y축 중심점 위치         |
| radius    | Int16                          | 1 ~ 2000      | 2 Byte   | 반지름                  |
| pixel     | [DisplayPixel](#DisplayPixel)  | -             | 1 Byte   | 색상                    |
| flagFill  | Bool                           | -             | 1 Byte   | True인 경우 내부를 채움 |


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

| 변수 이름  | 형식                            | 범위          | 크기          | 설명           |
|:----------:|:-------------------------------:|:-------------:|:-------------:|:---------------|
| x          | Int16                           | -2000 ~ 2000  | 2 Byte        | X축 위치       |
| y          | Int16                           | -2000 ~ 2000  | 2 Byte        | Y축 위치       |
| font       | [DisplayFont](#DisplayFont)     | -             | 1 Byte        | 폰트           |
| pixel      | [DisplayPixel](#DisplayPixel)   | -             | 1 Byte        | 색상           |
| message    | ASCII String                    | -             | 30 Byte 이하  | 표시할 문자열  |


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

| 변수 이름  | 형식                            | 범위          | 크기          | 설명           |
|:----------:|:-------------------------------:|:-------------:|:-------------:|:---------------|
| x_start    | Int16                           | -2000 ~ 2000  | 2 Byte        | X축 시작 위치  |
| x_end      | Int16                           | -2000 ~ 2000  | 2 Byte        | X축 끝 위치    |
| y          | Int16                           | -2000 ~ 2000  | 2 Byte        | Y축 위치       |
| align      | [DisplayAlign](#DisplayAlign)   | -             | 1 Byte        | 정렬           |
| font       | [DisplayFont](#DisplayFont)     | -             | 1 Byte        | 폰트           |
| pixel      | [DisplayPixel](#DisplayPixel)   | -             | 1 Byte        | 색상           |
| message    | ASCII String                    | -             | 30 Byte 이하  | 표시할 문자열  |


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

| 변수 이름  | 형식                      | 범위       | 크기   | 설명                   |
|:----------:|:-------------------------:|:----------:|:------:|:-----------------------|
| mode       | [BuzzerMode](#BuzzerMode) | -          | 1 Byte | 버저 동작 모드         |
| value      | UInt16                    | 0 ~ 8000   | 2 Byte | Scale 값 또는 Hz 값    |
| time       | UInt16                    | 0 ~ 65,535 | 2 Byte | 소리를 지속할 시간(ms) |

- e.g. [Buzzer 클래스 데이터를 직접 채워서 전송하기](examples_08_buzzer.md#Class_Buzzer)

<br>
<br>


<a name="VibratorMode"></a>
## VibratorMode

진동 모드

```py
class VibratorMode(Enum):

    Stop                = 0     # 정지

    Instantly         = 1     # 즉시 적용
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

| 변수 이름  | 형식                          | 범위        | 크기     | 설명                |
|:----------:|:-----------------------------:|:-----------:|:--------:|:--------------------|
| mode       | [VibratorMode](#VibratorMode) | -           | 1 Byte   | 진동 동작 모드      |
| on         | UInt16                        | 0 ~ 65,535  | 2 Byte   | 진동을 켠 시간(ms)  |
| off        | UInt16                        | 0 ~ 65,535  | 2 Byte   | 진동을 끈 시간(ms)  |
| total      | UInt16                        | 0 ~ 65,535  | 2 Byte   | 전체 동작 시간(ms)  |

- e.g. [Vibrator 클래스 데이터를 직접 채워서 전송하기](examples_09_vibrator.md#Class_Vibrator)


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

| 변수 이름  | 형식                                    | 범위          | 크기     | 설명           |
|:----------:|:---------------------------------------:|:-------------:|:--------:|:---------------|
| x          | Int8                                    | -100 ~ 100    | 1 Byte   | X축 값         |
| y          | Int8                                    | -100 ~ 100    | 1 Byte   | Y축 값         |
| direction  | [JoystickDirection](#JoystickDirection) | -             | 1 Byte   | 조이스틱 방향  |
| event      | [JoystickEvent](#JoystickEvent)         | -             | 1 Byte   | 이벤트         |


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

| 변수 이름 | 형식                             | 범위  | 크기     | 설명            |
|:---------:|:--------------------------------:|:-----:|:--------:|:----------------|
| left      | [JoystickBlock](#JoystickBlock)  | -     | 4 Byte   | 왼쪽 조이스틱   |
| right     | [JoystickBlock](#JoystickBlock)  | -     | 4 Byte   | 오른쪽 조이스틱 |

- e.g. [조이스틱 입력값 출력](examples_12_input.md#Joystick)


<br>
<br>


<a name="ButtonFlagController"></a>
## ButtonFlagController

조종기 버튼 플래그

```py
class ButtonFlagController(Enum):

    None_           = 0x0000
    
    FrontLeft       = 0x0001
    FrontRight      = 0x0002
    
    MidTurnLeft     = 0x0004
    MidTurnRight    = 0x0008
    
    MidUp           = 0x0010
    MidLeft         = 0x0020
    MidRight        = 0x0040
    MidDown         = 0x0080
    
    RearLeft        = 0x0100
    RearRight       = 0x0200
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

| 변수 이름 | 형식                        | 범위  | 크기     | 설명         |
|:---------:|:---------------------------:|:-----:|:--------:|:-------------|
| button    | UInt16                      | -     | 2 Byte   | 버튼 입력    |
| event     | [ButtonEvent](#ButtonEvent) | -     | 1 Byte   | 버튼 이벤트  |

- e.g. [버튼 입력값 출력](examples_12_input.md#Button)


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

- e.g. [드론 모드를 변경 후 확인](examples_07_setup.md#ModeVehicle)


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

| 변수 이름  | 형식    | 범위              | 크기     | 설명    |
|:----------:|:-------:|:-----------------:|:--------:|:--------|
| x          | Int16   | -32,768 ~ 32,767  | 2 Byte   | X       |
| y          | Int16   | -32,768 ~ 32,767  | 2 Byte   | Y       |
| z          | Int16   | -32,768 ~ 32,767  | 2 Byte   | Z       |


<br>
<br>


<a name="AccelBias"></a>
## AccelBias

가속도 바이어스

[Vector](#Vector)를 상속받습니다.

```py
class AccelBias(Vector):
    pass
```

| 변수 이름   | 형식    | 범위              | 크기     | 설명 |
|:-----------:|:-------:|:-----------------:|:--------:|:-----|
| x           | Int16   | -32,768 ~ 32,767  | 2 Byte   | X    |
| y           | Int16   | -32,768 ~ 32,767  | 2 Byte   | Y    |
| z           | Int16   | -32,768 ~ 32,767  | 2 Byte   | Z    |


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

- e.g. [자세 확인](examples_05_sensor.md#Attitude)


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
| direction   | [Direction](02_system.md#Direction)  | -                        | 1 Byte   | 적외선 데이터를 받은 센서의 위치  |
| irData      | UInt32                               | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | 데이터                            |

- e.g. [적외선 데이터 송수신 확인](examples_05_sensor.md#IrMessage)


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

- e.g. [IMU 센서 데이터 확인](examples_05_sensor.md#Imu)


<br>
<br>


<a name="Battery"></a>
## Battery

배터리

```py
class Battery(ISerializable):

    def __init__(self):
        self.gradient                   = 0
        self.yIntercept                 = 0
        self.adjustGradient             = 0
        self.adjustYIntercept           = 0
        self.flagBatteryCalibration     = False
        self.batteryRaw                 = 0
        self.batteryPercent             = 0
        self.voltage                    = 0
```

| 변수 이름               | 형식     | 범위         | 크기     | 설명                                |
|:-----------------------:|:--------:|:------------:|:--------:|:------------------------------------|
| gradient                | Float32  | -            | 4 Byte   | 기울기                              |
| yIntercept              | Float32  | -            | 4 Byte   | Y 절편                              |
| adjustGradient          | Float32  | -            | 4 Byte   | 기울기 조정값                       |
| adjustYIntercept        | Float32  | -            | 4 Byte   | Y 절편 조정값                       |
| flagBatteryCalibration  | Bool     | True / False | 1 Byte   | 배터리 캘리브레이션 완료 여부       |
| batteryRaw              | Int16    | 0 ~ 4095     | 2 Byte   | 배터리 ADC Raw 값                   |
| batteryPercent          | Float32  | 0 ~ 100.0    | 4 Byte   | 배터리 % 값                         |
| voltage                 | Float32  | 0 ~ 4.5      | 4 Byte   | 배터리 출력값을 Voltage로 변환한 값 |


<br>
<br>


<a name="Pressure"></a>
## Pressure

압력 센서

```py
class Pressure(ISerializable):

    def __init__(self):
        self.temperature    = 0
        self.pressure       = 0
```

| 변수 이름   | 형식     | 범위 | 크기     | 설명                            |
|:-----------:|:--------:|:----:|:--------:|:--------------------------------|
| temperature | Float32  | -    | 4 Byte   | 온도(℃)                        |
| pressure    | Float32  | -    | 4 Byte   | 압력을 해발고도로 변환한 값(m)  |

- e.g. [압력 센서 데이터 확인](examples_05_sensor.md#Pressure)


<br>
<br>


<a name="Range"></a>
## Range

거리 센서

추가 센서 모듈을 장착하지 않으면 bottom 값만 출력됩니다.

거리 센서의 최대 정상 측정 가능 범위는 0.04m ~ 2.0m 입니다.

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

| 변수 이름 | 형식       | 범위    | 크기     | 설명     |
|:---------:|:----------:|:-------:|:--------:|:---------|
| left      | Float32    | -       | 4 Byte   | 좌측(m)  |
| front     | Float32    | -       | 4 Byte   | 정면(m)  |
| right     | Float32    | -       | 4 Byte   | 우측(m)  |
| rear      | Float32    | -       | 4 Byte   | 후면(m)  |
| top       | Float32    | -       | 4 Byte   | 위(m)    |
| bottom    | Float32    | -       | 4 Byte   | 아래(m)  |

- e.g. [거리 센서 데이터 확인](examples_05_sensor.md#Range)


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
| positionX  | Float32   | -     | 4 Byte   | X축(m)  |
| positionY  | Float32   | -     | 4 Byte   | Y축(m)  |


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

| 변수 이름  | 형식                               | 범위      | 크기     | 설명           |
|:----------:|:----------------------------------:|:---------:|:--------:|:---------------|
| rotation   | [Rotation](02_system.md#Rotation)  | -         | 1 Byte   | 모터 회전 방향 |
| value      | UInt16                             | 0 ~ 4095  | 2 Byte   | 모터 회전 속도 |


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
| motor[0]   | [MotorBlock](#MotorBlock)   | -     | 3 Byte   | 왼쪽 앞 모터   |
| motor[1]   | [MotorBlock](#MotorBlock)   | -     | 3 Byte   | 오른쪽 앞 모터 |
| motor[2]   | [MotorBlock](#MotorBlock)   | -     | 3 Byte   | 오른쪽 뒤 모터 |
| motor[3]   | [MotorBlock](#MotorBlock)   | -     | 3 Byte   | 왼쪽 뒤 모터   |


<br>
<br>


<a name="MotorSingle"></a>
## MotorSingle

한 개의 모터 제어

```py
class MotorSingle(ISerializable):

    def __init__(self):
        self.target     = 0
        self.rotation   = Rotation.None_
        self.value      = 0
```

| 변수 이름  | 형식                               | 범위      | 크기     | 설명            |
|:----------:|:----------------------------------:|:---------:|:--------:|:----------------|
| target     | UInt8                              | 0 ~ 3     | 1 Byte   | 동작 대상 모터  |
| rotation   | [Rotation](02_system.md#Rotation)  | -         | 1 Byte   | 모터 회전 방향  |
| value      | UInt16                             | 0 ~ 4095  | 2 Byte   | 모터 회전 속도  |


<br>

---

<h3><i>petrone_v2</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. **Protocol**
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

<br>

[Index](index.md)
