**[*e_drone* for rust](index.md)** / **Intro**

Modified : 2018.8.8

---

* Kramdown table of contents
{:toc .toc}

<br>


# 시작하기 전에

아직 Rust을 설치하지 않으셨다면 다음 문서를 먼저 확인하시기 바랍니다.

[Rust 설치](https://www.rust-lang.org/ko-KR/install.html)


<br>
<br>


# 1. *e_drone* for rust 소개

***e_drone* for rust**는 rust에서 ***E-DRONE***을 쉽게 사용할 수 있도록 도와주는 라이브러리입니다.

[https://crates.io/crates/e_drone](https://crates.io/crates/e_drone)


<br>
<br>


# 2. Cargo를 사용한 프로젝트 생성

Cargo를 사용한 프로젝트 시작부터 설명합니다.

rust 테스트 프로젝트를 생성할 폴더에서 *명령 프롬프트* 또는 *Power Shell*을 연 다음, 아래의 명령을 입력하면 *test0*이라는 프로젝트가 생성됩니다.

```
> cargo new test0 --bin
```


<br>
<br>


# 3. 의존성 추가

생성한 프로젝트 폴더로 이도앟면 *Cargo.toml* 파일이 있습니다. 이 파일을 텍스트 편집기로 열어서 아래와 같이 e_drone 라이브러리에 대한 의존성을 추가합니다. 뒤의 숫자는 버젼입니다. 처음 시작하시는 분이라면 최신 버젼을 사용하시기 바랍니다.

```toml
> [dependencies]
> e_drone = "1.0.0"
```


<br>
<br>


# 4. 빌드 및 실행

아래의 명령을 실행하면 프로젝트를 빌드하고 생성된 실행 파일을 실행합니다.

```
> cargo run
```

빌드만 하시려면 아래의 명령을 실행하시기 바랍니다.

```
> cargo build
```


<br>
<br>


# 4. 시리얼 포트 검색


Drone 클래스 내부에서 *serialport*를 사용하여 시리얼 포트에 연결합니다. 시리얼 포트에 연결하려면 장치 이름을 알고 있어야 합니다. 이 때 필요한 것이 컴퓨터에 연결된 시리얼 통신 장치들을 검색할 수 있는 명령입니다. 이 명령은 **serialport**에서 제공하고 있습니다.

<br>

새로운 테스트 프로젝트를 만들고 *Cargo.toml* 파일에 *serialport*에 대한 의존성을 추가합니다.

```toml
[dependencies]
serialport = "*"
```

<br>

장치에 대한 상세한 정보를 확인하려면 아래의 코드를 실행해보시기 바랍니다.

```rust
extern crate serialport;

fn main()
{
    if let Ok(ports) = serialport::available_ports()
    {
        match ports.len()
        {
            0 => println!("No ports found."),
            1 => println!("Found 1 port:"),
            n => println!("Found {} ports:", n),
        };
        
        for p in ports
        {
            println!("  {0} / {1:?}", p.port_name, p.port_type);
        }
    }
    else
    {
        print!("Error listing serial ports");
    }
}
```


<br>

---

<h3><i>e_drone</i> for rust</H3>

 1. **Intro**
 2. [System](02_system.md)
 3. [Protocol](03_protocol.md)
 4. [Drone](04_drone.md)
 5. [Examples - Ping](examples_01_ping.md)
 6. [Examples - Information](examples_02_information.md)
 7. [Examples - Pairing](examples_03_pairing.md)
 8. [Examples - Control](examples_04_control.md)
 9. [Examples - Sensor](examples_05_sensor.md)
10. [Examples - Motor](examples_06_motor.md)
11. [Examples - Setup](examples_07_setup.md)
12. [Examples - Buzzer](examples_08_buzzer.md)
13. [Examples - Vibrator](examples_09_vibrator.md)
14. [Examples - Light](examples_10_light.md)
15. [Examples - Display](examples_11_display.md)
16. [Examples - Input](examples_12_input.md)
17. [Examples - Error](examples_13_error.md)

<br>

[Index](index.md)
