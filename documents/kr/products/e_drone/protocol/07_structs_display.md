**[E-DRONE](index.md)** / **Protocol** / **Structs** / **Display**

Modified : 2018.3.6

---

#### Display 제어와 관련된 정의 및 구조체들을 소개합니다.

---

* Kramdown table of contents
{:toc .toc}


<br>
<br>


# Definitions


<br>
<br>


<a name="Display_Pixel"></a>
## Display::Pixel::Type

픽셀 색상

```cpp
namespace Display
{
    namespace Pixel
    {
        enum Type
        {
            Black,
            White
        };
    }
}
```


<br>
<br>


<a name="Display_Font"></a>
## Display::Font::Type

폰트

```cpp
namespace Display
{
    namespace Font
    {
        enum Type
        {
            LiberationMono5x8,
            LiberationMono10x16,
        };
    }
}
```


<br>
<br>


<a name="Display_Align"></a>
## Display::Align::Type

문자열 정렬

```cpp
namespace Display
{
    namespace Align
    {
        enum Type
        {
            Left,
            Center,
            Right
        };
    }
}
```

<br>
<br>


<a name="Display_Line"></a>
## Display::Line::Type

선

```cpp
namespace Display
{
    namespace Line
    {
        enum Type
        {
            Solid,
            Dotted,
            Dashed,
        };
    }
}
```


<br>
<br>


# Structs


<br>
<br>


<a name="Protocol_Display_ClearAll"></a>
## Protocol::Display::ClearAll

화면 전체 지우기

```cpp
namespace Protocol
{
    namespace Display
    {
        struct ClearAll
        {
            u8      pixel;    
        };
    }
}
```

| 변수 이름   | 형식                                    | 범위 | 크기     | 설명        |
|:-----------:|:---------------------------------------:|:----:|:--------:|:------------|
| pixel       | [Display::Pixel::Type](#Display_Pixel)  | -    | 1 Byte   | 채울 색상   |


<br>
<br>


<a name="Protocol_Display_Clear"></a>
## Protocol::Display::Clear

선택 영역 지우기

```cpp
namespace Protocol
{
    namespace Display
    {
        struct Clear
        {
            s16     x;
            s16     y;
            s16     width;
            s16     height;
            u8      pixel;
        };
    }
}
```

| 변수 이름  | 형식                                     | 범위          | 크기     | 설명            |
|:----------:|:----------------------------------------:|:-------------:|:--------:|:----------------|
| x          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | X축 시작 위치   |
| y          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치   |
| width      | int16_t                                  | -2000 ~ 2000  | 2 Byte   | 너비            |
| height     | int16_t                                  | -2000 ~ 2000  | 2 Byte   | 높이            |
| pixel      | [Display::Pixel::Type](#Display_Pixel)   | -             | 1 Byte   | 채울 색상       |


<br>
<br>


<a name="Protocol_Display_Invert"></a>
## Protocol::Display::Invert

선택 영역 반전

```cpp
namespace Protocol
{
    namespace Display
    {
        struct Invert
        {
            s16     x;
            s16     y;
            s16     width;
            s16     height;
        };
    }
}
```

| 변수 이름   | 형식    | 범위          | 크기     | 설명           |
|:-----------:|:-------:|:-------------:|:--------:|:---------------|
| x           | int16_t | -2000 ~ 2000  | 2 Byte   | X축 시작 위치  |
| y           | int16_t | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치  |
| width       | int16_t | -2000 ~ 2000  | 2 Byte   | 너비           |
| height      | int16_t | -2000 ~ 2000  | 2 Byte   | 높이           |


<br>
<br>


<a name="Protocol_Display_DrawPoint"></a>
## Protocol::Display::DrawPoint

점 찍기

```cpp
namespace Protocol
{
    namespace Display
    {
        struct DrawPoint
        {
            s16     x;
            s16     y;
            u8      pixel;
        };
    }
}
```

| 변수 이름  | 형식                                    | 범위          | 크기     | 설명       |
|:----------:|:---------------------------------------:|:-------------:|:--------:|:-----------|
| x          | int16_t                                 | -2000 ~ 2000  | 2 Byte   | X축 위치   |
| y          | int16_t                                 | -2000 ~ 2000  | 2 Byte   | Y축 위치   |
| pixel      | [Display::Pixel::Type](#Display_Pixel)  | -             | 1 Byte   | 점 색상    |


<br>
<br>


<a name="Protocol_Display_DrawLine"></a>
## Protocol::Display::DrawLine

선 그리기

```cpp
namespace Protocol
{
    namespace Display
    {
        struct DrawLine
        {
            s16     x1;
            s16     y1;
            s16     x2;
            s16     y2;
            u8      pixel;
            u8      line;
        };
    }
}
```

| 변수 이름  | 형식                                    | 범위          | 크기     | 설명           |
|:----------:|:---------------------------------------:|:-------------:|:--------:|:---------------|
| x1         | int16_t                                 | -2000 ~ 2000  | 2 Byte   | X축 시작 위치  |
| y1         | int16_t                                 | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치  |
| x2         | int16_t                                 | -2000 ~ 2000  | 2 Byte   | X축 끝 위치    |
| y2         | int16_t                                 | -2000 ~ 2000  | 2 Byte   | Y축 끝 위치    |
| pixel      | [Display::Pixel::Type](#Display_Pixel)  | -             | 1 Byte   | 선 색상        |
| line       | [Display::Line::Type](#Display_Line)    | -             | 1 Byte   | 선 형태        |


<br>
<br>


<a name="Protocol_Display_DrawRect"></a>
## Protocol::Display::DrawRect

네모 상자 그리기

```cpp
namespace Protocol
{
    namespace Display
    {
        struct DrawRect
        {
            s16     x;
            s16     y;
            s16     width;
            s16     height;
            u8      pixel;
            u8      flagFill;
            u8      line;
        };
    }
}
```

| 변수 이름  | 형식                                     | 범위          | 크기     | 설명                     |
|:----------:|:----------------------------------------:|:-------------:|:--------:|:-------------------------|
| x          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | X축 시작 위치            |
| y          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Y축 시작 위치            |
| width      | int16_t                                  | -2000 ~ 2000  | 2 Byte   | 너비                     |
| height     | int16_t                                  | -2000 ~ 2000  | 2 Byte   | 높이                     |
| pixel      | [Display::Pixel::Type](#Display_Pixel)   | -             | 1 Byte   | 색상                     |
| flagFill   | uint8_t                                  | -             | 1 Byte   | 0(채우지 않음), 1(채움)  |
| line       | [Display::Line::Type](#Display_Line)     | -             | 1 Byte   | 선 형태                  |


<br>
<br>


<a name="Protocol_Display_DrawCircle"></a>
## Protocol::Display::DrawCircle

원 그리기

```cpp
namespace Protocol
{
    namespace Display
    {
        struct DrawCircle
        {
            s16     x;
            s16     y;
            s16     radius;
            u8      pixel;
            u8      flagFill;
        };
    }
}
```

| 변수 이름  | 형식                                     | 범위          | 크기     | 설명                     |
|:----------:|:----------------------------------------:|:-------------:|:--------:|:-------------------------|
| x          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | X축 중심점 위치          |
| y          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Y축 중심점 위치          |
| radius     | int16_t                                  | 1 ~ 2000      | 2 Byte   | 반지름                   |
| pixel      | [Display::Pixel::Type](#Display_Pixel)   | -             | 1 Byte   | 색상                     |
| flagFill   | uint8_t                                  | -             | 1 Byte   | 0(채우지 않음), 1(채움)  |


<br>
<br>


<a name="Protocol_Display_DrawString"></a>
## Protocol::Display::DrawString

문자열 그리기

화면에 표시할 문자열은 DrawString 구조체 뒤에 이어서 ASCII 문자열을 붙여서 전송.

헤더의 length는 (Protocol::Display::DrawString의 길이 + 화면에 표시할 문자열의 길이) 값을 넣어야 합니다.

```cpp
namespace Protocol
{
    namespace Display
    {
        struct DrawString
        {
            s16     x;
            s16     y;
            u8      font;
            u8      pixel;
        };
    }
}
```

| 변수 이름  | 형식                                    | 범위          | 크기          | 설명           |
|:----------:|:---------------------------------------:|:-------------:|:-------------:|:---------------|
| x          | int16_t                                 | -2000 ~ 2000  | 2 Byte        | X축 위치       |
| y          | int16_t                                 | -2000 ~ 2000  | 2 Byte        | Y축 위치       |
| font       | [Display::Font::Type](#Display_Font)    | -             | 1 Byte        | 폰트           |
| pixel      | [Display::Pixel::Type](#Display_Pixel)  | -             | 1 Byte        | 색상           |
| message    | ASCII String                            | -             | 30 Byte 이하  | 표시할 문자열  |


<br>
<br>


<a name="Protocol_Display_DrawStringAlign"></a>
## Protocol::Display::DrawStringAlign

문자열 정렬하여 그리기

화면에 문자열 쓰기. 문자열은 xStart와 xEnd 사이에서 align으로 지정한 위치에 놓인다.

화면에 표시할 문자열은 DrawStringAlign 구조체 뒤에 이어서 ASCII 문자열을 붙여서 전송.

헤더의 length는 (Protocol::Display::DrawStringAlign 길이 + 화면에 표시할 문자열의 길이) 값을 넣어야 합니다.

```cpp
namespace Protocol
{
    namespace Display
    {
        struct DrawStringAlign
        {
            s16     xStart;
            s16     xEnd;
            s16     y;
            u8      align;
            u8      font;
            u8      pixel;
        };
    }
}
```

| 변수 이름  | 형식                                     | 범위          | 크기          | 설명           |
|:----------:|:----------------------------------------:|:-------------:|:-------------:|:---------------|
| xStart     | int16_t                                  | -2000 ~ 2000  | 2 Byte        | X축 시작 위치  |
| xEnd       | int16_t                                  | -2000 ~ 2000  | 2 Byte        | X축 끝 위치    |
| y          | int16_t                                  | -2000 ~ 2000  | 2 Byte        | Y축 위치       |
| align      | [Display::Align::Type](#Display_Align)   | -             | 1 Byte        | 정렬           |
| font       | [Display::Font::Type](#Display_Font)     | -             | 1 Byte        | 폰트           |
| pixel      | [Display::Pixel::Type](#Display_Pixel)   | -             | 1 Byte        | 색상           |
| message    | ASCII String                             | -             | 30 Byte 이하  | 표시할 문자열  |


<br>
<br>



---

<h3>E-DRONE</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. ***Structs - Display***

<br>

[Index](index.md)
