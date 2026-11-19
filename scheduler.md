# 웹 일정 관리 · scheduler-app

[← 포트폴리오](README.md) · [원본 저장소](https://github.com/seo219/scheduler-app)

## 목표와 기능

캘린더, 날짜별 계획, 할 일, 일정 템플릿을 한 웹 앱에서 관리합니다. 원본에는 AI 일정과 휴일 일정 화면도 포함되어 있습니다. 이 문서는 확인한 라우팅·할 일 CRUD·시간 계산 코드를 중심으로 설명하며, AI 응답 품질이나 실서비스 운영 성과는 주장하지 않습니다.

**기술:** React, React Router, JavaScript/TypeScript, Firebase/Firestore, dayjs, Vite.

## 화면·저장·계산의 분리

| 영역 | 코드 | 역할 |
|---|---|---|
| 화면 연결 | [App.jsx](https://github.com/seo219/scheduler-app/blob/main/src/App.jsx) | 로그인·가입, 캘린더·계획·할 일·설정 경로 |
| 데이터 접근 | [todoService.js](https://github.com/seo219/scheduler-app/blob/main/src/services/todoService.js) | 사용자별 할 일 조회·생성·수정·삭제 |
| 시간 계산 | [freeSlots.ts](https://github.com/seo219/scheduler-app/blob/main/src/utils/freeSlots.ts) | 바쁜 일정 사이의 빈 시간 추출 |
| 활동 배치 | [packActivities.ts](https://github.com/seo219/scheduler-app/blob/main/src/utils/packActivities.ts) | 빈 시간대에 이동·활동 블록 배치 |

App.jsx는 주요 화면을 RequireAuth와 Layout 아래 배치합니다. 이 화면 구조만으로 Firestore 데이터 접근 규칙까지 검증된 것은 아닙니다.

## 핵심 알고리즘 1 · 빈 시간 계산

computeFreeSlots는 다음 순서로 동작합니다.

1. 종료가 시작보다 늦은 일정만 남깁니다.
2. 시작 시각으로 정렬합니다.
3. 하루의 시작·종료 범위에 맞게 구간을 자릅니다.
4. cursor보다 다음 일정 시작이 늦으면 사이를 빈 시간으로 기록합니다.
5. cursor를 이미 지난 종료 시각보다 뒤로만 전진시킵니다.
6. 마지막 일정 이후의 시간도 반환합니다.

겹친 일정은 cursor를 뒤로 되돌리지 않아 하나의 점유 구간처럼 처리됩니다. 정렬 때문에 시간 복잡도는 일반적으로 O(n log n), 이후 순회는 O(n)입니다.

**예시:** 사용 가능 시간이 09~18시이고 일정이 10~12시·11~13시라면 빈 구간은 09~10시와 13~18시입니다. 이는 로직 설명용 예시이며 실행 시험 결과가 아닙니다.

## 핵심 알고리즘 2 · 활동 배치

packActivitiesIntoSlots는 각 빈 시간의 cursor부터 활동을 순서대로 넣습니다. 이동 20분, 준비 시간, 활동 길이, 기본 버퍼 10분을 합산해 해당 슬롯에 들어갈지 판단합니다.

**현재 코드에서 확인한 제약**

- 이동 시간은 실제 경로 조회가 아닌 20분 고정값입니다.
- totalNeed에는 prepMin이 포함되지만, 실제 활동 시작 cursor에는 준비 시간이 별도 반영되지 않습니다.
- 다음 활동이 들어가지 않으면 같은 슬롯에서 더 짧은 후속 활동을 탐색하지 않습니다.

따라서 최적 스케줄링 알고리즘이나 실제 이동시간 기반 배치로 표현하지 않습니다. 준비 시간 처리와 대체 후보 탐색은 개선 과제입니다.

## Firestore CRUD

todoService는 users/{userId}/todos 경로에서 문서를 관리합니다. 목록은 dueDate 오름차순으로 조회하고, 개별 문서가 없으면 null을 반환합니다. 화면 코드와 데이터 접근 함수를 나눈 구조를 확인할 수 있습니다.

## 실행 안내

원본을 내려받아 저장소 루트에서 다음 명령을 사용합니다.

```bash
npm ci
npm run dev
```

원본 package.json에는 build·lint·preview 스크립트도 있습니다. Firebase와 외부 API를 사용하는 기능은 프로젝트에 맞는 설정이 필요합니다. 이 포트폴리오에서는 설정값을 복제하거나 서버를 배포하지 않았고, 설치·빌드 통과 여부는 확인하지 않았습니다.

## 개선 과제

활동 준비 시간의 실제 타임라인 반영, 구간 경계·중첩 입력 테스트, 날짜·시간대 정책 명시, UI 접근 제어와 서버 데이터 규칙의 별도 검증.
