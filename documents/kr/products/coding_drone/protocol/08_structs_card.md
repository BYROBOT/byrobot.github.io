**[CODING DRONE](index.md)** / **Protocol** / **Structs** / **Card**

Modified : 2020.1.13

---

#### 카드 코딩과 관련된 정의 및 구조체들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>
<br>


# Definitions


<br>
<br>


<a name="Card_CardNameColor"></a>
## Card::CardNameColor::Type

카드 분류(색상)

```cpp
namespace CardNameColor
{
    enum Type
    {
        None            = 0x00,

        WhiteWhite      = 0x11,
        WhiteRed        = 0x12,
        WhiteYellow     = 0x13,
        WhiteGreen      = 0x14,
        WhiteCyan       = 0x15,
        WhiteBlue       = 0x16,
        WhiteMagenta    = 0x17,
        WhiteBlack      = 0x18,
        
        RedWhite        = 0x21,
        RedRed          = 0x22,
        RedYellow       = 0x23,
        RedGreen        = 0x24,
        RedCyan         = 0x25,
        RedBlue         = 0x26,
        RedMagenta      = 0x27,
        RedBlack        = 0x28,

        YellowWhite     = 0x31,
        YellowRed       = 0x32,
        YellowYellow    = 0x33,
        YellowGreen     = 0x34,
        YellowCyan      = 0x35,
        YellowBlue      = 0x36,
        YellowMagenta   = 0x37,
        YellowBlack     = 0x38,

        GreenWhite      = 0x41,
        GreenRed        = 0x42,
        GreenYellow     = 0x43,
        GreenGreen      = 0x44,
        GreenCyan       = 0x45,
        GreenBlue       = 0x46,
        GreenMagenta    = 0x47,
        GreenBlack      = 0x48,

        CyanWhite       = 0x51,
        CyanRed         = 0x52,
        CyanYellow      = 0x53,
        CyanGreen       = 0x54,
        CyanCyan        = 0x55,
        CyanBlue        = 0x56,
        CyanMagenta     = 0x57,
        CyanBlack       = 0x58,

        BlueWhite       = 0x61,
        BlueRed         = 0x62,
        BlueYellow      = 0x63,
        BlueGreen       = 0x64,
        BlueCyan        = 0x65,
        BlueBlue        = 0x66,
        BlueMagenta     = 0x67,
        BlueBlack       = 0x68,

        MagentaWhite    = 0x71,
        MagentaRed      = 0x72,
        MagentaYellow   = 0x73,
        MagentaGreen    = 0x74,
        MagentaCyan     = 0x75,
        MagentaBlue     = 0x76,
        MagentaMagenta  = 0x77,
        MagentaBlack    = 0x78,

        BlackWhite      = 0x81,
        BlackRed        = 0x82,
        BlackYellow     = 0x83,
        BlackGreen      = 0x84,
        BlackCyan       = 0x85,
        BlackBlue       = 0x86,
        BlackMagenta    = 0x87,
        BlackBlack      = 0x88,
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Card_CardNameCardCoding"></a>
## Card::CardNameCardCoding::Type

카드 코딩 모드

```cpp
namespace CardNameCardCoding
{
    enum Type
    {
        None                    = CardNameColor::None,
        
        // White - Mode
        CalibrationWhite        = CardNameColor::WhiteWhite,
        Card                    = CardNameColor::WhiteRed,          // 카드 코딩
        Motion                  = CardNameColor::WhiteYellow,       // 모션 코딩
        //Reserved_01           = CardNameColor::WhiteGreen,        // 
        //Reserved_02           = CardNameColor::WhiteCyan,         // 
        //Reserved_03           = CardNameColor::WhiteBlue,         // 
        //Reserved_04           = CardNameColor::WhiteMagenta,      // 
        Piano                   = CardNameColor::WhiteBlack,        // 피아노 모드
        
        // Red - Function
        CodingStart             = CardNameColor::RedWhite,          // 카드 입력 시작 - 카드 입력 중 White Dimming
        CodingEnd               = CardNameColor::RedRed,            // 카드 입력 종료 - 카드 입력 완료 시 White Hold
        FunctionStart           = CardNameColor::RedYellow,         // 함수 입력 시작 - 입력 중 Cyan Dimming
        FunctionEnd             = CardNameColor::RedGreen,          // 함수 입력 종료 - 카드 입력 완료 시 Cyan Hold
        FunctionCall            = CardNameColor::RedCyan,           // 함수 호출
        PlayMelody              = CardNameColor::RedBlue,           // 멜로디 호출
        Speed                   = CardNameColor::RedMagenta,        // 도리도리
        Wait1Sec                = CardNameColor::RedBlack,          // 1초 기다림
        
        // Yellow - LightBody
        LightBodyWhite          = CardNameColor::YellowWhite,
        LightBodyRed            = CardNameColor::YellowRed,
        LightBodyYellow         = CardNameColor::YellowYellow,
        LightBodyGreen          = CardNameColor::YellowGreen,
        LightBodyCyan           = CardNameColor::YellowCyan,
        LightBodyBlue           = CardNameColor::YellowBlue,
        LightBodyMagenta        = CardNameColor::YellowMagenta,
        LightBodyBlack          = CardNameColor::YellowBlack,
        
        // Green - 이착륙 및 이동 거리, 회전 각도 설정
        Takeoff                 = CardNameColor::GreenWhite,        // 이륙
        Landing                 = CardNameColor::GreenRed,          // 착륙
        Distance300             = CardNameColor::GreenYellow,       // 10cm
        Distance500             = CardNameColor::GreenGreen,        // 50cm
        Distance1000            = CardNameColor::GreenCyan,         // 1m
        Degree30                = CardNameColor::GreenBlue,         // 10도
        Degree45                = CardNameColor::GreenMagenta,      // 45도
        Degree90                = CardNameColor::GreenBlack,        // 90도
        
        // Cyan - Move - Basic
        MoveForward             = CardNameColor::CyanWhite,         // Front Obstacle
        MoveBackward            = CardNameColor::CyanRed,           // 착륙 시 사용, Ground Color Red
        MoveLeft                = CardNameColor::CyanYellow,        // 착륙 시 사용, Ground Color Yellow
        MoveRight               = CardNameColor::CyanGreen,         // 착륙 시 사용, Ground Color Green
        MoveUp                  = CardNameColor::CyanCyan,          // 착륙 시 사용, Ground Color Cyan
        MoveDown                = CardNameColor::CyanBlue,          // 착륙 시 사용, Ground Color Blue
        TurnLeft                = CardNameColor::CyanMagenta,
        TurnRight               = CardNameColor::CyanBlack,
        
        // Blue - If
        IfFindFrontObstacle     = CardNameColor::BlueWhite,
        IfFindGroundRed         = CardNameColor::BlueRed,
        IfFindGroundYellow      = CardNameColor::BlueYellow,
        IfFindGroundGreen       = CardNameColor::BlueGreen,
        IfFindGroundCyan        = CardNameColor::BlueCyan,
        IfFindGroundBlue        = CardNameColor::BlueBlue,
        IfElse                  = CardNameColor::BlueMagenta,
        IfEnd                   = CardNameColor::BlueBlack,
        
        // Magenta - Loop
        LoopStartInfinite       = CardNameColor::MagentaWhite,      // 중앙, 왼쪽 30도, 오른쪽 60도, 왼쪽 30도 
        LoopStart2              = CardNameColor::MagentaRed,
        LoopStart3              = CardNameColor::MagentaYellow,
        LoopStart4              = CardNameColor::MagentaGreen,
        LoopStart5              = CardNameColor::MagentaCyan,
        LoopStart10             = CardNameColor::MagentaBlue,
        LoopBreak               = CardNameColor::MagentaMagenta,
        LoopEnd                 = CardNameColor::MagentaBlack,      // 1초 기다림
        
        // Black - Melody
        C5                      = CardNameColor::BlackWhite,
        D5                      = CardNameColor::BlackRed,
        E5                      = CardNameColor::BlackYellow,
        F5                      = CardNameColor::BlackGreen,
        G5                      = CardNameColor::BlackCyan,
        A5                      = CardNameColor::BlackBlue,
        B5                      = CardNameColor::BlackMagenta,
        C6                      = CardNameColor::BlackBlack,
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Card_CardNamePiano"></a>
## Card::CardNamePiano::Type

피아노 모드

```cpp
namespace CardNamePiano
{
    enum Type
    {
        None                        = CardNameColor::None,
        
        // Red - Function
        RecordingStart              = CardNameColor::RedWhite,          // 사용자 정의 멜로디 입력 시작
        RecordingEnd                = CardNameColor::RedRed,            // 사용자 정의 멜로디 입력 종료
        Melody1                     = CardNameColor::RedYellow,         // 멜로디 1
        Melody2                     = CardNameColor::RedGreen,          // 멜로디 2
        Melody3                     = CardNameColor::RedCyan,           // 멜로디 3
        Play                        = CardNameColor::RedBlue,           // 저장한 멜로디 플레이
        MuteShort                   = CardNameColor::RedMagenta,        // 쉼표 0.5초
        Mute                        = CardNameColor::RedBlack,          // 쉼표 1초
        
        // Yellow - 3 Octave Sharp
        CS3                         = CardNameColor::YellowWhite,
        DS3                         = CardNameColor::YellowRed,
        //ES3                       = CardNameColor::YellowYellow,
        FS3                         = CardNameColor::YellowGreen,
        GS3                         = CardNameColor::YellowCyan,
        AS3                         = CardNameColor::YellowBlue,
        //BS3                       = CardNameColor::YellowMagenta,
        //CS4                       = CardNameColor::YellowBlack,
        
        // Green - 3 Octave
        C3                          = CardNameColor::GreenWhite,
        D3                          = CardNameColor::GreenRed,
        E3                          = CardNameColor::GreenYellow,
        F3                          = CardNameColor::GreenGreen,
        G3                          = CardNameColor::GreenCyan,
        A3                          = CardNameColor::GreenBlue,
        B3                          = CardNameColor::GreenMagenta,
        //C4                        = CardNameColor::GreenBlack,
        
        // Cyan - 4 Octave Sharp
        CS4                         = CardNameColor::CyanWhite,
        DS4                         = CardNameColor::CyanRed,
        //ES4                       = CardNameColor::CyanYellow,
        FS4                         = CardNameColor::CyanGreen,
        GS4                         = CardNameColor::CyanCyan,
        AS4                         = CardNameColor::CyanBlue,
        //BS4                       = CardNameColor::CyanMagenta,
        //CS5                       = CardNameColor::CyanBlack,
        
        // Blue - 4 Octave
        C4                          = CardNameColor::BlueWhite,
        D4                          = CardNameColor::BlueRed,
        E4                          = CardNameColor::BlueYellow,
        F4                          = CardNameColor::BlueGreen,
        G4                          = CardNameColor::BlueCyan,
        A4                          = CardNameColor::BlueBlue,
        B4                          = CardNameColor::BlueMagenta,
        //C5                        = CardNameColor::BlueBlack,
        
        // Magenta - 5 Octave Sharp
        CS5                         = CardNameColor::MagentaWhite,
        DS5                         = CardNameColor::MagentaRed,
        //ES5                       = CardNameColor::MagentaYellow,
        FS5                         = CardNameColor::MagentaGreen,
        GS5                         = CardNameColor::MagentaCyan,
        AS5                         = CardNameColor::MagentaBlue,
        //BS5                       = CardNameColor::MagentaMagenta,
        //CS6                       = CardNameColor::MagentaBlack,
        
        // Black - 5 Octave
        C5                          = CardNameColor::BlackWhite,
        D5                          = CardNameColor::BlackRed,
        E5                          = CardNameColor::BlackYellow,
        F5                          = CardNameColor::BlackGreen,
        G5                          = CardNameColor::BlackCyan,
        A5                          = CardNameColor::BlackBlue,
        B5                          = CardNameColor::BlackMagenta,
        //C6                        = CardNameColor::BlackBlack,
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Card_CardColor"></a>
## Card::CardColor::Type

카드 색 분류

```cpp
namespace CardColor
{
    enum Type
    {
        Unknown     = 0x00,
        White       = 0x01,
        Red         = 0x02,
        Yellow      = 0x03,
        Green       = 0x04,
        Cyan        = 0x05,
        Blue        = 0x06,
        Magenta     = 0x07,
        Black       = 0x08,
        Grey        = 0x09,
        
        EndOfType
    };
}
```

<br>
<br>


# Structs


<br>
<br>


<a name="Protocol_Card_Classify"></a>
## Protocol::Card::Classify

카드 색상 분류

Protocol::Card::Classify 클래스를 배열로 사용(순서대로 front, rear)

```cpp
namespace Protocol
{       
    namespace Card
    {
        class Classify
        {
        public:
            s8  cc[6][3][2];    // [r, y, g, c, b, m][h, s, l][min, max] - h는 +-60 범위 사용. s, l은 x100을 적용하여 0~100 범위 사용
            s8  l[2];           // [min, max] / min 이하는 black, white 이상은 white
        };
    }
}
```

| 변수 이름     | 형식       | 크기     | 범위      | 설명                      |
|:-------------:|:----------:|:--------:|:---------:|:--------------------------|
| cc[0][0][0]   | s8         | 1 Byte   | -60 ~ 60  | Red, Hue, Min             |
| cc[0][0][1]   | s8         | 1 Byte   | -60 ~ 60  | Red, Hue, Max             |
| cc[0][1][0]   | s8         | 1 Byte   | 0 ~ 100   | Red, Saturaton, Min       |
| cc[0][1][1]   | s8         | 1 Byte   | 0 ~ 100   | Red, Saturaton, Max       |
| cc[0][2][0]   | s8         | 1 Byte   | 0 ~ 100   | Red, Lightness, Min       |
| cc[0][2][1]   | s8         | 1 Byte   | 0 ~ 100   | Red, Lightness, Max       |
| cc[1][0][0]   | s8         | 1 Byte   | -60 ~ 60  | Yellow, Hue, Min          |
| cc[1][0][1]   | s8         | 1 Byte   | -60 ~ 60  | Yellow, Hue, Max          |
| cc[1][1][0]   | s8         | 1 Byte   | 0 ~ 100   | Yellow, Saturaton, Min    |
| cc[1][1][1]   | s8         | 1 Byte   | 0 ~ 100   | Yellow, Saturaton, Max    |
| cc[1][2][0]   | s8         | 1 Byte   | 0 ~ 100   | Yellow, Lightness, Min    |
| cc[1][2][1]   | s8         | 1 Byte   | 0 ~ 100   | Yellow, Lightness, Max    |
| cc[2][0][0]   | s8         | 1 Byte   | -60 ~ 60  | Green, Hue, Min           |
| cc[2][0][1]   | s8         | 1 Byte   | -60 ~ 60  | Green, Hue, Max           |
| cc[2][1][0]   | s8         | 1 Byte   | 0 ~ 100   | Green, Saturaton, Min     |
| cc[2][1][1]   | s8         | 1 Byte   | 0 ~ 100   | Green, Saturaton, Max     |
| cc[2][2][0]   | s8         | 1 Byte   | 0 ~ 100   | Green, Lightness, Min     |
| cc[2][2][1]   | s8         | 1 Byte   | 0 ~ 100   | Green, Lightness, Max     |
| cc[3][0][0]   | s8         | 1 Byte   | -60 ~ 60  | Cyan, Hue, Min            |
| cc[3][0][1]   | s8         | 1 Byte   | -60 ~ 60  | Cyan, Hue, Max            |
| cc[3][1][0]   | s8         | 1 Byte   | 0 ~ 100   | Cyan, Saturaton, Min      |
| cc[3][1][1]   | s8         | 1 Byte   | 0 ~ 100   | Cyan, Saturaton, Max      |
| cc[3][2][0]   | s8         | 1 Byte   | 0 ~ 100   | Cyan, Lightness, Min      |
| cc[3][2][1]   | s8         | 1 Byte   | 0 ~ 100   | Cyan, Lightness, Max      |
| cc[4][0][0]   | s8         | 1 Byte   | -60 ~ 60  | Blue, Hue, Min            |
| cc[4][0][1]   | s8         | 1 Byte   | -60 ~ 60  | Blue, Hue, Max            |
| cc[4][1][0]   | s8         | 1 Byte   | 0 ~ 100   | Blue, Saturaton, Min      |
| cc[4][1][1]   | s8         | 1 Byte   | 0 ~ 100   | Blue, Saturaton, Max      |
| cc[4][2][0]   | s8         | 1 Byte   | 0 ~ 100   | Blue, Lightness, Min      |
| cc[4][2][1]   | s8         | 1 Byte   | 0 ~ 100   | Blue, Lightness, Max      |
| cc[5][0][0]   | s8         | 1 Byte   | -60 ~ 60  | Magenta, Hue, Min         |
| cc[5][0][1]   | s8         | 1 Byte   | -60 ~ 60  | Magenta, Hue, Max         |
| cc[5][1][0]   | s8         | 1 Byte   | 0 ~ 100   | Magenta, Saturaton, Min   |
| cc[5][1][1]   | s8         | 1 Byte   | 0 ~ 100   | Magenta, Saturaton, Max   |
| cc[5][2][0]   | s8         | 1 Byte   | 0 ~ 100   | Magenta, Lightness, Min   |
| cc[5][2][1]   | s8         | 1 Byte   | 0 ~ 100   | Magenta, Lightness, Max   |
| l[0]          | s8         | 1 Byte   | 0 ~ 100   | Lightness Min(Black)      |
| l[1]          | s8         | 1 Byte   | 0 ~ 100   | Lightness Max(White)      |


<br>
<br>


<a name="Protocol_Card_Range"></a>
## Protocol::Card::Range

RGB Raw 데이터의 출력 범위(캘리브레이션 시 검정색과 흰 색을 읽혔을 때의 출력값을 기준으로 사용)

```cpp
namespace Protocol
{       
    namespace Card
    {
        class Range
        {
        public:
            s16     range[2][3][2];     // [Front/Rear][R/G/B][Min/Max]     24 byte
        };
    }
}
```

| 변수 이름       | 형식          | 크기     | 범위          | 설명                 |
|:---------------:|:-------------:|:--------:|:-------------:|:---------------------|
| range[0][0][1]  | int16_t       | 24 Byte  | 0 ~ 4095      | Front, Red, Min      |
| range[0][0][2]  | int16_t       | 24 Byte  | 0 ~ 4095      | Front, Red, Max      |
| range[0][1][1]  | int16_t       | 24 Byte  | 0 ~ 4095      | Front, Green, Min    |
| range[0][1][2]  | int16_t       | 24 Byte  | 0 ~ 4095      | Front, Green, Max    |
| range[0][2][1]  | int16_t       | 24 Byte  | 0 ~ 4095      | Front, Blue, Min     |
| range[0][2][2]  | int16_t       | 24 Byte  | 0 ~ 4095      | Front, Blue, Max     |
| range[1][0][1]  | int16_t       | 24 Byte  | 0 ~ 4095      | Rear, Red, Min       |
| range[1][0][2]  | int16_t       | 24 Byte  | 0 ~ 4095      | Rear, Red, Max       |
| range[1][1][1]  | int16_t       | 24 Byte  | 0 ~ 4095      | Rear, Green, Min     |
| range[1][1][2]  | int16_t       | 24 Byte  | 0 ~ 4095      | Rear, Green, Max     |
| range[1][2][1]  | int16_t       | 24 Byte  | 0 ~ 4095      | Rear, Blue, Min      |
| range[1][2][2]  | int16_t       | 24 Byte  | 0 ~ 4095      | Rear, Blue, Max      |


<br>
<br>


<a name="Protocol_Card_Raw"></a>
## Protocol::Card::Raw

카드 Raw 데이터

rgbRaw : ADC에서 읽은 RGB의 RAW 데이터<br>
rgb : rgbRaw를 range를 기준으로 0 ~ 255 사이의 값으로 변환한 값<br>
hsvl : rgb를 hsv, hsl로 변환한 값<br>
color : hsvl 값을 Color Classify에 설정된 기준으로 판별한 색<br>
card : 카드(front 상위 4비트, rear 하위 4비트)

```cpp
namespace Protocol
{       
    namespace Card
    {
        class Raw
        {
            public:
                s16     rgbRaw[2][3];   // [Front/Rear][R/G/B]  12 byte
                u8      rgb[2][3];      // [Front/Rear][R/G/B]   6 byte
                s16     hsvl[2][4];     // [Front/Rear][R/G/B]  12 byte
                u8      color[2];       // [Front/Rear]          2 byte
                u8      card;           //                       1 byte
        };
    }
}
```

| 변수 이름     | 형식       | 크기     | 범위             | 설명                |
|:-------------:|:----------:|:--------:|:----------------:|:--------------------|
| rgbRaw[0][0]  | int16_t    | 2 Byte   | 0 ~ 4095         | Raw, Front, Red     |
| rgbRaw[0][1]  | int16_t    | 2 Byte   | 0 ~ 4095         | Raw, Front, Green   |
| rgbRaw[0][2]  | int16_t    | 2 Byte   | 0 ~ 4095         | Raw, Front, Blue    |
| rgbRaw[1][0]  | int16_t    | 2 Byte   | 0 ~ 4095         | Raw, Rear, Red      |
| rgbRaw[1][1]  | int16_t    | 2 Byte   | 0 ~ 4095         | Raw, Rear, Green    |
| rgbRaw[1][2]  | int16_t    | 2 Byte   | 0 ~ 4095         | Raw, Rear, Blue     |
| rgb[0][0]     | int16_t    | 1 Byte   | 0 ~ 255          | Front, Red          |
| rgb[0][1]     | int16_t    | 1 Byte   | 0 ~ 255          | Front, Green        |
| rgb[0][2]     | int16_t    | 1 Byte   | 0 ~ 255          | Front, Blue         |
| rgb[1][0]     | int16_t    | 1 Byte   | 0 ~ 255          | Rear, Red           |
| rgb[1][1]     | int16_t    | 1 Byte   | 0 ~ 255          | Rear, Green         |
| rgb[1][2]     | int16_t    | 1 Byte   | 0 ~ 255          | Rear, Blue          |
| hsvl[0][0]    | int16_t    | 2 Byte   | 0 ~ 360          | Front, Hue          |
| hsvl[0][1]    | int16_t    | 2 Byte   | 0 ~ 100          | Front, Saturation   |
| hsvl[0][2]    | int16_t    | 2 Byte   | 0 ~ 100          | Front, Value        |
| hsvl[0][3]    | int16_t    | 2 Byte   | 0 ~ 100          | Front, Lightness    |
| hsvl[1][0]    | int16_t    | 2 Byte   | 0 ~ 360          | Rear, Hue           |
| hsvl[1][1]    | int16_t    | 2 Byte   | 0 ~ 100          | Rear, Saturation    |
| hsvl[1][2]    | int16_t    | 2 Byte   | 0 ~ 100          | Rear, Value         |
| hsvl[1][3]    | int16_t    | 2 Byte   | 0 ~ 100          | Rear, Lightness     |
| color[0]      | [Card::CardColor::Type](#Card_CardColor) | 1 Byte   | -                | Front Color               |
| color[1]      | [Card::CardColor::Type](#Card_CardColor) | 1 Byte   | -                | Rear Color                |
| card          | [Card::CardNameColor::Type](#Card_CardNameColor), <br>[Card::CardNameCardCoding::Type](#Card_CardNameCardCoding), <br>[Card::CardNamePiano::Type](#Card_CardNamePiano)  | 1 Byte   | - | 카드 |


<br>
<br>


<a name="Protocol_Card_Color"></a>
## Protocol::Card::Color

카드 데이터(무선 통신에 사용하려고 Raw에서 크기를 줄임)

hsvl : rgb를 hsv, hsl로 변환한 값<br>
color : hsvl 값을 Color Classify에 설정된 기준으로 판별한 색<br>
card : 카드(front 상위 4비트, rear 하위 4비트)

```cpp
namespace Protocol
{       
    namespace Card
    {
        class Color
        {
            public:
                s16     hsvl[2][4];     // [Front/Rear][R/G/B]  12 byte
                u8      color[2];       // [Front/Rear]          2 byte
                u8      card;           //                       1 byte
        };
    }
}
```

| 변수 이름     | 형식       | 크기     | 범위             | 설명                |
|:-------------:|:----------:|:--------:|:----------------:|:--------------------|
| hsvl[0][0]    | int16_t    | 2 Byte   | 0 ~ 360          | Front, Hue          |
| hsvl[0][1]    | int16_t    | 2 Byte   | 0 ~ 100          | Front, Saturation   |
| hsvl[0][2]    | int16_t    | 2 Byte   | 0 ~ 100          | Front, Value        |
| hsvl[0][3]    | int16_t    | 2 Byte   | 0 ~ 100          | Front, Lightness    |
| hsvl[1][0]    | int16_t    | 2 Byte   | 0 ~ 360          | Rear, Hue           |
| hsvl[1][1]    | int16_t    | 2 Byte   | 0 ~ 100          | Rear, Saturation    |
| hsvl[1][2]    | int16_t    | 2 Byte   | 0 ~ 100          | Rear, Value         |
| hsvl[1][3]    | int16_t    | 2 Byte   | 0 ~ 100          | Rear, Lightness     |
| color[0]      | [Card::CardColor::Type](#Card_CardColor) | 1 Byte   | -                | Front Color               |
| color[1]      | [Card::CardColor::Type](#Card_CardColor) | 1 Byte   | -                | Rear Color                |
| card          | [Card::CardNameColor::Type](#Card_CardNameColor), <br>[Card::CardNameFunction::Type](#Card_CardNameFunction)  | 1 Byte   | - | 카드 |


<br>
<br>


<a name="Protocol_Card_Raw"></a>
## Protocol::Card::Raw

카드 목록

```cpp
namespace Protocol
{       
    namespace Card
    {
        class List
        {
            public:
                u8      index;          // 현재 실행중인 카드의 인덱스
                u8      size;           // 입력된 카드의 총 갯수
                
                u8      cardIndex;      // 현재 전송하는 카드 배열의 시작 번호
                u8      card[12];
        };
    }
}
```

| 변수 이름     | 형식      | 크기     | 범위     | 설명                                |
|:-------------:|:---------:|:--------:|:--------:|:------------------------------------|
| index         | uint8_t   | 1 Byte   | 0 ~ 100  | 현재 실행중인 카드의 인덱스         |
| size          | uint8_t   | 1 Byte   | 0 ~ 100  | 입력된 카드의 총 갯수               |
| cardIndex     | uint8_t   | 1 Byte   | 0 ~ 100  | 현재 전송하는 카드 배열의 시작 번호 |
| card[12]      | [Card::CardNameColor::Type](#Card_CardNameColor), <br>[Card::CardNameFunction::Type](#Card_CardNameFunction)  | 12 Byte   | - | 카드 목록 |


<br>
<br>



---

<h3>CODING DRONE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)
8. ***Structs - Card***

<br>

[Index](index.md)
