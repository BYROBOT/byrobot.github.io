***DRONEFIGHTER2017 / Protocol / Definitions***<br>
Modified : 2018.02.08

---

#### Introduce Drone Fighter's base protocol definition.

---

<br>

## <a name="Protocol_CommandType">Protocol::CommandType::Type</a>
CommandBase structer use commandType variables.

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
            None = 0,                       // No event

            // mode
            ModeVehicle = 0x10,             // Vehicle Mode change

            // control
            Coordinate = 0x20,              // Vehicle coordinate change
            Trim,                           // Vehicle trim change
            FlightEvent,                    // Vehicle flight event
            DriveEvent,                     // Vehicle drive event
            Stop,                           // Vehicle stop
            
            ClearTrim = 0x50,               // Vehicle trim clear
            GyroBiasAndTrimReset,           // Vehicle gyro bias and trim reset
            
            UserInterfacePreset = 0x80,     // User interface preset.
            DataStorageWrite,               // Save to database if changes are mode

            // admin
            ClearCounter = 0xA0,            // Drone log counter clear (for Administrator)

            EndOfType
        };
    }
}
```

<br>
<br>

## <a name="Mode_Vehicle">Mode::Vehicle::Type</a>
Drone Fighter Vehicle mode enum

```cpp
namespace Mode
{
    namespace Vehicle
    {
        enum Type
        {
            None = 0,           // None
            
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
            None = 0,           // none
            
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
            None = 0,           // none
            
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
            None = 0,           // none
            
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

## <a name="SensorOrientation">SensorOrientation::Type</a>
Sensor Orientation
```cpp
namespace SensorOrientation
{
    enum Type
    {
        None = 0,           // none
        
        Normal,             // Normal status
        ReverseStart,       // Reverse start
        Reversed,           // Reversed
        
        EndOfType
    };
}
```

<br>
<br>

## <a name="Direction">Direction::Type</a>
Drone direction
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
Select drone coordinate.
World is absolute mode, Determine the coordinates of the drone world around the external world.
Local is normal mode, Determine the coordinate with the drones in the center.

```cpp
namespace Coordinate
{
    enum Type
    {
        None = 0,           // none
        
        World,              // Absolute
        Local,              // Normal
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Trim">Trim::Type</a>
If drone flows in one direction. Adjust the orientation to allow hovering. The value changes for each transfer.

```cpp
namespace Trim
{
    enum Type
    {
        None = 0,           // none

        RollIncrease,       // Roll increase
        RollDecrease,       // Roll decrease                
        PitchIncrease,      // Pitch increase
        PitchDecrease,      // Pitch decrease               
        YawIncrease,        // Yaw increase
        YawDecrease,        // Yaw decrease             
        ThrottleIncrease,   // Throttle increase
        ThrottleDecrease,   // Throttle decrease
        
        Reset,              // all trim reset
        
        EndOfType
    };
}
```


<br>
<br>


## <a name="Motor_Direction">Motor::Direction::Type</a>
Drone motor direction

```cpp
namespace Motor
{
    namespace Direction
    {
        enum Type
        {
            None = 0,           // none

            Forward,            // forward
            Reverse,            // backward

            EndOfType
        };
    }
}
```

<br>
<br>


## <a name="Motor_Part">Motor::Part::Type</a>
Drone moter part

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
Excute flight event.

```cpp
namespace FlightEvent
{
    enum Type
    {
        None = 0,               // none
        
        Stop = 0x10,            // stop
        TakeOff,                // takeoff
        Landing,                // landing
        
        Reverse,                // reverse
        
        FlipFront,              // flip front
        FlipRear,               // flip rear
        FlipLeft,               // flip left
        FlipRight,              // flip right
        
        Shot,                   // IR shot action
        UnderAttack,            // IR shot recieve action
        
        ResetHeading = 0xA0,    // heading reset(in absolute mode reset degree)
        
        EndOfType   
    };
}
```


<br>
<br>


## <a name="Joystick_Direction">Joystick::Direction::Type</a>
Drone Fighter 2017 controller's joystic direction

```cpp
namespace Joystick
{
    // Joystick direction
    namespace Direction
    {
        enum Type
        {
            None    = 0,        // none
            
            VT      = 0x10,     //     Up(Vertical)
            VM      = 0x20,     // Center(Vertical)
            VB      = 0x40,     //   Down(Vertical)
            
            HL      = 0x01,     //   Left(Horizontal)
            HM      = 0x02,     // Center(Horizontal)
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
Drone Fighter 2017 controller's joystic direction

```cpp
namespace Joystick
{
    // Joystick direction
    namespace Event
    {
        enum Type
        {
            None    = 0,        // 이벤트 없음
            
            In,                 // 특정 영역에 진입
            Stay,               // 특정 영역에서 상태 유지
            Out,                // 특정 영역에서 벗어남
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="Joystick_Command">Joystick::Command::Type</a>
Drone Fighter 2017 controller's joystic direction

```cpp
namespace Joystick
{
    // Joystick command
    namespace Command
    {
        enum Type
        {
            None,

            UpDownUpDown,       // Up-Down-Up-Down
            LeftRightLeftRight, // Left-Right-Left-Right
            TurnLeft,           // Turn left
            TurnRight,          // Turn right

            EndOfType
        };
    }
}
```


<br>
<br>



## <a name="Buzzer_Mode">Buzzer::Mode::Type</a>
Drone Fighter 2017 controller's buzzer mode

```cpp
namespace Buzzer
{
    namespace Mode
    {
        enum Type
        {
            Stop                = 0,    // Stop(Use to turn off the buzzer when received from the communication, call in a set only)

            MuteInstantally     = 1,    // Apply Instantly in mute
            MuteContinually     = 2,    // Apply continualy in mute

            ScaleInstantally    = 3,    // Instantly application of scale
            ScaleContinually    = 4,    // Continualy application of scale

            HzInstantally       = 5,    // Instantly application of Hz
            HzContinually       = 6,    // Continualy application of Hz

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
            /* 1, 2, 3 octave is Timer tick use (noise of sound) */
            C1, CS1, D1, DS1, E1, F1, FS1, G1, GS1, A1, AS1, B1,
            C2, CS2, D2, DS2, E2, F2, FS2, G2, GS2, A2, AS2, B2,
            C3, CS3, D3, DS3, E3, F3, FS3, G3, GS3, A3, AS3, B3,

            /* 4, 5, 6, 7, 8 octave is PWM use(normal sound) */
            C4, CS4, D4, DS4, E4, F4, FS4, G4, GS4, A4, AS4, B4,
            C5, CS5, D5, DS5, E5, F5, FS5, G5, GS5, A5, AS5, B5,
            C6, CS6, D6, DS6, E6, F6, FS6, G6, GS6, A6, AS6, B6,
            C7, CS7, D7, DS7, E7, F7, FS7, G7, GS7, A7, AS7, B7,
            C8, CS8, D8, DS8, E8, F8, FS8, G8, GS8, A8, AS8, B8,
        
            EndOfType,
            
            Mute    = 0xEE,     // mute
            Fin     = 0xFF      // end of sheet
        };
    }
}
```

<br>
<br>


## <a name="Vibrator_Mode">Vibrator::Mode::Type</a>
Drone Fighter 2017 controller's vibrator mode

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
<br>


## <a name="UserInterface_Commands">UserInterface::Commands::Type</a>
Drone Fighter 2017 controller's input command type

```cpp
namespace UserInterface
{
    namespace Commands
    {
        enum Type
        {
            None,
            
            Setup_Button_FrontLeft_Down,
            Setup_Button_FrontRight_Down,
            Setup_Button_MidTurnLeft_Down,
            Setup_Button_MidTurnRight_Down,
            Setup_Button_MidUp_Down,
            Setup_Button_MidLeft_Down,
            Setup_Button_MidRight_Down,
            Setup_Button_MidDown_Down,
            
            Setup_Joystick_Left_Up_In,
            Setup_Joystick_Left_Left_In,
            Setup_Joystick_Left_Right_In,
            Setup_Joystick_Left_Down_In,
            
            Setup_Joystick_Right_Up_In,
            Setup_Joystick_Right_Left_In,
            Setup_Joystick_Right_Right_In,
            Setup_Joystick_Right_Down_In,
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="UserInterface_Functions">UserInterface::Functions::Type</a>
Drone Fighter 2017 controller interface functions

```cpp
namespace UserInterface
{
    namespace Functions
    {
        enum Type
        {
            None,
            
            JoystickCalibration_Reset,
            
            Change_Team_Red,
            Change_Team_Blue,
            
            Change_Mode_Vehicle_Flight,
            Change_Mode_Vehicle_FlightNoGuard,
            Change_Mode_Vehicle_Drive,
            
            Change_Coordinate_Local,                // Normal
            Change_Coordinate_World,                // Absolute
            
            Change_Mode_Control_Mode1,
            Change_Mode_Control_Mode2,
            Change_Mode_Control_Mode3,
            Change_Mode_Control_Mode4,
                            
            GyroBias_Reset,
            
            Change_Mode_USB_CDC,
            Change_Mode_USB_HID,
            
            EndOfType
        };
    }
}
```


<br>
<br>


## <a name="UserInterface_Preset">UserInterface::Preset::Type</a>
Drone Fighter 2017 controller interface preset

```cpp
namespace UserInterface
{
    namespace Preset
    {
        enum Type
        {
            None,
            
            Clear,              // clear preset
            Custom,             // user setting (Changed in default settings)
            
            Drone2017,          // default setting
            Education,          // education setting
            
            EndOfType
        };
    }
}
```


<br>


---

### DRONE FIGHTER 2017

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)

<br>

[Index](index.md)
