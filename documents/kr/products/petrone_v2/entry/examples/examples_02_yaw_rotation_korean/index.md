**[*petrone_v2* for entry](../index.md)** / **Examples** / **Yaw rotation(Korean)**

Modified : 2017.10.30

---

<br>


## <a name="Yaw rotation(Korean)">Yaw rotation(Korean)</a>

Petrone V2의 **Gyroscope sensor**를 이용하여 원하는 **각도와 속도**만큼 드론을 제어하는 예제입니다.

원하는 각도와 회전속도 값을 입력받아야 하므로 함수를 사용했습니다.

정확한 제어를 위해서 변수와 조건문이 다소 사용되어 복잡하게 느껴질 수 있습니다.

따라서 전체 블럭을 먼저 보여드린 후, 세부적인 설명을 아래 추가하겠습니다.

<br>

<div align="left">
    <img src="petrone_v2_function_yaw_rotation_korean.png" alt="petrone_v2_function_yaw_rotation_korean">
</div>


<br>
<br>


## <a name="변수 설명">변수 설명</a>

이번 예제에서 사용된 변수들을 설명하겠습니다.

| 변수 이름      | 범위       | 설명                                                   |
|:-------------:|:----------:|:-------------------------------------------------------|
| currentYaw    | -180 ~ 180 | 출발 지점의 '각도(자세Yaw)'값을 저장하는데 사용됩니다.     |
| rotation      | -          | 자세Yaw 값이 180도 이상을(혹은 -180도 이하를) 넘어가는 경우에 계산하기 위해 사용됩니다. |
| target        | -          | 입력받은 값. 원하는 회전 각도입니다.                      |
| speed         | -          | 입력받은 값. 원하는 회전 속도입니다.                      |
| Kp            | 1          | P제어(비례제어)의 매개변수입니다. 이번 예제에서는 1로 고정했습니다.  |
| flag          | 0 ~ 2      | rotation 값을 정확히 계산하기 위해서 사용됩니다.            |
| entryYaw      | -          | 실제 회전한 각도입니다. (자세Yaw - currentYaw + rotation)  |
| error         | -          | 목표 각도까지 남은 값입니다. 더 회전해야하는 각도입니다.     |


<br>
<br>


## <a name="flag">flag</a>

flag는 rotation 값을 정확히 계산하기 위해서 사용됩니다. 이러한 계산을 하는 이유는 드론이 실제 회전한 각도를 정확히 알기 위해서입니다.

시계 방향 회전의 경우를 먼저 설명하겠습니다.

Petrone V2의 자세Yaw 값은 -180도에서 180도까지의 범위를 가집니다. 따라서 181도라는 자세Yaw 값은 없으며, -179도라고 표시됩니다.

이런 경우에 rotation이라는 변수를 사용하여 360도를 더해준다면, (-179 + 360 = 181) 우리가 얻고자 하는 값을 구할 수 있습니다.

(엔트리 화면 좌측 하단에 있는 하드웨어 센서 창입니다. 이 부분을 확인하면서 보시면 도움이 될 것입니다.)

<div align="left">
    <img src="entry_hardware_sensor_display_korean.jpg" alt="entry_hardware_sensor_display_korean">
</div>

<br>

결국 자세Yaw 값이 180도를 넘는 순간 (-) 값을 가지므로 360도를 더해줘야 하지만, 주의할 사항이 있습니다.

목표 각도까지 회전하기 위해서 '계속 반복하기'라는 반복문(무한루프)를 사용하고 있다는 점입니다.

'자세Yaw 값이 (-)일 때 360도를 더하라'라는 블럭을 만든다면 반복할 때마다 360도를 계속 더하게 될 것입니다.

그래서 flag 변수를 사용하여 360도라는 값을 한 번만 더하게 만들었습니다.

<div align="left">
    <img src="flag_clockwise_rotation_korean.jpg" alt="flag_clockwise_rotation_korean">
</div>

<br>

그리고 중요한 사항이 하나 더 있습니다. 코딩에서 변수를 사용할 때 중요한 부분 중 하나는 '변수의 초기화' 입니다.

그래서 전체 블럭의 맨 윗부분을 보시면 이러한 블럭들이 있습니다. 만약 이 부분이 없다면 경우에 따라서 오작동이 일어나게 됩니다.

<div align="left">
    <img src="flag_init_korean.jpg" alt="flag_init_korean">
</div>

<br>

지금까지 시계 방향 회전의 경우를 알아보았습니다. flag와 관련된 부분을 처음 접해보셨다면 꽤 어렵게 느껴질 수 있습니다. 

그런 점이 단점이라면 반대로 장점도 있겠죠? flag의 장점은 바로 강력한 기능성입니다.

앞으로 살펴볼 시계 반대 방향 회전의 경우에도 flag가 똑같이 사용됩니다. 시계 방향 회전에서 확실히 이해하셨다면 이번에는 쉽게 느껴질 것입니다.

<br>

다음은 시계 반대 방향 회전의 경우입니다.


<br>

---

<h3><i>petrone_v2</i> for entry</H3>

 1. [Examples - Bottom range(Korean)](../examples_01_bottom_range_korean/)
 2. [Examples - Bottom range(English)](../examples_01_bottom_range_english/)
 3. **Examples - Yaw rotation(Korean)**
 4. [Examples - Yaw rotation(English)](../examples_02_yaw_rotation_english/)

<br>

[Index](../index.md)
