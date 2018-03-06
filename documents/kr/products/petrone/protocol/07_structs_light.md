**[PETRONE](index.md)** / **BLE** / **Protocol** / **Structs** / **Light**

Modified : 2018.3.6

---

#### LED 제어와 관련된 구조체들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>

<a name="Protocol_LightMode"></a>
## Protocol::LightMode
LED 모드 변경 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightMode
    {
        LightModeBase   lightMode;
    };
}
```
- lightMode : [Protocol::LightModeBase](05_base_structs.md#Protocol_LightModeBase)

<br>
<br>

<a name="Protocol_LightMode2"></a>
## Protocol::LightMode2
LED 모드 변경 두 개를 전달합니다.
```cpp
namespace Protocol
{
    struct LightMode2
    {
        LightModeBase   lightMode1;
        LightModeBase   lightMode2;
    };
}
```
- lightMode1, lightMode2 : [Protocol::LightModeBase](05_base_structs.md#Protocol_LightModeBase)

<br>
<br>

<a name="Protocol_LightModeCommand"></a>
## Protocol::LightModeCommand
LED 모드 변경 하나와 명령 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightModeCommand
    {
        LightModeBase   lightMode;
        CommandBase     command;
    };
}
```
- lightMode : [Protocol::LightModeBase](05_base_structs.md#Protocol_LightModeBase)
- command : [Protocol::CommandBase](05_base_structs.md#Protocol_CommandBase)

<br>
<br>

<a name="Protocol_LightModeCommandIr"></a>
## Protocol::LightModeCommandIr
LED 모드 변경 하나와 명령 하나, 그리고 IR 메세지를 전달합니다.
```cpp
namespace Protocol
{
    struct LightModeCommandIr
    {
        LightModeBase   lightMode;
        CommandBase     command;
        u32             irData;
    };
}
```
- lightMode : [Protocol::LightModeBase](05_base_structs.md#Protocol_LightModeBase)
- command : [Protocol::CommandBase](05_base_structs.md#Protocol_CommandBase)

<br>
<br>

<a name="Protocol_LightModeColor"></a>
## Protocol::LightModeColor
LED 모드 변경 하나를 전달합니다. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    struct LightModeColor
    {
        LightModeColorBase   lightModeColor;
    };
}
```
- lightModeColor : [Protocol::LightModeColorBase](05_base_structs.md#Protocol_LightModeColorBase)

<br>
<br>

<a name="Protocol_LightModeColor2"></a>
## Protocol::LightModeColor2
LED 모드 변경 두 개를 전달합니다. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    struct LightModeColor2
    {
        LightModeColorBase   lightModeColor1;
        LightModeColorBase   lightModeColor2;
    };
}
```
- lightModeColor1, lightModeColor2 : [Protocol::LightModeColorBase](05_base_structs.md#Protocol_LightModeColorBase)

<br>
<br>

<a name="Protocol_LightEvent"></a>
## Protocol::LightEvent
LED 이벤트 실행 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightEvent
    {
        LightEventBase   lightEvent;
    };
}
```
- lightEvent : [Protocol::LightEventBase](05_base_structs.md#Protocol_LightEventBase)

<br>
<br>

<a name="Protocol_LightEvent2"></a>
## Protocol::LightEvent2
LED 이벤트 실행 두 개를 전달합니다.
```cpp
namespace Protocol
{
    struct LightEvent2
    {
        LightEventBase   lightEvent1;
        LightEventBase   lightEvent2;
    };
}
```
- lightEvent1, lightEvent2 : [Protocol::LightEventBase](05_base_structs.md#Protocol_LightEventBase)

<br>
<br>

<a name="Protocol_LightEventCommand"></a>
## Protocol::LightEventCommand
LED 이벤트 실행 하나와 명령 하나를 전달합니다.
```cpp
namespace Protocol
{
    struct LightEventCommand
    {
        LightEventBase   lightEvent;
        CommandBase      command;
    };
}
```
- lightEvent : [Protocol::LightEventBase](05_base_structs.md#Protocol_LightEventBase)
- command : [Protocol::CommandBase](05_base_structs.md#Protocol_CommandBase)

<br>
<br>

<a name="Protocol_LightEventCommandIr"></a>
## Protocol::LightEventCommandIr
LED 이벤트 실행 하나와 명령 하나, 그리고 IR 메세지를 전달합니다.
```cpp
namespace Protocol
{
    struct LightEventCommandIr
    {
        LightEventBase   lightEvent;
        CommandBase      command;
        u32              irData;
    };
}
```
- lightEvent : [Protocol::LightEventBase](05_base_structs.md#Protocol_LightEventBase)
- command : [Protocol::CommandBase](05_base_structs.md#Protocol_CommandBase)

<br>
<br>

<a name="Protocol_LightEventColor"></a>
## Protocol::LightEventColor
LED 이벤트 실행 하나를 전달합니다. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    struct LightEventColor
    {
        LightEventColorBase   lightEventColor;
    };
}
```
- lightEventColor : [Protocol::LightEventColorBase](05_base_structs.md#Protocol_LightEventColorBase)

<br>
<br>

<a name="Protocol_LightEventColor2"></a>
## Protocol::LightEventColor2
LED 이벤트 실행 두 개를 전달합니다. RGB 값을 직접 지정합니다.
```cpp
namespace Protocol
{
    struct LightEventColor2
    {
        LightEventColorBase   lightEventColor1;
        LightEventColorBase   lightEventColor2;
    };
}
```
- lightEventColor1, lightEventColor2 : [Protocol::LightEventColorBase](05_base_structs.md#Protocol_LightEventColorBase)

<br>
<br>

<a name="Protocol_LightModeDefaultColor"></a>
## Protocol::LightModeDefaultColor2
LED 시작 모드를 설정합니다. RGB 값을 직접 지정합니다. 여기서 지정한 값은 드론의 내부 메모리에 저장합니다.
```cpp
namespace Protocol
{
    struct LightModeDefaultColor
    {
        LightModeColorBase   lightModeDefaultColor;
    };
}
```
- lightModeDefaultColor : [Protocol::LightModeColorBase](05_base_structs.md#Protocol_LightModeColorBase)

<br>
<br>

<a name="Protocol_LightModeDefaultColor2"></a>
## Protocol::LightModeDefaultColor2
LED 시작 모드 두 개를 설정합니다. RGB 값을 직접 지정합니다. 여기서 지정한 값은 드론의 내부 메모리에 저장합니다.
```cpp
namespace Protocol
{
    struct LightModeDefaultColor2
    {
        LightModeColorBase   lightModeDefaultColor1;
        LightModeColorBase   lightModeDefaultColor2;
    };
}
```
- lightModeDefaultColor1, lightModeDefaultColor2 : [Protocol::LightModeColorBase](05_base_structs.md#Protocol_LightModeColorBase)



<br>

---

<h3> PETRONE</h3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
7. ***Structs - Light***
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

