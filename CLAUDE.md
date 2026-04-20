# 피리어드 (Period.) — 프로젝트 컨텍스트

## 세션 시작 시 필수 작업
작업 전 반드시 최신 소스를 fetch해서 시작할 것:
- 홈페이지 소스: https://github.com/period317/period317.github.io/blob/main/index.html
- posts.json: https://github.com/period317/period317.github.io/blob/main/posts.json

---

## 전체 시스템 구조

```
[홈페이지] period317.github.io
    └─ 상담 폼 (3종) → Formspree (xgopvzoe) → Telegram (Formspree Bot)

[네이버 블로그] blog.naver.com/songtorytelling
    └─ RSS 피드 → Make.com → Notion 블로그 글 마스터 DB

[Notion 워크스페이스]
    ├─ 블로그 글 마스터 DB  (32cd5f8aa11b8164bdeae69f1d0cd969)
    └─ 학생 후기 DB         (331d5f8aa11b808b98a5f24749e316df)
```

---

## 레포지토리

**작업 레포 (이것만 사용):**
- GitHub: https://github.com/period317/period317.github.io
- 브랜치: `main`
- 배포 URL: https://period317.github.io
- 빌드 없음 — push하면 GitHub Pages에 바로 반영

**중복 레포 (무시할 것):**
- https://github.com/period317/period-site (내용 동일, 브랜치명만 `master`, 배포 안 됨, 삭제 예정)

---

## 파일 구조

```
period317.github.io/
├── index.html        ← 전체 사이트 (HTML/CSS/JS 단일 파일)
├── posts.json        ← 블로그 포스트 목록 (콘텐츠 탭에서 동적 로드)
├── CLAUDE.md         ← 이 파일
├── profile-ad.png    ← 어드쌤 프로필 사진
├── profile-piri.png  ← 피리쌤 프로필 사진
├── review-thumb.png  ← 후기 썸네일
├── robots.txt
└── sitemap.xml
```

---

## 사이트 구조 (탭 구성)

| 탭 | ID | 주요 내용 |
|---|---|---|
| 홈 | `home` | 히어로 + 카운트다운, 피리어드 소개, 블로그·유튜브 링크 |
| 선생님 | `teacher` | 어드쌤·피리쌤 프로필(사진+경력), 합격생 목록 |
| 수업 | `class` | 수업방식·내용·수업료 + 영화입시 DB (학교별 실기 정보, 서브탭) |
| 콘텐츠 | `content` | posts.json 기반 블로그 카드, 유튜브 링크 |
| 후기 | `reviews` | 수강생 후기 (모달 형태) |
| 무료상담 | `consultation` | 직접 입력 폼 3종 (Formspree 연동) |
| 입시 스케줄 | `schedule` | 19개교 영화·영상과 수시 입시 일정 (2025년 기준·26학번), 전형유형 필터, 월별 타임라인, 학교별 블로그 링크 예정 |

---

## 상담 폼 (Formspree → Telegram)

- **폼 종류**: 입시상담 / 단편제작 / 피드백 (`class="consult-form"`)
- **Formspree endpoint**: `https://formspree.io/f/xgopvzoe`
- **전송 방식**: JS fetch (FormData) → Formspree → Telegram (Formspree Bot)
- **성공 처리**: 폼 숨기고 `#form-success` 표시
- **주요 필드**: 문의유형(hidden), 신청자, 연락처, 희망전공, 입시상태, 경험, 도움유형, 상세내용, 지역, 상담시간

---

## RSS → Notion 자동화

- **툴**: Make.com
- **소스**: 네이버 블로그 RSS (`blog.naver.com/songtorytelling`)
- **대상 DB**: 피리어드 블로그 글 마스터 DB
- **동작**: 새 블로그 글 발행 시 자동으로 Notion DB에 행 추가

---

## Notion DB

### 블로그 글 마스터 DB
- **Notion URL**: https://www.notion.so/32cd5f8aa11b8164bdeae69f1d0cd969
- **상위 페이지**: 블로그 글 관리

| 필드 | 타입 | 값 |
|------|------|----|
| 제목 | title | |
| 대분류 | select | 피리어드 / 피리어드 에세이 / 입시분석 / 실기 강의 / 자료실 |
| 소분류 | select | 강사소개 / 수업소개 / 학생 후기 / 무료진단/상담 / 입시/영화/미래 / 영화 리뷰 / 책 리뷰 / 공통 분석 / 학교별 분석 / 글쓰기 / 분석 / 구술 / 논술 / 영화심층분석 / 연도별 모집요강 |
| 상태 | select | 초안 / 작성완료 / 발행완료 |
| 발행일 | date | |
| 원문링크 | url | |
| 본문 | text | |
| 태그 | multi_select | 영화 / 입시 / 실기 / 에세이 / 리뷰 / 분석 / 자료 |
| 플랫폼 | multi_select | 네이버블로그 / 유튜브 / 웹사이트 |
| 메모 | text | |

### 학생 후기 DB
- **Notion URL**: https://www.notion.so/331d5f8aa11b808b98a5f24749e316df
- **상위 페이지**: 피리어드 내부 관리

| 필드 | 타입 | 값 |
|------|------|----|
| 이름 | title | |
| 성별 | select | 여 / 남 |
| 시작 시기 | select | 중3 / 고1 / 고2 / 고3 / 재수 / 삼수 |
| 기간 | text | |
| 수업 내용 | multi_select | 단편영화제작 / 논술 / 영화이론 / 영화/방송/미디어 상식 / 이미지 분석 / 시나리오 분석 / 영화 분석 기초 / 구술/면접지 작성 / 이야기 글쓰기 |
| 담당 강사 | select | 피리+어드 / 어드 / 피리 |
| 후기 원문 | text | |
| 후기 최종 | text | |
| 후기 제목 | text | |
| 과외 전 경험 | multi_select | 아무 경험 없음 / 영상관련 고등학교 / 대학전공(재수 이상) / 학원 / 과외 / 단편영화제작참여 / 단편영화연출 |
| 목표학교 | multi_select | |
| 합격학교 | multi_select | 대진대 / 성균관대 / 서경대 / 수원대 / 청주대 / 숙실대 / 숭실대 / 서울예대 |
| 합격증 | file | |
| 과외유입경로 | select | 학부모추천 / 검색 / 지인추천 / 과외학생추천 |
| 입학년도 | number | |

---

## 브랜드 & 강사 정보

**브랜드명:** 피리어드 (Period.)
**슬로건:** "더 이상 묻지마, 끝." (영어 슬랭 Period!의 뜻)
**대상:** 영화과 입시 준비 학생

**어드쌤**
- 중앙대 연극영화과 영화연출 전공, 수석졸업
- 중앙대 첨단영상대학원
- 학원·한림예고 6년, 약 150명 지도
- 상세소개: https://blog.naver.com/songtorytelling/224217327581

**피리쌤**
- 연세대 신문방송학과 졸업
- IT기업, 카드사(최단기 과장 승진), 외국계 PR팀 경력
- 자소서·구술·면접·진로 전략 담당
- 2019년부터 합류
- 상세소개: https://blog.naver.com/songtorytelling/224217581391

**1:1 과외 실적 (2019~2025):** 11명 전원 목표 달성
합격 학교: 한국예술종합학교, 중앙대, 서경대, 서울예대, 숭실대, 성균관대, 동아방송대, 백석예대 등

---

## 수업료

| 구분 | 금액 |
|---|---|
| 1회 (2시간) | 30만원 |
| 월 정기 (주 1회) | 100만원 |
| 6개월 이상 | 85만원 (15% 할인) |

장소: 스터디 카페 (강사 부담), 영등포·동작 근처, 협의 가능

---

## 외부 링크

| 용도 | URL |
|---|---|
| 네이버 블로그 | https://blog.naver.com/songtorytelling |
| 유튜브 채널 | https://www.youtube.com/channel/UC6LLKLW14n1foRQ-30JZ2Xg |
| 카카오톡 오픈채팅 | https://open.kakao.com/me/film_period |
| 무료상담 Google Forms (구버전) | https://forms.gle/LjpJcbkbh3YR7Zev9 |

---

## 디자인 가이드

**CSS 변수 (`:root`):**
```css
--bg: #ffffff
--pink: #F1296C      ← 메인 포인트 컬러
--lavender: #DDCEDD
--mauve: #917991
--mint: #53DABF
--blue: #4497E9
--text: #1a1a1a
--text-2: #555
--text-3: #999
--border: rgba(0,0,0,0.07)
--radius: 12px
--nav-h: 48px
--header-h: 56px
```

**폰트:** 시스템 폰트 (-apple-system, Apple SD Gothic Neo, 맑은 고딕)
**레이아웃:** 모바일 우선, 768px 이상에서 데스크탑 레이아웃

---

## 기술 스택 & 특이사항

- 순수 HTML/CSS/JS 단일 파일 (index.html), 프레임워크 없음
- Google Analytics: G-P0ZT2K5V2F
- 네이버 사이트 인증: 42d537c123cd7143c25bd5dc82e9fb244caa78d9
- OG/Twitter Card 메타태그 포함
- sitemap.xml, robots.txt 포함

**수정 시 주의:**
- CSS 변수는 `:root`에 집중
- 단일 파일이므로 섹션 찾을 때 `<!-- ========== 탭명 ==========` 주석으로 이동
- push 즉시 배포됨 (스테이징 없음)

---

## posts.json 구조

블로그 포스트를 동적으로 로드하는 데이터 파일.

```json
{
  "title": "포스트 제목",
  "url": "블로그 URL",
  "tag": "기초가이드 | 학원 vs 과외 | ...",
  "category": "입시분석 | 피리어드 | ...",
  "desc": "한 줄 설명",
  "date": "YYYY-MM-DD",
  "status": "발행완료 | 작성중"
}
```

새 블로그 글 추가 시 posts.json에 항목 추가하면 콘텐츠 탭에 자동 반영.

---

## Claude 로컬 환경 세팅

### GitHub 인증
- **계정**: period317
- **인증방식**: git credential store (영구 저장)
- **파일**: `~/.git-credentials`
- push 시 토큰 입력 불필요

### Claude Code 자동 승인
- **파일**: `~/.claude/settings.json`
- `"defaultMode": "bypassPermissions"` 설정 완료
- 매번 허용 팝업 없이 자동 실행

### Google Workspace MCP (2026-04-05 완료 — 윈도우 집 PC)
- **패키지**: taylorwilsdon/google_workspace_mcp
- **설치 위치**: `C:/Users/user/google_workspace_mcp` (`~/google_workspace_mcp`)
- **uv 설치**: `pip install uv` (Python 3.14 환경)
- **OAuth 앱**: Google Cloud Console 프로젝트명 `period`, 데스크탑 앱 타입
- **Client ID**: `733934180874-jnsl47jpt73d70qfmobvnlces9jbuvr3.apps.googleusercontent.com`
- **자격증명 저장**: `~/.google_workspace_mcp/credentials/`
- **등록 명령**: `claude mcp add -s user google_workspace` (stdio, user 스코프)
- **활성 툴**: gmail, calendar (`--single-user --tools gmail calendar`)
- **상태**: 연결 완료 (`mcp__google_workspace__*` 툴 사용 가능)

---

## 완료된 작업 이력

| 날짜 | 작업 | 결과 |
|------|------|------|
| 2026-04-04 | CLAUDE.md 전면 작성 (34줄→233줄) | GitHub push (commit: 6192e99) |
| 2026-04-04 | sitemap 링크 버그 수정 (`/period-site/sitemap.xml` → `/sitemap.xml`) | GitHub push (commit: d0f41f9) |
| 2026-04-04 | Make.com JSON 에러 수정 (title 특수문자로 인한 JSON 파싱 오류) | replace()로 따옴표/줄바꿈 이스케이프 |
| 2026-04-04 | Google Analytics (G-P0ZT2K5V2F) 세팅 확인 | 정상 |
| 2026-04-04 | 네이버 사이트 인증 확인 | 정상 |
| 2026-04-04 | Formspree → Telegram 연동 확인 | 정상 (endpoint: xgopvzoe) |
| 2026-04-04 | GitHub 토큰 영구 저장 | ~/.git-credentials |
| 2026-04-04 | Claude bypassPermissions 설정 | ~/.claude/settings.json |
| 2026-04-05 | Google Workspace MCP 윈도우 설치 (uv, google_workspace_mcp 클론, OAuth 앱 생성) | `claude mcp add -s user` 등록 완료 |
| 2026-04-05 | Google Workspace MCP 연결 확인 | `mcp__google_workspace__*` 툴 정상 로드 |
| 2026-04-05 | Gmail 마케팅 메일 17개 trash 이동 | `batch_modify_gmail_message_labels` 사용 |
| 2026-04-05 | Google Calendar 2개 생성 | 📋 Period. 작업로그, 📅 Period. 일정 (Python API 직접 호출) |
| 2026-04-05 | 2026학년도 영화·영상과 수시 입시 조사 | 19개교 (실기전형 16 + 학생부종합 3) |
| 2026-04-05 | Notion 영화·영상과 수시 입시 DB 생성 | 피리어드 내부 관리 하위, collection://79331095 |
| 2026-04-05 | 홈페이지 입시 일정 테이블 추가 | 입시과외 탭 (2025년 기준·26학번), commit: e33f3e8 |
| 2026-04-05 | Google Calendar 입시 이벤트 9개 등록 | 📅 Period. 일정 캘린더, 9월~12월 |
| 2026-04-05 | 19개교 입시 후기·기출·면접 질문 조사 | 로컬 저장: 영화과_입시_조사_19개교.txt |
| 2026-04-05 | Notion 블로그 초안 4편 생성 | #8 실기유형해설, #9 비용·일정·FAQ, #10 면접기출, 별첨2 학교별 분석 |
| 2026-04-05 | 홈페이지 입시 스케줄 탭 추가 | `#schedule` 탭, 19개교 카드+필터+타임라인, commit: 1c40c62 |
| 2026-04-21 | 홈페이지 전면 리뉴얼 배포 | preview.html → index.html 승격, 기존 index는 index-legacy.html로 백업(noindex), commit: 1af622b |
| 2026-04-21 | 신규 구성: 히어로 제거 · Intro 섹션 신설 | "영화입시 전문과외 피리어드입니다" + 3문단 소개, section-title 통일 |
| 2026-04-21 | 로고 영역에 "영화입시 전문과외" 태그라인 추가 | Period. 로고 옆 구분선 + 서브카피 |
| 2026-04-21 | SEO 메타 복원 | canonical/og:url `/` 로 교정, twitter card + og:image + sitemap 링크 + author 복원, naver-site-verification/gtag 유지 |
| 2026-04-21 | sitemap.xml lastmod 갱신 | 2026-03-27 → 2026-04-21 |
| 2026-04-21 | Google Search Console / 네이버 서치어드바이저 재제출 | 사이트맵 + 메인 URL 수집 요청 완료 (수동) |
| 2026-04-21 | 상담 폼 Formspree 장애 해결 | 원인: 한글 필드명(`연락처`, `상세내용`) + `email` 필드 부재 → 400 Bad Request. 영어 필드명(`phone`, `message`, `type`) + hidden email 추가로 해결. Telegram 정상 수신 확인, commit: e38c45b |
| 2026-04-21 | 푸터 이메일 통일 | `film317@naver.com` → `hhp621@naver.com`, commit: abf3e95 |

---

## 개선 과제 백로그 (GitHub Issues 연동)

> 상세 내용은 GitHub Issues에서 관리. 여기선 빠른 참조용으로만 유지.

```xml
<backlog updated="2026-04-05">

  <!-- ── 홈페이지 ── -->
  <issue id="13" label="홈페이지" priority="high" github="#13">
    <title>피리쌤 자소서·면접 전담 차별점 강조</title>
    <why>경쟁사 4곳 전부 자소서/면접 전담 없음. 현재 선생님 탭에만 묻혀 있음.</why>
    <what>홈 히어로 또는 수업 탭 상단에 2인 분업 구조 1줄 명시</what>
  </issue>

  <issue id="15" label="홈페이지" priority="high" github="#15">
    <title>수강생 후기 추가 — 노션 후기 DB 반영</title>
    <why>우디쌤 69개 vs 피리어드 4개. 공개 동의 케이스 확인 후 추가 가능.</why>
    <what>노션 후기 DB에서 공개 가능 케이스 확인 필요 (직접 판단 필요)</what>
    <notion>331d5f8a-a11b-808b-98a5-f24749e316df</notion>
  </issue>

  <!-- ── 콘텐츠 ── -->
  <issue id="14" label="콘텐츠" priority="high" github="#14">
    <title>posts.json 업데이트 — 블로그 발행완료 글 반영</title>
    <why>노션 블로그 DB ~20개 중 사이트엔 4개만 표시. 발행완료 글 누락.</why>
    <what>노션 DB 상태=발행완료 목록 확인 후 posts.json 추가</what>
    <notion>collection://32cd5f8a-a11b-8157-a974-000be1b8bc37</notion>
  </issue>

  <issue id="16" label="콘텐츠" priority="medium" github="#16">
    <title>블로그 글 발행 — SWOT 기반 4편 우선 작성</title>
    <why>자소서/면접·예고입시 콘텐츠 공백 시장. SEO 유입 + 차별점 소구.</why>
    <what>
      1. 영화과 입시, 자소서가 당락을 가른다 (피리쌤 전문성)
      2. 1:1 과외 vs 학원 비교
      3. 예고 입시 준비법 (한림·안양)
      4. 합격생 스토리 시리즈 (익명)
    </what>
  </issue>

  <!-- ── 경쟁사/전략 ── -->
  <issue id="17" label="경쟁사" priority="low" github="#17">
    <title>경쟁사 DB 보완 — 개인 과외 강사·온라인 플랫폼 추가</title>
    <why>현재 4곳(레슨포·우디쌤·포커스·필름스테이션)만 정리됨. 개인 강사 미조사.</why>
    <what>네이버 블로그 개인 강사, 클래스101·탈잉 플랫폼 조사</what>
    <notion>f1f53d3a-8ae7-480e-8a87-86115aa74f92</notion>
  </issue>

  <issue id="18" label="전략" priority="medium" github="#18">
    <title>인스타그램 개설 및 SNS/온라인 수업 방향 결정</title>
    <why>경쟁사 3곳 인스타 운영 중. 온라인 수업은 SWOT 약점으로 명시됨.</why>
    <what>인스타 개설 여부, 온라인 수업 여부 — 직접 결정 필요</what>
  </issue>

</backlog>
```

---

## 경쟁사 인사이트 요약

```xml
<competitors updated="2026-04-05">
  <key-finding>경쟁사 4곳 전부 자소서/면접 전담 강사 없음 — 피리어드 최강 차별점</key-finding>
  <key-finding>우디쌤이 콘텐츠(유튜브+틱톡+블로그+인스타) 전략으로 검색 상위 점령 중</key-finding>
  <key-finding>레슨포 수업료 월 45만원(그룹) — 피리어드 1:1 프리미엄 포지셔닝 유지 가능</key-finding>
  <key-finding>필름스테이션: 동작구 인근, 평점 3.7 — 지역 경쟁에서 피리어드 우위 가능</key-finding>
  <swot-gap>SWOT 강점에 '수업료 투명 공개' 기재되어 있으나 현재 사이트는 비공개 운영 — 전략 방향 통일 필요</swot-gap>
  <notion-db>f1f53d3a-8ae7-480e-8a87-86115aa74f92</notion-db>
  <notion-swot>338d5f8a-a11b-81bf-828d-ecc5aac49206</notion-swot>
</competitors>
```

---

## TODO (미완료)

### 🟡 Google 캘린더 2개 생성
- `📋 피리어드 작업로그` — Claude 세션/작업 기록용
- `📅 피리어드 일정` — 수업·사업 일정 관리용
- MCP 연결 완료, 새 대화에서 `mcp__google_workspace__manage_event` 사용

### 🟡 Gmail 정리
삭제 대상 (Formspree 상담 신청 2개는 유지):
- Make.com 마케팅 메일 7개
- Tally 메일 1개
- Google Analytics 안내 메일 1개
- MCP 연결 완료, `mcp__google_workspace__batch_modify_gmail_message_labels` 사용

### 🟢 period-site 레포 삭제
- https://github.com/period317/period-site (배포 안 되는 중복 레포)
- GitHub 웹에서 직접 삭제 (Settings → Delete repository)
