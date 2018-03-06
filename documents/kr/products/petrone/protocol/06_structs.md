***PETRONE / BLE / Protocol / Structs***<br>
Modified : 2017.10.18

---

#### 데이터 송수신 시에 사용하는 구조체들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>

## <a name="Protocol_Ping">Protocol::Ack</a>
PETRONE이 데이터를 수신 받았을 때 응답으로 보내는 데이터입니다. PETRONE의 현재 내부 시간과 수신 받은 데이터의 타입을 담아서 반환합니다. Ack와 Control을 제외한 대부분의 명령에 대해 응답으로 전송합니다.
```cpp
namespace Protocol
{
    struct Ack
    {
        u32  systemTime;    // 수신 받은 시각
        u8   dataType;      // 수신 받은 데이터 타입
    };
}
```
- dataType : [Protocol::DataType::Type](03_datatype.md#DataType)


<br>
<br>


## <a name="Request">Protocol::Request</a>
PETRONE에 데이터를 요청할 때 사용합니다.
```cpp
namespace Protocol
{
    struct Request
    {
        u8   dataType;     // 요청할 데이터 타입
    };
}
```
- dataType : [Protocol::DataType::Type](03_datatype.md#DataType)


<br>
<br>


## <a name="Protocol_Control">Protocol::Control</a>
PETRONE을 조종할 때 사용하는 입력값입니다.
```cpp
namespace Protocol
{
    struct Control
    {
        s8   roll;        // Roll
        s8   pitch;       // Pitch
        s8   yaw;         // Yaw
        s8   throttle;    // Throttle
    };
}
```

Control 입력 값의 범위는 다음과 같습니다. Drive 모드에서는 **throttle**(전후)과 **roll**(좌우)만 사용합니다.


|이름      | 형식 | 범위        | 방향      | 음수 값(-) | 양수 값(+)    |
|:--------:|:----:|:-----------:|:---------:|:----------:|:-------------:|
| roll     | s8   | -100 ~ 100  | 좌우 이동 | 좌측       | 우측          |
| pitch    | s8   | -100 ~ 100  | 전후 이동 | 후방       | 전방          |
| yaw      | s8   | -100 ~ 100  | 좌우 회전 | 반시계     | 시계 방향     |
| throttle | s8   | -100 ~ 100  | 승하강    | 하강       | 상승          |


<br>
<br>


## <a name="Protocol_Command">Protocol::Command</a>
명령 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct Command
    {
        CommandBase   command;
    };
}
```
- command : [Protocol::CommandBase](05_base_structs.md#CommandBase)


<br>
<br>


## <a name="Protocol_Command2">Protocol::Command2</a>
명령 두 개를 전달합니다.
```cpp
namespace Protocol
{
    struct Command2
    {
        CommandBase   command1;
        CommandBase   command2;
    };
}
```
- command1, command2 : [Protocol::CommandBase](05_base_structs.md#CommandBase)


<br>
<br>


## <a name="Protocol_Command3">Protocol::Command3</a>
명령 세 개를 전달합니다.
```cpp
namespace Protocol
{
    struct Command3
    {
        CommandBase   command1;
        CommandBase   command2;
        CommandBase   command3;
    };
}
```
- command1, command2, command3 : [Protocol::CommandBase](05_base_structs.md#CommandBase)


<br>
<br>


## <a name="Protocol_Address">Protocol::Address</a>
BLE 주소를 반환합니다.
```cpp
namespace Protocol
{
    struct Address
    {
        u8   address[6];
    };
}
```

<br>
<br>


## <a name="Protocol_State">Protocol::State</a>
PETRONE의 현재 상태값을 반환합니다.
```cpp
namespace Protocol
{
    struct State
    {
        u8          modeVehicle;        // 동작 모드
        
        u8          modeSystem;         // 시스템 모드
        u8          modeFlight;         // 비행 모드
        u8          modeDrive;          // 주행 모드
        
        u8          sensorOrientation;  // 센서 방향
        u8          coordinate;         // 방위
        u8          battery;            // 배터리량(0 ~ 100)
    };
}
```
- modeVehicle : [System::ModeVehicle::Type](04_definitions.md#ModeVehicle)
- modeSystem : [System::ModeSystem::Type](04_definitions.md#ModeSystem)
- modeFlight : [System::ModeFlight::Type](04_definitions.md#ModeFlight)
- modeDrive : [System::ModeDrive::Type](04_definitions.md#ModeDrive)
- sensorOrientation : [System::SensorOrientation::Type](04_definitions.md#SensorOrientation)
- coordinate : [System::Coordinate::Type](04_definitions.md#Coordinate)


<br>
<br>


## <a name="Protocol_Attitude">Protocol::Attitude</a>
자세값을 반환합니다.
```cpp
namespace Protocol
{
    struct Attitude
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
    };
}
```

드론의 자세를 확인할 때의 사용 범위는 다음과 같습니다.

|이름      | 형식 | 범위        | 설명                                |
|:--------:|:----:|:-----------:|:-----------------------------------:|
| roll     | s16  | -180 ~ 180  | 좌우 기울기 각도                    |
| pitch    | s16  | -180 ~ 180  | 전후 기울기 각도                    |
| yaw      | s16  |    0 ~ 360  | 중력 방향을 축으로 회전할 때의 각도 |


자이로 센서 데이터를 확인할 때의 사용 범위는 다음과 같습니다.

|이름      | 형식 | 범위            |
|:--------:|:----:|:---------------:|
| roll     | s16  | -32768 ~ 32767  |
| pitch    | s16  | -32768 ~ 32767  |
| yaw      | s16  | -32768 ~ 32767  |


<br>
<br>


## <a name="Protocol_GyroBias">Protocol::GyroBias</a>
자이로 바이어스 값을 반환합니다.
```cpp
namespace Protocol
{
    struct GyroBias
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
    };
}
```

<br>
<br>


## <a name="Protocol_TrimFlight">Protocol::TrimFlight</a>
비행 Trim을 조정할 때 사용합니다.
```cpp
namespace Protocol
{
    struct TrimFlight
    {
        s16          roll;         // Roll
        s16          pitch;        // Pitch
        s16          yaw;          // Yaw
        s16          throttle;     // Throttle
    };
}
```

<br>
<br>


## <a name="Protocol_TrimDrive">Protocol::TrimDrive</a>
자동차 Trim을 조정할 때 사용합니다.
```cpp
namespace Protocol
{
    struct TrimDrive
    {
        s16          wheel;         // Wheel
    };
}
```

<br>
<br>


## <a name="Protocol_TrimAll">Protocol::TrimAll</a>
비행 및 자동차 Trim을 한 번에 조정할 때 사용합니다.
```cpp
namespace Protocol
{
    struct TrimAll
    {
        TrimFlight   flight;
        TrimDrive    drive;
    };
}
```
- flight : [Protocol::TrimFlight](#TrimFlight)
- drive : [Protocol::TrimDrive](#TrimDrive)


<br>
<br>


## <a name="Protocol_CountFlight">Protocol::CountFlight</a>
비행과 관련된 저장값을 읽을 때 사용합니다.
```cpp
namespace Protocol
{
    struct CountFlight
    {
        u64 timeFlight;             // 비행 시간
        
        u16 countTakeOff;           // 이륙 횟수
        u16 countLanding;           // 착륙 횟수
        u16 countAccident;          // 충돌 횟수
    };
}
```

<br>
<br>


## <a name="Protocol_CountDrive">Protocol::CountDrive</a>
주행과 관련된 저장값을 읽을 때 사용합니다.
```cpp
namespace Protocol
{
    struct CountDrive
    {
        u64 timeDrive;              // 주행 시간
        
        u16 countAccident;          // 충돌 횟수
    };
}
```
countAccident 변수는 주행 중 충돌을 카운트 하기 위해 만든 변수이나 실제 주행 시 노면이 고르지 못할 때의 충격에 의해서도 카운트가 증가하는 문제가 있습니다. 현재로는 크게 의미가 없는 값으로 생각하시면 됩니다.


<br>
<br>


## <a name="Protocol_IrMessage">Protocol::IrMessage</a>
IR 데이터를 전송하는데 사용하거나, PETRONE이 IR 데이터를 수신 받았을 때 외부 장치로 전송하는 데이터입니다.
```cpp
namespace Protocol
{
    struct IrMessage
    {
        u8  direction;               // 수신 받은 방향
        u32 irData;                  // IR 메세지
    };
}
```
- direction : [System::Direction::Type](04_definitions.md#Direction)


<br>
<br>


## <a name="Protocol_ImuRawAndAngle">Protocol::ImuRawAndAngle</a>
자이로 센서에서 출력한 값과 내부에서 계산한 드론의 자세 값을 반환합니다.
```cpp
namespace Protocol
{
    struct ImuRawAndAngle
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


<br>
<br>


## <a name="Protocol_Pressure">Protocol::Pressure</a>
압력 센서의 출력값을 반환합니다. d1과 d2는 MS5607에서만 출력하는 값으로 DPS310이 사용된 기체에서는 0으로 출력됩니다.
```cpp
namespace Protocol
{
    struct Pressure
    {
        s32		d1;
        s32		d2;
        s32		temperature;
        s32		pressure;
    };
}
```
- pressure 출력 값의 단위는 밀리미터(mm)입니다.


<br>
<br>


## <a name="Protocol_ImageFlow">Protocol::ImageFlow</a>
자세 제어에 사용하는 영상 데이터 처리 값입니다.
```cpp
namespace Protocol
{
    struct ImageFlow
    {
        s32		positionX;
        s32		positionY;
    };
}
```
- positionX, positionY 출력 값의 단위는 밀리미터(mm)입니다.


<br>
<br>


## <a name="Protocol_Button">Protocol::Button</a>
버튼 입력 값입니다.
```cpp
namespace Protocol
{
    struct Button
    {
        u8      button;
    };
}
```


<br>
<br>


## <a name="Protocol_Motor">Protocol::Motor</a>
모터를 동작시키거나, 현재 모터에 입력된 값을 확인할 때 사용합니다.
```cpp
namespace Protocol
{
    struct Motor
    {
        MotorBase motor[4];
    };
}
```
- motor : [Protocol::MotorBase::Type](05_base_structs.md#MotorBase)


<br>
<br>


## <a name="Protocol_Range">Protocol::Range</a>
거리 센서에서 입력받은 거리 값을 반환합니다. 앞으로 거리센서 모듈이 추가될 예정이어서 6방향에 대한 값을 모두 담는 구조체를 사용합니다.
```cpp
namespace Protocol
{
    struct Range
    {
        u16	left;
        u16	front;
        u16	right;
        u16	rear;
        u16	top;
        u16	bottom;
    };
}
```
- 모든 출력 값의 단위는 밀리미터(mm)입니다.


<br>
<br>


## <a name="Protocol_UpdateLookupTarget">Protocol::UpdateLookupTarget</a>
펌웨어 정보 요청.<br>
페트론은 제어 MCU와 통신 MCU로 구성되어 있습니다. Protocol::UpdateLookupTarget은 원하는 장치의 Protocol::UpdateInformation을 요청할 때 사용합니다.
```cpp
namespace Protocol
{
    struct UpdateLookupTarget
    {
        u32	deviceType;
    };
}
```
- deviceType : [System::DeviceType::Type](04_definitions.md#DeviceType)


<br>
<br>


## <a name="Protocol_UpdateInformation">Protocol::UpdateInformation</a>
펌웨어 정보.<br>
PC 또는 App 등에서 Protocol::UpdateLookupTarget을 전송한 경우 deviceType이 일치하는 장치가 Protocol::UpdateInformation을 응답으로 전송합니다.
```cpp
namespace Protocol
{
    struct UpdateInformation
    {
        u8      modeUpdate;     // 현재 업데이트 모드

        u32     deviceType;     // 장치 Type
        u8      imageType;      // 현재 펌웨어의 이미지 타입
        u16     imageVersion;   // 현재 펌웨어의 버젼

        u8      year;           // 빌드 년
        u8      month;          // 빌드 월
        u8      day;            // 빌드 일
    };
}
```
- modeUpdate : [System::ModeUpdate::Type](04_definitions.md#ModeUpdate)
- deviceType : [System::DeviceType::Type](04_definitions.md#DeviceType)
- imageType : [System::ImageType::Type](04_definitions.md#ImageType)


<br>
<br>


## <a name="Protocol_Update">Protocol::Update</a>
펌웨어 업데이트.<br>
펌웨어 업데이트 시에는 파일에서 16바이트씩 데이터를 잘라서 전송합니다. Protocol::Update를 전송하는 동안에 다른 응답은 없습니다. 만약 전송 실패가 발생한 경우 드론이 Protocol::UpdateLocationCorrect를 보냅니다. 해당 패킷을 받으면 지정한 블럭 위치부터 다시 전송을 시작하면 됩니다.
```cpp
namespace Protocol
{
    struct Update
    {
        u16     indexBlock;         // 블럭 번호(16바이트 단위)
        u8      dataArray[16];      // 데이터 블럭
    };
}
```
- indexBlock : 파일의 실제 위치에서 16으로 나눈 값


<br>
<br>


## <a name="Protocol_UpdateLocationCorrect">Protocol::UpdateLocationCorrect</a>
펌웨어 업데이트 위치 정정.<br>
펌웨어 업데이트 중 전송에 실패하는 블럭이 발생하는 경우 indexBlockNext부터 다시 전송하라는 요청을 보냅니다.
```cpp
namespace Protocol
{
    struct UpdateLocationCorrect
    {
        u16     indexBlockNext;     // 요청 블럭 번호
    };
}
```
- indexBlockNext : 파일의 실제 위치에서 16으로 나눈 값


<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. ***Structs***
7. [Structs - Light](07_structs_light.md)
8. [Firmware Update](08_firmware_update.md)


### PETRONE Link

1. [Intro](link/01_intro.md)
2. [DataType](link/02_datatype.md)
3. [Definitions](link/03_definitions.md)
4. [Structs](link/04_structs.md)
5. [Examples](link/05_examples.md)

<br>

[Index](index.md)

<br>

