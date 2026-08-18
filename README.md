# employee-change-form v17

중요 버그 수정 버전입니다.

원인:
- v15와 v16에서 `config.json`의 위한씨엠 좌표와 21px 설정은 수정됐지만,
- 실제 `index.html`은 `config.json`을 읽지 않고 내부에 박혀 있는 `CONFIG` 배열을 사용하고 있었습니다.
- 그래서 위한씨엠 보험료 / 신청인 이름 / 서명 / (인) 좌표 수정과 일부 크기 설정이 실제 화면에 반영되지 않았습니다.

v17 수정:
- 현재 `config.json` 전체 내용을 `index.html`의 `CONFIG`에 다시 삽입
- 위한씨엠 전용 보험료 / 이름 / 서명 / (인) 좌표 실제 반영
- 전체 자동입력 21px 설정 실제 반영
- 대원에스테이트 교체 SVG 유지
- 사용자 수정 SVG 20개 그대로 유지

GitHub에는 `index.html`, `config.json`, `svgs/` 폴더 전체를 덮어쓰세요.
