**[PETRONE_V2](index.md)** / **Protocol** / **Structs**

Modified : 2018.3.6

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

| 변수 이름 | 형식                                                                 | 범위      | 크기     | 설명                     |
|:---------:|:--------------------------------------------------------------------:|:---------:|:--------:|:-------------------------|
| dataType  | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)         | -         | 1 Byte   | 데이터의 타입            |
| length    | uint8_t                                                              | 0 ~ 255   | 1 Byte   | 데이터의 길이            |
| from      | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType)  | -         | 1 Byte   | 데이터를 전송하는 장치   |
| to        | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType)  | -         | 1 Byte   | 데이터를 수신하는 장치   |


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

| 변수 이름   | 형식        | 범위  | 크기     | 설명           |
|:-----------:|:-----------:|:-----:|:--------:|:---------------|
| systemTime  | uint64_t    | -     | 8 Byte   | 시스템 시간    |


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

| 변수 이름    | 형식                                                         | 범위   | 크기     | 설명                                |
|:------------:|:------------------------------------------------------------:|:------:|:--------:|:------------------------------------|
| systemTime   | uint64_t                                                     | -      | 8 Byte   | 시스템 시간                         |
| dataType     | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType) | -      | 1 Byte   | 수신 받은 데이터 타입               |
| crc16        | uint16_t                                                     | -      | 2 Byte   | 수신 받은 헤더와 데이터의 CRC16 값  |


<br>
<br>


<a name="Protocol_Error"></a>
## Protocol::Error

오류

드론에 문제가 생긴 경우 Error 구조체를 600ms에 한 번 RF를 통해 송신합니다.

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

| 변수 이름            | 형식                                                                | 범위   | 크기     | 설명                    |
|:--------------------:|:-------------------------------------------------------------------:|:------:|:--------:|:------------------------|
| systemTime           | uint64_t                                                            | -      | 8 Byte   | 시스템 시간             |
| errorFlagsForSensor  | [ErrorFlagsForSensor::Type](04_definitions.md#ErrorFlagsForSensor)  | -      | 4 Byte   | 센서 오류 플래그 조합   |
| errorFlagsForState   | [ErrorFlagsForState::Type](04_definitions.md#ErrorFlagsForState)    | -      | 4 Byte   | 상태 오류 플래그 조합   |


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

| 변수 이름     | 형식                                                          | 범위  | 크기     | 설명                  |
|:-------------:|:-------------------------------------------------------------:|:-----:|:--------:|:----------------------|
| dataType      | [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)  | -     | 1 Byte   | 요청할 데이터 타입    |


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
        u8      modeUpdate;     // 현재 업데이트 모드

        u32     deviceType;     // 장치 타입
        u32     imageVersion;   // 현재 펌웨어의 버전

        u16     year;           // 빌드 년
        u8      month;          // 빌드 월
        u8      day;            // 빌드 일
    };
}
```

| 변수 이름     | 형식                                                                | 범위 | 크기     | 설명                |
|:-------------:|:-------------------------------------------------------------------:|:----:|:--------:|:--------------------|
| modeUpdate    | [Mode::Update::Type](04_definitions.md#Mode_Update)                 | -    | 1 Byte   | 업데이트 진행 상황  |
| deviceType    | [Protocol::DeviceType::Type](04_definitions.md#Protocol_DeviceType) | -    | 1 Byte   | 장치의 타입         |
| version       | [Protocol::Version](#Protocol_Version)                              | -    | 4 Byte   | 펌웨어의 버전       |
| year          | uint16_t                                                            | -    | 2 Byte   | 펌웨어 빌드 년      |
| month         | uint8_t                                                             | -    | 1 Byte   | 펌웨어 빌드 월      |
| day           | uint8_t                                                             | -    | 1 Byte   | 펌웨어 빌드 일      |


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
            u16                     build:14;   // Build Number(0~16383)
            DevelopmentStage::Type  stage:2;    // Development stage(0~3)
            u8                      minor;      // Minor Number
            u8                      major;      // Major Number
        };

        u32 v;
    };
}
```

| 변수 이름  | 형식                                                           | 범위       | 크기     | 설명         |
|:----------:|:--------------------------------------------------------------:|:----------:|:--------:|:-------------|
| build      | uint16_t                                                       | 0 ~ 16383  | 14 bit   | 빌드 번호    |
| stage      | [Protocol::DevelopmentStage::Type](#Protocol_DevelopmentStage) | -          | 2 bit    | 개발 단계    |
| minor      | uint8_t                                                        | 0 ~ 255    | 1 Byte   | 부 번호      |
| major      | uint8_t                                                        | 0 ~ 255    | 1 Byte   | 주 번호      |
| v          | uint32_t                                                       | -          | 4 Byte   | build, stage, minor, major를 하나로 묶은 것  |


<br>
<br>


<a name="Protocol_DevelopmentStage"></a>
## Protocol::DevelopmentStage::Type

펌웨어 개발 단계

```cpp
namespace Protocol
{
    namespace DevelopmentStage
    {
        enum Type
        {
            Alpha,
            Beta,
            ReleaseCandidate,
            Release
        };
    }
}
```


<br>
<br>


<a name="Control_Double8"></a>
## Control::Double8

자동차 조종

드론 모드일 때 이 명령을 전송하면 무시합니다.

```cpp
namespace Control
{
    struct Double8
    {
        s8      wheel;      // wheel
        s8      accel;      // accel
    };
}
```

Control::Double8 입력 값의 범위는 다음과 같습니다

| 변수 이름  | 형식   | 범위       | 크기     | 설명         | 음수 값(-) | 양수 값(+)    |
|:----------:|:------:|:----------:|:--------:|:-------------|:----------:|:-------------:|
| wheel      | int8_t | -100 ~ 100 | 1 Byte   | 좌우 회전    | 좌회전     | 우회전        |
| accel      | int8_t | -100 ~ 100 | 1 Byte   | 전후진       | 후진       | 전진          |


<br>
<br>


<a name="Control_Quad8"></a>
## Control::Quad8

드론 및 자동차 조종

Drive 모드에서는 **throttle**(전후)과 **roll**(좌우)만 사용합니다.

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

| 변수 이름 | 형식     | 범위         | 크기     | 설명       | 음수 값(-) | 양수 값(+)    |
|:---------:|:--------:|:------------:|:--------:|:-----------|:----------:|:-------------:|
| roll      | int8_t   | -100 ~ 100   | 1 Byte   | 좌우       | 좌측       | 우측          |
| pitch     | int8_t   | -100 ~ 100   | 1 Byte   | 전후       | 후방       | 전방          |
| yaw       | int8_t   | -100 ~ 100   | 1 Byte   | 좌우 회전  | 반시계     | 시계 방향     |
| throttle  | int8_t   | -100 ~ 100   | 1 Byte   | 승하강     | 하강       | 상승          |


<br>
<br>


<a name="Protocol_Command"></a>
## Protocol::Command

설정 변경

```cpp
namespace Protocol
{
    struct Command
    {
        u8      commandType;   // 명령 타입
        u8      option;        // 명령에 대한 옵션
    };
}
```

| 변수 이름   | 형식                                                                    | 범위    | 크기     | 설명         |
|:-----------:|:-----------------------------------------------------------------------:|:-------:|:--------:|:-------------|
| commandType | [Protocol::CommandType::Type](04_definitions.md#Protocol_CommandType)   | -       | 1 Byte   | 명령 타입    |
| option      | [Mode::Vehicle::Type](04_definitions.md#Mode_Vehicle)                   | -       | 1 Byte   | 옵션         |
|             | [System::FlightEvent::Type](04_definitions.md#FlightEvent)              | -       |          |              |
|             | [System::DriveEvent::Type](04_definitions.md#DriveEvent)                | -       |          |              |
|             | [Coordinate::Type](04_definitions.md#Coordinate)                        | -       |          |              |
|             | [System::Trim::Type](04_definitions.md#Trim)                            | -       |          |              |
|             | uint8_t                                                                 | -       |          |              |


<br>
<br>


<a name="Protocol_Address"></a>
## Protocol::Address

장치 주소

```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[16];
    };
}
```

| 변수 이름  | 형식            | 범위  | 크기     | 설명         |
|:----------:|:---------------:|:-----:|:--------:|:-------------|
| address    | uint8_t Array   | -     | 16 Byte  | 장치 주소    |


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
        u8      modeVehicle;        // 동작 모드
        
        u8      modeSystem;         // 시스템 모드
        u8      modeFlight;         // 비행 모드
        u8      modeDrive;          // 주행 모드
        
        u8      sensorOrientation;  // 센서 방향
        u8      coordinate;         // 방위
        u8      battery;            // 배터리량(0 ~ 100%)
    };
}
```

| 변수 이름         | 형식                                                           | 범위     | 크기     | 설명                   |
|:-----------------:|:--------------------------------------------------------------:|:--------:|:--------:|:-----------------------|
| modeVehicle       | [Mode::Vehicle::Type](04_definitions.md#Mode_Vehicle)          | -        | 1 Byte   | Vehicle 동작 모드      |
| modeSystem        | [Mode::System::Type](04_definitions.md#Mode_System)            | -        | 1 Byte   | System 동작 모드       |
| modeFlight        | [Mode::Flight::Type](04_definitions.md#Mode_Flight)            | -        | 1 Byte   | 비행 제어기 동작 모드  |
| modeDrive         | [Mode::Drive::Type](04_definitions.md#Mode_Drive)              | -        | 1 Byte   | 주행 제어기 동작 모드  |
| sensorOrientation | [SensorOrientation::Type](04_definitions.md#SensorOrientation) | -        | 1 Byte   | 센서 방향              |
| coordinate        | [Coordinate::Type](04_definitions.md#Coordinate)               | -        | 1 Byte   | Coordinate 설정 상태   |
| battery           | uint8_t                                                        | 0 ~ 100  | 1 Byte   | 드론 배터리 잔량       |


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

| 변수 이름  | 형식       | 범위              | 크기     | 설명       |
|:----------:|:----------:|:-----------------:|:--------:|:-----------|
| roll       | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Roll       |
| pitch      | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Pitch      |
| yaw        | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Yaw        |


드론의 자세를 확인할 때 값의 범위는 다음과 같습니다.

|이름      | 형식     | 범위        | 설명                |
|:--------:|:--------:|:-----------:|:-------------------:|
| roll     | int16_t  |  -90 ~  90  | 좌우 기울기 각도    |
| pitch    | int16_t  |  -90 ~  90  | 전후 기울기 각도    |
| yaw      | int16_t  | -180 ~ 180  | 좌우 회전 시 각도   |


<br>
<br>


<a name="Protocol_AccelBias"></a>
## Protocol::AccelBias

엑셀 바이어스

```cpp
namespace Protocol
{
    struct AccelBias
    {
        s16     x;         // X
        s16     y;         // Y
        s16     z;         // Z
    };
}
```

| 변수 이름  | 형식       | 범위              | 크기     | 설명       |
|:----------:|:----------:|:-----------------:|:--------:|:-----------|
| x          | int16_t    | -32,768 ~ 32,767  | 2 Byte   | X          |
| y          | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Y          |
| z          | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Z          |


<br>
<br>


<a name="Protocol_GyroBias"></a>
## Protocol::GyroBias

자이로 바이어스

```cpp
namespace Protocol
{
    struct GyroBias
    {
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
    };
}
```

| 변수 이름  | 형식       | 범위              | 크기     | 설명       |
|:----------:|:----------:|:-----------------:|:--------:|:-----------|
| roll       | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Roll       |
| pitch      | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Pitch      |
| yaw        | int16_t    | -32,768 ~ 32,767  | 2 Byte   | Yaw        |


<br>
<br>


<a name="Protocol_TrimFlight"></a>
## Protocol::TrimFlight

비행 Trim

```cpp
namespace Protocol
{
    struct TrimFlight
    {
        s16     roll;         // Roll
        s16     pitch;        // Pitch
        s16     yaw;          // Yaw
        s16     throttle;     // Throttle
    };
}
```

| 변수 이름 | 형식     | 범위         | 크기     | 설명       |
|:---------:|:--------:|:------------:|:--------:|:-----------|
| roll      | int16_t  | -200 ~ 200   | 2 Byte   | Roll       |
| pitch     | int16_t  | -200 ~ 200   | 2 Byte   | Pitch      |
| yaw       | int16_t  | -200 ~ 200   | 2 Byte   | Yaw        |
| throttle  | int16_t  | -200 ~ 200   | 2 Byte   | Throttle   |


<br>
<br>


<a name="Protocol_TrimDrive"></a>
## Protocol::TrimDrive

자동차 Trim

```cpp
namespace Protocol
{
    struct TrimDrive
    {
        s16     wheel;         // Wheel
        s16     accel;         // Accel
    };
}
```

| 변수 이름 | 형식     | 범위         | 크기     | 설명    |
|:---------:|:--------:|:------------:|:--------:|:--------|
| wheel     | int16_t  | -200 ~ 200   | 2 Byte   | Wheel   |
| accel     | int16_t  | -200 ~ 200   | 2 Byte   | Accel   |


<br>
<br>


<a name="Protocol_TrimAll"></a>
## Protocol::TrimAll

비행 및 자동차 Trim

```cpp
namespace Protocol
{
    struct TrimAll
    {
        TrimFlight  flight;
        TrimDrive   drive;
    };
}
```

| 변수 이름 | 형식                                          | 범위         | 크기     | 설명       |
|:---------:|:---------------------------------------------:|:------------:|:--------:|:-----------|
| flight    | [Protocol::TrimFlight](#Protocol_TrimFlight)  | -200 ~ 200   | 2 Byte   | 비행 Trim  |
| drive     | [Protocol::TrimDrive](#Protocol_TrimDrive)    | -200 ~ 200   | 2 Byte   | 주행 Trim  |


<br>
<br>


<a name="Protocol_CountFlight"></a>
## Protocol::CountFlight

비행 카운터

비행과 관련된 저장값을 읽을 때 사용합니다.

```cpp
namespace Protocol
{
    struct CountFlight
    {
        u64     timeFlight;             // 비행 시간
        
        u16     countTakeOff;           // 이륙 횟수
        u16     countLanding;           // 착륙 횟수
        u16     countAccident;          // 충돌 횟수
    };
}
```

| 변수 이름        | 형식       | 범위       | 크기     | 설명             |
|:----------------:|:----------:|:----------:|:--------:|:-----------------|
| timeFlight       | uint64_t   | -          | 8 Byte   | 비행 시간(ms)    |
| countTakeOff     | uint16_t   | 0 ~ 65535  | 2 Byte   | 이륙 횟수        |
| countLanding     | uint16_t   | 0 ~ 65535  | 2 Byte   | 착륙 횟수        |
| countAccident    | uint16_t   | 0 ~ 65535  | 2 Byte   | 충돌 횟수        |


<br>
<br>


<a name="Protocol_CountDrive"></a>
## Protocol::CountDrive

주행 카운터

주행과 관련된 저장값을 읽을 때 사용합니다.

countAccident 변수는 주행 중 충돌을 카운트 하기 위해 만든 변수이나 실제 주행 시 노면이 고르지 못할 때의 충격에 의해서도 카운트가 증가하는 문제가 있습니다. 현재로는 크게 의미가 없는 값으로 생각하시면 됩니다.

```cpp
namespace Protocol
{
    struct CountDrive
    {
        u64     timeDrive;              // 주행 시간
        
        u16     countAccident;          // 충돌 횟수
    };
}
```

| 변수 이름     | 형식       | 범위          | 크기     | 설명           |
|:-------------:|:----------:|:-------------:|:--------:|:---------------|
| timeDrive     | uint64_t   | -             | 8 Byte   | 주행 시간(ms)  |
| countAccident | uint16_t   | 0 ~ 65,535    | 2 Byte   | 충돌 횟수      |


<br>
<br>


<a name="Protocol_IrMessage"></a>
## Protocol::IrMessage

IR 데이터 송수신

IR 데이터를 전송하는데 사용하거나, IR 데이터를 수신 받았을 때 외부 장치로 전송하는 데이터입니다.

드론 전면과 후면에 적외선 수신 센서가 각각 하나씩 설치되어 있으며, 각 방향으로 들어오는 데이터를 구분하는데 direction을 사용합니다.

```cpp
namespace Protocol
{
    struct IrMessage
    {
        u8      direction;               // 수신 받은 방향
        u32     irData;                  // IR 메세지
    };
}
```

| 변수 이름 | 형식                                                   | 범위                    | 크기   | 설명             |
|:---------:|:------------------------------------------------------:|:-----------------------:|:------:|:-----------------|
| direction | [System::Direction::Type](04_definitions.md#Direction) | -                       | 1 Byte | 적외선 수신 방향 |
| irData    | uint32_t                                               | 0x00000000 ~ 0xFFFFFFFF | 4 Byte | 데이터           |


<br>
<br>


<a name="Protocol_Imu"></a>
## Protocol::Imu

IMU 센서 데이터와 드론의 자세

```cpp
namespace Protocol
{
    struct Imu
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


<a name="Protocol_Battery"></a>
## Protocol::Battery

배터리

```cpp
namespace Protocol
{
    struct Battery
    {
        f32     gradient;
        f32     yIntercept;
        f32     adjustGradient;
        f32     adjustYIntercept;
        u8      flagBatteryCalibration;

        s16     batteryRaw;
        f32     batteryPercent;

        f32     voltage;
    };
}
```

| 변수 이름               | 형식     | 범위         | 크기     | 설명                                |
|:-----------------------:|:--------:|:------------:|:--------:|:------------------------------------|
| gradient                | float    | -            | 4 Byte   | 기울기                              |
| yIntercept              | float    | -            | 4 Byte   | Y 절편                              |
| adjustGradient          | float    | -            | 4 Byte   | 기울기 조정값                       |
| adjustYIntercept        | float    | -            | 4 Byte   | Y 절편 조정값                       |
| flagBatteryCalibration  | uint8_t  | 0 / 1        | 1 Byte   | 배터리 캘리브레이션 완료 여부       |
| batteryRaw              | uint16_t | 0 ~ 4095     | 2 Byte   | 배터리 ADC Raw 값                   |
| batteryPercent          | float    | 0 ~ 100.0    | 4 Byte   | 배터리 % 값                         |
| voltage                 | float    | 0 ~ 4.5      | 4 Byte   | 배터리 출력값을 Voltage로 변환한 값 |


<br>
<br>


<a name="Protocol_Pressure"></a>
## Protocol::Pressure

압력 센서

```cpp
namespace Protocol
{
    struct Pressure
    {
        f32     temperature;
        f32     pressure;
    };
}
```

| 변수 이름   | 형식     | 범위 | 크기     | 설명                            |
|:-----------:|:--------:|:----:|:--------:|:--------------------------------|
| temperature | float    | -    | 4 Byte   | 온도(℃)                        |
| pressure    | float    | -    | 4 Byte   | 압력을 해발고도로 변환한 값(m)  |


<br>
<br>


<a name="Protocol_ImageFlow"></a>
## Protocol::ImageFlow

ImageFlow

옵티컬 플로우로 계산한 상대 위치 값

```cpp
namespace Protocol
{
    struct ImageFlow
    {
        f32     positionX;
        f32     positionY;
    };
}
```

| 변수 이름  | 형식      | 범위  | 크기     | 설명    |
|:----------:|:---------:|:-----:|:--------:|:--------|
| positionX  | float     | -     | 4 Byte   | X축(m)  |
| positionY  | float     | -     | 4 Byte   | Y축(m)  |


<br>
<br>


<a name="Protocol_Range"></a>
## Protocol::Range

거리 센서

추가 센서 모듈을 장착하지 않으면 bottom 값만 출력됩니다.

거리 센서의 최대 정상 측정 가능 범위는 0.04m ~ 2.0m 입니다.

```cpp
namespace Protocol
{
    struct Range
    {
        f32     left;
        f32     front;
        f32     right;
        f32     rear;
        f32     top;
        f32     bottom;
    };
}
```

| 변수 이름 | 형식       | 범위    | 크기     | 설명     |
|:---------:|:----------:|:-------:|:--------:|:---------|
| left      | Float32    | -       | 4 Byte   | 좌측(m)  |
| front     | Float32    | -       | 4 Byte   | 정면(m)  |
| right     | Float32    | -       | 4 Byte   | 우측(m)  |
| rear      | Float32    | -       | 4 Byte   | 후면(m)  |
| top       | Float32    | -       | 4 Byte   | 위(m)    |
| bottom    | Float32    | -       | 4 Byte   | 아래(m)  |


<br>
<br>


<a name="Protocol_Motor"></a>
## Protocol::Motor

모터

모터를 4개를 동시에 작동시키거나, 현재 모터에 입력된 값을 확인할 때 사용합니다.

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

| 변수 이름  | 형식                                       | 범위      | 크기     | 설명      |
|:----------:|:------------------------------------------:|:---------:|:--------:|:----------|
| rotation   | [Rotation::Type](04_definitions.md#Rotation)  | -         | 1 Byte   | 회전 방향 |
| value      | uint16_t                                   | 0 ~ 4095  | 2 Byte   | 회전 속도 |


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

| 변수 이름  | 형식                                               | 범위      | 크기     | 설명            |
|:----------:|:--------------------------------------------------:|:---------:|:--------:|:----------------|
| target     | [Motor::Part::Type](04_definitions.md#Motor_Part)  | 0 ~ 3     | 1 Byte   | 동작 대상 모터  |
| rotation   | [Rotation::Type](04_definitions.md#Rotation)       | -         | 1 Byte   | 회전 방향       |
| value      | uint16_t                                           | 0 ~ 4095  | 2 Byte   | 회전 속도       |


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

| 변수 이름 | 형식                                                  | 범위  | 크기     | 설명         |
|:---------:|:-----------------------------------------------------:|:-----:|:--------:|:-------------|
| button    | uint16_t                                              | -     | 2 Byte   | 버튼 입력    |
| event     | [Button::Event::Type](04_definitions.md#Button_Event) | -     | 1 Byte   | 버튼 이벤트  |


<br>
<br>


<a name="Protocol_JoystickBlock"></a>
## Protocol::JoystickBlock

조종기 조이스틱 한 축의 입력 값

```cpp
namespace Protocol
{
    struct JoystickBlock
    {
        s8      x;
        s8      y;
        u8      direction;
        u8      event;
    };
}
```

| 변수 이름  | 형식                                                              | 범위          | 크기     | 설명             |
|:----------:|:-----------------------------------------------------------------:|:-------------:|:--------:|:-----------------|
| x          | int8_t                                                            | -100 ~ 100    | 1 Byte   | 조이스틱 가로축  |
| y          | int8_t                                                            | -100 ~ 100    | 1 Byte   | 조이스틱 세로축  |
| direction  | [Joystick::Direction::Type](04_definitions.md#Joystick_Direction) | -             | 1 Byte   | 조이스틱 방향    |
| event      | [Joystick::Event::Type](04_definitions.md#Joystick_Event)         | -             | 1 Byte   | 이벤트           |


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

| 변수 이름 | 형식                                                | 범위  | 크기     | 설명            |
|:---------:|:---------------------------------------------------:|:-----:|:--------:|:----------------|
| left      | [Protocol::JoystickBlock](#Protocol_JoystickBlock)  | -     | 4 Byte   | 왼쪽 조이스틱   |
| right     | [Protocol::JoystickBlock](#Protocol_JoystickBlock)  | -     | 4 Byte   | 오른쪽 조이스틱 |


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

| 변수 이름  | 형식                                                    | 범위        | 크기   | 설명                   |
|:----------:|:-------------------------------------------------------:|:-----------:|:------:|:-----------------------|
| mode       | [Buzzer::Mode::Type](04_definitions.md#Buzzer_Mode)     | -           | 1 Byte | 버저 동작 모드         |
| value      | [Buzzer::Scale::Type](04_definitions.md#Buzzer_Scale)   | -           | 2 Byte | Scale                  |
|            | UInt16                                                  | 0 ~ 8000    |        | Hz                     |
| time       | UInt16                                                  | 0 ~ 65,535  | 2 Byte | 소리를 지속할 시간(ms) |


<br>
<br>


<a name="Protocol_Vibrator"></a>
## Protocol::Vibrator

진동

```cpp
namespace Protocol
{
    struct Vibrator
    {
        u8      mode;   // 모드(0은 set, 1은 reserve)
        u16     on;     // 진동을 켠 시간(ms)
        u16     off;    // 진동을 끈 시간(ms)
        u16     total;  // 전체 진행 시간(ms)
    };
}
```

| 변수 이름  | 형식                                                    | 범위        | 크기     | 설명                |
|:----------:|:-------------------------------------------------------:|:-----------:|:--------:|:--------------------|
| mode       | [Vibrator::Mode::Type](04_definitions.md#Vibrator_Mode) | -           | 1 Byte   | 진동 동작 모드      |
| on         | uint16_t                                                | 0 ~ 65,535  | 2 Byte   | 진동을 켠 시간(ms)  |
| off        | uint16_t                                                | 0 ~ 65,535  | 2 Byte   | 진동을 끈 시간(ms)  |
| total      | uint16_t                                                | 0 ~ 65,535  | 2 Byte   | 전체 동작 시간(ms)  |


<br>
<br>


<a name="Protocol_Pairing"></a>
## Protocol::Pairing

페어링

장치의 페어링 정보를 확인하거나 변경할 때 사용합니다.

주소에 0x0000은 사용하지 않음, 0xFFFF는 Broadcasting.

```cpp
namespace Protocol
{
    struct Pairing
    {
        u16     addressLocal;
        u16     addressRemote;
        u8      channel;
    };
}
```

| 변수 이름       | 형식      | 범위             | 크기     | 설명               |
|:---------------:|:---------:|:----------------:|:--------:|:-------------------|
| addressLocal    | uint16_t  | 0x0001 ~ 0xFFFE  | 2 Byte   | 장치의 주소        |
| addressRemote   | uint16_t  | 0x0001 ~ 0xFFFE  | 2 Byte   | 상대 장치의 주소   |
| channel         | uint18_t  | 0 ~ 230          | 1 Byte   | 채널               |


<br>
<br>


<a name="Protocol_Rssi"></a>
## Protocol::Rssi

RSSI

Received signal strength indication

[http://www.metageek.com/training/resources/understanding-rssi.html](http://www.metageek.com/training/resources/understanding-rssi.html)

현재 무선으로 연결된 장치의 신호 세기를 반환합니다.

```cpp
namespace Protocol
{
    struct Rssi
    {
        s8     Rssi;
    };
}
```

| 변수 이름    | 형식     | 범위      | 크기     | 설명       |
|:------------:|:--------:|:---------:|:--------:|:-----------|
| rssi         | int8_t   | -100 ~ 0  | 1 Byte   | 신호 세기  |


<br>
<br>


<a name="Protocol_InformationAssembledForController"></a>
## Protocol::InformationAssembledForController

자주 갱신되는 데이터 모음(조종기)

조종기에 표시되는 데이터의 갱신 속도 향상을 위해 조종기에서 Control 명령을 드론에 RF로 전송하는 경우, 드론에서 Ack 대신 이 데이터를 응답으로 전송합니다.

```cpp
namespace Protocol
{
    struct InformationAssembledForController
    {
        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;

        float   pressureTemperature;
        float   pressureAltitude;

        float   rangeGround;
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
        s16     accelX;
        s16     accelY;
        s16     accelZ;

        s16     gyroRoll;
        s16     gyroPitch;
        s16     gyroYaw;

        s16     angleRoll;
        s16     anglePitch;
        s16     angleYaw;

        float   pressureTemperature;
        float   pressureAltitude;

        float   imageFlowPositionX;
        float   imageFlowPositionY;

        float   rangeGround;
    };
}
```


<br>

---

<h3>PETRONE V2</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Structs***
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)
