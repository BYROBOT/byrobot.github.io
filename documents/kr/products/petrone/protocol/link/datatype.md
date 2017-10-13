***PETRONE / LINK / Protocol / DateType***<br>
Modified : 2017.07.11

---

#### 데이터 타입을 소개합니다.

---

<br>

## PETRONE LINK

PETRONE LINK는 PETRONE의 통신 프로토콜을 확장하여 사용하고 있습니다.
<br>
기본적으로 PETRONE을 제어하는 데 사용하는 COMMAND 명령을 통해 LINK를 제어합니다. LINK를 제어하는 명령들은 PETRONE에는 전달되지 않으며, 그 외의 데이터는 LINK가 양쪽의 통신을 중계합니다.
<br>

## <a name="DataType">Protocol::DataType::Type</a>
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

 - [Protocol::DataType::Type](../datatype.md#DataType)


<br>

---

### PETRONE

1. [Intro](../intro.md)
2. [Typedef](../typedef.md)
3. [DataType](../datatype.md)
4. [Definitions](../definitions.md)
5. [Base Structs](../base_structs.md)
6. [Structs](../structs.md)
7. [Structs - Light](../structs_light.md)
8. [Firmware Update](../firmware_update.md)


### PETRONE Link

1. [Intro](intro.md)
2. ***DataType***
3. [Definitions](definitions.md)
4. [Structs](structs.md)
5. [Examples](examples.md)

<br>

[Index](../index.md)

<br>

[Home](../../../../../README.md)

