**[E-DRONE](index.md)** / **Protocol** / **Structs** / **Light**

Modified : 2018.9.5

---

#### LED 제어와 관련된 정의 및 구조체들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}

<br>
<br>

# Definitions

<br>

<a name="Light_Drone_Mode"></a>
## Light::Drone::Mode::Type

드론 LED 동작 모드

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
                RearManual,             // 수동 제어
                RearHold,               // 지정한 색상을 계속 켬
                RearFlicker,            // 깜빡임
                RearFlickerDouble,      // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
                RearDimming,            // 밝기 제어하여 천천히 깜빡임
                
                BodyNone = 0x20,
                BodyManual,             // 수동 제어
                BodyHold,               // 지정한 색상을 계속 켬
                BodyFlicker,            // 깜빡임
                BodyFlickerDouble,      // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
                BodyDimming,            // 밝기 제어하여 천천히 깜빡임
                
                ANone = 0x30,
                AManual,                // 수동 제어
                AHold,                  // 지정한 색상을 계속 켬
                AFlicker,               // 깜빡임
                AFlickerDouble,         // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
                ADimming,               // 밝기 제어하여 천천히 깜빡임
                
                BNone = 0x40,
                BManual,                // 수동 제어
                BHold,                  // 지정한 색상을 계속 켬
                BFlicker,               // 깜빡임
                BFlickerDouble,         // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
                BDimming,               // 밝기 제어하여 천천히 깜빡임
                
                CNone = 0x50,
                CManual,                // 수동 제어
                CHold,                  // 지정한 색상을 계속 켬
                CFlicker,               // 깜빡임
                CFlickerDouble,         // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
                CDimming,               // 밝기 제어하여 천천히 깜빡임
                
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

드론 LED Flag

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
                CRed        = 0x0040,
                CGreen      = 0x0080,
                CBlue       = 0x0100,
            };
        }
    }
}
```


<br>
<br>


<a name="Light_Controller_Mode"></a>
## Light::Controller::Mode::Type

조종기 LED 동작 모드

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
                BodyNone = 0x10,
                BodyManual,         // 수동 제어
                BodyHold,           // 지정한 색상을 계속 켬
                BodyFlicker,        // 깜빡임
                BodyFlickerDouble,  // 깜빡임(두 번 깜빡이고 깜빡인 시간만큼 꺼짐)
                BodyDimming,        // 밝기 제어하여 천천히 깜빡임
                
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

드론 LED Flag

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

LED 팔레트 인덱스

드론과 조종기 내부에 정의된 팔레트의 색상 인덱스입니다.
의도보다 색상이 더 밝게 표현되기 때문에 테스트 후 사용하기를 권해드립니다.

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

RGB LED 색상 설정

0일 때 꺼지고 255일 때 가장 밝습니다.

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

| 변수 이름   | 형식    | 범위     | 크기     | 설명    |
|:-----------:|:-------:|:--------:|:--------:|:--------|
| r           | uint8_t | 0 ~ 255  | 1 Byte   | Red     |
| g           | uint8_t | 0 ~ 255  | 1 Byte   | Green   |
| b           | uint8_t | 0 ~ 255  | 1 Byte   | Blue    |


<br>
<br>


<a name="Protocol_Light_Manual"></a>
## Protocol::Light::Manual

LED 수동 제어

flag로 지정한 LED의 밝기를 변경합니다. 지정하지 않은 LED의 밝기는 그대로 유지됩니다. 밝기 값은 0일 때 꺼지며 값이 커질수록 밝아집니다.

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Manual
        {
            u16 flags;         // Flags 열거형을 조합한 값
            u8  brightness;    // 밝기
        };
    }
}
```

| 변수 이름   | 형식                                                 | 범위                                      | 크기     | 설명                          |
|:-----------:|:----------------------------------------------------:|:-----------------------------------------:|:--------:|:------------------------------|
| flags       | [Light::Drone::Flags](#Light_Drone_Flags)            | 0b0000000000000000 ~ 0b1111111111111111   | 2 Byte   | 드론 LED 선택 플래그 조합     |
|             | [Light::Controller::Flags](#Light_Controller_Flags)  | 0b0000000000000000 ~ 0b1111111111111111   |          | 조종기 LED 선택 플래그 조합   |
| brightness  | uint8_t                                              | 0 ~ 255                                   | 1 Byte   | 밝기                          |


<br>
<br>


<a name="Protocol_Light_Mode"></a>
## Protocol::Light::Mode

LED 모드 변경

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Mode
        {
            u8      mode;       // LED 모드
            u16     interval;   // LED 모드의 갱신 주기
        };
    }
}
```

| 변수 이름   | 형식                                                    | 범위       | 크기     | 설명                           |
|:-----------:|:-------------------------------------------------------:|:----------:|:--------:|:-------------------------------|
| mode        | [Light::Drone::Mode::Type](#Light_Drone_Mode)           | -          | 1 Byte   | 드론 LED 동작 모드             |
|             | [Light::Controller::Mode::Type](#Light_Controller_Mode) | -          |          | 조종기 LED 동작 모드           |
| interval    | uint16_t                                                | 0 ~ 65535  | 2 Byte   | 내부 밝기 제어 함수 호출 주기  |


<br>
<br>


<a name="Protocol_Light_ModeColor"></a>
## Protocol::Light::ModeColor

LED 모드 변경(RGB)

RGB 색상을 직접 지정하여 LED 동작 모드를 변경합니다.

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

| 변수 이름   | 형식                                           | 범위   | 크기     | 설명           |
|:-----------:|:----------------------------------------------:|:------:|:--------:|:---------------|
| mode        | [Protocol::Light::Mode](#Protocol_Light_Mode)  | -      | 3 Byte   | LED 동작 모드  |
| color       | [Light::Color](#Light_Color)                   | -      | 3 Byte   | LED RGB 색상   |


<br>
<br>


<a name="Protocol_Light_ModeColors"></a>
## Protocol::Light::ModeColors

LED 모드 변경(Palette)

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

| 변수 이름   | 형식                                           | 범위   | 크기     | 설명                |
|:-----------:|:----------------------------------------------:|:------:|:--------:|:--------------------|
| mode        | [Protocol::Light::Mode](#Protocol_Light_Mode)  | -      | 3 Byte   | LED 동작 모드       |
| colors      | [Light::Colors::Type](#Light_Colors)           | -      | 1 Byte   | LED 팔레트 인덱스   |


<br>
<br>


<a name="Protocol_Light_Event"></a>
## Protocol::Light::Event

LED 이벤트

```cpp
namespace Protocol
{
    namespace Light
    {
        struct Event
        {
            u8      event;      // LED 이벤트
            u16     interval;   // LED 이벤트 갱신 주기
            u8      repeat;     // LED 이벤트 반복 횟수
        };
    }
}
```

| 변수 이름  | 형식                                                    | 범위       | 크기   | 설명                          |
|:----------:|:-------------------------------------------------------:|:----------:|:------:|:------------------------------|
| event      | [Light::Drone::Mode::Type](#Light_Drone_Mode)           | -          | 1 Byte | 드론 LED 동작 모드            |
|            | [Light::Controller::Mode::Type](#Light_Controller_Mode) | -          |        | 조종기 LED 동작 모드          |
| interval   | UInt16                                                  | 0 ~ 65535  | 2 Byte | 내부 색상 변화 함수 호출 주기 |
| repeat     | UInt8                                                   | 0 ~ 255    | 1 Byte | 반복 횟수                     |


<br>
<br>


<a name="Protocol_Light_EventColor"></a>
## Protocol::Light::EventColor

LED 이벤트(RGB)

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

| 변수 이름   | 형식                                            | 범위  | 크기     | 설명           |
|:-----------:|:-----------------------------------------------:|:-----:|:--------:|:---------------|
| event       | [Protocol::Light::Event](#Protocol_Light_Event) | -     | 4 Byte   | LED 이벤트     |
| color       | [Light::Color](#Light_Color)                    | -     | 3 Byte   | LED RGB 색상   |


<br>
<br>


<a name="Protocol_Light_EventColors"></a>
## Protocol::Light::EventColors

LED 이벤트(Palette)

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

| 변수 이름 | 형식                                             | 범위  | 크기     | 설명              |
|:---------:|:------------------------------------------------:|:-----:|:--------:|:------------------|
| event     | [Protocol::Light::Event](#Protocol_Light_Event)  | -     | 4 Byte   | LED 이벤트        |
| colors    | [Light::Colors::Type](#Light_Colors)             | -     | 1 Byte   | LED 팔레트 인덱스 |


<br>
<br>


---

<h3>E-DRONE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. ***Structs - Light***
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)
