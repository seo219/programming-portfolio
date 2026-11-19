<div align="center">

# 신이서 · 프로그래밍 포트폴리오
**웹·데스크톱·데이터·장치 제어를 코드로 연결합니다.**

Python · JavaScript / TypeScript · React · Java · C# · MSSQL · Arduino

[GitHub](https://github.com/seo219) · [자동화 포트폴리오](https://github.com/seo219/fa-automation-portfolio)

</div>

---

## 소개

GitHub 프로젝트와 Drive에 보관한 코드를 개발 분야별로 정리했습니다. 화면과 데이터 저장, 비동기 처리, 상태 관리, 좌표 계산, 외부 장치 통신을 실제 코드와 연결해 보여줍니다.

**프로젝트·교육 실습·팀 작업·자료 사본을 구분**했고, 직접 구현한 범위가 확인되지 않은 내용을 단독 성과로 주장하지 않습니다.

## 프로젝트

| 분야 | 내용 | 상세 |
|---|---|---|
| React 일정 관리 | 캘린더·할 일 CRUD·템플릿·빈 시간 계산 | [프로젝트](scheduler.md) |
| Python 스마트 카페 | UI·Service·Repository 분리, FEFO 재고·주문·통계 | [프로젝트](smart-cafe.md) |
| Python 객체지향 | Book/Library, 등록·검색·대출·반납·JSON | [프로젝트](library.md) |
| Java · C# · MSSQL | Swing·소켓·스레드, Windows Forms·비동기 DB·프로시저 | [Drive 코드](desktop-development.md) |
| JavaScript · React | 타이머·스톱워치·장바구니·환율·날씨, 일정 앱 이전 버전 | [Drive 코드](web-practice.md) |
| AI · 데이터 · OpenCV | 곤충 탐지 실험, 데이터 도구, Colab, 영상 처리 실습 | [실험·학습](ai-data-practice.md) |
| 로봇 소프트웨어 | SO-101 Controller·Backend·Grasper, 독립 SlotRobot·Arduino | [구조·테스트](robot-software.md) |
| Indy Python 제어 | TCP 좌표·팔레타이징·PLC 핸드셰이크 | [코드 분석](robot-python.md) |

## 실제 소스와 자료

Drive의 **576개 코드·설정·문서 파일**을 12개 ZIP으로 정리해 이 저장소에 업로드했습니다. HTML/CSS, 프로젝트 설정, 노트북과 테스트가 포함되어 있어 파일 수를 개발 성과 수로 환산하지 않습니다.

[전체 소스 다운로드 목록](materials.md) · [파일별 경로·SHA-256](source-manifest.csv) · [곤충 탐지 발표 PDF](evidence-insect-study.pdf)

GitHub의 원본 프로젝트도 유지했습니다: [scheduler-app](https://github.com/seo219/scheduler-app), [Py_Cafe](https://github.com/seo219/Py_Cafe), [OOP](https://github.com/seo219/OOP), [AI_PGM](https://github.com/seo219/AI_PGM), [neuromeka_Py](https://github.com/seo219/neuromeka_Py).

## 코드에서 확인할 역량

| 관점 | 사례 |
|---|---|
| 계산 절차 설계 | 일정 구간 정렬·범위 제한·빈 시간 추출 |
| 책임 분리 | UI → CafeService → JSON Repository |
| 상태 일관성 | 주문 전 재고 검사·예외 시 메모리 복구 |
| 비동기 처리 | fetch·async/await, C# 비동기 DB 호출 |
| 객체와 데이터 | Book 직렬화·역직렬화, 슬롯별 말 수 추적 |
| 장치 추상화 | Backend·Grasper와 모의 장치를 이용한 로봇 테스트 |

## 검증

이번 정리에서는 Drive 팀 로봇 모의 테스트 **58개**, 독립 SlotRobot 테스트 **15개**가 통과했습니다. 공개용으로 정리한 ZIP에서도 다시 확인했습니다. Python 소스는 구문 검사했고, 비밀값·연락처·식별값을 제거했습니다.

웹 앱 빌드, Java/C# 전체 빌드, DB 접속, AI 학습과 실제 로봇 동작을 모두 재검증한 것은 아닙니다. Drive ZIP은 시점별 스냅샷이며 v7 최종 팀 소스 전체와 같지 않습니다.

## 자료 공개 기준

API 키·접속 비밀번호·.env·개인정보·캐시·실행 바이너리는 제외하거나 설정 자리표시자로 치환했습니다. 제3자 교안과 외부 이미지 원본은 통째로 재배포하지 않았습니다. 공개본은 원본 보존용 복제와 구분되며 로컬 설정이 필요합니다.

[반영·제외 목록](materials.md) · [출처와 검증 범위](sources.md)
