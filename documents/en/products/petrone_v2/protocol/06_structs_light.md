**[PETRONE_V2](index.md)** / **Protocol** / **Structs** / **Light**

Modified : 2018.02.14

---

#### Introduce the LED control structures

---


<br>
<br>

# Definitions

<br>

## <a name="Light_Drone_Mode">Light::Drone::Mode::Type</a>

Communicates one LED mode change

```cpp
namespace Light
{
    namespace Drone
    {
        namespace Mode
        {
            enum Type
            {
                None,
                
                EyeNone = 0x10,
                EyeManual,              // Eye LED manual control
                EyeHold,                // Eye LED color Hold 
                EyeFlicker,             // Eye LED flicker light     
                EyeFlickerDouble,       // ye LED flicker light (Blinking twice and turning off as much as the blinking time.)            
                EyeDimming,             // Eye LED Dimming
                
                ArmNone = 0x40,         
                ArmManual,              // Arm LED manual control
                ArmHold,                // Arm LED color Hold
                ArmFlicker,             // Arm LED flicker light      
                ArmFlickerDouble,       // Arm LED flicker light (Blinking twice and turning off as much as the blinking time.)            
                ArmDimming,             // Arm LED Dimming
                
                EndOfType
            };
        }
    }
}
```


<br>
<br>


## <a name="Light_Drone_Flags">Light::Drone::Flags::Type</a>

Drone LED Flag

```cpp
namespace Light
{
    namespace Drone
    {
        namespace Flags
        {
            enum Type
            {
                None        = 0x00,
                
                EyeRed      = 0x80,
                EyeGreen    = 0x40,
                EyeBlue     = 0x20,

                ArmRed      = 0x10,
                ArmGreen    = 0x08,
                ArmBlue     = 0x04
            };
        }
    }
}
```


<br>
<br>


## <a name="Light_Controller_Mode">Light::Controller::Mode::Type</a>

Controller LED operation mode

```cpp
namespace Light
{
    namespace Controller
    {
        namespace Mode
        {
            enum Type
            {
                None,
                
                // Team
                TeamNone = 0x10,
                TeamManual,         // Manual control
                TeamHold,
                TeamFlicker,
                TeamFlickerDouble,
                TeamDimming,
                
                EndOfType
            };
        }
    }
}
```


<br>
<br>


## <a name="Light_Controller_Flags">Light::Controller::Flags::Type</a>

Drone LED Flag

```cpp
namespace Light
{
    namespace Controller
    {
        namespace Flags
        {
            enum Type
            {
                None        = 0x00,
                
                Red         = 0x80,
                Green       = 0x40,
                Blue        = 0x20
            };
        }
    }
}
```


<br>
<br>


## <a name="Light_Colors">Light::Colors::Type</a>

LED Color palette index

Colour index of the palette defined inside the drones and the controls.
Please recommend using it after testing. May differ from the color intended.

```cpp
namespace Light
{
    namespace Colors
    {
        enum Type
        {
            AliceBlue,              // 0x00
            AntiqueWhite,           // 0x01 
            Aqua,                   // 0x02
            Aquamarine,             // 0x03
            Azure,                  // 0x04
            Beige,                  // 0x05
            Bisque,                 // 0x06 
            Black,                  // 0x07 
            BlanchedAlmond,         // 0x08 
            Blue,                   // 0x09 
            BlueViolet,             // 0x0A
            Brown,                  // 0x0B 
            BurlyWood,              // 0x0C 
            CadetBlue,              // 0x0D 
            Chartreuse,             // 0x0E 
            Chocolate,              // 0x0F
            Coral,                  // 0x10
            CornflowerBlue,         // 0x11
            Cornsilk,               // 0x12
            Crimson,                // 0x13
            Cyan,                   // 0x14
            DarkBlue,               // 0x15
            DarkCyan,               // 0x16
            DarkGoldenRod,          // 0x17
            DarkGray,               // 0x18
            DarkGreen,              // 0x19
            DarkKhaki,              // 0x1A
            DarkMagenta,            // 0x1B
            DarkOliveGreen,         // 0x1C
            DarkOrange,             // 0x1D
            DarkOrchid,             // 0x1E
            DarkRed,                // 0x1F
            DarkSalmon,             // 0x20
            DarkSeaGreen,           // 0x21
            DarkSlateBlue,          // 0x22
            DarkSlateGray,          // 0x23
            DarkTurquoise,          // 0x24
            DarkViolet,             // 0x25
            DeepPink,               // 0x26
            DeepSkyBlue,            // 0x27
            DimGray,                // 0x28
            DodgerBlue,             // 0x29
            FireBrick,              // 0x2A
            FloralWhite,            // 0x2B
            ForestGreen,            // 0x2C
            Fuchsia,                // 0x2D
            Gainsboro,              // 0x2E
            GhostWhite,             // 0x2F
            Gold,                   // 0x30
            GoldenRod,              // 0x31
            Gray,                   // 0x32
            Green,                  // 0x33
            GreenYellow,            // 0x34
            HoneyDew,               // 0x35
            HotPink,                // 0x36
            IndianRed,              // 0x37
            Indigo,                 // 0x38
            Ivory,                  // 0x39
            Khaki,                  // 0x3A
            Lavender,               // 0x3B
            LavenderBlush,          // 0x3C
            LawnGreen,              // 0x3D
            LemonChiffon,           // 0x3E
            LightBlue,              // 0x3F
            LightCoral,             // 0x40
            LightCyan,              // 0x41
            LightGoldenRodYellow,   // 0x42
            LightGray,              // 0x43
            LightGreen,             // 0x44
            LightPink,              // 0x45
            LightSalmon,            // 0x46
            LightSeaGreen,          // 0x47
            LightSkyBlue,           // 0x48
            LightSlateGray,         // 0x49
            LightSteelBlue,         // 0x4A
            LightYellow,            // 0x4B
            Lime,                   // 0x4C
            LimeGreen,              // 0x4D
            Linen,                  // 0x4E
            Magenta,                // 0x4F
            Maroon,                 // 0x50
            MediumAquaMarine,       // 0x51
            MediumBlue,             // 0x52
            MediumOrchid,           // 0x53
            MediumPurple,           // 0x54
            MediumSeaGreen,         // 0x55
            MediumSlateBlue,        // 0x56
            MediumSpringGreen,      // 0x57
            MediumTurquoise,        // 0x58
            MediumVioletRed,        // 0x59
            MidnightBlue,           // 0x5A
            MintCream,              // 0x5B
            MistyRose,              // 0x5C
            Moccasin,               // 0x5D
            NavajoWhite,            // 0x5E
            Navy,                   // 0x5F
            OldLace,                // 0x60
            Olive,                  // 0x61
            OliveDrab,              // 0x62
            Orange,                 // 0x63
            OrangeRed,              // 0x64
            Orchid,                 // 0x65
            PaleGoldenRod,          // 0x66
            PaleGreen,              // 0x67
            PaleTurquoise,          // 0x68
            PaleVioletRed,          // 0x69
            PapayaWhip,             // 0x6A
            PeachPuff,              // 0x6B
            Peru,                   // 0x6C
            Pink,                   // 0x6D
            Plum,                   // 0x6E
            PowderBlue,             // 0x6F
            Purple,                 // 0x70
            RebeccaPurple,          // 0x71
            Red,                    // 0x72
            RosyBrown,              // 0x73
            RoyalBlue,              // 0x74
            SaddleBrown,            // 0x75
            Salmon,                 // 0x76
            SandyBrown,             // 0x77
            SeaGreen,               // 0x78
            SeaShell,               // 0x79
            Sienna,                 // 0x7A
            Silver,                 // 0x7B
            SkyBlue,                // 0x7C
            SlateBlue,              // 0x7D
            SlateGray,              // 0x7E
            Snow,                   // 0x7F
            SpringGreen,            // 0x80
            SteelBlue,              // 0x81
            Tan,                    // 0x82
            Teal,                   // 0x83
            Thistle,                // 0x84
            Tomato,                 // 0x85
            Turquoise,              // 0x86
            Violet,                 // 0x87
            Wheat,                  // 0x88
            White,                  // 0x89
            WhiteSmoke,             // 0x8A
            Yellow,                 // 0x8B
            YellowGreen,            // 0x8C
            
            EndOfType
        };
    }
}
```


<br>
<br>


# Structs


<br>
<br>


## <a name="Light_Color">Light::Color</a>

RGB LED color setting

Off at 0 and brightest at 255.

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

| Variable Name  | Type | Range | Size | Description  |
|:-----------:|:-------:|:--------:|:--------:|:--------|
| r           | uint8_t | 0 ~ 255  | 1 Byte   | Red     |
| g           | uint8_t | 0 ~ 255  | 1 Byte   | Green   |
| b           | uint8_t | 0 ~ 255  | 1 Byte   | Blue    |


<br>
<br>


## <a name="Protocol_Light_Manual">Protocol::Light::Manual</a>

LED Manual control

Change the brightness of the LED specified by flag. Unspecified LEDs remain at their brightness. Off at 0 and brightest at 255.

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Manual
        {
            u8  flags;         // Flags of enumulate value
            u8  brightness;    // brightness     
        };
    }
}
```

| Variable Name  | Type | Range | Size | Description  |
|:-----------:|:----------------------------------------------------:|:-------------------------:|:--------:|:------------------------------|
| flags       | [Light::Drone::Flags](#Light_Drone_Flags)            | 0b00000000 ~ 0b11111111   | 1 Byte   | Drone LED selection flag combination    |
|             | [Light::Controller::Flags](#Light_Controller_Flags)  | 0b00000000 ~ 0b11111111   |          | Controller LED ED selection flag combination |
| brightness  | uint8_t                                              | 0 ~ 255                   | 1 Byte   | Brightness                      |


<br>
<br>


## <a name="Protocol_Light_Mode">Protocol::Light::Mode</a>

LED mode change

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Mode
        {
            u8      mode;       // LED mode
            u16     interval;   // LED mode change call interval 
        };
    }
}
```

| Variable Name  | Type | Range | Size | Description  |
|:-----------:|:-------------------------------------------------------:|:----------:|:--------:|:-------------------------------|
| mode        | [Light::Drone::Mode::Type](#Light_Drone_Mode)           | -          | 1 Byte   | Drone LED control mode             |
|             | [Light::Controller::Mode::Type](#Light_Controller_Mode) | -          |          | Controller LED control mode             |
| interval    | uint16_t                                                | 0 ~ 65535  | 2 Byte   | function call interval  |


<br>
<br>


## <a name="Protocol_Light_ModeColor">Protocol::Light::ModeColor</a>

LED mode change(RGB)

LED mode change structure. RGB color can be specified directly.

```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColor
        {
            Protocol::Light::Mode   mode;
            Light::Color            color;
        };
    }
}
```

| Variable Name  | Type | Range | Size | Description  |
|:-----------:|:----------------------------------------------:|:------:|:--------:|:---------------|
| mode        | [Protocol::Light::Mode](#Protocol_Light_Mode)  | -      | 3 Byte   | LED control mode  |
| color       | [Light::Color](#Light_Color)                   | -      | 3 Byte   | LED RGB color   |


<br>
<br>


## <a name="Protocol_Light_ModeColorCommand">Protocol::Light::ModeColorCommand</a>

LED mode change(RGB) + Command

```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorCommand
        {
            Protocol::Light::Mode   mode;
            Light::Color            color;
            Protocol::Command       command;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:------------------------------------------------:|:------:|:--------:|:---------------|
| mode        | [Protocol::Light::Mode](#Protocol_Light_Mode)    | -      | 3 Byte   | LED light mode  |
| color       | [Light::Color](#Light_Color)                     | -      | 3 Byte   | LED RGB Color   |
| command     | [Protocol::Command](05_structs.md#Protocol_Command) | -      | 2 Byte   | Command           |


<br>
<br>


## <a name="Protocol_Light_ModeColorCommandIr">Protocol::Light::ModeColorCommandIr</a>

LED mode change(RGB) + Command + IR

```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorCommandIr
        {
            Protocol::Light::Mode   mode;
            Light::Color            color;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:---------:|:------------------------------------------------:|:-----------------------:|:--------:|:-------------------|
| mode      | [Protocol::Light::Mode](#Protocol_Light_Mode)    | -                       | 3 Byte   | LED light mode      |
| color     | [Light::Color](#Light_Color)                     | -                       | 3 Byte   | LED RGB Color       |
| command   | [Protocol::Command](05_structs.md#Protocol_Command) | -                       | 2 Byte   | Command               |
| irData    | uint32_t                                         | 0x00000000 ~ 0xFFFFFFFF | 4 Byte   | IR message data|


<br>
<br>


## <a name="Protocol_Light_ModeColors">Protocol::Light::ModeColors</a>

LED mode change(Palette)

```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColors
        {
            Protocol::Light::Mode   mode;
            u8                      colors;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:----------------------------------------------:|:------:|:--------:|:--------------------|
| mode        | [Protocol::Light::Mode](#Protocol_Light_Mode)  | -      | 3 Byte   | LED light mode       |
| colors      | [Light::Colors::Type](#Light_Colors)           | -      | 1 Byte   | LED Palette index   |


<br>
<br>


## <a name="Protocol_Light_ModeColorsCommand">Protocol::Light::ModeColorsCommand</a>

LED mode change(Palette) + Command

```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorsCommand
        {
            Protocol::Light::Mode   mode;
            u8                      colors;
            Protocol::Command       command;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:------------------------------------------------:|:------:|:--------:|:--------------------|
| mode        | [Protocol::Light::Mode](#Protocol_Light_Mode)    | -      | 3 Byte   | LED light mode       |
| colors      | [Light::Colors::Type](#Light_Colors)             | -      | 1 Byte   | LED Palette index   |
| command     | [Protocol::Command](05_structs.md#Protocol_Command) | -      | 2 Byte   | Command                |


<br>
<br>


## <a name="Protocol_Light_ModeColorsCommandIr">Protocol::Light::ModeColorsCommandIr</a>

LED mode change(Palette) + Command + IR

```cpp
namespace Protocol
{
    namespace Light
    {
        struct ModeColorsCommandIr
        {
            Protocol::Light::Mode   mode;
            u8                      colors;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:------------------------------------------------:|:-----------------------:|:--------:|:--------------------|
| mode        | [Protocol::Light::Mode](#Protocol_Light_Mode)    | -                       | 3 Byte   | LED light mode       |
| colors      | [Light::Colors::Type](#Light_Colors)             | -                       | 1 Byte   | LED Palette index   |
| command     | [Protocol::Command](05_structs.md#Protocol_Command) | -                       | 2 Byte   | Command                |
| irData      | uint32_t                                         | 0x00000000 ~ 0xFFFFFFFF | 4 Byte   | IR message data |


<br>
<br>


## <a name="Protocol_Light_Event">Protocol::Light::Event</a>

LED light event

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Event
        {
            u8      event;      // LED light event
            u16     interval;   // LED light event 갱신 주기
            u8      repeat;     // LED light event 반복 횟수
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:-------------------------------------------------------:|:----------:|:------:|:------------------------------|
| event      | [Light::Drone::Mode::Type](#Light_Drone_Mode)           | -          | 1 Byte | Drone LED light mode            |
|            | [Light::Controller::Mode::Type](#Light_Controller_Mode) | -          |        | Controller LED light mode          |
| interval   | UInt16                                                  | 0 ~ 65535  | 2 Byte | internal color call interval |
| repeat     | UInt8                                                   | 0 ~ 255    | 1 Byte | repeat count                    |


<br>
<br>


## <a name="Protocol_Light_EventColor">Protocol::Light::EventColor</a>

LED light event(RGB)

```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColor
        {
            Protocol::Light::Event  event;
            Light::Color            color;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:-----------------------------------------------:|:-----:|:--------:|:---------------|
| event       | [Protocol::Light::Event](#Protocol_Light_Event) | -     | 4 Byte   | LED light event     |
| color       | [Light::Color](#Light_Color)                    | -     | 3 Byte   | LED RGB Color   |


<br>
<br>


## <a name="Protocol_Light_EventColorCommand">Protocol::Light::EventColorCommand</a>

LED light event(RGB) + Command

```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorCommand
        {
            Protocol::Light::Event  event;
            Light::Color            color;
            Protocol::Command       command;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:------------------------------------------------:|:----:|:--------:|:--------------|
| event       | [Protocol::Light::Event](#Protocol_Light_Event)  | -    | 4 Byte   | LED light event    |
| color       | [Light::Color](#Light_Color)                     | -    | 3 Byte   | LED RGB Color  |
| command     | [Protocol::Command](05_structs.md#Protocol_Command) | -    | 2 Byte   | Command          |


<br>
<br>


## <a name="Protocol_Light_EventColorCommandIr">Protocol::Light::EventColorCommandIr</a>

LED light event(RGB) + Command + IR

```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorCommandIr
        {
            Protocol::Light::Event  event;
            Light::Color            color;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:------------------------------------------------:|:------------------------:|:--------:|:-------------------|
| event       | [Protocol::Light::Event](#Protocol_Light_Event)  | -                        | 4 Byte   | LED light event         |
| color       | [Light::Color](#Light_Color)                     | -                        | 3 Byte   | LED RGB Color       |
| command     | [Protocol::Command](05_structs.md#Protocol_Command) | -                        | 2 Byte   | Command               |
| irData      | uint32_t                                         | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | IR message data|


<br>
<br>


## <a name="Protocol_Light_EventColors">Protocol::Light::EventColors</a>

LED light event(Palette)

```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColors
        {
            Protocol::Light::Event  event;
            u8                      colors;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:---------:|:------------------------------------------------:|:-----:|:--------:|:------------------|
| event     | [Protocol::Light::Event](#Protocol_Light_Event)  | -     | 4 Byte   | LED light event        |
| colors    | [Light::Colors::Type](#Light_Colors)             | -     | 1 Byte   | LED Palette index |


<br>
<br>


## <a name="Protocol_Light_EventColorsCommand">Protocol::Light::EventColorsCommand</a>

LED light event(Palette) + Command

```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorsCommand
        {
            Protocol::Light::Event  event;
            u8                      colors;
            Protocol::Command       command;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:---------:|:-------------------------------------------------:|:-----:|:--------:|:------------------|
| event     | [Protocol::Light::Event](#Protocol_Light_Event)   | -     | 4 Byte   | LED light event        |
| colors    | [Light::Colors::Type](#Light_Colors)              | -     | 1 Byte   | LED Palette index |
| command   | [Protocol::Command](05_structs.md#Protocol_Command)  | -     | 2 Byte   | Command              |


<br>
<br>


## <a name="Protocol_Light_EventColorsCommandIr">Protocol::Light::EventColorsCommandIr</a>

LED light event(Palette) + Command + IR

```cpp
namespace Protocol
{
    namespace Light
    {
        struct EventColorsCommandIr
        {
            Protocol::Light::Event  event;
            u8                      colors;
            Protocol::Command       command;
            u32                     irData;
        };
    }
}
```

| Variable Name | Type      | Range  | Size     | Description    |
|:---------:|:-------------------------------------------------:|:-----------------------:|:--------:|:-------------------|
| event     | [Protocol::Light::Event](#Protocol_Light_Event)   | -                       | 4 Byte   | LED light event         |
| colors    | [Light::Colors::Type](#Light_Colors)              | -                       | 1 Byte   | LED Palette index  |
| command   | [Protocol::Command](05_structs.md#Protocol_Command)  | -                       | 2 Byte   | Command               |
| irData    | uint32_t                                          | 0x00000000 ~ 0xFFFFFFFF | 4 Byte   | IR message data|


<br>
<br>



---

<h3>PETRONE V2</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. ***Structs - Light***
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)
