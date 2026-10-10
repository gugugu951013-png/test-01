# 스토어 출시 (Google Play)

## 1. 서명 키 만들기 (PC에서 1회, 잃어버리면 안 됩니다)
JDK 설치 후 터미널(명령 프롬프트)에서:
keytool -genkey -v -keystore release.jks -alias gyeol -keyalg RSA -keysize 2048 -validity 10000
(비밀번호와 별칭 gyeol 을 기억해 두세요. release.jks 파일은 안전한 곳에 백업하세요.)

## 2. 키를 Base64 문자열로 바꾸기
- Windows PowerShell: [Convert]::ToBase64String([IO.File]::ReadAllBytes("release.jks")) | Set-Clipboard
- Mac/Linux: base64 -i release.jks | pbcopy

## 3. GitHub 저장소 Secrets 등록
저장소 Settings → Secrets and variables → Actions → New repository secret
- KEYSTORE_BASE64 : 2번에서 복사한 문자열
- KS_PASS : 키스토어 비밀번호
- KEY_ALIAS : gyeol
- KEY_PASS : 키 비밀번호

## 4. AAB 만들기
Actions 탭 → "Build Release AAB" → Run workflow → 끝나면 Artifacts의 gyeol-aab 다운로드(app-release.aab).

## 5. Play Console
개발자 계정 등록(1회 25달러) → 앱 만들기 → 테스트 트랙에 aab 업로드 → 스토어 등록정보(설명, 아이콘 512x512, 스크린샷), 개인정보처리방침 URL, 콘텐츠 등급 작성.
개인 계정이면 폐쇄 테스트 12명 x 14일 이후 프로덕션 신청.

참고: 앱 ID(com.gyeol.writing)는 capacitor.config.json에서 바꿀 수 있고, 한 번 올리면 변경할 수 없습니다.
