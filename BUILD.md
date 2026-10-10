# 결 — 앱 빌드 방법

## 내 폰에서 써보기 (APK)
1. GitHub에서 새 저장소를 만들고 이 폴더 내용을 그대로 올립니다.
2. 저장소의 Actions 탭 → "Build APK" 실행이 끝나길 기다립니다.
3. 실행 결과의 Artifacts에서 gyeol-apk를 받아 압축을 풀면 app-debug.apk가 있습니다.
4. 폰으로 옮겨 설치합니다 (출처를 알 수 없는 앱 설치 허용 필요).

## 스토어 출시
- Google Play: 서명한 AAB가 필요합니다 (android 폴더에서 ./gradlew bundleRelease). 개발자 계정 등록(1회 25달러).
- App Store: Mac + Xcode에서 npx cap add ios 후 빌드. Apple Developer Program(연 99달러).
- 공통: 앱 아이콘/스플래시(@capacitor/assets), 개인정보처리방침 URL, 스토어 스크린샷.
- 현재 폰트는 Google Fonts를 불러오므로, 출시 전 폰트 파일을 앱에 포함시키는 것을 권장합니다.
