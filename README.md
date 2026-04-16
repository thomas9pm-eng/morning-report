# 모닝 브리핑 루틴 ☀️

매일 아침 9시(KST)에 자동으로 생성되는 모닝 브리핑 보고서입니다.

Claude Code의 **Routines** 기능을 사용하여 스케줄 실행됩니다.

## 보고서 구성

| 섹션 | 내용 |
|------|------|
| 📊 글로벌 시장 요약 | S&P 500, 나스닥, VIX, 원유, 비트코인, Fear & Greed, 환율 |
| 📰 오늘의 핵심 뉴스 | AI, 우주산업, 테슬라, 반도체, 거시경제 관련 뉴스 5개 |
| 📝 메르 블로그 최신글 | 네이버 블로그 "메르"(ranto28) 최신 글 3개 |
| 📅 오늘의 일정 | Google Calendar 연동 일정 |
| 🌤️ 오늘의 날씨 | 경기도 부천시 날씨 |

## 파일 구조

```
morning-report/
├── README.md                        # 이 파일
├── routine_prompt.md                # 루틴 프롬프트 원본
├── setup_guide.md                   # 상세 셋업 가이드
└── morning_briefing_YYYYMMDD.md     # 자동 생성되는 보고서 (날짜별)
```

## 사전 준비

1. **플랜**: Pro / Max / Team / Enterprise 중 하나
2. **커넥터**: Google Calendar 연결 (`claude.ai → Settings → Connectors`)
3. **환경**: Full internet access 활성화 (`claude.ai/code → Environments`)

## 루틴 설정

| 항목 | 설정값 |
|------|--------|
| 이름 | 모닝 브리핑 |
| 프롬프트 | [`routine_prompt.md`](./routine_prompt.md) 내용 복사 |
| 모델 | Claude Sonnet 4 또는 Opus 4 |
| 리포지토리 | 이 repo 연결 |
| 환경 | Full internet access |
| 커넥터 | Google Calendar |
| 트리거 | Schedule → Daily → 오전 9:00 (KST) |

자세한 설정 방법은 [`setup_guide.md`](./setup_guide.md)를 참고하세요.

## 루틴 관리

- **루틴 페이지**: [claude.ai/code/routines](https://claude.ai/code/routines)
- **수동 실행**: 루틴 상세 페이지 → Run now
- **일시정지**: Repeats 섹션 토글 off
- **주말 제외**: 트리거를 Weekdays로 변경
