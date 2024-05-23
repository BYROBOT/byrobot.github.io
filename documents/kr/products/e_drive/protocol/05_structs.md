**[E-DRIVE](index.md)** / **Protocol** / **Structs**

Modified : 2020.1.13

---

#### 데이터 송수신 시에 사용하는 구조체들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}

<br>


<a name="Protocol_Header"></a>
## Protocol::Header

헤더

데이터 송수신 시에 사용하는 헤더입니다.

```cpp
namespace Protocol
{
    struct Header
    {
        u8      dataType;       // 데이터의 형식
        u8      length;         // 데이터의 길이
        u8      from;           // 데이터를 전송하는 장치의 DeviceType
        u8      to;             // 데이터를 수신하는 장치의 DeviceType
        
    };
}
```

| 변수 이름 | 형식                                                                 | 크기     | 범위      | 설명                     |
|:---------:|:--------------------------------------------------------------------:|:--------:|:---------:|:-------------------------|
| dataType  | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)         | 1 Byte   | -         | 데이터의 타입            |
| length    | uint8_t                                                              | 1 Byte   | 0 ~ 255   | 데이터의 길이            |
| from      | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType)  | 1 Byte   | -         | 데이터를 전송하는 장치   |
| to        | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType)  | 1 Byte   | -         | 데이터를 수신하는 장치   |


<br>
<br>


<a name="Protocol_Ping"></a>
## Protocol::Ping

Ping

특정 장치가 존재하는지를 확인할 때 사용합니다. 응답은 Ack를 받습니다.

```cpp
namespace Protocol
{
    struct Ping
    {
        u64     systemTime;   // Ping을 전송하는 장치의 시각
    };
}
```

| 변수 이름   | 형식        | 크기     | 범위  | 설명           |
|:-----------:|:-----------:|:--------:|:-----:|:---------------|
| systemTime  | uint64_t    | 8 Byte   | -     | 시스템 시간    |


<br>
<br>


<a name="Protocol_Ack"></a>
## Protocol::Ack

응답

특정한 데이터를 요청하지 않은 경우에 Ack를 응답으로 전송합니다. 수신 받은 데이터의 crc16을 포함하여 돌려보내기 때문에 데이터를 전송한 측에서 정상적으로 데이터를 전송했는지 판별하는데 사용합니다.

```cpp
namespace Protocol
{
    struct Ack
    {
        u64     systemTime;     // 수신 받은 시간
        u8      dataType;       // 수신 받은 데이터 타입
        u16     crc16;          // 수신 받은 데이터의 crc16
    };
}
```

| 변수 이름    | 형식                                                         | 크기     | 범위   | 설명                                |
|:------------:|:------------------------------------------------------------:|:--------:|:------:|:------------------------------------|
| systemTime   | uint64_t                                                     | 8 Byte   | -      | 시스템 시간                         |
| dataType     | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType) | 1 Byte   | -      | 수신 받은 데이터 타입               |
| crc16        | uint16_t                                                     | 2 Byte   | -      | 수신 받은 헤더와 데이터의 CRC16 값  |


<br>
<br>


<a name="Protocol_Error"></a>
## Protocol::Error

오류

드론에 문제가 생긴 경우 Error 구조체를 600ms에 한 번 송신합니다.

errorFlagsForSensor와 errorFlagsForState는 각각의 값에 해당하는 플래그를 조합하여 여러 오류들이 동시에 발생하는 것을 표시합니다.

문제가 완전히 없어진 경우 Error 플래그를 0으로 초기화하여 추가로 5회 전송 후 전송을 중단합니다.

```cpp
namespace Protocol
{
    struct Error
    {
        u64     systemTime;             // 에러 메세지 송신 시각
        u32     errorFlagsForSensor;    // 센서 오류 플래그
        u32     errorFlagsForState;     // 상태 오류 플래그
    };
}
```

| 변수 이름            | 형식                                                                | 크기     | 범위   | 설명                    |
|:--------------------:|:-------------------------------------------------------------------:|:--------:|:------:|:------------------------|
| systemTime           | uint64_t                                                            | 8 Byte   | -      | 시스템 시간             |
| errorFlagsForSensor  | [ErrorFlagsForSensor::Type](04_definitions.md#ErrorFlagsForSensor)  | 4 Byte   | -      | 센서 오류 플래그 조합   |
| errorFlagsForState   | [ErrorFlagsForState::Type](04_definitions.md#ErrorFlagsForState)    | 4 Byte   | -      | 상태 오류 플래그 조합   |


<br>
<br>


<a name="Protocol_Request"></a>
## Protocol::Request

데이터 요청

```cpp
namespace Protocol
{
    struct Request
    {
        u8      dataType;          // 요청할 데이터 타입
    };
}
```

| 변수 이름     | 형식                                                          | 크기     | 범위  | 설명                  |
|:-------------:|:-------------------------------------------------------------:|:--------:|:-----:|:----------------------|
| dataType      | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)  | 1 Byte   | -     | 요청할 데이터 타입    |


<br>
<br>


<a name="Protocol_Address"></a>
## Protocol::Address

장치 주소(고유번호)

```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[16];
    };
}
```

| 변수 이름  | 형식            | 크기     | 범위  | 설명         |
|:----------:|:---------------:|:--------:|:-----:|:-------------|
| address    | uint8_t Array   | 16 Byte  | -     | 장치 주소    |


<br>
<br>


<a name="Protocol_Information"></a>
## Protocol::Information

펌웨어 정보

```cpp
namespace Protocol
{
    struct Information
    {
        u8      modeUpdate;     // 업데이트 모드

        u32     modelNumber;    // 모델 번호
        u32     version;        // 현재 펌웨어의 버전

        u16     year;           // 빌드 년
        u8      month;          // 빌드 월
        u8      day;            // 빌드 일
    };
}
```

| 변수 이름     | 형식                                                                | 크기     | 범위 | 설명                |
|:-------------:|:-------------------------------------------------------------------:|:--------:|:----:|:--------------------|
| modeUpdate    | [Mode::Update::Type](04_definitions.md#Mode_Update)                 | 1 Byte   | -    | 업데이트 모드       |
| modelNumber   | [ModelNumber::Type](04_definitions.md#ModelNumber)                  | 4 Byte   | -    | 모델 번호           |
| version       | [Protocol::Version](#Protocol_Version)                              | 4 Byte   | -    | 펌웨어의 버전       |
| year          | uint16_t                                                            | 2 Byte   | -    | 펌웨어 빌드 년      |
| month         | uint8_t                                                             | 1 Byte   | -    | 펌웨어 빌드 월      |
| day           | uint8_t                                                             | 1 Byte   | -    | 펌웨어 빌드 일      |


<br>
<br>


<a name="Protocol_InformationCC2541"></a>
## Protocol::InformationCC2541

BLE(Bluetooth Low Energy) 통신 칩의 펌웨어 정보

```cpp
namespace Protocol
{
    struct InformationCC2541
    {
        u8      modeUpdate;     // 업데이트 모드

        u32     modelNumber;    // 모델 번호
        u32     version;        // 현재 펌웨어의 버전

        u16     year;           // 빌드 년
        u8      month;          // 빌드 월
        u8      day;            // 빌드 일

        u8      imageType;      // 이미지 타입
    };
}
```

| 변수 이름     | 형식                                                                | 크기     | 범위 | 설명                |
|:-------------:|:-------------------------------------------------------------------:|:--------:|:----:|:--------------------|
| modeUpdate    | [Mode::Update::Type](04_definitions.md#Mode_Update)                 | 1 Byte   | -    | 업데이트 모드       |
| modelNumber   | [ModelNumber::Type](04_definitions.md#ModelNumber)                  | 4 Byte   | -    | 모델 번호           |
| version       | [Protocol::Version](#Protocol_Version)                              | 4 Byte   | -    | 펌웨어의 버전       |
| year          | uint16_t                                                            | 2 Byte   | -    | 펌웨어 빌드 년      |
| month         | uint8_t                                                             | 1 Byte   | -    | 펌웨어 빌드 월      |
| day           | uint8_t                                                             | 1 Byte   | -    | 펌웨어 빌드 일      |
| imageType     | [ImageType::Type](04_definitions.md#ImageType)                      | 1 Byte   | -    | 이미지 타입         |


<br>
<br>


<a name="Protocol_Version"></a>
## Protocol::Version

펌웨어 버전

버전 비교 시 v 값으로 비교할 수 있도록 struct 내부의 변수 배치 순서를 다른 구조체들과 다르게 역순으로 배열하였습니다.

```cpp
namespace Protocol
{
    union Version
    {
        struct
        {
            u16     build;      // Build Number
            u8      minor;      // Minor Number
            u8      major;      // Major Number
        };

        u32 v;
    };
}
```

| 변수 이름  | 형식             | 크기     | 범위       | 설명         |
|:----------:|:----------------:|:--------:|:----------:|:-------------|
| build      | uint16_t         | 14 bit   | 0 ~ 65535  | 빌드 번호    |
| minor      | uint8_t          | 1 Byte   | 0 ~ 255    | 부 번호      |
| major      | uint8_t          | 1 Byte   | 0 ~ 255    | 주 번호      |
| v          | uint32_t         | 4 Byte   | -          | build, minor, major를 하나로 묶은 것  |



<br>
<br>


<a name="Control_Double8"></a>
## Control::Double8

조종

```cpp
namespace Control
{
    struct Double8
    {
        s8      accel;      // accel
        s8      wheel;      // wheel
    };
}
```

| 변수 이름 | 형식     | 크기     | 범위         | 설명       | 음수 값(-) | 양수 값(+)    |
|:---------:|:--------:|:--------:|:------------:|:-----------|:----------:|:-------------:|
| accel     | int8_t   | 1 Byte   | -100 ~ 100   | 전후       | 후방       | 전방          |
| wheel     | int8_t   | 1 Byte   | -100 ~ 100   | 좌우       | 좌측       | 우측          |


<br>
<br>


<a name="Control_Double8AndRequestData"></a>
## Control::Double8AndRequestData

조종 및 데이터 요청

조종 명령 시 응답 데이터로 Ack 대신 요청한 데이터를 응답으로 보내게 함.

```cpp
namespace Control
{
    struct Double8AndRequestData
    {
        s8      accel;      // accel
        s8      wheel;      // wheel

        u8      dataType;   // DataType
    };
}
```

| 변수 이름 | 형식     | 크기     |범위          | 설명       | 음수 값(-) | 양수 값(+)    |
|:---------:|:--------:|:--------:|:------------:|:-----------|:----------:|:-------------:|
| accel     | int8_t   | 1 Byte   | -100 ~ 100   | 전후       | 후방       | 전방          |
| wheel     | int8_t   | 1 Byte   | -100 ~ 100   | 좌우       | 좌측       | 우측          |
| dataType  | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType) | - | 1 Byte | 요청할 데이터 타입 | - | - |


<br>
<br>


<a name="Control_PositionDriveMove"></a>
## Control::PositionDriveMove

이동

```cpp
namespace Control
{
    struct PositionDriveMove
    {
        float       positionX;              // meter
        float       positionY;              // meter
        float       velocity;               // m/s
    };
}
```


| 변수 이름             | 형식     | 크기     | 범위           | 단위     | 설명                 |
|:---------------------:|:--------:|:--------:|:--------------:|:---------|:---------------------|
| positionX             | float    | 4 Byte   | -10.0 ~ 10.0   | meter    | 앞(+), 뒤(-)         |
| positionY             | float    | 4 Byte   | -10.0 ~ 10.0   | meter    | 좌(+), 우(-)         |
| velocity              | float    | 4 Byte   | 0.0 ~ 5.0      | m/s      | 앞뒤 이동 속도       |


<br>
<br>


<a name="Control_PositionDriveHeading"></a>
## Control::PositionDriveHeading

제자리 회전

```cpp
namespace Control
{
    struct PositionDriveHeading
    {
        float       heading;                // degree
        float       rotationalVelocity;     // deg/s
    };
}
```


| 변수 이름             | 형식     | 크기     | 범위           | 단위     | 설명                        |
|:---------------------:|:--------:|:--------:|:--------------:|:---------|:----------------------------|
| heading               | float    | 4 Byte   | -360.0 ~ 360.0 | degree   | 반시계방향(+), 시계방향(-)  |
| rotationalVelocity    | float    | 4 Byte   | 10.0 ~ 180.0   | degree/s | 좌우 회전 속도              |


<br>
<br>


<a name="Protocol_Command_Command"></a>
## Protocol::Command::Command

설정 변경

```cpp
namespace Protocol
{
    namespace Command
    {
        struct Command
        {
            u8      commandType;   // 명령 타입
            u8      option;        // 명령에 대한 옵션
        };
    }
}
```

| 변수 이름   | 형식                                                                    | 크기     | 범위    | 설명         |
|:-----------:|:-----------------------------------------------------------------------:|:--------:|:-------:|:-------------|
| commandType | [Protocol::CommandType::Type](04_definitions.md#Protocol_CommandType)   | 1 Byte   | -       | 명령 타입    |
| option      | [Mode::Drone::Type](04_definitions.md#Mode_Drone)                       | 1 Byte   | -       | 옵션         |
|             | [System::DriveEvent::Type](04_definitions.md#DriveEvent)                |          | -       |              |
|             | uint8_t                                                                 |          | -       |              |


<br>
<br>


<a name="Protocol_Command_LightEvent"></a>
## Protocol::Command::LightEvent

설정 변경 + LED 이벤트

```cpp
namespace Protocol
{
    namespace Command
    {
        struct LightEvent
        {
            Protocol::Command::Command      command;
            Protocol::Light::Event          event;
        };
    }
}
```

| 변수 이름   | 형식                                                                  | 크기     | 범위    | 설명         |
|:-----------:|:---------------------------------------------------------------------:|:--------:|:-------:|:-------------|
| command     | [Protocol::Command::Command](#Protocol_Command_Command)               | 2 Byte   | -       | 명령         |
| event       | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event)    | 4 Byte   | -       | LED 이벤트   |


<br>
<br>


<a name="Protocol_Command_LightEventColor"></a>
## Protocol::Command::LightEventColor

설정 변경 + LED 이벤트(RGB)

```cpp
namespace Protocol
{
    namespace Command
    {
        struct LightEventColor
        {
            Protocol::Command::Command      command;
            Protocol::Light::Event          event;
            Light::Color                    color;
        };
    }
}
```

| 변수 이름   | 형식                                                                  | 크기     | 범위    | 설명         |
|:-----------:|:---------------------------------------------------------------------:|:--------:|:-------:|:-------------|
| command     | [Protocol::Command::Command](#Protocol_Command_Command)               | 2 Byte   | -       | 명령         |
| event       | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event)    | 4 Byte   | -       | LED 이벤트   |
| color       | [Light::Color](06_structs_light.md#Light_Color)                       | 3 Byte   | -       | LED RGB 색상 |


<br>
<br>


<a name="Protocol_Command_LightEventColors"></a>
## Protocol::Command::LightEventColors

설정 변경 + LED 이벤트(Palette)

```cpp
namespace Protocol
{
    namespace Command
    {
        struct LightEventColors
        {
            Protocol::Command::Command      command;
            Protocol::Light::Event          event;
            u8                              colors;
        };
    }
}
```

| 변수 이름   | 형식                                                                  | 크기     | 범위    | 설명              |
|:-----------:|:---------------------------------------------------------------------:|:--------:|:-------:|:------------------|
| command     | [Protocol::Command::Command](#Protocol_Command_Command)               | 2 Byte   | -       | 명령              |
| event       | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event)    | 4 Byte   | -       | LED 이벤트        |
| colors      | [Light::Colors::Type](06_structs_light.md#Light_Colors)               | 1 Byte   | -       | LED 팔레트 인덱스 |


<br>
<br>


<a name="Protocol_RawMotion"></a>
## Protocol::RawMotion

Motion 센서 RAW 데이터

```cpp
namespace Protocol
{
    struct RawMotion
    {
        s16     accX;
        s16     accY;
        s16     accZ;
        
        s16     gyroRoll;
        s16     gyroPitch;
        s16     gyroYaw;
    };
}
```

| 변수 이름  | 형식     | 크기     | 범위              | 설명           |
|:----------:|:--------:|:--------:|:-----------------:|:---------------|
| accelX     | int16_t  | 2 Byte   | -32,768 ~ 32,767  | 가속도 X       |
| accelY     | int16_t  | 2 Byte   | -32,768 ~ 32,767  | 가속도 Y       |
| accelZ     | int16_t  | 2 Byte   | -32,768 ~ 32,767  | 가속도 Z       |
| gyroRoll   | int16_t  | 2 Byte   | -32,768 ~ 32,767  | 자이로 Roll    |
| gyroPitch  | int16_t  | 2 Byte   | -32,768 ~ 32,767  | 자이로 Pitch   |
| gyroYaw    | int16_t  | 2 Byte   | -32,768 ~ 32,767  | 자이로 Yaw     |


<br>
<br>


<a name="Protocol_RawLineTracer"></a>
## Protocol::RawLineTracer

라인트레이서 RAW 데이터

```cpp
namespace Protocol
{
    struct RawLineTracer
    {
        s16         frontH;         // Front H raw data
        s8          frontS;         // Front S raw data
        s8          frontV;         // Front V raw data
        
        u8          sequence;       // 시퀀스
        s8          accel;          // accel
        s8          wheel;          // wheel
        
        u8          color;          // color
    };
}
```

| 변수 이름     | 형식        | 크기     | 범위                | 설명                      |
|:-------------:|:-----------:|:--------:|:-------------------:|:--------------------------|
| frontH        | uint16_t    | 2 Byte   | 0 ~ 360             | Front H raw data          |
| frontS        | int8_t      | 1 Byte   |                     | Front S raw data          |
| frontV        | int8_t      | 1 Byte   |                     | Front V raw data          |
| sequence      | uint8_t     | 1 Byte   |                     | 시퀀스                    |
| accel         | int8_t      | 1 Byte   |                     | accel                     |
| wheel         | int8_t      | 1 Byte   |                     | wheel                     |
| color         | uint8_t     | 1 Byte   |                     | color                     |


<br>
<br>


<a name="Protocol_State"></a>
## Protocol::State

현재 상태

```cpp
namespace Protocol
{
    struct State
    {
        u8      modeDrone;      // 드론 동작 모드
        u8      modeDrive;      // 주행 모드
        
        u16     irFrontLeft;    // 정면 좌측 거리센서
        u16     irFrontRight;   // 정면 우측 거리센서
        
        u8      colorFront;     // 바닥 앞 부분 색상(RGB)
        u8      colorRear;      // 바닥 뒷 부분 색상(RGB)
        u8      card;           // 식별한 카드(상위 4비트는 front, 하위 4비트는 rear 색상)

        u8      battery;        // 배터리
        s8      rssi;           // RSSI
    };
}
```

| 변수 이름         | 형식                                                      | 크기     | 범위       | 설명                    |
|:-----------------:|:---------------------------------------------------------:|:--------:|:----------:|:------------------------|
| modeDrone         | [Mode::Drone::Type](04_definitions.md#Mode_Drone)         | 1 Byte   | -          | 드론 동작 모드          |
| modeDrive         | [Mode::Drive::Type](04_definitions.md#Mode_Drive)         | 1 Byte   | -          | 주행 모드               |
| irFrontLeft       | uint16_t                                                  | 2 Byte   | 0 ~ 4,096  | 정면 좌측 거리센서(Raw) |
| irFrontRight      | uint16_t                                                  | 2 Byte   | 0 ~ 4,096  | 정면 우측 거리센서(Raw) |
| colorFront        | [CardColor::Type](04_definitions.md#CardColor)            | 1 Byte   | -          | 바닥 앞 부분 색상(RGB)  |
| colorRear         | [CardColor::Type](04_definitions.md#CardColor)            | 1 Byte   | -          | 바닥 뒷 부분 색상(RGB)  |
| card              | [CardNameColor::Type](04_definitions.md#CardNameColor), <br>[CardNameFunction::Type](04_definitions.md#CardNameFunction)  | 1 Byte   | -  | 식별한 카드  |
| battery           | uint8_t                                                   | 1 Byte   | 0 ~ 100    | 배터리                  |
| rssi              | int8_t                                                    | 1 Byte   | -127 ~ 0   | 신호 세기               |


<br>
<br>


<a name="Protocol_Attitude"></a>
## Protocol::Attitude

자세

```cpp
namespace Protocol
{
    struct Attitude
    {
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
    };
}
```

| 변수 이름  | 형식       | 크기     | 범위              | 설명       |
|:----------:|:----------:|:--------:|:-----------------:|:-----------|
| roll       | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Roll       |
| pitch      | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Pitch      |
| yaw        | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Yaw        |


자세를 확인할 때 값의 범위는 다음과 같습니다.

|이름      | 형식     | 크기     | 범위        | 설명                |
|:--------:|:--------:|:--------:|:-----------:|:-------------------:|
| roll     | int16_t  | 2 Byte   |  -90 ~  90  | 좌우 기울기 각도    |
| pitch    | int16_t  | 2 Byte   |  -90 ~  90  | 전후 기울기 각도    |
| yaw      | int16_t  | 2 Byte   | -180 ~ 180  | 좌우 회전 시 각도   |


<br>
<br>


<a name="Protocol_Position"></a>
## Protocol::Position

위치

```cpp
namespace Protocol
{
    struct Position
    {
        float       x;      // meter
        float       y;      // meter
        float       z;      // meter
    };
}
```


| 변수 이름     | 형식   | 크기     | 범위             | 단위     | 설명                 |
|:-------------:|:------:|:--------:|:----------------:|:---------|:---------------------|
| x             | float  | 4 Byte   | -100.0 ~ 100.0   | meter    | 앞(+), 뒤(-)         |
| y             | float  | 4 Byte   | -100.0 ~ 100.0   | meter    | 좌(+), 우(-)         |
| z             | float  | 4 Byte   | -100.0 ~ 100.0   | meter    | 위(+), 아래(-)       |


<br>
<br>


<a name="Protocol_Motion"></a>
## Protocol::Motion

Motion 센서 데이터와 자세

```cpp
namespace Protocol
{
    struct Motion
    {
        s16     accX;
        s16     accY;
        s16     accZ;

        s16     gyroRoll;
        s16     gyroPitch;
        s16     gyroYaw;

        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;
    };
}
```

| 변수 이름  | 형식     | 크기    | 범위                                | 단위                 | 설명          |
|:----------:|:--------:|:-------:|:-----------------------------------:|:--------------------:|:--------------|
| accelX     | int16_t  | 2 Byte  | -1,568 ~ 1,568<br>(-156.8 ~ 156.8)  | m/s<sup>2</sup> x 10 | 가속도 X      |
| accelY     | int16_t  | 2 Byte  | -1,568 ~ 1,568<br>(-156.8 ~ 156.8)  | m/s<sup>2</sup> x 10 | 가속도 Y      |
| accelZ     | int16_t  | 2 Byte  | -1,568 ~ 1,568<br>(-156.8 ~ 156.8)  | m/s<sup>2</sup> x 10 | 가속도 Z      |
| gyroRoll   | int16_t  | 2 Byte  | -2,000 ~ 2,000                      | degree/s             | 자이로 Roll   |
| gyroPitch  | int16_t  | 2 Byte  | -2,000 ~ 2,000                      | degree/s             | 자이로 Pitch  |
| gyroYaw    | int16_t  | 2 Byte  | -2,000 ~ 2,000                      | degree/s             | 자이로 Yaw    |
| angleRoll  | int16_t  | 2 Byte  | -180 ~ 180                          | degree               | 자세 Roll     |
| anglePitch | int16_t  | 2 Byte  | -180 ~ 180                          | degree               | 자세 Pitch    |
| angleYaw   | int16_t  | 2 Byte  | -180 ~ 180                          | degree               | 자세 Yaw      |


<br>
<br>


<a name="Protocol_Range"></a>
## Protocol::Range

Range 센서 데이터 출력

```cpp
namespace Protocol
{
    struct Range
    {
        s16     left;
        s16     front;
        s16     right;
        s16     rear;
        s16     top;
        s16     bottom;
    };
}
```

| 변수 이름  | 형식     | 크기    | 범위            | 단위      | 설명                                      |
|:----------:|:--------:|:-------:|:---------------:|:---------:|:------------------------------------------|
| left       | int16_t  | 2 Byte  | 0 ~ 2,000       | mm        | 왼쪽을 바라보는 거리 센서의 출력 값       |
| front      | int16_t  | 2 Byte  | 0 ~ 2,000       | mm        | 정면을 바라보는 거리 센서의 출력 값       |
| right      | int16_t  | 2 Byte  | 0 ~ 2,000       | mm        | 오른쪽을 바라보는 거리 센서의 출력 값     |
| rear       | int16_t  | 2 Byte  | 0 ~ 2,000       | mm        | 뒤를 바라보는 거리 센서의 출력 값         |
| top        | int16_t  | 2 Byte  | 0 ~ 2,000       | mm        | 위쪽를 바라보는 거리 센서의 출력 값       |
| bottom     | int16_t  | 2 Byte  | 0 ~ 2,000       | mm        | 아래쪽을 바라보는 거리 센서의 출력 값     |


<br>
<br>


<a name="Protocol_Count"></a>
## Protocol::Count

카운트

주행 시간 및 관련 카운트 값을 읽을 때 사용합니다.

```cpp
namespace Protocol
{
    struct Count
    {
        u32     timeSystem;             // 시스템 동작 시간
        u32     timeDrive;              // 주행 시간

        u16     countStart;             // 시작 횟수
        u16     countStop;              // 정지 횟수
        u16     countAccident;          // 충돌 횟수
    };
}
```

| 변수 이름        | 형식       | 크기     | 범위       | 설명                  |
|:----------------:|:----------:|:--------:|:----------:|:----------------------|
| timeSystem       | uint32_t   | 4 Byte   | -          | 시스템 동작 시간(sec) |
| timeDrive        | uint32_t   | 4 Byte   | -          | 주행 시간(sec)        |
| countStart       | uint16_t   | 2 Byte   | 0 ~ 65,535 | 시작 횟수             |
| countStop        | uint16_t   | 2 Byte   | 0 ~ 65,535 | 정지 횟수             |
| countAccident    | uint16_t   | 2 Byte   | 0 ~ 65,535 | 충돌 횟수             |


<br>
<br>


<a name="Protocol_Bias"></a>
## Protocol::Bias

바이어스

```cpp
namespace Protocol
{
    struct Bias
    {
        s16     accelX;         // X
        s16     accelY;         // Y
        s16     accelZ;         // Z

        s16     gyroRoll;       // Roll
        s16     gyroPitch;      // Pitch
        s16     gyroYaw;        // Yaw
    };
}
```

| 변수 이름  | 형식       | 크기     | 범위              | 설명        |
|:----------:|:----------:|:--------:|:-----------------:|:------------|
| accelX     | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Accel X     |
| accelY     | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Accel Y     |
| accelZ     | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Accel Z     |
| gyroRoll   | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Gyro Roll   |
| gyroPitch  | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Gyro Pitch  |
| gyroYaw    | int16_t    | 2 Byte   | -32,768 ~ 32,767  | Gyro Yaw    |


<br>
<br>


<a name="Protocol_Trim"></a>
## Protocol::Trim

Trim

```cpp
namespace Protocol
{
    struct Trim
    {
        s16     wheel;      // Wheel
    };
}
```

| 변수 이름 | 형식     | 크기     | 범위         | 설명       |
|:---------:|:--------:|:--------:|:------------:|:-----------|
| wheel     | int16_t  | 2 Byte   | -200 ~ 200   | Wheel      |


<br>
<br>


<a name="Protocol_Motor"></a>
## Protocol::Motor

모터

모터를 동시에 작동시키거나, 현재 모터에 입력된 값을 확인할 때 사용합니다.

아래의 구조체를 배열로 사용합니다.

```cpp
namespace Protocol
{
    struct Motor
    {
        u8      rotation;
        s16     value;
    };
}
```

| 변수 이름  | 형식                                          | 크기     | 범위      | 설명      |
|:----------:|:---------------------------------------------:|:--------:|:---------:|:----------|
| rotation   | [Rotation::Type](04_definitions.md#Rotation)  | 1 Byte   | -         | 회전 방향 |
| value      | uint16_t                                      | 2 Byte   | 0 ~ 4,095 | 회전 속도 |


<br>
<br>


<a name="Protocol_MotorSingle"></a>
## Protocol::MotorSingle

한 개의 모터 제어

하나의 모터를 동작시키거나, 현재 모터에 입력된 값을 확인할 때 사용합니다.

```cpp
namespace Protocol
{
    struct MotorSingle
    {
        u8      target;
        u8      rotation;
        s16     value;
    };
}
```

| 변수 이름  | 형식                                               | 크기     | 범위      | 설명            |
|:----------:|:--------------------------------------------------:|:--------:|:---------:|:----------------|
| target     | [Motor::Part::Type](04_definitions.md#Motor_Part)  | 1 Byte   | 0 ~ 3     | 동작 대상 모터  |
| rotation   | [Rotation::Type](04_definitions.md#Rotation)       | 1 Byte   | -         | 회전 방향       |
| value      | uint16_t                                           | 2 Byte   | 0 ~ 4,095 | 회전 속도       |


<br>
<br>


<a name="Protocol_Buzzer"></a>
## Protocol::Buzzer

버저

```cpp
namespace Protocol
{
    struct Buzzer
    {
        u8      mode;   // 버저 작동 모드
        u16     value;  // Scale 또는 hz
        u16     time;   // 연주 시간(ms)
    };
}
```

| 변수 이름  | 형식                                                    | 크기   | 범위        | 설명                   |
|:----------:|:-------------------------------------------------------:|:------:|:-----------:|:-----------------------|
| mode       | [Buzzer::Mode::Type](04_definitions.md#Buzzer_Mode)     | 1 Byte | -           | 버저 동작 모드         |
| value      | [Buzzer::Scale::Type](04_definitions.md#Buzzer_Scale)   | 2 Byte | -           | Scale                  |
|            | UInt16                                                  | 2 Byte | 0 ~ 8,000   | Hz                     |
| time       | UInt16                                                  | 2 Byte | 0 ~ 65,535  | 소리를 지속할 시간(ms) |


<br>
<br>


<a name="Protocol_BuzzerMelody"></a>
## Protocol::BuzzerMelody

버저 멜로디

버저에 예약 가능한 소리의 갯수는 64개입니다. 멜로디에 따라 짧은 멜로디는 여러번 반복이 가능하나 여러개의 음이 담긴 멜로디는 몇 회 이내에서만 정상적으로 동작합니다.

```cpp
namespace Protocol
{
    struct BuzzerMelody
    {
        u8      melody;   // 멜로디 종류
        u8      repeat;   // 반복 횟수
    };
}
```

| 변수 이름  | 형식                                                      | 크기   | 범위    | 설명                                       |
|:----------:|:---------------------------------------------------------:|:------:|:-------:|:-------------------------------------------|
| melody     | [Buzzer::Melody::Type](04_definitions.md#Buzzer_Melody)   | 1 Byte | -       | 멜로디 종류                                |
| repeat     | UInt8                                                     | 1 Byte | 0 ~ 10  | 소리의 길이에 따라 반복 가능한 횟수가 다름 |


<br>
<br>


<a name="Protocol_Button"></a>
## Protocol::Button

버튼

```cpp
namespace Protocol
{
    struct Button
    {
        u16     button;
        u8      event;
    };
}
```

| 변수 이름 | 형식                                                  | 크기     | 범위  | 설명         |
|:---------:|:-----------------------------------------------------:|:--------:|:-----:|:-------------|
| button    | uint16_t                                              | 2 Byte   | -     | 버튼 입력    |
| event     | [Button::Event::Type](04_definitions.md#Button_Event) | 1 Byte   | -     | 버튼 이벤트  |


<br>
<br>


<a name="Protocol_InformationAssembledForController"></a>
## Protocol::InformationAssembledForController

자주 갱신되는 데이터 모음(조종기)

조종기에 표시되는 데이터의 갱신 속도를 높일 목적으로 여러 데이터를 하나로 합친 구조체

```cpp
namespace Protocol
{
    struct InformationAssembledForController
    {
        s16     angleRoll;              // 자세 Roll
        s16     anglePitch;             // 자세 Pitch
        s16     angleYaw;               // 자세 Yaw

        u16     rpm;                    // RPM

        s16     positionX;              // meter x 10
        s16     positionY;              // meter x 10
        s16     positionZ;              // meter x 10

        s8      speedX;                 // meter x 10
        s8      speedY;                 // meter x 10

        u8      rangeHeight;            // meter x 100

        s8      rssi;                   // RSSI
    };
}
```


<br>
<br>


<a name="Protocol_InformationAssembledForEntry"></a>
## Protocol::InformationAssembledForEntry

자주 갱신되는 데이터 모음(엔트리)

```cpp
namespace Protocol
{
    struct InformationAssembledForEntry
    {
        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;

        float   pressureTemperature;
        float   pressureAltitude;

        float   positionX;
        float   positionY;

        float   rangeHeight;
    };
}
```


<br>
<br>


<a name="Protocol_InformationAssembledForByBlocks"></a>
## Protocol::InformationAssembledForByBlocks

자주 갱신되는 데이터 모음(바이블럭)

```cpp
namespace Protocol
{
    struct InformationAssembledForByBlocks
    {
        s8          battery;            // 배터리 잔량
        
        s16         angleRoll;          // 자세 Roll
        s16         anglePitch;         // 자세 Pitch
        s16         angleYaw;           // 자세 Yaw
        
        s16         positionX;          // meter x 10
        s16         positionY;          // meter x 10
        s16         positionZ;          // meter x 10
        
        s16         rangeLeft;          // meter x 1000
        s16         rangeFront;         // meter x 1000
        s16         rangeRight;         // meter x 1000
        s16         rangeBottom;        // meter x 1000
    };
}
```


<br>

---

<h3>E-DRIVE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Structs***
6. [Structs - Light](06_structs_light.md)
7. [Structs - Card](07_structs_card.md)

<br>

[Index](index.md)
