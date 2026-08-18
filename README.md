# employee-change-form

회사종합보험 직원변경 신청 웹폼 프로토타입입니다.

## 기능
- 위탁사 20개 선택
- 위탁사별 원본 취업규칙동의서 자동 표시
- 단지명/직책/성명/생년월일/변경일/보험료 실시간 반영
- 마우스/터치 전자서명
- 완성 동의서 PDF 다운로드
- 퇴사 선택 시 입사용 직급/동의서/서명 영역 숨김
- 대한종합개발 선택 시 전화번호/주소 추가 입력

## 배포
GitHub Pages에서 main / (root)로 배포합니다.

## Google Sheets 연동
현재 `접수완료`는 테스트용으로 브라우저 localStorage에 저장합니다. 다음 단계에서 Google Apps Script 또는 Make Webhook URL을 연결하면 Google Sheets 기록과 PDF 저장을 자동화할 수 있습니다.
