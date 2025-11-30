# 🙋 박태훈 포트폴리오

> 박태훈(Park Taehoon) - 게임 클라이언트 개발 포트폴리오
> <br />  1998년생, 군필 (의경 만기제대)

<br />

# 👨🏻‍💻 About me

**기획자가 코드 수정 없이 밸런싱할 수 있는 구조**를 만드는 개발자입니다.

- **Unreal 5.4** 뱀파이어 서바이버 시스템을 2주 만에 아키텍처부터 설계
  - 오브젝트 풀링으로 GC 호출 **80% 감소** 달성
  - `DataAsset` 기반 설계로 기획자 독립 작업 가능한 구조 구축

- **Unity** 14개 언어 지원 폰트 시스템 설계
  - `ScriptableObject` 기반 원클릭 폰트 머티리얼 생성
  - 언어 변경 시 전체 UI 동적 교체 시스템 구현

- **상용 게임 출시 경험** (Dreamotion 인턴십)
  - 알파 테스트부터 데모 출시까지 전체 파이프라인 경험
  - QA 15회, 버그 리포트 103건 처리

<br />

# 📝 Projects
6개월동안 _PAGE25_ 팀에서 인디 게임 **목성의 노래**의 서브 프로그래머를 맡아 Unity 작업을 수행했습니다.
<br /> 또한, 3개월동안 크래프톤 산하의 게임업체 _Dreamotion_ 에서 **My Little Puppy**의 클라이언트 개발을 보조하며 인턴십을 수행했습니다.

## 1. 🪐목성의 노래 | _PAGE25_

<img width="1182" height="658" alt="그림4" src="https://github.com/user-attachments/assets/b1f7e2f7-c323-4cc9-83a8-179168f10707" />

> 내러티브 1인칭 3D 퍼즐 게임
> 개발기간 : 2025.07.01 ~ 2025.11.25
> 
> **📊 핵심 성과**
> - FSM 기반 플레이 모드 구분으로 **상태 충돌 버그 제거**
> - 패널 가상 커서 시스템으로 인게임 크로스헤어와 **분리된 UI 조작** 구현
> - 이벤트 그래프의 커스텀 노드 확장으로 **다중 파라미터 메서드 호출** 지원

> **🛠 기술적 도전**
> - [**ASCII 아트 렌더러 플러그인**](https://github.com/Hunobas/AsciiImageUGUI-UPM) 개발
>   - CPU 점유 **92% 감소**, 프레임 내 비중 **95% 감소**
>   - AsyncGPUReadback 기반 + 색 구간 12bit 양자화로 CPU 점유율 최적화 경험
> 
> [프로젝트 상세 설명](https://github.com/Hunobas/Song-Of-Jupitor)

<br />

## 2. 🌏 TOGU : Planet Survivors | _개인 프로젝트_

<img width="1663" height="833" alt="image" src="https://github.com/user-attachments/assets/d69b7157-1993-49a6-938b-400d243f0c00" />

> 3D 탑다운 로그라이크 슈팅 게임
> 개발기간 : 2025.04.15 ~ 2025.07.01
>
> **📊 핵심 성과**
> - 커스텀 오브젝트 풀링으로 **GC 호출 빈도 80% 감소**
> - 기획자 친화적 `DataAsset` 설계로 **코드 수정 없이 무기/몬스터 추가 가능**
> - 마우스 회전 기반 요일 변화 시스템으로 차별화된 게임플레이 구현
>
> **🛠 기술적 도전**
> - 모듈형 리워드 시스템: 3단계 책임 분리 + 인터페이스 다형성
> - 전략 패턴 기반 AI: 유니크 포인터로 런타임 전략 교체
> - Data-Driven 설계: `FRuntimeFloatCurve` 기반 웨이브 난이도 실시간 조절
>
> [프로젝트 상세 설명](https://github.com/Hunobas/Planet)

<br />

## 3. 🐶 My Little Puppy | _Dreamotion_

![그림5](https://github.com/user-attachments/assets/2282e694-733e-4fde-b230-28a5b101ba55)

> 내러티브 3인칭 3D 어드벤처 게임
> 개발기간 : 2025.01.02 ~ 2025.03.31
> 
> **📊 핵심 성과**
> - 14개 언어 지원 시스템 구축 → **언어 관련 버그 0건**으로 데모 출시
> - FPS 히트맵 자동 생성기로 **QA 병목 구간 시각화**
> - QA 15회, 버그/폴리싱 103건 제출
>
> **🛠 기술적 기여**
> - ScriptableObject 기반 폰트 머티리얼 관리 시스템
> - 언어 변경 시 전체 UI Layer 폰트 일괄 교체
> - 유럽권 특수 구분자 파싱 오류 해결
>
> [프로젝트 상세 설명](https://ethereal-judo-1f1.notion.site/My-Little-Puppy-1c6486e2cdb980fcbc33f487a01bd7fc)

<br />

## 4. 🐁 THE RATTUS | _크래프톤 정글 부트캠프_

<img width="1042" height="587" alt="image" src="https://github.com/user-attachments/assets/8ea2a253-b519-4eda-ae3d-5767059cb9c1" />

> 웹기반 2인 협동 시뮬레이션 게임
> 개발기간 : 2024.04.18 ~ 2024.5.25
> 
> - **핵심 역할** : 백엔드 테크 리드 역할을 맡으며 웹기반 게임의 리버스 프록시 아키텍처를 설계하고, 모션 캡처 라이브러리 연동 및 데디케이트 서버를 구현했습니다.
> - **Language** : Typescript, Python, NGINX
> - **Skill** : React, nestJS, flask, NGINX, AWS
>
> [프로젝트 상세 설명](https://github.com/younggun339/jungleTwo)

<br />
<br />

# 📞 Contact

- 이메일 : hunobas.dev@gmail.com
- 블로그 : <a href="https://velog.io/@po127992/posts">
  <img src="https://user-images.githubusercontent.com/68724828/185885678-8f619bfa-1160-4bb4-a026-f758a4014f82.png" height="26px" style="margin-top: 10px" />
  </a>
- 깃허브 : <a href="https://github.com/hunobas">
  <img src="https://user-images.githubusercontent.com/68724828/185908612-22f4d219-78a7-4de7-bb02-deecaa63bffa.png" height="28px" style="margin-top: 10px" />
  </a>
