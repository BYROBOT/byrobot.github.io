***PETRONE / BLE / Protocol / DataType***<br>
Modified : 2018.02.13

---

#### Introduce data type.

---

<br>

## <a name="DataType">Protocol::DataType::Type</a>
Data type

```cpp
namespace Protocol
{
    namespace DataType
    {
        enum Type
        {
            None = 0,                   // none

            // System information
            Ping,                       // ping device(reserved)
            Ack,                        // Response to data receive
            Error,                      // error(reserved)
            Request,                    // Request data of the specified type
            
            // Control, Command
            Control = 0x10,             // Control
            Command,                    // Command
            Command2,                   // Multiple Command(double command)
            Command3,                   // Multiple Command(triple command)
            
            // LED
            LightMode = 0x20,           // LED mode
            LightMode2,                 // LED mode x2
            LightModeCommand,           // LED mode, Command
            LightModeCommandIr,         // LED mode, Command, IR data
            LightModeColor,             // LED mode 3 colors
            LightModeColor2,            // LED mode 3 colors x2
            
            LightEvent,                 // LED event
            LightEvent2,                // LED event x2 
            LightEventCommand,          // LED event, Command
            LightEventCommandIr,        // LED event, Command, IR data
            LightEventColor,            // LED event 3 colors
            LightEventColor2,           // LED event 3 colors x2
            
            LightModeDefaultColor,      // LED mode default 3 color.
            LightModeDefaultColor2,     // LED mode default 3 color x2
            
            // State 
            Address = 0x30,             // Device address
            State,                      // Drone state (Vehicle mode, Coordinate, battery)
            Attitude,                   // Drone attitude(Vector)
            GyroBias,                   // Drone gyro bias(Vector)
            TrimAll,                    // Drone trim all
            TrimFlight,                 // Drone trim flight
            TrimDrive,                  // Drone trim drive
            
            CountFlight,                // count of flight
            CountDrive,                 // count of drive
            
            // IR Data transmission
            IrMessage = 0x40,           // IR data send & recieve
            
            // Sensor control
            ImuRawAndAngle = 0x50,      // IMU Raw + Angle
            Pressure,                   // Pressure sensor
            ImageFlow,                  // ImageFlow
            Button,                     // Button command
            Battery,                    // Battery
            Motor,                      // Motor control and check current value 
            Temperature,                // Temperature sensor
            Range,                      // Range sensor
        
            // Firmware update
            UpdateLookupTarget = 0x90,	// Update device lookup
            UpdateInformation,          // Update information
            Update,                     // Update ( block size 16 )
            UpdateLocationCorrect,      // Update location correct
            
            EndOfType
        };
    }
}
```


<br>

---

### PETRONE

1. [Intro](01_intro.md)
2. [Typedef](02_typedef.md)
3. ***DataType***
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

