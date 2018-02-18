***PETRONE / BLE / Protocol / Intro***<br>
Modified : 2018.2.13

---

<br>

# 1. Bluetooth Low Energy(Bluetooth SMART)

**PETRONE** uses Bluetooth Low Energy(BLE) for wireless connections.

<br>
The services and Characteristics used in PETRONE :

| Service       | Characteristic | UUID                                   | Direction of data              |
|:-------------:|:--------------:|:--------------------------------------:|:------------------------------:|
| DRONE_SERVICE |                | *C320DF00-7891-11E5-8BCF-FEFF819CDC9F* |                                |
| ├             | DRONE_DATA     | *C320DF01-7891-11E5-8BCF-FEFF819CDC9F* | Drone → Application (*Notify*) |
| └             | DRONE_CONF     | *C320DF02-7891-11E5-8BCF-FEFF819CDC9F* | Application → Drone (*Write*)  |

<br>
<br>

# 2. Data transfer structure.
<table>
    <tr>
        <td><div align="center">0</div></td>
        <td><div align="center">1</div></td>
        <td><div align="center">2</div></td>
        <td><div align="center">...</div></td>
        <td><div align="center">N-1</div></td>
        <td><div align="center">N</div></td>
    </tr>
    <tr>
        <td><div align="center">DataType</div></td>
        <td colspan="5"><div align="center">Data</div></td>
    </tr>
</table>

- Fist byte is datatype 
- Passing data defined in the first byte (datatype) from the second byte
- Maximum data length is 20byte.

<br>
<br>

# 3. Data transfer rules

- Data transfer cycles are recommended for **Android** *50ms* and **iOS** *100ms*
- If request to PETRONE, response that data. Ack response if not. Control commands do not send Ack and any responses.
- If app sends data to the drone, **Write** *DRONE_CONF*.
- If drone sends data to the app, **Notify** *DRONE_DATA*.


<br>

---

### PETRONE

1. ***Intro***
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. [Definitions](04_definitions.md)
5. [Base Structs](05_base_structs.md)
6. [Structs](06_structs.md)
7. [Structs - Light](07_structs_light.md)
8. [Firmware Update](08_firmware_update.md)


### PETRONE Link

1. [Intro](link/01_intro.md)
2. [DataType](link/02_datatype.md)
3. [Definitions](link/03_definitions.md)
4. [Structs](link/04_structs.md)
5. [Examples](link/05_examples.md)

<br>

[Index](index.md)

<br>

