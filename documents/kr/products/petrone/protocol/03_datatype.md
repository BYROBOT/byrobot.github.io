**[PETRONE](index.md)** / **BLE** / **Protocol** / **DataType**

Modified : 2018.3.6

---

#### 데이터 타입을 소개합니다.

---

<br>

## <a name="Protocol_DataType">Protocol::DataType::Type</a>
데이터 타입

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            None = 0,                   // 없음

            // 시스템 정보
            Ping,                       // 통신 확인(reserved)
            Ack,                        // 데이터 수신에 대한 응답
            Error,                      // 오류(reserved)
            Request,                    // 지정한 타입의 데이터 요청
            
            // 조종, 명령 
            Control = 0x10,             // 조종
            Command,                    // 명령
            Command2,                   // 다중 명령(2가지 설정을 동시에 변경)
            Command3,                   // 다중 명령(3가지 설정을 동시에 변경)
            
            // LED
            LightMode = 0x20,           // LED 모드 지정
            LightMode2,                 // LED 모드 2개 지정
            LightModeCommand,           // LED 모드, 커맨드
            LightModeCommandIr,         // LED 모드, 커맨드, IR 데이터 송신
            LightModeColor,             // LED 모드 3색 직접 지정
            LightModeColor2,            // LED 모드 3색 직접 지정 2개
            
            LightEvent,                 // LED 이벤트
            LightEvent2,                // LED 이벤트 2개, 
            LightEventCommand,          // LED 이벤트, 커맨드
            LightEventCommandIr,        // LED 이벤트, 커맨드, IR 데이터 송신
            LightEventColor,            // LED 이벤트 3색 직접 지정
            LightEventColor2,           // LED 이벤트 3색 직접 지정 2개
            
            LightModeDefaultColor,      // LED 초기 모드 3색 직접 지정
            LightModeDefaultColor2,     // LED 초기 모드 3색 직접 지정 2개
            
            // 상태 
            Address = 0x30,             // 장치 주소
            State,                      // 드론의 상태(비행 모드, 방위기준, 배터리량)
            Attitude,                   // 드론의 자세(Vector)
            GyroBias,                   // 자이로 바이어스 값(Vector)
            TrimAll,                    // 전체 트림
            TrimFlight,                 // 비행 트림
            TrimDrive,                  // 주행 트림
            
            CountFlight,                // 비행 관련 카운트 
            CountDrive,                 // 주행 관련 카운트 
            
            // 데이터 송수신
            IrMessage = 0x40,           // IR 데이터 송수신
            
            // 센서 및 제어
            ImuRawAndAngle = 0x50,      // IMU Raw + Angle
            Pressure,                   // 압력 센서 데이터
            ImageFlow,                  // ImageFlow
            Button,                     // 버튼 입력
            Battery,                    // 배터리
            Motor,                      // 모터 제어 및 현재 제어값 확인
            Temperature,                // 온도 데이터
            Range,                      // 거리 센서
        
            // 펌웨어 업데이트
            UpdateLookupTarget = 0x90,	// 업데이트 대상 장치 검색
            UpdateInformation,          // 업데이트 정보
            Update,                     // 업데이트 16바이트 단위
            UpdateLocationCorrect,      // 업데이트 위치 정정
            
            EndOfType
        };
    }
}
```


<br>
<br>

아래는 각 DataType와 연관된 구조체들을 링크로 연결해두었습니다.

| 이름                    | 값   | 설명                           | 구조체  |
|:------------------------|:----:|:-------------------------------|:--------|
| None                    | 0x00 | 없음                           | &nbsp; |
| Ping                    | 0x01 | 통신 확인                      | &nbsp; |
| Ack                     | 0x02 | 데이터 수신에 대한 응답        | [Protocol::Ack](06_structs.md#Protocol_Ack) |
| Error                   | 0x03 | 오류(reserved)                 | &nbsp; |
| Request                 | 0x04 | 지정한 타입의 데이터 요청      | [Protocol::Request](06_structs.md#Protocol_Request) |
| Control                 | 0x10 | 조종 명령                      | [Protocol::Control](06_structs.md#Protocol_Control) |
| Command                 | 0x11 | 명령                           | [Protocol::Command](06_structs.md#Protocol_Command) |
| Command2                | 0x12 | 명령 x 2                       | [Protocol::Command2](06_structs.md#Protocol_Command2) |
| Command3                | 0x13 | 명령 x 3                       | [Protocol::Command3](06_structs.md#Protocol_Command3) |
| LightMode               | 0x20 | LED 모드 지정                  | [Protocol::LightMode](07_structs_light.md#Protocol_LightMode) |
| LightMode2              | 0x21 | LED 모드 지정 x 2              | [Protocol::LightMode2](07_structs_light.md#Protocol_LightMode2) |
| LightModeCommand        | 0x22 | LED 모드, 커맨드               | [Protocol::LightModeCommand](07_structs_light.md#Protocol_LightModeCommand) |
| LightModeCommandIr      | 0x23 | LED 모드, 커맨드, IR           | [Protocol::LightModeCommandIr](07_structs_light.md#Protocol_LightModeCommandIr) |
| LightModeColor          | 0x24 | LED 모드 3색                   | [Protocol::LightModeColor](07_structs_light.md#Protocol_LightModeColor) |
| LightModeColor2         | 0x25 | LED 모드 3색 x 2               | [Protocol::LightModeColor2](07_structs_light.md#Protocol_LightModeColor2) |
| LightEvent              | 0x26 | LED 이벤트                     | [Protocol::LightEvent](07_structs_light.md#Protocol_LightEvent) |
| LightEvent2             | 0x27 | LED 이벤트                     | [Protocol::LightEvent2](07_structs_light.md#Protocol_LightEvent2) |
| LightEventCommand       | 0x28 | LED 이벤트, 커맨드             | [Protocol::LightEventCommand](07_structs_light.md#Protocol_LightEventCommand) |
| LightEventCommandIr     | 0x29 | LED 이벤트, 커맨드, IR         | [Protocol::LightEventCommandIr](07_structs_light.md#Protocol_LightEventCommandIr) |
| LightEventColor         | 0x2A | LED 이벤트 3색                 | [Protocol::LightEventColor](07_structs_light.md#Protocol_LightEventColor) |
| LightEventColor2        | 0x2B | LED 이벤트 3색 x 2             | [Protocol::LightEventColor2](07_structs_light.md#Protocol_LightEventColor2) |
| LightModeDefaultColor   | 0x2C | LED 초기 모드 3색              | [Protocol::LightModeDefaultColor2](07_structs_light.md#Protocol_LightModeDefaultColor) |
| LightModeDefaultColor2  | 0x2D | LED 초기 모드 3색 x 2          | [Protocol::LightModeDefaultColor2](07_structs_light.md#Protocol_LightModeDefaultColor2) |
| Address                 | 0x30 | BLE 주소                       | [Protocol::Address](06_structs.md#Protocol_Address) |
| State                   | 0x31 | 드론의 상태                    | [Protocol::State](06_structs.md#Protocol_State) |
| Attitude                | 0x32 | 드론의 자세(Angle)             | [Protocol::Attitude](06_structs.md#Protocol_Attitude) |
| GyroBias                | 0x33 | Gyro 바이어스 값               | [Protocol::GyroBias](06_structs.md#Protocol_GyroBias) |
| TrimAll                 | 0x34 | 전체 트림                      | [Protocol::TrimAll](06_structs.md#Protocol_TrimAll) |
| TrimFlight              | 0x35 | 비행 트림                      | [Protocol::TrimFlight](06_structs.md#Protocol_TrimFlight) |
| TrimDrive               | 0x36 | 주행 트림                      | [Protocol::TrimDrive](06_structs.md#Protocol_TrimDrive) |
| CountFlight             | 0x37 | 비행 관련 카운트               | [Protocol::CountFlight](06_structs.md#Protocol_CountFlight) |
| CountDrive              | 0x38 | 주행 관련 카운트               | [Protocol::CountDrive](06_structs.md#Protocol_CountDrive) |
| IrMessage               | 0x40 | IR 데이터 송수신               | [Protocol::IrMessage](06_structs.md#Protocol_IrMessage) |
| ImuRawAndAngle          | 0x50 | IMU(Accel, Gyro, Angle)        | [Protocol::ImuRawAndAngle](06_structs.md#Protocol_ImuRawAndAngle) |
| Pressure                | 0x51 | 압력 센서 데이터               | [Protocol::Pressure](06_structs.md#Protocol_Pressure) |
| ImageFlow               | 0x52 | ImageFlow                      | [Protocol::ImageFlow](06_structs.md#Protocol_ImageFlow) |
| Button                  | 0x53 | 버튼 입력                      | [Protocol::Button](06_structs.md#Protocol_Button) |
| Battery                 | 0x54 | 배터리                         | &nbsp; |
| Motor                   | 0x55 | 모터 제어 및 현재 제어값 확인  | [Protocol::Motor](06_structs.md#Protocol_Motor) |
| Temperature             | 0x56 | 온도 센서                      | &nbsp; |
| Range                   | 0x57 | 거리 센서                      | [Protocol::Range](06_structs.md#Protocol_Range) |
| UpdateLookupTarget      | 0x90 | 업데이트 대상 장치 검색        | [Protocol::UpdateLookupTarget](06_structs.md#Protocol_UpdateLookupTarget) |
| UpdateInformation       | 0x91 | 펌웨어 정보                    | [Protocol::UpdateInformation](06_structs.md#Protocol_UpdateInformation) |
| Update                  | 0x92 | 펌웨어 업데이트                | [Protocol::Update](06_structs.md#Protocol_Update) |
| UpdateLocationCorrect   | 0x93 | 펌웨어 업데이트 위치 정정      | [Protocol::UpdateLocationCorrect](06_structs.md#Protocol_UpdateLocationCorrect) |

<br>

---

<h3> PETRONE </h3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
7. [Structs - Light](07_structs_light.md)
8. [Firmware Update](08_firmware_update.md)


<h3> PETRONE Link</h3>

1. [Intro](link/01_intro.md)
2. [DataType](link/02_datatype.md)
3. [Definitions](link/03_definitions.md)
4. [Structs](link/04_structs.md)
5. [Examples](link/05_examples.md)

<br>

[Index](index.md)

<br>

