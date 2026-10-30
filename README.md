# 그려라 다마고치!! — 웹 + Android 공개 개발판

## 웹 배포 (GitHub Pages)
1. 새 GitHub 저장소를 만들고 **이 폴더 안의 파일 전체**를 저장소 최상위에 업로드합니다. `.github/workflows` 폴더까지 포함해야 합니다.
2. 저장소의 **Settings → Pages → Build and deployment → Source** 에서 **GitHub Actions** 를 선택합니다.
3. Actions에서 `Deploy website` 실행 결과를 확인합니다. 주소는 `https://사용자명.github.io/저장소명/` 형태입니다.
4. Android Chrome에서는 사이트 메뉴에서 홈 화면에 추가/앱 설치가 가능합니다(지원 여부는 환경에 따라 다름).

## APK 빌드 (GitHub Actions)
1. 저장소 **Actions → Build Android APK → Run workflow** 실행.
2. 빌드 완료 후 실행 페이지 하단 **Artifacts**에서 `draw-tamagotchi-debug-apk`를 내려받습니다.
3. 압축을 풀고 `app-debug.apk`를 Android 기기에 설치합니다.
4. 이 APK는 **테스트용 debug 서명**입니다. 일반 대중 배포·Play Store 출시는 안정적인 앱 ID, 정식 릴리스 서명, 개인정보처리방침 및 공개 테스트가 추가로 필요합니다.

## 기기 저장 / 백업
게임 화면 오른쪽 아래 `💾 저장·백업`에서 JSON 파일을 내보내거나 복원할 수 있습니다. JSON에는 그림 데이터가 포함됩니다. **같은 데이터가 웹과 APK 사이에 자동 동기화되지는 않습니다.** 직접 백업 후 복원하세요.

## 주의
- 계정 및 서버가 없는 버전입니다. localStorage 용량 제한으로 그림을 많이 추가하면 저장이 실패할 수 있습니다. 충분한 실사용 테스트 후 IndexedDB로 이전하는 것이 좋습니다.
- 관리자 코드 `kakkak1208`는 기존 테스트 기능으로 남아 있으며 공개 웹에서는 누구나 소스 코드를 확인할 수 있습니다. **운영 경제 시스템에 쓰기 전에 제거/비활성화해야 합니다.**
- 기기 시계 기반 성장 시간이므로 사용자 임의 시간 변경에 영향을 받을 수 있습니다.
- 서비스 워커는 HTTPS 웹 배포에서만 작동하며, 브라우저가 캐시한 이전 파일이 잠시 남을 수 있습니다.
- 이 구성은 배포/빌드 설정 파일이며, 실제 웹 게시나 APK 빌드 완료를 뜻하지 않습니다.
