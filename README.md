# SKT CX Governance Hub

SKT Next Channel UX 거버넌스 문서 사이트.  
배포 주소: **https://governance-xi.vercel.app**

---

## 사이트 구조

```
governance/
├── index.html              ← 홈 (문서 카드 목록)
├── UXP/
│   └── UXP_governance.html ← UX 원칙 (여정 7단계 × 16패턴)
├── UXPT/
│   └── UXPT_governance.html ← UX 패턴 (버튼·로딩·네비 등 56패턴)
├── VOT/
│   └── VOT_governance.html ← Voice & Tone (DEF·RUL·SIT·SEG)
├── AIG/
│   └── AIG_governance.html ← AI 가이드라인 (T Agent·Use Case·비주얼)
├── CV/
│   └── CV_governance.html  ← 서비스 핵심 가치 (CV01~CV04)
├── TK/                     ← Confluence 원본 참고자료 (배포 안 됨, 작업 맥락용)
└── llms.txt                ← AI 참조용 인덱스
```

각 `*_governance.html`이 실제 배포되는 문서 본체입니다.  
`TK/` 폴더는 원본 기획 자료(Confluence 저장본)로, 각 거버넌스 패턴의 근거 자료입니다.

---

## 수정 및 배포 방법

### 저장소 처음 받기
```bash
git clone https://github.com/sunnyhill333-dotcom/governance.git
cd governance
```

### 파일 수정 후 배포
```bash
git add .
git commit -m "VOT 컴포넌트 규칙 추가"
git push
```

push 후 1~2분 내에 **https://governance-xi.vercel.app** 자동 반영됩니다.  
Vercel 계정·CLI 설치 불필요.

### 새 패턴 카드 추가하는 HTML 패턴
```html
<article class="pattern-card" data-pattern-id="VOT_CMP_1" data-status="new">
  <div class="pattern-card-header">
    <div class="pattern-id-badge">VOT_CMP_1</div>
    <div class="pattern-meta">
      <div class="pattern-name">패턴 이름</div>
      <div class="pattern-desc">한 줄 설명</div>
    </div>
    <span class="status-badge status-new">New</span>
  </div>
  <div class="pattern-body">
    <!-- rule-row, do-dont-grid, copy-block, scenario-table 조합 -->
  </div>
</article>
```

상태 뱃지: `status-fundamental` / `status-recommend` / `status-new` / `status-refine`

---

## 업데이트 히스토리

### 2026.06.17 — 전체 문서 정비 (현재 버전)
- UXP: 고객 여정 7단계 전 구간 패턴 완성 (ETR·EXP·SCH·DCD·ACT·TCP·RSV)
- UXP: 각 패턴에 TK 지향점·CV 연계 추가
- UXPT: 인터랙션 패턴 8종 완성 (BTN·CCC·ERR·LOD·NAV·PGT·PRC·RCV)
- VOT: DEF 3장 + RUL 6장 + SIT 7장 + SEG 4장 완성
- VOT: RUL_5(Zone A LLM 보이스), RUL_6(AI 언어 라벨) 신규 추가
- AIG: T Agent 정의·AI Key Use Case·AI 비주얼 커뮤니케이션 완성
- CV: 핵심 가치 4종(Borderless·Intent-Based·Frictionless·Engaging) 완성
- 전 문서 TK 패널 연동 (Confluence 원본 기획 요건과 패턴 크로스 참조)
- 홈(index.html) CSS Highlight API 기반 전문 검색 기능 구현

### 2026.06 초 — VOT 초안 → 통합 HTML
- VOT: 상황별(SIT) 7개, 고객 특성별(SEG) 4개 패턴 초안 작성
- `VOT/old/VOT_inline_card_do_dont.html` 스타일 실험 후 현재 구조로 통합

### 2026.05 — UXP 초안 → 통합 HTML
- `UXP/old/UXL_*.md` 마크다운 초안 → `UXL_*_final.html` 섹션별 검토 → `UXP_governance.html` 단일 파일 통합
- ETR·EXP·SCH·DCD·ACT·TCP·RSV 순서로 작성

### 2026.04 — SDG 초안 및 사이트 구조 수립
- `SDG/old/SDG_governance.md` 마크다운으로 컴포넌트·네이밍 규칙 초안
- 섹션별 단위 HTML(`SDG_CMP_unit.html` 등) 실험 후 현재 사이트 구조(폴더별 governance.html) 확정
- Vercel CLI 배포 설정 (`.vercel/project.json`)

---

## VOT 인수인계 — 클라이언트 피드백 (2026.06.23)

> 8월부터 SB Studio를 통한 스토리보드 산출 시작 예정.  
> 현재 VOT 수준으로는 스토리보드 내 라이팅 품질을 보장하기 어렵다는 피드백.

### 추가 필요한 작업 (우선순위 순)

#### 1순위: VOT_CMP — 컴포넌트별 라이팅 규칙 신설
현재 `VOT_RUL_1`은 컴포넌트별 **최대 글자 수만** 정의.  
아래 컴포넌트별로 **구조 패턴 + DO/DON'T + Copy Template** 추가 필요.

| 컴포넌트 | 현재 | 필요한 것 |
|---|---|---|
| Micro Task 카드 | 길이 기준만 | 레이블 구조(명사+동사), 컨텍스트 작성 규칙 |
| AIA Advice | 길이 기준만 | 결론선행 구조, 줄바꿈 기준, 개인화 삽입 위치 |
| Offer 카드 | 길이 기준만 | headline/sub 구조, 절감 수치 표기 패턴 |
| FRL 안심 문구 | 길이 기준만 | 확정형 표현 패턴, 수동태 예외 기준 |
| 토스트/스낵바 | 길이 기준만 | 동사형 완료 패턴, 이모지 사용 기준 |
| 오류 메시지 | 길이 기준만 | 원인+행동 2문장 구조 |
| CTA 버튼 | 없음 | 동사형 단문 기준, 금지 표현 |

참고 레퍼런스: [신한카드 UX 라이팅 가이드](https://ux.shinhan.com/155fe4737/p/779d89---)

#### 2순위: VOT_TRM — 용어집 & 교정셋 신설
고객언어연구팀 자료 수신 후 반영 예정.

| 항목 | 내용 | 수신 시기 |
|---|---|---|
| '사람잡는 글쓰기' | 전사 UX 라이팅 고객 언어 가이드라인 | 메일로 수신 예정 (곧) |
| 디지털 UX언어 가이드 | 팀 자체 제작 라이팅 가이드 | **2026년 8월** |
| 교정셋 데이터 | as-is / to-be 교정 세트 | 내부 수집 중 |
| 권장어 매핑 테이블 | 금지어 ↔ 권장어 | 내부 수집 중 |
| 정규표현식 패턴 | 통화·날짜·시간 표기 규칙 | 내부 수집 중 |

> 이 데이터는 추후 RAG화해서 SB Studio API에 연동 예정 (기획2팀 현규님 협업).  
> 데이터 수신 시 VOT_TRM 섹션 신설 후 `llms.txt`도 함께 업데이트.

#### 3순위: llms.txt 업데이트
새 섹션 추가 시 `llms.txt`의 VOT 항목에 패턴 ID 목록 추가.

---

## 참고

- Vercel 프로젝트: `governance` (team: SKT Next)  
- TK 원본 자료 위치: `TK/` 폴더 (Confluence 저장 HTML)  
- 구 초안 자료 위치: `UXP/old/`, `VOT/old/`, `SDG/old/`
