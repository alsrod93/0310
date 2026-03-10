# 제품 요구사항 정의서 (PRD): 학습 밀착형 AI 공학계산기 (Edu-Math AI Calculator)

## 1. 제품 개요 (Product Overview)

### 1.1. 제품명
학습 밀착형 AI 공학계산기 (Edu-Math AI Calculator)

### 1.2. 목적 (Objective)
기존 공학용 계산기가 제공하는 단순 결과 도출 시스템을 넘어, 사용자의 학습 수준에 맞춘 문제 풀이 과정과 필수 수학적 개념 설명을 제공하여 사용자(주로 학생)의 실질적인 문제 해결력 향상 및 완전 학습을 지원합니다.

### 1.3. 대상 사용자 (Target Audience)
*   **초·중학생 (Beginner):** 수식의 기본 개념과 원리 파악이 필요한 기초 학습자
*   **고등학생 (Intermediate):** 내신 및 수능 대비를 위해 다양한 유형의 유사 문제 풀이 훈련이 요구되는 심화 학습자
*   **대학생/일반인 (Advanced):** 전공 수학 등 복잡한 수식의 단계별 도출 과정과 엄밀한 이론적 배경이 필요한 고급 학습자

---

## 2. 주요 기능 요구사항 (Functional Requirements)

### 2.1. 수식 입력 및 계산 (Formula Input & Calculation)
*   **사용자 입력:** 문자, 숫자, 수학 기호를 포함한 수식을 입력할 수 있어야 합니다.
*   **계산 수행:** 입력된 수식에 대한 정확한 수학적 결과값을 산출해야 합니다.
*   **난이도 선택:** 사용자가 본인의 학습 수준(초등, 중등, 고등, 대학생)을 선택할 수 있는 드롭다운 메뉴 형태의 인터페이스를 제공해야 합니다.

### 2.2. 단계별 풀이 제공 (Step-by-step Solution)
*   도출된 결과를 바탕으로 해를 구하기까지의 **모든 과정을 단계별로 분할**하여 텍스트 형태로 제시해야 합니다.
*   가독성을 위해 모든 수학 기호와 수식은 **LaTeX 포맷**으로 렌더링되어야 합니다. (MathJax 또는 KaTeX 라이브러리 활용)

### 2.3. 맞춤형 개념 설명 (Tailored Concept Explanation)
*   선택된 난이도에 따라 **각 단계에 사용된 핵심 수학 개념을 맞춤형으로 설명**해야 합니다.
    *   *초등/중등:* 직관적이고 쉬운 비유 활용 (기초 원리 중심)
    *   *고등:* 교육과정 연계 공식 증명 및 개념 위주
    *   *대학생/일반:* 엄밀한 수학적 정의와 이론적 배경 포함 (심층 해설)

### 2.4. 유사 문제 생성 (Generated Similars)
*   입력된 수식 및 사용된 개념과 **유사한 난이도를 가진 연습 문제를 1개 이상 자동 생성**하여 추가 제공해야 합니다.
*   유사 문제의 난이도와 해설 역시는 사용자가 선택한 학습 수준에 부합해야 합니다.

---

## 3. 화면 디자인 및 스타일 요구사항 (Screen Design & Style)

### 3.1. 전반적인 분위기 (Overall Tone & Mood)
*   **Modern & Clean:** 학생들이 학습 시 집중력을 방해받지 않도록 장식을 최소화한 모던하고 정돈된 룩앤필(Look and Feel)을 지향해야 합니다.
*   **색상 팔레트:**
    *   Primary: 신뢰감을 주는 푸른색 계열(Navy 또는 Royal Blue)
    *   Background: 눈의 피로를 최소화하는 밝은 회색 또는 미색(Off-white)
    *   Text: 가독성이 높은 짙은 회색(Dark Gray)
    *   다크 모드(Dark Mode) 토글 옵션 지원 고려.

### 3.2. 화면 및 레이아웃 구조 (Layout Structure)
*   **헤더(Header):** 서비스 로고 및 학습 수준(난이도) 선택 드롭다운 영역.
*   **입력 영역(Input Section):** 수식을 입력할 수 있는 텍스트 박스, 가상 키패드(수학 기호 입력 용이성 제공), 그리고 '계산/풀이 시작' 버튼.
*   **결과 영역(Result Section):** 
    *   최종 결과값 강조(Bold & Primary Color) 표시.
    *   풀이 과정과 개념 설명을 단계별로 나누어 배치.
*   **유사 문제 영역(Similar Problem Section):** 풀이 영역 하단에, 스스로 풀어볼 수 있는 아웃링크 또는 '유사 문제 확인' 버튼으로 진입 가능한 섹션.

### 3.3. UI 컴포넌트 특성 (UI Components)
*   **아코디언 형태(Accordion):** 긴 풀이 과정이나 상세 개념 설명, 추가 유사 문제는 클릭 시 접고 펼칠 수 있는 인터랙션(아코디언 뷰)을 사용하여 정보 인지 부하를 줄입니다.
*   **반응형(RWD):** 모바일, 태블릿, 데스크톱 등 디바이스 별로 입력 폼 크기와 결과 영역 너비가 최적화되어야 합니다.

---

## 4. 시스템 아키텍처 및 상세 프로젝트 구조 (Architecture & Project Structure)

### 4.1. 아키텍처 데이터 흐름 (Data Flow)
1. **Frontend(Client):** 웹 브라우저에서 사용자가 수식 및 학습 수준 입력. 요청(Request) 전송.
2. **Backend(Vercel Flask):** 프론트엔드 요청 수신 후, 내부 로직 및 프롬프트를 조합하여 Groq AI API 호출.
3. **AI Engine:** Groq API에서 JSON 형태로 정답, 단계별 풀이, 개념 설명, 유사 문제 응답(Response).
4. **Frontend(Client):** 반환받은 JSON 데이터를 DOM 요소에 파싱하고 LaTeX으로 변환 후 화면 출력.

### 4.2. 프로젝트 파일 구조 (Project File Tree)
Vercel Serverless Function 배포를 고려한 로컬 구조입니다.

```text
edu-math-ai-calculator/
├── api/
│   └── index.py            # Vercel 배포용 Flask 진입점 파일 (라우팅, API 래퍼)
├── static/
│   ├── css/
│   │   ├── style.css       # 메인 스타일시트
│   │   └── theme.css       # 라이트/다크 모드 색상 테마 변수 정의
│   ├── js/
│   │   └── app.js          # API 비동기 통신 및 LaTeX 렌더링, 이벤트 리스너 등
│   └── icons/              # 파비콘 및 각종 서비스 UI 아이콘 이미지 폴더
├── templates/
│   └── index.html          # 메인 HTML UI 구조
├── requirements.txt        # python 라이브러리 의존성 파일 (Flask, groq, requests 등)
├── vercel.json             # Vercel 빌드 및 배포 라우팅 설정 파일
└── README.md               # 프로젝트 설정 및 로컬 구동 가이드
```

---

## 5. 비기능 및 인프라 요구사항 (Non-Functional Requirements)

### 5.1. 성능 및 최적화
*   **지연시간 최소화:** Groq API의 장점인 빠른 추론 속도를 극대화할 수 있도록, 불필요한 서버-클라이언트 간 페이로드를 줄여 체감속도 3초 이내 응답을 보장합니다.
*   **경량 프론트엔드:** React, Vue 등의 SPA 프레임워크를 배제하고 HTML, CSS, Vanilla JS를 사용하여 초기 로딩 타임을 최소화합니다.

### 5.2. 인프라스트럭처 (Infrastructure)
*   **코드 버전 관리:** Git 기반 중앙 저장소 (GitHub 주 사용) 활용.
*   **배포 파이프라인:** Vercel 연동을 통한 Push 트리거 기반 자동 빌드 및 배포 시스템 운영.

---

## 6. 제약 사항 (Constraints)

*   모든 수식은 클라이언트에서 LaTeX(`$...$` 혹은 `$$...$$`) 형태로 정상 렌더링되어야 합니다.
*   수학 해석 엔진은 외부 라이브러리(SymPy 등)를 메인으로 하기 보단, AI(Groq API) 프롬프트 엔지니어링을 최우선적으로 사용하여 서술형으로 텍스트를 구성해야 합니다.

---

## 7. 릴리즈 계획 (Release Plan)

*   **1단계:** 환경 설정 및 API 연동 (완료 목표: Sprint 1)
*   **2단계:** 프론트엔드 UI 개발 (완료 목표: Sprint 2)
*   **3단계:** 백엔드 로직 구현 (완료 목표: Sprint 3)
*   **4단계:** 통합 및 배포 (완료 목표: Sprint 4)
