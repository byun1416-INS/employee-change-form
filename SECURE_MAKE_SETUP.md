# v1.21 보안형 전환 순서

## 목표
- 위탁사 선택 드롭다운 제거
- 전용 URL의 `key`로 위탁사 자동 확정
- 공개 GitHub에는 20개 SVG/line 파일을 두지 않음
- 입사: 인증된 위탁사의 양식만 불러오기 + 서명 + PDF
- 퇴사: 양식/미리보기/서명/PDF 없음

## 1. Google Drive
비공개 폴더 하나를 만들고 각 위탁사별 아래 2개 파일을 올립니다.
- 원본 SVG: 예) `wihan_cm.svg`
- 선 복구 SVG: 예) `wihan_cm_line.svg`

공유 설정은 '제한됨'으로 유지합니다.

## 2. Make Data Store
Data Store 이름 예: `employee_form_access`

필드:
- key: access_key (Data Store Record Key로 사용하는 것을 권장)
- company_name
- slug
- active
- drive_svg_file_id
- drive_line_file_id
- config_json

`make_datastore_records.csv`에 20개 보안키와 각 회사 config_json을 만들어 두었습니다.
Drive에 파일을 올린 뒤 각 행의 `drive_svg_file_id`, `drive_line_file_id`만 채우면 됩니다.

## 3. 인증/양식 제공 Make Scenario
순서:
1. Webhooks > Custom webhook
2. Data Store > Get a record (Record key = access_key)
3. active 확인
4. Google Drive > Download a file (drive_svg_file_id)
5. Google Drive > Download a file (drive_line_file_id)
6. Webhooks > Webhook response

응답 JSON 예:
{
  "ok": true,
  "company": "{{company_name}}",
  "config": {{config_json}},
  "svg_data_url": "data:image/svg+xml;base64,{{SVG 파일 데이터를 base64로 변환}}",
  "line_data_url": "data:image/svg+xml;base64,{{line 파일 데이터를 base64로 변환}}"
}

응답 헤더:
- Content-Type: application/json
- Access-Control-Allow-Origin: *

## 4. secure-config.js
인증용 Custom Webhook 주소를 `INS_AUTH_WEBHOOK_URL`에 넣습니다.
접수용 주소를 `INS_UPLOAD_WEBHOOK_URL`에 넣습니다.

## 5. 테스트 후에만 GitHub 공개 양식 삭제
v1.21 인증 테스트가 끝나기 전에는 현재 운영 v1.20을 건드리지 마세요.
테스트 완료 후 GitHub 저장소의 `svgs/`, `lines/`, 공개 `config.json`을 제거하고
v1.21의 `index.html`, `secure-config.js`만 배포합니다.

## 전용 링크
`위탁사별_전용링크_20개.txt`에 20개 링크를 생성했습니다.
