# 주재원 자녀 수학 과외 — 랜딩 페이지

해외 주재원 자녀의 **귀국 대비 1:1 온라인 수학 과외** 상담 신청 페이지입니다.
빌드 도구 없이 `index.html` 하나로 동작합니다.

- 배포 주소: <https://yj0084.github.io/>  (GitHub Pages · main 브랜치 root)
- 상담 채널: 카카오톡 **juuws** · 이메일 **yjp0084@gmail.com**

---

## 파일 구성

| 파일 | 설명 |
| --- | --- |
| `index.html` | 페이지 전체 (CSS·JS 포함, 외부 의존은 Pretendard 웹폰트 하나) |
| `assets/reviews/review-01~08.jpg` | 실제 후기·성적 캡처 (개인정보 가림 처리 후 크롭) |
| `assets/kakao-qr.png` | 카카오톡 친구 추가 QR (이름이 지워진 크롭본) |
| `robots.txt` | 검색 로봇 허용 + 사이트맵 위치 |
| `sitemap.xml` | 검색엔진 제출용 사이트맵 |
| `.nojekyll` | GitHub Pages에서 Jekyll 빌드를 끄는 파일 |

## 로컬에서 보기

`index.html`을 브라우저로 열면 바로 동작합니다.
(주소가 `file://`이어도 시차 계산·신청서 생성·복사·메일 보내기가 모두 동작합니다.)

## 자주 고칠 곳

`index.html` 맨 아래 `<script>` 안의 `CONFIG` 하나만 고치면 됩니다.

```js
var CONFIG = {
  email: 'yjp0084@gmail.com',   // 상담 이메일
  kakaoId: 'juuws',             // 카카오톡 ID (복사 버튼·안내 문구에 자동 반영)
  tutorWindow: { start: 7, end: 22 }  // 한국 시간 기준 수업 가능 범위(시)
};
```

- **추천 시간 계산 기준**: 한국 시간 오전 7시~오후 10시 사이에서 후보를 만들고, 학생 현지 시각이
  방과 후(16~21시)·등교 전(6~8시 30분)·주말 낮이면 '추천', 애매하면 '가능', 학교 시간·수면 시간이면
  '어려움'으로 표시합니다. 서머타임은 기기 시계(Intl) 기준으로 자동 반영됩니다.
- **수업 시간대를 바꾸려면** `tutorWindow` 값을 수정하세요.
- **연락처·오픈채팅 주소를 추가하려면** `CONFIG`에 값을 넣고, `#contact` 영역의 안내 문구도 함께 고쳐 주세요.

### 도메인을 바꿀 때

아래 4곳의 `https://yj0084.github.io/`를 새 주소로 바꿔 주세요.

1. `index.html`의 `<link rel="canonical">`
2. `index.html`의 `og:url`
3. `index.html`의 구조화 데이터(`application/ld+json`) 안 `@id`·`url`
4. `robots.txt`의 `Sitemap:` , `sitemap.xml`의 `<loc>`

## 검색엔진 등록 (배포 후)

1. **구글 서치 콘솔** — <https://search.google.com/search-console> 에서 `https://yj0084.github.io/` 등록
   → 소유 확인은 `index.html` `<head>`의 `google-site-verification` 주석을 풀고 발급받은 값을 넣는 방식이 가장 간단합니다.
2. **네이버 서치어드바이저** — <https://searchadvisor.naver.com> 에서 사이트 등록
   → `naver-site-verification` 메타태그 값을 같은 방법으로 넣습니다.
3. 두 곳 모두 **사이트맵 제출**에 `https://yj0084.github.io/sitemap.xml` 을 넣습니다.

## 후기 이미지에 대해

후기 캡처는 학생·학부모의 이름을 가린 뒤 필요한 영역만 잘라 사용했습니다.
`assets/reviews/`의 파일을 교체하려면 같은 파일명으로 덮어쓰면 페이지가 그대로 반영됩니다.
(카드 크기는 CSS `columns` masonry라 이미지 비율이 달라도 깨지지 않습니다.)
