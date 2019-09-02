**[E-DRIVE](index.md)** / **Protocol** / **Structs** / **Card**

Modified : 2019.9.2

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


<a name="Card_CardNameFunction"></a>
## Card::CardNameFunction::Type

카드 분류(기능)

```cpp
namespace CardNameFunction
{
    enum Type
    {
        None                            = CardNameColor::None,

        // White - Mode
        RemoteControl               = CardNameColor::WhiteWhite,
        CardCodingStart             = CardNameColor::WhiteRed,      // 카드 입력 시작
        CardCodingEnd               = CardNameColor::WhiteYellow,   // 카드 입력 종료
        FunctionStart               = CardNameColor::WhiteGreen,    // 함수 입력 시작
        FunctionEnd                 = CardNameColor::WhiteCyan,     // 함수 입력 종료
        FunctionCall                = CardNameColor::WhiteBlue,     // 함수 호출
        LineTracer                  = CardNameColor::WhiteMagenta,  // 라인 트레이서 시작
        Piano                       = CardNameColor::WhiteBlack,    // 피아노 모드
        
        
        // Red - LightBody
        LightBodyWhite              = CardNameColor::RedWhite,
        LightBodyRed                = CardNameColor::RedRed,
        LightBodyYellow             = CardNameColor::RedYellow,
        LightBodyGreen              = CardNameColor::RedGreen,
        LightBodyCyan               = CardNameColor::RedCyan,
        LightBodyBlue               = CardNameColor::RedBlue,
        LightBodyMagenta            = CardNameColor::RedMagenta,
        LightBodyBlack              = CardNameColor::RedBlack,
        
        // Yellow - Light On
        LightOnHighBeam             = CardNameColor::YellowWhite,
        LightOnEmergencyLight       = CardNameColor::YellowRed,
        LightOnLowBeam              = CardNameColor::YellowYellow,
        LightOnLeftTurnSignal       = CardNameColor::YellowGreen,
        LightOnRightTurnSignal      = CardNameColor::YellowCyan,
        LightOnTailLight            = CardNameColor::YellowBlue,
        LightOffTailLight           = CardNameColor::YellowMagenta,
        LightOffLowBeam             = CardNameColor::YellowBlack,
        
        // Green - Move - Basic
        MoveForward                 = CardNameColor::GreenWhite,
        MoveForward1Block           = CardNameColor::GreenRed,
        MoveTurnLeft180Deg          = CardNameColor::GreenYellow,
        MoveTurnLeft90Deg           = CardNameColor::GreenGreen,
        MoveTurnRight90Deg          = CardNameColor::GreenCyan,
        MoveBackward1Block          = CardNameColor::GreenBlue,
        MoveBackward                = CardNameColor::GreenMagenta,
        MoveStop                    = CardNameColor::GreenBlack,
        
        // Cyan - If
        IfFindFrontObstacle         = CardNameColor::CyanWhite,         // Front Obstacle
        IfFindGroundRed             = CardNameColor::CyanRed,           // Ground Color Red
        IfFindGroundYellow          = CardNameColor::CyanYellow,        // Ground Color Yellow
        IfFindGroundGreen           = CardNameColor::CyanGreen,         // Ground Color Green
        IfFindGroundCyan            = CardNameColor::CyanCyan,          // Ground Color Cyan
        IfFindGroundBlue            = CardNameColor::CyanBlue,          // Ground Color Blue
        IfElse                      = CardNameColor::CyanMagenta,
        IfEnd                       = CardNameColor::CyanBlack,
        
        // Blue - Loop
        LoopStartInfinite           = CardNameColor::BlueWhite,
        LoopStart2                  = CardNameColor::BlueRed,
        LoopStart3                  = CardNameColor::BlueYellow,
        LoopStart4                  = CardNameColor::BlueGreen,
        LoopStart5                  = CardNameColor::BlueCyan,
        LoopStart10                 = CardNameColor::BlueBlue,
        LoopBreak                   = CardNameColor::BlueMagenta,
        LoopEnd                     = CardNameColor::BlueBlack,
        
        // Magenta - Preset
        presetYawing60Deg           = CardNameColor::MagentaWhite,      // 중앙, 왼쪽 30도, 오른쪽 60도, 왼쪽 30도 
        presetZigZag                = CardNameColor::MagentaRed,        // 중앙, 왼쪽 90도, 오른쪽 180도, 왼쪽 90도 
        presetWave                  = CardNameColor::MagentaYellow,
        presetTornadoLeft           = CardNameColor::MagentaGreen,
        presetTornadoRight          = CardNameColor::MagentaCyan,
        presetCircleLeft            = CardNameColor::MagentaBlue,
        presetCircleRight           = CardNameColor::MagentaMagenta,
        presetWait1Sec              = CardNameColor::MagentaBlack,      // 1초 기다림
        
        // Black - Melody
        Melody1                     = CardNameColor::BlackWhite,
        Melody2                     = CardNameColor::BlackRed,
        Melody3                     = CardNameColor::BlackYellow,
        Melody4                     = CardNameColor::BlackGreen,
        Melody5                     = CardNameColor::BlackCyan,
        Melody6                     = CardNameColor::BlackBlue,
        Melody7                     = CardNameColor::BlackMagenta,
        Melody8                     = CardNameColor::BlackBlack,
        
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

```cpp
namespace Protocol
{       
    namespace Card
    {
        class Classify
        {
        public:
            u16     hRY;        // Hue 경계     Red-Yellow
            u16     hYG;        // Hue 경계  Yellow-Green
            u16     hGC;        // Hue 경계   Green-Cyan
            u16     hCB;        // Hue 경계    Cyan-Blue
            u16     hBM;        // Hue 경계    Blue-Magenta
            u16     hMR;        // Hue 경계 Magenta-Red
            
            float   lBlack;     // Black으로 인식할 Lightness
            float   lWhite;     // White로 인식할 Lightness
            float   sUnknown;   // Unknown으로 처리할 Saturation
        };
    }
}
```

| 변수 이름  | 형식       | 크기     | 범위     | 설명                      |
|:----------:|:----------:|:--------:|:--------:|:--------------------------|
| hRY        | int16_t    | 2 Byte   | 0 ~ 360  | Hue 경계     Red-Yellow   |
| hYG        | int16_t    | 2 Byte   | 0 ~ 360  | Hue 경계  Yellow-Green    |
| hGC        | int16_t    | 2 Byte   | 0 ~ 360  | Hue 경계   Green-Cyan     |
| hCB        | int16_t    | 2 Byte   | 0 ~ 360  | Hue 경계    Cyan-Blue     |
| hBM        | int16_t    | 2 Byte   | 0 ~ 360  | Hue 경계    Blue-Magenta  |
| hMR        | int16_t    | 2 Byte   | 0 ~ 360  | Hue 경계 Magenta-Red      |
| lBlack     | float      | 4 Byte   | 0 ~ 1.0  | Black으로 인식할 Lightness    |
| lWhite     | float      | 4 Byte   | 0 ~ 1.0  | White로 인식할 Lightness      |
| sUnknown   | float      | 4 Byte   | 0 ~ 1.0  | Unknown으로 처리할 Saturation |


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

| 변수 이름       | 형식          | 크기     | 범위          | 설명                               |
|:---------------:|:-------------:|:--------:|:-------------:|:-----------------------------------|
| range[2][3][2]  | int16_t       | 24 Byte  | 0 ~ 4095      | ADC RAW 출력 값의 최소, 최대 값    |


<br>
<br>


<a name="Protocol_Card_Raw"></a>
## Protocol::Card::Raw

카드 Raw 데이터

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

| 변수 이름     | 형식                                      | 크기     | 범위             | 설명           |
|:-------------:|:-----------------------------------------:|:--------:|:----------------:|:---------------|
| rgbRaw[2][3]  | int16_t                                   | 12 Byte  | 0 ~ 4095         | RGB Raw        |
| rgb[2][3]     | uint8_t                                   | 6 Byte   | 0 ~ 255          | 설정된 RGB 범위를 기준으로 0 ~ 255 사이의 값으로 변경한 값       |
| hsvl[2][4]    | int16_t                                   | 12 Byte  | 0 ~ 360, 0 ~ 100 | rgb 데이터를 Hue, Saturation, Value, Lightness 값으로 변환한 것  |
| color[2]      | [Card::CardColor::Type](#Card_CardColor)  | 2 Byte   | -                | hsvl 값을 Classify에 설정된 기준에 따라 분류한 색                |
| card          | [Card::CardNameColor::Type](#Card_CardNameColor), [Card::CardNameFunction::Type](#Card_CardNameFunction)  | 1 Byte   | - | 앞 센서의 색을 상위 4비트, 뒤 센서의 색을 하위 4비트에 할당하여 만든 카드 값  |


<br>
<br>


<a name="Protocol_Card_Color"></a>
## Protocol::Card::Color

카드 데이터(무선 통신에 사용하려고 Raw에서 크기를 줄임)

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

| 변수 이름     | 형식                                      | 크기     | 범위             | 설명                                                             |
|:-------------:|:-----------------------------------------:|:--------:|:----------------:|:-----------------------------------------------------------------|
| hsvl[2][4]    | int16_t                                   | 12 Byte  | 0 ~ 360, 0 ~ 100 | rgb 데이터를 Hue, Saturation, Value, Lightness 값으로 변환한 것  |
| color[2]      | [Card::CardColor::Type](#Card_CardColor)  | 2 Byte   | -                | hsvl 값을 Classify에 설정된 기준에 따라 분류한 색                |
| card          | [Card::CardNameColor::Type](#Card_CardNameColor), [Card::CardNameFunction::Type](#Card_CardNameFunction)  | 1 Byte   | - | 앞 센서의 값을 상위 4비트, 뒤 센서의 값을 하위 4비트에 할당하여 만든 카드 값  |


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
| card[12]      | [Card::CardNameColor::Type](#Card_CardNameColor), [Card::CardNameFunction::Type](#Card_CardNameFunction)  | 12 Byte   | - | 앞 센서의 값을 상위 4비트, 뒤 센서의 값을 하위 4비트에 할당하여 만든 카드 값  |


<br>
<br>



---

<h3>E-DRIVE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. ***Structs - Card***

<br>

[Index](index.md)
