# API 키 설정

Transy에서 AI 번역을 사용하려면 API 키가 필요합니다. 무료로 시작하거나, 유료 API를 사용해 더 많이 읽을 수 있습니다.

---

## 무료로 시작하기

### 옵션 1: Google Gemini (GCP) 무료 티어

Google에서 제공하는 Gemini API를 무료로 사용할 수 있습니다.

#### 1단계: Google AI Studio 접속

1. [Google AI Studio](https://aistudio.google.com/)에 접속
2. Google 계정으로 로그인

#### 2단계: API 키 생성

1. 좌측 메뉴에서 "Get API key" 클릭
2. "Create API key" 버튼 클릭
3. 프로젝트 선택 (없으면 새로 생성)
4. 생성된 API 키 복사

> **주의**: API 키는 한 번만 표시됩니다. 안전한 곳에 저장해 두세요.

#### 무료 티어 한도 (2026년 2월 기준)

| 모델 | 분당 요청 (RPM) | 일일 요청 (RPD, 일일 요청 횟수) | 분당 토큰 (TPM) |
|------|----------------|--------------------------------|-----------------|
| **Gemini 2.5 Flash (앱 기본)** | 10 | 250 | 250,000 |
| Gemini 2.5 Flash-Lite | 15 | 1,000 | 250,000 |
| Gemini 2.5 Pro | 5 | 100 | 250,000 |
| Gemini 3.1 Pro Preview | - | - | - |
| Gemini 3 Flash Preview | 무료 | 무료 | - |
| Gemini 2.0 Flash-Lite | 무료 | 무료 | 250,000 |
| Gemma 3 27B | 완전 무료 | 완전 무료 | - |

> **팁**: 앱 기본 모델인 **Gemini 2.5 Flash**는 일 250 RPD(일일 요청 횟수) 무료입니다. 일반적인 소설 읽기에 충분합니다.
>
> **참고**: 2025년 12월에 Google이 무료 한도를 50~80% 축소했습니다. 최신 정보는 [Gemini API 가격 정책](https://ai.google.dev/pricing) 공식 페이지에서 확인하세요.

---

### 옵션 2: OpenRouter 무료 티어

OpenRouter는 다양한 AI 모델을 하나의 API로 사용할 수 있는 서비스입니다.

#### 무료 할당량

| 조건 | 무료 할당량 |
|------|------------|
| 가입 즉시 | 50 RPD (일일 요청 횟수) |
| $10 이상 결제 후 | 1,000 RPD (일일 요청 횟수) |

> **참고**: $10 결제 후 잔액은 유료 API 호출에 사용됩니다. 무료 모델만 사용하는 경우 차감되지 않습니다.

#### 무료 모델 검색

최신 무료 모델 목록 (컨텍스트 크기 기준 정렬):
- [OpenRouter 무료 모델 목록](https://openrouter.ai/models?max_price=0&order=context-high-to-low)

#### 앱에서 OpenRouter 설정 방법

1. [OpenRouter](https://openrouter.ai/)에서 계정 생성
2. API 키 발급 (Settings → API Keys)
3. 앱 설정 → API 키 추가
   - 제공자: **OpenRouter** 선택
   - API 키: 발급받은 키 입력
4. API 조합(폴백 체인) 설정에서:
   - 제공자: **OpenRouter** 선택
   - 모델: 위 링크에서 확인한 무료 모델 ID 직접 입력 (예: `google/gemma-3-27b-it:free`)

---

## 유료 API 가성비 추천

실사용 비교 기준 가성비 추천 순위입니다.

### 추천 순위

| 순위 | 모델 | 설명 |
|------|------|------|
| 1위 | **Grok 4.1 Fast** (Non-Reasoning) | 가성비 최우수, 속도와 품질의 균형 |
| 2위 | **Gemini 2.5 Flash** | 안정적인 품질, GCP 직접 또는 OpenRouter 경유 |
| 비추천 | Gemini 2.5 Flash-Lite | 반복 출력 버그 있음 — 사용 비추천 |

> **Flash-Lite 주의**: Gemini 2.5 Flash-Lite는 번역 중 텍스트가 반복되는 버그가 있어 사용을 권장하지 않습니다.

### Grok 4.1 Fast 사용 방법

앱에 내장된 **Grok Provider**를 사용합니다:
1. 앱 설정 → API 키 추가
   - 제공자: **Grok** 선택
   - API 키: [xAI 콘솔](https://console.x.ai/)에서 발급
2. API 조합 설정에서 제공자: **Grok** 선택
   - 모델 기본값: `grok-4-1-fast-non-reasoning` (변경 불필요)

### OpenRouter에서 유료 모델 선택하기

OpenRouter를 통해 다양한 유료 모델을 비교하고 사용할 수 있습니다:
- [OpenRouter 모델 목록](https://openrouter.ai/models)
- 사용량에 따라 과금되며, 사전에 크레딧을 충전해야 합니다.

### OpenAI Compatible 사용 방법

OpenAI API 스펙을 지원하는 다양한 서비스를 연결할 수 있습니다. Deepseek, Mistral, Ollama 등 OpenAI 호환 API를 제공하는 서비스라면 모두 사용 가능합니다.

> **중요**: Base URL 설정이 필수입니다. 각 서비스의 API 엔드포인트 주소를 정확히 입력해야 합니다.

**설정 방법**:
1. 앱 설정 → API 키 추가
   - 제공자: **OpenAI Compatible** 선택
   - API 키: 해당 서비스에서 발급받은 키 입력
   - Base URL: 서비스의 API 엔드포인트 입력
2. API 조합 설정에서 제공자: **OpenAI Compatible** 선택
   - 모델: 사용할 모델 ID를 직접 입력

**호환 서비스 예시**:
- [Deepseek](https://platform.deepseek.com/) — Base URL: `https://api.deepseek.com/v1`
- [Mistral](https://console.mistral.ai/) — Base URL: `https://api.mistral.ai/v1`
- [Ollama](https://ollama.com/) (로컬) — Base URL: `http://localhost:11434/v1`
- 기타 OpenAI API 호환 서비스

### GLM (ZhiPu) 사용 방법

ZhiPu AI에서 제공하는 중국 AI 모델을 사용할 수 있습니다.

**사용 가능한 모델**:

| 모델 | 설명 |
|------|------|
| **GLM-4.7 Flash** | 무료 기본 모델 (앱 기본값) |
| **GLM-4.7** | 고품질 모델 |
| **GLM-4.7 FlashX** | 경량 고속 모델 |

**설정 방법**:
1. [ZhiPu AI 콘솔](https://open.bigmodel.cn/)에서 API 키 발급
2. 앱 설정 → API 키 추가
   - 제공자: **ZhiPu GLM** 선택
   - API 키: 발급받은 키 입력
3. API 조합 설정에서 제공자: **ZhiPu GLM** 선택

> **참고**: GLM-4.7 Flash는 무료로 제공되어 비용 부담 없이 사용할 수 있습니다.

---

## 앱에서 API 키 등록

### 설정 화면 진입

1. 앱 실행 후 라이브러리 화면에서 우측 상단 설정(톱니바퀴) 아이콘 클릭
2. 설정 화면에서 "API 키 관리" 섹션 확인

설정 화면 구성:
- **상단 바**: "설정" 타이틀과 뒤로가기 버튼
- **스크롤 가능한 섹션들**: 프리미엄, API 키 관리, 번역 설정 등
- **하단 저장 버튼**: 전체 너비의 OutlinedButton

### API 키 추가

"API 키 관리" 섹션에서:
1. "API 키 추가" 버튼 클릭
2. 다이얼로그에서 별칭, API 키, 제공자 입력
3. "저장" 클릭

### 키 검증

저장 시 자동으로 API 키가 유효한지 검증합니다.

- 성공: 키가 정상적으로 등록됨
- 실패: 키가 잘못되었거나 만료됨

---

## 여러 API 키 관리

Transy는 여러 개의 API 키를 등록하고 관리할 수 있습니다.

### 용도

- 개인용/업무용 키 분리
- 여러 프로젝트의 키 관리
- API 설정 체인 구성 (하나가 실패하면 다른 것 사용)

### 키 관리

등록된 API 키 목록이 카드 형태로 표시됩니다:
- **편집**: 별칭 수정
- **삭제**: 사용하지 않는 키 제거
- **사용량 확인**: "사용량 통계 보기" 버튼으로 API 호출 통계 확인

---

## 사용 가능한 모델

Transy에서 사용할 수 있는 Gemini 모델입니다.

### 텍스트 모델 (번역/전처리용)

| 모델 | 특징 | 추천 용도 |
|------|------|----------|
| **Gemini 2.5 Flash** | 빠르고 경제적 (앱 기본값) | 일반 번역, 대부분의 사용자 |
| **Gemini 2.5 Pro** | 높은 품질 | 고품질 번역이 필요할 때 |
| **Gemini 2.5 Flash-Lite** | 매우 빠름, 저비용 | ⚠️ 비추천 (줄바꿈 버그) |
| **Gemini 3.1 Pro Preview** | 최신 모델 (실험적, 유료 전용) | 최고 품질 번역 |
| **Gemini 3 Flash Preview** | 최신 모델 (실험적) | 최신 기능 테스트 |
| **Gemini 2.0 Flash-Lite** | 가벼운 이전 버전 | 빠른 처리 |
| **Gemma 3 27B** | 오픈소스 모델 | 완전 무료 |

### TTS 모델 (음성 변환용)

| 모델 | 특징 |
|------|------|
| **Gemini 2.5 Flash TTS** | 기본 TTS 모델 (권장) |
| **Gemini 2.5 Pro TTS** | 고품질 TTS |

---

## 어떤 모델을 선택해야 할까요?

### 무료로 시작하는 분

**Gemini 2.5 Flash** (앱 기본 모델) — 일 250 RPD(일일 요청 횟수) 무료, 대부분의 소설에 적합

또는 **OpenRouter 무료 티어** — 가입 즉시 50 RPD(일일 요청 횟수), 다양한 모델 선택 가능

### 가성비로 더 많이 읽고 싶은 분

**Grok 4.1 Fast** (Non-Reasoning) — 실사용 비교에서 가성비 1위

### 안정성을 원하는 분

**Gemini 2.5 Flash** — GCP 직접 사용, 안정적인 서비스

> **주의**: Gemini 2.5 Flash-Lite는 줄바꿈이 무한 생성되는 버그가 있어 사용을 비추천합니다.

---

## 문제 해결

### "API 키가 유효하지 않습니다"

- 키를 복사할 때 앞뒤 공백이 포함되지 않았는지 확인
- 키가 만료되거나 삭제되지 않았는지 확인
- [Google AI Studio](https://aistudio.google.com/)에서 키 상태 확인

### "할당량 초과"

- 무료 티어 한도를 초과한 경우
- 일일 한도가 리셋될 때까지 대기 (24시간 후)
- 또는 유료 플랜으로 업그레이드
- 또는 다른 할당량을 가진 키-모델 을 추가

### API 키를 잃어버렸어요

- Google AI Studio에서 새 키를 생성하세요
- 기존 키는 삭제하고 새 키를 사용하는 것이 안전합니다

---

[← 앱 설치](installation.md) | [다음: 첫 소설 추가하기 →](first-novel.md)
