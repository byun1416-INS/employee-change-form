# employee-change-form v1.12

v1.11 기준으로 접수완료 기능을 추가했습니다.

- PDF 다운로드 버튼: 기존처럼 PDF를 사용자 PC/휴대폰에 다운로드
- 접수완료 버튼:
  1. 현재 미리보기로 PDF 생성
  2. 입력정보와 PDF를 Make Custom Webhook으로 전송
  3. Make에서 Google Drive Upload a file로 저장 가능
- 업로드 주소는 `upload-config.js` 한 줄만 설정하면 됩니다.
- v1.11의 양식/서명 위치/선 복구 설정은 그대로 유지했습니다.

필수 업로드 파일:
`index.html`, `config.json`, `upload-config.js`, `svgs/`, `lines/`
