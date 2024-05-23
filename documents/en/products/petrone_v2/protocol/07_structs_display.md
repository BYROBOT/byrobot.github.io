**[PETRONE_V2](index.md)** / **Protocol** / **Structs** / **Display**

Modified : 2018.02.14

---

#### Controller display to introduce control and the related definitions and structure.

---


<br>
<br>


# Definitions


<br>
<br>


## <a name="Display_Pixel">Display::Pixel::Type</a>

Pixel color

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


## <a name="Display_Font">Display::Font::Type</a>

Font

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


## <a name="Display_Align">Display::Align::Type</a>

String align

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


## <a name="Display_Line">Display::Line::Type</a>

Line

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


## <a name="Protocol_Display_ClearAll">Protocol::Display::ClearAll</a>

Clear screen

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

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:---------------------------------------:|:----:|:--------:|:------------|
| pixel       | [Display::Pixel::Type](#Display_Pixel)  | -    | 1 Byte   | Fill color   |


<br>
<br>


## <a name="Protocol_Display_Clear">Protocol::Display::Clear</a>

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

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:----------------------------------------:|:-------------:|:--------:|:----------------|
| x          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | X axis start position |
| y          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Y axis start position |
| width      | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Width          |
| height     | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Height         |
| pixel      | [Display::Pixel::Type](#Display_Pixel)   | -             | 1 Byte   | Pixel color |


<br>
<br>


## <a name="Protocol_Display_Invert">Protocol::Display::Invert</a>

Invert select area

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

| Variable Name | Type      | Range  | Size     | Description    |
|:-----------:|:-------:|:-------------:|:--------:|:---------------|
| x          | int16_t | -2000 ~ 2000  | 2 Byte   | X axis start position |
| y          | int16_t | -2000 ~ 2000  | 2 Byte   | Y axis start position |
| width      | int16_t | -2000 ~ 2000  | 2 Byte   | Width          |
| height     | int16_t | -2000 ~ 2000  | 2 Byte   | Height         |

<br>
<br>


## <a name="Protocol_Display_DrawPoint">Protocol::Display::DrawPoint</a>

Draw point

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

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:---------------------------------------:|:-------------:|:--------:|:-----------|
| x          | int16_t                                 | -2000 ~ 2000  | 2 Byte   | X axis position  |
| y          | int16_t                                 | -2000 ~ 2000  | 2 Byte   | Y axis position  |
| pixel      | [Display::Pixel::Type](#Display_Pixel)  | -             | 1 Byte   | Pixel color  |


<br>
<br>


## <a name="Protocol_Display_DrawLine">Protocol::Display::DrawLine</a>

Draw line

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

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:---------------------------------------:|:-------------:|:--------:|:---------------|
| x          | int16_t                                 | -2000 ~ 2000  | 2 Byte   | X axis start position  |
| y          | int16_t                                 | -2000 ~ 2000  | 2 Byte   | Y axis satrt position  |
| x2         | int16_t                                 | -2000 ~ 2000  | 2 Byte   | X axis end position    |
| y2         | int16_t                                 | -2000 ~ 2000  | 2 Byte   | Y axis end position    |
| pixel      | [Display::Pixel::Type](#Display_Pixel)  | -             | 1 Byte   | line color     |
| line       | [Display::Line::Type](#Display_Line)    | -             | 1 Byte   | line type      |


<br>
<br>


## <a name="Protocol_Display_DrawRect">Protocol::Display::DrawRect</a>

Draw rectangle

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

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:----------------------------------------:|:-------------:|:--------:|:-------------------------|
| x          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | X axis position  |
| y          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Y axis position  |
| width      | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Width                   |
| height     | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Height                  |
| pixel      | [Display::Pixel::Type](#Display_Pixel)   | -             | 1 Byte   | Pixel color            |
| flagFill   | uint8_t                                  | -             | 1 Byte   | 0(do not fill), 1(fill)  |
| line       | [Display::Line::Type](#Display_Line)     | -             | 1 Byte   | line type          |


<br>
<br>


## <a name="Protocol_Display_DrawCircle">Protocol::Display::DrawCircle</a>

Draw circle

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

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:----------------------------------------:|:-------------:|:--------:|:-------------------------|
| x          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | X axis center position  |
| y          | int16_t                                  | -2000 ~ 2000  | 2 Byte   | Y axis center position  |
| radius     | int16_t                                  | 1 ~ 2000      | 2 Byte   | Radius                   |
| pixel      | [Display::Pixel::Type](#Display_Pixel)   | -             | 1 Byte   | Pixel color            |
| flagFill   | uint8_t                                  | -             | 1 Byte   | 0(do not fill), 1(fill)  |


<br>
<br>


## <a name="Protocol_Display_DrawString">Protocol::Display::DrawString</a>

Draw string

Send strings to display on the screen with ASCII strings attached after drawString structures.
The length of the header must have a value (**Protocol::Display::DrawString** length + Display string length).

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

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:---------------------------------------:|:-------------:|:-------------:|:---------------|
| x          | int16_t                                 | -2000 ~ 2000  | 2 Byte        | X axis position |
| y          | int16_t                                 | -2000 ~ 2000  | 2 Byte        | Y axis position |
| font       | [Display::Font::Type](#Display_Font)    | -             | 1 Byte        | Font           |
| pixel      | [Display::Pixel::Type](#Display_Pixel)  | -             | 1 Byte        | Font color     |
| message    | ASCII String                            | -             | Less than 30 Byte  | String  |


<br>
<br>


## <a name="Protocol_Display_DrawStringAlign">Protocol::Display::DrawStringAlign</a>

Draw string with align

The string is placed in the align designated location between xStart and xEnd.
Send strings to display on the screen with ASCII strings attached after drawString structures.
The length of the header must have a value (**Protocol::Display::DrawStringAlign** length + Display string length).


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

| Variable Name | Type      | Range  | Size     | Description    |
|:----------:|:----------------------------------------:|:-------------:|:-------------:|:---------------|
| xStart     | int16_t                                 | -2000 ~ 2000  | 2 Byte        | X axis start position |
| xEnd       | int16_t                                 | -2000 ~ 2000  | 2 Byte        | X axis end position |
| y          | int16_t                                 | -2000 ~ 2000  | 2 Byte        | Y axis position |
| align      | [Display::Align::Type](#Display_Align)   | -             | 1 Byte        | Align           |
| font       | [Display::Font::Type](#Display_Font)    | -             | 1 Byte        | Font           |
| pixel      | [Display::Pixel::Type](#Display_Pixel)  | -             | 1 Byte        | Font color     |
| message    | ASCII String                            | -             | Less than 30 Byte  | String  |


<br>
<br>



---

<h3>PETRONE V2</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. ***Structs - Display***

<br>

[Index](index.md)
