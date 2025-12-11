# Welcome to Delivery Lab Organization!

## Git Flow Strategy

본 문서는 OrderHero 개발 조직이 사용하기 위한 **표준 Git Flow 전략**을 정의한다.  
핵심 목표는 **main 브랜치의 절대적 안정성**, **개발 브랜치(dev)의 통합 관리**,  
그리고 **기능별(feature) 개발의 독립성 보장**이다.

## 핵심 원칙

### 1. main ← dev 병합 금지
`dev 브랜치를 main 브랜치에 절대 merge하지 않는다.`  
main은 오직 검증 완료된 작업 브랜치만 merge될 수 있다.

### 2. 작업 브랜치는 main 브랜치에서 생성
새로운 기능/수정 작업은 항상 다음과 같이 시작한다:

```bash
git checkout main
git pull
git checkout -b feature/your-task
```

### 3. dev ← 작업 브랜치 : Rebase Merge 권장

통합 테스트 및 QA를 위해 dev에 병합할 때는 rebase merge를 사용한다.
* feature 브랜치의 실제 commit history 유지
* dev에서 충돌을 빠르게 발견하고 조정
* dev를 기능 통합 환경으로 유지

### 4. main ← 작업 브랜치 : Squash Merge 권장
배포 브랜치(main)는 기능별 1 commit 형태로 정리한다.
* main 브랜치는 항상 깔끔한 이력 유지
* 기능 단위로 rollback 용이
* 불필요한 세부 commit이 main에 누적되지 않음

### Hotfix 전략
* hotfix/* 브랜치는 main에서 생성
* main에 squash merge 후 dev에 rebase merge로 반영

---

## 초기 설정
* 자신의 계정 Profile -> settings -> Developer Settings -> Personal access token(PAT) -> Token(classic)
* repo check
* workflow check
* gits check
* update token 클릭
* 토큰 반드시 별도 파일로 저장(저장하지 않으면 두번 다시 찾지 못함)
* 1.에서 생성한 토큰을 가지고 clone시 사용
* 프로젝트 Clone
* 예) git clone https://github.com/orderhero-lab/[레포명].git --recursive
