# JavaScript · React의 개발 과정
[← 포트폴리오](README.md)

## JavaScript 미니 프로젝트

[소스·HTML·CSS 50개](source-javascript.zip)

| 프로젝트 | 핵심 로직 |
|---|---|
| 타이머 | 초 단위 상태, setInterval, 시작·정지·재개·리셋, 종료 표시 |
| 확장 타이머·스톱워치 | 버튼 상태 전환, 기록 목록, 진행률, localStorage 테마 |
| 시계 | Date를 화면 시간 표시로 변환 |
| 장바구니 | Product/Cart, 항목 추가·수량 변경·삭제·합계, DOM 재표시 |
| 환율 | fetch·async/await 및 then 방식, 응답 변환·결과 표시 |
| 날씨·지도 | 도시·좌표 조회, 예보 표시, Leaflet 마커와 지도 갱신 |
| 기초 | 함수, 화살표 함수, 콜백 예제 |

원본의 외부 API 키는 공개 스냅샷에서 CONFIGURE_LOCALLY로 바꿨습니다. API 기능을 쓰려면 본인 설정이 필요합니다. 브라우저에서 실행하는 예제에 장기 비밀키를 직접 넣는 방식은 후속 개선 과제입니다.

**실행:** ZIP을 풀고 각 프로젝트의 HTML을 확인합니다. 외부 API·지도 라이브러리·오디오가 필요한 기능은 관련 리소스가 있어야 합니다. 자동 실행 검증이나 API 요청은 수행하지 않았습니다.

## React의 두 이전 버전

[React 폴더 버전 44개](source-react-legacy.zip) · [src.zip 버전 40개](source-scheduler-drive.zip)

Drive의 React/src에는 로그인·설정·목록·캘린더·입력 화면을 나눈 초기 SchedulerApp이 있습니다. 별도 src.zip에는 Router, RequireAuth, pages/services/api 구조의 일정 관리 코드가 있습니다.

GitHub의 [scheduler-app](scheduler.md)은 현재 공개 원본입니다. 세 소스는 서로 다른 시점의 스냅샷이며 이번 작업에서 임의로 병합하지 않았습니다. Drive src.zip에는 package.json 등 프로젝트 루트 파일이 없으므로 단독 npm 실행 패키지가 아닙니다. 의존성은 대응하는 프로젝트 환경을 확인해야 합니다.

## 코드 검토 관점

- 이벤트가 상태와 화면을 어떻게 바꾸는지
- 비동기 요청의 성공·실패를 어떻게 표현하는지
- 시간 계산과 사용자 입력을 어디서 검증하는지
- UI·서비스·외부 API 모듈을 어떻게 나누는지

프로젝트별 실제 사용 기술와 현재 제약을 함께 보여주고, 소스가 있다고 배포·운영·모든 기능 시험이 완료됐다고 표현하지 않습니다.
