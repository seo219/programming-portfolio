<div align="center">

# 신이서 · Programming Portfolio
**문제를 데이터와 로직으로 나누고, 동작하는 프로그램으로 연결합니다.**

Python · JavaScript / TypeScript · React · Firebase · 객체지향 설계

[GitHub](https://github.com/seo219) · [FA 자동화 포트폴리오](https://github.com/seo219/fa-automation-portfolio)

</div>

---

## 소개

웹 일정 관리, Python 카페 운영 프로그램, 객체지향 도서 관리, 로봇 제어 코드를 개발 관점에서 정리했습니다. 화면에서 받은 입력이 서비스 로직과 저장 데이터로 이어지는 과정, 반복 계산을 함수로 분리하는 방식, 실패 조건을 처리하는 흐름을 중심으로 보여줍니다.

이 저장소는 기존 프로젝트의 코드와 설계를 연결하는 **문서형 프로그래밍 포트폴리오**입니다. 실제 구현과 앞으로의 개선 과제를 구분했습니다.

## 대표 프로젝트

| 프로젝트 | 핵심 내용 | 주요 기술 | 상세 |
|---|---|---|---|
| **웹 일정 관리** | 캘린더·할 일·템플릿, 빈 시간 계산과 활동 배치 | React, JavaScript, TypeScript, Firebase, Vite | [프로젝트 보기](scheduler.md) |
| **스마트 카페 운영** | 주문·원재료 재고·유통기한·통계, 계층 분리 | Python, Tkinter, JSON, unittest | [프로젝트 보기](smart-cafe.md) |
| **도서 관리** | 도서 등록·검색·대출·반납, 객체 직렬화 | Python, class, JSON | [프로젝트 보기](library.md) |
| **Python 로봇 제어** | 좌표 생성, 모션 완료 확인, PLC 통신 | Python, IndyDCP3, pymcprotocol | [코드 분석 보기](robot-python.md) |

## 코드에서 확인할 개발 역량

| 관점 | 사례 |
|---|---|
| 문제를 계산 절차로 표현 | 일정 구간 정렬·범위 제한·빈 시간 추출 |
| 책임에 따라 코드 분리 | UI → CafeService → JsonCafeRepository |
| 상태 변경의 일관성 | 주문 전 재고 검사, 예외 시 메모리 스냅샷 복구 |
| 객체와 저장 형식 연결 | Book.to_dict / Book.from_dict |
| 외부 시스템과 동기화 | PLC 요청·완료 신호, 로봇 motion_id와 타임아웃 |
| 검증 가능한 로직 | 카페 서비스 회귀 테스트 코드 |

## 추천 열람 순서

1. [웹 일정 관리](scheduler.md)에서 프런트엔드 구조와 시간 계산을 확인합니다.
2. [스마트 카페](smart-cafe.md)에서 데이터 규칙·서비스 분리·테스트 사례를 확인합니다.
3. [도서 관리](library.md)에서 객체지향과 파일 저장의 기초를 확인합니다.
4. [로봇 Python](robot-python.md)에서 외부 장치 제어 코드를 확인합니다.

## 원본 저장소

[ scheduler-app ](https://github.com/seo219/scheduler-app) · [ Py_Cafe ](https://github.com/seo219/Py_Cafe) · [ OOP ](https://github.com/seo219/OOP) · [ neuromeka_Py ](https://github.com/seo219/neuromeka_Py)

프로젝트별 실행 방법은 상세 문서에 있습니다. 이 저장소 자체는 앱이 아니며 원본 프로젝트별 환경 설정이 필요합니다.

## 확인 범위

공개 원본 코드와 README를 정적으로 검토했습니다. 이 정리 작업에서는 앱 실행·빌드·장비 동작 시험을 수행하지 않았습니다. 원본 테스트의 존재와 실제 실행 통과를 구분합니다. 팀 또는 공동 작업의 개인 기여율은 확인되지 않아 단독 구현 성과로 단정하지 않았습니다.

[출처와 검증 범위](sources.md)
