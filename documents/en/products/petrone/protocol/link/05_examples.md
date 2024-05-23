***PETRONE / LINK / Protocol / Structs***<br>
Modified : 2017.10.18

---

#### Data transfer Examples

---

<br>

## <a name="LinkModeBroadcast_Active">LinkModeBroadcast - Active</a>
This command is change the LINK to Active mode. When communicating with a module from your PC or the Arduino Board, the first thing you do is send the command to the PETRONE Connect mode without having to double-click a LINK module button. When updating the Aduino firmware in Active mode, it automatically switches to Mute Mode, so you only need to use this command to switch modes. 
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E0</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">83</div></td>
        <td><div align="center">33</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LinkSystemReset">LinkSystemReset</a>
LINK Soft Reset command. If a problem occurs during operation but serial communication is sent when possible, this command resets the module.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E1</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">F0</div></td>
        <td><div align="center">20</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LinkState">LinkState</a>
Request for LINK module state.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">E0</div></td>
        <td><div align="center">B6</div></td>
        <td><div align="center">E6</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LinkDiscoverStart">LinkDiscoverStart</a>
Discover BLE Device command.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E2</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">A3</div></td>
        <td><div align="center">75</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_0">Connect 0</a>
Used to connect to Unit 0 of devices discovered by Discover Start. The 6th byte is index of the device to which to connect.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E4</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">05</div></td>
        <td><div align="center">DF</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_1">Connect 1</a>
Used to connect device 1 of devices discovered with Discover Start.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E4</div></td>
        <td><div align="center">01</div></td>
        <td><div align="center">24</div></td>
        <td><div align="center">CF</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_2">Connect 2</a>
Used to connect device 2 of devices discovered with Discover Start.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E4</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">47</div></td>
        <td><div align="center">FF</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Connect_1">Disconnect</a>
Disconnect command
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E5</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">34</div></td>
        <td><div align="center">EC</div></td>
    </tr>
</table>

<br>
<br>

## <a name="RSSI_polling_start">RSSI polling start</a>
Command used to start polling RSSI values for the currently connected device. The value for the 6th byte is specified here as 02. In this case, the RSSI value is scanned with a 200ms interval multiplied by 100.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E6</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">25</div></td>
        <td><div align="center">99</div></td>
    </tr>
</table>

<br>
<br>

## <a name="RSSI_polling_stop">RSSI polling stop</a>
Command to stop polling RSSI values on the currently connected device.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">E7</div></td>
        <td><div align="center">00</div></td>
        <td><div align="center">56</div></td>
        <td><div align="center">8A</div></td>
    </tr>
</table>

<br>
<br>

## <a name="Address">Address</a>
Request LINK module connected PETRONE device address.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="2"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">11</div></td>
        <td><div align="center">02</div></td>
        <td><div align="center">90</div></td>
        <td><div align="center">30</div></td>
        <td><div align="center">CB</div></td>
        <td><div align="center">2D</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LED_Dimming_Yellow">LED Dimming - Yellow</a>
If connect with PETRONE, Send commands below will illuminate the propeller side LED brightly in yellow and then return the light to dark.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="3"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">20</div></td>
        <td><div align="center">03</div></td>
        <td><div align="center">45</div></td>
        <td><div align="center">8B</div></td>
        <td><div align="center">07</div></td>
        <td><div align="center">B0</div></td>
        <td><div align="center">D2</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LED_Dimming_Cyan">LED Dimming - Cyan</a>
If connect with PETRONE, Send commands below will illuminate the propeller side LED brightly in cyan and then return the light to dark.

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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="3"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">20</div></td>
        <td><div align="center">03</div></td>
        <td><div align="center">45</div></td>
        <td><div align="center">14</div></td>
        <td><div align="center">07</div></td>
        <td><div align="center">65</div></td>
        <td><div align="center">DA</div></td>
    </tr>
</table>

<br>
<br>

## <a name="LED_Dimming_Red">LED Dimming - Red</a>
If connect with PETRONE, Send commands below will illuminate the propeller side LED brightly in red and then return the light to dark.
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
    </tr>
    <tr>
        <td rowspan="2" colspan="2"><div align="center">Start code</div></td>
        <td colspan="2"><div align="center">Header</div></td>
        <td rowspan="2" colspan="3"><div align="center">Data</div></td>
        <td rowspan="2" colspan="2"><div align="center">CRC16</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td><div align="center">Length</div></td>
    </tr>
    <tr>
        <td><div align="center">0A</div></td>
        <td><div align="center">55</div></td>
        <td><div align="center">20</div></td>
        <td><div align="center">03</div></td>
        <td><div align="center">45</div></td>
        <td><div align="center">72</div></td>
        <td><div align="center">07</div></td>
        <td><div align="center">E9</div></td>
        <td><div align="center">7B</div></td>
    </tr>
</table>







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
2. [DataType](02_datatype.md)
3. [Definitions](03_definitions.md)
4. [Structs](04_structs.md)
5. ***Examples***

<br>

[Index](../index.md)

<br>

