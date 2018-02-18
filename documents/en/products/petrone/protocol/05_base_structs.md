***PETRONE / BLE / Protocol / BaseStructs***<br>
Modified : 2018.02.13

---

#### Introduce the structures used to send and receive data.

---

<br>

## <a name="CommandBase">Protocol::CommandBase</a>
Use to change settings or request data for PETRONE
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
- commandType : [Protocol::CommandType::Type](04_definitions.md#CommandType)
- option : [System::ModeVehicle::Type](04_definitions.md#ModeVehicle), [System::Coordinate::Type](04_definitions.md#Coordinate), [System::Trim::Type](04_definitions.md#Trim),  [System::FlightEvent::Type](04_definitions.md#FlightEvent), [Protocol::DataType::Type](03_datatype.md#DataType)

<br>
<br>

## <a name="LightModeBase">Protocol::LightModeBase</a>
LED mode change structure
```cpp
namespace Protocol
{
    struct LightModeBase
    {
        u8 mode;         // LED mode
        u8 color;        // RGB color(pallet index)
        u8 interval;     // call interval
    };
}
```
- mode : [Light::Mode::Type](04_definitions.md#LightMode)
- color : [Light::Colors::Type](04_definitions.md#LightColors)

<br>
<br>

## <a name="LightColor">Light::Color</a>
This structure is used to directly color RGB LED.
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

## <a name="LightModeColorBase">Protocol::LightModeColorBase</a>
LED mode change structure. RGB color can be specified directly.
```cpp
namespace Protocol
{
    struct LightModeColorBase
    {
        u8             mode;           // LED mode
        Light::Color   color;          // RGB colors
        u8             interval;       // call interval
    };
}
```
- mode : [Light::Mode::Type](04_definitions.md#LightMode)
- color : [Light::Color](#LightColor)

<br>
<br>

## <a name="LightEventBase">Protocol::LightEventBase</a>
Execute LED event structure. Returns to the mode you used to run after running it repeatedly for the specified number of times.
```cpp
namespace Protocol
{
    struct LightEventBase
    {
        u8 event;        // LED event
        u8 color;        // RGB color(pallet index)
        u8 interval;     // call interval
        u8 repeat;       // repeat count
    };
}
```
- event : [Light::Mode::Type](04_definitions.md#LightMode)
- color : [Light::Colors::Type](04_definitions.md#LightColors)

<br>
<br>

## <a name="LightEventColorBase">Protocol::LightEventColorBase</a>
Execute LED event structure. Returns to the mode you used to run after running it repeatedly for the specified number of times. RGB color can be specified directly.
```cpp
namespace Protocol
{
    struct LightEventColorBase
    {
        u8             event;          // LED event
        Light::Color   color;          // RGB color
        u8             interval;       // call interval
        u8             repeat;         // repeat count
    };
}
```
- event : [Light::Mode::Type](04_definitions.md#LightMode)
- color : [Light::Color](#LightColor)

<br>
<br>

## <a name="MotorBase">Protocol::MotorBase</a>
Motor control and check current value structure
```cpp
namespace Protocol
{
    struct MotorBase
    {
        s16 forward;        // forward
        s16 reverse;        // reverse
    };
}
```


<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. ***Base Structs***
6. [Structs](06_structs.md)
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

