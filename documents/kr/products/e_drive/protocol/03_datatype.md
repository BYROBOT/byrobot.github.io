**[E-DRIVE](index.md)** / **Protocol** / **DataType**

Modified : 2019.8.30

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

            // Light
            LightManual                 = 0x20,     // LED 수동 제어
            LightMode                   = 0x21,     // LED 모드 지정
            LightEvent                  = 0x22,     // LED 이벤트
            LightDefault                = 0x23,     // LED 기본 색상

            // 센서 RAW 데이터
            RawMotion                   = 0x30,     // Motion 센서 데이터 RAW 값
            RawLineTracer,                          // 라인트레이서 데이터 RAW 값

            // 상태,  센서
            State                       = 0x40,     // 상태(비행 모드, 방위기준, 배터리량)
            Attitude,                               // 자세(Angle)(Attitude)
            Position,                               // 위치
            Motion,                                 // Motion 센서 데이터 처리한 값(IMU)
            Range,                                  // 거리센서 데이터

            // 설정
            Count                       = 0x50,     // 카운트
            Bias,                                   // 엑셀, 자이로 바이어스 값
            Trim,                                   // 트림

            // Devices
            Motor                       = 0x60,     // 모터 제어 및 현재 제어값 확인
            MotorSingle,                            // 한 개의 모터 제어
            Buzzer,                                 // 부저 제어

            // Input
            Button                      = 0x70,     // 버튼 입력

            // Card
            CardClassify                = 0x90,     // 카드 색상 분류 기준 설정
            CardRange,                              // 카드 색 범위(RAW 데이터의 출력 범위)
            CardRaw,                                // 카드 데이터 RAW 값(유선으로만 전송)
            CardColor,                              // 카드 데이터
            CardList,                               // 카드 리스트 데이터
            CardFunctionList,                       // 카드 함수 리스트 데이터

            // Information Assembled
            InformationAssembledForController       = 0xA0,     // 데이터 모음
            InformationAssembledForEntry            = 0xA1,     // 데이터 모음
            InformationAssembledForByBlocks         = 0xA2,     // 데이터 모음

            // LINK 모듈
            LinkState                               = 0xE0,     // 링크 모듈의 상태
            LinkEvent,                                          // 링크 모듈의 이벤트
            LinkEventAddress,                                   // 링크 모듈의 이벤트 + 주소
            LinkRssi,                                           // 링크와 연결된 장치의 RSSI값
            LinkDiscoveredDevice,                               // 검색된 장치
            LinkPasscode,                                       // 페어링 시 필요한 Passcode 설정
            
            EndOfType
        };
    }
}
```


<br>
<br>

아래는 각 DataType와 연관된 구조체들을 링크로 연결해두었습니다.

| 이름                                  | 값   | 대상 | 설명                                            | 구조체  |
|:--------------------------------------|:----:|:----:|:------------------------------------------------|:--------|
| None                                  | 0x00 | -    | 없음                                            | &nbsp; |
| Ping                                  | 0x01 | A    | 통신 확인                                       | [Protocol::Ping](05_structs.md#Protocol_Ping) |
| Ack                                   | 0x02 | A    | 데이터 수신에 대한 응답                         | [Protocol::Ack](05_structs.md#Protocol_Ack) |
| Error                                 | 0x03 | A    | 오류                                            | [Protocol::Error](05_structs.md#Protocol_Error) |
| Request                               | 0x04 | A    | 지정한 타입의 데이터 요청                       | [Protocol::Request](05_structs.md#Protocol_Request) |
| Message                               | 0x05 | -    | 문자열 데이터                                   | &nbsp; |
| Address                               | 0x06 | A    | 주소                                            | [Protocol::Address](05_structs.md#Protocol_Address) |
| Information                           | 0x07 | A    | 펌웨어 및 장치 정보                             | [Protocol::Information](05_structs.md#Protocol_Information) |
| Update                                | 0x08 | A    | 펌웨어 업데이트                                 | &nbsp; |
| UpdateLocation                        | 0x09 | A    | 펌웨어 업데이트 위치                            | &nbsp; |
| Encrypt                               | 0x0A | A    | 펌웨어 암호화                                   | &nbsp; |
| SystemCount                           | 0x0B | A    | 시스템 카운터                                   | &nbsp; |
| SystemInformation                     | 0x0C | A    | 시스템 정보                                     | &nbsp; |
| Registration                          | 0x0D | -    | 제품 등록                                       | &nbsp; |
| Administrator                         | 0x0E | -    | 관리자                                          | &nbsp; |
| Monitor                               | 0x0F | -    | 디버깅 데이터                                   | &nbsp; |
| Control                               | 0x10 | C    | 조종                                            | [Control::Quad8](05_structs.md#Control_Quad8),<br> [Control::Quad8AndRequestData](05_structs.md#Control_Quad8AndRequestData),<br> [Control::PositionDriveMove](05_structs.md#Control_PositionDriveMove),<br> [Control::PositionDriveHeading](05_structs.md#Control_PositionDriveHeading) |
| Command                               | 0x11 | A    | 명령                                            | [Protocol::Command::Command](05_structs.md#Protocol_Command_Command),<br> [Protocol::Command::LightEvent](05_structs.md#Protocol_Command_LightEvent),<br> [Protocol::Command::LightEventColor](05_structs.md#Protocol_Command_LightEventColor),<br> [Protocol::Command::LightEventColors](05_structs.md#Protocol_Command_LightEventColors) |
| LightManual                           | 0x20 | A    | LED 수동 제어                                   | [Protocol::Light::Manual](06_structs_light.md#Protocol_Light_Manual) |
| LightMode                             | 0x21 | C    | LED 모드 지정                                   | [Protocol::Light::Mode](06_structs_light.md#Protocol_Light_Mode),<br> [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor),<br> [Protocol::Light::ModeColors](06_structs_light.md#Protocol_Light_ModeColors) |
| LightEvent                            | 0x22 | C    | LED 이벤트                                      | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event),<br> [Protocol::Light::EventColor](06_structs_light.md#Protocol_Light_EventColor),<br> [Protocol::Light::EventColors](06_structs_light.md#Protocol_Light_EventColors) |
| LightDefault                          | 0x23 | C    | LED 초기색                                      | [Protocol::Light::ModeColor](06_structs_light.md#Protocol_Light_ModeColor),<br> [Protocol::Light::ModeColors](06_structs_light.md#Protocol_Light_ModeColors) |
| RawMotion                             | 0x30 | C    | Motion Raw 데이터(Accel, Gyro)                  | [Protocol::RawMotion](05_structs.md#Protocol_RawMotion) |
| RawLineTracer                         | 0x31 | C    | 라인트레이서 데이터 RAW 값                      | [Protocol::RawLineTracer](05_structs.md#Protocol_RawLineTracer) |
| RawCard                               | 0x32 | C    | 카드 데이터 RAW 값                              | [Protocol::RawCard](05_structs.md#Protocol_RawCard) |
| RawCardList                           | 0x33 | C    | 카드 리스트 데이터                              | [Protocol::RawCardList](05_structs.md#Protocol_RawCardList) |
| RawCardFunctionList                   | 0x34 | C    | 카드 함수 리스트 데이터                         | [Protocol::RawCardFunctionList](05_structs.md#Protocol_RawCardFunctionList) |
| State                                 | 0x40 | C    | 드론의 상태                                     | [Protocol::State](05_structs.md#Protocol_State) |
| Attitude                              | 0x41 | C    | 드론의 자세(Angle)                              | [Protocol::Attitude](05_structs.md#Protocol_Attitude) |
| Position                              | 0x42 | C    | 위치                                            | [Protocol::Position](05_structs.md#Protocol_Position) |
| Motion                                | 0x43 | C    | Motion 센서(Accel, Gyro, Angle)                 | [Protocol::Motion](05_structs.md#Protocol_Motion) |
| Range                                 | 0x44 | C    | Range 센서                                      | [Protocol::Range](05_structs.md#Protocol_Range) |
| Count                                 | 0x50 | C    | 카운트                                          | [Protocol::Count](05_structs.md#Protocol_Count) |
| Bias                                  | 0x51 | C    | Accel, Gyro 바이어스 값                         | [Protocol::Bias](05_structs.md#Protocol_Bias) |
| Trim                                  | 0x52 | C    | Trim                                            | [Protocol::Trim](05_structs.md#Protocol_Trim) |
| Motor                                 | 0x60 | C    | 모터 제어 및 현재 제어값 확인                   | [Protocol::Motor](05_structs.md#Protocol_Motor) |
| MotorSingle                           | 0x61 | C    | 한 개의 모터 제어                               | [Protocol::MotorSingle](05_structs.md#Protocol_MotorSingle) |
| Buzzer                                | 0x62 | C    | 버저 제어                                       | [Protocol::Buzzer](05_structs.md#Protocol_Buzzer),<br> [Protocol::BuzzerMelody](05_structs.md#Protocol_BuzzerMelody) |
| Button                                | 0x70 | A    | 버튼 입력                                       | [Protocol::Button](05_structs.md#Protocol_Button) |
| CardClassify                          | 0x90 | D    | 카드 색상 분류 기준 설정                       | [Protocol::Card::Classify](08_structs_card.md#Protocol_Card_Classify) |
| CardRange                             | 0x91 | D    | 카드 색 범위(RAW 데이터의 출력 범위)           | [Protocol::Card::Range](08_structs_card.md#Protocol_Card_Range) |
| CardRaw                               | 0x92 | D    | 카드 데이터 RAW 값(유선으로만 전송)            | [Protocol::Card::Raw](08_structs_card.md#Protocol_Card_Raw) |
| CardColor                             | 0x93 | D    | 카드 데이터                                    | [Protocol::Card::Color](08_structs_card.md#Protocol_Card_Color) |
| CardList                              | 0x94 | D    | 카드 리스트 데이터                             | [Protocol::Card::List](08_structs_card.md#Protocol_Card_List) |
| CardFunctionList                      | 0x95 | D    | 카드 함수 리스트 데이터                        | [Protocol::Card::FunctionList](08_structs_card.md#Protocol_Card_List) |
| InformationAssembledForController     | 0xA0 | C    | 자주 갱신되는 데이터 모음(조종기)               | [Protocol::InformationAssembledForController](05_structs.md#Protocol_InformationAssembledForController) |
| InformationAssembledForEntry          | 0xA1 | C    | 자주 갱신되는 데이터 모음(엔트리)               | [Protocol::InformationAssembledForEntry](05_structs.md#Protocol_InformationAssembledForEntry) |
| InformationAssembledForByBlocks       | 0xA2 | C    | 자주 갱신되는 데이터 모음(바이블럭)             | [Protocol::InformationAssembledForByBlocks](05_structs.md#Protocol_InformationAssembledForByBlocks) |
| LinkState                             | 0xE0 | B    | 링크 모듈의 상태                                | [Protocol::LinkState](05_structs.md#Protocol_LinkState) |
| LinkEvent                             | 0xE1 | B    | 링크 모듈의 이벤트                              | [Protocol::LinkEvent](05_structs.md#Protocol_LinkEvent) |
| LinkEventAddress                      | 0xE2 | B    | 링크 모듈의 이벤트 + 주소                       | [Protocol::LinkEventAddress](05_structs.md#Protocol_LinkEventAddress) |
| LinkRssi                              | 0xE3 | B    | 링크와 연결된 장치의 RSSI값                     | [Protocol::LinkRssi](05_structs.md#Protocol_LinkRssi) |
| LinkDiscoveredDevice                  | 0xE4 | B    | 검색된 장치                                     | [Protocol::LinkDiscoveredDevice](05_structs.md#Protocol_LinkDiscoveredDevice) |
| LinkPasscode                          | 0xE5 | B    | 페어링 시 필요한 Passcode 설정                  | [Protocol::LinkPasscode](05_structs.md#Protocol_LinkPasscodee) |

<br>

- A: 모든 장치(All)
- B: 블루투스 모듈(Bluetooth)
- C: 자동차(Car)

<br>

---

<h3>E-DRIVE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Card](07_structs_card.md)

<br>

[Index](index.md)
