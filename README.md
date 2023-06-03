# myex
강의자료, 책 등에서의 실습예제 나만의 방식으로 해본 것들

# GradeManagementSystem(학점관리시스템)
- 자바 프로그래밍 입문의 최종 프로젝트 실습
- 데이터와 목표만 가지고 직접 설계 및 구현한 프로그램(책의 코드와 다름)
- Student 클래스 : 학생에 관한 클래스
  - 필드: 이름, 학번, 전공, 평균 점수, 최종 학점, 수강 과목(해시맵)
  - 생성자: 이름과 전공을 입력해야하고 학번은 자동으로 생성되며 수강과목 해시맵이 생성됨
  - 메서드: 평균 점수 집계, 최종 학접 집계, 수강과목 추가, 수강과목 점수 추가, 자동 학번 부여 등
- Major 클래스 : 전공에 관한 클래스
  - 필드: 전공명, 전공번호, 필수 수강과목
  - 생성자: 전공명과 필수 수강과목을 입력해야하고 전공번호는 자동 부여됨
  - 메서드: 전공명 getter, 전공번호 getter 필수 수강과목 getter 등
- Subject 클래스 : 강의 과목에 관한 클래스
  - 필드: 과목명, 과목번호, Pass/Fail 여부
  - 생성자: 과목명을 입력해야 하고 과목번호는 자동 생성됨
  - 메서드 : 과목명 getter, Pass/Fail 여부 setter 등
- Course 클래스 : 수강한 과목에 관한 속성 및 기능을 넣은 클래스
  - 필드: 과목, 점수, 학점, 학점 정책
  - 생성자: 과목을 입력해야 하며 점수는 -1(미입력)로 초기화됨
  - 메서드 : 학점 정책 setter(Pass/Fail여부-필수 수강과목 여부 확인 후 아니면 일반 학점 정책 적용), 점수 setter(점수가 입력되면 학점도 집계되도록 함) 등
- GradeSystem 인터페이스 : 학점을 산출하는 추상 메서드만 있는 학점 정책 인터페이스
  - General 구현 클래스 : 싱글톤 패턴의 일반 학점 정책
    - 오버라이딩한 String getGrade(int 점수)만 입력
  - ForRequiredSubject 구현 클래스 : 싱글톤 패턴의 필수과목 학점 정책
    - 오버라이딩한 String getGrade(int 점수)만 입력
  - PassFail 구현 클래스
    - 오버라이딩한 String getGrade(int 점수)만 입력
- Report 봉인된 추상 클래스 : 리포트에 관한 템플릿을 제공하는 추상 클래스. SubjectReport와 MajorReport 클래스만 상속을 허용함.
  - 필드: 자주 사용하는 기호들에 관한 것들 상수로 선언, Reportable 인터페이스, 학생 ArrayList, 최종 리포트, 헤더, 메인, 푸터
  - 생성자: Reportable을 상속받는 타입과 학생들(가변인자)을 입력해야하고 필요한 생성자와 템플릿 메서드 호출
  - 메서드: 헤더 생성, 메인 생성, 푸터 생성, 집계(총점, 최빈값, 최고점, 최저점, 평균, 인원) 메서드, 학생 목록 필터링(조건에 맞는 학생만), 최종 리포트를 만들기 위한 템플릿 메서드, 리포트 출력하는 메서드
  - Reportable 마커 인터페이스 : 리포트할 수 있는 것들을 제한하는 마커 인터페이스
  - MajorReport 구현 클래스 : 전공생에 대한 결과를 집계하는 리포트 클래스
    - 생성자와 리포트 결과 출력하는 메서드만 사용 가능
    - 생성자: 전공과 학생들(배열)을 입력하면 집계됨
    - 메서드: 학생 목록 필터링(해당 전공생만 ArrayList에 추가), 헤더 내용 생성, 메인 내용 생성, 푸터 내용 생성, sum(의미가 없는 것 같은데 오버라이딩해야해서 -1 반환하게 함), mode(학점 중 최빈값 반환 - 동일하면 앞에 있는 성적 출력), avg(학생 평균 점수 출력), max/min(학생 최고점/최저점 출력)
  - SubjectReport 구현 클래스 : 강의 수강생에 대한 결과를 집계하는 리포트 클래스
    - 생성자와 리포트 결과 출력하는 메서드만 사용 가능
    - 생성자: 과목과 학생들(가변인자)을 입력하면 집계됨
    - 메서드: 학생 목록 필터링(해당 과목을 듣는 학생만 ArrayList에 추가), 헤더 내용 생성, 메인 내용 생성, 푸터 내용 생성, sum(학생들의 점수 총합), mode(점수 시스템이 달라서 null 반환/사용하지 않음), avg(학생 점수 평균 산출), max/min(학생들 점수 중 최고점/최저점 산출)
- RunTest 실행 클래스
  - 강의 과목 생성
  - 전공 생성
  - 학생 생성
  - 수강과목 담기 및 점수 입력
  - 학생 목록 생성
  - 클래스 및 메서드 테스트용 출력들
  - 강의과목 리포트 생성
  - 전공 리포트 생성
- FinalStaticNumber 클래스 : 상수 영역(만들어놓고 사용할 일이 없어서 비워져있음)
- 기타 과정에 대한 것들 기록(https://blog.naver.com/biyoonx/223117795740)
