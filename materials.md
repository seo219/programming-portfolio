# Drive 자료와 공개 소스 안내
[← 포트폴리오](README.md)

Drive 폴더 목록을 재귀적으로 조사하고 코드와 ZIP 내부 소스를 정리했습니다. 원본 프로젝트와 교육 실습·자료 사본을 구분합니다.

## 다운로드

| 묶음 | 파일 수 | 공개 파일 |
|---|---:|---|
| Java | 30 | [source-java.zip](source-java.zip) |
| C# | 162 | [source-csharp.zip](source-csharp.zip) |
| MSSQL | 6 | [source-mssql.zip](source-mssql.zip) |
| JavaScript | 50 | [source-javascript.zip](source-javascript.zip) |
| React 초기 버전 | 44 | [source-react-legacy.zip](source-react-legacy.zip) |
| 일정 관리 Drive 버전 | 40 | [source-scheduler-drive.zip](source-scheduler-drive.zip) |
| Colab | 8 | [source-notebooks.zip](source-notebooks.zip) |
| OpenCV 실습 | 18 | [source-opencv-practice.zip](source-opencv-practice.zip) |
| 데이터 도구·설정 | 5 | [source-dataset-tools.zip](source-dataset-tools.zip) |
| Arduino | 24 | [source-arduino.zip](source-arduino.zip) |
| 윷놀이 팀 소스 | 178 | [source-yutnori-team.zip](source-yutnori-team.zip) |
| 로봇 독립 도구 | 11 | [source-robot-tools.zip](source-robot-tools.zip) |

총 **576개 코드·설정·문서 파일**입니다. 이 개수는 개발 프로젝트 수나 직접 작성한 코드 수를 의미하지 않습니다.

[파일별 경로·크기·SHA-256](source-manifest.csv) · [Python 구문 검사 기록](source-syntax-notes.json)

## 공개용 변경

인증 정보, 사설 장비 주소, 개인 연락처와 식별값을 자리표시자로 바꾸고, 노트북 출력과 사용자 메타데이터를 제거했습니다. 원본은 수정하지 않았습니다. ZIP은 검토·참고용 스냅샷이며 로컬 환경 설정을 다시 해야 합니다.

## 별도 보존하거나 제외한 자료

| 자료 | 처리 |
|---|---|
| .env, DB 접속 비밀번호, API 키, 라이선스 시리얼 | 공개본 제외·치환 |
| 이력서·입사지원서·프로필, DB 샘플 XLS | 공개 제외 |
| bin/obj/.vs, 바이너리·APK·캐시 | 빌드 결과·실행파일이므로 제외 |
| 모델 h5·대규모 CSV·외부 이미지 데이터셋 | 다운로드 중복을 피하고 소스·분석 내용만 반영 |
| 강의노트·C교안·Python교안·다른 사람 발표자료·발표양식 | 제3자 자료 전체 재배포 제외, 학습 분야만 반영 |
| Intel교육 영상 | 내용·권리 확인 없는 일괄 공개 제외 |
| Google 문서의 곤충 결과 이미지 | 확인 후 실험 설명에 반영, 이미지 묶음 재배포 제외 |
| PLC 래더·자동화 자료 | [별도 FA 포트폴리오](https://github.com/seo219/fa-automation-portfolio)에 반영 |

원본 Drive의 공유 상태는 변경하지 않았으며, 공개 문서에 비공개 Drive 링크를 싣지 않았습니다.
