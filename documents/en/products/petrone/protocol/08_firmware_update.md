***PETRONE / BLE / Protocol / FirmwareUpdate***<br>
Modified : 2017.10.18

---

#### How to update PETRONE firmware

---

<br>

## PETRONE Firmware

PETRONE is configured with **Controll Firmware(Main)** and **Communication Firmware(Sub)**.
Each firmware divides the internal flash space into two areas ( **ImageA**, **ImageB**).
When updating firmware, proceed from **ImageA** to **ImageB**, **ImageB** to **ImageA**. So current running firmware is **ImageA** than send **ImageB**.
<br>
<br>

## Firmware header structure
The first 16 bytes of the firmware file are configured as below. You can read this section for information about the firmware file.
<br>
### <a name="UpdaterHeader">Updater::Header</a>
```cpp
namespace Updater
{
    struct Header
    {
        u16     reserve;        // reserve [2byte]

        u32     length;         // firmware length( Length of actual firmware except header 16 bytes)[4byte]

        u8      year;           // firmware build year[2byte]
        u8      month;          // firmware build month[1byte]
        u8      day;            // firmware build day[1byte

        u16     version;        // firmware version[2byte]
        u8      imageType;      // firmware image type[1byte]
        u32     deviceType;     // target device type[4byte]
    };
}
```
- imageType : [System::ImageType::Type](04_definitions.md#ImageType)
- deviceType : [System::DeviceType::Type](04_definitions.md#DeviceType)

<br>
<br>

## Firmware update process

1. Download the 4 firmware file from the server before starting the firmware update.(Main A/B and Sub A/B)를 받습니다.

2. Read the first 16 bytes of the firmware file to determine information about each file. ([Updater::Header](#UpdaterHeader))

3. Request current running firmware information. ([Protocol::UpdateLookupTarget](06_structs.md#UpdateLookupTarget))

4. Response [Protocol::UpdateInformation](06_structs.md#UpdateInformation) structure from drone.

5. Compare the firmware on the drone with the information on the firmware received from the server to send the appropriate firmware. ([Protocol::Update](06_structs.md#Update))
    - When updating the firmware, the file transfers data that is truncated to 16 bytes. 1 block size is 16byte.
    - Current running firmware type is **ImageA** send **RawImageB** or **EncryptedImageB**. On the contrary **ImageB**, send **RawImageA** or **EncryptedImageA**인.
    - If there is no problem transferring firmware data via BLE, drone does not respond. If you lose or encounter problems with the data being transmitted, send a firmware update location correction([Protocol::UpdateLocationCorrect](06_structs.md#UpdateLocationCorrect)). If you receive this structure, you must start sending again from that location.
    - When firmware data is transmitted via serial communication, the firmware update location correction is response every block([Protocol::UpdateLocationCorrect](06_structs.md#UpdateLocationCorrect)).

6. Processing Petron Firmware Update
    - Boots to the new image only when the firmware update has completed successfully. In most cases, failure to update the firmware is not a major problem, because the older firmware is preserved even if it fails in the middle.
    - If you have updated the control firmware, restart the control program immediately after the firmware update is complete. If the communication firmware has been updated, disconnect BLE and restart the communication program.
<br>
<br>

## Precautions for Firmware update

- It is not recommended to return to the old firmware when updating the firmware. Most updates are provided to troubleshoot problems with older firmware, so changing to an older firmware might cause unexpected problems. In addition, some updates might add new hardware support. In such cases, if you change to an older firmware, the hardware might not work.

- If the protocol changes with the firmware update, the changes are reflects in the current document. If you change to existing firmware, you may experience problems with the protocol not matching the document, resulting in failure to perform the desired action, or dangerous malfunction.

- Firmware updates are recommended through an app provided by the robot or via a PC program.


<br>
<br>

## Request data example

- Request control firmware(serial communication)

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">4</div></td>
        <td><div align="center">5</div></td>
        <td><div align="center">6</div></td>
        <td><div align="center">7</div></td>
        <td><div align="center">8</div></td>
        <td><div align="center">9</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="4"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">04</div></td>
        <td><div align="center">01</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">16</div></td>
        <td><div align="center">31</div></td>
    </tr>
</table>

- Request communication Firmware(serial communication)

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">4</div></td>
        <td><div align="center">5</div></td>
        <td><div align="center">6</div></td>
        <td><div align="center">7</div></td>
        <td><div align="center">8</div></td>
        <td><div align="center">9</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="4"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">04</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">CA</div></td>
        <td><div align="center">AA</div></td>
    </tr>
</table>

<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
7. [Structs - Light](07_structs_light.md)
8. **Firmware Update**


### PETRONE Link

1. [Intro](link/01_intro.md)
2. [DataType](link/02_datatype.md)
3. [Definitions](link/03_definitions.md)
4. [Structs](link/04_structs.md)
5. [Examples](link/05_examples.md)

<br>

[Index](index.md)

<br>

