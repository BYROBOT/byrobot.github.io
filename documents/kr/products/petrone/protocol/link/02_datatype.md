**[PETRONE](index.md)** / **LINK** / **Protocol** / **DateType**

Modified : 2018.3.6

---

#### 데이터 타입을 소개합니다.

---

<br>

## PETRONE LINK

PETRONE LINK는 PETRONE의 통신 프로토콜을 확장하여 사용하고 있습니다.
<br>
기본적으로 PETRONE을 제어하는 데 사용하는 COMMAND 명령을 통해 LINK를 제어합니다. LINK를 제어하는 명령들은 PETRONE에는 전달되지 않으며, 그 외의 데이터는 LINK가 양쪽의 통신을 중계합니다.
<br>

<a name="Protocol_DataType"></a>
## Protocol::DataType::Type
기존 PETRONE의 데이터 타입에 LINK용 데이터 타입을 추가하여 사용합니다.

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            // LINK 모듈
            LinkState = 0xE0,       // 링크 모듈의 상태
            LinkEvent,              // 링크 모듈의 이벤트
            LinkEventAddress,       // 링크 모듈의 이벤트 + 주소
            LinkRssi,               // 링크와 연결된 장치의 RSSI값
            LinkDiscoveredDevice,   // 검색된 장치
            LinkPasscode,           // 페어링 시 필요한 Passcode 설정
        };
    }
}
 
```

 - [Protocol::DataType::Type](../03_datatype.md#Protocol_DataType)


<br>

---

<h3> PETRONE</h3>

1. [Intro](../01_intro.md)
2. [Typedef](../02_typedef.md)
3. [DataType](../03_datatype.md)
4. [Definitions](../04_definitions.md)
5. [Base Structs](../05_base_structs.md)
6. [Structs](../06_structs.md)
7. [Structs - Light](../07_structs_light.md)
8. [Firmware Update](../08_firmware_update.md)


<h3> PETRONE Link</h3>

1. [Intro](01_intro.md)
2. ***DataType***
3. [Definitions](03_definitions.md)
4. [Structs](04_structs.md)
5. [Examples](05_examples.md)

<br>

[Index](../index.md)

<br>

