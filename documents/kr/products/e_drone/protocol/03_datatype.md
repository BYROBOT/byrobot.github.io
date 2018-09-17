**[E-DRONE](index.md)** / **Protocol** / **DataType**

Modified : 2018.9.5

---

#### 데이터 타입을 소개합니다.

---

<br>

<a name="Protocol_DataType"></a>
## Protocol::DataType::Type
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
            Error                       = 0x03,     // 오류(reserve, 비트 플래그는 추후에 지정)
            Request                     = 0x04,     // 지정한 타입의 데이터 요청
            Message                     = 0x05,     // 문자열 데이터
            Address                     = 0x06,     // 장치 주소(MAC이 있는 경우 MAC) 혹은 고유번호(MAC이 없는 경우 UUID)
            Information                 = 0x07,     // 펌웨어 및 장치 정보
            Update                      = 0x08,     // 펌웨어 업데이트
            UpdateLocation              = 0x09,     // 펌웨어 업데이트 위치 정정
            Encrypt                     = 0x0A,     // 펌웨어 암호화
            SystemCount                 = 0x0B,     // 시스템 카운트
            SystemInformation           = 0x0C,     // 시스템 정보
            Registration                = 0x0D,     // 제품 등록(암호화 데이터 및 등록 데이터를 데이터 길이로 구분)
            Administrator               = 0x0E,     // 관리자 권한 획득
            Monitor                     = 0x0F,     // 디버깅용 값 배열 전송. 첫번째 바이트에 타입, 두 번째 바이트에 페이지 지정(수신 받는 데이터의 저장 경로 구분)
            Control                     = 0x10,     // 조종

            Command                     = 0x11,     // 명령
            Pairing                     = 0x12,     // 페어링
            Rssi                        = 0x13,     // RSSI

            // Light
            LightManual                 = 0x20,     // LED 수동 제어
            LightMode                   = 0x21,     // LED 모드 지정
            LightEvent                  = 0x22,     // LED 이벤트
            LightDefault                = 0x23,     // LED 기본 색상

            // 상태,  센서
            State                       = 0x40,     // 드론의 상태(비행 모드, 방위기준, 배터리량)
            Attitude,                               // 드론의 자세(Angle)(Attitude)
            Position,                               // 위치
            Altitude,                               // 높이, 고도
            Motion,                                 // Motion 센서 RAW 데이터(IMU)
            Flow,                                   // Flow 센서 RAW 데이터
    
            // 설정
            Count                       = 0x50,     // 카운트
            Bias,                                   // 엑셀, 자이로 바이어스 값
            Trim,                                   // 트림
            Weight,                                 // 무게 설정
            
            // Devices
            Motor                       = 0x60,     // 모터 제어 및 현재 제어값 확인
            MotorSingle,                            // 한 개의 모터 제어
            Buzzer,                                 // 부저 제어
            Vibrator,                               // 진동 제어

            // Input
            Button                      = 0x70,     // 버튼 입력
            Joystick,                               // 조이스틱 입력
                
            // Display
            DisplayClear                = 0x80,     // 화면 지우기
            DisplayInvert,                          // 화면 반전
            DisplayDrawPoint,                       // 점 그리기
            DisplayDrawLine,                        // 선 그리기
            DisplayDrawRect,                        // 사각형 그리기
            DisplayDrawCircle,                      // 원 그리기
            DisplayDrawString,                      // 문자열 쓰기
            DisplayDrawStringAlign,                 // 문자열 쓰기
            DisplayDrawImage,                       // 그림 그리기

            // Information Assembled
            InformationAssembledForController       = 0xA0,     // 자주 갱신되는 비행 데이터 모음
            InformationAssembledForEntry            = 0xA1,     // 자주 갱신되는 비행 데이터 모음

            // Navigation
            NavigationTarget                        = 0xD0,     // 네비게이션 목표점
            NavigationLocation                      = 0xD1,     // 네비게이션 가상 위치
            NavigationMonitor                       = 0xD2,
            NavigationHeading                       = 0xD3,
            NavigationCounter                       = 0xD4,
            
            GpsRtkNavigationState                   = 0xDA,     // RTK RAW 데이터 전송
            GpsRtkExtendedRawMeasurementData        = 0xDB,     // RTK RAW 데이터 전송

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
| Ping                                  | 0x01 | A    | 통신 확인                                      | [Protocol::Ping](05_structs.md#Protocol_Ping) |
| Ack                                   | 0x02 | A    | 데이터 수신에 대한 응답                        | [Protocol::Ack](05_structs.md#Protocol_Ack) |
| Error                                 | 0x03 | A    | 오류                                           | [Protocol::Error](05_structs.md#Protocol_Error) |
| Request                               | 0x04 | A    | 지정한 타입의 데이터 요청                      | [Protocol::Request](05_structs.md#Protocol_Request) |
| Message                               | 0x05 | -    | 문자열 데이터                                  | &nbsp; |
| Address                               | 0x06 | A    | 주소                                           | [Protocol::Address](05_structs.md#Protocol_Address) |
| Information                           | 0x07 | A    | 펌웨어 및 장치 정보                            | [Protocol::Information](05_structs.md#Protocol_Information) |
| Update                                | 0x08 | A    | 펌웨어 업데이트                                | &nbsp; |
| UpdateLocation                        | 0x09 | A    | 펌웨어 업데이트 위치                           | &nbsp; |
| Encrypt                               | 0x0A | A    | 펌웨어 암호화                                  | &nbsp; |
| SystemCount                           | 0x0B | A    | 시스템 카운터                                  | &nbsp; |
| SystemInformation                     | 0x0C | A    | 시스템 정보                                    | &nbsp; |
| Registration                          | 0x0D | -    | 제품 등록                                      | &nbsp; |
| Administrator                         | 0x0E | -    | 관리자                                         | &nbsp; |
| Monitor                               | 0x0F | -    | 디버깅 데이터                                  | &nbsp; |
| Control                               | 0x10 | D    | 조종                                           | [Control::Quad8](05_structs.md#Control_Quad8), [Control::Quad8AndRequestData](05_structs.md#Control_Quad8AndRequestData), [Control::Position16](05_structs.md#Control_Position16), [Control::Position](05_structs.md#Control_Position) |
| Command                               | 0x11 | A    | 명령                                           | [Protocol::Command::Command](05_structs.md#Protocol_Command_Command), [Protocol::Command::LightEvent](05_structs.md#Protocol_Command_LightEvent), [Protocol::Command::LightEventColor](05_structs.md#Protocol_Command_LightEventColor), [Protocol::Command::LightEventColors](05_structs.md#Protocol_Command_LightEventColors) |
| Pairing                               | 0x12 | A    | 페어링                                         | [Protocol::Pairing](05_structs.md#Protocol_Pairing) |
| Rssi                                  | 0x13 | A    | RSSI                                           | [Protocol::Rssi](05_structs.md#Protocol_Rssi) |
| LightManual                           | 0x20 | A    | LED 수동 제어                                  | [Protocol::Light::Manual](06_structs_light.md#Protocol_Light_Manual) |
| LightMode                             | 0x21 | D    | LED 모드 지정                                  | [Protocol::Light::Mode](06_structs_light.md#Protocol_Light_Mode), [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor), [Protocol::Light::ModeColors](06_structs_light.md#Protocol_Light_ModeColors) |
| LightEvent                            | 0x22 | D    | LED 이벤트                                     | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event), [Protocol::Light::EventColor](06_structs_light.md#Protocol_Light_EventColor), [Protocol::Light::EventColors](06_structs_light.md#Protocol_Light_EventColors) |
| LightDefault                          | 0x23 | D    | LED 초기색                                     | [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor), [Protocol::Light::ModeColors](06_structs_light.md#Protocol_Light_ModeColors) |
| State                                 | 0x40 | D    | 드론의 상태                                    | [Protocol::State](05_structs.md#Protocol_State) |
| Attitude                              | 0x41 | D    | 드론의 자세(Angle)                             | [Protocol::Attitude](05_structs.md#Protocol_Attitude) |
| Position                              | 0x42 | D    | 위치                                           | [Protocol::Position](05_structs.md#Protocol_Position) |
| Altitude                              | 0x43 | D    | 높이, 고도                                     | [Protocol::Altitude](05_structs.md#Protocol_Altitude) |
| Motion                                | 0x44 | D    | Motion 센서(Accel, Gyro, Angle)                | [Protocol::Motion](05_structs.md#Protocol_Motion) |
| Flow                                  | 0x45 | D    | Flow 센서로 계산한 위치                        | [Protocol::Flow](05_structs.md#Protocol_Flow) |
| Count                                 | 0x50 | D    | 카운트                                         | [Protocol::Count](05_structs.md#Protocol_Count) |
| Bias                                  | 0x51 | D    | Accel, Gyro 바이어스 값                        | [Protocol::Bias](05_structs.md#Protocol_Bias) |
| Trim                                  | 0x52 | D    | Trim                                           | [Protocol::Trim](05_structs.md#Protocol_Trim) |
| Weight                                | 0x53 | D    | 무게                                           | [Protocol::Weight](05_structs.md#Protocol_Weight) |
| Motor                                 | 0x60 | D    | 모터 제어 및 현재 제어값 확인                  | [Protocol::Motor](05_structs.md#Protocol_Motor) |
| MotorSingle                           | 0x61 | D    | 한 개의 모터 제어                              | [Protocol::MotorSingle](05_structs.md#Protocol_MotorSingle) |
| Buzzer                                | 0x62 | C    | 버저 제어                                      | [Protocol::Buzzer](05_structs.md#Protocol_Buzzer) |
| Vibrator                              | 0x63 | C    | 진동 제어                                      | [Protocol::Vibrator](05_structs.md#Protocol_Vibrator) |
| Button                                | 0x70 | A    | 버튼 입력                                      | [Protocol::Button](05_structs.md#Protocol_Button) |
| Joystick                              | 0x71 | C    | 조이스틱 입력                                  | [Protocol::Joystick](05_structs.md#Protocol_Joystick) |
| DisplayClear                          | 0x80 | C    | 화면 지우기                                    | [Protocol::Display::ClearAll](07_structs_display.md#Protocol_Display_ClearAll), [Protocol::Display::Clear](07_structs_display.md#Protocol_Display_Clear)   |
| DisplayInvert                         | 0x81 | C    | 화면 반전                                      | [Protocol::Display::Invert](07_structs_display.md#Protocol_Display_Invert) |
| DisplayDrawPoint                      | 0x82 | C    | 점 그리기                                      | [Protocol::Display::DrawPoint](07_structs_display.md#Protocol_Display_DrawPoint) |
| DisplayDrawLine                       | 0x83 | C    | 선 그리기                                      | [Protocol::Display::DrawLine](07_structs_display.md#Protocol_Display_DrawLine) |
| DisplayDrawRect                       | 0x84 | C    | 사각형 그리기                                  | [Protocol::Display::DrawRect](07_structs_display.md#Protocol_Display_DrawRect) |
| DisplayDrawCircle                     | 0x85 | C    | 원 그리기                                      | [Protocol::Display::DrawCircle](07_structs_display.md#Protocol_Display_DrawCircle) |
| DisplayDrawString                     | 0x86 | C    | 문자열 쓰기                                    | [Protocol::Display::DrawString](07_structs_display.md#Protocol_Display_DrawString) |
| DisplayDrawStringAlign                | 0x87 | C    | 문자열 정렬하여 쓰기                           | [Protocol::Display::DrawStringAlign](07_structs_display.md#Protocol_Display_DrawStringAlign) |
| DisplayDrawImage                      | 0x88 | C    | 이미지 그리기                                  | [Protocol::Display::DrawImage](07_structs_display.md#Protocol_Display_DrawImage) |
| InformationAssembledForController     | 0xA0 | D    | 자주 갱신되는 데이터 모음(조종기)              | [Protocol::InformationAssembledForController](05_structs.md#Protocol_InformationAssembledForController) |
| InformationAssembledForEntry          | 0xA1 | D    | 자주 갱신되는 데이터 모음(엔트리)              | [Protocol::InformationAssembledForEntry](05_structs.md#Protocol_InformationAssembledForEntry) |

<br>

- A: 모든 장치(All)
- C: 조종기(Controller)
- D: 드론(Drone)

<br>

---

<h3>E-DRONE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)
