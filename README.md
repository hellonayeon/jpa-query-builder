# jpa-query-builder
## 🚀 1단계 - Reflection
### 요구사항
- [ ] 클래스 정보 출력: Car 클래스의 모든 필드, 생성자, 메소드에 대한 정보를 출력
- [ ] "test" 로 시작하는 메소드 실행
- [ ] @PrintView 애노테이션 메소드 실행
- [ ] private field 에 값 할당
- [ ] 인자를 가진 생성자의 인스턴스 생성

## 🚀 2단계 - QueryBuilder DDL
### 고려해야 하는 부분
* 단일 데이터베이스(H2)만 고려하지 않고, 여러 종류의 데이터베이스가 연동되더라도 사용할 수 있는 코드를 작성하자.
  * 어떤 인터페이스들이 추출되어야 하는가? (추상화 레벨)

### 요구사항
- [ ] Entity 클래스 정보를 바탕으로 create, drop 쿼리 만들어보기

### 기능 도출
* 클래스의 @Annotation 식별
* Java 데이터타입과 SQL 데이터타입을 매핑
* Query String 생성

## 🚀 3단계 - QueryBuilder DML
### 요구 사항
* [ ] insert, select, delete 쿼리 생성
* [ ] 모두 조회 (findAll), 단건 조회 (findById) 기능

### 기능 도출
* `insert`, `select`, `delete` Query String 생성
  * `where` 조건 처리
* Query 실행

## 🚀 4단계 - Simple Entity Object
### 고려해야 하는 부분
- [ ] ddl, dml 패키지 내부 구현을 통일화
  - dml 진행하면서 구현한 metadata 구조를 ddl 과 동일하게 적용한다.
  - metadata 는 Entity 에 대한 테이블 DDL, DML 쿼리를 생성하기 위해 필요한 정보를 가진 불변데이터이다.
- [ ] 형변환 작업이 들어가 있는 코드 개선
- [ ] where 조건 구현 제거
- [ ] 데이터베이스의 기본 채번 타입 설정 (IDENTITY)

### 요구 사항
* [ ] EntityManager 인터페이스 생성
  * [ ] find()
  * [ ] persist() (insert)
  * [ ] remove() (delete)
  * [ ] update()
