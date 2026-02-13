**[Coding Drone Plus](index.md)** / **Protocol** / **Definitions**

Modified : 2026.1.29

---

#### Basic definitions being used by Coding Drone Plus

---

* Kramdown table of contents
{:toc .toc}


<br>


<a name="Protocol_CommandType"></a>
## Protocol::CommandType::Type

Command type

```cpp
namespace Protocol
{
    namespace CommandType
    {
        enum Type
        {
                None                    = 0x00,      // none

                Stop                    = 0x01,      // stop

                ModeControlFlight       = 0x02,      // set flight control mode
                Headless                = 0x03,      // set headless mode
                ControlSpeed            = 0x04,      // set control speed

                ClearBias               = 0x05,      // reset gyro/accel bias (trim is also reset)
                ClearTrim               = 0x06,      // reset trim

                FlightEvent             = 0x07,      // run flight event

                SetDefault              = 0x08,      // reset to default settings
                Backlight               = 0x09,      // set controller backlight
                ModeController          = 0x0A,      // set controller mode (0x10:Control, 0x80:Link)
                Link                    = 0x0B,      // link control (0:Client Mode, 1:Server Mode, 2:Pairing Start)
                LoadDefaultColor        = 0x0C,      // set default color

                Trim                    = 0x0D,      // trim

                ModeTest                = 0xF0,      // test lock (unavailable until test completed / 27:enable, 11:disable)

                ResetTimeCount          = 0xFC,      // reset test time (option 37)

                RfChannel               = 0xFD,      // RF channel (2400, 2440, 2483)
                RfModulate              = 0xFE,      // RF modulate (Modulate, Rx, Unmodulate)

                EndOfType
        };
    }
}
```


<br>
<br>


<a name="ModelNumber"></a>
## ModelNumber::Type

Model number

Starting from CodingDrone (Drone4), DeviceType is shared across products. During firmware update, an additional identifier is required to distinguish devices beyond DeviceType, so ModelNumber was added.

```cpp
namespace ModelNumber
{
    enum Type
    {
        None                    = 0,

        //                           AAAABBCC, AAAA(Project Number), BB(Device Type), CC(Revision)
        // Drone_11 Pan2025 chip
        Drone_11_Drone_P0        = 0x000B1000,    // reserve
        Drone_11_Drone_P1        = 0x000B1001,    // 65 no coding
        Drone_11_Drone_P2        = 0x000B1002,    // fixed wing
        Drone_11_Drone_P3        = 0x000B1003,    // 65 coding
        Drone_11_Drone_P4        = 0x000B1004,    // 95 battle drone
        Drone_11_Drone_P5        = 0x000B1005,    // drone soccer
        Drone_11_Drone_P6        = 0x000B1006,    // reserve
        Drone_11_Drone_P7        = 0x000B1007,    // reserve
        Drone_11_Drone_P8        = 0x000B1008,    // reserve
        Drone_11_Drone_P9        = 0x000B1009,    // reserve

        Drone_11_Controller_P0   = 0x000B2000,    // reserve
        Drone_11_Controller_P1   = 0x000B2001,    // small size, 65 drone, USB
        Drone_11_Controller_P2   = 0x000B2002,    // small size, 65 drone, no USB
        Drone_11_Controller_P3   = 0x000B2003,    // small size, bird wing, fixed wing, no return
        Drone_11_Controller_P4   = 0x000B2004,    // middle size, battle drone, USB
        Drone_11_Controller_P5   = 0x000B2005,    //
        Drone_11_Controller_P6   = 0x000B2006,    //
        Drone_11_Controller_P7   = 0x000B2007,    //
        Drone_11_Controller_P8   = 0x000B2008,    //
        Drone_11_Controller_P9   = 0x000B2009,    //

        Drone_11_Link_P0         = 0x000B3000,    // Drone_11_Link_P0 RoboRobo
        Drone_11_Link_P1         = 0x000B3001,    //
        Drone_11_Link_P2         = 0x000B3002,    //
        Drone_11_Link_P3         = 0x000B3003,    //
        Drone_11_Link_P4         = 0x000B3004,    //
        Drone_11_Link_P5         = 0x000B3005,    //
        Drone_11_Link_P6         = 0x000B3006,    //
        Drone_11_Link_P7         = 0x000B3007,    //
        Drone_11_Link_P8         = 0x000B3008,    //
        Drone_11_Link_P9         = 0x000B3009,    //

        // Drone_12 chip
        Drone_12_Drone_P0        = 0x000C1000,    // coding drone STM32F401RC + XN297
        Drone_12_Drone_P1        = 0x000C1001,    // coding drone STM32F407VE + NRF24L01
        Drone_12_Drone_P2        = 0x000C1002,    //
        Drone_12_Drone_P3        = 0x000C1003,    //
        Drone_12_Drone_P4        = 0x000C1004,    //
        Drone_12_Drone_P5        = 0x000C1005,    //
        Drone_12_Drone_P6        = 0x000C1006,    //
        Drone_12_Drone_P7        = 0x000C1007,    //
        Drone_12_Drone_P8        = 0x000C1008,    //
        Drone_12_Drone_P9        = 0x000C1009,    //

        Drone_12_Controller_P0   = 0x000C2000,    // coding drone STM32F401RC + XN297
        Drone_12_Controller_P1   = 0x000C2001,    // coding drone STM32F407VE + NRF24L01
        Drone_12_Controller_P2   = 0x000C2002,    //
        Drone_12_Controller_P3   = 0x000C2003,    //
        Drone_12_Controller_P4   = 0x000C2004,    //
        Drone_12_Controller_P5   = 0x000C2005,    //
        Drone_12_Controller_P6   = 0x000C2006,    //
        Drone_12_Controller_P7   = 0x000C2007,    //
        Drone_12_Controller_P8   = 0x000C2008,    //
        Drone_12_Controller_P9   = 0x000C2009,    //

        Drone_12_Link_P0         = 0x000C3000,    // Drone_12_Link_P0
        Drone_12_Link_P1         = 0x000C3001,    //
        Drone_12_Link_P2         = 0x000C3002,    //
        Drone_12_Link_P3         = 0x000C3003,    //
        Drone_12_Link_P4         = 0x000C3004,    //
        Drone_12_Link_P5         = 0x000C3005,    //
        Drone_12_Link_P6         = 0x000C3006,    //
        Drone_12_Link_P7         = 0x000C3007,    //
        Drone_12_Link_P8         = 0x000C3008,    //
        Drone_12_Link_P9         = 0x000C3009,    //

        Drone_12_Tester_P0       = 0x000CA000,
        Drone_12_Tester_P1       = 0x000CA001,    //
        Drone_12_Tester_P2       = 0x000CA002,    //
        Drone_12_Tester_P3       = 0x000CA003,    //
        Drone_12_Tester_P4       = 0x000CA004,    //
        Drone_12_Tester_P5       = 0x000CA005,    //
        Drone_12_Tester_P6       = 0x000CA006,    //
        Drone_12_Tester_P7       = 0x000CA007,    //
        Drone_12_Tester_P8       = 0x000CA008,    //
        Drone_12_Tester_P9       = 0x000CA009,    //

        Drone_12_Monitor_P0      = 0x000CA100,
        Drone_12_Monitor_P1      = 0x000CA101,    //
        Drone_12_Monitor_P2      = 0x000CA102,    //
        Drone_12_Monitor_P3      = 0x000CA103,    //
        Drone_12_Monitor_P4      = 0x000CA104,    //
        Drone_12_Monitor_P5      = 0x000CA105,    //
        Drone_12_Monitor_P6      = 0x000CA106,    //
        Drone_12_Monitor_P7      = 0x000CA107,    //
        Drone_12_Monitor_P8      = 0x000CA108,    //
        Drone_12_Monitor_P9      = 0x000CA109,    //

        // Drone_13 chip
        Drone_13_Drone_P0        = 0x000D1000,    // coding drone STM32F401RC + XN297
        Drone_13_Drone_P1        = 0x000D1001,    //
        Drone_13_Drone_P2        = 0x000D1002,    //
        Drone_13_Drone_P3        = 0x000D1003,    //
        Drone_13_Drone_P4        = 0x000D1004,    //
        Drone_13_Drone_P5        = 0x000D1005,    //
        Drone_13_Drone_P6        = 0x000D1006,    //
        Drone_13_Drone_P7        = 0x000D1007,    //
        Drone_13_Drone_P8        = 0x000D1008,    //
        Drone_13_Drone_P9        = 0x000D1009,    //

        Drone_13_Controller_P0   = 0x000D2000,    // coding drone STM32F401RC + XN297
        Drone_13_Controller_P1   = 0x000D2001,    //
        Drone_13_Controller_P2   = 0x000D2002,    //
        Drone_13_Controller_P3   = 0x000D2003,    //
        Drone_13_Controller_P4   = 0x000D2004,    //
        Drone_13_Controller_P5   = 0x000D2005,    //
        Drone_13_Controller_P6   = 0x000D2006,    //
        Drone_13_Controller_P7   = 0x000D2007,    //
        Drone_13_Controller_P8   = 0x000D2008,    //
        Drone_13_Controller_P9   = 0x000D2009,    //

        Drone_13_Link_P0         = 0x000D3000,    // Drone_13_Link_P0
        Drone_13_Link_P1         = 0x000D3001,    //
        Drone_13_Link_P2         = 0x000D3002,    //
        Drone_13_Link_P3         = 0x000D3003,    //
        Drone_13_Link_P4         = 0x000D3004,    //
        Drone_13_Link_P5         = 0x000D3005,    //
        Drone_13_Link_P6         = 0x000D3006,    //
        Drone_13_Link_P7         = 0x000D3007,    //
        Drone_13_Link_P8         = 0x000D3008,    //
        Drone_13_Link_P9         = 0x000D3009,    //

        Drone_13_Tester_P0       = 0x000DA000,
        Drone_13_Tester_P1       = 0x000DA001,    //
        Drone_13_Tester_P2       = 0x000DA002,    //
        Drone_13_Tester_P3       = 0x000DA003,    //
        Drone_13_Tester_P4       = 0x000DA004,    //
        Drone_13_Tester_P5       = 0x000DA005,    //
        Drone_13_Tester_P6       = 0x000DA006,    //
        Drone_13_Tester_P7       = 0x000DA007,    //
        Drone_13_Tester_P8       = 0x000DA008,    //
        Drone_13_Tester_P9       = 0x000DA009,    //

        Drone_13_Monitor_P0      = 0x000DA100,
        Drone_13_Monitor_P1      = 0x000DA101,    //
        Drone_13_Monitor_P2      = 0x000DA102,    //
        Drone_13_Monitor_P3      = 0x000DA103,    //
        Drone_13_Monitor_P4      = 0x000DA104,    //
        Drone_13_Monitor_P5      = 0x000DA105,    //
        Drone_13_Monitor_P6      = 0x000DA106,    //
        Drone_13_Monitor_P7      = 0x000DA107,    //
        Drone_13_Monitor_P8      = 0x000DA108,    //
        Drone_13_Monitor_P9      = 0x000DA109,    //
    };
}
```


<br>
<br>


<a name="Protocol_DeviceType"></a>
## DeviceType::Type

Device type

```cpp
namespace DeviceType
{
    enum Type
    {
        None            = 0x00,

        Drone           = 0x10,     // drone (Server)

        Controller      = 0x20,     // controller (Client)

        LinkClient      = 0x30,     // link module (Client)
        LinkServer      = 0x31,     // link module (Server)
        BleClient       = 0x32,     // BLE client
        BleServer       = 0x33,     // BLE server

        Range           = 0x40,     // range sensor module

        Base            = 0x70,     // base

        ByScratch       = 0x80,     // byScratch
        Scratch         = 0x81,     // Scratch
        Entry           = 0x82,     // Naver Entry

        Tester          = 0xA0,     // tester
        Monitor         = 0xA1,     // monitor
        Updater         = 0xA2,     // firmware updater
        Encrypter       = 0xA3,     // encrypter

        EndOfType,

        Whispering      = 0xFE,     // deliver only to the immediately adjacent device (do not forward)
        Broadcasting    = 0xFF      // deliver to all connected devices
    };
}
```


<br>
<br>


<a name="ErrorFlagsForSensor"></a>
## ErrorFlagsForSensor::Type

Sensor error flag

```cpp
namespace ErrorFlagsForSensor
{
    enum Type
    {
        None                                    = 0x00000000,

        Motion_NoAnswer                         = 0x00000001,    // Motion sensor no answer
        Motion_WrongValue                       = 0x00000002,    // Motion sensor wrong value
        Motion_NotCalibrated                    = 0x00000004,    // Gyro bias calibration not completed
        Motion_Calibrating                      = 0x00000008,    // Gyro bias calibrating

        Pressure_NoAnswer                       = 0x00000010,    // Pressure sensor no answer
        Pressure_WrongValue                     = 0x00000020,    // Pressure sensor wrong value

        RangeGround_NoAnswer                    = 0x00000100,    // Ground range sensor no answer
        RangeGround_WrongValue                  = 0x00000200,    // Ground range sensor wrong value
        RangeFront_NoAnswer                     = 0x00000400,    // Front range sensor no answer
        RangeFront_WrongValue                   = 0x00000800,    // Front range sensor wrong value

        Flow_NoAnswer                           = 0x00001000,    // Flow sensor no answer
        Flow_WrongValue                         = 0x00002000,    // Flow wrong value
        Flow_CannotRecognizeGroundImage         = 0x00004000,    // Cannot recognize ground image

        RF_NoAnswer                             = 0x10000000,    // RF no answer
        RF_Paired                               = 0x20000000,    // RF pairing complete
        RF_Connected                            = 0x40000000,    // RF connected
    };
}
```


<br>
<br>


<a name="ErrorFlagsForState"></a>
## ErrorFlagsForState::Type

State error flag

```cpp
namespace ErrorFlagsForState
{
    enum Type
    {
        None                                    = 0x00000000,

        NotRegistered                           = 0x00000001,    // Device not registered
        FlashReadLock_UnLocked                  = 0x00000002,    // Flash memory read lock is not set
        BootloaderWriteLock_UnLocked            = 0x00000004,    // Bootloader area write lock is not set
        LowBattery                              = 0x00000008,    // Low Battery
        
        TakeoffFailure_CheckPropellerAndMotor   = 0x00000010,    // Takeoff failure (check propeller and motor)
        CheckPropellerVibration                 = 0x00000020,    // Propeller vibration detected
        Attitude_NotStable                      = 0x00000040,    // Attitude is tilted too much or flipped
        Motors_NotGood                          = 0x00000080,    // Motors are not in good condition
        
        CanNotFlip_LowBattery                   = 0x00000100,    // Battery is below 30
        CanNotFlip_TooHeavy                     = 0x00000200,    // Vehicle is too heavy
    };
}
```


<br>
<br>


<a name="Mode_Control_Flight"></a>
## Mode::Control::Flight::Type

Flight control mode

```cpp
namespace Mode
{
    namespace Control
    {
        namespace Flight
        {
            enum Type
            {
                None        = 0x00,

                Attitude    = 0x10,     // Attitude - X,Y are angles (deg), Z,Yaw are speed (m/s)
                Position    = 0x11,     // Position - X,Y,Z,Yaw are speed (m/s)
                Manual      = 0x12,     // Manual altitude control
                Rate        = 0x13,     // Rate - X,Y are angular speed (deg/s), Z,Yaw are speed (m/s)
                Function    = 0x14,     // Function - X,Y,Z,Yaw are speed (m/s)
                BirdWing    = 0x15,     // Bird wing
                FixedWing   = 0x16,     // Fixed wing

                EndOfType
            };
        }
    }
}
```


<br>
<br>


<a name="Mode_System"></a>
## Mode::System::Type

System operation state

```cpp
namespace Mode
{
    namespace System
    {
        enum Type
        {
            None,

            Boot                = 0x10,     // boot
            Start,                          // start code execution
            Running,                        // main code running
            ReadyToReset,                   // waiting to reset (reset after 1 second)

            Error               = 0xA0,     // error

            EndOfType
        };
    }
    
}
```


<br>
<br>


<a name="Mode_Drone"></a>
## Mode::Drone::Type

Drone mode

```cpp
namespace Mode
{
    namespace Drone
    {
        enum Type
        {
            None,                   // none
            
            Flight      = 0x10,     // flight
            Card,                   // card coding
            Motion,                 // motion coding
            Piano,                  // piano mode
            
            Link        = 0x80,     // relay
            Calibration,            // color calibration mode
            
            Error       = 0xA0,     // error (cannot operate normally due to a problem)
            
            EndOfType
        };
    }
    
}
```


<br>
<br>


<a name="Mode_Controller"></a>
## Mode::Controller::Type

Controller mode

```cpp
namespace Mode
{
    namespace Controller
    {
        enum Type
        {
            None,                   // none
            
            Control     = 0x10,     // control
            Setup,                  // setup
            
            Link        = 0x80,     // link
            
            Error       = 0xA0,     // error
            
            EndOfType
        };
    }
    
}
```


<br>
<br>


<a name="Mode_Connection"></a>
## Mode::Connection::Type

Connection mode

```cpp
namespace Mode
{
    namespace Connection
    {
        enum Type
        {
            None,
            
            PairingStart,					// pairing start (wait after address reset // one side generates a new address and sends it)
            PairingExchange,				// pairing data exchange
            PairingComplete,				// drone pairing complete
            
            Ready,							// not connected (transitions to this state before connecting or after disconnecting)
            
            ConnectingStart,				// start connecting
            Connecting,						// checking connection
            Connected,						// connected
            
            LostConnection,					// lost connection (no communication between Server and Client)
            
            Disconnected,					// disconnected
            
            EndOfPairing
        };
    }
    
}
```


<br>
<br>


<a name="Mode_Flight"></a>
## Mode::Flight::Type

Flight controller operation state

```cpp
namespace Mode
{
    namespace Flight
    {
        enum Type
        {
            None                = 0x00,

            Ready               = 0x10,     // ready

            Start               = 0x11,     // takeoff ready
            Takeoff             = 0x12,     // takeoff (auto transitions to Flight)
            Flight              = 0x13,     // flight
            Landing             = 0x14,     // landing
            Flip                = 0x15,     // flip
            Reverse             = 0x16,     // reverse

            Stop                = 0x20,     // forced stop

            Accident            = 0x30,     // accident (auto transitions to Ready)
            Error               = 0x31,     // error

            Test                = 0x40,     // test mode

            EndOfType
        };
    }
    
}
```


<br>
<br>


<a name="Mode_Update"></a>
## Mode::Update::Type

Update state

```cpp
namespace Updater
{
    namespace ModeUpdate
    {
        enum Type
        {
            None,               //

            Ready,              // update available
            Update,             // updating
            Complete,           // update complete

            Failed,             // update failed (e.g., reached complete but body CRC16 mismatch)

            NotAvailable,       // update not available (e.g., debug mode)
            RunApplication,     // running application

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="SensorOrientation"></a>
## SensorOrientation::Type

Sensor orientation

```cpp
namespace SensorOrientation
{
    enum Type
    {
        None = 0,            // none

        Normal,              // normal
        ReverseStart,        // started to flip over
        Reversed,            // flipped over

        EndOfType
    };
}
```


<br>
<br>


<a name="Direction"></a>
## Direction::Type

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

        Center,

        EndOfType
    };
}
```


<br>
<br>


<a name="Mode_Movement"></a>
## Mode::Movement::Type

Movement state

```cpp
namespace Mode
{
    namespace Movement
    {
        enum Type
        {
            None                = 0x00,

            Ready               = 0x01,
            Hovering            = 0x02,
            Moving              = 0x03,
            ReturnHome          = 0x04
        };
    }
}
```


<br>
<br>


<a name="Headless"></a>
## Headless::Type

Heading reference

Select the reference direction for control.

Headless moves based on the <b><i>takeoff heading</i></b> or the <b><i>user-defined heading</i></b>, regardless of which direction the drone is facing.

Normal moves based on the <b><i>current heading of the drone</i></b>.

On the controller, Headless is shown as 'Headless ON' and Normal as 'Headless OFF'. The default setting is Normal.

```cpp
namespace Headless
{
    enum Type
    {
        None = 0,

        Headless,   // headless (absolute)
        Normal,     // normal

        EndOfType
    };
}
```


<br>
<br>


<a name="Rotation"></a>
## Rotation::Type

Motor rotation direction

Coding Drone Plus has four motors. Starting from the front-left motor, motor numbers are assigned as 0, 1, 2, 3.

During flight, motor 0 and 2 rotate clockwise, and motor 1 and 3 rotate counterclockwise.

Each motor rotates only in its fixed direction.

```cpp
namespace Rotation
{
    enum Type
    {
        None = 0,

        Clockwise,              // clockwise
        Counterclockwise,       // counterclockwise

        EndOfType
    };
}
```


<br>
<br>


<a name="Motor_Part"></a>
## Motor::Part::Type

Motor number

```cpp
namespace Motor
{
    namespace Part
    {
        enum Type
        {
            MFR,    // Front Right
            MRR,    // Rear Right
            MRL,    // Rear Left
            MFL,    // Front Left

            EndOfPart,

            All
        };
    }
}
```


<br>
<br>


<a name="FlightEvent"></a>
## FlightEvent::Type

Flight event

```cpp
namespace FlightEvent
{
    enum Type
    {
        None            = 0x00,     // none
        
        Stop            = 0x10,     // stop
        Takeoff         = 0x11,     // takeoff
        Landing         = 0x12,     // landing
        
        Reverse         = 0x13,     // reverse
        
        FlipFront       = 0x14,     // flip
        FlipRear        = 0x15,     // flip
        FlipLeft        = 0x16,     // flip
        FlipRight       = 0x17,     // flip
        
        Return          = 0x18,     // return

        Shot            = 0x90,     // shot
        UnderAttack,                // under attack
        
        ResetHeading    = 0xA0,     // reset heading (in headless mode, set current heading to 0 degrees)
        
        EndOfType
    };
}
```


<br>
<br>


<a name="Button_Drone_ButtonType"></a>
## Button::Drone::ButtonType::Type

Drone button flag

```cpp
namespace Button
{
    namespace Drone
    {
        namespace ButtonType
        {
            enum Type
            {
                None        = 0x0000,

                // button
                Pairing     = 0x0001    // pairing
            };
        }
    }
}
```


<br>
<br>


<a name="Button_Controller_ButtonType"></a>
## Button::Controller::ButtonType::Type

Controller button flag

```cpp
namespace Button
{
    namespace Controller
    {
        namespace ButtonType
        {
            enum Type
            {
                None                = 0x0000,

                // button
                FrontLeftTop        = 0x0001,
                FrontLeftBottom     = 0x0002,
                FrontRightTop       = 0x0004,
                FrontRightBottom    = 0x0008,

                TopLeft             = 0x0010,
                TopRight            = 0x0020,   // POWER ON/OFF

                MidUp               = 0x0040,
                MidLeft             = 0x0080,
                MidRight            = 0x0100,
                MidDown             = 0x0200,

                BottomLeft          = 0x0400,
                BottomRight         = 0x0800,
            };
        }
    }
}
```


<br>
<br>


<a name="Button_Event"></a>
## Button::Event::Type

Button event

```cpp
namespace Button
{
    namespace Event
    {
        enum Type
        {
            None,

            Down,               // press start
            Press,              // pressing
            Up,                 // release

            EndContinuePress    // end continuous press
        };
    }
}
```


<br>
<br>


<a name="Joystick_Direction"></a>
## Joystick::Direction::Type

Joystick direction

```cpp
namespace Joystick
{
    namespace Direction
    {
        enum Type
        {
            None    = 0x00,     // undefined area (ignored)

            VT      = 0x10,     // top (vertical)
            VM      = 0x20,     // middle (vertical)
            VB      = 0x40,     // bottom (vertical)

            HL      = 0x01,     // left (horizontal)
            HM      = 0x02,     // middle (horizontal)
            HR      = 0x04,     // right (horizontal)

            TL = 0x11,  TM = 0x12,  TR = 0x14,
            ML = 0x21,  CN = 0x22,  MR = 0x24,
            BL = 0x41,  BM = 0x42,  BR = 0x44
        };
    }
}
```


<br>
<br>


<a name="Joystick_Event"></a>
## Joystick::Event::Type

Joystick event

```cpp
namespace Joystick
{
    namespace Event
    {
        enum Type
        {
            None    = 0,        // no event

            In,                 // enter area
            Stay,               // stay in area
            Out,                // leave area

            Calibration,        // calibrating

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="Buzzer_Mode"></a>
## Buzzer::Mode::Type

Buzzer mode

```cpp
namespace Buzzer
{
    namespace Mode
    {
        enum Type
        {
            Stop                = 0,    // stop (Stop in Mode is used to turn off the buzzer when received via communication; called only by set)

            MuteInstantly       = 1,    // apply mute instantly
            MuteContinually     = 2,    // reserve mute

            ScaleInstantly      = 3,    // apply scale instantly
            ScaleContinually    = 4,    // reserve scale

            HzInstantly         = 5,    // apply frequency instantly
            HzContinually       = 6,    // reserve frequency

            EndOfType
        };
    }
}
```


<br>
<br>


<a name="Buzzer_Scale"></a>
## Buzzer::Scale::Type

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

            Mute    = 0xEE,     // mute
            Fin     = 0xFF      // end of score
        };
    }
}
```

<br>
<br>

<a name="Vibrator_Mode"></a>
## Vibrator::Mode::Type

Vibrator mode

```cpp
namespace Vibrator
{
    namespace Mode
    {
        enum Type
        {
            Stop            = 0,    // stop

            Instantly       = 1,    // apply instantly
            Continually     = 2,    // reserve

            EndOfType
        };
    }
}
```


<br>


---

<h3>Coding Drone Plus</H3>

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. [DataType](03_datatype.md)
4. ***Definitions***
5. [Structs](05_structs.md)
6. [Structs - Light](06_structs_light.md)
<!-- 7. [Structs - Display](07_structs_display.md) -->

<br>

[Index](index.md)
