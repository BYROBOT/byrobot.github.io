***PETRONE / LINK / Protocol / Intro***<br>
Modified : 2017.10.18

---

<br>

# 1. Introduce PETRONE LINK 

**PETRONE LINK**(LINK) is communication module for connect and control PETRONE.
  PETRONE and LINK communicat using **Bluetooth Low Energy**(BLE). But, LINK user can connect to PETRONE use only serial communication.


<br>
<br>


# 2. Data transmission structure

Communicating with **LINK** device, the data block configuration is as follows:

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

Each item is explained as follows.

| Area       | Description                                             |
|:-----------|:--------------------------------------------------------|
| Start code | Data transmission notice                                |
| Header     | Length of data that follows header                      |
| Data       | Data                                                    |
| CRC16      | Check the header and the data were delivered correctly. |

<br>
<a href="http://www.menie.org/georges/embedded/crc16.html">http://www.menie.org/georges/embedded/crc16.html</a>    |


 Data and the CRA16 zone use Little Endian. When Little Endian is present, If more than two bytes, low byte is front of the array. You can change it conveniently using Bitconverter in C#.


|               | 0x1234    | 0x12345678      |
|:-------------:|:---------:|:---------------:|
| Big Endian    | [ 12 34 ] | [ 12 34 56 78 ] |
| Little Endian | [ 34 12 ] | [ 78 56 34 12 ] |


<br>
<br>


# 3. Precautions in use

- To control the LINK module, typically use [Command](../06_structs.md#Command).

- When sending data to LINK module, the device will send Ack with the exception of a few commands.

- LINK module communicates changing the behavior mode of LINK when it is in Active mode.

- The device scan is operate for 1.6 seconds and will not use serial communication until the scan is complete. 


<br>
<br>


# 4. Configure parameters for serial port


| Area      | Setting value |
|:---------:|:-------------:|
| Baud Rate | 115200        |
| Parity    | None          |
| Data Bits | 8             |
| Stop Bits | 1             |


<br>
<br>


# 5. Driver install

- LINK module is using Silicon Labs CP2104 for serial communication. If Windows™ can not install the USB driver automatically, please visit the site below to obtain and install the drivers for your OS.

[CP210x USB to UART Bridge VCP Drivers](https://www.silabs.com/products/mcu/Pages/USBtoUARTBridgeVCPDrivers.aspx)

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

1. ***Intro***
2. [DataType](02_datatype.md)
3. [Definitions](03_definitions.md)
4. [Structs](04_structs.md)
5. [Examples](05_examples.md)

<br>

[Index](../index.md)