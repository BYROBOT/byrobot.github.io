**[*petrone* for python](index.md)** / **Examples** / **Test Flight**

Modified : 2018.11.26

---

* Kramdown table of contents
{:toc .toc}


<br>


<a name="test_flight"></a>
## 테스트 비행 실행

테스트 비행을 실행합니다.

```py
from time import sleep

from petrone.drone import *
from petrone.protocol import *
from petrone.system import *

if __name__ == '__main__':
    
    # Drone의 객체 생성
    drone = Drone(True, True, True, True, True)

    # 장치에 연결
    drone.connect()
    sleep(2)
    
    # 장치에 연결된 경우
    if drone.isConnected():

        drone.sendStartTestFlight();
        sleep(3)

        # 장치 연결 해제
        print("Disconnect device.")
        drone.sendLinkDisconnect()
        sleep(0.2)

    drone.close()
```

<br>

실행 결과는 다음과 같습니다.


<div align="center">
    <img src="../examples_03_test_flight_ex1.jpg" alt="example1 result">
    <p>테스트 비행</p>
</div>



<br>


---

<h3><i>petrone</i> for python</H3>

 1. [Intro](01_intro.md)
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Information](examples_01_information.md)
 6. [Examples - Imu](examples_02_imu.md)
 7. **Examples - Test Flight**
 8. [Examples - Light](examples_04_light.md)

<br>

[Index](index.md)
