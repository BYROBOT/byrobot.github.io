**[Coding Drone Plus](index.md)** / **Protocol** / **Structs** / **Light**

Modified : 2026.1.29

---

#### Introduce the LED control definitions and structures

---

* Table of contents
  * [LED control (0x24 ~ 0x27)](#LED_control)
    * [LED_rainbow (0x24)](#LED_rainbow_0x24)
    * [LED_flicker (0x25)](#LED_flicker_0x25)
    * [LED_random (0x26)](#LED_random_0x26)
    * [LED_individual (0x27)](#LED_individual_0x27)

<br>
<br>

<a name="LED_control"></a>
## LED control (0x24 ~ 0x27)

Coding Drone Plus LED control is handled by separate packet-based commands.
See the examples below.

<br>
<br>

<a name="LED_rainbow_0x24"></a>
### LED_rainbow (0x24)

Format:

```
0A 55 24 05 [from] [to] [r] [g] [b] [interval_L] [interval_H] [crc] [crc]
```

Example:

```
0A 55 24 05 20 10 FF AA 00 0A 00 66 30
```

- RGB = 255, 170, 0
- Interval = 10 ms

- The RGB values are not used in this mode. The rainbow effect always starts from red, so (0,0,0) is acceptable.
- Interval represents the color transition step duration.
  Recommended default: 10 ms
  Increasing to 20, 30 makes the effect 2×, 3× slower.

<br>
<br>

<a name="LED_flicker_0x25"></a>
### LED_flicker (0x25)

Format:

```
0A 55 25 05 [from] [to] [r] [g] [b] [interval_L] [interval_H] [crc] [crc]
```

Example:

```
0A 55 25 05 20 10 FF 00 FF 64 00 DE BE
```

- RGB = 255, 0, 255
- Interval = 100 ms

- The LED turns on with the specified RGB color for [interval] ms, then turns off for the same duration.
- Total cycle period = 2 × interval
  (e.g., 100 ms results in a 200 ms full on/off cycle)

<br>
<br>

<a name="LED_random_0x26"></a>
### LED_random (0x26)

Format:

```
0A 55 26 05 [from] [to] [r] [g] [b] [interval_L] [interval_H] [crc] [crc]
```

- LEDs change to random colors approximately every 10 ms.
- Both RGB and interval parameters are ignored in this mode.

<br>
<br>

<a name="LED_individual_0x27"></a>
### LED_individual (0x27)

Format:

```
0A 55 27 11 [from] [to]
[LED0_R] [LED0_G] [LED0_B]
[LED1_R] [LED1_G] [LED1_B]
[LED2_R] [LED2_G] [LED2_B]
[LED3_R] [LED3_G] [LED3_B]
[LED4_R] [LED4_G] [LED4_B]
[interval_L] [interval_H] [crc] [crc]
```

- RGB values for LED 0 are not used.
- RGB values for LED 1, 2, 3, and 4 directly control the LED colors.
- Interval sets the update timing.

<br>
<br>

<details markdown="1">
<summary><b>Legacy (rarely used): Protocol::Light definitions and structs</b></summary>

# Definitions

<br>

<a name="Light_Drone_Mode"></a>
## Light::Drone::Mode::Type

Drone LED mode

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
                
                RearNone = 0x10,
                RearManual,             // manual control
                RearHold,               // keep the specified color on
                RearFlicker,            // flicker
                RearFlickerDouble,      // double flicker (flicker twice, then off for the same time as flicker)
                RearDimming,            // dimming (slow flicker by brightness control)
                RearSunrise,            // sunrise (gradually brighter from off)
                RearSunset,             // sunset (gradually darker from on)
                
                BodyNone = 0x20,
                BodyManual,             // manual control
                BodyHold,               // keep the specified color on
                BodyFlicker,            // flicker
                BodyFlickerDouble,      // double flicker (flicker twice, then off for the same time as flicker)
                BodyDimming,            // dimming (slow flicker by brightness control)
                BodySunrise,            // sunrise (gradually brighter from off)
                BodySunset,             // sunset (gradually darker from on)
                
                ANone = 0x30,
                AManual,                // manual control
                AHold,                  // keep the specified color on
                AFlicker,               // flicker
                AFlickerDouble,         // double flicker (flicker twice, then off for the same time as flicker)
                ADimming,               // dimming (slow flicker by brightness control)
                ASunrise,               // sunrise (gradually brighter from off)
                ASunset,                // sunset (gradually darker from on)
                
                BNone = 0x40,
                BManual,                // manual control
                BHold,                  // keep the specified color on
                BFlicker,               // flicker
                BFlickerDouble,         // double flicker (flicker twice, then off for the same time as flicker)
                BDimming,               // dimming (slow flicker by brightness control)
                BSunrise,               // sunrise (gradually brighter from off)
                BSunset,                // sunset (gradually darker from on)
                
                EndOfType
            };
        }
    }
}
```


<br>
<br>


<a name="Light_Drone_Flags"></a>
## Light::Drone::Flags::Type

Drone LED flag

```cpp
namespace Light
{
    namespace Drone
    {
        namespace Flags
        {
            enum Type
            {
                None        = 0x0000,
                
                Rear        = 0x0001,
                BodyRed     = 0x0002,
                BodyGreen   = 0x0004,
                BodyBlue    = 0x0008,
                
                A           = 0x0010,
                B           = 0x0020,
            };
        }
    }
}
```


<br>
<br>


<a name="Light_Controller_Mode"></a>
## Light::Controller::Mode::Type

Controller LED mode

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
                
                // Body
                BodyNone = 0x20,
                BodyManual,         // manual control
                BodyHold,           // keep the specified color on
                BodyFlicker,        // flicker
                BodyFlickerDouble,  // double flicker (flicker twice, then off for the same time as flicker)
                BodyDimming,        // dimming (slow flicker by brightness control)
                BodySunrise,        // sunrise (gradually brighter from off)
                BodySunset,         // sunset (gradually darker from on)
                BodyRainbow,        // rainbow
                BodyRainbow2,       // rainbow
                
                EndOfType
            };
        }
    }
}
```


<br>
<br>


<a name="Light_Controller_Flags"></a>
## Light::Controller::Flags::Type

Controller LED flag

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
                
                BodyRed     = 0x01,
                BodyGreen   = 0x02,
                BodyBlue    = 0x04,
            };
        }
    }
}
```


<br>
<br>


<a name="Light_Colors"></a>
## Light::Colors::Type

LED palette index

This is the color index of the palette defined inside the drone and controller.
Because the color may look brighter than intended, we recommend testing before use.

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


<a name="Light_Color"></a>
## Light::Color

RGB LED color

0 turns off and 255 is the brightest.

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

| Name | Type | Size | Range | Description |
|:-----------:|:-------:|:--------:|:--------:|:--------|
| r           | uint8_t | 1 Byte   | 0 ~ 255  | Red     |
| g           | uint8_t | 1 Byte   | 0 ~ 255  | Green   |
| b           | uint8_t | 1 Byte   | 0 ~ 255  | Blue    |


<br>
<br>


<a name="Protocol_Light_Manual"></a>
## Protocol::Light::Manual

LED manual control

Changes the brightness of LEDs specified by `flags`. LEDs not specified keep their brightness. Brightness is off at 0 and becomes brighter as the value increases.

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Manual
        {
            u16 flags;         // Combination of Flags enum
            u8  brightness;    // Brightness
        };
    }
}
```

| Name | Type | Size | Range | Description |
|:-----------:|:----------------------------------------------------:|:--------:|:-----------------------------------------:|:------------------------------|
| flags | [Light::Drone::Flags](#Light_Drone_Flags) | 2 Byte | 0b0000000000000000 ~ 0b1111111111111111 | Drone LED flag combination |
|      | [Light::Controller::Flags](#Light_Controller_Flags) |        | 0b0000000000000000 ~ 0b1111111111111111 | Controller LED flag combination |
| brightness | uint8_t | 1 Byte | 0 ~ 255 | Brightness |


<br>
<br>


<a name="Protocol_Light_Mode"></a>
## Protocol::Light::Mode

Change LED mode

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Mode
        {
            u8      mode;       // LED mode
            u16     interval;   // Update interval for LED mode
        };
    }
}
```

| Name | Type | Size | Range | Description |
|:-----------:|:-------------------------------------------------------:|:--------:|:----------:|:-------------------------------|
| mode | [Light::Drone::Mode::Type](#Light_Drone_Mode) | 1 Byte | - | Drone LED mode |
|      | [Light::Controller::Mode::Type](#Light_Controller_Mode) |        | - | Controller LED mode |
| interval | uint16_t | 2 Byte | 0 ~ 65535 | Internal brightness update interval |


<br>
<br>


<a name="Protocol_Light_ModeColor"></a>
## Protocol::Light::ModeColor

Change LED mode (RGB)

Changes the LED mode by specifying the RGB color directly.

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

| Name | Type | Size | Range | Description |
|:-----------:|:----------------------------------------------:|:--------:|:------:|:---------------|
| mode | [Protocol::Light::Mode](#Protocol_Light_Mode) | 3 Byte | - | LED mode |
| color | [Light::Color](#Light_Color) | 3 Byte | - | LED RGB color |


<br>
<br>


<a name="Protocol_Light_ModeColors"></a>
## Protocol::Light::ModeColors

Change LED mode (Palette)

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

| Name | Type | Size | Range | Description |
|:-----------:|:----------------------------------------------:|:--------:|:------:|:--------------------|
| mode | [Protocol::Light::Mode](#Protocol_Light_Mode) | 3 Byte | - | LED mode |
| colors | [Light::Colors::Type](#Light_Colors) | 1 Byte | - | LED palette index |


<br>
<br>


<a name="Protocol_Light_Event"></a>
## Protocol::Light::Event

LED event

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Event
        {
            u8      event;      // LED event
            u16     interval;   // Update interval for LED event
            u8      repeat;     // Repeat count
        };
    }
}
```

| Name | Type | Size | Range | Description |
|:----------:|:-------------------------------------------------------:|:------:|:----------:|:------------------------------|
| event | [Light::Drone::Mode::Type](#Light_Drone_Mode) | 1 Byte | - | Drone LED mode |
|       | [Light::Controller::Mode::Type](#Light_Controller_Mode) |        | - | Controller LED mode |
| interval | UInt16 | 2 Byte | 0 ~ 65535 | Internal color update interval |
| repeat | UInt8 | 1 Byte | 0 ~ 255 | Repeat count |


<br>
<br>


<a name="Protocol_Light_EventColor"></a>
## Protocol::Light::EventColor

LED event (RGB)

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

| Name  | Type                                           | Size   | Range | Description     |
|:-----------:|:-----------------------------------------------:|:--------:|:-----:|:---------------|
| event | [Protocol::Light::Event](#Protocol_Light_Event) | 4 Byte | - | LED event      |
| color | [Light::Color](#Light_Color)                    | 3 Byte | - | LED RGB color  |


<br>
<br>


<a name="Protocol_Light_EventColors"></a>
## Protocol::Light::EventColors

LED event (Palette)

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

| Name  | Type                                            | Size   | Range | Description       |
|:---------:|:------------------------------------------------:|:--------:|:-----:|:------------------|
| event  | [Protocol::Light::Event](#Protocol_Light_Event)  | 4 Byte | - | LED event         |
| colors | [Light::Colors::Type](#Light_Colors)             | 1 Byte | - | LED palette index |


<br>
<br>


</details>

---

<h3>Coding Drone Plus</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. ***Structs - Light***
<!-- 7. [Structs - Display](07_structs_display.md) -->

<br>

[Index](index.md)
