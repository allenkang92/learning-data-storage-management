# 트랜잭션 (Database Transaction)

## 1. 트랜잭션의 개념
- 데이터베이스의 상태를 변환시키는 하나의 논리적 작업 단위
- 한번에 모두 수행되어야 할 연산들의 집합
- 데이터베이스의 무결성과 일관성을 보장하는 메커니즘

## 2. 트랜잭션의 특성 (ACID)

### 2.1 원자성 (Atomicity)
- 트랜잭션의 연산은 모두 수행되거나 전혀 수행되지 않아야 함
- 부분적 실행이나 중단은 허용되지 않음
- 장애 발생 시 롤백을 통한 복구

### 2.2 일관성 (Consistency)
- 트랜잭션 실행 전후의 데이터베이스 상태가 일관되어야 함
- 무결성 제약조건 유지
- 데이터의 정합성 보장

### 2.3 격리성 (Isolation)
- 동시에 실행되는 트랜잭션들이 서로 영향을 미치지 않음
- 동시성 제어를 통한 관리
- 격리 수준에 따른 동작 보장

### 2.4 지속성 (Durability)
- 성공적으로 완료된 트랜잭션의 결과는 영구적으로 보장
- 시스템 장애에도 데이터 보존
- 로그를 통한 복구 가능

## 3. 트랜잭션 상태

### 3.1 활동 (Active)
- 트랜잭션이 실행 중인 상태
- 연산 수행 진행
- 읽기/쓰기 작업 진행

### 3.2 부분 완료 (Partially Committed)
- 마지막 연산이 실행된 직후 상태
- 결과는 아직 데이터베이스에 반영되지 않음
- COMMIT 명령 대기

### 3.3 완료 (Committed)
- 트랜잭션이 성공적으로 완료된 상태
- 모든 변경사항이 데이터베이스에 반영
- 영구적 저장 보장

### 3.4 실패 (Failed)
- 오류가 발생하여 중단된 상태
- 정상적인 실행 불가능
- 복구 작업 필요

### 3.5 철회 (Aborted)
- 트랜잭션이 취소된 상태
- 모든 변경사항이 롤백됨
- 시작 전 상태로 복구

## 4. 트랜잭션 제어

### 4.1 COMMIT
- 트랜잭션 완료 명령
- 변경사항 영구 저장
- 일관성 보장

### 4.2 ROLLBACK
- 트랜잭션 취소 명령
- 변경사항 되돌리기
- 원자성 보장

### 4.3 SAVEPOINT
- 복구 지점 설정
- 부분 롤백 가능
- 트랜잭션 제어 유연성

## 5. 동시성 제어

### 5.1 락킹 (Locking)
- 공유 락 (Shared Lock)
- 배타적 락 (Exclusive Lock)
- 2단계 락킹 프로토콜

### 5.2 격리 수준
- READ UNCOMMITTED
- READ COMMITTED
- REPEATABLE READ
- SERIALIZABLE

## 6. 회복 기법

### 6.1 로그 기반 회복
- UNDO/REDO 로깅
- 체크포인트 활용
- 즉각 갱신 회복

### 6.2 그림자 페이징
- 이중 페이지 테이블
- 원자적 상태 전이
- 빠른 복구 가능