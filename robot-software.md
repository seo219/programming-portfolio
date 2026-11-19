# 로봇 소프트웨어 · 설계와 검증
[← 포트폴리오](README.md)

## 소스 자료

[윷놀이 팀 소스 스냅샷 178개](source-yutnori-team.zip) · [독립 로봇 도구 11개](source-robot-tools.zip) · [Arduino 24개](source-arduino.zip)

### 윷놀이 팀 로봇 모듈

Drive ZIP의 src/robot에는 다음 역할이 나뉘어 있습니다.

| 구성 | 책임 |
|---|---|
| RobotController | 슬롯 이름을 이동 절차로 연결, 동작 전 설정 검사, 성공 후 말 수 갱신 |
| Grasper / ScriptGrasper | 집기·놓기 전략과 파지 확인 |
| SlotTracker | 대기 칸 한 개 이송·판 위 업힌 말 전체 이송, 빈 칸·용량 초과 검증 |
| Backend / LeRobotBackend | 장비 관찰·명령, 속도에 맞춘 보간, 오차·타임아웃 확인 |
| FakeBackend | 실제 장비 없이 명령과 상태를 검증 |

하드웨어 실패 시 컨트롤러는 False를 반환하고 말 수 기록을 바꾸지 않습니다. 설정·자세 미측정 오류는 동작 전에 구분합니다. LeRobot은 연결할 때 불러와 라이브러리가 없는 PC에서도 모의 백엔드를 이용한 테스트가 가능하도록 했습니다.

코드 docstring에는 로봇 모듈 담당이 신이서로 기재되어 있습니다. 전체 게임·AI·비전·LLM 코드는 팀 구성으로 제공하며 모두 개인 단독 구현으로 표현하지 않습니다.

### 독립 SlotRobot 도구

SlotRobot API는 plan·connect·move·home·close와 컨텍스트 관리를 제공합니다. plan은 장비 연결 없이 경로를 확인할 수 있습니다. 동작은 HOME → 출발 접근 → 집기 → 확인 → 도착 → HOME 흐름이며, 빈 파지·경로·관절 범위·보정 불일치를 검사합니다.

독립 도구의 원시 엔코더 자세 형식과 팀 저장소의 자세 형식은 다릅니다. 설정을 서로 덮어쓰면 안 됩니다. 이 도구의 README는 실제 로봇 시험 전 상태임을 명시합니다.

## 실제 실행한 테스트

| 코드 | 명령·범위 | 결과 |
|---|---|---|
| 팀 스냅샷 | pytest: robot_backend / robot_config / robot_grasp / robot_slots | **58 passed** |
| 독립 도구 | unittest discover: test_robot_api / test_slot_robot | **15 passed** |

실제 Python 3.13 환경에서 모의 장치 테스트 73개를 실행했습니다. 장비를 연결하지 않았고 전체 팀 테스트나 v7 최종 코드 전체의 통과를 의미하지 않습니다. 공개 ZIP의 로봇 설정·코드에 대해서도 동일 범위를 다시 확인했습니다.

## 버전의 한계

Drive 팀 ZIP은 v7 발표·결과보고서 이전 상태입니다. v7의 손목 카메라 보정과 실제 게임 85/86 성공 보고는 발표·보고서 근거이며, 이 ZIP에 최종 구현이 전부 들어 있다고 주장하지 않습니다.

자동화 관점의 동작 과정과 실물 시험 결과는 [FA 포트폴리오](https://github.com/seo219/fa-automation-portfolio)에서 확인할 수 있습니다.

## Arduino 통신

24개 스케치에는 LED·센서·RGB PWM·Bluetooth·시리얼 읽기/쓰기·명령 파싱이 있습니다. 0613_protocol은 #로 시작하고 @로 끝나는 메시지를 읽어 LED ON/OFF와 MOTOR 속도(0~255)를 처리합니다.

정상 메시지와 값 범위를 검사하지만 최대 수신 길이·수신 타임아웃·누락 구분자 처리는 개선 과제입니다. Arduino 보드 컴파일·실물 통신 시험은 수행하지 않았습니다.
