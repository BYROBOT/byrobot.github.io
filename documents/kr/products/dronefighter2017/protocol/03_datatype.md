***DRONEFIGHTER2017 / Protocol / DataType***<br>
Modified : 2017.10.18

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
            None                        = 0x00,     // 없음
            Ping                        = 0x01,     // 통신 확인
            Ack                         = 0x02,     // 데이터 수신에 대한 응답
            Error                       = 0x03,     // 오류
            Request                     = 0x04,     // 지정한 타입의 데이터 요청
            Message                     = 0x05,     // 문자열 데이터
            Reserved_1                  = 0x06,     // 예약
            Reserved_2                  = 0x07,     // 예약
            Monitor                     = 0x08,     // 디버깅용 값 배열 전송
            SystemCounter               = 0x09,     // 시스템 카운터
            Information                 = 0x0A,     // 펌웨어 및 장치 정보
            UpdateLocation              = 0x0B,     // 펌웨어 업데이트 위치 정정
            Update                      = 0x0C,     // 펌웨어 업데이트
            Encrypt                     = 0x0D,     // 펌웨어 암호화
            Address                     = 0x0E,     // 장치 주소
            Administrator               = 0x0F,     // 관리자 권한 획득
            Control                     = 0x10,     // 조종 명령
    
            Command                     = 0x11,     // 명령

            // Light
            LightManual                 = 0x20,     // LED 수동 제어

            LightMode                   = 0x21,     // LED 모드
            LightModeCommand            = 0x22,     // LED 모드, 커맨드
            LightModeCommandIr          = 0x23,     // LED 모드, 커맨드, IR
            LightModeColor              = 0x24,     // LED 모드 3색
            LightModeColorCommand       = 0x25,     // LED 모드 3색, 커맨드
            LightModeColorCommandIr     = 0x26,     // LED 모드 3색, 커맨드, IR
            LightModeColors             = 0x27,     // LED 모드 팔레트
            LightModeColorsCommand      = 0x28,     // LED 모드 팔레트, 커맨드
            LightModeColorsCommandIr    = 0x29,     // LED 모드 팔레트, 커맨드, IR

            LightEvent                  = 0x2A,     // LED 이벤트
            LightEventCommand           = 0x2B,     // LED 이벤트, 커맨드
            LightEventCommandIr         = 0x2C,     // LED 이벤트, 커맨드, IR
            LightEventColor             = 0x2D,     // LED 이벤트 3색
            LightEventColorCommand      = 0x2E,     // LED 이벤트 3색, 커맨드
            LightEventColorCommandIr    = 0x2F,     // LED 이벤트 3색, 커맨드, IR
            LightEventColors            = 0x30,     // LED 이벤트 팔레트
            LightEventColorsCommand     = 0x31,     // LED 이벤트 팔레트, 커맨드
            LightEventColorsCommandIr   = 0x32,     // LED 이벤트 팔레트, 커맨드, IR

            LightModeDefaultColor       = 0x33,     // LED 초기 모드 3색
            
            // 상태, 설정
            State                       = 0x40,     // 드론의 상태
            Attitude,                               // 드론의 자세
            GyroBias,                               // 자이로 바이어스 값
            TrimAll,                                // 전체 트림
            TrimFlight,                             // 비행 트림
            TrimDrive,                              // 주행 트림
            UserInterface,                          // 사용자 인터페이스 설정
    
            // Sensor raw data      
            Imu                         = 0x50,     // IMU Raw
            Pressure,                               // 압력 센서 데이터
            Battery,                                // 배터리
            Range,                                  // 거리 센서
            ImageFlow,                              // ImageFlow
            CameraImage,                            // CameraImage
                    
            // Input        
            Button                      = 0x70,     // 버튼 입력
            Joystick,                               // 조이스틱 입력
                    
            // Devices      
            Motor                       = 0x80,     // 모터 제어 및 현재 제어값 확인
            MotorSingle,                            // 한 개의 모터 제어
            IrMessage,                              // IR 데이터 송수신
            Buzzer,                                 // 부저 제어
            Vibrator,                               // 진동 제어
    
            // 카운트       
            CountFlight                 = 0x90,     // 비행 관련 카운트
            CountDrive,                             // 주행 관련 카운트
                    
            // RF       
            Pairing                     = 0xA0,     // 페어링
            Rssi,                                   // RSSI

            EndOfType
        };
    }
}
```


<br>
<br>

아래는 각 DataType와 연관된 구조체들을 링크로 연결해두었습니다.

| 이름                      | 값   | 대상 | 설명                                     | 구조체  |
|:--------------------------|:----:|:-:|:--------------------------------------------|:--------|
| None                      | 0x00 | - | 없음                                        | &nbsp; |
| Ping                      | 0x01 | A | 통신 확인                                   | [Protocol::Ping](05_structs.md#Protocol_Ping) |
| Ack                       | 0x02 | A | 데이터 수신에 대한 응답                     | [Protocol::Ack](05_structs.md#Protocol_Ack) |
| Error                     | 0x03 | - | 오류(reserve, 비트 플래그는 추후에 지정)    | &nbsp; |
| Request                   | 0x04 | A | 지정한 타입의 데이터 요청                   | [Protocol::Request](05_structs.md#Protocol_Request) |
| Message                   | 0x05 | - | 문자열 데이터                               | &nbsp; |
| Reserved_1                | 0x06 | - | 예약                                        | &nbsp; |
| Reserved_2                | 0x07 | - | 예약                                        | &nbsp; |
| Monitor                   | 0x08 | D | 디버깅용 값 배열 전송                       | &nbsp; |
| SystemCounter             | 0x09 | A | 시스템 카운터                               | &nbsp; |
| Information               | 0x0A | A | 펌웨어 및 장치 정보                         | &nbsp; |
| UpdateLocation            | 0x0B | A | 펌웨어 업데이트 위치 정정                   | &nbsp; |
| Update                    | 0x0C | A | 펌웨어 업데이트                             | &nbsp; |
| Encrypt                   | 0x0D | - | 펌웨어 암호화                               | &nbsp; |
| Address                   | 0x0E | A | 장치 주소                                   | &nbsp; |
| Administrator             | 0x0F | - | 관리자 권한                                 | &nbsp; |
| Control                   | 0x10 | D | 조종 명령                                   | [Control::Double8](05_structs.md#Control_Double8), [Control::Quad8](05_structs.md#Control_Quad8) |
| Command                   | 0x11 | A | 명령                                        | [Protocol::Command](05_structs.md#Protocol_Command) |
| LightManual               | 0x20 | A | LED 수동 제어                               | [Protocol::Light::Manual](06_structs_light.md#Protocol_Light_Manual) |
| LightMode                 | 0x21 | A | LED 모드 지정                               | [Protocol::Light::Mode](06_structs_light.md#Protocol_Light_Mode) |
| LightModeCommand          | 0x22 | A | LED 모드, 커맨드                            | [Protocol::Light::ModeCommand](06_structs_light.md#Protocol_Light_ModeCommand) |
| LightModeCommandIr        | 0x23 | A | LED 모드, 커맨드, IR                        | [Protocol::Light::ModeCommandIr](06_structs_light.md#Protocol_Light_ModeCommandIr) |
| LightModeColor            | 0x24 | - | LED 모드 3색                                | &nbsp; |
| LightModeColorCommand     | 0x25 | - | LED 모드 3색, 커맨드                        | &nbsp; |
| LightModeColorCommandIr   | 0x26 | - | LED 모드 3색, 커맨드, IR                    | &nbsp; |
| LightModeColors           | 0x27 | - | LED 모드 팔레트                             | &nbsp; |
| LightModeColorsCommand    | 0x28 | - | LED 모드 팔레트, 커맨드                     | &nbsp; |
| LightModeColorsCommandIr  | 0x29 | - | LED 모드 팔레트, 커맨드, IR                 | &nbsp; |
| LightEvent                | 0x2A | A | LED 이벤트                                  | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event) |
| LightEventCommand         | 0x2B | A | LED 이벤트, 커맨드                          | [Protocol::Light::EventCommand](06_structs_light.md#Protocol_Light_EventCommand) |
| LightEventCommandIr       | 0x2C | A | LED 이벤트, 커맨드, IR                      | [Protocol::Light::EventCommandIr](06_structs_light.md#Protocol_Light_EventCommandIr) |
| LightEventColor           | 0x2D | - | LED 이벤트 3색                              | &nbsp; |
| LightEventColorCommand    | 0x2E | - | LED 이벤트 3색, 커맨드                      | &nbsp; |
| LightEventColorCommandIr  | 0x2F | - | LED 이벤트 3색, 커맨드, IR                  | &nbsp; |
| LightEventColors          | 0x30 | - | LED 이벤트 팔레트                           | &nbsp; |
| LightEventColorsCommand   | 0x31 | - | LED 이벤트 팔레트, 커맨드                   | &nbsp; |
| LightEventColorsCommandIr | 0x32 | - | LED 이벤트 팔레트, 커맨드, IR               | &nbsp; |
| LightModeDefaultColor     | 0x33 | - | LED 초기 모드 3색                           | [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor) |
| State                     | 0x40 | D | 드론의 상태                                 | [Protocol::State](05_structs.md#Protocol_State) |
| Attitude                  | 0x41 | D | 드론의 자세(Angle)                          | [Protocol::Attitude](05_structs.md#Protocol_Attitude) |
| GyroBias                  | 0x42 | D | 자이로 바이어스 값                          | [Protocol::GyroBias](05_structs.md#Protocol_GyroBias) |
| TrimAll                   | 0x43 | D | 전체 트림                                   | [Protocol::TrimAll](05_structs.md#Protocol_TrimAll) |
| TrimFlight                | 0x44 | D | 비행 트림                                   | [Protocol::TrimFlight](05_structs.md#Protocol_TrimFlight) |
| TrimDrive                 | 0x45 | D | 주행 트림                                   | [Protocol::TrimDrive](05_structs.md#Protocol_TrimDrive) |
| UserInterface             | 0x46 | C | 사용자 인터페이스 설정                      | [Protocol::UserInterface](05_structs.md#Protocol_UserInterface) |
| Imu                       | 0x50 | D | IMU(Accel, Gyro, Angle)                     | [Protocol::Imu](05_structs.md#Protocol_Imu) |
| Pressure                  | 0x51 | - | 압력 센서 데이터                            | &nbsp; |
| Battery                   | 0x52 | - | 배터리                                      | &nbsp; |
| Range                     | 0x53 | - | 거리 센서                                   | &nbsp; |
| ImageFlow                 | 0x54 | - | ImageFlow                                   | &nbsp; |
| CameraImage               | 0x55 | - | CameraImage                                 | &nbsp; |
| Button                    | 0x70 | A | 버튼 입력                                   | [Protocol::Button](05_structs.md#Protocol_Button) |
| Joystick                  | 0x71 | C | 조이스틱 입력                               | [Protocol::Joystick](05_structs.md#Protocol_Joystick) |
| Motor                     | 0x80 | D | 모터 제어 및 현재 제어값 확인               | [Protocol::Motor](05_structs.md#Protocol_Motor) |
| MotorSingle               | 0x81 | D | 한 개의 모터 제어                           | [Protocol::MotorSingle](05_structs.md#Protocol_MotorSingle) |
| IrMessage                 | 0x82 | D | IR 데이터 송수신                            | [Protocol::IrMessage](05_structs.md#Protocol_IrMessage) |
| Buzzer                    | 0x83 | C | 버저 제어                                   | [Protocol::Buzzer](05_structs.md#Protocol_Buzzer) |
| Vibrator                  | 0x84 | C | 진동 제어                                   | [Protocol::Vibrator](05_structs.md#Protocol_Vibrator) |
| CountFlight               | 0x90 | D | 비행 관련 카운트                            | [Protocol::CountFlight](05_structs.md#Protocol_CountFlight) |
| CountDrive                | 0x91 | D | 주행 관련 카운트                            | [Protocol::CountDrive](05_structs.md#Protocol_CountDrive) |
| Pairing                   | 0xA0 | A | 페어링                                      | [Protocol::Pairing](05_structs.md#Protocol_Pairing) |
| Rssi                      | 0xA1 | - | RSSI                                        | &nbsp; |

<br>

- A: 모든 장치(All)
- C: 조종기(Controller)
- D: 드론(Drone)

<br>

---

### DRONE FIGHTER 2017

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
