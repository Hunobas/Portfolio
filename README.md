# 박태훈 | 게임 클라이언트 프로그래머

> 1998년생, 군필 (의경 만기제대)
> 
> 📧 hunobas.dev@gmail.com
>
>> Unreal Engine 5로 뱀서라이크 프로토타입을 3주간 빈 템플릿에서 아키텍처 설계부터 완성한 경험이 있습니다.
>> 데이터 기반 설계에 관심이 크며, 기획자가 코드 수정 없이 콘텐츠를 확장할 수 있는 구조를 만들 때 가장 큰 보람을 느낍니다.

---

## 니오스트림인터랙티브 지원동기

Little Devil Inside의 트레일러에서 가장 인상적이었던 건 **자유로운 탐험과 예측 불가능한 상황의 연속**이었습니다. 낚시하다 갑자기 몬스터에게 습격당하고, 황무지에서 모닥불을 피우며 밤을 지새우는 장면들은 "게임 같은 게임"이라는 컨셉이 무엇인지 직관적으로 보여줬습니다.

저는 God of War: Ragnarök와 Monster Hunter 시리즈를 깊이 플레이하며 액션 어드벤처 장르의 전투 리듬과 탐험 루프를 체득했습니다. 특히 **다양한 상황에서 플레이어가 선택할 수 있는 자유도**가 게임의 몰입감을 결정한다고 느꼈고, 이를 뒷받침하는 시스템 구조에 자연스럽게 관심을 갖게 되었습니다.

개인 Unreal 프로젝트에서 **시간 기반 행동 전환 시스템**과 **요일별 아이템 활성화 시스템**을 설계하며, 플레이어 선택이 게임플레이에 실질적 영향을 주는 구조를 고민했습니다. 이런 경험이 Little Devil Inside의 높은 자유도와 다양한 플레이 흐름을 수용하는 시스템 설계에 기여할 수 있으리라 생각합니다.

---

## 핵심 역량

### 1. FSM 기반 플레이 모드 설계

<img width="1020" height="458" alt="FSM 구조도" src="https://github.com/user-attachments/assets/d0b930d5-8c1a-4120-8fbd-e9b4ee1dfc44" />

**목성의 노래** — Unity 기반 1인칭 퍼즐 어드벤처 (팀 프로젝트, 5명)

재활용되는 4가지 주요 플레이 모드(Normal/Panel/Cinema/Pause)가 중첩되어 조작 불가 버그가 발생하는 문제를 해결했습니다.
게임 흐름 중간에 미니 게임 모드가 있어 추가적인 플레이 모드가 요구되어도 빠르게 확장할 수 있는 구조를 설계했습니다.

**해결 방식**: 중앙 집중식 FSM으로 모드 전환을 단일 책임 관리
```csharp
public void ChangePlayMode(IPlayMode next)
{
    // 시네마 모드 진행 중에는 일시정지 외 다른 모드 전환 무시
    if (IsPlayingCinema && !ReferenceEquals(next, PauseMode))
        return;
    
    var prev = _activeMode;
    prev?.OnExit(next);  // 이전 모드 정리
    _activeMode = next;
    _activeMode.OnEnter(prev);
}
```

| 개선 항목 | Before | After |
|---------|--------|-------|
| 상태 충돌 버그 | 주 2~3건 | 0건 |
| 신규 모드 추가 | - | IPlayMode 구현만으로 20분 내 완료 |

- [GameState 전체 코드](https://github.com/Hunobas/Song-Of-Jupitor/blob/7386ab978fc3115a13a700758c7a618567bc168a/Scripts/System/GameState.cs#L15)

---

### 2. 팀 협업 & 문서화

**My Little Puppy** — 드림모션 인턴 3개월 (38명 규모, Steam 데모 출시)

루트모션 관련 버그 3건을 해결하며 **캐릭터 트랜스폼 수정 컨벤션**을 제안했습니다.

| 버그 유형 | 원인 | 해결 |
|----------|------|------|
| 루트모션 회전 불일치 | 외부 보간 로직과 루트모션 중복 적용 | 루트모션 전용 업데이트 메서드 분리 |
| 상태 전환 시 위치 튐 | Walk→Idle 전환 시 속도값 미초기화 | 상태머신 종료 시점에 블렌딩 속도 리셋 |
| 컷씬 일시정지 위치 오류 | 일시정지 모드에서 LateUpdate 처리 누락 | 이전 모드 체크 후 HandleGameActors 호출 |

- [경력기술서 상세](https://ethereal-judo-1f1.notion.site/My-Little-Puppy-1c6486e2cdb980fcbc33f487a01bd7fc)

---

### 3. Unreal Engine 5 시스템 아키텍처

![PlayDemoGIF](https://github.com/user-attachments/assets/9257c9b1-f15a-492e-9788-a3118e2ce21c)

**TOGU: Planet Survivors** — UE 5.4 기반 로그라이크 탑다운 슈팅 (개인 프로젝트, 3주)

| 시스템 | 구현 내용 |
|--------|----------|
| 오브젝트 풀링 | TCircularQueue 기반, FCriticalSection으로 Thread-safe 처리. GC 호출 빈도 80% 감소 |
| 보상 시스템 | MVC 패턴 + 인터페이스 기반 3단계 책임 분리 (Selector → Manager → Applicator) |
| 데이터 드리븐 | UDataAsset 기반 캐릭터/적/웨이브 스탯. 기획자가 코드 수정 없이 밸런싱 가능 |

- [GitHub](https://github.com/Hunobas/Planet) ・ [데모 영상](https://youtu.be/1-GPB7u94ic)
- [신규 무기/아이템 추가 가이드](https://ethereal-judo-1f1.notion.site/223486e2cdb980c5a807f920ebad70a6) ・ [신규 몬스터 추가 가이드](https://ethereal-judo-1f1.notion.site/223486e2cdb98001869cef28bb9bfbb5)

<details>
<summary><b>주요 코드 링크</b></summary>

- [ObjectPoolManager - Thread-safe 풀 관리](https://github.com/Hunobas/Planet/blob/9abc29b52a75614a9ff8170548ae4311105b9b2b/Source/Planet/System/ObjectPoolManagerComponent.h#L34)
- [RewardManager - MVC Controller](https://github.com/Hunobas/Planet/blob/9abc29b52a75614a9ff8170548ae4311105b9b2b/Source/Planet/System/Reward/Manager/RewardManager.h#L19)
- [IRewardApplicator - 확장 인터페이스](https://github.com/Hunobas/Planet/blob/main/Source/Planet/System/Reward/Applicator/IRewardApplicator.h#L12)

</details>

---

## CS 기초

크래프톤 정글 6개월 합숙 과정에서 저수준 시스템 프로그래밍을 경험했습니다.

[![Solved.ac 뱃지](http://mazassumnida.wtf/api/v2/generate_badge?boj=po1279)](https://solved.ac/po1279)

- [RB트리 구현](https://github.com/Hunobas/rbtree-lab) — 삽입/삭제 케이스별 시각화 디버깅 프레임 제작
- [malloc 구현](https://github.com/Hunobas/malloc-lab) — Segregated Free List 방식
- [PintOS 커널](https://github.com/sjlim32/4-5-team5-pintos-project3/tree/Week10/Hunobas) — 테스트 137/141 통과 (96.4%)

---

## 프로젝트 요약

| 프로젝트 | 엔진 | 기간 | 규모 | 역할 |
|----------|------|------|------|------|
| [TOGU: Planet Survivors](https://github.com/Hunobas/Planet) | UE 5.4 | 2025.04~06 | 1명 | 전체 아키텍처 설계 및 구현 |
| [목성의 노래](https://github.com/Hunobas/Song-Of-Jupitor) | Unity | 2025.06~2026.01 | 5명 | FSM, 렌더링 최적화, 퍼즐 로직 |
| [My Little Puppy](https://ethereal-judo-1f1.notion.site/My-Little-Puppy-1c6486e2cdb980fcbc33f487a01bd7fc) | Unity | 2025.01~03 | 38명 | 루트모션 버그 수정, 에디터 확장 |

---

## Contact

- 📞 010-3702-1279
- 📧 hunobas.dev@gmail.com
- 📝 [Velog](https://velog.io/@po127992/posts)
- 💻 [GitHub](https://github.com/hunobas)
