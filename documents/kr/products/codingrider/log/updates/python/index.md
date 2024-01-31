**[E-DRONE](/documents/kr/products/e_drone/) update log**

Modified : 2022.1.4

---

* Kramdown table of contents
{:toc .toc}


<br>


# 2022.1.4

- **e_drone: 22.1.17**

> - 파이썬 명명 규칙에 맞추어 정의, 함수 이름 전체를 수정함(대표적인 변경 사항으로 함수와 변수 이름은 카멜 케이스에서 소문자만 사용한 스네이크 케이스로, enum 항목은 모두 대문자 + 언더바 형태로 변경)
> - 커맨드라인 명령, 설명 수정
> - 조종기, 드론 모두에 사용하거나 사용할 것으로 예상되는 명령은 모두 DeviceType 값을 받도록 변경함
> - e_drone 소스 코드 저장소를 github으로 이전( https://github.com/byrobot-python/e_drone )
> - dev 파이썬 문서의 예제를 쉽게 실행해볼 수 있도록 e_drone_examples 소스 코드 저장소를 github에 추가함 ( https://github.com/byrobot-python/e_drone_examples )
> - Flow 센서 데이터에 대한 정의 추가


<br>

---

# 2021.1.5

- **e_drone: 21.1.6**

> - 커맨드라인 명령, 설명 수정
> - 커맨드라인 명령에 이륙, 착륙, 정지 추가
> - install_requires에서 numpy 참조 제거


<br>

---

# 2020.9.3

- **e_drone: 20.9.1**

> - 커맨드라인 설명 수정


<br>

---

# 2020.7.29

- **e_drone: 20.7.6**

> - 라이브러리 버전을 Year.Month.BuildNumber 형식으로 변경
> - 커맨드라인 명령 추가
> - 'python -m e_drone' 실행 시 커맨드라인 명령 표시함
> - sendClearTrim() 명령 복원


<br>

---

# 2020.1.29

- **e_drone: 0.1.33**

> - sendLightDefaultColor 함수 추가 (XTS-65는 이 함수로만 LED 색 변경 가능)


<br>

---

# 2020.1.21

- **e_drone: 0.1.32**

> - time.clock() 함수가 파이썬 3.8부터 제거됨. perf_counter()로 대체


<br>

---

# 2019.3.13

- **e_drone: 0.1.31**

> - 펌웨어 업그레이드 출력 화면 배색 및 배치 수정


<br>

---

<br>
