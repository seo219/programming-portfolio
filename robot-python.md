# Python 로봇 제어 · 외부 장치와 동기화

[← 포트폴리오](README.md) · [원본 저장소](https://github.com/seo219/neuromeka_Py)

## 개발 관점의 핵심

| 코드 | 구조 |
|---|---|
| [gripper.py](https://github.com/seo219/neuromeka_Py/blob/main/gripper.py) | 좌표 생성·그리퍼 출력·이동 명령·완료 대기를 함수로 분리 |
| [pc_plc_robot.py](https://github.com/seo219/neuromeka_Py/blob/main/pc_plc_robot.py) | PLC 요청 비트 감시, 로봇 모션, 완료 비트 반환 |
| [25repeat.py](https://github.com/seo219/neuromeka_Py/blob/main/25repeat.py) | 행·열 인덱스로 25개 위치를 만들고 인접 위치 이송 |

## 좌표 생성

팔레타이징은 기준 자세를 복사해 층·행·열 오프셋을 더합니다. 접근점은 TCP Z 방향 벡터를 사용해 계산하며, 좌표 계산과 실제 이동 명령을 나눕니다.

## 완료 확인

gripper.py는 명령 전 motion_id를 저장합니다. 새 모션 또는 이동 중 상태를 확인한 뒤 목표 도달과 이동 종료를 확인하고, monotonic 시간 기준 제한을 넘으면 TimeoutError를 발생시킵니다.

## PLC 핸드셰이크

M100 시작 요청 → HOME/ZERO 이동 → 목표 도달 → M101 완료 펄스 → M100 OFF 대기 순서입니다. 요청이 계속 ON인 동안 반복 실행되지 않도록 해제 대기를 둡니다.

## 실행 조건

장비 통신 정보, TCP·툴 프레임, DO 채널과 실제 작업 좌표가 필요합니다. SDK·장비 호환성은 별도로 확인해야 합니다. 25repeat.py는 기준 좌표 값이 비어 있어 그대로는 구문 실행할 수 없습니다.

외부 장치 동작은 이번 정리에서 실행하지 않았습니다. FA 관점의 설명과 별도 SO-101 팀 프로젝트는 [FA 포트폴리오](https://github.com/seo219/fa-automation-portfolio)에서 확인할 수 있습니다.


## Drive SO-101 코드 추가

기존 Indy 실습과 별도로 [SO-101 팀 모듈·독립 도구·Arduino](robot-software.md)를 추가했습니다. 장치와 설정 형식이 다르므로 구분합니다.
