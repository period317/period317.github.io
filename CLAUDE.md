# 피리어드 (Period.) — 프로젝트 컨텍스트

## 세션 시작 시 필수 작업
작업 전 반드시 최신 소스를 fetch해서 시작할 것:
- 홈페이지 소스: https://github.com/period317/period317.github.io/blob/main/index.html
- posts.json: https://github.com/period317/period317.github.io/blob/main/posts.json

---

## 레포지토리 구조

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
├── index.html        ← 전체 사이트 (HTML/CSS/JS 단일 파일, 2514줄, 123KB)
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
| 무료상담 | `consultation` | Google Forms 연결 |

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
| 무료상담 Google Forms | https://forms.gle/LjpJcbkbh3YR7Zev9 |

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

블로그 포스트를 동적으로 로드하는 데이터 파일. 현재 4개 항목.

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
