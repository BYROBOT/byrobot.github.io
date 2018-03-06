**[PETRONE](index.md)** / **BLE** / **Protocol** / **BaseStructs**

Modified : 2018.3.6

---

#### 데이터 전송 시 그대로 전달되지는 않으나 다른 구조체의 일부분으로 포함되는 구조체들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>

<a name="Protocol_CommandBase"></a>
## Protocol::CommandBase
PETRONE의 설정을 변경하거나 데이터를 요청할 때 사용합니다.
```cpp
namespace Protocol
{
    struct CommandBase
    {
        u8 commandType;   // 명령 타입
        u8 option;        // 명령에 대한 옵션
    };
}
```
- commandType : [Protocol::CommandType::Type](04_definitions.md#Protocol_CommandType)
- option : [System::ModeVehicle::Type](04_definitions.md#System_ModeVehicle), [System::Coordinate::Type](04_definitions.md#System_Coordinate), [System::Trim::Type](04_definitions.md#System_Trim),  [System::FlightEvent::Type](04_definitions.md#System_FlightEvent), [Protocol::DataType::Type](03_datatype.md#Protocol_DataType)

<br>
<br>

<a name="Protocol_LightModeBase"></a>
## Protocol::LightModeBase
LED 모드를 변경할 때 사용하는 구조체입니다.
```cpp
namespace Protocol
{
    struct LightModeBase
    {
        u8 mode;         // LED 모드
        u8 color;        // RGB 색상(팔레트 인덱스)
        u8 interval;     // 내부 연산 함수 호출 주기
    };
}
```
- mode : [Light::Mode::Type](04_definitions.md#Light_Mode)
- color : [Light::Colors::Type](04_definitions.md#Light_Colors)

<br>
<br>

<a name="Protocol_LightColor"></a>
## Light::Color
RGB LED의 색상을 직접 지정할 때 사용하는 구조체입니다.
```cpp
namespace Light
{
    struct Color
    {
        u8 r;           // Red
        u8 g;           // Green
        u8 b;           // Blue
    };
}
```

<br>
<br>

<a name="Protocol_LightModeColorBase"></a>
## Protocol::LightModeColorBase
LED 모드를 변경할 때 사용하는 구조체입니다. RGB 색상을 직접 지정할 수 있습니다.
```cpp
namespace Protocol
{
    struct LightModeColorBase
    {
        u8             mode;           // LED 모드
        Light::Color   color;          // RGB 색상
        u8             interval;       // 내부 연산 함수 호출 주기
    };
}
```
- mode : [Light::Mode::Type](04_definitions.md#Light_Mode)
- color : [Light::Color](#Light_Color)

<br>
<br>

<a name="Protocol_LightEventBase"></a>
## Protocol::LightEventBase
LED 이벤트를 실행할 때 사용하는 구조체입니다. 지정한 횟수만큼 반복 실행 후 기존 실행하던 모드로 복귀합니다.
```cpp
namespace Protocol
{
    struct LightEventBase
    {
        u8 event;        // LED 모드
        u8 color;        // RGB 색상(팔레트 인덱스)
        u8 interval;     // 내부 연산 함수 호출 주기
        u8 repeat;       // 반복 횟수
    };
}
```
- event : [Light::Mode::Type](04_definitions.md#Light_Mode)
- color : [Light::Colors::Type](04_definitions.md#Light_Colors)

<br>
<br>

<a name="Protocol_LightEventColorBase"></a>
## Protocol::LightEventColorBase
LED 이벤트를 실행할 때 사용하는 구조체입니다. 지정한 횟수만큼 반복 실행 후 기존 실행하던 모드로 복귀합니다. RGB 색상을 직접 지정할 수 있습니다.
```cpp
namespace Protocol
{
    struct LightEventColorBase
    {
        u8             event;          // LED 모드
        Light::Color   color;          // RGB 색상
        u8             interval;       // 내부 연산 함수 호출 주기
        u8             repeat;         // 반복 횟수
    };
}
```
- event : [Light::Mode::Type](04_definitions.md#Light_Mode)
- color : [Light::Color](#Protocol_LightColor)

<br>
<br>

<a name="Protocol_MotorBase"></a>
## Protocol::MotorBase
모터를 작동하거나 현재 모터에 적용된 입력값을 확인하는데 사용하는 구조체입니다.
```cpp
namespace Protocol
{
    struct MotorBase
    {
        s16 forward;        // 정방향
        s16 reverse;        // 역방향
    };
}
```


<br>

---

<h3> PETRONE</h3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Base Structs***
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

