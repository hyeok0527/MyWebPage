# 권혁의 개인 포트폴리오

Hugo와 Blowfish를 활용해 자기소개와 프로젝트 경험을 정리한 사이트입니다.

- 공개 사이트: https://hyeok0527.github.io/MyWebPage/
- 저장소: https://github.com/hyeok0527/MyWebPage
- Actions: https://github.com/hyeok0527/MyWebPage/actions

## 주요 수정 위치

| 대상 | 경로 |
|---|---|
| 홈 본문 | `site/portfolio-content/_index.md` |
| 자기소개 | `site/portfolio-content/about/index.md` |
| 프로젝트 목록 | `site/portfolio-content/projects/_index.md` |
| 프로젝트 상세 | `site/portfolio-content/projects/mywebpage/index.md` |
| 프로필 | `site/config/_default/languages.en.toml` |
| 메뉴 | `site/config/_default/menus.en.toml` |
| 화면 설정 | `site/config/_default/params.toml` |
| 기본 설정·콘텐츠 경로 | `site/config/_default/hugo.toml` |
| 홈 템플릿 | `site/layouts/index.html` |
| 운영 설정 | `site/pages.json` |
| 배포 구성 | `.github/workflows/hugo-pages.yml` |

원본 예제는 `site/content/`에 보존합니다. 공개 사이트는 `contentDir = "portfolio-content"` 설정으로 새 콘텐츠만 빌드합니다. 앞으로 글을 수정할 때는 **site/portfolio-content/**를 사용하세요.
기존 언어 파일명은 en을 유지하지만 locale과 isoCode는 ko이며, 다른 예제 언어는 비활성화합니다.

## 도구 버전과 설치

기존 워크플로에 지정된 버전: Hugo Extended 0.167.0, Dart Sass 1.105.0, Python 3.12, Node.js 24, Go 1.27.1.
이는 저장소 설정에 적힌 값이며 로컬 설치·실행을 검증했다는 뜻은 아닙니다.
로컬 작업 시 각 도구의 공식 설치 안내를 따라 해당 버전을 설치하고 PATH에 추가하세요.

- Hugo: https://gohugo.io/installation/
- Sass: https://sass-lang.com/install/
- Python: https://www.python.org/downloads/
- Node.js: https://nodejs.org/en/download
- Go: https://go.dev/doc/install

## 설치 후 빌드

저장소 루트(MyWebPage 폴더)에서 실행합니다.

```bash
python .github/pages_build.py --dependencies
python .github/pages_build.py --build
```

기존 배포 스크립트가 site/pages.json과 site/config/ 설정을 사용하며 결과를 public/에 만듭니다.
일부 환경에서 python 명령이 없다면 python3를 사용하세요.
빌드 후 로컬 확인은 다음과 같습니다.

```bash
cd site
hugo server --config pages.json --baseURL http://localhost:1313/MyWebPage/ --appendPort=false
```

브라우저에서 http://localhost:1313/MyWebPage/ 를 엽니다. 로컬 실행 명령은 적용 후 사용자 환경에서 확인해야 합니다.

## 수정과 재배포

1. 콘텐츠의 `[직접 입력: ...]`을 실제 내용으로 교체하고 사실관계를 검토합니다.
2. 변경 내용을 diff로 확인하고 의미 있는 작업 단위로 commit합니다.
3. main에 push합니다. 다른 브랜치에서 작업했다면 main에 병합합니다.
4. Actions에서 해당 커밋의 build와 deploy 성공을 확인합니다.
5. 공개 사이트에서 소개, 프로젝트, 메뉴와 자산이 정상인지 확인합니다.

GitHub Settings → Pages → Source는 GitHub Actions를 사용합니다.
수업 제공 준비 스크립트를 재실행해 사이트를 다시 생성하면 사용자 수정이 덮어써질 수 있으므로 일반 콘텐츠 수정에는 재실행하지 않습니다.

## 검증 계획

아래는 검사 계획이며 완료 기록이 아닙니다. 실제 검사 후 결과와 근거를 보고서에 기록하세요.

- 배포: main push 자동 실행, Hugo 빌드, Pages 배포 상태.
- 경로·자산: 내부 URL 직접 접속과 새로고침, CSS·이미지 로딩, localhost 잔존 여부.
- 메뉴·링크: 소개·프로젝트·GitHub·홈 복귀와 뒤로 가기.
- 반응형: 1440px·768px·390px, 폭 변경, 200% 확대.
- 키보드: Tab 초점, Enter 실행, 메뉴 닫기와 초점 이동.
- 언어: 생성된 HTML의 lang이 ko 계열인지 확인.

프로젝트 대표 이미지와 본문 이미지를 사용합니다. 이미지 표시, 화면 크기 대응과 대체 설명을 검사합니다.

## 출처와 AI 활용

- 테마: Blowfish — https://github.com/nunocoracao/blowfish
- 원본 LICENSE 및 필요한 저작권 고지는 보존합니다. 테마 자산과 외부 자료는 해당 이용 조건을 따릅니다.
- 사이트 준비·배포: 수업 제공 Python 스크립트와 기존 워크플로를 활용합니다.
- 개인 콘텐츠: 본인의 실제 활동을 바탕으로 작성하고 사실관계를 확인합니다.
- AI 도움: BAZE Mindlogic Super Agent를 활용해 파일 구성, 문구 초안, 설정 정리와 문제 점검을 지원받았습니다. 테마와 배포 스크립트를 직접 처음부터 개발한 것으로 주장하지 않습니다.
- AI 활용 날짜·실제 요청·채택 판단·반영 경로·검증 결과는 제출 보고서에 기록합니다. 모델명 미표시 시 미표시로 적습니다.

## 제출 기록

사이트 코드 수정 완료 커밋을 기준으로 기록하며, 이후 README 제출 기록만 수정한 커밋은 기준에서 제외합니다.

### 최종 코드와 배포
- 기준 브랜치: main
- 최종 코드 전체 SHA: 35711c04a1e40ea23bbcd3e46c37bbbc756cb479
- 커밋 링크: https://github.com/hyeok0527/MyWebPage/commit/35711c04a1e40ea23bbcd3e46c37bbbc756cb479
- 해당 커밋의 Actions 실행 링크: https://github.com/hyeok0527/MyWebPage/actions/runs/42219049844
- 빌드·배포 결과: 성공
- 공개 사이트: https://hyeok0527.github.io/MyWebPage/

### 실제 작업 환경
- 운영체제·버전: MacOS 27.2(26B123)
- 편집기: Visual Studio Code
- Git 버전: git version 2.54.0 (Apple Git-157)
- 로컬 Hugo 실행 여부·버전: 로컬 미실행
- 배포 방식: GitHub Actions를 통한 Hugo 빌드 및 GitHub Pages 배포

### 최종 검증
실제로 확인한 항목만 정상 또는 문제 있음으로 바꾸고 근거를 적습니다.

| 영역 | 결과 | 확인할 내용 |
|---|---|---|
| 빌드·배포 | 정상 | 기준 커밋과 Actions 실행의 SHA 일치 및 전체 실행 성공 확인 |
| 링크·이미지 | 미검증 | 메뉴, 직접 접속, 새로고침, 대표·본문 이미지 |
| 반응형 | 미검증 | 실제 기기 또는 개발자 도구 화면 폭 기록 |
| 키보드 | 미검증 | Tab 초점과 Enter 실행 |
| 스크롤 | 미검증 | 빠른 스크롤 후 되튐, 최상단 이동 |
| 언어·확대 | 미검증 | HTML lang, 200% 확대 시 잘림 |

- 검증 일시: 2026년 11월 6일 오후 9시 47분 (KST)
- 브라우저·기기: Safari / MacBook Air M5
- 남은 문제·미검증 항목: Safari에서 확인한 범위 내 발견된 문제는 없음. 모바일 실제 기기, 다른 브라우저, 키보드 탐색 및 200% 확대는 미검증.
- 남은 문제·미검증 항목: 스크롤 시 간헐적인 버벅임이 있어 추가 개선이 필요함. 모바일 실제 기기와 다른 브라우저에서의 동작은 미검증.


## 설치 후 빌드

저장소 루트(MyWebPage 폴더)에서 실행합니다.

```bash
python .github/pages_build.py --dependencies
python .github/pages_build.py --build
```

기존 배포 스크립트가 `site/pages.json`과 `site/config/` 설정을 사용하며 결과를 `public/`에 만듭니다.
일부 환경에서 `python` 명령이 없다면 `python3`를 사용하세요.

로컬 확인 명령은 다음과 같습니다. 이 프로젝트에서는 로컬 Hugo 실행을 검증하지 않았으며, 실제 빌드·배포는 GitHub Actions를 사용했습니다.

```bash
cd site
hugo server --config pages.json --baseURL http://localhost:1313/MyWebPage/ --appendPort=false
```

브라우저에서 http://localhost:1313/MyWebPage/ 를 엽니다.

