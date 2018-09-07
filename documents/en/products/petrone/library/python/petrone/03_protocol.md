**[*petrone* for python](index.md)** / **Protocol**

Modified : 2018.2.12

---

<h3>Introduce data transmission protocol define.</h3>

---


<br>

## <a name="DataType">DataType</a>

Data Type

Introduce data transmission data type.

```py
class DataType(Enum):
    
    None_                       = 0x00      # None
    
    ##### BLE + Serial #####
    Ping                        = 0x01      # Device communication ping
    Ack                         = 0x02      # Data receive ack
    Error                       = 0x03      # Error(reserve bit flag define later.)
    Request                     = 0x04      # Request data of the specified
    Passcode                    = 0x05      # New pairing passcode.

    Control                     = 0x10      # Control command
    Command                     = 0x11      # Command
    Command2                    = 0x12      # Multibple command(Double command)
    Command3                    = 0x13      # Multibple command(Triple command)

    # Light
    LightMode                   = 0x20      # LED mode
    LightMode2                  = 0x21      # LED mode x2
    LightModeCommand            = 0x22      # LED mode, Command
    LightModeCommandIr          = 0x23      # LED mode, Command, IR
    LightModeColor              = 0x24      # LED mode 3 colors
    LightModeColor2             = 0x25      # LED mode 3 colors x2

    LightEvent                  = 0x26      # LED event
    LightEvent2                 = 0x27      # LED event x2
    LightEventCommand           = 0x28      # LED event, Command
    LightEventCommandIr         = 0x29      # LED event, Command, IR
    LightEventColor             = 0x2A      # LED event 3 colors
    LightEventColor2            = 0x2B      # LED event 3 colors x2

    LightModeDefaultColor       = 0x2C      # LED mode default 3 color
    LightModeDefaultColor2      = 0x2D      # LED mode default 3 color x2

    # State settings
    Address                     = 0x30      # IEEE Address
    State                       = 0x31      # Drone state ( Mode, Coordinate, Battery )
    Attitude                    = 0x32      # Drone attitude( Angle )
    GyroBias                    = 0x33      # Gyro bias value
    TrimAll                     = 0x34      # All Trim value
    TrimFlight                  = 0x35      # Flight Trim value
    TrimDrive                   = 0x36      # Drive Trim value

    CountFlight                 = 0x37      # Count of Flight log
    CountDrive                  = 0x38      # Count of Drive log

    # IR
    IrMessage                   = 0x40      # IR Message Send/Recv

    # Sensor and control
    Imu                         = 0x50      # IMU Raw
    Pressure                    = 0x51      # Pressure sensor data
    ImageFlow                   = 0x52      # ImageFlow
    Button                      = 0x53      # Button
    Battery                     = 0x54      # Battery
    Motor                       = 0x55      # Motor control and check current value 
    Temperature                 = 0x56      # Temperature data
    Range                       = 0x57      # Range sensor data

    # Firmware update
    UpdateLookupTarget          = 0x90      # Update target device lookup
    UpdateInformation           = 0x91      # Update information. ( Main or sub )
    Update                      = 0x92      # Update firmware
    UpdateLocationCorrect       = 0x93      # Update firmware correct location ( from PETRONE )

    # LINK Module
    LinkState                   = 0xE0      # link module state
    LinkEvent                   = 0xE1      # link module event
    LinkEventAddress            = 0xE2      # link module event + address
    LinkRssi                    = 0xE3      # link module device RSSI value
    LinkDiscoveredDevice        = 0xE4      # Discovered device from link module
    LinkPasscode                = 0xE5      # Connect passcode for link module

    Message                     = 0xF0      # String message

    EndOfType                   = 0xFF
```


<br>
<br>


## <a name="CommandType">CommandType</a>

Command type

Contains the features that you can execute by sending a single command or additional options.

```py
class CommandType(Enum):
    
    None_                       = 0x00      # None

    # Mode
    ModeVehicle                 = 0x10      # Vehicle mode

    # Control
    Headless                    = 0x20      # Headless mode
    Trim                        = 0x21      # Trim change
    FlightEvent                 = 0x22      # Flight event
    DriveEvent                  = 0x23      # Drive event
    Stop                        = 0x24      # Stop

    ResetHeading                = 0x50      # Reset heading
    ClearGyroBias               = 0x51      # Clear gyro bias (Trim clear at the same time.)
    ClearTrim                   = 0x52      # Clear trim

    # Communicate[Wireless Lan]
    ResetWirelessLan            = 0x70		# Wireless lan reset
    WirelessLanConnected        = 0x70      # Connect Wireless lan 
    WirelessLanDisconnected     = 0x70      # Disconnect Wireless lan

    # Communicate[Bluetooth]
    PairingActivate             = 0x80      # Pairing Activate
    PairingDeactivate           = 0x81      # Pairing Inactivate
    AdvertisingStart            = 0x82      # Change the device to advertisements
    AdvertisingStop             = 0x83      # Change the device to disable advertisements
    TerminateConnection         = 0x84      # Disconnect a BLE peripheral
    ClearBondList               = 0x85      # Clear bonding device list

    # Request
    Request                     = 0x90      # Request data of the specified type
    UpdateCompleteSub           = 0x90      # Update complete (Sub)
    ClearUpdateAreaMain         = 0x90      # Clear update area (Main)


    # LINK Module
    LinkModeBroadcast           = 0xE0      # LINK broadcast mode change
    LinkSystemReset             = 0xE1      # LINK System reset
    LinkDiscoverStart           = 0xE2      # LINK discover start
    LinkDiscoverStop            = 0xE3      # LINK discover stop
    LinkConnect                 = 0xE4      # LINK connect specified device
    LinkDisconnect              = 0xE5      # LINK disconnect from device
    LinkRssiPollingStart        = 0xE6      # LINK RSSI polling start
    LinkRssiPollingStop         = 0xE7      # LINK RSSI polling stop

    EndOfType                   = 0xFF
```


<br>
<br>


## <a name="Header">Header</a>

Header

It contains the type and length of data that follows the header.

```py
class Header(ISerializable):

    def __init__(self):
        self.dataType    = DataType.None_
        self.length      = 0
```

| Variable Name | Type                                    | Range   | Size     | Description            |
|:-------------:|:---------------------------------------:|:-------:|:--------:|:-----------------------|
| dataType      | [DataType](#DataType)                   | -       | 1 Byte   | Data type              |
| length        | UInt8                                   | 0 ~ 255 | 1 Byte   | Data length            |


<br>
<br>


## <a name="Ping">Ping</a>

Ping

Used to check the status of the connection with other devices. The relative device sends an Ack response to the ping.
When a ping is transmitted from a drone, the systemTime contains the system time value of the ping sending device.

```py
class Ping(ISerializable):

    def __init__(self):
        self.systemTime     = 0
```

| Variable Name | Type      | Range  | Size     | Description    |
|:-------------:|:---------:|:------:|:--------:|:---------------|
| systemTime    | UInt32    | -      | 4 Byte   | System time    |


<br>
<br>


## <a name="Ack">Ack</a>

Ack

If a data request is sent to drone, the corresponding data is responded. If the data is not ready, Ack is in response.
The device that sent the data can check the Ack for normal transfer.

```py
class Ack(ISerializable):

    def __init__(self):
        self.systemTime     = 0
        self.dataType       = DataType.None_
```

| Variable Name  | Type                    | Range | Size     | Description            |
|:--------------:|:-----------------------:|:-----:|:--------:|:-----------------------|
| systemTime     | UInt32                  | -     | 4 Byte   | System time            |
| dataType       | [DataType](#DataType)   | -     | 1 Byte   | Received data type     |


<br>
<br>


## <a name="Request">Request</a>

Request

Request data to drone or controller

```py
class Request(ISerializable):

    def __init__(self):
        self.dataType    = DataType.None_
```

| Variable Name | Type                        | Range | Size     | Description       |
|:-------------:|:---------------------------:|:-----:|:--------:|:------------------|
| dataType      | [DataType](#DataType)       | -     | 1 Byte   | Request data type |


<br>
<br>


## <a name="Control">Control</a>

Control

Can be used for both Flight and Drive mode.

```py
class Control(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
        self.throttle   = 0
```

| Variable Name | Type      | Range      | Size     | Description |
|:-------------:|:---------:|:----------:|:--------:|:------------|
| roll          | Int8      | -100 ~ 100 | 1 Byte   | Roll        |
| pitch         | Int8      | -100 ~ 100 | 1 Byte   | Pitch       |
| yaw           | Int8      | -100 ~ 100 | 1 Byte   | Yaw         |
| throttle      | Int8      | -100 ~ 100 | 1 Byte   | Throttle    |


<br>
<br>


## <a name="Command">Command</a>

Command

Used to send commands to the drone or controller.
The option must have a value or a enumerate value for each type.

```py
class Command(ISerializable):

    def __init__(self):
        self.commandType    = CommandType.None_
        self.option         = 0
```

| Variable Name  | Type                                    | Range  | Size     | Description  |
|:--------------:|:---------------------------------------:|:------:|:--------:|:-------------|
| commandType    | [CommandType](#CommandType)             | -      | 1 Byte   | Command Type |
| option         | [ModeVehicle](02_system.md#ModeVehicle) | -      | 1 Byte   | Option       |
|                | [FlightEvent](02_system.md#FlightEvent) | -      | 1 Byte   |              |
|                | [DriveEvent](02_system.md#DriveEvent)   | -      | 1 Byte   |              |
|                | [Headless](02_system.md#Headless)       | -      | 1 Byte   |              |
|                | [Trim](02_system.md#Trim)               | -      | 1 Byte   |              |
|                | UInt8                                   | -      | 1 Byte   |              |


<br>
<br>


## <a name="LightModeDrone">LightModeDrone</a>

Drone LED mode

```py
class LightModeDrone(Enum):
    
    None_               = 0x00

    EyeNone             = 0x10
    EyeHold             = 0x11      # Eye LED color Hold 
    EyeMix              = 0x12      # Eye LED change color Sequential
    EyeFlicker          = 0x13      # Eye LED flicker light        	
    EyeFlickerDouble    = 0x14      # Eye LED flicker light (Blinking twice and turning off as much as the blinking time.)       	
    EyeDimming          = 0x15      # Eye LED Dimming

    ArmNone             = 0x40
    ArmHold             = 0x41      # Arm LED color Hold
    ArmMix              = 0x42      # Arm LED change color Sequential
    ArmFlicker          = 0x43      # Arm LED flicker light   
    ArmFlickerDouble    = 0x44      # Arm LED flicker light (Blinking twice and turning off as much as the blinking time.)   
    ArmDimming          = 0x45      # Arm LED Dimming
    ArmFlow             = 0x46      # Arm LED flow first to second color
    ArmFlowReverse      = 0x47      # Arm LED flow second to first color

    EndOfType           = 0x48
```


<br>
<br>


## <a name="Color">Color</a>

RGB LED color setting

Off at 0 and brightest at 255.

```py
class Color(ISerializable):

    def __init__(self):
        self.r      = 0
        self.g      = 0
        self.b      = 0
```

| Variable Name | Type   | Range    | Size   | Description |
|:-------------:|:------:|:--------:|:------:|:------------|
| r             | UInt8  | 0 ~ 255  | 1 Byte | Red         |
| g             | UInt8  | 0 ~ 255  | 1 Byte | Green       |
| b             | UInt8  | 0 ~ 255  | 1 Byte | Blue        |


<br>
<br>


## <a name="Colors">Colors</a>

Color palette index

Colour index of the palette defined inside the drones and the controls.
Please recommend using it after testing. May differ from the color intended.

```py
class Colors(Enum):

    AliceBlue              = 0
    AntiqueWhite           = 1
    Aqua                   = 2
    Aquamarine             = 3
    Azure                  = 4
    Beige                  = 5
    Bisque                 = 6
    Black                  = 7
    BlanchedAlmond         = 8
    Blue                   = 9
    BlueViolet             = 10
    Brown                  = 11
    BurlyWood              = 12
    CadetBlue              = 13
    Chartreuse             = 14
    Chocolate              = 15
    Coral                  = 16
    CornflowerBlue         = 17
    Cornsilk               = 18
    Crimson                = 19
    Cyan                   = 20
    DarkBlue               = 21
    DarkCyan               = 22
    DarkGoldenRod          = 23
    DarkGray               = 24
    DarkGreen              = 25
    DarkKhaki              = 26
    DarkMagenta            = 27
    DarkOliveGreen         = 28
    DarkOrange             = 29
    DarkOrchid             = 30
    DarkRed                = 31
    DarkSalmon             = 32
    DarkSeaGreen           = 33
    DarkSlateBlue          = 34
    DarkSlateGray          = 35
    DarkTurquoise          = 36
    DarkViolet             = 37
    DeepPink               = 38
    DeepSkyBlue            = 39
    DimGray                = 40
    DodgerBlue             = 41
    FireBrick              = 42
    FloralWhite            = 43
    ForestGreen            = 44
    Fuchsia                = 45
    Gainsboro              = 46
    GhostWhite             = 47
    Gold                   = 48
    GoldenRod              = 49
    Gray                   = 50
    Green                  = 51
    GreenYellow            = 52
    HoneyDew               = 53
    HotPink                = 54
    IndianRed              = 55
    Indigo                 = 56
    Ivory                  = 57
    Khaki                  = 58
    Lavender               = 59
    LavenderBlush          = 60
    LawnGreen              = 61
    LemonChiffon           = 62
    LightBlue              = 63
    LightCoral             = 64
    LightCyan              = 65
    LightGoldenRodYellow   = 66
    LightGray              = 67
    LightGreen             = 68
    LightPink              = 69
    LightSalmon            = 70
    LightSeaGreen          = 71
    LightSkyBlue           = 72
    LightSlateGray         = 73
    LightSteelBlue         = 74
    LightYellow            = 75
    Lime                   = 76
    LimeGreen              = 77
    Linen                  = 78
    Magenta                = 79
    Maroon                 = 80
    MediumAquaMarine       = 81
    MediumBlue             = 82
    MediumOrchid           = 83
    MediumPurple           = 84
    MediumSeaGreen         = 85
    MediumSlateBlue        = 86
    MediumSpringGreen      = 87
    MediumTurquoise        = 88
    MediumVioletRed        = 89
    MidnightBlue           = 90
    MintCream              = 91
    MistyRose              = 92
    Moccasin               = 93
    NavajoWhite            = 94
    Navy                   = 95
    OldLace                = 96
    Olive                  = 97
    OliveDrab              = 98
    Orange                 = 99
    OrangeRed              = 100
    Orchid                 = 101
    PaleGoldenRod          = 102
    PaleGreen              = 103
    PaleTurquoise          = 104
    PaleVioletRed          = 105
    PapayaWhip             = 106
    PeachPuff              = 107
    Peru                   = 108
    Pink                   = 109
    Plum                   = 110
    PowderBlue             = 111
    Purple                 = 112
    RebeccaPurple          = 113
    Red                    = 114
    RosyBrown              = 115
    RoyalBlue              = 116
    SaddleBrown            = 117
    Salmon                 = 118
    SandyBrown             = 119
    SeaGreen               = 120
    SeaShell               = 121
    Sienna                 = 122
    Silver                 = 123
    SkyBlue                = 124
    SlateBlue              = 125
    SlateGray              = 126
    Snow                   = 127
    SpringGreen            = 128
    SteelBlue              = 129
    Tan                    = 130
    Teal                   = 131
    Thistle                = 132
    Tomato                 = 133
    Turquoise              = 134
    Violet                 = 135
    Wheat                  = 136
    White                  = 137
    WhiteSmoke             = 138
    Yellow                 = 139
    YellowGreen            = 140
    
    EndOfType              = 141
```


<br>
<br>


## <a name="LightMode">LightMode</a>

LED Mode

Use the palette index to change LED behavior mode.

```py
class LightMode(ISerializable):

    def __init__(self):
        self.mode        = LightModeDrone.None_
        self.colors      = Colors.Black
        self.interval    = 0
```

| Variable Name  | Type                              | Range   | Size     | Description                    |
|:--------------:|:---------------------------------:|:-------:|:--------:|:-------------------------------|
| mode           | [LightModeDrone](#LightModeDrone) | -       | 1 Byte   | Drone LED Mode                 |
| colors         | [Colors](#Colors)                 | -       | 1 Byte   | LED palette index              |
| interval       | UInt8                             | 0 ~ 255 | 1 Byte   | Color brightness call interval |


<br>
<br>


## <a name="LightModeCommand">LightModeCommand</a>

LED Mode change(Palette) + Command

Add a command to the LightMode.

```py
class LightModeCommand(ISerializable):
    
    def __init__(self):
        self.lightMode  = LightMode()
        self.command    = Command()
```

| Variable Name | Type                     | Range | Size     | Description |
|:-------------:|:------------------------:|:-----:|:--------:|:------------|
| lightMode     | [LightMode](#LightMode)  | -     | 3 Byte   | LED Mode    |
| command       | [Command](#Command)      | -     | 2 Byte   | Command     |


<br>
<br>


## <a name="LightModeCommandIr">LightModeCommandIr</a>

LED Mode change(Palette) + Command + IR

Add a IR to the LightModeCommand.

```py
class LightModeCommandIr(ISerializable):
    
    def __init__(self):
        self.lightMode  = LightMode()
        self.command    = Command()
        self.irData     = 0
```

| Variable Name | Type                     | Range                   | Size     | Description |
|:-------------:|:------------------------:|:-----------------------:|:--------:|:------------|
| lightMode     | [LightMode](#LightMode)  | -                       | 3 Byte   | LED Mode    |
| command       | [Command](#Command)      | -                       | 2 Byte   | Command     |
| irData        | UInt32                   | 0x00000000 ~ 0xFFFFFFFF | 4 Byte   | IR data     |


<br>
<br>


## <a name="LightModeColor">LightModeColor</a>

LED Mode change(RGB)

Change LED behavior mode by manually specifying RGB color.

```py
class LightModeColor(ISerializable):
    
    def __init__(self):
        self.mode       = LightMode()
        self.color      = Color()
        self.interval   = 0
```

| Variable Name  | Type                              | Range   | Size     | Description                    |
|:--------------:|:---------------------------------:|:-------:|:--------:|:-------------------------------|
| mode           | [LightModeDrone](#LightModeDrone) | -       | 1 Byte   | Drone LED Mode                 |
| colors         | [Colors](#Colors)                 | -       | 3 Byte   | LED RGB Color                  |
| interval       | UInt8                             | 0 ~ 255 | 1 Byte   | Color brightness call interval |



<br>
<br>


## <a name="LightEvent">LightEvent</a>

LED Event change(Palette)

Use the palette index to execute LED events.

```py
class LightEvent(ISerializable):
    
    def __init__(self):
        self.event      = LightModeDrone.None_
        self.colors     = Colors.Black
        self.interval   = 0
        self.repeat     = 0
```

| Variable Name  | Type                              | Range   | Size     | Description                    |
|:--------------:|:---------------------------------:|:-------:|:--------:|:-------------------------------|
| event          | [LightModeDrone](#LightModeDrone) | -       | 1 Byte   | Drone LED Mode                 |
| colors         | [Colors](#Colors)                 | -       | 1 Byte   | LED palette index              |
| interval       | UInt8                             | 0 ~ 255 | 1 Byte   | Color brightness call interval |
| repeat         | UInt8                             | 0 ~ 255 | 1 Byte   | Repeat count                   |


<br>
<br>


## <a name="LightEventCommand">LightEventCommand</a>

LED Event change(Palette) + Command

Add a command to the LightEvent.

```py
class LightEventCommand(ISerializable):
    
    def __init__(self):
        self.lightEvent = LightEvent()
        self.command    = Command()
```

| Variable Name  | Type                      | Range | Size     | Description        |
|:--------------:|:-------------------------:|:-----:|:--------:|:-------------------|
| lightEvent     | [LightEvent](#LightEvent) | -     | 4 Byte   | LED Event          |
| command        | [Command](#Command)       | -     | 2 Byte   | Command            |



<br>
<br>


## <a name="LightEventCommandIr">LightEventCommandIr</a>

LED Event change(Palette) + Command + IR

Add a IR to the LightEventCommand.

```py
class LightEventCommandIr(ISerializable):
    
    def __init__(self):
        self.lightEvent = LightEvent()
        self.colors     = Colors.Black
        self.command    = Command()
        self.irData     = 0
```

| Variable Name  | Type                      | Range                    | Size     | Description        |
|:--------------:|:-------------------------:|:------------------------:|:--------:|:-------------------|
| lightEvent     | [LightEvent](#LightEvent) | -                        | 4 Byte   | LED Event          |
| command        | [Command](#Command)       | -                        | 2 Byte   | Command            |
| irData         | UInt32                    | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | IR data            |


<br>
<br>


## <a name="LightEventColor">LightEventColor</a>

LED Event change(RGB)

Execute LED events by directly specifying RGB color.

```py
class LightEventColor(ISerializable):
    
    def __init__(self):
        self.event      = LightEvent()
        self.color      = Color()
```

| Variable Name  | Type                              | Range   | Size     | Description                    |
|:--------------:|:---------------------------------:|:-------:|:--------:|:-------------------------------|
| event          | [LightModeDrone](#LightModeDrone) | -       | 1 Byte   | Drone LED Mode                 |
| colors         | [Colors](#Colors)                 | -       | 3 Byte   | LED RGB Color                  |
| interval       | UInt8                             | 0 ~ 255 | 1 Byte   | Color brightness call interval |
| repeat         | UInt8                             | 0 ~ 255 | 1 Byte   | Repeat count                   |


<br>
<br>


## <a name="Address">Address</a>

Device Address

Unique device id assigned to the device.

```py
class Address(ISerializable):

    def __init__(self):
        self.address    = bytearray()
```

| Variable Name | Type          | Range | Size     | Description    |
|:-------------:|:-------------:|:-----:|:--------:|:---------------|
| address       | UInt8 Array   | -     | 6 Byte   | Device Address |


<br>
<br>


## <a name="State">State</a>

Drone state

```py
class State(ISerializable):

    def __init__(self):
        self.modeVehicle        = ModeVehicle.None_

        self.modeSystem         = ModeSystem.None_
        self.modeFlight         = ModeFlight.None_
        self.modeDrive          = ModeDrive.None_

        self.sensorOrientation  = SensorOrientation.None_
        self.headless           = Headless.None_
        self.battery            = 0
```

| Variable Name     | Type                                                | Range    | Size     | Description        |
|:-----------------:|:---------------------------------------------------:|:--------:|:--------:|:-------------------|
| modeVehicle       | [ModeVehicle](02_system.md#ModeVehicle)             | -        | 1 Byte   | Vehicle mode       |
| modeSystem        | [ModeSystem](02_system.md#ModeSystem)               | -        | 1 Byte   | System mode        |
| modeFlight        | [ModeFlight](02_system.md#ModeFlight)               | -        | 1 Byte   | Flight mode        |
| modeDrive         | [ModeDrive](02_system.md#ModeDrive)                 | -        | 1 Byte   | Drive mode         |
| sensorOrientation | [SensorOrientation](02_system.md#SensorOrientation) | -        | 1 Byte   | Sensor Orientation |
| headless          | [Headless](02_system.md#Headless)                   | -        | 1 Byte   | Headless mode      |
| battery           | UInt8                                               | 0 ~ 100  | 1 Byte   | Drone battery      |


<br>
<br>


## <a name="Attitude">Attitude</a>

Attitude

```py
class Attitude(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
```

| Variable Name | Type  | Range             | Size     | Description |
|:-------------:|:-----:|:-----------------:|:--------:|:------------|
| roll          | Int16 | -32,768 ~ 32,767  | 2 Byte   | Roll        |
| pitch         | Int16 | -32,768 ~ 32,767  | 2 Byte   | Pitch       |
| yaw           | Int16 | -32,768 ~ 32,767  | 2 Byte   | Yaw         |


<br>
<br>


## <a name="GyroBias">GyroBias</a>

Gyro Bias

Inherit from [Attitude](#Attitude)

```py
class GyroBias(Attitude):
    pass
```

| Variable Name | Type  | Range             | Size     | Description |
|:-------------:|:-----:|:-----------------:|:--------:|:------------|
| roll          | Int16 | -32,768 ~ 32,767  | 2 Byte   | Roll        |
| pitch         | Int16 | -32,768 ~ 32,767  | 2 Byte   | Pitch       |
| yaw           | Int16 | -32,768 ~ 32,767  | 2 Byte   | Yaw         |


<br>
<br>


## <a name="TrimFlight">TrimFlight</a>

Flight trim setting

If drone flows in one direction. Adjust the orientation to allow hovering. The value changes for work correctly.

```py
class TrimFlight(ISerializable):

    def __init__(self):
        self.roll       = 0
        self.pitch      = 0
        self.yaw        = 0
        self.throttle   = 0
```

| Variable Name | Type  | Range      | Size     | Description |
|:-------------:|:-----:|:----------:|:--------:|:------------|
| roll          | Int16 | -200 ~ 200 | 2 Byte   | Roll        |
| pitch         | Int16 | -200 ~ 200 | 2 Byte   | Pitch       |
| yaw           | Int16 | -200 ~ 200 | 2 Byte   | Yaw         |
| throttle      | Int16 | -200 ~ 200 | 2 Byte   | Throttle    |


<br>
<br>


## <a name="TrimDrive">TrimDrive</a>

Drive trim setting

If drone is not to go straight. Adjust go straight ahead. The wheel value changes for work correctly.

```py
class TrimDrive(ISerializable):

    def __init__(self):
        self.wheel      = 0
```

| Variable Name | Type  | Range      | Size     | Description |
|:-------------:|:-----:|:----------:|:--------:|:------------|
| wheel         | Int16 | -200 ~ 200 | 2 Byte   | Wheel       |


<br>
<br>


## <a name="CountFlight">CountFlight</a>

Flight counter

Each counter value is stored in the drone as UInt32. But, converts to UInt16 for transfer.
If a larger value is needed, We will change it.

```py
class CountFlight(ISerializable):

    def __init__(self):
        self.timeFlight     = 0

        self.countTakeOff   = 0
        self.countLanding   = 0
        self.countAccident  = 0
```

| Variable Name    | Type       | Range      | Size     | Description       |
|:----------------:|:----------:|:----------:|:--------:|:------------------|
| timeFlight       | UInt64     | -          | 8 Byte   | Flight time(ms)   |
| countTakeOff     | UInt16     | 0 ~ 65535  | 2 Byte   | count of takeoff  |
| countLanding     | UInt16     | 0 ~ 65535  | 2 Byte   | count of landing  |
| countAccident    | UInt16     | 0 ~ 65535  | 2 Byte   | count of accident |


<br>
<br>


## <a name="CountDrive">CountDrive</a>

Drive counter

Each counter value is stored in the drone as UInt32. But, converts to UInt16 for transfer.
If a larger value is needed, We will change it.
But count may also increase due to the impact of uneven road surfaces during actual driving. Consider it meaningless at this time.

```py
class CountDrive(ISerializable):
    
    def __init__(self):
        self.timeDrive      = 0

        self.countAccident  = 0
```

| Variable Name    | Type       | Range      | Size     | Description       |
|:----------------:|:----------:|:----------:|:--------:|:------------------|
| timeDrive        | UInt64     | -          | 8 Byte   | Drive time(ms)    |
| countAccident    | UInt16     | 0 ~ 65535  | 2 Byte   | count of accident |


<br>
<br>


## <a name="IrMessage">IrMessage</a>

IR Message transmission

An IR data receiver is attached to the front and back of the drone.
The direction tells which receiver has received the data.

```py
class IrMessage(ISerializable):

    def __init__(self):
        self.direction  = Direction.None_
        self.irData     = 0
```

| Variable Name    | Type                                 | Range                    | Size     | Description        |
|:----------------:|:------------------------------------:|:------------------------:|:--------:|:-------------------|
| direction        | [Direction](02_system.md#Direction)  | -                        | 1 Byte   | IR Sensor position |
| irData           | UInt32                               | 0x00000000 ~ 0xFFFFFFFF  | 4 Byte   | data               |


<br>
<br>


## <a name="Imu">Imu</a>

IMU Sensor Data and Position of the drones :

The angleRoll, anglePitch, angleYaw is the same as the attitude values of drones can be received at Attitude protocol.

```py
class Imu(ISerializable):

    def __init__(self):
        self.accelX     = 0
        self.accelY     = 0
        self.accelZ     = 0
        self.gyroRoll   = 0
        self.gyroPitch  = 0
        self.gyroYaw    = 0
        self.angleRoll  = 0
        self.anglePitch = 0
        self.angleYaw   = 0
```

| Variable Name | Type  | Range            | Size   | Description   |
|:-------------:|:-----:|:----------------:|:------:|:--------------|
| accelX        | Int16 | -32,768 ~ 32,767 | 2 Byte | Accelometer X |
| accelY        | Int16 | -32,768 ~ 32,767 | 2 Byte | Accelometer Y |
| accelZ        | Int16 | -32,768 ~ 32,767 | 2 Byte | Accelometer Z |
| gyroRoll      | Int16 | -32,768 ~ 32,767 | 2 Byte | Gyro Roll     |
| gyroPitch     | Int16 | -32,768 ~ 32,767 | 2 Byte | Gyro Pitch    |
| gyroYaw       | Int16 | -32,768 ~ 32,767 | 2 Byte | Gyro Yaw      |
| angleRoll     | Int16 | -32,768 ~ 32,767 | 2 Byte | Angle Roll    |
| anglePitch    | Int16 | -32,768 ~ 32,767 | 2 Byte | Angle Pitch   |
| angleYaw      | Int16 | -32,768 ~ 32,767 | 2 Byte | Angle Yaw     |


<br>
<br>


## <a name="Pressure">Pressure</a>

Pressure sensor

```py
class Pressure(ISerializable):

    def __init__(self):
        self.d1             = 0
        self.d2             = 0
        self.temperature    = 0
        self.pressure       = 0
```

| Variable Name | Type   | Range  | Size   | Description              |
|:-------------:|:------:|:------:|:------:|:-------------------------|
| d1            | UInt32 | -      | 4 Byte | Raw data 1               |
| d2            | UInt32 | -      | 4 Byte | Raw data 2               |
| temperature   | UInt32 | -      | 4 Byte | temperature(℃)           |
| pressure      | UInt32 | -      | 4 Byte | pressure(C level height) |


<br>
<br>


## <a name="ImageFlow">ImageFlow</a>

Image optical flow calcurated axis position

```py
class ImageFlow(ISerializable):

    def __init__(self):
        self.positionX     = 0
        self.positionY     = 0
```

| Variable Name | Type   | Range  | Size   | Description |
|:-------------:|:------:|:------:|:------:|:------------|
| positionX     | UInt32 | -      | 4 Byte | X Axis(m)   |
| positionY     | UInt32 | -      | 4 Byte | Y Axis(m)   |


<br>
<br>


## <a name="ButtonFlagDrone">ButtonFlagDrone</a>

Drone button flag

```py
class ButtonFlagDrone(Enum):

    None_           = 0x00
    
    Reset           = 0x01
```


<br>
<br>


## <a name="Button">Button</a>

Drone button input

```py
class Button(ISerializable):

    def __init__(self):
        self.button     = 0
```

| Variable Name | Type   | Range  | Size   | Description |
|:-------------:|:------:|:------:|:------:|:------------|
| button        | UInt16 | -      | 1 Byte | 버튼 입력     |


<br>
<br>


## <a name="Battery">Battery</a>

Battery info

```py
class Battery(ISerializable):

    def __init__(self):
        self.adjustGradient             = 0
        self.adjustYIntercept           = 0
        self.gradient                   = 0
        self.yIntercept                 = 0
        self.flagBatteryCalibration     = False
        self.batteryRaw                 = 0
        self.batteryPercent             = 0
        self.voltage                    = 0
```

| Variable Name           | Type   | Range        | Size     | Description                       |
|:-----------------------:|:------:|:------------:|:--------:|:----------------------------------|
| adjustGradient          | Int16  | -            | 2 Byte   | adjustment gradient               |
| adjustYIntercept        | Int16  | -            | 2 Byte   | adjustment y-intercept            |
| gradient                | Int16  | -            | 2 Byte   | gradient                          |
| yIntercept              | Int16  | -            | 2 Byte   | y-intercept                       |
| flagBatteryCalibration  | Bool   | True / False | 1 Byte   | battery calibration complete flag |
| batteryRaw              | Int32  | 0 ~ 4095     | 4 Byte   | battery ADC Raw                   |
| batteryPercent          | Int8   | 0 ~ 100      | 1 Byte   | battery remain percent            |
| voltage                 | Int16  | 0 ~ 4.5      | 2 Byte   | battery power Voltage             |


<br>
<br>


## <a name="MotorBlock">MotorBlock</a>

Motor block

When performing a rotation in a forward direction, always enter 0 in reverse.
If you do the reverse direction, always enter 0 in forward.

```py
class MotorBlock(ISerializable):

    def __init__(self):
        self.forward    = 0
        self.reverse    = 0
```

| Variable Name | Type   | Range    | Size   | Description                  |
|:-------------:|:------:|:--------:|:------:|:-----------------------------|
| forward       | UInt16 | 0 ~ 4095 | 2 Byte | Moter forward rotation speed |
| reverse       | UInt16 | 0 ~ 4095 | 2 Byte | Moter reverse rotation speed |


<br>
<br>


## <a name="Motor">Motor</a>

All Motor control

The order is from the left front motor to the clockwise.

```py
class Motor(ISerializable):

    def __init__(self):
        self.motor      = []
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
        self.motor.append(MotorBlock())
```

| Variable Name | Type                      | Range | Size   | Description       |
|:-------------:|:-------------------------:|:-----:|:------:|:------------------|
| motor[0]      | [MotorBlock](#MotorBlock) | -     | 4 Byte | Left front motor  |
| motor[1]      | [MotorBlock](#MotorBlock) | -     | 4 Byte | Right front motor |
| motor[2]      | [MotorBlock](#MotorBlock) | -     | 4 Byte | Right rear motor  |
| motor[3]      | [MotorBlock](#MotorBlock) | -     | 4 Byte | Left rear motor  |


<br>
<br>


## <a name="Range">Range</a>

Range sensor

If an additional sensor module is not installed, output only bottom value.

Range sensor can be measured in 40mm ~ 2000mm.

```py
class Range(ISerializable):

    def __init__(self):
        self.left       = 0
        self.front      = 0
        self.right      = 0
        self.rear       = 0
        self.top        = 0
        self.bottom     = 0
```

| Variable Name | Type   | Range   | Size   | Description |
|:-------------:|:------:|:-------:|:------:|:------------|
| left          | UInt16 | -       | 2 Byte | left(mm)    |
| front         | UInt16 | -       | 2 Byte | front(mm)   |
| right         | UInt16 | -       | 2 Byte | right(mm)   |
| rear          | UInt16 | -       | 2 Byte | rear(mm)    |
| top           | UInt16 | -       | 2 Byte | top(mm)     |
| bottom        | UInt16 | -       | 2 Byte | bottom(mm)  |


<br>
<br>


## <a name="UpdateInformation">UpdateInformation</a>

Firmware Information

It contains current firmware information and the progress of the update.

```py
class UpdateInformation(ISerializable):

    def __init__(self):
        self.modeUpdate     = ModeUpdate.None_

        self.deviceType     = DeviceType.None_
        self.imageType      = ImageType.None_
        self.version        = 0

        self.year           = 0
        self.month          = 0
        self.day            = 0
```

| Variable Name | Type                                  | Range | Size     | Description                 |
|:-------------:|:-------------------------------------:|:-----:|:--------:|:----------------------------|
| modeUpdate    | [ModeUpdate](02_system.md#ModeUpdate) | -     | 1 Byte   | The progress of the update  |
| deviceType    | [DeviceType](02_system.md#DeviceType) | -     | 4 Byte   | Device type                 |
| imageType     | [ImageType](02_system.md#ImageType)   | -     | 1 Byte   | Image type                  |
| version       | UInt16                                | -     | 2 Byte   | Firmware version            |
| year          | UInt8                                 | -     | 1 Byte   | Firmware build year         |
| month         | UInt8                                 | -     | 1 Byte   | Firmware build month        |
| day           | UInt8                                 | -     | 1 Byte   | Firmware build day          |


<br>
<br>


## <a name="LinkRssi">LinkRssi</a>

RSSI

Received signal strength indication

[http://www.metageek.com/training/resources/understanding-rssi.html](http://www.metageek.com/training/resources/understanding-rssi.html)

Returns the signal strength of the device connected to the Link module.

```py
class LinkRssi(ISerializable):

    def __init__(self):
        self.rssi       = 0
```

| Variable Name | Type     | Range     | Size   | Description     |
|:-------------:|:--------:|:---------:|:------:|:----------------|
| rssi          | Int8     | -100 ~ 0  | 1 Byte | Signal strength |


<br>
<br>


## <a name="Message">Message</a>

Message

Send string message.

```py
class Message():

    def __init__(self):
        self.message    = ""
```

| Variable Name | Type            | Range | Size           | Description |
|:-------------:|:---------------:|:-----:|:--------------:|:------------|
| message       | ASCII String    | -     | Device depence | Message     |


<br>

---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. **Protocol**
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)
 
<br>

[Index](index.md)
