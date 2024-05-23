**[*petrone* for python](index.md)** / **Intro**

Modified : 2018.02.13

---

* Kramdown table of contents
{:toc .toc}


<br>

# 1. Introduce *petrone* for python 

***petrone* for python** is a library that helps you easily use ***PETRONE*** through the ***PETRONE LINK*** in Python.

[https://pypi.python.org/pypi/petrone](https://pypi.python.org/pypi/petrone)


<br>
<br>


# 2. Install

The command below will install *petrone*.

```
> pip install petrone
```

<br>

If the latest version is not installed, please use the command below :

```
> pip --no-cache-dir install petrone
```


<br>
<br>


# 3. Uninstall

The command below will uninstall *petrone*.

```
> pip uninstall petrone
```


<br>
<br>


# 4. Scan serial port

Connect to the serial port using a pyserial in Drone class. You must know the device name to connect to the serial port. What you need at this point is a command to search serial communications devices connected to your computer. This command is provided by **pyserial**.

(**ㅔyserial** is installed with *petrone*)

<br>

The following code identifies the names of serial communication devices connected to your computer.

```py
from serial.tools.list_ports import comports

for port, desc, hwid in sorted(comports()):
    print("%s" % (port))
```

<br>

Please execute this code to learn more information the device.

```py
from serial.tools.list_ports import comports

nodes = comports()

count = 0;
for node in nodes:
    print("[{0}]".format(count))
    print("         device: ", node.device)
    print("    description: ", node.description)
    print("   manufacturer: ", node.manufacturer)
    print("           hwid: ", node.hwid)
    print("      interface: ", node.interface)
    print("       location: ", node.location)
    print("           name: ", node.name)
    count += 1
```


<br>
<br>


# 5. Application project example

The following is an example of an application project :

The typical progress is : '**Allocate Drone object**' -> '**Open serial port**' -> '**Scan PETRONE**' ->  '**Connect to PETRONE**' -> '**Use PETRONE**' ->  '**Disconnect PETRONE**' ->  '**Close serial port**'

```py
from time import sleep

from petrone.drone import *
from petrone.protocol import *
from petrone.system import *


def eventUpdateInformation(data):
    print("eventUpdateInformation() / {0} / {1} / {2} / Ver:{3} / 20{4:02}.{5}.{6}".format(data.modeUpdate, data.deviceType, data.imageType, data.version, data.year, data.month, data.day))


if __name__ == '__main__':
    
    # Create Drone object
    drone = Drone(True, True, True, True, True)

    # Regist event handler
    drone.setEventHandler(DataType.UpdateInformation, eventUpdateInformation)

    # connect device.
    drone.connect()    # Connect to the device with the strongest signal, the last connected serial port or detected device (PETRONE).
    #drone.connect(portName="COM14", deviceName="PETRONE 6504")      # Specifies and connects serial ports and devices (PETRONE)
    sleep(1)
    
    # Request information when connected to a device
    if drone.isConnected():

        # Request device main firmware information
        print("Request information of main firmware.")
        drone.sendUpdateLookupTarget(DeviceType.DroneMain)
        sleep(2)

        # Request device sub firmware information
        print("Request information of sub firmware.")
        drone.sendUpdateLookupTarget(DeviceType.DroneSub)
        sleep(2)

        # Disconnect from device.
        print("Disconnect device.")
        drone.sendLinkDisconnect()
        sleep(0.2)

    drone.close()
```

<br>

The results of the execute are like this :

```py
[     0.012] Connected.(COM40)]
0A 55 11 02 E0 03 A2 23
0A 55 11 02 E2 00 A3 75
0A 55 E1 02 04 00 FA 50
[     0.220] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x50FA]
[     0.220] EventLink.ScanStop]
0A 55 E4 1C 00 A8 B5 60 78 D5 A4 50 45 54 52 4F 4E 45 20 36 35 30 34 00 00 00 00 00 00 00 00 D6 CF 54
[     0.283] Success / Receiver / Section.End / Receive complete / DataType.LinkDiscoveredDevice / [receive: 0x54CF]
[     0.283] LinkDiscoveredDevice / 0 / A8 B5 60 78 D5 A4  / PETRONE 6504 / -42]
0A 55 E1 02 04 00 FA 50
[     1.825] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x50FA]
[     1.825] EventLink.ScanStop]
0A 55 11 02 E4 00 05 DF
0A 55 E2 08 07 00 A8 B5 60 78 D5 A4 8A 49
[     2.436] Success / Receiver / Section.End / Receive complete / DataType.LinkEventAddress / [receive: 0x498A]
[     2.436] EventLink.Connected]
0A 55 E1 02 18 00 E4 16
[     3.400] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x16E4]
[     3.401] EventLink.ReadyToControl]
Request information of main firmware.
0A 55 90 04 01 00 00 00 16 31
0A 55 91 0B 01 01 00 00 00 01 27 00 11 06 08 71 3A
[     4.754] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0x3A71]
eventUpdateInformation() / ModeUpdate.Ready / DeviceType.DroneMain / ImageType.ImageA / Ver:39 / 2017.6.8
Request information of sub firmware.
0A 55 90 04 02 00 00 00 CA AA
0A 55 91 0B 01 02 00 00 00 01 12 00 10 07 0E C0 C0
[     6.752] Success / Receiver / Section.End / Receive complete / DataType.UpdateInformation / [receive: 0xC0C0]
eventUpdateInformation() / ModeUpdate.Ready / DeviceType.DroneSub / ImageType.ImageA / Ver:18 / 2016.7.14
Disconnect device.
0A 55 11 02 E5 00 34 EC
0A 55 E1 02 1A 16 71 02
[     8.752] Success / Receiver / Section.End / Receive complete / DataType.LinkEvent / [receive: 0x0271]
[     8.752] EventLink.Disconnected]
[     8.923] Closing serial port.]
```


<br>

---

<h3><i>petrone</i> for python</H3>

 1. **Intro**
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)

<br>

[Index](index.md)
