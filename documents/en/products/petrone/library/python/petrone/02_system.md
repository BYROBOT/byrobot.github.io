**[*petrone* for python](index.md)** / **System**

Modified : 2018.02.13

---

<h3>Introduce the system definitions.</h3>

---


<br>

## <a name="DeviceType">DeviceType</a>

Device type

Used mostly to determine version of device firmware.

```py
class DeviceType(Enum):
    
    None_               = 0x00

    DroneMain           = 0x01      # Drone main firmware
    DroneSub            = 0x02      # Drone sub firmware
    Link                = 0x03      # Link module
    Tester              = 0x04      # test

    EndOfType           = 0x05
```


<br>
<br>


## <a name="ModeVehicle">ModeVehicle</a>

Vehicle Mode

```py
class ModeVehicle(Enum):
    
    None_               = 0x00

    FlightGuard         = 0x10
    FlightNoGuard       = 0x11
    FlightFPV           = 0x12

    Drive               = 0x20
    DriveFPV            = 0x21

    Test                = 0x30

    EndOfType           = 0x31
```


<br>
<br>


## <a name="ModeSystem">ModeSystem</a>

System Operating Mode

```py
class ModeSystem(Enum):
    
    None_               = 0x00

    Boot                = 0x01      # Booting
    Wait                = 0x02      # Waiting for connect

    Ready               = 0x03      # Ready

    Running             = 0x04      # Running code

    Update              = 0x05      # Firmware update
    UpdateComplete      = 0x06      # Firmware update complete

    Error               = 0x07      # Error

    EndOfType           = 0x08
```


<br>
<br>


## <a name="ModeFlight">ModeFlight</a>

Flight mode - system operating 

```py
class ModeFlight(Enum):
    
    None_               = 0x00

    Ready               = 0x01      # Ready for fly

    TakeOff             = 0x02      # Takeoff (Automatic transition to flight mode)
    Flight              = 0x03      # Flight
    Flip                = 0x04
    Stop                = 0x05      # Force stop
    Landing             = 0x06      # Landing
    Reverse             = 0x07      # Reverse

    Accident            = 0x08      # Accident (Automatic transition to Ready)
    Error               = 0x09      # Error

    EndOfType           = 0x0A
```


<br>
<br>


## <a name="ModeDrive">ModeDrive</a>

Drive mode - system operating

```py
class ModeDrive(Enum):
    
    None_               = 0x00

    Ready               = 0x01      # Ready

    Start               = 0x02      # Start
    Drive               = 0x03      # Drive
    Stop                = 0x04      # Force stop

    Accident            = 0x05      # Accident (Automatic transition to Ready)
    Error               = 0x06      # Error

    EndOfType           = 0x07
```


<br>
<br>


## <a name="ModeUpdate">ModeUpdate</a>

Update mode - system operating

```py
class ModeUpdate(Enum):

    None_               = 0x00

    Ready               = 0x01      # Ready for Update
    Update              = 0x02      # Updating
    Complete            = 0x03      # Update complete

    Faild               = 0x04      # Update Faild( Ex: Update has reached completion but firmware data body CRC16 does not match, etc.)

    EndOfType           = 0x05
```


<br>
<br>


## <a name="FlightEvent">FlightEvent</a>

Flight event

```py
class FlightEvent(Enum):
    
    None_               = 0x00

    TakeOff             = 0x01      # Takeoff

    FlipFront           = 0x02      # Flip to front 
    FlipRear            = 0x03      # Flip to rear
    FlipLeft            = 0x04      # Flip to left
    FlipRight           = 0x05      # Flip to right

    Stop                = 0x06      # Stop
    Landing             = 0x07      # Landing
    Reverse             = 0x08      # Reverse

    Shot                = 0x09      # IR missle shot action
    UnderAttack         = 0x0A      # IR missle underattack action

    EndOfType           = 0x0B
```


<br>
<br>


## <a name="DriveEvent">DriveEvent</a>

Drive Event

```py
class DriveEvent(Enum):
    
    None_               = 0x00

    Stop                = 0x01
    
    Shot                = 0x02
    UnderAttack         = 0x03

    EndOfType           = 0x04
```


<br>
<br>


## <a name="Direction">Direction</a>

Direction

```py
class Direction(Enum):
    
    None_               = 0x00

    Left                = 0x01
    Front               = 0x02
    Right               = 0x03
    Rear                = 0x04

    Top                 = 0x05
    Bottom              = 0x06

    EndOfType           = 0x07
```


<br>
<br>


## <a name="SensorOrientation">SensorOrientation</a>

Sensor Orientation

To check the condition when the drone is Reversed.

```py
class SensorOrientation(Enum):
    
    None_               = 0x00

    Normal              = 0x01
    ReverseStart        = 0x02
    Reversed            = 0x03

    EndOfType           = 0x04
```


<br>
<br>


## <a name="Headless">Headless</a>

Headless mode

- **Headless** mode : The reference directions is fixed in the ***direction of view when the drones are takeoff***.

- **Normal** : Moves on the direction the drone is looking.

```py
class Headless(Enum):
    
    None_               = 0x00

    Headless            = 0x01      # Headless
    Normal              = 0x02      # Normal

    EndOfType           = 0x03
```


<br>
<br>


## <a name="Trim">Trim</a>

Trim

Used to increase or decrease the trim setting by step.

```py
class Trim(Enum):
    
    None_               = 0x00  # None

    RollIncrease        = 0x01  # Roll Increase
    RollDecrease        = 0x02  # Roll Decrease
    PitchIncrease       = 0x03  # Pitch Increase
    PitchDecrease       = 0x04  # Pitch Decrease
    YawIncrease         = 0x05  # Yaw Increase
    YawDecrease         = 0x06  # Yaw Decrease
    ThrottleIncrease    = 0x07  # Throttle Increase
    ThrottleDecrease    = 0x08  # Throttle Decrease

    Reset               = 0x09  # All trim reset

    EndOfType           = 0x0A
```


<br>


---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. **System**
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)

<br>

[Index](index.md)
