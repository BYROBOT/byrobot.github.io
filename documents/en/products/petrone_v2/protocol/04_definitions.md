**[PETRONE_V2](index.md)** / **Protocol** / **Definitions**

Modified : 2018.02.13

---

#### Introduce Petrone V2 base protocol definition.

---


<br>


## <a name="Protocol_CommandType">Protocol::CommandType::Type</a>

Command Type

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None = 0,

            // 설정
            ModeVehicle = 0x10,             // Vehicle Mode change

            // 제어
            Coordinate = 0x20,              // Vehicle coordinate 
            Trim,                           // Vehicle trim change
            FlightEvent,                    // Vehicle flight event
            DriveEvent,                     // Vehicle drive event
            Stop,                           // Vehicle stop
            
            ClearTrim = 0x50,               // Vehicle trim clear
            ClearGyroBias,                  // Vehicle gyro bias and trim reset
            
            DataStorageWrite = 0x80,        // Save to database if changes are mode

            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Protocol_DeviceType">Protocol::DeviceType::Type</a>
Device Type enum

```cpp
namespace Protocol
{
    namespace DeviceType
    {
        enum Type
        {
            None = 0,

            Drone = 0x30,           // Drone
            Controller,             // Controller
            Link,                   // LINK Module
            Tester,                 // Tester
            Monitor,                // Monitor
            Updater,                // Firmware Updater
            Encrypter,              // Encrypter
            Scratch,                // Scratch
            Entry,                  // NAVER Entry
            ByScratch,              // ByScratch

            EndOfType,

            Broadcasting = 0xFF
        };
    }
}
```


<br>
<br>


## <a name="ErrorFlagsForSensor">ErrorFlagsForSensor::Type</a>

Sensor error flag

```cpp
namespace ErrorFlagsForSensor
{
    enum Type
    {
        None                        = 0x00000000,

        Imu_NoAnswer                = 0x00000001,   // IMU is not response
        Imu_WrongValue              = 0x00000002,
        Imu_NotCalibrated           = 0x00000004,   // Gyro Bias is not calibrate 
        Imu_Calibrating             = 0x00000008,   // Gyro Bias calibrating.

        Pressure_NoAnswer           = 0x00000010,   // Pressure sensor not response
        Pressure_WrongValue         = 0x00000020,

        RangeGround_NoAnswer        = 0x00000100,   // Range sensor not response
        RangeGround_WrongValue      = 0x00000200,

        Camera_NoAnswer             = 0x00001000,   // Camera not response
        OpticalFlow_WrongValue      = 0x00002000,

        Battery_NoAnswer            = 0x00010000,   // Battery not response
        Battery_WrongValue          = 0x00020000,
        Battery_NotCalibrated       = 0x00040000,   // Battery in/output no calibrated.
    };
}
```


<br>
<br>


## <a name="ErrorFlagsForState">ErrorFlagsForState::Type</a>

State error flag

```cpp
namespace ErrorFlagsForState
{
    enum Type
    {
        None                        = 0x00000000,

        NotTested                   = 0x00000001,   // not tested
    };
}
```


<br>
<br>


## <a name="Mode_Vehicle">Mode::Vehicle::Type</a>

Vehicle mode enum

```cpp
namespace Mode
{
    namespace Vehicle
    {
        enum Type
        {
            None = 0,
            
            Flight = 0x10,      // Flight mode with guard
            FlightNoGuard,      // Flight mode without guard
            FlightFPV,          // Flight FPV mode
            
            Drive = 0x20,       // Drive mode
            DriveFPV,           // Drive FPV mode
            
            Test = 0x30,        // Test
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Mode_System">Mode::System::Type</a>
Indicates the system behavior drone status.

```cpp
namespace Mode
{
    namespace System
    {
        enum Type
        {
            None = 0,
            
            Boot,               // booting
            Start,              // start code
            Running,            // running main code
            ReadyToReset,       // ready for reset ( Reset in 1 second )
            Error,              // error
                    
            EndOfType
        };
    }
    
}
```


<br>
<br>


## <a name="Mode_Flight">Mode::Flight::Type</a>

Indicates the operational status of the flight mode.

```cpp
namespace Mode
{
    namespace Flight
    {
        enum Type
        {
            None = 0,
            
            Ready = 0x10,       // Ready
            
            TakeOff,            // TakeOff (Automatically transferred to flight status)
            Flight,             // Flight
            Landing,            // Landing
            Flip,               // Flip         
            Reverse,            // Reverse
            
            Stop = 0x20,        // Force stop
            
            Accident = 0x30,    // Accident (Automatically transferred to Ready status)
            Error,              // Error
            
            Test = 0x40,        // test mode
            
            EndOfType
        };
    }
    
}
```


<br>
<br>


## <a name="Mode_Drive">Mode::Drive::Type</a>
Indicates the operational status of the drive mode.

```cpp
namespace Mode
{
    namespace Drive
    {
        enum Type
        {
            None = 0,
            
            Ready = 0x10,       // Ready
            
            Start,              // Start
            Drive,              // Drive
            
            Stop = 0x20,        // Force stop
            
            Accident = 0x30,    // Accident (Automatically transferred to Ready status)
            Error,              // Error
            
            Test = 0x40,        // test mode

            EndOfType
        };
    }
    
}
```


<br>
<br>


## <a name="Mode_Update">Mode::Update::Type</a>

Update state

```cpp
namespace Mode
{
    namespace Update
    {
        enum Type
        {
            None,

            Ready,              // Ready for update
            Update,             // Updating.
            Complete,           // Update complete
                
            Faild,              // Update Faild( Ex: Update has reached completion but firmware data body CRC16 does not match, etc.)

            NotAvailable,       // Cannot available update(Debug mode, etc.)
            RunApplication,     // application is running

            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="SensorOrientation">SensorOrientation::Type</a>
Sensor Orientation

```cpp
namespace SensorOrientation
{
    enum Type
    {
        None = 0,
        
        Normal,             // Normal
        ReverseStart,       // Reverse Start
        Reversed,           // Reversed
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Direction">Direction::Type</a>
Direction

```cpp
namespace Direction
{
    enum Type
    {
        None = 0,

        Left,
        Front,
        Right,
        Rear,
        
        Top,
        Bottom,
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Coordinate">Coordinate::Type</a>

Control coordinate.

- **World** mode : The Absolute mode. The reference directions is fixed in the ***direction of view when the drones are takeoff***.
- **Local** : Moves on the direction the drone is looking.
On the controller,  'World' is display ' Headless ON ' and Local is display ' Headless OFF '. The default setting is Local.
조종기 상에서는 World를 'Headless ON', Local을 'Headless OFF'로 표현하고 있습니다. 기본 설정은 Local입니다.

```cpp
namespace Coordinate
{
    enum Type
    {
        None = 0,
        
        World,      // Absolute(Headless/Absolute)
        Local,      // Normal(Normal)
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Trim">Trim::Type</a>

Trim

If PETRONE flows in one direction. Adjust the orientation to allow hovering. The value changes for each transfer.

```cpp
namespace Trim
{
    enum Type
    {
        None = 0,

        RollIncrease,       // Roll Increase
        RollDecrease,       // Roll Decrease                
        PitchIncrease,      // Pitch Increase
        PitchDecrease,      // Pitch Decrease               
        YawIncrease,        // Yaw Increase
        YawDecrease,        // Yaw Decrease             
        ThrottleIncrease,   // Throttle Increase
        ThrottleDecrease,   // Throttle Decrease
        
        Reset,              // reset all trim
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Rotation">Rotation::Type</a>

Motor Rotation control

PETRONE V2 has total 4 motors, From the front left motor, numbers are 0, 1, 2 and 3. 
During drone flight 0 and 2 motors rotate clockwise and motors 1 and 3 rotate counterclockwise.
Motors 0 and 1 operate both clockwise and counterclockwise to restore the drones to their original state when turned.

```cpp
namespace Rotation
{
    enum Type
    {
        None = 0,
        
        Clockwise,              // Clockwise direction
        Counterclockwise,       // Counterclockwise direction
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Motor_Part">Motor::Part::Type</a>

Motor number

```cpp
namespace Rotation
{
    namespace Part
    {
        enum Type
        {
            M1,		// Front Left
            M2,		// Front Right
            M3,		// Rear Right
            M4,		// Rear Left
            
            EndOfPart,
            
            All
        };
    }
}
```


<br>
<br>


## <a name="FlightEvent">FlightEvent::Type</a>

PETRONE Flight event 

```cpp
namespace FlightEvent
{
    enum Type
    {
        None = 0,               // none
        
        Stop = 0x10,            // Force stop
        TakeOff,                // takeoff
        Landing,                // landing
        
        Reverse,                // reverse
        
        FlipFront,              // flip front(Not Yet)
        FlipRear,               // flip rear(Not Yet)
        FlipLeft,               // flip left(Not Yet)
        FlipRight,              // flip right(Not Yet)
        
        Shot,                   // IR shot action
        UnderAttack,            // IR shot recieve action
        
        ResetHeading = 0xA0,    // reset heading(Change the current heading to 0 degrees when in absolute mode)
        
        EndOfType   
    };
}
```


<br>
<br>


## <a name="DriveEvent">DriveEvent::Type</a>

PETRONE Drive event

```cpp
namespace DriveEvent
{
    enum Type
    {
        None = 0,           // None

        Stop = 0x10,        // Force stop

        Shot,               // IR shot action
        UnderAttack,        // IR shot recieve action

        EndOfType
    };
}
```


<br>
<br>


## <a name="Button_Event">Button::Event::Type</a>

Button event

```cpp
namespace Button
{
    namespace Event
    {
        enum Type
        {
            None,

            Down,               // Press down start
            Press,              // Press In
            Up,                 // Button Up

            EndContinuePress    // End of press
        };
    }
}
```


<br>
<br>


## <a name="Joystick_Direction">Joystick::Direction::Type</a>

Joystick direction

```cpp
namespace Joystick
{
    // Joystick direction
    namespace Direction
    {
        enum Type
        {
            None    = 0,        // Undefined Area (Ignore)
            
            VT      = 0x10,     //    Top(Vertical)
            VM      = 0x20,     // Middle(Vertical)
            VB      = 0x40,     // Bottom(Vertical)
            
            HL      = 0x01,     //   Left(Horizontal)
            HM      = 0x02,     // Middle(Horizontal)
            HR      = 0x04,     //  Right(Horizontal)
            
            TL = 0x11,  TM = 0x12,  TR = 0x14,
            ML = 0x21,  CN = 0x22,  MR = 0x24,
            BL = 0x41,  BM = 0x42,  BR = 0x44
        };
    }
}
```


<br>
<br>


## <a name="Joystick_Event">Joystick::Event::Type</a>

Joystick event

```cpp
namespace Joystick
{
    // Joystick event
    namespace Event
    {
        enum Type
        {
            None    = 0,        // no event
            
            In,                 // Specific area in
            Stay,               // Stay in a specific area
            Out,                // Specific area out
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Buzzer_Mode">Buzzer::Mode::Type</a>

Buzzer mode

```cpp
namespace Buzzer
{
    namespace Mode
    {
        enum Type
        {
            Stop                = 0,    // Stop in Mode is used to turn off the buzzer when received from communication, call in a set only

            MuteInstantally     = 1,    // Mute Instantally
            MuteContinually     = 2,    // Mute Continually

            ScaleInstantally    = 3,    // Scale Instantally
            ScaleContinually    = 4,    // Scale Continually

            HzInstantally       = 5,    // Hz Instantally
            HzContinually       = 6,    // Hz Continually

            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Buzzer_Scale">Buzzer::Scale::Type</a>

Buzzer scale

```cpp
namespace Buzzer
{
    namespace Scale
    {
        enum Type
        {
            C1, CS1, D1, DS1, E1, F1, FS1, G1, GS1, A1, AS1, B1,
            C2, CS2, D2, DS2, E2, F2, FS2, G2, GS2, A2, AS2, B2,
            C3, CS3, D3, DS3, E3, F3, FS3, G3, GS3, A3, AS3, B3,
            C4, CS4, D4, DS4, E4, F4, FS4, G4, GS4, A4, AS4, B4,
            
            C5, CS5, D5, DS5, E5, F5, FS5, G5, GS5, A5, AS5, B5,
            C6, CS6, D6, DS6, E6, F6, FS6, G6, GS6, A6, AS6, B6,
            C7, CS7, D7, DS7, E7, F7, FS7, G7, GS7, A7, AS7, B7,
            C8, CS8, D8, DS8, E8, F8, FS8, G8, GS8, A8, AS8, B8,
        
            EndOfType,
            
            Mute    = 0xEE,     // Mute
            Fin     = 0xFF      // The end of music
        };
    }
}
```

<br>
<br>


## <a name="Vibrator_Mode">Vibrator::Mode::Type</a>

Vibrator mode

```cpp
namespace Vibrator
{
    namespace Mode
    {
        enum Type
        {
            Stop            = 0,    // Stop
            
            Instantally     = 1,    // Instantly vibrate.
            Continually     = 2,    // Continualy vibrate.
            
            EndOfType
        };
    }
}
```


<br>


---

<h3>PETRONE V2</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
7. [Structs - Display](07_structs_display.md)

<br>

[Index](index.md)
