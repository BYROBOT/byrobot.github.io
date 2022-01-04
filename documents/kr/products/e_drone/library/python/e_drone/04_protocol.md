**[*e_drone* for python](index.md)** / **Protocol**

Modified : 2021.12.29

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
    
    NONE                        = 0x00      # 없음
    
    PING                        = 0x01      # 통신 확인
    ACK                         = 0x02      # 데이터 수신에 대한 응답
    ERROR                       = 0x03      # 오류(reserve, 비트 플래그는 추후에 지정)
    REQUEST                     = 0x04      # 지정한 타입의 데이터 요청
    MESSAGE                     = 0x05      # 문자열 데이터
    ADDRESS                     = 0x06      # 장치 주소(MAC이 있는 경우 MAC) 혹은 고유번호(MAC이 없는 경우 UUID)
    INFORMATION                 = 0x07      # 펌웨어 및 장치 정보
    UPDATE                      = 0x08      # 펌웨어 업데이트
    UPDATE_LOCATION             = 0x09      # 펌웨어 업데이트 위치 정정
    ENCRYPT                     = 0x0A      # 펌웨어 암호화
    SYSTEM_COUNT                = 0x0B      # 시스템 카운트
    SYSTEM_INFORMATION          = 0x0C      # 시스템 정보
    REGISTRATION                = 0x0D      # 제품 등록
    ADMINISTRATOR               = 0x0E      # 관리자 권한 획득
    MONITOR                     = 0x0F      # 디버깅용 값 배열 전송. 첫번째 바이트에 타입, 두 번째 바이트에 페이지 지정(수신 받는 데이터의 저장 경로 구분)
    CONTROL                     = 0x10      # 조종

    COMMAND                     = 0x11      # 명령
    PAIRING                     = 0x12      # 페어링
    RSSI                        = 0x13      # RSSI
    TIME_SYNC                   = 0x14      # 시간 동기화
    TRANSMISSION_POWER          = 0x15      # 전송 출력
    CONFIGURATION               = 0x16      # 설정
    ECHO                        = 0x17      # 반향(정상적으로 송수신 되는 데이터 길이 확인용, 받은 데이터를 그대로 반환, RF로 송수신 가능한 데이터 길이를 확인할 목적으로 추가)

    BATTLE                      = 0x1F      # 전투

    # Light
    LIGHT_MANUAL                = 0x20      # LED 수동 제어
    LIGHT_MODE                  = 0x21      # LED 모드
    LIGHT_EVENT                 = 0x22      # LED 이벤트
    LIGHT_DEFAULT               = 0x23      # LED 초기 모드

    # 센서 RAW 데이터
    RAW_MOTION                  = 0x30      # Motion 센서 데이터 RAW 값
    RAW_FLOW                    = 0x31      # Flow 센서 데이터 RAW 값

    # 상태, 센서
    STATE                       = 0x40      # 드론의 상태(비행 모드 방위기준 배터리량)
    ATTITUDE                    = 0x41      # 드론의 자세(Angle)
    POSITION                    = 0x42      # 위치
    ALTITUDE                    = 0x43      # 높이, 고도
    MOTION                      = 0x44      # Motion 센서 데이터 처리한 값(IMU)
    RANGE                       = 0x45      # 거리센서 데이터
    FLOW                        = 0x46      # optical flow 센서 데이터

    # 설정
    COUNT                       = 0x50      # 카운트
    BIAS                        = 0x51      # 엑셀, 자이로 바이어스 값
    TRIM                        = 0x52      # 트림
    WEIGHT                      = 0x53      # 무게
    LOST_CONNECTION             = 0x54      # 연결이 끊긴 후 반응 시간 설정

    # Devices
    MOTOR                       = 0x60      # 모터 제어 및 현재 제어값 확인
    MOTOR_SINGLE                = 0x61      # 한 개의 모터 제어
    BUZZER                      = 0x62      # 부저 제어
    VIBRATOR                    = 0x63      # 진동 제어

    # Input
    BUTTON                      = 0x70      # 버튼 입력
    JOYSTICK                    = 0x71      # 조이스틱 입력

    # Display
    DISPLAY_CLEAR               = 0x80      # 화면 지우기
    DISPLAY_INVERT              = 0x81      # 화면 반전
    DISPLAY_DRAW_POINT          = 0x82      # 점 그리기
    DISPLAY_DRAW_LINE           = 0x83      # 선 그리기
    DISPLAY_DRAW_RECT           = 0x84      # 사각형 그리기
    DISPLAY_DRAW_CIRCLE         = 0x85      # 원 그리기
    DISPLAY_DRAW_STRING         = 0x86      # 문자열 쓰기
    DISPLAY_DRAW_STRING_ALIGN   = 0x87      # 문자열 쓰기
    DISPLAY_DRAW_Image          = 0x88      # 그림 그리기

    # Card
    CARD_CLASSIFY               = 0x90      # 카드 색상 분류 기준 설정
    CARD_RANGE                  = 0x91      # 카드 색 범위(RAW 데이터의 출력 범위)
    CARD_RAW                    = 0x92      # 카드 데이터 RAW 값(유선으로만 전송)
    CARD_COLOR                  = 0x93      # 카드 데이터
    CARD_LIST                   = 0x94      # 카드 리스트 데이터
    CARD_FUNCTION_LIST          = 0x95      # 카드 함수 리스트 데이터
    
    # Information Assembled
    INFORMATION_ASSEMBLED_FOR_CONTROLLER   = 0xA0      # 자주 갱신되는 데이터 모음
    INFORMATION_ASSEMBLED_FOR_ENTRY        = 0xA1      # 자주 갱신되는 데이터 모음
    INFORMATION_ASSEMBLED_FOR_BYBLOCKS     = 0xA2      # 자주 갱신되는 데이터 모음

    # Navigation
    NAVIGATION_TARGET            = 0xD0      # 네비게이션 목표점
    NAVIGATION_LOCATION          = 0xD1      # 네비게이션 드론 위치
    NAVIGATION_MONITOR           = 0xD2
    NAVIGATION_HEADING           = 0xD3
    NAVIGATION_COUNTER           = 0xD4
    NAVIGATION_SATELLITE         = 0xD5      # 위성 정보
    NAVIGATION_LOCATION_ADJUST   = 0xD6      # 드론 위치 조정

    NAVIGATION_TARGET_ECEF       = 0xD8      # 드론 타겟 위치(ECEF)
    NAVIGATION_LOCATION_ECEF     = 0xD9      # 드론 현재 위치(ECEF)

    GPS_RTK_NAVIGATION_STATE                 = 0xDA      # RTK RAW 데이터 전송
    GPS_RTK_EXTENDED_RAW_MEASUREMENT_DATA    = 0xDB      # RTK RAW 데이터 전송

    END_OF_TYPE                  = 0xDC
```


<br>
<br>


<a name="CommandType"></a>
## CommandType

명령 타입

단일 명령 또는 추가 옵션을 보내는 것으로 실행할 수 있는 기능들을 담고 있습니다.

```py
class CommandType(Enum):
    
    NONE                    = 0x00      # 없음

    STOP                    = 0x01      # 정지

    # 설정
    MODE_CONTROL_FLIGHT     = 0x02      # 비행 제어 모드 설정
    HEADLESS                = 0x03      # 헤드리스 모드 선택
    CONTROL_SPEED           = 0x04      # 제어 속도 설정

    CLEAR_BIAS              = 0x05      # 자이로 바이어스 리셋(트림도 같이 초기화 됨)
    CLEAR_TRIM              = 0x06      # 트림 초기화

    FLIGHT_EVENT            = 0x07      # 비행 이벤트 실행

    SET_DEFAULT             = 0x08      # 기본 설정으로 초기화
    BACKLIGHT               = 0x09      # 조종기 백라이트 설정
    MODE_CONTROLLER         = 0x0A      # 조종기 동작 모드(0x10:조종, 0x80:링크)
    LINK                    = 0x0B      # 링크 제어(0:Client Mode, 1:Server Mode, 2:Pairing Start)

    # 관리자
    CLEAR_COUNTER           = 0xA0      # 카운터 클리어(관리자 권한을 획득했을 경우에만 동작)

    # Navigation
    NAVIGATION_TARGET_CLEAR = 0xE0      # 네비게이션 목표점 초기화
    NAVIGATION_START        = 0xE1      # 네비게이션 시작(처음부터)
    NAVIGATION_PAUSE        = 0xE2      # 네비게이션 일시 정지
    NAVIGATION_RESTART      = 0xE3      # 네비게이션 다시 시작(일시 정지 후 다시 시작할 때 사용)
    NAVIGATION_STOP         = 0xE4      # 네비게이션 중단
    NAVIGATION_NEXT         = 0xE5      # 네비게이션 목표점을 다음으로 변경
    NAVIGATION_RETURN_HOME  = 0xE6      # 시작 위치로 귀환

    GPS_RTK_BASE            = 0xEA
    GPS_RTK_ROVER           = 0xEB

    END_OF_TYPE             = 0xEC
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
        self.data_type   = DataType.NONE
        self.length      = 0
        self.from_       = DeviceType.NONE
        self.to_         = DeviceType.NONE
```

| 변수 이름 |                 형식                  |  크기  |  범위   |          설명          |
| :-------: | :-----------------------------------: | :----: | :-----: | :--------------------- |
| data_type |         [DataType](#DataType)         | 1 Byte |    -    | 데이터의 타입          |
|  length   |                 UInt8                 | 1 Byte | 0 ~ 255 | 데이터의 길이          |
|   from_   | [DeviceType](03_system.md#DeviceType) | 1 Byte |    -    | 데이터를 전송하는 장치 |
|    to_    | [DeviceType](03_system.md#DeviceType) | 1 Byte |    -    | 데이터를 수신하는 장치 |


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
        self.system_time     = 0
```

|  변수 이름  |  형식  |  크기  | 범위  |    설명     |
| :---------: | :----: | :----: | :---: | :---------- |
| system_time | UInt64 | 8 Byte |   -   | 시스템 시간 |

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
        self.system_time    = 0
        self.data_type      = DataType.NONE
        self.crc16          = 0
```

|  변수 이름  |         형식          |  크기  | 범위  |                설명                |
| :---------: | :-------------------: | :----: | :---: | :--------------------------------- |
| system_time |        UInt64         | 8 Byte |   -   | 시스템 시간                        |
|  data_type  | [DataType](#DataType) | 1 Byte |   -   | 수신 받은 데이터 타입              |
|    crc16    |        UInt16         | 2 Byte |   -   | 수신 받은 헤더와 데이터의 CRC16 값 |

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
        self.system_time               = 0
        self.error_flags_for_sensor    = 0
        self.error_flags_for_state     = 0
```

|       변수 이름        |                          형식                           |  크기  | 범위  |         설명          |
| :--------------------: | :-----------------------------------------------------: | :----: | :---: | :-------------------- |
|      system_time       |                         UInt64                          | 8 Byte |   -   | 시스템 시간           |
| error_flags_for_sensor | [ErrorFlagsForSensor](03_system.md#ErrorFlagsForSensor) | 4 Byte |   -   | 센서 오류 플래그 조합 |
| error_flags_for_state  |  [ErrorFlagsForState](03_system.md#ErrorFlagsForState)  | 4 Byte |   -   | 상태 오류 플래그 조합 |

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
        self.data_type    = DataType.NONE
```

| 변수 이름 |         형식          |  크기  | 범위  |        설명        |
| :-------: | :-------------------: | :----: | :---: | :----------------- |
| data_type | [DataType](#DataType) | 1 Byte |   -   | 요청할 데이터 타입 |


<br>
<br>


<a name="Message"></a>
## Message

메세지

문자열 데이터를 전송할 때 사용합니다.

```py
class Message():

    def __init__(self):
        self.message    = ""
```

| 변수 이름 |     형식     |       크기       | 범위  |  설명  |
| :-------: | :----------: | :--------------: | :---: | :----- |
|  message  | ASCII String | 장치에 따라 다름 |   -   | 메세지 |


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
        self.minor          = 0
        self.major          = 0

        self.v              = 0         # build, minor, major을 하나의 UInt32로 묶은 것(버전 비교 시 사용)
```

| 변수 이름 |  형식  |  크기  |   범위    |                 설명                 |
| :-------: | :----: | :----: | :-------: | :----------------------------------- |
|   build   | UInt16 | 2 Byte | 0 ~ 65535 | 빌드 번호                            |
|   minor   | UInt8  | 1 Byte |  0 ~ 255  | 부 번호                              |
|   major   | UInt8  | 1 Byte |  0 ~ 255  | 주 번호                              |
|     v     | UInt32 | 4 Byte |     -     | build, minor, major를 하나로 묶은 것 |


<br>
<br>


<a name="SystemInformation"></a>
## SystemInformation

시스템 정보

드론과 조종기 간 장치 정보를 교환하는데 사용합니다. 추후에 계속 변경될 가능성이 있습니다.

```py
class SystemInformation(ISerializable):

    def __init__(self):
        self.crc32_bootloader    = 0
        self.crc32_application   = 0
```

|     변수 이름     |  형식  |  크기  | 범위  |           설명           |
| :---------------: | :----: | :----: | :---: | :----------------------- |
| crc32_bootloader  | UInt32 | 4 Byte |   -   | Bootloader 영역의 CRC32  |
| crc32_application | UInt32 | 4 Byte |   -   | Application 영역의 CRC32 |


<br>
<br>


<a name="Information"></a>
## Information

펌웨어 정보

현재 펌웨어의 정보와 업데이트 진행 상황 등을 포함하고 있습니다.

```py
class Information(ISerializable):

    def __init__(self):
        self.mode_update    = ModeUpdate.NONE

        self.model_number   = ModelNumber.NONE
        self.version        = Version()

        self.year           = 0
        self.month          = 0
        self.day            = 0
```

|  변수 이름   |                  형식                   |  크기  | 범위  |        설명        |
| :----------: | :-------------------------------------: | :----: | :---: | :----------------- |
| mode_update  |  [ModeUpdate](03_system.md#ModeUpdate)  | 1 Byte |   -   | 업데이트 진행 상황 |
| model_number | [ModelNumber](03_system.md#ModelNumber) | 4 Byte |   -   | 모델 번호          |
|   version    |           [Version](#Version)           | 4 Byte |   -   | 펌웨어의 버전      |
|     year     |                 UInt16                  | 2 Byte |   -   | 펌웨어 빌드 년     |
|    month     |                  UInt8                  | 1 Byte |   -   | 펌웨어 빌드 월     |
|     day      |                  UInt8                  | 1 Byte |   -   | 펌웨어 빌드 일     |

- e.g. [조종기의 펌웨어 정보 요청(이벤트 함수 등록)](examples_02_information.md#Class_Information)


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

| 변수 이름 |    형식     |  크기   | 범위  |   설명    |
| :-------: | :---------: | :-----: | :---: | :-------- |
|  address  | UInt8 Array | 16 Byte |   -   | 장치 주소 |


<br>
<br>


<a name="Pairing"></a>
## Pairing

페어링

장치의 페어링 정보를 확인하거나 변경할 때 사용합니다.

```py
class Pairing(ISerializable):

    def __init__(self):
        self.address_0      = 0
        self.address_1      = 0
        self.address_2      = 0

        self.scramble       = 0

        self.channel_0      = 0
        self.channel_1      = 0
        self.channel_2      = 0
        self.channel_3      = 0
```

| 변수 이름 |  형식  |  크기  |   범위    |     설명      |
| :-------: | :----: | :----: | :-------: | :------------ |
| address_0 | UInt16 | 2 Byte | 0 ~ 65535 | 장치의 주소 0 |
| address_1 | UInt16 | 2 Byte | 0 ~ 65535 | 장치의 주소 1 |
| address_2 | UInt16 | 2 Byte | 0 ~ 65535 | 장치의 주소 2 |
| scramble  | UInt16 | 1 Byte |  0 ~ 127  | 스크램블      |
| channel_0 | UInt8  | 1 Byte |  0 ~ 81   | 채널 0        |
| channel_1 | UInt8  | 1 Byte |  0 ~ 81   | 채널 1        |
| channel_2 | UInt8  | 1 Byte |  0 ~ 81   | 채널 2        |
| channel_3 | UInt8  | 1 Byte |  0 ~ 81   | 채널 3        |


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

| 변수 이름 | 형식  |   범위   |  크기  |   설명    |
| :-------: | :---: | :------: | :----: | :-------- |
|   rssi    | Int8  | -100 ~ 0 | 1 Byte | 신호 세기 |


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
        self.command_type   = CommandType.NONE
        self.option         = 0
```

|  변수 이름   |                        형식                         |  크기  | 범위  |   설명    |
| :----------: | :-------------------------------------------------: | :----: | :---: | :-------- |
| command_type |             [CommandType](#CommandType)             | 1 Byte |   -   | 명령 타입 |
|    option    | [ModeControlFlight](03_system.md#ModeControlFlight) | 1 Byte |   -   | 옵션      |
|              |       [FlightEvent](03_system.md#FlightEvent)       | 1 Byte |   -   |           |
|              |          [Headless](03_system.md#Headless)          | 1 Byte |   -   |           |
|              |                        UInt8                        | 1 Byte |   -   |           |


<br>
<br>


<a name="CommandLightEvent"></a>
## CommandLightEvent

명령 + LED 이벤트

드론 또는 조종기에 명령과 함께 LED 이벤트를 전달할 때 사용합니다.

```py
class CommandLightEvent(ISerializable):

    def __init__(self):
        self.command    = Command()
        self.event      = LightEvent()
```

| 변수 이름 |           형식            |  크기  | 범위  |    설명    |
| :-------: | :-----------------------: | :----: | :---: | :--------- |
|  command  |    [Command](#Command)    | 2 Byte |   -   | 명령       |
|   event   | [LightEvent](#LightEvent) | 4 Byte |   -   | LED 이벤트 |


<br>
<br>


<a name="CommandLightEventColor"></a>
## CommandLightEventColor

명령 + LED 이벤트(RGB)

드론 또는 조종기에 명령과 함께 LED 이벤트(RGB)를 전달할 때 사용합니다.

```py
class CommandLightEventColor(ISerializable):

    def __init__(self):
        self.command    = Command()
        self.event      = LightEvent()
        self.color      = Color()
```

| 변수 이름 |           형식            |  크기  | 범위  |     설명     |
| :-------: | :-----------------------: | :----: | :---: | :----------- |
|  command  |    [Command](#Command)    | 2 Byte |   -   | 명령         |
|   event   | [LightEvent](#LightEvent) | 4 Byte |   -   | LED 이벤트   |
|   color   |      [Color](#Color)      | 3 Byte |   -   | LED RGB 색상 |


<br>
<br>


<a name="CommandLightEventColors"></a>
## CommandLightEventColors

명령 + LED 이벤트(Palette)

드론 또는 조종기에 명령과 함께 LED 이벤트(Palette)를 전달할 때 사용합니다.

```py
class CommandLightEventColors(ISerializable):

    def __init__(self):
        self.command    = Command()
        self.event      = LightEvent()
        self.colors     = Colors.Black
```

| 변수 이름 |           형식            |  크기  | 범위  |       설명        |
| :-------: | :-----------------------: | :----: | :---: | :---------------- |
|  command  |    [Command](#Command)    | 2 Byte |   -   | 명령              |
|   event   | [LightEvent](#LightEvent) | 4 Byte |   -   | LED 이벤트        |
|  colors   |     [Colors](#Colors)     | 1 Byte |   -   | LED 팔레트 인덱스 |


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

| 변수 이름 | 형식  |  크기  |    범위    |   설명   |
| :-------: | :---: | :----: | :--------: | :------- |
|   roll    | Int8  | 1 Byte | -100 ~ 100 | Roll     |
|   pitch   | Int8  | 1 Byte | -100 ~ 100 | Pitch    |
|    yaw    | Int8  | 1 Byte | -100 ~ 100 | Yaw      |
| throttle  | Int8  | 1 Byte | -100 ~ 100 | Throttle |


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
        self.data_type  = DataType.NONE
```

| 변수 이름 |         형식          |  크기  |    범위    |        설명        |
| :-------: | :-------------------: | :----: | :--------: | :----------------- |
|   roll    |         Int8          | 1 Byte | -100 ~ 100 | Roll               |
|   pitch   |         Int8          | 1 Byte | -100 ~ 100 | Pitch              |
|    yaw    |         Int8          | 1 Byte | -100 ~ 100 | Yaw                |
| throttle  |         Int8          | 1 Byte | -100 ~ 100 | Throttle           |
| data_type | [DataType](#DataType) | 1 Byte |     -      | 요청할 데이터 타입 |


<br>
<br>


<a name="ControlPositionShort"></a>
## ControlPositionShort

드론 이동 명령

모든 변수에 2byte 정수를 사용하는 대신 position과 velocity의 값에 x10을 적용.

```py
class ControlPositionShort(ISerializable):

    def __init__(self):
        self.position_x          = 0
        self.position_y          = 0
        self.position_z          = 0

        self.velocity            = 0
        
        self.heading             = 0
        self.rotational_velocity = 0
```

|      변수 이름      | 형식  |  크기  |           범위           |    단위    |         설명         |
| :-----------------: | :---: | :----: | :----------------------: | :--------- | :------------------- |
|     position_x      | Int16 | 2 Byte | -100 ~ 100(-10.0 ~ 10.0) | meter x 10 | 앞(+), 뒤(-)         |
|     position_y      | Int16 | 2 Byte | -100 ~ 100(-10.0 ~ 10.0) | meter x 10 | 좌(+), 우(-)         |
|     position_z      | Int16 | 2 Byte | -100 ~ 100(-10.0 ~ 10.0) | meter x 10 | 위(+), 아래(-)       |
|      velocity       | Int16 | 2 Byte |    5 ~ 20(0.5 ~ 2.0)     | m/s x 10   | 위치 이동 속도       |
|       heading       | Int16 | 2 Byte |        -360 ~ 360        | degree     | 좌회전(+), 우회전(-) |
| rotational_velocity | Int16 | 2 Byte |         10 ~ 360         | degree/s   | 좌우 회전 속도       |


<br>
<br>


<a name="ControlPosition"></a>
## ControlPosition

드론 이동 명령

position과 velocity는 실수 값, heading과 rotationalVelocity에는 정수 값 사용

```py
class ControlPosition(ISerializable):

    def __init__(self):
        self.position_x             = 0
        self.position_y             = 0
        self.position_z             = 0

        self.velocity               = 0

        self.heading                = 0
        self.rotational_velocity    = 0
```

|      변수 이름      | 형식  |  크기  |     범위     |   단위   |         설명         |
| :-----------------: | :---: | :----: | :----------: | :------- | :------------------- |
|     position_x      | float | 4 Byte | -10.0 ~ 10.0 | meter    | 앞(+), 뒤(-)         |
|     position_y      | float | 4 Byte | -10.0 ~ 10.0 | meter    | 좌(+), 우(-)         |
|     position_z      | float | 4 Byte | -10.0 ~ 10.0 | meter    | 위(+), 아래(-)       |
|      velocity       | float | 4 Byte |  0.5 ~ 2.0   | m/s      | 위치 이동 속도       |
|       heading       | Int16 | 2 Byte |  -360 ~ 360  | degree   | 좌회전(+), 우회전(-) |
| rotational_velocity | Int16 | 2 Byte |   10 ~ 360   | degree/s | 좌우 회전 속도       |


<br>
<br>


<a name="LightModeDrone"></a>
## LightModeDrone

드론 LED 동작 모드

```py
class LightModeDrone(Enum):
    
    NONE                    = 0x00

    REAR_NONE               = 0x10
    REAR_MANUAL             = 0x11      # 수동 제어
    REAR_HOLD               = 0x12      # 지정한 색상을 계속 켬
    REAR_FLICKER            = 0x13      # 깜빡임
    REAR_FLICKER_DOUBLE     = 0x14      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    REAR_DIMMING            = 0x15      # 밝기 제어하여 천천히 깜빡임
    REAR_SUNRISE            = 0x16
    REAR_SUNSET             = 0x17

    BODY_NONE               = 0x20
    BODY_MANUAL             = 0x21      # 수동 제어
    BODY_HOLD               = 0x22      # 지정한 색상을 계속 켬
    BODY_FLICKER            = 0x23      # 깜빡임
    BODY_FLICKER_DOUBLE     = 0x24      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    BODY_DIMMING            = 0x25      # 밝기 제어하여 천천히 깜빡임
    BODY_SUNRISE            = 0x26
    BODY_SUNSET             = 0x27
    BODY_RAINBOW            = 0x28
    BODY_RAINBOW2           = 0x29

    A_NONE                  = 0x30
    A_MANUAL                = 0x31      # 수동 제어
    A_HOLD                  = 0x32      # 지정한 색상을 계속 켬
    A_FLICKER               = 0x33      # 깜빡임
    A_FLICKER_DOUBLE        = 0x34      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    A_DIMMING               = 0x35      # 밝기 제어하여 천천히 깜빡임
    A_SUNRISE               = 0x36
    A_SUNSET                = 0x37

    B_NONE                  = 0x40
    B_MANUAL                = 0x41      # 수동 제어
    B_HOLD                  = 0x42      # 지정한 색상을 계속 켬
    B_FLICKER               = 0x43      # 깜빡임
    B_FLICKER_DOUBLE        = 0x44      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    B_DIMMING               = 0x45      # 밝기 제어하여 천천히 깜빡임
    B_SUNRISE               = 0x46
    B_SUNSET                = 0x47

    END_OF_TYPE             = 0x60
```


<br>
<br>


<a name="LightFlagsDrone"></a>
## LightFlagsDrone

드론 LED 플래그

```py
class LightFlagsDrone(Enum):
    
    NONE                = 0x0000

    REAR                = 0x0001

    BODY_RED            = 0x0002
    BODY_GREEN          = 0x0004
    BODY_BLUE           = 0x0008

    A                   = 0x0010
    B                   = 0x0020
```


<br>
<br>


<a name="LightModeController"></a>
## LightModeController

조종기 LED 동작 모드

```py
class LightModeController(Enum):
    
    NONE                    = 0x00

    BODY_NONE               = 0x20
    BODY_MANUAL             = 0x21      # 수동 제어
    BODY_HOLD               = 0x22      # 지정한 색상을 계속 켬
    BODY_FLICKER            = 0x23      # 깜빡임
    BODY_FLICKER_DOUBLE     = 0x24      # 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
    BODY_DIMMING            = 0x25      # 밝기 제어하여 천천히 깜빡임
    BODY_SUNRISE            = 0x26
    BODY_SUNSET             = 0x27
    BODY_RAINBOW            = 0x28
    BODY_RAINBOW2           = 0x29

    END_OF_TYPE             = 0x30
```


<br>
<br>


<a name="LightFlagsController"></a>
## LightFlagsController

조종기 LED 플래그

```py
class LightFlagsController(Enum):
    
    NONE                = 0x00

    BODY_RED            = 0x01
    BODY_GREEN          = 0x02
    BODY_BLUE           = 0x04
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

| 변수 이름 | 형식  |  크기  |  범위   | 설명  |
| :-------: | :---: | :----: | :-----: | :---- |
|     r     | UInt8 | 1 Byte | 0 ~ 255 | Red   |
|     g     | UInt8 | 1 Byte | 0 ~ 255 | Green |
|     b     | UInt8 | 1 Byte | 0 ~ 255 | Blue  |


<br>
<br>


<a name="Colors"></a>
## Colors

색상 팔레트 인덱스

드론과 조종기 내부에 정의된 팔레트의 색상 인덱스입니다.
의도보다 색상이 더 밝게 표현되기 때문에 테스트 후 사용하기를 권해드립니다.

```py
class Colors(Enum):

    ALICEBLUE              = 0
    ANTIQUEWHITE           = 1
    AQUA                   = 2
    AQUAMARINE             = 3
    AZURE                  = 4
    BEIGE                  = 5
    BISQUE                 = 6
    BLACK                  = 7
    BLANCHEDALMOND         = 8
    BLUE                   = 9
    BLUEVIOLET             = 10
    BROWN                  = 11
    BURLYWOOD              = 12
    CADETBLUE              = 13
    CHARTREUSE             = 14
    CHOCOLATE              = 15
    CORAL                  = 16
    CORNFLOWERBLUE         = 17
    CORNSILK               = 18
    CRIMSON                = 19
    CYAN                   = 20
    DARKBLUE               = 21
    DARKCYAN               = 22
    DARKGOLDENROD          = 23
    DARKGRAY               = 24
    DARKGREEN              = 25
    DARKKHAKI              = 26
    DARKMAGENTA            = 27
    DARKOLIVEGREEN         = 28
    DARKORANGE             = 29
    DARKORCHID             = 30
    DARKRED                = 31
    DARKSALMON             = 32
    DARKSEAGREEN           = 33
    DARKSLATEBLUE          = 34
    DARKSLATEGRAY          = 35
    DARKTURQUOISE          = 36
    DARKVIOLET             = 37
    DEEPPINK               = 38
    DEEPSKYBLUE            = 39
    DIMGRAY                = 40
    DODGERBLUE             = 41
    FIREBRICK              = 42
    FLORALWHITE            = 43
    FORESTGREEN            = 44
    FUCHSIA                = 45
    GAINSBORO              = 46
    GHOSTWHITE             = 47
    GOLD                   = 48
    GOLDENROD              = 49
    GRAY                   = 50
    GREEN                  = 51
    GREENYELLOW            = 52
    HONEYDEW               = 53
    HOTPINK                = 54
    INDIANRED              = 55
    INDIGO                 = 56
    IVORY                  = 57
    KHAKI                  = 58
    LAVENDER               = 59
    LAVENDERBLUSH          = 60
    LAWNGREEN              = 61
    LEMONCHIFFON           = 62
    LIGHTBLUE              = 63
    LIGHTCORAL             = 64
    LIGHTCYAN              = 65
    LIGHTGOLDENRODYELLOW   = 66
    LIGHTGRAY              = 67
    LIGHTGREEN             = 68
    LIGHTPINK              = 69
    LIGHTSALMON            = 70
    LIGHTSEAGREEN          = 71
    LIGHTSKYBLUE           = 72
    LIGHTSLATEGRAY         = 73
    LIGHTSTEELBLUE         = 74
    LIGHTYELLOW            = 75
    LIME                   = 76
    LIMEGREEN              = 77
    LINEN                  = 78
    MAGENTA                = 79
    MAROON                 = 80
    MEDIUMAQUAMARINE       = 81
    MEDIUMBLUE             = 82
    MEDIUMORCHID           = 83
    MEDIUMPURPLE           = 84
    MEDIUMSEAGREEN         = 85
    MEDIUMSLATEBLUE        = 86
    MEDIUMSPRINGGREEN      = 87
    MEDIUMTURQUOISE        = 88
    MEDIUMVIOLETRED        = 89
    MIDNIGHTBLUE           = 90
    MINTCREAM              = 91
    MISTYROSE              = 92
    MOCCASIN               = 93
    NAVAJOWHITE            = 94
    NAVY                   = 95
    OLDLACE                = 96
    OLIVE                  = 97
    OLIVEDRAB              = 98
    ORANGE                 = 99
    ORANGERED              = 100
    ORCHID                 = 101
    PALEGOLDENROD          = 102
    PALEGREEN              = 103
    PALETURQUOISE          = 104
    PALEVIOLETRED          = 105
    PAPAYAWHIP             = 106
    PEACHPUFF              = 107
    PERU                   = 108
    PINK                   = 109
    PLUM                   = 110
    POWDERBLUE             = 111
    PURPLE                 = 112
    REBECCAPURPLE          = 113
    RED                    = 114
    ROSYBROWN              = 115
    ROYALBLUE              = 116
    SADDLEBROWN            = 117
    SALMON                 = 118
    SANDYBROWN             = 119
    SEAGREEN               = 120
    SEASHELL               = 121
    SIENNA                 = 122
    SILVER                 = 123
    SKYBLUE                = 124
    SLATEBLUE              = 125
    SLATEGRAY              = 126
    SNOW                   = 127
    SPRINGGREEN            = 128
    STEELBLUE              = 129
    TAN                    = 130
    TEAL                   = 131
    THISTLE                = 132
    TOMATO                 = 133
    TURQUOISE              = 134
    VIOLET                 = 135
    WHEAT                  = 136
    WHITE                  = 137
    WHITESMOKE             = 138
    YELLOW                 = 139
    YELLOWGREEN            = 140
    
    END_OF_TYPE            = 141
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

| 변수 이름  |  형식  |  크기  |      범위       |      설명       |
| :--------: | :----: | :----: | :-------------: | :-------------- |
|   flags    | UInt16 | 2 Byte | 0x0000 ~ 0xFFFF | LED 선택 플래그 |
| brightness | UInt8  | 1 Byte |     0 ~ 255     | 밝기            |


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

| 변수 이름 |  형식  |  크기  |   범위    |             설명              |
| :-------: | :----: | :----: | :-------: | :---------------------------- |
|   mode    | UInt8  | 1 Byte |     -     | LED 동작 모드                 |
| interval  | UInt16 | 2 Byte | 0 ~ 65535 | 내부 밝기 제어 함수 호출 주기 |


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

| 변수 이름 |          형식           |  크기  | 범위  |     설명      |
| :-------: | :---------------------: | :----: | :---: | :------------ |
|   mode    | [LightMode](#LightMode) | 3 Byte |   -   | LED 동작 모드 |
|   color   |     [Color](#Color)     | 3 Byte |   -   | LED RGB 색상  |

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

| 변수 이름 |          형식           |  크기  | 범위  |       설명        |
| :-------: | :---------------------: | :----: | :---: | :---------------- |
|   mode    | [LightMode](#LightMode) | 3 Byte |   -   | LED 동작 모드     |
|  colors   |    [Colors](#Colors)    | 1 Byte |   -   | LED 팔레트 인덱스 |

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

| 변수 이름 |  형식  |  크기  |   범위    |             설명              |
| :-------: | :----: | :----: | :-------: | :---------------------------- |
|   event   | UInt8  | 1 Byte |     -     | LED 동작 모드                 |
| interval  | UInt16 | 2 Byte | 0 ~ 65535 | 내부 색상 변화 함수 호출 주기 |
|  repeat   | UInt8  | 1 Byte |  0 ~ 255  | 반복 횟수                     |


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

| 변수 이름 |           형식            |  크기  | 범위  |     설명     |
| :-------: | :-----------------------: | :----: | :---: | :----------- |
|   event   | [LightEvent](#LightEvent) | 4 Byte |   -   | LED 이벤트   |
|   color   |      [Color](#Color)      | 3 Byte |   -   | LED RGB 색상 |



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

| 변수 이름 |           형식            |  크기  | 범위  |       설명        |
| :-------: | :-----------------------: | :----: | :---: | :---------------- |
|   event   | [LightEvent](#LightEvent) | 4 Byte |   -   | LED 이벤트        |
|  colors   |     [Colors](#Colors)     | 1 Byte |   -   | LED 팔레트 인덱스 |



<br>
<br>


<a name="DisplayPixel"></a>
## DisplayPixel

픽셀 색상

```py
class DisplayPixel(Enum):
    
    BLACK               = 0X00
    WHITE               = 0X01
    INVERSE             = 0X02
    OUTLINE             = 0X03
```


<br>
<br>


<a name="DisplayFont"></a>
## DisplayFont

폰트

```py
class DisplayFont(Enum):
    
    LIBERATION_MONO_5X8   = 0X00
    LIBERATION_MONO_10X16 = 0X01
```


<br>
<br>


<a name="DisplayAlign"></a>
## DisplayAlign

문자열 정렬

```py
class DisplayAlign(Enum):
    
    LEFT                = 0X00
    CENTER              = 0X01
    RIGHT               = 0X02
```


<br>
<br>


<a name="DisplayLine"></a>
## DisplayLine

선

```py
class DisplayLine(Enum):
    
    SOLID               = 0X00
    DOTTED              = 0X01
    DASHED              = 0X02
```


<br>
<br>


<a name="DisplayClearAll"></a>
## DisplayClearAll

화면 전체 지우기

```py
class DisplayClearAll(ISerializable):

    def __init__(self):
        self.pixel       = DisplayPixel.WHITE
```

| 변수 이름 |             형식              |  크기  | 범위  |   설명    |
| :-------: | :---------------------------: | :----: | :---: | :-------- |
|   pixel   | [DisplayPixel](#DisplayPixel) | 1 Byte |   -   | 채울 색상 |


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
        self.pixel       = DisplayPixel.WHITE
```

| 변수 이름 |             형식              |  크기  |     범위     |     설명      |
| :-------: | :---------------------------: | :----: | :----------: | :------------ |
|     x     |             Int16             | 2 Byte | -2000 ~ 2000 | X축 시작 위치 |
|     y     |             Int16             | 2 Byte | -2000 ~ 2000 | Y축 시작 위치 |
|   width   |             Int16             | 2 Byte | -2000 ~ 2000 | 너비          |
|  height   |             Int16             | 2 Byte | -2000 ~ 2000 | 높이          |
|   pixel   | [DisplayPixel](#DisplayPixel) | 1 Byte |      -       | 채울 색상     |


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

| 변수 이름 | 형식  |  크기  |     범위     |     설명      |
| :-------: | :---: | :----: | :----------: | :------------ |
|     x     | Int16 | 2 Byte | -2000 ~ 2000 | X축 시작 위치 |
|     y     | Int16 | 2 Byte | -2000 ~ 2000 | Y축 시작 위치 |
|   width   | Int16 | 2 Byte | -2000 ~ 2000 | 너비          |
|  height   | Int16 | 2 Byte | -2000 ~ 2000 | 높이          |


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
        self.pixel       = DisplayPixel.WHITE
```

| 변수 이름 |             형식              |  크기  |     범위     |   설명   |
| :-------: | :---------------------------: | :----: | :----------: | :------- |
|     x     |             Int16             | 2 Byte | -2000 ~ 2000 | X축 위치 |
|     y     |             Int16             | 2 Byte | -2000 ~ 2000 | Y축 위치 |
|   pixel   | [DisplayPixel](#DisplayPixel) | 1 Byte |      -       | 점 색상  |


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
        self.pixel       = DisplayPixel.WHITE
        self.line        = DisplayLine.SOLID
```

| 변수 이름 |             형식              |  크기  |     범위     |     설명      |
| :-------: | :---------------------------: | :----: | :----------: | :------------ |
|    x1     |             Int16             | 2 Byte | -2000 ~ 2000 | X축 시작 위치 |
|    y1     |             Int16             | 2 Byte | -2000 ~ 2000 | Y축 시작 위치 |
|    x2     |             Int16             | 2 Byte | -2000 ~ 2000 | X축 끝 위치   |
|    y2     |             Int16             | 2 Byte | -2000 ~ 2000 | Y축 끝 위치   |
|   pixel   | [DisplayPixel](#DisplayPixel) | 1 Byte |      -       | 선 색상       |
|   line    |  [DisplayLine](#DisplayLine)  | 1 Byte |      -       | 선 형태       |


<br>
<br>


<a name="DisplayDrawRect"></a>
## DisplayDrawRect

사각형 그리기

```py
class DisplayDrawRect(ISerializable):

    def __init__(self):
        self.x          = 0
        self.y          = 0
        self.width      = 0
        self.height     = 0
        self.pixel      = DisplayPixel.WHITE
        self.flag_fill  = True
        self.line       = DisplayLine.SOLID
```

| 변수 이름 |             형식              |  크기  |     범위     |          설명           |
| :-------: | :---------------------------: | :----: | :----------: | :---------------------- |
|     x     |             Int16             | 2 Byte | -2000 ~ 2000 | X축 시작 위치           |
|     y     |             Int16             | 2 Byte | -2000 ~ 2000 | Y축 시작 위치           |
|   width   |             Int16             | 2 Byte | -2000 ~ 2000 | 너비                    |
|  height   |             Int16             | 2 Byte | -2000 ~ 2000 | 높이                    |
|   pixel   | [DisplayPixel](#DisplayPixel) | 1 Byte |      -       | 색상                    |
| flag_fill |             Bool              | 1 Byte |      -       | True인 경우 내부를 채움 |
|   line    |  [DisplayLine](#DisplayLine)  | 1 Byte |      -       | 선 형태                 |


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
        self.pixel      = DisplayPixel.WHITE
        self.flag_fill  = True
```

| 변수 이름 |             형식              |  크기  |     범위     |          설명           |
| :-------: | :---------------------------: | :----: | :----------: | :---------------------- |
|     x     |             Int16             | 2 Byte | -2000 ~ 2000 | X축 중심점 위치         |
|     y     |             Int16             | 2 Byte | -2000 ~ 2000 | Y축 중심점 위치         |
|  radius   |             Int16             | 2 Byte |   1 ~ 2000   | 반지름                  |
|   pixel   | [DisplayPixel](#DisplayPixel) | 1 Byte |      -       | 색상                    |
| flag_fill |             Bool              | 1 Byte |      -       | True인 경우 내부를 채움 |


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
        self.font       = DisplayFont.LIBERATION_MONO_5X8
        self.pixel      = DisplayPixel.WHITE
        self.message    = ""
```

| 변수 이름 |             형식              |     크기     |     범위     |     설명      |
| :-------: | :---------------------------: | :----------: | :----------: | :------------ |
|     x     |             Int16             |    2 Byte    | -2000 ~ 2000 | X축 위치      |
|     y     |             Int16             |    2 Byte    | -2000 ~ 2000 | Y축 위치      |
|   font    |  [DisplayFont](#DisplayFont)  |    1 Byte    |      -       | 폰트          |
|   pixel   | [DisplayPixel](#DisplayPixel) |    1 Byte    |      -       | 색상          |
|  message  |         ASCII String          | 12 Byte 이하 |      -       | 표시할 문자열 |


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
        self.align      = DisplayAlign.CENTER
        self.font       = DisplayFont.LIBERATION_MONO_5X8
        self.pixel      = DisplayPixel.WHITE
        self.message    = ""
```

| 변수 이름 |             형식              |     크기     |     범위     |     설명      |
| :-------: | :---------------------------: | :----------: | :----------: | :------------ |
|  x_start  |             Int16             |    2 Byte    | -2000 ~ 2000 | X축 시작 위치 |
|   x_end   |             Int16             |    2 Byte    | -2000 ~ 2000 | X축 끝 위치   |
|     y     |             Int16             |    2 Byte    | -2000 ~ 2000 | Y축 위치      |
|   align   | [DisplayAlign](#DisplayAlign) |    1 Byte    |      -       | 정렬          |
|   font    |  [DisplayFont](#DisplayFont)  |    1 Byte    |      -       | 폰트          |
|   pixel   | [DisplayPixel](#DisplayPixel) |    1 Byte    |      -       | 색상          |
|  message  |         ASCII String          | 12 Byte 이하 |      -       | 표시할 문자열 |


<br>
<br>


<a name="BuzzerMode"></a>
## BuzzerMode

버저 모드

```py
class BuzzerMode(Enum):

    STOP                = 0     # 정지(Mode에서의 Stop은 통신에서 받았을 때 Buzzer를 끄는 용도로 사용, set으로만 호출)

    MUTE                = 1     # 묵음 즉시 적용
    MUTE_RESERVE        = 2     # 묵음 예약

    SCALE               = 3     # 음계 즉시 적용
    SCALE_RESERVE       = 4     # 음계 예약

    HZ                  = 5     # 주파수 즉시 적용
    HZ_RESERVE          = 6     # 주파수 예약

    END_OF_TYPE         = 7
```


<br>
<br>


<a name="BuzzerScale"></a>
## BuzzerScale

버저 음계

```py
class BuzzerScale(Enum):

    C1 = 0x00; CS1 = 0x01; D1 = 0x02; DS1 = 0x03; E1 = 0x04; F1 = 0x05; FS1 = 0x06; G1 = 0x07; GS1 = 0x08; A1 = 0x09; AS1 = 0x0A; B1 = 0x0B
    C2 = 0x0C; CS2 = 0x0D; D2 = 0x0E; DS2 = 0x0F; E2 = 0x10; F2 = 0x11; FS2 = 0x12; G2 = 0x13; GS2 = 0x14; A2 = 0x15; AS2 = 0x16; B2 = 0x17
    C3 = 0x18; CS3 = 0x19; D3 = 0x1A; DS3 = 0x1B; E3 = 0x1C; F3 = 0x1D; FS3 = 0x1E; G3 = 0x1F; GS3 = 0x20; A3 = 0x21; AS3 = 0x22; B3 = 0x23
    C4 = 0x24; CS4 = 0x25; D4 = 0x26; DS4 = 0x27; E4 = 0x28; F4 = 0x29; FS4 = 0x2A; G4 = 0x2B; GS4 = 0x2C; A4 = 0x2D; AS4 = 0x2E; B4 = 0x2F

    C5 = 0x30; CS5 = 0x31; D5 = 0x32; DS5 = 0x33; E5 = 0x34; F5 = 0x35; FS5 = 0x36; G5 = 0x37; GS5 = 0x38; A5 = 0x39; AS5 = 0x3A; B5 = 0x3B
    C6 = 0x3C; CS6 = 0x3D; D6 = 0x3E; DS6 = 0x3F; E6 = 0x40; F6 = 0x41; FS6 = 0x42; G6 = 0x43; GS6 = 0x44; A6 = 0x45; AS6 = 0x46; B6 = 0x47
    C7 = 0x48; CS7 = 0x49; D7 = 0x4A; DS7 = 0x4B; E7 = 0x4C; F7 = 0x4D; FS7 = 0x4E; G7 = 0x4F; GS7 = 0x50; A7 = 0x51; AS7 = 0x52; B7 = 0x53
    C8 = 0x54; CS8 = 0x55; D8 = 0x56; DS8 = 0x57; E8 = 0x58; F8 = 0x59; FS8 = 0x5A; G8 = 0x5B; GS8 = 0x5C; A8 = 0x5D; AS8 = 0x5E; B8 = 0x5F

    END_OF_TYPE   = 0x60

    MUTE        = 0xEE  # 묵음
    FIN         = 0xFF  # 악보의 끝
```


<br>
<br>


<a name="Buzzer"></a>
## Buzzer

버저

BuzzerMode가 **BuzzerMode.SCALE**이거나 **BuzzerMode.SCALE_RESERVE**인 경우 value에는 [BuzzerScale](#BuzzerScale)의 value 값을 사용하시면 됩니다.

BuzzerMode가 **BuzzerMode.HZ**이거나 **BuzzerMode.HZ_RESERVE**인 경우 value에는 Hz 값을 사용하시면 됩니다.

```py
class Buzzer(ISerializable):

    def __init__(self):
        self.mode       = BuzzerMode.STOP
        self.value      = 0
        self.time       = 0
```

| 변수 이름 |           형식            |  크기  |    범위    |          설명          |
| :-------: | :-----------------------: | :----: | :--------: | :--------------------- |
|   mode    | [BuzzerMode](#BuzzerMode) | 1 Byte |     -      | 버저 동작 모드         |
|   value   |          UInt16           | 2 Byte |  0 ~ 8000  | Scale 값 또는 Hz 값    |
|   time    |          UInt16           | 2 Byte | 0 ~ 65,535 | 소리를 지속할 시간(ms) |

- e.g. [Buzzer 클래스 데이터를 직접 채워서 전송하기](examples_08_buzzer.md#Class_Buzzer)

<br>
<br>


<a name="VibratorMode"></a>
## VibratorMode

진동 모드

```py
class VibratorMode(Enum):

    STOP            = 0     # 정지

    INSTANTLY       = 1     # 즉시 적용
    CONTINUALLY     = 2     # 예약

    END_OF_TYPE     = 3
```


<br>
<br>


<a name="Vibrator"></a>
## Vibrator

진동

```py
class Vibrator(ISerializable):

    def __init__(self):
        self.mode       = VibratorMode.STOP
        self.on         = 0
        self.off        = 0
        self.total      = 0
```

| 변수 이름 |             형식              |  크기  |    범위    |        설명        |
| :-------: | :---------------------------: | :----: | :--------: | :----------------- |
|   mode    | [VibratorMode](#VibratorMode) | 1 Byte |     -      | 진동 동작 모드     |
|    on     |            UInt16             | 2 Byte | 0 ~ 65,535 | 진동을 켠 시간(ms) |
|    off    |            UInt16             | 2 Byte | 0 ~ 65,535 | 진동을 끈 시간(ms) |
|   total   |            UInt16             | 2 Byte | 0 ~ 65,535 | 전체 동작 시간(ms) |

- e.g. [Vibrator 클래스 데이터를 직접 채워서 전송하기](examples_09_vibrator.md#Class_Vibrator)


<br>
<br>


<a name="ButtonFlagController"></a>
## ButtonFlagController

조종기 버튼 플래그

```py
class ButtonFlagController(Enum):

    NONE                = 0x0000

    FRONT_LEFT_TOP      = 0x0001
    FRONT_LEFT_BOTTOM   = 0x0002
    FRONT_RIGHT_TOP     = 0x0004
    FRONT_RIGHT_BOTTOM  = 0x0008

    TOP_LEFT            = 0x0010
    TOP_RIGHT           = 0x0020    # POWER ON/OFF

    MID_UP              = 0x0040
    MID_LEFT            = 0x0080
    MID_RIGHT           = 0x0100
    MID_DOWN            = 0x0200

    BOTTOM_LEFT         = 0x0400
    BOTTOM_RIGHT        = 0x0800
```


<br>
<br>


<a name="ButtonFlagDrone"></a>
## ButtonFlagDrone

드론 버튼 플래그

```py
class ButtonFlagDrone(Enum):

    NONE        = 0x0000
    
    RESET       = 0x0001
```


<br>
<br>


<a name="ButtonEvent"></a>
## ButtonEvent

버튼 이벤트

```py
class ButtonEvent(Enum):

    NONE                = 0x00
    
    DOWN                = 0x01  # 누르기 시작
    PRESS               = 0x02  # 누르는 중
    UP                  = 0x03  # 뗌
    
    END_CONTINUE_PRESS  = 0x04  # 연속 입력 종료
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
        self.event      = ButtonEvent.NONE
```

| 변수 이름 |            형식             |  크기  | 범위  |    설명     |
| :-------: | :-------------------------: | :----: | :---: | :---------- |
|  button   |           UInt16            | 2 Byte |   -   | 버튼 입력   |
|   event   | [ButtonEvent](#ButtonEvent) | 1 Byte |   -   | 버튼 이벤트 |

- e.g. [버튼 입력값 출력](examples_12_input.md#Button)


<br>
<br>


<a name="JoystickDirection"></a>
## JoystickDirection

조이스틱 방향

```py
class JoystickDirection(Enum):

    NONE   = 0         # 정의하지 않은 영역(무시함)

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

    NONE        = 0     # 이벤트 없음
    
    IN          = 1     # 특정 영역에 진입
    STAY        = 2     # 특정 영역에서 상태 유지
    OUT         = 3     # 특정 영역에서 벗어남
    
    END_OF_TYPE = 4
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
        self.direction  = JoystickDirection.NONE
        self.event      = JoystickEvent.NONE
```

| 변수 이름 |                  형식                   |  크기  |    범위    |     설명      |
| :-------: | :-------------------------------------: | :----: | :--------: | :------------ |
|     x     |                  Int8                   | 1 Byte | -100 ~ 100 | X축 값        |
|     y     |                  Int8                   | 1 Byte | -100 ~ 100 | Y축 값        |
| direction | [JoystickDirection](#JoystickDirection) | 1 Byte |     -      | 조이스틱 방향 |
|   event   |     [JoystickEvent](#JoystickEvent)     | 1 Byte |     -      | 이벤트        |


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

| 변수 이름 |              형식               |  크기  | 범위  |      설명       |
| :-------: | :-----------------------------: | :----: | :---: | :-------------- |
|   left    | [JoystickBlock](#JoystickBlock) | 4 Byte |   -   | 왼쪽 조이스틱   |
|   right   | [JoystickBlock](#JoystickBlock) | 4 Byte |   -   | 오른쪽 조이스틱 |

- e.g. [조이스틱 입력값 출력](examples_12_input.md#Joystick)


<br>
<br>


<a name="RawMotion"></a>
## RawMotion

Motion 센서 데이터 RAW 값

```py
class RawMotion(ISerializable):

    def __init__(self):
        self.accel_x     = 0
        self.accel_y     = 0
        self.accel_z     = 0
        self.gyro_roll   = 0
        self.gyro_pitch  = 0
        self.gyro_yaw    = 0
```

| 변수 이름  | 형식  |  크기  |       범위       |     설명     |
| :--------: | :---: | :----: | :--------------: | :----------- |
|  accel_x   | Int16 | 2 Byte | -32,768 ~ 32,767 | 가속도 X     |
|  accel_y   | Int16 | 2 Byte | -32,768 ~ 32,767 | 가속도 Y     |
|  accel_z   | Int16 | 2 Byte | -32,768 ~ 32,767 | 가속도 Z     |
| gyro_roll  | Int16 | 2 Byte | -32,768 ~ 32,767 | 자이로 Roll  |
| gyro_pitch | Int16 | 2 Byte | -32,768 ~ 32,767 | 자이로 Pitch |
|  gyro_yaw  | Int16 | 2 Byte | -32,768 ~ 32,767 | 자이로 Yaw   |


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

| 변수 이름 |  형식   |  크기  | 범위  |  설명  |
| :-------: | :-----: | :----: | :---: | :----- |
|     x     | Float32 | 4 Byte |   -   | X축(m) |
|     y     | Float32 | 4 Byte |   -   | Y축(m) |


<br>
<br>


<a name="State"></a>
## State

드론 상태

```py
class State(ISerializable):

    def __init__(self):
        self.mode_system          = ModeSystem.NONE
        self.mode_flight          = ModeFlight.NONE
        self.mode_control_flight  = ModeControlFlight.NONE
        self.mode_movement        = ModeMovement.NONE
        self.headless             = Headless.NONE
        self.control_speed        = 0
        self.sensor_orientation   = SensorOrientation.NONE
        self.battery              = 0
```

|      변수 이름      |                        형식                         |  크기  |  범위   |         설명          |
| :-----------------: | :-------------------------------------------------: | :----: | :-----: | :-------------------- |
|     mode_system     |        [ModeSystem](03_system.md#ModeSystem)        | 1 Byte |    -    | System 동작 모드      |
|     mode_flight     |        [ModeFlight](03_system.md#ModeFlight)        | 1 Byte |    -    | 비행 제어기 동작 모드 |
| mode_control_flight | [ModeControlFlight](03_system.md#ModeControlFlight) | 1 Byte |    -    | 비행 제어 모드        |
|    mode_movement    |      [ModeMovement](03_system.md#ModeMovement)      | 1 Byte |    -    | 이동 상태             |
|      headless       |          [Headless](03_system.md#Headless)          | 1 Byte |    -    | Headless 설정 상태    |
|    control_speed    |                        UInt8                        | 1 Byte |  0 ~ 2  | 이동 속도 설정        |
| sensor_orientation  | [SensorOrientation](03_system.md#SensorOrientation) | 1 Byte |    -    | 센서 방향             |
|       battery       |                        UInt8                        | 1 Byte | 0 ~ 100 | 드론 배터리 잔량      |

- e.g. [드론 모드를 변경 후 확인](examples_07_setup.md#ModeVehicle)


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

| 변수 이름 | 형식  |  크기  |       범위       | 설명  |
| :-------: | :---: | :----: | :--------------: | :---- |
|   roll    | Int16 | 2 Byte | -32,768 ~ 32,767 | Roll  |
|   pitch   | Int16 | 2 Byte | -32,768 ~ 32,767 | Pitch |
|    yaw    | Int16 | 2 Byte | -32,768 ~ 32,767 | Yaw   |

- e.g. [자세 확인](examples_05_sensor.md#Attitude)


<br>
<br>


<a name="Position"></a>
## Position

드론의 위치

```py
class Position(ISerializable):

    def __init__(self):
        self.x     = 0
        self.y     = 0
        self.z     = 0
```

| 변수 이름 |  형식   |  크기  | 범위  |  설명  |
| :-------: | :-----: | :----: | :---: | :----- |
|     x     | Float32 | 4 Byte |   -   | X축(m) |
|     y     | Float32 | 4 Byte |   -   | Y축(m) |
|     z     | Float32 | 4 Byte |   -   | Z축(m) |


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
        self.range_height   = 0
```

|  변수 이름   |  형식   |  크기  | 범위  |              설명              |
| :----------: | :-----: | :----: | :---: | :----------------------------- |
| temperature  | Float32 | 4 Byte |   -   | 온도(℃)                        |
|   pressure   | Float32 | 4 Byte |   -   | 압력                           |
|   altitude   | Float32 | 4 Byte |   -   | 압력을 해발고도로 변환한 값(m) |
| range_height | Float32 | 4 Byte |   -   | 거리센서에서 출력한 높이 값(m) |

- e.g. [고도 데이터 확인](examples_05_sensor.md#Altitude)


<br>
<br>


<a name="Motion"></a>
## Motion

Motion 센서 데이터와 드론의 자세

angle_roll, angle_pitch, angle_yaw는 Attitude에서 받을 수 있는 드론의 자세값과 같은 값입니다.

accel_x, accel_y, accel_z 값은 **x10**을 한 값입니다.

```py
class Motion(ISerializable):

    def __init__(self):
        self.accel_x     = 0
        self.accel_y     = 0
        self.accel_z     = 0
        self.gyro_roll   = 0
        self.gyro_pitch  = 0
        self.gyro_yaw    = 0
        self.angle_roll  = 0
        self.angle_pitch = 0
        self.angle_yaw   = 0
```

|  변수 이름  | 형식  |  크기  |               범위               |         단위         |     설명     |
| :---------: | :---: | :----: | :------------------------------: | :------------------: | :----------- |
|   accel_x   | Int16 | 2 Byte | -1568 ~ 1568<br>(-156.8 ~ 156.8) | m/s<sup>2</sup> x 10 | 가속도 X     |
|   accel_y   | Int16 | 2 Byte | -1568 ~ 1568<br>(-156.8 ~ 156.8) | m/s<sup>2</sup> x 10 | 가속도 Y     |
|   accel_z   | Int16 | 2 Byte | -1568 ~ 1568<br>(-156.8 ~ 156.8) | m/s<sup>2</sup> x 10 | 가속도 Z     |
|  gyro_roll  | Int16 | 2 Byte |           -2000 ~ 2000           |       degree/s       | 자이로 Roll  |
| gyro_pitch  | Int16 | 2 Byte |           -2000 ~ 2000           |       degree/s       | 자이로 Pitch |
|  gyro_yaw   | Int16 | 2 Byte |           -2000 ~ 2000           |       degree/s       | 자이로 Yaw   |
| angle_roll  | Int16 | 2 Byte |            -180 ~ 180            |        degree        | 자세 Roll    |
| angle_pitch | Int16 | 2 Byte |            -180 ~ 180            |        degree        | 자세 Pitch   |
|  angle_yaw  | Int16 | 2 Byte |            -180 ~ 180            |        degree        | 자세 Yaw     |

- e.g. [Motion 센서 데이터 확인](examples_05_sensor.md#Imu)


<br>
<br>


<a name="Flow"></a>
## Flow

Flow 센서에서 연산한 위치 + 거리 센서의 값

```py
class Flow(ISerializable):

    def __init__(self):
        self.x     = 0
        self.y     = 0
        self.z     = 0
```

| 변수 이름 |  형식   |  크기  | 범위  |          설명           |
| :-------: | :-----: | :----: | :---: | :---------------------- |
|     x     | Float32 | 4 Byte |   -   | X축(m)                  |
|     y     | Float32 | 4 Byte |   -   | Y축(m)                  |
|     z     | Float32 | 4 Byte |   -   | Z축(m) / 거리 센서의 값 |

- e.g. [Flow 센서 데이터 확인](examples_05_sensor.md#Flow)

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

| 변수 이름 | 형식  |  크기  |       범위       | 설명 |
| :-------: | :---: | :----: | :--------------: | :--- |
|     x     | Int16 | 2 Byte | -32,768 ~ 32,767 | X    |
|     y     | Int16 | 2 Byte | -32,768 ~ 32,767 | Y    |
|     z     | Int16 | 2 Byte | -32,768 ~ 32,767 | Z    |


<br>
<br>


<a name="Count"></a>
## Count

카운트

각 카운트 값은 드론 내부에 UInt32로 저장하고 있지만, 전송 시에는 UInt16으로 변환하여 전송합니다. 만약 더 큰 값이 필요한 상황이 생기면 변경할 예정입니다.(6만번 이상 이착륙 등)

```py
class Count(ISerializable):

    def __init__(self):
        self.time_flight     = 0

        self.count_takeoff   = 0
        self.count_landing   = 0
        self.count_accident  = 0
```

|   변수 이름    |  형식  |  크기  |   범위    |     설명      |
| :------------: | :----: | :----: | :-------: | :------------ |
|  time_flight   | UInt64 | 8 Byte |     -     | 비행 시간(ms) |
| count_takeoff  | UInt16 | 2 Byte | 0 ~ 65535 | 이륙 횟수     |
| count_landing  | UInt16 | 2 Byte | 0 ~ 65535 | 착륙 횟수     |
| count_accident | UInt16 | 2 Byte | 0 ~ 65535 | 충돌 횟수     |


<br>
<br>


<a name="Bias"></a>
## Bias

바이어스

가속도, 자이로에 대한 바이어스 설정값입니다.
읽기만 가능합니다.

```py
class Bias(ISerializable):
    
    def __init__(self):
        self.accel_x     = 0
        self.accel_y     = 0
        self.accel_z     = 0
        self.gyro_roll   = 0
        self.gyro_pitch  = 0
        self.gyro_yaw    = 0
```

| 변수 이름  | 형식  |  크기  |       범위       |    설명    |
| :--------: | :---: | :----: | :--------------: | :--------- |
|  accel_x   | Int16 | 2 Byte | -32,768 ~ 32,767 | Accel X    |
|  accel_y   | Int16 | 2 Byte | -32,768 ~ 32,767 | Accel Y    |
|  accel_z   | Int16 | 2 Byte | -32,768 ~ 32,767 | Accel Z    |
| gyro_roll  | Int16 | 2 Byte | -32,768 ~ 32,767 | Gyro Roll  |
| gyro_pitch | Int16 | 2 Byte | -32,768 ~ 32,767 | Gyro Pitch |
|  gyro_yaw  | Int16 | 2 Byte | -32,768 ~ 32,767 | Gyro Yaw   |


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

| 변수 이름 | 형식  |  크기  |    범위    |   설명   |
| :-------: | :---: | :----: | :--------: | :------- |
|   roll    | Int16 | 2 Byte | -200 ~ 200 | Roll     |
|   pitch   | Int16 | 2 Byte | -200 ~ 200 | Pitch    |
|    yaw    | Int16 | 2 Byte | -200 ~ 200 | Yaw      |
| throttle  | Int16 | 2 Byte | -200 ~ 200 | Throttle |

- e.g. [드론 Trim 설정 변경 후 확인](examples_07_setup.md#Trim)


<br>
<br>


<a name="Weight"></a>
## Weight

무게

드론 + 적재물의 무게입니다. 단위는 그램(g)입니다.

```py
class Weight(ISerializable):

    def __init__(self):
        self.weight     = 0
```

| 변수 이름 |  형식   |  크기  | 범위  | 설명 |
| :-------: | :-----: | :----: | :---: | :--- |
|  weight   | Float32 | 4 Byte |   -   | 무게 |


<br>
<br>


<a name="LostConnection"></a>
## LostConnection

통신 연결이 끊긴 후 반응 시간 설정

마지막으로 비행 이벤트 또는 조종 명령을 보냈던 장치와의 연결이 끊어진 후에 지정한 시간이 경과하면 해당 명령을 실행. 시간을 0으로 설정한 경우 해당 명령은 실행하지 않음. 시간 단위는 ms

```py
class LostConnection(ISerializable):

    def __init__(self):
        self.time_neutral    = 0
        self.time_landing    = 0
        self.time_stop       = 0
```

|  변수 이름   |  형식  |  크기  |       범위        |   설명    |
| :----------: | :----: | :----: | :---------------: | :-------- |
| time_neutral | UInt16 | 2 Byte |    0 ~ 65,535     | 조종 중립 |
| time_landing | UInt16 | 2 Byte |    0 ~ 65,535     | 착륙      |
|  time_stop   | UInt32 | 4 Byte | 0 ~ 4,294,967,295 | 정지      |


<br>
<br>


<a name="MotorBlock"></a>
## MotorBlock

모터 블럭

```py
class MotorBlock(ISerializable):

    def __init__(self):
        self.rotation   = Rotation.NONE
        self.value      = 0
```

| 변수 이름 |               형식                |  크기  |   범위   |      설명      |
| :-------: | :-------------------------------: | :----: | :------: | :------------- |
| rotation  | [Rotation](03_system.md#Rotation) | 1 Byte |    -     | 모터 회전 방향 |
|   value   |              UInt16               | 2 Byte | 0 ~ 4095 | 모터 회전 속도 |


<br>
<br>


<a name="Motor"></a>
## Motor

모터 전체 제어

모터 순서는 왼쪽 앞부터 시계 방향입니다.

```py
class Motor(ISerializable):

    def __init__(self):
        self.motor = []
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
```

| 변수 이름 |           형식            |  크기  | 범위  |      설명      |
| :-------: | :-----------------------: | :----: | :---: | :------------- |
| motor[0]  | [MotorBlock](#MotorBlock) | 3 Byte |   -   | 왼쪽 앞 모터   |
| motor[1]  | [MotorBlock](#MotorBlock) | 3 Byte |   -   | 오른쪽 앞 모터 |
| motor[2]  | [MotorBlock](#MotorBlock) | 3 Byte |   -   | 오른쪽 뒤 모터 |
| motor[3]  | [MotorBlock](#MotorBlock) | 3 Byte |   -   | 왼쪽 뒤 모터   |


<br>
<br>


<a name="MotorSingle"></a>
## MotorSingle

한 개의 모터 제어

```py
class MotorSingle(ISerializable):

    def __init__(self):
        self.target     = 0
        self.value      = 0
```

| 변수 이름 |  형식  |  크기  |   범위   |      설명      |
| :-------: | :----: | :----: | :------: | :------------- |
|  target   | UInt8  | 1 Byte |  0 ~ 3   | 동작 대상 모터 |
|   value   | UInt16 | 2 Byte | 0 ~ 4095 | 모터 회전 속도 |


<br>
<br>


<a name="MotorSingleRotation"></a>
## MotorSingleRotation

한 개의 모터 제어 + 회전 방향을 포함

```py
class MotorSingleRotation(ISerializable):

    def __init__(self):
        self.target     = 0
        self.rotation   = Rotation.NONE
        self.value      = 0
```

| 변수 이름 |               형식                |  크기  |   범위   |      설명      |
| :-------: | :-------------------------------: | :----: | :------: | :------------- |
|  target   |               UInt8               | 1 Byte |  0 ~ 3   | 동작 대상 모터 |
| rotation  | [Rotation](03_system.md#Rotation) | 1 Byte |    -     | 모터 회전 방향 |
|   value   |              UInt16               | 2 Byte | 0 ~ 4095 | 모터 회전 속도 |


<br>

---

<h3><i>e_drone</i> for python</H3>

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
16. [Examples - Display](examples_11_display.md)
17. [Examples - Input](examples_12_input.md)
18. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
