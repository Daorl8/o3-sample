# CHANGELOG — O³ BAKERY CAFE (오쓰리)

## v0.2 — 2026-09-25 (수정)
- **강아지 로고 찌그러짐 방어**: 히어로·푸터 강아지 img에 `aspect-ratio:1/1; object-fit:contain; height:auto` 명시(파일 520×520·attr 92×92 모두 정사각이라 왜곡 원인 미재현 → 어떤 CSS 환경에서도 안 눌리게 방어적 고정).
- **Find Us 구글 지도 추가**: 키 없는 embed iframe(`google.com/maps?q=경남 거제시 아주1로 8&output=embed`) 삽입. 1px 잉크 보더·16:10·컬러(grayscale 미적용). 도로명 주소 확보로 핀 정확도 확보. ※매장이 포항이 아니라 **경남 거제시**임(기존 문서 포항 표기 오류 → 교정).
- QA: 태그균형(div30·section4·iframe1·figure1·footer1) OK.

## v0.3 — 2026-09-25 (리뷰 반영)
- **실주소 본문 노출**(리뷰 최우선): Find Us·footer에 "경남 거제시 아주1로 8" 표기(랜드마크 "스타타워 2차 1층"은 보조로). 손님이 읽기/복사 가능.
- **JSON-LD PostalAddress 추가**: 경상남도·거제시·아주1로 8 1층·KR (SEO).
- **메뉴 안내 보강**: 홀케이크 2일 전 주문 문구 추가(가격 문의 안내는 기존 유지).
- 지도=구글 임베드 **유지**(네이버 임베드는 NCP API 키·도메인 등록 필요, 비용 회피 목적). 네이버 place 버튼은 정밀 핀 담당.
- **보류(도메인 확정 후 납품 단계)**: canonical·og:url·절대경로 og:image / 폰트 self-host. ← 도메인 없이는 확정 불가라 미이행.

## v0.4 — 2026-09-26 (메뉴 사진 교정)
- **시그니처 6번째 카드 교체**: "딸기 타르트"(사진이 실제로는 크루아상 생지 성형 컷 — 불일치) → **무화과 캉파뉴(Fig Campagne)**. IG 원본 619845979(무화과·호두 캉파뉴 단면)를 900×900 webp로 slug(o3-campagne.webp). 빵 하드계열 추가로 메뉴 다양성↑.
- 구 이미지 o3-tart-strawberry.webp = 마운트 삭제 불가라 .assetsignore로 배포 제외.

## v0.5 — 2026-09-26 (한글 세리프 궁서 트랩 수정)
- **`--serif` 체인에 Noto Serif KR 추가**: `"Cormorant Garamond", "Noto Serif KR", "Apple SD Gothic Neo", serif`. 기존 체인엔 웹 로드 한글 세리프가 없어(Apple SD Gothic Neo=맥 전용) Windows에서 한글 헤딩·리드가 궁서/바탕으로 깨졌음. CDN에 `family=Noto+Serif+KR:wght@500;600`(쓰는 굵기만 스코프) 추가.
- 영향 셀렉터: `.hero h1`·`.hero .lead`·`.sec-head h2`·`.intro h2`·`.iblock h3`·`.site-foot .big` 등 한글 다수.
- LESSONS.md §22로 규칙화(라틴 세리프 헤딩 쓸 때 한글 세리프 체인 기본 포함). 납품 시 서브셋 self-host 전환 예정.

## v0.1 — 2026-09-25 (최초 시안)
- **이미지 큐레이션**: IG 원본 60장에서 로고(O³ BAKERY CAFE 워드마크)+식빵 강아지 캐릭터+제품 실사진 6종(크루아상·에그타르트·딸기 생크림 케이크·당근 케이크·청포도 케이크·딸기 타르트) 선별. 리포스트(단추과자상점·우고빵·OVENDAYS·YP)·텍스트오버레이(공지·이벤트·기념일)·불쇼 제외. webp `o3-` slug + favicon + og jpg.
- **디자인**: 화이트+블랙 모던 미니멀(심플/큐트 지향). 로고의 우아한 세리프에 맞춰 Cormorant Garamond(디스플레이)+Pretendard(본문). 순수 B&W, 얇은 헤어라인·1px 그리드. **강아지 캐릭터는 히어로·푸터에만 절제 사용**.
- **빌드**: 단일 index.html — 헤더·히어로(O³ 로고타입+강아지)·소개(직접 반죽·굽기 + 소금빵/케이크 3노트)·시그니처 6종·영업시간+오시는길·푸터. reveal+noscript+rAF, JSON-LD Bakery(영업시간·전화·place·sameAs).
- **네이버 실데이터**: place ID 1698561157 정식 지도링크·IG @o3_bakers·0507-1484-0691. 소금빵 11:30/케이크 2일전/딸기 시즌 안내.
- **QA**: 자산·태그균형·이모지0·alt10/10·lazy6/10 통과. AA 보정(뮤트 #8A8A8A→#6E6E6E=화이트5.1·섹션4.7; 잉크 18.6).
- **레포 스캐폴드**: wrangler.toml·.assetsignore·STRUCTURE.md.

### 보류/확인
- ⚠️정식 도로명 주소 미제공("스타타워 2차 1층"만) → place 링크로 보완. 금·토 영업시간(네이버 추석표기로 가려짐) 사장님 확인. 가격 미제공→문의 안내.
- og:url·canonical·절대 og:image = 도메인 확정 후. 폰트 self-host = 납품. 헤드리스 렌더 미실행→정적 QA 갈음.
