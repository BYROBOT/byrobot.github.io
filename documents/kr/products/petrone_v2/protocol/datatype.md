**[PETRONE_V2](index.md)** / **Protocol** / **DataType**

Modified : 2017.09.20

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
            AccelBias,                              // 엑셀 바이어스 값(Vector)
            GyroBias,                               // 자이로 바이어스 값
            TrimAll,                                // 전체 트림
            TrimFlight,                             // 비행 트림
            TrimDrive,                              // 주행 트림
    
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

            // Display
            DisplayClear                = 0xB0,     // 화면 지우기
            DisplayInvert,                          // 화면 반전
            DisplayDrawPoint,                       // 점 그리기
            DisplayDrawLine,                        // 선 그리기
            DisplayDrawRect,                        // 사각형 그리기
            DisplayDrawCircle,                      // 원 그리기
            DisplayDrawString,                      // 문자열 쓰기
            DisplayDrawStringAlign,                 // 문자열 정렬하여 쓰기

            // Information Assembled
            InformationAssembledForController       = 0xD0,     // 자주 갱신되는 데이터 모음(조종기)
            InformationAssembledForEntry            = 0xD1,     // 자주 갱신되는 데이터 모음(드론)

            EndOfType
        };
    }
}
```


<br>
<br>

아래는 각 DataType와 연관된 구조체들을 링크로 연결해두었습니다.

| 이름                                  | 값   | 대상 | 설명                                           | 구조체  |
|:--------------------------------------|:----:|:----:|:-----------------------------------------------|:--------|
| None                                  | 0x00 | -    | 없음                                           | &nbsp; |
| Ping                                  | 0x01 | A    | 통신 확인                                      | [Protocol::Ping](structs.md#Protocol_Ping) |
| Ack                                   | 0x02 | A    | 데이터 수신에 대한 응답                        | [Protocol::Ack](structs.md#Protocol_Ack) |
| Error                                 | 0x03 | -    | 오류(reserve, 비트 플래그는 추후에 지정)       | [Protocol::Error](structs.md#Protocol_Error) |
| Request                               | 0x04 | A    | 지정한 타입의 데이터 요청                      | [Protocol::Request](structs.md#Protocol_Request) |
| Message                               | 0x05 | -    | 문자열 데이터                                  | &nbsp; |
| Reserved_1                            | 0x06 | -    | 예약                                           | &nbsp; |
| Reserved_2                            | 0x07 | -    | 예약                                           | &nbsp; |
| Monitor                               | 0x08 | D    | 디버깅용 값 배열 전송                          | &nbsp; |
| SystemCounter                         | 0x09 | A    | 시스템 카운터                                  | &nbsp; |
| Information                           | 0x0A | A    | 펌웨어 및 장치 정보                            | [Protocol::Information](structs.md#Protocol_Information) |
| UpdateLocation                        | 0x0B | A    | 펌웨어 업데이트 위치 정정                      | &nbsp; |
| Update                                | 0x0C | A    | 펌웨어 업데이트                                | &nbsp; |
| Encrypt                               | 0x0D | -    | 펌웨어 암호화                                  | &nbsp; |
| Address                               | 0x0E | A    | 장치 주소                                      | [Protocol::Address](structs.md#Protocol_Address) |
| Administrator                         | 0x0F | -    | 관리자 권한                                    | &nbsp; |
| Control                               | 0x10 | D    | 조종 명령                                      | [Control::Double8](structs.md#Control_Double8), [Control::Quad8](structs.md#Control_Quad8) |
| Command                               | 0x11 | A    | 명령                                           | [Protocol::Command](structs.md#Protocol_Command) |
| LightManual                           | 0x20 | A    | LED 수동 제어                                  | [Protocol::Light::Manual](structs_light.md#Protocol_Light_Manual) |
| LightMode                             | 0x21 | -    | LED 모드 지정                                  | [Protocol::Light::Mode](structs_light.md#Protocol_Light_Mode) |
| LightModeCommand                      | 0x22 | -    | LED 모드, 커맨드                               | [Protocol::Light::ModeCommand](structs_light.md#Protocol_Light_ModeCommand) |
| LightModeCommandIr                    | 0x23 | -    | LED 모드, 커맨드, IR                           | [Protocol::Light::ModeCommandIr](structs_light.md#Protocol_Light_ModeCommandIr) |
| LightModeColor                        | 0x24 | A    | LED 모드 3색                                   | [Protocol::Light::ModeColor](structs_light.md#Protocol_Light_ModeColor) |
| LightModeColorCommand                 | 0x25 | A    | LED 모드 3색, 커맨드                           | [Protocol::Light::ModeColorCommand](structs_light.md#Protocol_Light_ModeColorCommand) |
| LightModeColorCommandIr               | 0x26 | A    | LED 모드 3색, 커맨드, IR                       | [Protocol::Light::ModeColorCommandIr](structs_light.md#Protocol_Light_ModeColorCommandIr) |
| LightModeColors                       | 0x27 | A    | LED 모드 팔레트                                | [Protocol::Light::ModeColors](structs_light.md#Protocol_Light_ModeColors) |
| LightModeColorsCommand                | 0x28 | A    | LED 모드 팔레트, 커맨드                        | [Protocol::Light::ModeColorsCommand](structs_light.md#Protocol_Light_ModeColorsCommand) |
| LightModeColorsCommandIr              | 0x29 | A    | LED 모드 팔레트, 커맨드, IR                    | [Protocol::Light::ModeColorsCommandIr](structs_light.md#Protocol_Light_ModeColorsCommandIr) |
| LightEvent                            | 0x2A | -    | LED 이벤트                                     | [Protocol::Light::Event](structs_light.md#Protocol_Light_Event) |
| LightEventCommand                     | 0x2B | -    | LED 이벤트, 커맨드                             | [Protocol::Light::EventCommand](structs_light.md#Protocol_Light_EventCommand) |
| LightEventCommandIr                   | 0x2C | -    | LED 이벤트, 커맨드, IR                         | [Protocol::Light::EventCommandIr](structs_light.md#Protocol_Light_EventCommandIr) |
| LightEventColor                       | 0x2D | A    | LED 이벤트 3색                                 | [Protocol::Light::EventColor](structs_light.md#Protocol_Light_EventColor) |
| LightEventColorCommand                | 0x2E | A    | LED 이벤트 3색, 커맨드                         | [Protocol::Light::EventColorCommand](structs_light.md#Protocol_Light_EventColorCommand) |
| LightEventColorCommandIr              | 0x2F | A    | LED 이벤트 3색, 커맨드, IR                     | [Protocol::Light::EventColorCommandIr](structs_light.md#Protocol_Light_EventColorCommandIr) |
| LightEventColors                      | 0x30 | A    | LED 이벤트 팔레트                              | [Protocol::Light::EventColors](structs_light.md#Protocol_Light_EventColors) |
| LightEventColorsCommand               | 0x31 | A    | LED 이벤트 팔레트, 커맨드                      | [Protocol::Light::EventColorsCommand](structs_light.md#Protocol_Light_EventColorsCommand) |
| LightEventColorsCommandIr             | 0x32 | A    | LED 이벤트 팔레트, 커맨드, IR                  | [Protocol::Light::EventColorsCommandIr](structs_light.md#Protocol_Light_EventColorsCommandIr) |
| LightModeDefaultColor                 | 0x33 | D    | LED 초기 모드 3색                              | [Protocol::Light::ModeColor](structs_light.md#Protocol_Light_ModeColor) |
| State                                 | 0x40 | D    | 드론의 상태                                    | [Protocol::State](structs.md#Protocol_State) |
| Attitude                              | 0x41 | D    | 드론의 자세(Angle)                             | [Protocol::Attitude](structs.md#Protocol_Attitude) |
| AccelBias                             | 0x42 | D    | Accel 바이어스 값                              | [Protocol::AccelBias](structs.md#Protocol_AccelBias) |
| GyroBias                              | 0x43 | D    | Gyro 바이어스 값                               | [Protocol::GyroBias](structs.md#Protocol_GyroBias) |
| TrimAll                               | 0x44 | D    | 전체 트림                                      | [Protocol::TrimAll](structs.md#Protocol_TrimAll) |
| TrimFlight                            | 0x45 | D    | 비행 트림                                      | [Protocol::TrimFlight](structs.md#Protocol_TrimFlight) |
| TrimDrive                             | 0x46 | D    | 주행 트림                                      | [Protocol::TrimDrive](structs.md#Protocol_TrimDrive) |
| Imu                                   | 0x50 | D    | IMU(Accel, Gyro, Angle)                        | [Protocol::Imu](structs.md#Protocol_Imu) |
| Pressure                              | 0x51 | D    | 압력 센서 데이터                               | [Protocol::Pressure](structs.md#Protocol_Pressure) |
| Battery                               | 0x52 | D    | 배터리                                         | [Protocol::Battery](structs.md#Protocol_Battery) |
| Range                                 | 0x53 | D    | 거리 센서                                      | [Protocol::Range](structs.md#Protocol_Range) |
| ImageFlow                             | 0x54 | D    | ImageFlow                                      | [Protocol::ImageFlow](structs.md#Protocol_ImageFlow) |
| CameraImage                           | 0x55 | D    | CameraImage                                    | &nbsp; |
| Button                                | 0x70 | A    | 버튼 입력                                      | [Protocol::Button](structs.md#Protocol_Button) |
| Joystick                              | 0x71 | C    | 조이스틱 입력                                  | [Protocol::Joystick](structs.md#Protocol_Joystick) |
| Motor                                 | 0x80 | D    | 모터 제어 및 현재 제어값 확인                  | [Protocol::Motor](structs.md#Protocol_Motor) |
| MotorSingle                           | 0x81 | D    | 한 개의 모터 제어                              | [Protocol::MotorSingle](structs.md#Protocol_MotorSingle) |
| IrMessage                             | 0x82 | D    | IR 데이터 송수신                               | [Protocol::IrMessage](structs.md#Protocol_IrMessage) |
| Buzzer                                | 0x83 | C    | 버저 제어                                      | [Protocol::Buzzer](structs.md#Protocol_Buzzer) |
| Vibrator                              | 0x84 | C    | 진동 제어                                      | [Protocol::Vibrator](structs.md#Protocol_Vibrator) |
| CountFlight                           | 0x90 | D    | 비행 관련 카운트                               | [Protocol::CountFlight](structs.md#Protocol_CountFlight) |
| CountDrive                            | 0x91 | D    | 주행 관련 카운트                               | [Protocol::CountDrive](structs.md#Protocol_CountDrive) |
| Pairing                               | 0xA0 | A    | 페어링                                         | [Protocol::Pairing](structs.md#Protocol_Pairing) |
| Rssi                                  | 0xA1 | A    | RSSI                                           | [Protocol::Rssi](structs.md#Protocol_Rssi) |
| DisplayClear                          | 0xB0 | C    | 화면 지우기                                    | [Protocol::Display::ClearAll](structs_display.md#Protocol_Display_ClearAll), [Protocol::Display::Clear](structs_display.md#Protocol_Display_Clear)   |
| DisplayInvert                         | 0xB1 | C    | 화면 반전                                      | [Protocol::Display::Invert](structs_display.md#Protocol_Display_Invert) |
| DisplayDrawPoint                      | 0xB2 | C    | 점 그리기                                      | [Protocol::Display::DrawPoint](structs_display.md#Protocol_Display_DrawPoint) |
| DisplayDrawLine                       | 0xB3 | C    | 선 그리기                                      | [Protocol::Display::DrawLine](structs_display.md#Protocol_Display_DrawLine) |
| DisplayDrawRect                       | 0xB4 | C    | 사각형 그리기                                  | [Protocol::Display::DrawRect](structs_display.md#Protocol_Display_DrawRect) |
| DisplayDrawCircle                     | 0xB5 | C    | 원 그리기                                      | [Protocol::Display::DrawCircle](structs_display.md#Protocol_Display_DrawCircle) |
| DisplayDrawString                     | 0xB6 | C    | 문자열 쓰기                                    | [Protocol::Display::DrawString](structs_display.md#Protocol_Display_DrawString) |
| DisplayDrawStringAlign                | 0xB7 | C    | 문자열 정렬하여 쓰기                           | [Protocol::Display::DrawStringAlign](structs_display.md#Protocol_Display_DrawStringAlign) |
| InformationAssembledForController     | 0xD0 | D    | 자주 갱신되는 데이터 모음(조종기)              | [Protocol::InformationAssembledForController](structs.md#Protocol_InformationAssembledForController) |
| InformationAssembledForEntry          | 0xD1 | D    | 자주 갱신되는 데이터 모음(엔트리)              | [Protocol::InformationAssembledForEntry](structs.md#Protocol_InformationAssembledForEntry) |

<br>

- A: 모든 장치(All)
- C: 조종기(Controller)
- D: 드론(Drone)

<br>

---

<h3>PETRONE V2</H3>

1. [Intro](intro.md)
2. [Typedef](typedef.md)
3. ***DataType***
4. [Definitions](definitions.md)
5. [Structs](structs.md)
6. [Structs - Light](structs_light.md)
7. [Structs - Display](structs_display.md)

<br>

[Index](index.md)
