***PETRONE / LINK / Protocol / DateType***<br>
Modified : 2017.10.18

---

#### Introduce data type.

---

<br>

## PETRONE LINK

PETRONE LINK extends and uses PETRONE's communication protocol.
<br>
LINK via the COMMAND that you use to control PETRONE. The commands for control LINK are not forwarded to PETRONE, Other data are broadcast both sides by LINK.
<br>

## <a name="DataType">Protocol::DataType::Type</a>
Extends data type for LINK and uses PETRONE's data type protocol.

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            // LINK Module
            LinkState = 0xE0,       // LINK module's state
            LinkEvent,              // LINK module's event
            LinkEventAddress,       // LINK module's event + Address
            LinkRssi,               // RSSI value on the device associated with the link.
            LinkDiscoveredDevice,   // Discovered Device
            LinkPasscode,           // Passcode for pairing
        };
    }
}
 
```

 - [Protocol::DataType::Type](../03_datatype.md#DataType)


<br>

---

### PETRONE

1. [Intro](../01_intro.md)
2. [Typedef](../02_typedef.md)
3. [DataType](../03_datatype.md)
4. [Definitions](../04_definitions.md)
5. [Base Structs](../05_base_structs.md)
6. [Structs](../06_structs.md)
7. [Structs - Light](../07_structs_light.md)
8. [Firmware Update](../08_firmware_update.md)


### PETRONE Link

1. [Intro](01_intro.md)
2. ***DataType***
3. [Definitions](03_definitions.md)
4. [Structs](04_structs.md)
5. [Examples](05_examples.md)

<br>

[Index](../index.md)

<br>

