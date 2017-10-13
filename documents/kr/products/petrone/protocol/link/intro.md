***PETRONE / LINK / Protocol / Intro***<br>
Modified : 2017.09.11

---

<br>

# 1. PETRONE LINK 소개

**PETRONE LINK**(이하 LINK)는 PETRONE과의 연결 및 제어를 도와주는 통신 모듈입니다. PETRONE과 LINK 사이에는 **Bluetooth Low Energy**(이하 BLE)를 사용하여 통신하지만, LINK 사용자는 시리얼 통신만으로 PETRONE과 연결할 수 있습니다.


<br>
<br>


# 2. 전송 데이터 구조

**LINK** 장치와 통신을 할 때의 데이터 블럭 구성은 다음과 같습니다.

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">...</div></td>
        <td><div align="center">N-1</div></td>
        <td><div align="center">N</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0x0A</div></td>
        <td><div align="center">0x55</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
    </tr>
</table>
각 항목에 대한 설명은 다음과 같습니다.


|영역 | 설명 |
|:---|:---|
| Start code | 데이터 전송 시작을 알림 |
| Header | 헤더 뒤에 이어지는 데이터의 형식과 길이 |
| Data | 전송할 데이터 |
| CRC16 | Header와 Data가 정상적으로 전달되었는지 판별<br><a href="http://www.menie.org/georges/embedded/crc16.html">http://www.menie.org/georges/embedded/crc16.html</a>    |


Data 영역과 CRC16 영역 모두 Little Endian을 사용하고 있습니다. Little Endian일 때 2바이트 이상의 변수는 하위 바이트가 배열의 앞 부분에 위치합니다. C#에서는 Bitconverter를 사용하시면 편리하게 변경할 수 있습니다.


| | 0x1234 | 0x12345678 |
|:---:|:---:|:---:|
| Big Endian | [ 12 34 ] | [ 12 34 56 78 ] |
| Little Endian | [ 34 12 ] | [ 78 56 34 12 ] |


<br>
<br>


# 3. 사용 시 주의사항

- LINK 모듈을 제어할 때에는 [Command](../structs.md#Command)를 주로 사용합니다.

- LINK 모듈에 데이터를 전송하는 경우 몇 가지 명령을 제외하고 대부분 Ack 데이터가 반송됩니다.

- LINK 모듈은 Active 모드일 때 LINK의 동작 모드 변경을 통신으로 알려줍니다.

- 장치 스캔은 1.6초 동안 동작하며 스캔이 끝날 때 까지는 시리얼 통신을 처리하지 못합니다.


<br>
<br>


# 4. 시리얼 통신 설정


|영역 | 설정값 |
|:---:|:---:|
| Baud Rate | 115200 |
| Parity | None      |
| Data Bits | 8 |
| Stop Bits | 1 |


<br>
<br>


# 5. 드라이버 설치

LINK 모듈은 시리얼 통신용으로 Silicon Labs사의 CP2104를 사용하고 있습니다. 윈도우에서 자동으로 USB 드라이버를 설치하지 못할 경우, 아래의 사이트를 방문하여 OS에 맞는 드라이버를 받아서 설치하시기 바랍니다.

[CP210x USB to UART Bridge VCP Drivers](https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)

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

1. ***Intro***
2. [DataType](datatype.md)
3. [Definitions](definitions.md)
4. [Structs](structs.md)
5. [Examples](examples.md)

<br>

[Index](../index.md)