# 매일 아침 모닝 브리핑 루틴 — 셋업 가이드

## 개요

Claude Code의 "루틴(Routines)" 기능을 이용해 **매일 아침 9시(KST)**에 자동으로 모닝 브리핑 보고서를 생성하는 설정 가이드입니다.

---

## 사전 준비

### 1. 플랜 확인
- Pro / Max / Team / Enterprise 중 하나 필요
- Claude Code on the Web이 활성화되어 있어야 합니다
- 일일 루틴 실행 횟수 제한: Pro 5회, Max 15회, Team/Enterprise 25회

### 2. 커넥터(Connectors) 연결
`claude.ai → Settings → Connectors` 에서 아래 항목을 연결해주세요:

| 커넥터 | 용도 |
|--------|------|
| **Google Calendar** | 오늘의 일정 읽기 |
| (선택) Slack | 보고서를 슬랙으로 받고 싶은 경우 |

### 3. 환경(Environment) 설정
- `claude.ai/code` → Environments에서 네트워크 접근을 **Full internet access**로 설정
- 웹 검색 및 외부 사이트 접근(네이버 블로그 등)이 필요하기 때문입니다

### 4. 리포지토리
- 루틴 생성 시 리포지토리 1개가 필요합니다
- 이 리포지토리(`morning-report`)를 연결하면 됩니다

---

## 루틴 생성 방법

### 웹에서 생성 (권장)
1. **[claude.ai/code/routines](https://claude.ai/code/routines)** 접속
2. **New routine** 클릭
3. 아래 내용을 순서대로 입력

| 항목 | 설정값 |
|------|--------|
| **이름** | 모닝 브리핑 |
| **프롬프트** | `routine_prompt.md` 파일 내용을 복사·붙여넣기 |
| **모델** | Claude Sonnet 4 (빠른 실행) 또는 Opus 4 |
| **리포지토리** | 이 repo (`morning-report`) 연결 |
| **환경** | Full internet access가 켜진 환경 |
| **커넥터** | Google Calendar 포함 확인 |
| **트리거** | Schedule → Daily → 오전 9:00 |

### CLI에서 생성
```
/schedule daily 모닝 브리핑 at 9am
```
이후 대화형으로 프롬프트와 설정을 입력합니다.

---

## 실행 확인 및 관리

### 실행 결과 확인
- `claude.ai/code/routines` → 해당 루틴 클릭 → 과거 실행(run) 목록 확인
- 각 실행을 클릭하면 세션으로 열려서 보고서 내용 확인 가능

### 수동 실행 (테스트)
- 루틴 상세 페이지에서 **Run now** 클릭하면 즉시 실행됩니다
- 처음 만든 후 반드시 한 번 테스트 실행해보세요

### 일시정지 / 수정
- **Repeats** 섹션의 토글로 스케줄 on/off
- 연필 아이콘으로 프롬프트, 커넥터, 트리거 수정 가능

---

## 커스터마이징 팁

### 보고서를 슬랙으로 받고 싶다면
프롬프트 마지막에 아래 문구를 추가하세요:
```
보고서 작성이 완료되면, Slack 커넥터를 사용해서
#morning-briefing 채널(또는 나에게 DM)으로 보고서 전문을 전송해줘.
```

### 특정 종목 모니터링 추가
프롬프트 1번 섹션에 아래를 추가하세요:
```
- **관심 종목**: SK하이닉스(000660.KS), KODEX 은선물(H)(167390)의 전일 종가와 등락률
```

### 주말 제외
트리거를 Daily 대신 **Weekdays**로 변경하면 월~금만 실행됩니다.

---

## 참고

- 루틴 공식 문서: https://code.claude.com/docs/en/routines
- 루틴 관리 페이지: https://claude.ai/code/routines
- 루틴은 Anthropic 클라우드에서 실행되므로 Mac이 꺼져 있어도 동작합니다
