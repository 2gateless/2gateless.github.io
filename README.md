# `2gateless.github.io` — 안드로이드 TWA 앱 도메인 인증 저장소

> [!CAUTION]
> **이 리포지토리를 삭제하거나 GitHub Pages 설정을 끄지 마세요.**  
> 삭제할 경우 [`2gateless/bluelaw`](https://github.com/2gateless/bluelaw) 안드로이드 앱 실행 시 상단에 Chrome 브라우저 주소창이 다시 나타나게 됩니다.

---

## 1. 생성 목적

[`2gateless/bluelaw`](https://github.com/2gateless/bluelaw) 웹앱을 PWABuilder로 패키징한 **안드로이드 앱(TWA, Trusted Web Activity)** 이 브라우저 주소창 없이 **네이티브 앱처럼 전체 화면**으로 실행되도록 **Digital Asset Links(디지털 자산 링크)** 인증 파일을 제공하기 위한 저장소입니다.

### 왜 별도 리포지토리가 필요한가요?
- 안드로이드 OS는 앱의 소유권을 검증할 때 하위 경로(`/bluelaw/`)가 아닌 **도메인 최상단 루트**(`https://2gateless.github.io/.well-known/assetlinks.json`)만 조회합니다.
- GitHub Pages에서 도메인 최상단 루트를 담당하는 저장소 이름은 반드시 **`<아이디>.github.io`** (`2gateless.github.io`)여야 하므로, 이 전용 리포지토리를 생성해 운영합니다.

---

## 2. 포함된 파일

| 파일 경로 | 역할 |
| :--- | :--- |
| `.well-known/assetlinks.json` | 안드로이드 앱(`io.github.app_2gateless.twa`)과 서명 키(SHA-256 지문)가 본인 소유임을 증명하는 인증 파일 |
| `.nojekyll` | GitHub Pages가 점(`.`)으로 시작하는 `.well-known` 폴더를 무시하지 않고 정상 배포하도록 하는 빈 설정 파일 |

- 확인 URL: https://2gateless.github.io/.well-known/assetlinks.json

---

## 3. 주의 사항

- **다른 리포지토리와의 영향**: 이 저장소는 루트 경로만 담당하므로 `https://2gateless.github.io/bluelaw/` 등 다른 프로젝트 리포지토리의 GitHub Pages 동작에 영향을 주지 않습니다.
- **폴더명 충돌 주의**: 이 저장소 안에 다른 리포지토리 이름과 동일한 폴더(예: `bluelaw/`)를 만들지 마세요.
- **서명 키 변경 시**: 만약 안드로이드 앱을 새 서명 키(Keystore)로 다시 빌드하게 되면, `.well-known/assetlinks.json`의 `sha256_cert_fingerprints` 값도 새 키에 맞게 함께 갱신해야 합니다.
