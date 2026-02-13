**[Coding Drone Plus](index.md)** / **Protocol** / **Structs** / **Display**

Modified : 2026.1.29

---

#### Introduce the display control definitions and structures

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

Pixel color

```cpp
namespace Display
{
    namespace Pixel
    {
        enum Type
        {
            Black,
            White,
            Inverse,
            Outline
        };
    }
}
```


<br>
<br>


<a name="Display_Font"></a>
## Display::Font::Type

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


<a name="Display_Align"></a>
## Display::Align::Type

String alignment

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


<a name="Protocol_Display_ClearAll"></a>
## Protocol::Display::ClearAll

Clear entire screen

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

| Name  | Type                                   | Size   | Range | Description |
|:-----------:|:---------------------------------------:|:--------:|:----:|:------------|
| pixel | [Display::Pixel::Type](#Display_Pixel) | 1 Byte | - | Fill color |


<br>
<br>


<a name="Protocol_Display_Clear"></a>
## Protocol::Display::Clear

Clear selected area

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

| Name   | Type                                    | Size   | Range         | Description        |
|:----------:|:----------------------------------------:|:--------:|:-------------:|:----------------|
| x      | int16_t                                 | 2 Byte | -2000 ~ 2000 | X start position   |
| y      | int16_t                                 | 2 Byte | -2000 ~ 2000 | Y start position   |
| width  | int16_t                                 | 2 Byte | -2000 ~ 2000 | Width              |
| height | int16_t                                 | 2 Byte | -2000 ~ 2000 | Height             |
| pixel  | [Display::Pixel::Type](#Display_Pixel)  | 1 Byte | -            | Fill color         |


<br>
<br>


<a name="Protocol_Display_Invert"></a>
## Protocol::Display::Invert

Invert selected area

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

| Name   | Type   | Size   | Range         | Description        |
|:-----------:|:-------:|:--------:|:-------------:|:---------------|
| x      | int16_t | 2 Byte | -2000 ~ 2000 | X start position   |
| y      | int16_t | 2 Byte | -2000 ~ 2000 | Y start position   |
| width  | int16_t | 2 Byte | -2000 ~ 2000 | Width              |
| height | int16_t | 2 Byte | -2000 ~ 2000 | Height             |


<br>
<br>


<a name="Protocol_Display_DrawPoint"></a>
## Protocol::Display::DrawPoint

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

| Name  | Type                                   | Size   | Range         | Description |
|:----------:|:---------------------------------------:|:--------:|:-------------:|:-----------|
| x     | int16_t                                | 2 Byte | -2000 ~ 2000 | X position |
| y     | int16_t                                | 2 Byte | -2000 ~ 2000 | Y position |
| pixel | [Display::Pixel::Type](#Display_Pixel) | 1 Byte | -            | Pixel color |


<br>
<br>


<a name="Protocol_Display_DrawLine"></a>
## Protocol::Display::DrawLine

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

| Name  | Type                                   | Size   | Range         | Description        |
|:----------:|:---------------------------------------:|:--------:|:-------------:|:---------------|
| x1    | int16_t                                | 2 Byte | -2000 ~ 2000 | X start position   |
| y1    | int16_t                                | 2 Byte | -2000 ~ 2000 | Y start position   |
| x2    | int16_t                                | 2 Byte | -2000 ~ 2000 | X end position     |
| y2    | int16_t                                | 2 Byte | -2000 ~ 2000 | Y end position     |
| pixel | [Display::Pixel::Type](#Display_Pixel) | 1 Byte | -            | Line color         |
| line  | [Display::Line::Type](#Display_Line)   | 1 Byte | -            | Line type          |


<br>
<br>


<a name="Protocol_Display_DrawRect"></a>
## Protocol::Display::DrawRect

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

| Name    | Type                                    | Size   | Range         | Description                |
|:----------:|:----------------------------------------:|:--------:|:-------------:|:-------------------------|
| x        | int16_t                                 | 2 Byte | -2000 ~ 2000 | X start position          |
| y        | int16_t                                 | 2 Byte | -2000 ~ 2000 | Y start position          |
| width    | int16_t                                 | 2 Byte | -2000 ~ 2000 | Width                     |
| height   | int16_t                                 | 2 Byte | -2000 ~ 2000 | Height                    |
| pixel    | [Display::Pixel::Type](#Display_Pixel)  | 1 Byte | -            | Pixel color               |
| flagFill | uint8_t                                 | 1 Byte | -            | 0 (no fill), 1 (fill)     |
| line     | [Display::Line::Type](#Display_Line)    | 1 Byte | -            | Line type                 |


<br>
<br>


<a name="Protocol_Display_DrawCircle"></a>
## Protocol::Display::DrawCircle

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

| Name    | Type                                    | Size   | Range         | Description                |
|:----------:|:----------------------------------------:|:--------:|:-------------:|:-------------------------|
| x        | int16_t                                 | 2 Byte | -2000 ~ 2000 | X center position         |
| y        | int16_t                                 | 2 Byte | -2000 ~ 2000 | Y center position         |
| radius   | int16_t                                 | 2 Byte | 1 ~ 2000     | Radius                    |
| pixel    | [Display::Pixel::Type](#Display_Pixel)  | 1 Byte | -            | Pixel color               |
| flagFill | uint8_t                                 | 1 Byte | -            | 0 (no fill), 1 (fill)     |


<br>
<br>


<a name="Protocol_Display_DrawString"></a>
## Protocol::Display::DrawString

Draw string

To display a string, append an ASCII string after the DrawString structure.

The header length must be (size of Protocol::Display::DrawString + length of the ASCII string).

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

| Name   | Type                                   | Size          | Range         | Description      |
|:----------:|:---------------------------------------:|:-------------:|:-------------:|:---------------|
| x       | int16_t                                | 2 Byte        | -2000 ~ 2000  | X position       |
| y       | int16_t                                | 2 Byte        | -2000 ~ 2000  | Y position       |
| font    | [Display::Font::Type](#Display_Font)   | 1 Byte        | -             | Font             |
| pixel   | [Display::Pixel::Type](#Display_Pixel) | 1 Byte        | -             | Pixel color      |
| message | ASCII String                           | Up to 30 Bytes| -             | String to display|


<br>
<br>


<a name="Protocol_Display_DrawStringAlign"></a>
## Protocol::Display::DrawStringAlign

Draw string with alignment

Write a string on the display. The string is placed between xStart and xEnd based on the `align` value.

To display a string, append an ASCII string after the DrawStringAlign structure.

The header length must be (size of Protocol::Display::DrawStringAlign + length of the ASCII string).

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

| Name   | Type                                    | Size          | Range         | Description      |
|:----------:|:----------------------------------------:|:-------------:|:-------------:|:---------------|
| xStart  | int16_t                                | 2 Byte        | -2000 ~ 2000  | X start position |
| xEnd    | int16_t                                | 2 Byte        | -2000 ~ 2000  | X end position   |
| y       | int16_t                                | 2 Byte        | -2000 ~ 2000  | Y position       |
| align   | [Display::Align::Type](#Display_Align) | 1 Byte        | -             | Align            |
| font    | [Display::Font::Type](#Display_Font)   | 1 Byte        | -             | Font             |
| pixel   | [Display::Pixel::Type](#Display_Pixel) | 1 Byte        | -             | Pixel color      |
| message | ASCII String                           | Up to 30 Bytes| -             | String to display|


<br>
<br>




---

<h3>Coding Drone Plus</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. ***Structs - Display***

<br>

[Index](index.md)
