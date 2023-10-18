**[SKYKICK EVOLUTION](index.md)** / **Protocol** / **DataType**

Modified : 2023.7.1

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
            None						= 0x00,		// 없음
            Ping						= 0x01,		// 통신 확인
            Ack							= 0x02,		// 데이터 수신에 대한 응답
            Error						= 0x03,		// 오류
            Request						= 0x04,		// 지정한 타입의 데이터 요청
            Information						= 0x07,		// 펌웨어 및 장치 정보
            Control						= 0x10,		// 조종
            
            Command						= 0x11,		// 명령
            Pairing						= 0x12,		// 페어링
            ResponseRate					= 0x13,		// ResponseRate
            
            // Light
            LightManual						= 0x20,		// LED 수동 제어
            LightMode						= 0x21,		// LED 모드 지정
            LightEvent						= 0x22,		// LED 이벤트
            
            // 센서 RAW 데이터
            RawMotion						= 0x30,		// Motion 센서 데이터 RAW 값
            
            // 상태,  센서
            State						= 0x40,		// 드론의 상태(비행 모드, 방위기준, 배터리량)
            Altitude						= 0x43,		// 높이, 고도
            Motion						= 0x44,		// Motion 센서 데이터 처리한 값(IMU)
            VisionSensor					= 0x47,		// Vision Sensor X, Y, Z
            
            // 설정
            Count						= 0x50,		// 카운트
            Bias						= 0x51,		// 엑셀, 자이로 바이어스 값
            Trim						= 0x52,		// 트림
            LostConnection					= 0x54,		// 연결이 끊긴 후 반응 시간 설정
            
            // Device
            Motor						= 0x60,		// 모터 제어 및 현재 제어값 확인
            Buzzer						= 0x62,		// 버저 제어
            Battery						= 0x64,		// 배터리
            
            // Input
            Button						= 0x70,		// 버튼
            Joystick,								// 조이스틱
            
            // Information Assembled
            InformationAssembledForController			= 0xA0,		// 데이터 모음
            
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
| Information                           | 0x07 | A    | 펌웨어 및 장치 정보                            | [Protocol::Information](05_structs.md#Protocol_Information) |
| Control                               | 0x10 | D    | 조종                                           | [Control::Quad8](05_structs.md#Control_Quad8),<br> [Control::Quad8AndRequestData](05_structs.md#Control_Quad8AndRequestData),<br> [Control::Position](05_structs.md#Control_Position) |
| Command                               | 0x11 | A    | 명령                                           | [Protocol::Command::Command](05_structs.md#Protocol_Command_Command) |
| Pairing                               | 0x12 | A    | 페어링                                         | [Protocol::Pairing](05_structs.md#Protocol_Pairing) |
| ResponseRate                          | 0x13 | A    | ResponseRate                                   | [Protocol::ResponseRate](05_structs.md#Protocol_ResponseRate) |
| LightManual                           | 0x20 | A    | LED 수동 제어                                  | [Protocol::Light::Manual](06_structs_light.md#Protocol_Light_Manual) |
| LightMode                             | 0x21 | D    | LED 모드 지정                                  | [Protocol::Light::Mode](06_structs_light.md#Protocol_Light_Mode) |
| LightEvent                            | 0x22 | D    | LED 이벤트                                     | [Protocol::Light::Event](06_structs_light.md#Protocol_Light_Event) |
| RawMotion                             | 0x30 | D    | Motion Raw 데이터(Accel, Gyro)                 | [Protocol::RawMotion](05_structs.md#Protocol_RawMotion) |
| State                                 | 0x40 | D    | 드론의 상태                                    | [Protocol::State](05_structs.md#Protocol_State)[Protocol::StateController](05_structs.md#Protocol_StateController)|
| Altitude                              | 0x43 | D    | 높이, 고도                                     | [Protocol::Altitude](05_structs.md#Protocol_Altitude) |
| Motion                                | 0x44 | D    | Motion 센서(Accel, Gyro, Angle)                | [Protocol::Motion](05_structs.md#Protocol_Motion) |
| VisionSensor                          | 0x47 | D    | 비전센서 (X,Y,Z)                               | [Protocol::VisionSensor](05_structs.md#Protocol_VisionSensor) |
| Count                                 | 0x50 | D    | 카운트                                         | [Protocol::Count](05_structs.md#Protocol_Count) |
| Trim                                  | 0x52 | D    | Trim                                           | [Protocol::Trim](05_structs.md#Protocol_Trim) |
| Buzzer                                | 0x62 | C    | 버저 제어                                      | [Protocol::Buzzer](05_structs.md#Protocol_Buzzer),<br> [Protocol::BuzzerMelody](05_structs.md#Protocol_BuzzerMelody) |
| Joystick                              | 0x71 | C    | 조이스틱 입력                                  | [Protocol::Joystick](05_structs.md#Protocol_Joystick) |
| InformationAssembledForController     | 0xA0 | D    | 자주 갱신되는 데이터 모음(조종기)              | [Protocol::InformationAssembledForController](05_structs.md#Protocol_InformationAssembledForController) |

<br>

- A: 모든 장치(All)
- C: 조종기(Controller)
- D: 드론(Drone)

<br>

---

<h3>SKYKICK EVOLUTION</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
