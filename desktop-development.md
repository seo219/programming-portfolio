# Java · C# · MSSQL 개발
[← 포트폴리오](README.md)

## Java: 이벤트, 스레드, 소켓, JDBC

[공개용 소스 30개](source-java.zip)

Drive의 JAVA/PROJECT1 소스를 확인했습니다. 교육 실습 코드이며 상용 서비스 구축 경험과 구분합니다.

| 사례 | 코드 | 구조와 확인한 점 |
|---|---|---|
| Swing 계산기 | POLITECH/WB03.java | 버튼 이벤트에서 숫자·이전 값·연산 플래그를 관리합니다. 나눗셈 버튼은 처리 리스너가 없어 완성된 사칙연산 계산기로 표현하지 않습니다. |
| 소켓 통신 | ServerTest/ClientTest, ServerChatTest/ClientChatTest | 서버·클라이언트 연결과 송수신 흐름을 분리합니다. |
| 송수신 스레드 | SendThread/ReceiveThread | 입출력 작업을 별도 스레드로 구성한 학습 사례입니다. |
| 공유 메모리 | SharedMemoryTest/SharesMemoryTest02 | 여러 스레드와 공유 상태를 다룹니다. |
| DB 조회 | TestSelectDB.java | JDBC로 SQL Server 연결, BOOK 조회, ResultSet 순회 후 자원 해제 |

실행에는 JDK와 사례별 클래스 경로, JDBC 예제에는 SQL Server JDBC 드라이버와 샘플 DB가 필요합니다. 접속 비밀번호는 공개본에서 제거했습니다. 테스트 실행이나 DB 접속은 수행하지 않았습니다.

## C#: Windows Forms와 비동기 DB 작업

[공개용 소스·프로젝트 파일 162개](source-csharp.zip)

### 입력 화면과 저장 프로시저 호출

Test01/DataInsert.cs는 화면 로드 시 DB에서 부서·전형 목록을 읽어 ComboBox에 채웁니다. 입력 확인 후 SqlCommand를 StoredProcedure 모드로 구성하고, 타입·길이를 지정한 SqlParameter를 추가해 ExecuteNonQueryAsync를 호출합니다.

```text
폼 로드 → 비동기 목록 조회 → 입력 확인
→ 프로시저와 매개변수 구성 → 비동기 실행 → 예외 표시
```

using 블록으로 연결·명령·리더의 수명을 관리하는 점을 확인했습니다. 개선 과제로는 int.Parse 대신 입력 범위를 검증하는 TryParse, 예외 후 호출자에게 성공·실패를 명확히 반환하는 구조가 있습니다. 현재 코드가 이를 모두 처리한다고 주장하지 않습니다.

### 메모장과 이벤트 학습

WinMemo/Form1.cs에는 열기·저장·다른 이름으로 저장, 편집·글꼴·확대·축소·인쇄 이벤트가 있습니다. Form_Event_Test는 delegate·이벤트 전달, 폼 간 데이터 전달, 스레드 이벤트, ListView·DataGrid·DB 명령을 다룹니다. Win_SuUp에는 모달·모달리스 창과 키·검증·목록 화면 실습이 있습니다.

## MSSQL: 프로시저와 조회

[SQL 스크립트 6개](source-mssql.zip)

- TestSp.sql: InsertExam, updateExam, deleteExam
- Sp_ListViewQuery.sql: InsertListView, DeleteListView, UpdateListView
- Sp.sql: CreateMyTable, InsertTestTable, DropTestTable
- 기타: 조회와 SQL 메모

C# 입력 화면과 SQL 프로시저는 연결해 읽을 수 있지만, 모든 파일이 같은 DB 버전의 완성본이라고 단정하지 않습니다. 데이터베이스와 테이블 스키마를 직접 구성해야 합니다. INSERT·UPDATE·DELETE·DROP 구문을 포함하므로 스크립트를 운영 DB에 그대로 실행하는 예제로 제공하지 않습니다.

## 자료 상태

출력 바이너리·캐시와 개인 데이터가 든 XLS는 제외했습니다. 소스 스냅샷에는 교육 환경의 외부 의존성이나 자동 생성 파일이 일부 빠질 수 있어 그대로 빌드되는 배포 패키지는 아닙니다. 학습 코드의 소유권·개인 기여율을 새로 주장하지 않습니다.
