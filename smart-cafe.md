# 스마트 카페 운영 · Py_Cafe

[← 포트폴리오](README.md) · [원본 프로젝트](https://github.com/seo219/Py_Cafe/tree/main/kiosk_GUI02/smart_cafe)

## 목표

주문을 원재료 재고와 연결하고, 배치별 유통기한·입고·폐기·매출을 관리하는 Python/Tkinter 프로그램입니다. 고객 화면과 관리자 화면은 하나의 서비스를 공유합니다.

## 설계

```mermaid
flowchart LR
    UI[고객·관리자 UI] --> S[CafeService]
    S --> R[JsonCafeRepository]
    R --> J[JSON 파일]
```

- UI: 입력과 표시 담당
- Service: 주문·재고·추천·통계 규칙 담당, Tkinter 의존 없음
- Repository: JSON 로드·저장 담당

[서비스 코드](https://github.com/seo219/Py_Cafe/blob/main/kiosk_GUI02/smart_cafe/smart_cafe/services/cafe_service.py) · [저장소 코드](https://github.com/seo219/Py_Cafe/blob/main/kiosk_GUI02/smart_cafe/smart_cafe/repositories/json_repository.py)

## 핵심 로직

### 제조 가능 수량과 병목 재료

레시피의 재료마다 사용 가능 재고 ÷ 1잔 소요량을 내림한 뒤, 그 최솟값을 제조 가능 수량으로 사용합니다. 가장 적은 수량을 허용하는 재료를 병목으로 함께 반환합니다.

### 유통기한이 빠른 배치부터 차감

usable_batches는 만료되지 않고 수량이 남은 배치를 유통기한·입고일·ID 순으로 정렬합니다. _deduct_fefo는 앞에서부터 필요한 양을 차감합니다. 같은 재료라도 배치별 상태를 유지하는 구조입니다.

### 주문 실패 시 일관성

place_order는 장바구니의 전체 필요 재료를 먼저 합산해 부족 여부를 검사합니다. 상태 변경 전 deepcopy 스냅샷을 만들고, 차감·주문 생성·저장 중 예외가 나면 메모리 데이터를 복구합니다.

파일 저장은 임시 JSON을 완성한 뒤 replace합니다. 이는 단일 파일 저장 중 손상 가능성을 줄이는 방식이며, 데이터베이스 트랜잭션이나 다중 프로세스 동시 주문 보장을 의미하지 않습니다.

## 테스트 코드

[기존 unittest 파일](https://github.com/seo219/Py_Cafe/blob/main/kiosk_GUI02/smart_cafe/tests/test_cafe_service.py)에는 다음 다섯 사례가 있습니다.

| 사례 | 검증 의도 |
|---|---|
| 제조 가능 수량 | 병목 재료 기준 계산 |
| 주문 재고 차감과 통계 | 배치 차감·금액·판매 수량 |
| 실패 주문 | 재고와 주문 기록이 변하지 않는지 |
| 입고·폐기 후 재로드 | 저장 상태 유지 |
| 주문 상태 | 허용하지 않는 상태 거부 |

임시 디렉터리를 사용하는 구조라 테스트 데이터와 실제 운영 파일을 분리합니다. 이번 정리에서는 이 테스트를 실행하지 않았습니다.

## 실행 안내

원본 저장소의 kiosk_GUI02/smart_cafe 폴더에서 실행합니다. README는 Python 3.10 이상을 권장합니다.

```bash
python app.py
python -m unittest discover -s tests -v
```

Tkinter를 사용할 수 있는 Python 환경이 필요합니다. 원본 데이터 파일을 사용하는 작업이므로 실행 시 주문·재고 데이터가 변경될 수 있습니다.

## 개선 과제

동시 쓰기 제어, 저장 실패 복구 시나리오 시험, 주문 상태별 매출 집계 정책 정의, 장바구니 수량의 엄격한 정수 검증.

공동 작업의 세부 담당은 확인되지 않아 전체 기능을 개인 단독 성과로 단정하지 않았습니다.
