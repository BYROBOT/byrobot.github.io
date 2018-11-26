**[*petrone* for python](index.md)** / **Examples** / **Light**

Modified : 2018.11.26

---

* Kramdown table of contents
{:toc .toc}


<br>


<a name="light_test"></a>
## LED 동작 확인

드론의 LED를 작동해봅니다.

```py
from time import sleep

from petrone.drone import *
from petrone.protocol import *
from petrone.system import *


if __name__ == '__main__':
    
    # Drone의 객체 생성
    drone = Drone(True, True, True, True, True)

    # 장치에 연결
    drone.connect(flagSystemReset=True)
    sleep(5)
    
    # 장치에 연결된 경우
    if drone.isConnected():


        drone.sendLightModeColor(LightModeDrone.ArmHold, 250, 0, 0, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmHold, 0, 250, 0, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmHold, 0, 0, 250, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmHold, 0, 250, 250, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmHold, 250, 0, 250, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmHold, 250, 250, 0, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmHold, 250, 250, 250, 255);
        sleep(2)


        drone.sendLightModeColor(LightModeDrone.ArmDimming, 250, 0, 0, 12);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmDimming, 0, 250, 0, 12);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmDimming, 0, 0, 250, 12);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmDimming, 0, 250, 250, 12);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmDimming, 250, 0, 250, 12);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmDimming, 250, 250, 0, 12);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmDimming, 250, 250, 250, 12);
        sleep(2)


        drone.sendLightModeColor(LightModeDrone.ArmFlicker, 250, 0, 0, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmFlicker, 0, 250, 0, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmFlicker, 0, 0, 250, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmFlicker, 0, 250, 250, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmFlicker, 250, 0, 250, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmFlicker, 250, 250, 0, 255);
        sleep(2)

        drone.sendLightModeColor(LightModeDrone.ArmFlicker, 250, 250, 250, 255);
        sleep(2)

        # 장치 연결 해제
        print("Disconnect device.")
        drone.sendLinkDisconnect()
        sleep(0.2)

    drone.close()
```

<br>


---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)
 6. [Examples - Imu](examples_02_imu.md)
 7. [Examples - Test Flight](examples_03_test_flight.md)
 8. **Examples - Light**

<br>

[Index](index.md)
