**[Coding Drone Plus](index.md)** / **Protocol** / **Intro**

Modified : 2026.1.29

---

* Kramdown table of contents
{:toc .toc}


<br>

# 1. Introduce Coding Drone Plus

Coding Drone Plus is changed communication module from Coding Drone and include controller.


<br>
<br>


# 2. Data transfer structure

Coding Drone Plus uses serial communication with external devices. In most cases, the controller and the PC are connected while communicating. The sending and receiving data are structured as follows:

<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">3</div></td>
        <td><div align="center">4</div></td>
        <td><div align="center">5</div></td>
        <td><div align="center">...</div></td>
        <td><div align="center">N-1</div></td>
        <td><div align="center">N</div></td>
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="4"><div align="center">Header</div></td>
        <td rowspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
        <td><div align="center">From</div></td>
        <td><div align="center">To</div></td>
    </tr>
    <tr>
        <td><div align="center">0x0A</div></td>
        <td><div align="center">0x55</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
        <td><div align="center">-</div></td>
    </tr>
</table>

<br>

Each item is explained as follows.

<br>

<table>
    <tr>
        <td colspan="2"><div align="center">Area</div></td>
        <td><div align="center">Description</div></td>
    </tr>
    <tr>
        <td colspan="2"><div align="center">Start code</div></td>
        <td><div align="left">Start data transmission</div></td>
    </tr>
    <tr>
        <td rowspan="4"><div align="center">Header</div></td>
        <td><div align="center">DataType</div></td>
        <td><div align="left">Data type</div></td>
    </tr>
    <tr>
        <td><div align="center">Length</div></td>
        <td><div align="left">Data length</div></td>
    </tr>
    <tr>
        <td><div align="center">From</div></td>
        <td><div align="left">Data transfer device's DeviceType</div></td>
    </tr>
    <tr>
        <td><div align="center">To</div></td>
        <td><div align="left">Data receive device's DeviceType</div></td>
    </tr>
    <tr>
        <td colspan="2"><div align="center">Data</div></td>
        <td><div align="left">Send data</div></td>
    </tr>
    <tr>
        <td colspan="2"><div align="center">CRC16</div></td>
        <td><div align="left">Check whether the header and the data were delivered correctly<br><a href="http://www.menie.org/georges/embedded/crc16.html">http://www.menie.org/georges/embedded/crc16.html</a></div></td>
    </tr>
</table>


<br>

Data and the CRC16 zone use Little Endian. When Little Endian is present, if more than two bytes, the low byte is front of the array. You can change it conveniently using BitConverter in C#.

<table>
    <tr>
        <td><div align="center">HEX value</div></td>
        <td colspan="2"><div align="center">0x1234</div></td>
    </tr>
    <tr>
        <td><div align="center">Array index</div></td>
        <td><div align="center"><b>0</b></div></td>
        <td><div align="center"><b>1</b></div></td>
    </tr>
    <tr>
        <td><div align="center">Big Endian</div></td>
        <td><div align="center">12</div></td>
        <td><div align="center">34</div></td>
    </tr>
    <tr>
        <td><div align="center">Little Endian</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">12</div></td>
    </tr>
</table>

<br>

<table>
    <tr>
        <td><div align="center">HEX value</div></td>
        <td colspan="4"><div align="center">0x12345678</div></td>
    </tr>
    <tr>
        <td><div align="center">Array index</div></td>
        <td><div align="center"><b>0</b></div></td>
        <td><div align="center"><b>1</b></div></td>
        <td><div align="center"><b>2</b></div></td>
        <td><div align="center"><b>3</b></div></td>
    </tr>
    <tr>
        <td><div align="center">Big Endian</div></td>
        <td><div align="center">12</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">56</div></td>
        <td><div align="center">78</div></td>
    </tr>
    <tr>
        <td><div align="center">Little Endian</div></td>
        <td><div align="center">78</div></td>
        <td><div align="center">56</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">12</div></td>
    </tr>
</table>


<br>
<br>


# 3. Precautions in use

- All devices only send data in response when requested.
- If a device is specified to receive data, the device will send Ack when it is not requested.
- If the data is transmitted via broadcast, if a command is not a data request but a typical one, the device that can process it runs the received command.
- If the data is transmitted via broadcast a data requests, the device can be respond data. If more than one device responds to the same data, this can cause conflicts between sending and receiving data. Be careful when you use it.
- Ack is not answered for the broadcast.


<br>
<br>


# 4. Serial communication settings


|Area       | Setting value |
|:---------:|:------:|
| Baud Rate | 115200 |
| Parity    | None   |
| Data Bits | 8      |
| Stop Bits | 1      |


<br>
<br>


# 5. Driver install

Coding Drone Plus controller is automatically recognized in Windows 10. Do not need additional driver.
If the device is not recognized, you need to install device driver.

<br>

---

<h3>Coding Drone Plus</H3>

1. **Intro**
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
<!-- 7. [Structs - Display](07_structs_display.md) -->

<br>

[Index](index.md)
