**[CODING RIDER](index.md)** / **Protocol** / **Structs**

Modified : 2023.7.1

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

```cpp
namespace Protocol
{
    struct Error
    {

    };
}
```

| 변수 이름     | 형식                                                          | 크기     | 범위  | 설명                  |
|:-------------:|:-------------------------------------------------------------:|:--------:|:-----:|:----------------------|


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

| 변수 이름     | 형식                                                 | 크기     | 범위 | 설명                |
|:-------------:|:-----------------------------------------------------|:--------:|:----:|:--------------------|
| modeUpdate    | [Mode::Update::Type](04_definitions.md#Mode_Update)  | 1 Byte   | -    | 업데이트 모드       |
| modelNumber   | [ModelNumber::Type](04_definitions.md#ModelNumber)   | 4 Byte   | -    | 모델 번호           |
| version       | [Protocol::Version](#Protocol_Version)               | 4 Byte   | -    | 펌웨어의 버전       |
| year          | uint16_t                                             | 2 Byte   | -    | 펌웨어 빌드 년      |
| month         | uint8_t                                              | 1 Byte   | -    | 펌웨어 빌드 월      |
| day           | uint8_t                                              | 1 Byte   | -    | 펌웨어 빌드 일      |


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

| 변수 이름  | 형식         | 크기     | 범위       | 설명         |
|:----------:|:------------:|:--------:|:----------:|:-------------|
| build      | uint16_t     | 14 bit   | 0 ~ 65535  | 빌드 번호    |
| minor      | uint8_t      | 1 Byte   | 0 ~ 255    | 부 번호      |
| major      | uint8_t      | 1 Byte   | 0 ~ 255    | 주 번호      |
| v          | uint32_t     | 4 Byte   | -          | build, minor, major를 하나로 묶은 것  |



<br>
<br>


<a name="Control_Quad8"></a>
## Control::Quad8

드론

```cpp
namespace Control
{
    struct Quad8
    {
        s8      roll;       // roll
        s8      pitch;      // pitch
        s8      yaw;        // yaw
        s8      throttle;   // throttle
    };
}
```

| 변수 이름 | 형식     | 크기     | 범위         | 설명       | 음수 값(-) | 양수 값(+)    |
|:---------:|:--------:|:--------:|:------------:|:-----------|:----------:|:-------------:|
| roll      | int8_t   | 1 Byte   | -100 ~ 100   | 좌우       | 좌측       | 우측          |
| pitch     | int8_t   | 1 Byte   | -100 ~ 100   | 전후       | 후방       | 전방          |
| yaw       | int8_t   | 1 Byte   | -100 ~ 100   | 좌우 회전  | 시계 방향  | 반시계 방향   |
| throttle  | int8_t   | 1 Byte   | -100 ~ 100   | 승하강     | 하강       | 상승          |


<br>
<br>


<a name="Control_Quad8AndRequestData"></a>
## Control::Quad8AndRequestData

드론 조종 및 데이터 요청

조종 명령 시 응답 데이터로 Ack 대신 요청한 데이터를 응답으로 보내게 함.

```cpp
namespace Control
{
    struct Quad8AndRequestData
    {
        s8      roll;       // roll
        s8      pitch;      // pitch
        s8      yaw;        // yaw
        s8      throttle;   // throttle

        u8      dataType;   // DataType
    };
}
```

| 변수 이름 | 형식     | 크기     |범위          | 설명       | 음수 값(-) | 양수 값(+)    |
|:---------:|:--------:|:--------:|:------------:|:-----------|:----------:|:-------------:|
| roll      | int8_t   | 1 Byte   | -100 ~ 100   | 좌우       | 좌측       | 우측          |
| pitch     | int8_t   | 1 Byte   | -100 ~ 100   | 전후       | 후방       | 전방          |
| yaw       | int8_t   | 1 Byte   | -100 ~ 100   | 좌우 회전  | 시계 방향  | 반시계 방향   |
| throttle  | int8_t   | 1 Byte   | -100 ~ 100   | 승하강     | 하강       | 상승          |
| dataType  | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType) | - | 1 Byte | 요청할 데이터 타입 | - | - |


<br>
<br>


<a name="Control_Position"></a>
## Control::Position

드론 이동 명령

드론에 이동 명령을 내리는 경우 사용

```cpp
namespace Control
{
    struct Position
    {
        float       positionX;              // meter
        float       positionY;              // meter
        float       positionZ;              // meter
        float       velocity;               // m/s
        
        s16         heading;                // degree
        s16         rotationalVelocity;     // deg/s
    };
}
```


| 변수 이름             | 형식     | 크기     | 범위           | 단위     | 설명                 |
|:---------------------:|:--------:|:--------:|:--------------:|:---------|:---------------------|
| positionX             | float    | 4 Byte   | -10.0 ~ 10.0   | meter    | 앞(+), 뒤(-)         |
| positionY             | float    | 4 Byte   | -10.0 ~ 10.0   | meter    | 좌(+), 우(-)         |
| positionZ             | float    | 4 Byte   | -10.0 ~ 10.0   | meter    | 위(+), 아래(-)       |
| velocity              | float    | 4 Byte   | 0.0 ~ 5.0      | m/s      | 앞뒤 이동 속도       |
| heading               | int16_t  | 2 Byte   | -360 ~ 360     | degree   | 반시계방향(+), 시계방향(-) |
| rotationalVelocity    | int16_t  | 2 Byte   | 10 ~ 180       | degree/s | 좌우 회전 속도       |


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
| option      | [Mode::Control::Flight::Type](04_definitions.md#Mode_Control_Flight)    | 1 Byte   | -       | 옵션         |
|             | [Escape::Type](04_definitions.md#Escape)                                |          | -       |              |
|             | [System::FlightEvent::Type](04_definitions.md#FlightEvent)              |          | -       |              |
|             | [System::Trim::Type](04_definitions.md#Trim)                            |          | -       |              |
|             | [Mode::Controller::Type](04_definitions.md#Mode_Controller)             |          | -       |              |
|             | uint8_t                                                                 |          | -       |              |


<br>
<br>


<a name="Protocol_ResponseRate"></a>
## Protocol::ResponseRate

RF 송수신 응답률 (조종기에서만 받을수 있음)

```cpp
namespace Protocol
{
    struct ResponseRate
    {
        u8	responseRate;
    };
}
```

| 변수 이름         | 형식                                                                  | 크기     | 범위     | 설명                   |
|:-----------------:|:---------------------------------------------------------------------:|:--------:|:--------:|:-----------------------|
| responseRate      | uint8_t                                                               | 1 Byte   | 0 ~ 100  | 송수신 응답률          |


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
| accelX     | Int16    | 2 Byte   | -32,768 ~ 32,767  | 가속도 X       |
| accelY     | Int16    | 2 Byte   | -32,768 ~ 32,767  | 가속도 Y       |
| accelZ     | Int16    | 2 Byte   | -32,768 ~ 32,767  | 가속도 Z       |
| gyroRoll   | Int16    | 2 Byte   | -32,768 ~ 32,767  | 자이로 Roll    |
| gyroPitch  | Int16    | 2 Byte   | -32,768 ~ 32,767  | 자이로 Pitch   |
| gyroYaw    | Int16    | 2 Byte   | -32,768 ~ 32,767  | 자이로 Yaw     |


<br>
<br>


<a name="Protocol_State"></a>
## Protocol::State

드론의 현재 상태

```cpp
namespace Protocol
{
    struct State
    {
        u8      modeSystem;         // 시스템 모드
        u8      modeFlight;         // 비행 모드

        u8      modeControlFlight;  // 비행 제어 모드
        u8      modeMovement;       // 이동 상태
        u8      Escape;             // Escape 모드
        u8      controlSpeed;       // 제어 속도
        u8      sensorOrientation;  // 센서 방향
        u8      battery;            // 배터리량(0 ~ 100%)
    };
}
```

| 변수 이름         | 형식                                                                  | 크기     | 범위     | 설명                   |
|:-----------------:|:---------------------------------------------------------------------:|:--------:|:--------:|:-----------------------|
| modeSystem        | [Mode::System::Type](04_definitions.md#Mode_System)                   | 1 Byte   | -        | System 동작 모드       |
| modeFlight        | [Mode::Flight::Type](04_definitions.md#Mode_Flight)                   | 1 Byte   | -        | 비행 제어기 동작 모드  |
| modeControlFlight | [Mode::Control::Flight::Type](04_definitions.md#Mode_Control_Flight)  | 1 Byte   | -        | 비행 제어 모드         |
| modeMovement      | [Mode::Movement::Type](04_definitions.md#Mode_Movement)               | 1 Byte   | -        | 이동 상태              |
| escape              | [Escape::Type](04_definitions.md#escape)                          | 1 Byte   | -        | escape 설정 상태       |
| controlSpeed      | uint8_t                                                               | 1 Byte   | -        | 제어 속도(1, 2, 3)     |
| sensorOrientation | [SensorOrientation::Type](04_definitions.md#SensorOrientation)        | 1 Byte   | -        | 센서 방향              |
| battery           | uint8_t                                                               | 1 Byte   | 0 ~ 100  | 드론 배터리 잔량       |


<br>
<br>


<a name="Protocol_Altitude"></a>
## Protocol::Altitude

고도

```cpp
namespace Protocol
{
    struct Altitude
    {
        f32   temperature;
        f32   pressure;
        f32   altitude;
        f32   rangeHeight;
    };
}
```

| 변수 이름     | 형식     | 크기     | 범위              | 설명                |
|:-------------:|:--------:|:--------:|:-----------------:|:--------------------|
| temperature   | float    | 4 Byte   | -                 | 온도                |
| pressure      | float    | 4 Byte   | -                 | 압력                |
| altitude      | float    | 4 Byte   | -                 | 고도                |
| rangeHeight   | float    | 4 Byte   | -                 | 거리 센서의 높이    |


<br>
<br>


<a name="Protocol_Motion"></a>
## Protocol::Motion

Motion 센서 데이터와 드론의 자세

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


<a name="Protocol_VisionSensor"></a>
## Protocol::VisionSensor

위치

```cpp
namespace Protocol
{
    struct VisionSensor
    {
        float       x;      // meter
        float       y;      // meter
        float       z;      // meter
    };
}
```


| 변수 이름 | 형식  |  크기  |      범위      | 단위  |      설명      |
| :-------: | :---: | :----: | :------------: | :---- | :------------- |
|     x     | float | 4 Byte | -100.0 ~ 100.0 | meter | 앞(+), 뒤(-)   |
|     y     | float | 4 Byte | -100.0 ~ 100.0 | meter | 좌(+), 우(-)   |
|     z     | float | 4 Byte |   0 ~ 4.0      | meter | 거리 센서의 값 |





<a name="Protocol_Count"></a>
## Protocol::Count

카운트

비행 시간 및 관련 카운트 값을 읽을 때 사용합니다.

```cpp
namespace Protocol
{
    struct Count
    {
        u32     timeSystem;             // 시스템 동작 시간
        u32     timeFlight;             // 비행 시간

        u16     countTakeOff;           // 이륙 횟수
        u16     countLanding;           // 착륙 횟수
        u16     countAccident;          // 충돌 횟수
    };
}
```

| 변수 이름        | 형식       | 크기     | 범위       | 설명                  |
|:----------------:|:----------:|:--------:|:----------:|:----------------------|
| timeSystem       | uint32_t   | 4 Byte   | -          | 시스템 동작 시간(sec) |
| timeFlight       | uint32_t   | 4 Byte   | -          | 비행 시간(sec)        |
| countTakeOff     | uint16_t   | 2 Byte   | 0 ~ 65,535 | 이륙 횟수             |
| countLanding     | uint16_t   | 2 Byte   | 0 ~ 65,535 | 착륙 횟수             |
| countAccident    | uint16_t   | 2 Byte   | 0 ~ 65,535 | 충돌 횟수             |


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
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
        s16     throttle;     // Throttle
    };
}
```

| 변수 이름 | 형식     | 크기     | 범위         | 설명       |
|:---------:|:--------:|:--------:|:------------:|:-----------|
| roll      | int16_t  | 2 Byte   | -200 ~ 200   | Roll       |
| pitch     | int16_t  | 2 Byte   | -200 ~ 200   | Pitch      |
| yaw       | int16_t  | 2 Byte   | -200 ~ 200   | Yaw        |
| throttle  | int16_t  | 2 Byte   | -200 ~ 200   | Throttle   |


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
|            | uint16_t                                                | 2 Byte | 0 ~ 8,000   | Hz                     |
| time       | uint16_t                                                | 2 Byte | 0 ~ 65,535  | 소리를 지속할 시간(ms) |


<br>
<br>


<a name="Protocol_Joystick"></a>
## Protocol::Joystick

조종기 좌우 조이스틱의 입력 값

```cpp
namespace Protocol
{
    struct Joystick
    {
        Protocol::JoystickBlock     left;
        Protocol::JoystickBlock     right;
    };
}
```

| 변수 이름 | 형식                                                | 크기     | 범위  | 설명            |
|:---------:|:---------------------------------------------------:|:--------:|:-----:|:----------------|
| left      | [Protocol::JoystickBlock](#Protocol_JoystickBlock)  | 4 Byte   | -     | 왼쪽 조이스틱   |
| right     | [Protocol::JoystickBlock](#Protocol_JoystickBlock)  | 4 Byte   | -     | 오른쪽 조이스틱 |


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
        s16     angleRoll;      // 자세 Roll
        s16     anglePitch;     // 자세 Pitch
        s16     angleYaw;       // 자세 Yaw

        u16     rpm;            // RPM

        s16     positionX;      // meter x 10
        s16     positionY;      // meter x 10
        s16     positionZ;      // meter x 10

        s8      speedX;         // meter x 10
        s8      speedY;         // meter x 10

        u8      rangeHeight;    // meter x 100

        s8      responseRate;   // 송수신 응답률
    };
}
```


<br>

---

<h3>SKYKICK EVOLUTION</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Structs***
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
