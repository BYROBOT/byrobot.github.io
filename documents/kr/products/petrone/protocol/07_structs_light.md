***PETRONE / BLE / Protocol / Structs / Light***<br>
Modified : 2017.10.18

---

#### LED 제어와 관련된 구조체들을 소개합니다.

---

<br>

## <a name="LightMode">Protocol::LightMode</a>
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
- lightMode : [Protocol::LightModeBase](base_structs.md#LightModeBase)

<br>
<br>

## <a name="LightMode2">Protocol::LightMode2</a>
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
- lightMode1, lightMode2 : [Protocol::LightModeBase](base_structs.md#LightModeBase)

<br>
<br>

## <a name="LightModeCommand">Protocol::LightModeCommand</a>
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
- lightMode : [Protocol::LightModeBase](base_structs.md#LightModeBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightModeCommandIr">Protocol::LightModeCommandIr</a>
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
- lightMode : [Protocol::LightModeBase](base_structs.md#LightModeBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightModeColor">Protocol::LightModeColor</a>
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
- lightModeColor : [Protocol::LightModeColorBase](base_structs.md#LightModeColorBase)

<br>
<br>

## <a name="LightModeColor2">Protocol::LightModeColor2</a>
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
- lightModeColor1, lightModeColor2 : [Protocol::LightModeColorBase](base_structs.md#LightModeColorBase)

<br>
<br>

## <a name="LightEvent">Protocol::LightEvent</a>
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
- lightEvent : [Protocol::LightEventBase](base_structs.md#LightEventBase)

<br>
<br>

## <a name="LightEvent2">Protocol::LightEvent2</a>
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
- lightEvent1, lightEvent2 : [Protocol::LightEventBase](base_structs.md#LightEventBase)

<br>
<br>

## <a name="LightEventCommand">Protocol::LightEventCommand</a>
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
- lightEvent : [Protocol::LightEventBase](base_structs.md#LightEventBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightEventCommandIr">Protocol::LightEventCommandIr</a>
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
- lightEvent : [Protocol::LightEventBase](base_structs.md#LightEventBase)
- command : [Protocol::CommandBase](base_structs.md#CommandBase)

<br>
<br>

## <a name="LightEventColor">Protocol::LightEventColor</a>
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
- lightEventColor : [Protocol::LightEventColorBase](base_structs.md#LightEventColorBase)

<br>
<br>

## <a name="LightEventColor2">Protocol::LightEventColor2</a>
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
- lightEventColor1, lightEventColor2 : [Protocol::LightEventColorBase](base_structs.md#LightEventColorBase)

<br>
<br>

## <a name="LightModeDefaultColor">Protocol::LightModeDefaultColor</a>
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
- lightModeDefaultColor : [Protocol::LightModeColorBase](base_structs.md#LightModeColorBase)

<br>
<br>

## <a name="LightModeDefaultColor2">Protocol::LightModeDefaultColor2</a>
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
- lightModeDefaultColor1, lightModeDefaultColor2 : [Protocol::LightModeColorBase](base_structs.md#LightModeColorBase)



<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
7. ***Structs - Light***
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

