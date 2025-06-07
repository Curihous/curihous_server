# 📈 QBit Backend

**초보 투자자를 위한 투자 스타일 맞춤형 AI 퀀트 트레이딩 기반 투자 훈련 플랫폼, QBit**

이 레포지토리는 QBit 서비스의 백엔드 서버로, 사용자 인증, 투자 성향 진단, 모의투자 결과 저장, AI 분석 요청 등 전반적인 비즈니스 로직과 데이터베이스 연동을 담당합니다.

> AI 분석 서버는 FastAPI(Python)로 별도 운영되며, 해당 레포지토리는 분리 관리됩니다.


## 🛠 주요 기술 스택

- **Spring Boot**: Java 기반 웹 애플리케이션 프레임워크  
- **Spring Security (JWT)**: 인증 및 권한 관리  
- **Spring Data JPA (Hibernate)**: ORM 기반 데이터 처리  
- **PostgreSQL / AWS RDS**: 관계형 데이터베이스  
- **Redis**: 실시간 데이터 캐싱 및 토큰 저장  
- **WebSocket + STOMP**: 실시간 호가창 처리  
- **Docker**: 컨테이너 기반 배포  
- **Jenkins**: CI/CD 자동화 파이프라인 구축

## 📑 API 문서

- Swagger UI: {링크 업데이트 예정}

# 📂 핵심 폴더 구조

```text
backend-server/
├── Dockerfile                     # 백엔드 서버 컨테이너 정의
├── Jenkinsfile                   # Jenkins CI/CD 파이프라인
├── build.gradle                  # 프로젝트 빌드 설정
├── scripts/                      # 배포 자동화 스크립트
│   └── deploy.sh
│
├── src/main/
│   ├── java/com/qbit/
│   │   ├── controller/           # API 엔드포인트 정의
│   │   ├── service/              # 비즈니스 로직 처리
│   │   ├── domain/               # Entity, DTO, Enum 등 핵심 도메인 모델
│   │   ├── repository/           # DB 연동 인터페이스 (JPA)
│   │   ├── config/               # 보안, CORS, DB 등 환경 설정
│   │   └── QbitApplication.java  # 메인 애플리케이션 클래스
│   └── resources/
│       └── application.yml       # 기본 설정 파일
│
├── configs/
│   └── application-prod.yml      # 운영 환경 설정
└── test/                         # 테스트 코드
```

## 🤝 협업 규칙

### 🔀 브랜치 전략

- `main`: 운영 및 배포용 브랜치
- `dev`: 개발 기능 통합 브랜치
- `feature/기능명`: 개별 기능 개발 브랜치 (예: `feature/login`, `feature/invest-report`)

> 모든 브랜치는 `dev` 브랜치에서 분기하며, 완료 후 `dev`로 Pull Request를 생성합니다.

### 📝 커밋 메시지 규칙

형식:  
`<타입>: <변경 내용 요약>`

예시:  
`feat: 회원가입 기능 구현`  
`fix: 종목 검색 오류 수정`

#### 커밋 타입 목록

| 타입       | 설명 |
|------------|------|
| `feat`     | 새로운 기능 추가 (API, 도메인 로직 등) |
| `fix`      | 버그 수정 (Null 오류, 예외 처리 등) |
| `refactor` | 리팩토링 (기능 변화 없이 구조 개선) |
| `style`    | 코드 스타일 수정 (공백, 들여쓰기 등) |
| `docs`     | 문서 수정 (README, Swagger, 주석 등) |
| `test`     | 테스트 코드 추가/수정 |
| `chore`    | 설정/빌드 관련 변경 (Gradle, .gitignore 등) |
| `perf`     | 성능 개선 (쿼리 최적화 등) |
| `ci`       | CI/CD 관련 설정 변경 (Jenkins, GitHub Actions 등) |
| `env`      | 환경 변수(.env) 또는 비밀 키 관련 변경 |

### 🔁 Pull Request 규칙

- PR은 `dev` 브랜치 기준으로 생성합니다.
- PR 제목 형식: `[기능명] 간단한 변경 요약`  
  예: `[투자 리포트] AI 분석 로직 추가`
- PR 설명에 다음 항목을 포함합니다:
  - 변경 내용 요약
  - 테스트 방법 또는 확인 요청 사항
- 팀원 1명 이상의 리뷰 승인 후 병합합니다.
