# 📅 2025-04-07

## 🔍 오늘 학습한 내용
회사 프로젝트 코드 리팩토링을 하려는데 코드가 고치기 힘들어 보였음. 1년 전에도 고민한 **'매개변수로 어떤 것을 받을까?', '이벤트로 처리할까? 직접 객체의 함수를 호출할까?'** 를 생각하는 나의 모습을 봄.  

최근 NestJS를 공부하면서 NestJS 프레임워크를 잘 사용하려면 의존성 주입을 이해해야 함을 느낌. 유니티에서도 의존성 방향을 제어할 수 있을지 궁금했고 의존성 제어가 내가 고민하던 내용의 핵심이 될 거라 생각하여  ChatGPT와 잠시 이야기해 봤음.

---
### Dependency Flow
- 안정된 것 -> 불안정한 것 / 추상 -> 구체의 방향으로 흘러야 함  
  (ex) Controller -> UI  
1. [Unity 개발하면서 의존성 방향이 깨지는 경우]  
    - 싱글톤 사용  
    - SerializeField로 직접 참조
    - Getter로 중간 클래스를 통해 객체 얻기
2. [의존성을 지키는 방법]
    - 인터페이스로 추상화  
        ```
        interface IAudioPlayer {
            void PlaySound(string id);
        }
        // GameLogic → IAudioPlayer ← AudioController 구현체
        ```
    - 이벤트
        ```
        // UI
        public UnityEvent OnButtonClicked;

        // Controller
        someButton.OnButtonClicked.AddListener(HandleGameStart);
        ```
    - DI (Dependency Injection)
## 💡 핵심 포인트 / 깨달은 점
- 어떤 함수를 public으로 할지 등 인터페이스 설계는 해당 클래스가 **'추상'인지, '구체'인지 즉, 계층을 먼저 알아야 함.**   
그리고 함수가 '추상'인데 '구체' 클래스에 맞춰서 함수를 작성하면 의존성이 강해져서 해당 함수는 '구체'클래스만을 위한 함수가 됨.

## ❓ 찝찝한 점 / 더 알아보고 싶은 것
- World 클래스의 위치
- 역할, UI와 상호작용하는 방법
- Skill 클래스는 World와 어느 정도 상호작용해야할까?
- 자주하는 실수가 의존성 흐름과 아직 연결되지 않았음 (한 번 더 고민해야 함)
